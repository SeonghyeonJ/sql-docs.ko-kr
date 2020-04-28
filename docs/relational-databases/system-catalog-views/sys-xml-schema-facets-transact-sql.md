---
title: sys. xml_schema_facets (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_facets
- xml_schema_facets_TSQL
- sys.xml_schema_facets_TSQL
- xml_schema_facets
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_facets catalog view
ms.assetid: 4402dde9-1877-4872-8550-140dc2a177d2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 41e00ca05205fcb1384d436de2f423c63e05ba5c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68103359"
---
# <a name="sysxml_schema_facets-transact-sql"></a>sys.xml_schema_facets(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Xml_types**에 해당 하는 xml 형식 정의의 패싯 (제한) 당 행을 반환 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**xml_component_id**|**int**|이 패싯이 속하는 XML 구성 요소(유형)의 ID입니다.|  
|**facet_id**|**int**|구성 요소 ID 내에서 고유한 패싯의 ID입니다. 서수이며 1부터 시작합니다.|  
|**종류로**|**char(2)**|패싯의 종류이며 다음과 같습니다.<br /><br /> LG = 길이<br /><br /> LN = 최소 길이<br /><br /> LX = 최대 길이<br /><br /> PT = 패턴(정규식)<br /><br /> EU = 열거<br /><br /> IN = 최소 포함 값<br /><br /> IX = 최대 포함 값<br /><br /> EN = 최소 제외 값<br /><br /> EX = 최대 제외 값<br /><br /> DT = 전체 자릿수<br /><br /> DF = 소수 자릿수<br /><br /> WS = 공백 정규화|  
|**kind_desc**|**nvarchar (60)**|패싯의 종류에 대한 설명이며 다음과 같습니다.<br /><br /> LENGTH<br /><br /> MINIMUM_LENGTH<br /><br /> MAXIMUM_LENGTH<br /><br /> PATTERN<br /><br /> ENUMERATION<br /><br /> MINIMUM_INCLUSIVE_VALUE<br /><br /> MAXIMUM_INCLUSIVE_VALUE<br /><br /> MINIMUM_EXCLUSIVE_VALUE<br /><br /> MAXIMUM_EXCLUSIVE_VALUE<br /><br /> TOTAL_DIGITS<br /><br /> FRACTION_DIGITS<br /><br /> WHITESPACE_NORMALIZATION|  
|**is_fixed**|**bit**|1 = 패싯에 미리 지정된 고정 값이 있습니다.<br /><br /> 0 = 고정 값이 (기본값)|  
|**value**|**nvarchar(4000)**|패싯의 미리 지정된 고정 값입니다.|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;카탈로그 뷰](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Xml 스키마 &#40;XML 형식 시스템&#41; 카탈로그 뷰 &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)  
  
  
