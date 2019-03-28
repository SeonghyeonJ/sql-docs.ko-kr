---
title: sp_helplogins (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3461d6f80bb1ac693cca78954e5165fb7f012436
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529745"
---
# <a name="sphelplogins-transact-sql"></a>sp_helplogins(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  각 데이터베이스의 로그인 및 연관된 사용자에 관한 정보를 제공합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>인수  
`[ @LoginNamePattern = ] 'login'` 로그인 이름이입니다. *login*은 **sysname**이며 기본값은 NULL입니다. *로그인* 지정한 경우 존재 해야 합니다. 하는 경우 *로그인* 은 지정 하지 않으면 모든 로그인에 대 한 정보 반환 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
 다음 표에서 볼 수 있듯이 첫 번째 보고서에는 지정한 각 로그인에 관한 정보가 포함되어 있습니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|로그인 이름입니다.|  
|**SID**|**varbinary(85)**|로그인 SID(보안 ID)입니다.|  
|**DefDBName**|**sysname**|기본 데이터베이스 **LoginName** 인스턴스에 연결할 때 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]입니다.|  
|**DefLangName**|**sysname**|사용 되는 언어를 기본 **LoginName**합니다.|  
|**하는지 여부가 결정 됩니다**|**char(5)**|Yes = **LoginName** 데이터베이스에 연결 된 사용자 이름이 있습니다.<br /><br /> 이상 = **LoginName** 는 연결 된 사용자 이름이 없습니다.|  
|**ARemote**|**char(7)**|Yes = **LoginName** 에 연결된 된 원격 로그인 합니다.<br /><br /> 이상 = **LoginName** 연결된 된 로그인이 없습니다.|  
  
 두 번째 보고서에는 다음 표와 같이 각 로그인에 매핑된 사용자와 해당 로그인의 역할 멤버 자격에 관한 정보가 포함되어 있습니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|로그인 이름입니다.|  
|**DBName**|**sysname**|기본 데이터베이스 **LoginName** 인스턴스에 연결할 때 사용 하 여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]입니다.|  
|**UserName**|**sysname**|사용자 계정이 **LoginName** 에 매핑되 **DBName**, 및 역할을 하는 **LoginName** 의 멤버인 **DBName**합니다.|  
|**UserOrAlias**|**char(8)**|MemberOf = **UserName** 는 역할입니다.<br /><br /> 사용자 = **UserName** 사용자 계정입니다.|  
  
## <a name="remarks"></a>Remarks  
 로그인을 제거 하기 전에 사용 하 여 **sp_helplogins** 로그인에 매핑되는 사용자 계정을 식별할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버 자격이 필요 합니다 **securityadmin** 고정된 서버 역할입니다.  
  
 지정 된 로그인에 매핑된 모든 사용자 계정을 식별 **sp_helplogins** 서버 내의 모든 데이터베이스를 확인 해야 합니다. 따라서 서버의 각 데이터베이스에 대해 다음 조건 중 최소한 하나를 만족해야 합니다.  
  
-   실행 중인 사용자 **sp_helplogins** 데이터베이스에 액세스할 수 있는 권한이 있습니다.  
  
-   합니다 **게스트** 데이터베이스에서 사용자 계정을 사용할 수 있습니다.  
  
 하는 경우 **sp_helplogins** 데이터베이스에 액세스할 수 없습니다 **sp_helplogins** 고 오류 메시지 15622를 표시 합니다. 가능한 한 많은 정보를 반환 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `John`이라는 로그인에 대한 정보를 보고합니다.  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>관련 항목  
 [Security Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
