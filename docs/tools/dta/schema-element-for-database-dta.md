---
title: Database의 Schema 요소(DTA)
description: dta 유틸리티에서 Database의 Schema 요소는 튜닝할 데이터베이스의 스키마를 지정합니다.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 929e74d0988b5cff59a18d847555ea4202432ebf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85732047"
---
# <a name="schema-element-for-database-dta"></a>Database의 Schema 요소(DTA)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

튜닝할 데이터베이스의 스키마를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특성|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|**Server** 요소 아래 지정된 **Database** 요소에 한 번만 지정해야 합니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[Server의 Database 요소&#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
|**자식 요소**|[Schema의 Name 요소&#40;DTA&#41;](../../tools/dta/name-element-for-schema-dta.md)<br /><br /> [Schema의 Table 요소&#40;DTA&#41;](../../tools/dta/table-element-for-schema-dta.md)|  
  
## <a name="example"></a>예제  
 이 요소의 사용 예는 [Server 요소&#40;DTA&#41;](../../tools/dta/server-element-dta.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
