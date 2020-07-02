---
title: 데이터베이스 개체 보안
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- database [Master Data Services], object security
- security [Master Data Services], database objects
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 656b36f796d05d6ea7533c8c35e4b6ffe9572f99
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85811588"
---
# <a name="database-object-security-master-data-services"></a>데이터베이스 개체 보안(Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에서 데이터는 여러 데이터베이스 테이블에 저장되고 뷰에서 볼 수 있습니다. [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 웹 애플리케이션에서 보안을 설정한 정보는 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에 액세스할 수 있는 사용자가 볼 수 있습니다.  
  
 특히 직원 급여 정보가 Employee 모델에 포함되거나 회사 재무 정보가 Account 모델에 포함될 수 있습니다. [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 사용자 인터페이스에서 이러한 모델에 대한 사용자 액세스를 거부할 수 있지만 데이터베이스에 액세스할 수 있는 사용자는 이 데이터를 볼 수 있습니다.  
  
 데이터베이스 개체에 대한 사용 권한을 부여하여 특정 데이터를 사용할 수 있는 사용자를 지정할 수 있습니다. 권한 부여 방법에 대한 자세한 내용은 [GRANT 개체 사용 권한&#40;Transact-SQL&#41;](../t-sql/statements/grant-object-permissions-transact-sql.md)을 참조하세요. SQL Server 보안 설정 방법은 [Securing SQL Server](../relational-databases/security/securing-sql-server.md)을 참조하십시오.  
  
 다음 태스크를 수행하려면 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 데이터베이스에 대한 액세스 권한이 필요합니다.  
  
-   [데이터 준비](#Staging)  
  
-   [비즈니스 규칙에 대해 데이터 유효성 검사](#rules)  
  
-   [버전 삭제](#Versions)  
  
-   [계층 멤버 권한 즉시 적용](#Hierarchy)  
  
-   [시스템 설정 구성](#SysSettings)  
  
##  <a name="staging-data"></a><a name="Staging"></a> 데이터 준비  
 다음 표에서 각 보안 개체에는 이름의 일부로 "이름"이 있습니다. 이것은 엔터티를 만들 때 지정된 준비 테이블의 이름을 나타냅니다. 자세한 내용은 [개요: 테이블에서 데이터 가져오기&#40;Master Data Services&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)를 참조하세요.  
  
|작업|보안 개체|사용 권한|  
|------------|----------------|-----------------|  
|리프 멤버 및 해당 특성을 만들고, 업데이트하고, 삭제합니다.|stg.name_Leaf|필수: INSERT<br /><br /> 선택 사항: SELECT 및 UPDATE|  
|리프 준비 테이블의 데이터를 해당 MDS 데이터 집합 테이블에 로드합니다.|stg.udp_name_Leaf|CREATE 문을 실행하기 전에|  
|통합 멤버 및 해당 특성을 만들고, 업데이트하고, 삭제합니다.|stg.name_Consolidated|필수: INSERT<br /><br /> 선택 사항: SELECT 및 UPDATE|  
|통합 준비 테이블의 데이터를 해당 MDS 데이터 집합 테이블에 로드합니다.|stg.udp_name_Consolidated|CREATE 문을 실행하기 전에|  
|명시적 계층에서 멤버를 이동합니다.|stg.name_Relationship|필수: INSERT<br /><br /> 선택 사항: SELECT 및 UPDATE|  
|관계 준비 테이블의 데이터를 해당 MDS 테이블에 로드합니다.|stg.udp_name_Relationship|CREATE 문을 실행하기 전에|  
|준비 테이블의 데이터를 MDS 데이터 집합 테이블에 삽입하는 동안 발생한 오류를 봅니다.|stg.udp_name_Relationship|SELECT|  
  
 자세한 내용은 [개요: 테이블에서 데이터 가져오기 &#40;MDS(Master Data Services)&#41;](../master-data-services/overview-importing-data-from-tables-master-data-services.md)를 참조 하세요.  
  
##  <a name="validating-data-against-business-rules"></a><a name="rules"></a>비즈니스 규칙에 대해 데이터 유효성 검사  
  
|작업|보안 개체|사용 권한|  
|------------|---------------|-----------------|  
|비즈니스 규칙에 대해 데이터 버전의 유효성을 검사합니다.|mdm.udpValidateModel|CREATE 문을 실행하기 전에|  
  
 자세한 내용은 [유효성 검사 저장 프로시저&#40;Master Data Services&#41;](../master-data-services/validation-stored-procedure-master-data-services.md)를 참조하세요.  
  
##  <a name="deleting-versions"></a><a name="Versions"></a>버전 삭제  
  
|작업|보안 개체|사용 권한|  
|------------|----------------|-----------------|  
|삭제할 버전의 ID 확인|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|모델의 버전 삭제|mdm.udpVersionDelete|CREATE 문을 실행하기 전에|  
  
 자세한 내용은 [버전 삭제&#40;Master Data Services&#41;](../master-data-services/delete-a-version-master-data-services.md)를 참조하세요.  
  
##  <a name="immediately-applying-hierarchy-member-permissions"></a><a name="Hierarchy"></a>계층 멤버 권한 즉시 적용  
  
|작업|보안 개체|사용 권한|  
|------------|----------------|-----------------|  
|멤버 권한 즉시 적용|mdm.udpSecurityMemberProcessRebuildModel|CREATE 문을 실행하기 전에|  
  
 자세한 내용은 [멤버 권한 즉시 적용&#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md)을 참조하세요.  
  
##  <a name="configuring-system-settings"></a><a name="SysSettings"></a>시스템 설정 구성  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에는 동작을 제어하기 위해 구성할 수 있는 시스템 설정이 있습니다. [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 에서 이러한 설정을 조정할 수 있으며, UPDATE 권한이 있는 경우에는 mdm.tblSystemSetting 데이터베이스 테이블에서 이러한 설정을 직접 조정할 수 있습니다. 자세한 내용은 [시스템 설정&#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [보안&#40;Master Data Services&#41;](../master-data-services/security-master-data-services.md)  
  
  
