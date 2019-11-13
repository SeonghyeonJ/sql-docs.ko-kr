---
title: sys. resource_governor_configuration (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_configuration_TSQL
- sys.resource_governor_configuration
- resource_governor_configuration_TSQL
- resource_governor_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_configuration catalog view
ms.assetid: 89099668-1dc6-4b07-9d8b-49bc95c7bfc0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8e4068d9763460995335fe5adbd6684ecb70d8b7
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73982624"
---
# <a name="sysresource_governor_configuration-transact-sql"></a>sys.resource_governor_configuration(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  저장된 리소스 관리자 상태를 반환합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|classifier_function_id|**int**|메타데이터에 저장된 것과 같은 분류자 함수의 ID입니다. Null을 허용하지 않습니다.<br /><br /> **참고** 이 함수는 새 세션을 분류 하 고 규칙을 사용 하 여 작업을 적절 한 작업 그룹으로 라우팅하는 데 사용 됩니다. 자세한 내용은 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)를 참조하세요.|  
|is_enabled|**bit**|리소스 관리자의 현재 상태를 나타냅니다.<br /><br /> 0 = Resource Governor를 사용할 수 없습니다.<br /><br /> 1 = Resource Governor를 사용할 수 있습니다.<br /><br /> Null을 허용하지 않습니다.|  
|max_outstanding_io_per_volume|**int**|**적용 대상**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 이상<br /><br /> 볼륨당 미해결 I/O의 최대 개수입니다.|  
  
## <a name="remarks"></a>설명  
 카탈로그 뷰는 리소스 관리자 구성을 메타데이터에 저장된 대로 표시합니다. 인-메모리 구성을 표시하려면 해당 동적 관리 뷰를 사용합니다.  
  
## <a name="permissions"></a>사용 권한  
 내용을 보려면 VIEW ANY DEFINITION 권한이 필요하고, 내용을 변경하려면 CONTROL SERVER 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 리소스 관리자 구성의 인-메모리 값과 저장된 메타데이터 값을 가져와서 비교하는 방법을 보여 줍니다.  
  
```  
USE master;  
GO  
-- Get the stored metadata.  
SELECT   
object_schema_name(classifier_function_id) AS 'Classifier UDF schema in metadata',   
object_name(classifier_function_id) AS 'Classifier UDF name in metadata'  
FROM   
sys.resource_governor_configuration;  
GO  
-- Get the in-memory configuration.  
SELECT   
object_schema_name(classifier_function_id) AS 'Active classifier UDF schema',   
object_name(classifier_function_id) AS 'Active classifier UDF name'  
FROM   
sys.dm_resource_governor_configuration;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [Resource Governor 카탈로그 뷰 &#40;transact-sql&#41; ](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [dm_resource_governor_configuration &#40;transact-sql&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-configuration-transact-sql.md)   
 [리소스 관리자](../../relational-databases/resource-governor/resource-governor.md)  
  
  
