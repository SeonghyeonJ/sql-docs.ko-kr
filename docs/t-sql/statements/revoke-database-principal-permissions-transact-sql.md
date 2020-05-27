---
title: REVOKE 데이터베이스 보안 주체 사용 권한
description: 데이터베이스 사용자, 데이터베이스 역할 또는 애플리케이션 역할에 대한 권한을 취소합니다.
titleSuffix: SQL Server (Transact-SQL)
ms.custom: seo-lt-2019
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], permissions
- REVOKE statement, roles
- database user permissions [SQL Server]
- REVOKE statement, users
- application roles [SQL Server], permissions
ms.assetid: c45e1086-c25b-48bb-a764-4a893e983db2
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0353ff7b9e0778a7ef59107f5ba2876e72bbdd69
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75243338"
---
# <a name="revoke-database-principal-permissions-transact-sql"></a>REVOKE 데이터베이스 보안 주체 사용 권한(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  데이터베이스 사용자, 데이터베이스 역할 또는 애플리케이션 역할에 대해 부여되거나 거부된 사용 권한을 취소합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
REVOKE [ GRANT OPTION FOR ] permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
       | [ ROLE :: database_role ]  
       | [ APPLICATION ROLE :: application_role ]  
    }  
    { FROM | TO } <database_principal> [ ,...n ]  
        [ CASCADE ]  
    [ AS <database_principal> ]  
  
<database_principal> ::=  
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>인수  
 *permission*  
 데이터베이스 보안 주체에 대해 취소할 수 있는 사용 권한을 지정합니다. 사용 권한 목록은 이 항목의 뒤에 나오는 주의 섹션을 참조하세요.  
  
 USER ::*database_user*  
 사용 권한을 취소할 사용자의 클래스 및 이름을 지정합니다. 범위 한정자( **::** )가 필요합니다.  
  
 ROLE ::*database_role*  
 사용 권한을 취소할 역할의 클래스 및 이름을 지정합니다. 범위 한정자( **::** )가 필요합니다.  
  
 APPLICATION ROLE ::*application_role*  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
 사용 권한을 취소할 애플리케이션 역할의 클래스 및 이름을 지정합니다. 범위 한정자( **::** )가 필요합니다.  
  
 GRANT OPTION  
 지정한 사용 권한을 다른 보안 주체에게 부여할 수 있는 권한이 취소됨을 나타냅니다. 사용 권한 자체는 취소되지 않습니다.  
  
> [!IMPORTANT]  
>  보안 주체에 GRANT 옵션 없이 지정된 사용 권한이 있는 경우 사용 권한 자체가 취소됩니다.  
  
 CASCADE  
 사용 권한이 취소된 보안 주체에게 사용 권한을 부여 받거나 거부당한 다른 보안 주체의 사용 권한도 취소됨을 나타냅니다.  
  
> [!CAUTION]  
>  WITH GRANT OPTION을 부여 받은 사용 권한이 연계되어 취소되면 해당 사용 권한의 GRANT 및 DENY가 모두 취소됩니다.  
  
 \<database_principal>로서 이 쿼리를 실행하는 보안 주체가 사용 권한을 부여하는 권한을 취소할 수 있는 다른 보안 주체를 지정합니다.  
  
 *Database_user*  
 데이터베이스 사용자를 지정합니다.  
  
 *Database_role*  
 데이터베이스 역할을 지정합니다.  
  
 *Application_role*  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
 애플리케이션 역할을 지정합니다.  
  
 *Database_user_mapped_to_Windows_User*  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상
  
 Windows 사용자로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_Windows_Group*  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상
  
 Windows 그룹으로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_certificate*  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상
  
 인증서로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_asymmetric_key*  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상
  
 비대칭 키로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_with_no_login*  
 해당 서버 수준의 보안 주체가 없는 데이터베이스 사용자를 지정합니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="database-user-permissions"></a>데이터베이스 사용자 권한  
 데이터베이스 사용자는 사용 권한 계층에서 해당 사용자의 부모인 데이터베이스에 포함된 데이터베이스 수준 보안 개체입니다. 다음 표에는 데이터베이스 사용자에 대해 취소할 수 있는 가장 제한적인 특정 사용 권한이 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한과 함께 나열되어 있습니다.  
  
