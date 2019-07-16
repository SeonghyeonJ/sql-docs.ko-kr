---
title: sp_dropdistributor (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistributor
- sp_dropdistributor_TSQL
helpviewer_keywords:
- sp_dropdistributor
ms.assetid: 0644032f-5ff0-4718-8dde-321bc9967a03
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9943e6f3d43ff1b543a86425b2644ee4c46a105c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68081509"
---
# <a name="spdropdistributor-transact-sql"></a>sp_dropdistributor(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  배포자를 제거합니다. 이 저장 프로시저는 배포 데이터베이스를 제외한 모든 데이터베이스의 배포자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_dropdistributor [ [ @no_checks= ] no_checks ]   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>인수  
`[ @no_checks = ] no_checks` 배포자를 삭제 하기 전에 종속 개체에 대 한 확인 여부를 나타냅니다. *no_checks* 됩니다 **비트**, 기본값은 0입니다.  
  
 경우 **0**하십시오 **sp_dropdistributor** 해당 배포자는 물론 모든 게시 및 배포 개체가 삭제 된 있는지 확인 합니다.  
  
 경우 **1**하십시오 **sp_dropdistributor** 배포자를 제거 하기 전에 모든 게시 및 배포 개체를 삭제 합니다.  
  
`[ @ignore_distributor = ] ignore_distributor` 이 저장된 프로시저는 배포자에 연결 하지 않고 실행 되는지 여부를 나타냅니다. *ignore_distributor* 됩니다 **비트**, 기본값은 **0**합니다.  
  
 경우 **0**하십시오 **sp_dropdistributor** 배포자에 연결 하 고 모든 복제 개체를 제거 합니다. 하는 경우 **sp_dropdistributor** 저장된 프로시저가 실패 배포자에 연결할 수 없는 합니다.  
  
 하는 경우 **1**, 배포자에 연결 되지 및 복제 개체가 제거 되지 않습니다. 배포자가 제거되었거나 영구적으로 오프라인 상태인 경우에 사용합니다. 배포자에서 게시자에 대한 개체는 배포자가 나중에 다시 설치될 때까지 제거되지 않습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>설명  
 **sp_dropdistributor** 모든 유형의 복제에 사용 됩니다.  
  
 서버에서 다른 게시자 또는 배포 개체가 없으면 **sp_dropdistributor** 하지 않으면 실패 **@no_checks** 로 설정 되어 **1**합니다.  
  
 이 저장된 프로시저를 실행 하 여 배포 데이터베이스를 삭제 한 후 실행 해야 합니다 **sp_dropdistributiondb**합니다.  
  
## <a name="example"></a>예제  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributor-trans_1.sql)]  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **sysadmin** 고정된 서버 역할을 실행할 수 있습니다 **sp_dropdistributor**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [게시 및 배포 해제](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_changedistributor_property &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_helpdistributor&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [복제 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
