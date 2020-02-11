---
title: '3 단원: SQL Server 자격 증명 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 61a25d1f4e86204d05b3be6bf2a5dbc8cd0474b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "70153829"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>3단원: SQL Server 자격 증명 만들기
  이 단원에서는 Azure 저장소 계정에 액세스 하는 데 사용 되는 보안 정보를 저장 하는 자격 증명을 만듭니다.  
  
 SQL Server 자격 증명은 SQL Server 외부의 리소스에 연결하는 데 필요한 인증 정보를 저장하는 데 사용되는 개체입니다. 자격 증명에는 스토리지 컨테이너의 URI 경로와 공유 액세스 서명 키 값이 저장됩니다. 데이터 또는 로그 파일에서 사용하는 각 스토리지 컨테이너에 대해 컨테이너 경로와 일치하는 이름의 SQL Server 자격 증명을 만들어야 합니다.  
  
 자격 증명에 대 한 일반 정보는 [자격 증명 &#40;데이터베이스 엔진&#41;](security/authentication-access/credentials-database-engine.md)를 참조 하세요.  
  
> [!IMPORTANT]  
>  아래에 설명 된 SQL Server 자격 증명을 만들기 위한 요구 사항은 [Azure의 SQL Server 데이터 파일](databases/sql-server-data-files-in-microsoft-azure.md) 기능에만 적용 됩니다. Azure 스토리지에서 백업 프로세스를 위한 자격 증명을 만드는 방법에 대한 자세한 내용은 [Lesson 2: Create a SQL Server Credential](../tutorials/lesson-2-create-a-sql-server-credential.md)를 참조하세요.  
  
 SQL Server 자격 증명을 만들려면 다음 단계를 수행합니다.  
  
1.  SQL Server Management Studio에 연결합니다.  
  
2.  개체 탐색기에서 설치된 데이터베이스 엔진의 인스턴스에 연결합니다.  
  
3.  표준 도구 모음에서 새 쿼리를 클릭합니다.  
  
4.  다음 예를 복사하여 쿼리 창에 붙여 넣고 필요한 대로 수정합니다. 다음 명령문은 저장소 컨테이너의 공유 액세스 인증서를 저장 하는 SQL Server 자격 증명을 만듭니다.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     자세한 내용은 [CREATE CREDENTIAL &#40;transact-sql&#41;](/sql/t-sql/statements/create-credential-transact-sql) SQL Server 온라인 설명서를 참조 하세요.  
  
5.  사용할 수 있는 모든 자격 증명을 보려면 쿼리 창에서 다음 문을 실행합니다.  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Sys. 자격 증명에 대 한 자세한 내용은 [sys. 자격 증명 &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) SQL Server 온라인 설명서를 참조 하세요.  
  
 **다음 단원:**  
  
 [4단원: Azure Storage에서 데이터베이스 만들기](lesson-3-database-backup-to-url.md)  
  
  
