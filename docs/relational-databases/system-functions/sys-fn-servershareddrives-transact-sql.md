---
title: sys.fn_servershareddrives (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_servershareddrives
- fn_servershareddrives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_servershareddrives function
- shared drives [SQL Server]
- names [SQL Server], shared drives
- sys.fn_serversharedrives function
ms.assetid: ff01eff7-8cb6-460c-ba7a-6a52bda6d471
author: rothja
ms.author: jroth
ms.openlocfilehash: 71858ee3c57af8d94bdf4ef4addad720655942f4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122546"
---
# <a name="sysfnservershareddrives-transact-sql"></a>sys.fn_servershareddrives(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  클러스터형 서버가 사용하는 공유 드라이브의 이름을 반환합니다.  
  
> [!IMPORTANT]  
>  이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 기능은 이전 버전과의 호환성을 위해 제공됩니다. 사용 하는 것이 좋습니다 [sys.dm_io_cluster_valid_path_names &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md) 대신 합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
fn_servershareddrives()  
```  
  
## <a name="tables-returned"></a>반환된 테이블  
 현재 서버가 클러스터형 서버인 **fn_servershareddrives** 공유 드라이브의 드라이브 이름을 반환 합니다.  
  
 현재 서버 인스턴스가 클러스터형된 서버가 아닌 경우 **fn_servershareddrives** 빈 행 집합을 반환 합니다.  
  
## <a name="remarks"></a>설명  
 `fn_servershareddrives`는 이 클러스터형 서버가 사용하는 공유 드라이브의 목록을 반환합니다. 이러한 공유 드라이브와 동일한 클러스터 그룹에 속해야 합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스입니다. 또한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 리소스도 이 드라이브에 종속됩니다.  
  
 이 함수는 사용자가 사용할 수 있는 드라이브를 식별하는 데 유용합니다.  
  
## <a name="permissions"></a>사용 권한  
 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 VIEW SERVER STATE 권한이 있어야 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `fn_servershareddrives`를 사용하여 클러스터형 서버 인스턴스에서 쿼리합니다.  
  
```  
SELECT * FROM fn_servershareddrives();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 DriveName  
  
 -------\-  
  
 분  
  
 n  
  
## <a name="see-also"></a>관련 항목  
 [sys.dm_io_cluster_valid_path_names &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)  
  
  
