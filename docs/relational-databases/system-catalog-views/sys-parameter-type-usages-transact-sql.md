---
description: sys.parameter_type_usages(Transact-SQL)
title: sys. parameter_type_usages (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.parameter_type_usages
- sys.parameter_type_usages_TSQL
- parameter_type_usages_TSQL
- parameter_type_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameter_type_usages catalog view
ms.assetid: af0e167b-bffb-4525-84ec-3607f9268d3d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f20fbf0face7b4b99c7c2d5b5920139e68670052
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542520"
---
# <a name="sysparameter_type_usages-transact-sql"></a>sys.parameter_type_usages(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  사용자 정의 형식의 매개 변수마다 한 행씩 반환합니다.  
  
> [!NOTE]  
>  이 뷰에서는 번호가 매겨진 프로시저의 매개 변수에 대한 행을 반환하지 않습니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|이 매개 변수가 속한 개체의 ID입니다.|  
|**parameter_id**|**int**|매개 변수의 ID입니다. 개체 내에서 고유합니다.|  
|**user_type_id**|**int**|사용자 정의 형식의 ID입니다.<br /><br /> 형식의 이름을 반환 하려면이 열에 대 한 [sys. types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) 카탈로그 뷰에 조인 합니다.|  
  
## <a name="permissions"></a>사용 권한  
 **public** 역할의 멤버 자격이 필요합니다. 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;스칼라 형식 카탈로그 뷰 ](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
