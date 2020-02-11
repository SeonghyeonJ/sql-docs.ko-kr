---
title: sys. system_components_surface_area_configuration (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.system_components_surface_area_configuration_TSQL
- system_components_surface_area_configuration
- system_components_surface_area_configuration_TSQL
- sys.system_components_surface_area_configuration
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_components_surface_area_configuration catalog view
ms.assetid: d9920008-3387-4f9e-8f21-47473f2ba04f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 665e73b3cd072bfffc214c518d75d96af3591f94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108870"
---
# <a name="syssystem_components_surface_area_configuration-transact-sql"></a>sys.system_components_surface_area_configuration(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  노출 영역 구성 요소를 사용하여 설정하거나 해제할 수 있는 실행 가능한 각 시스템 개체에 대해 행을 반환합니다. 자세한 내용은 [노출 영역 구성](../../relational-databases/security/surface-area-configuration.md)을 참조 하세요.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**component_name**|**sysname**|구성 요소 이름입니다. 키워드 데이터 정렬 Latin1_General_CI_AS_KS_WS를 가집니다. NULL이 될 수 없습니다.|  
|**database_name**|**sysname**|개체를 포함하는 데이터베이스입니다. 키워드 데이터 정렬 Latin1_General_CI_AS_KS_WS를 가집니다. 다음 중 하나여야 합니다.<br /><br /> **master**<br /><br /> **msdb**<br /><br /> **mssqlsystemresource**|  
|**schema_name**|**sysname**|개체를 포함하는 스키마입니다. 키워드 데이터 정렬 Latin1_General_CI_AS_KS_WS를 가집니다. NULL이 될 수 없습니다.|  
|**object_name**|**sysname**|개체 이름입니다. 키워드 데이터 정렬 Latin1_General_CI_AS_KS_WS를 가집니다. NULL이 될 수 없습니다.|  
|**상태일**|**tinyint**|0 = 사용 안 함<br /><br /> 1 = 사용|  
|**type**|**char (2)**|개체 유형입니다. 다음 중 하나일 수 있습니다.<br /><br /> P = SQL_STORED_PROCEDURE<br /><br /> PC = CLR_STORED_PROCEDURE<br /><br /> FN = SQL_SCALAR_FUNCTION<br /><br /> FS = CLR_SCALAR_FUNCTION<br /><br /> FT = CLR_TABLE_VALUED_FUNCTION<br /><br /> IF = SQL_INLINE_TABLE_VALUED_FUNCTION<br /><br /> TF = SQL_TABLE_VALUED_FUNCTION<br /><br /> X = EXTENDED_STORED_PROCEDURE|  
|**type_desc**|**nvarchar (60)**|개체 유형에 대한 이름 설명입니다.|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Transact-sql&#41;&#40;보안 카탈로그 뷰](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
