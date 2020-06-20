---
title: 배포자 및 게시자 정보 스크립트 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Publishers [SQL Server replication], information scripts
- Distributors [SQL Server replication], information scripts
ms.assetid: 8622db47-c223-48fa-87ff-0b4362cd069a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4695b53e52c9c63eaacb4f2f32c6bc9f65958213
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85060830"
---
# <a name="distributor-and-publisher-information-script"></a>배포자 및 게시자 정보 스크립트
  이 스크립트는 시스템 테이블 및 복제 저장 프로시저를 사용하여 배포자 및 게시자의 개체에 대한 일반적인 질문에 대해 응답할 수 있습니다. 스크립트는 "현재 상태로" 사용할 수 있으며 사용자 지정 스크립트의 기준도 제공할 수 있습니다. 스크립트를 사용자 환경에서 실행하려면 다음 두 가지를 수정해야 합니다.  
  
-   사용자의 게시 데이터베이스 이름을 사용할 수 있도록 `use AdventureWorks2012` 줄을 변경합니다.  
  
-   줄에서 주석 ( `--` )을 제거 `exec sp_helparticle @publication='<PublicationName>'` 하 고를 \<PublicationName> 게시 이름으로 바꿉니다.  
  
```  
--********** Execute at the Distributor in the master database **********--  
  
USE master;  
go  
  
--Is the current server a Distributor?  
--Is the distribution database installed?  
--Are there other Publishers using this Distributor?  
EXEC sp_get_distributor  
  
--Is the current server a Distributor?  
SELECT is_distributor FROM sys.servers WHERE name='repl_distributor' AND data_source=@@servername;  
  
--Which databases on the Distributor are distribution databases?  
SELECT name FROM sys.databases WHERE is_distributor = 1  
  
--What are the Distributor and distribution database properties?  
EXEC sp_helpdistributor;  
EXEC sp_helpdistributiondb;  
EXEC sp_helpdistpublisher;  
  
--********** Execute at the Publisher in the master database **********--  
  
--Which databases are published for replication and what type of replication?  
EXEC sp_helpreplicationdboption;  
  
--Which databases are published using snapshot replication or transactional replication?  
SELECT name as tran_published_db FROM sys.databases WHERE is_published = 1;  
--Which databases are published using merge replication?  
SELECT name as merge_published_db FROM sys.databases WHERE is_merge_published = 1;  
  
--What are the properties for Subscribers that subscribe to publications at this Publisher?  
EXEC sp_helpsubscriberinfo;  
  
--********** Execute at the Publisher in the publication database **********--  
  
USE AdventureWorks2012;  
go  
  
--What are the snapshot and transactional publications in this database?   
EXEC sp_helppublication;  
--What are the articles in snapshot and transactional publications in this database?  
--REMOVE COMMENTS FROM NEXT LINE AND REPLACE <PublicationName> with the name of a publication  
--EXEC sp_helparticle @publication='<PublicationName>';  
  
--What are the merge publications in this database?   
EXEC sp_helpmergepublication;  
--What are the articles in merge publications in this database?  
EXEC sp_helpmergearticle; -- to return information on articles for a single publication, specify @publication='<PublicationName>'  
  
--Which objects in the database are published?  
SELECT name AS published_object, schema_id, is_published AS is_tran_published, is_merge_published, is_schema_published  
FROM sys.tables WHERE is_published = 1 or is_merge_published = 1 or is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.procedures WHERE is_schema_published = 1  
UNION  
SELECT name AS published_object, schema_id, 0, 0, is_schema_published  
FROM sys.views WHERE is_schema_published = 1;  
  
--Which columns are published in snapshot or transactional publications in this database?  
SELECT object_name(object_id) AS tran_published_table, name AS published_column FROM sys.columns WHERE is_replicated = 1;  
  
--Which columns are published in merge publications in this database?  
SELECT object_name(object_id) AS merge_published_table, name AS published_column FROM sys.columns WHERE is_merge_published = 1;  
```  
  
## <a name="see-also"></a>참고 항목  
 [복제 관리자를 위한 질문과 대답](frequently-asked-questions-for-replication-administrators.md)   
 [sp_get_distributor&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-get-distributor-transact-sql)   
 [sp_helparticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql)   
 [sp_helpdistributiondb&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql)   
 [sp_helpdistpublisher&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql)   
 [sp_helpdistributor&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql)   
 [sp_helpmergearticle&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql)   
 [sp_helpmergepublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql)   
 [sp_helppublication&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql)   
 [sp_helpreplicationdboption&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpreplicationdboption-transact-sql)   
 [sp_helpsubscriberinfo&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql)   
 [sys.columns&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)   
 [sys.databases&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)   
 [sys.procedures&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-procedures-transact-sql)   
 [sys.servers&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-servers-transact-sql)   
 [sys.tables&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-tables-transact-sql)   
 [sys.views&#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-views-transact-sql)  
  
  