|데이터베이스 사용자 권한|데이터베이스 사용자 권한에 포함된 사용 권한|데이터베이스 사용 권한에 포함된 사용 권한|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>데이터베이스 역할 사용 권한  
 데이터베이스 역할은 사용 권한 계층에서 해당 역할의 부모인 데이터베이스에 포함된 데이터베이스 수준 보안 개체입니다. 다음 표에는 데이터베이스 역할에 대해 취소할 수 있는 가장 제한적인 특정 사용 권한이 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한과 함께 나열되어 있습니다.  
  
|데이터베이스 역할 사용 권한|데이터베이스 역할 사용 권한에 포함된 사용 권한|데이터베이스 사용 권한에 포함된 사용 권한|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>애플리케이션 역할 사용 권한  
 애플리케이션 역할은 사용 권한 계층에서 해당 역할의 부모인 데이터베이스에 포함된 데이터베이스 수준 보안 개체입니다. 다음 표에는 애플리케이션 역할에 대해 취소할 수 있는 가장 제한적인 특정 사용 권한이 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한과 함께 나열되어 있습니다.  
  
|애플리케이션 역할 사용 권한|애플리케이션 역할 사용 권한에 포함된 사용 권한|데이터베이스 사용 권한에 포함된 사용 권한|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>사용 권한  
 지정한 보안 주체에 대한 CONTROL 권한 또는 CONTROL 권한을 포함하는 상위 사용 권한이 필요합니다.  
  
 **db_owner** 고정 데이터베이스 역할의 멤버와 같이 데이터베이스에 대한 CONTROL 권한이 부여된 사용자는 데이터베이스의 모든 보안 개체에 대한 사용 권한을 부여할 수 있습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-revoking-control-permission-on-a-user-from-another-user"></a>A. 다른 사용자로부터 사용자에 대한 CONTROL 권한 취소  
 다음 예에서는 사용자 `CONTROL`로부터 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 사용자 `Wanida`에 대한 `RolandX` 권한을 취소합니다.  
  
```  
USE AdventureWorks2012;  
REVOKE CONTROL ON USER::Wanida FROM RolandX;  
GO  
```  
  
### <a name="b-revoking-view-definition-permission-on-a-role-from-a-user-to-which-it-was-granted-with-grant-option"></a>B. WITH GRANT OPTION이 부여된 사용자로부터 역할에 대한 VIEW DEFINITION 권한 취소  
 다음 예에서는 데이터베이스 사용자 `VIEW DEFINITION`로부터 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 역할 `SammamishParking`에 대한 `JinghaoLiu` 권한을 취소합니다. 사용자 `CASCADE`에게 `JinghaoLiu` 권한 `VIEW DEFINITION`이 부여되었기 때문에 `WITH GRANT OPTION` 옵션이 지정됩니다.  
  
```  
USE AdventureWorks2012;  
REVOKE VIEW DEFINITION ON ROLE::SammamishParking   
    FROM JinghaoLiu CASCADE;  
GO  
```  
  
### <a name="c-revoking-impersonate-permission-on-a-user-from-an-application-role"></a>C. 애플리케이션 역할로부터 사용자에 대한 IMPERSONATE 권한 취소  
 다음 예에서는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 애플리케이션 역할 `IMPERSONATE`로부터 사용자 `HamithaL`에 대한 `AccountsPayable17` 권한을 취소합니다.  
  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
```  
USE AdventureWorks2012;  
REVOKE IMPERSONATE ON USER::HamithaL FROM AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>참고 항목  
 [GRANT 데이터베이스 보안 주체 사용 권한 &#40;Transact-SQL&#41;](../../t-sql/statements/grant-database-principal-permissions-transact-sql.md)   
 [DENY 데이터베이스 보안 주체 사용 권한 &#40;Transact-SQL&#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [sys.database_principals&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER&#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [CREATE APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [CREATE ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT&#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [사용 권한&#40;데이터베이스 엔진&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

