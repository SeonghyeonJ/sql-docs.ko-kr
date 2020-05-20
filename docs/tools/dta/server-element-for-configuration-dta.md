---
title: Configuration의 Server 요소(DTA)
description: dta 유틸리티에서 Configuration의 Server 요소는 구성을 평가하려는 서버에 대한 식별 정보를 포함합니다.
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: f723e02b13ed5613d3606927ae500c3072c8c6fc
ms.sourcegitcommit: b8933ce09d0e631d1183a84d2c2ad3dfd0602180
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83151794"
---
# <a name="server-element-for-configuration-dta"></a>Configuration의 Server 요소(DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

데이터베이스 엔진 튜닝 관리자가 가상 구성( **Configuration** 요소에 의해 지정됨)을 평가하는 서버에 대한 식별 정보를 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특성|Description|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|각 **Configuration** 요소 당 한 번씩만 필요합니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[Configuration 요소&#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
|**자식 요소**|[Server의 Name 요소&#40;DTA&#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Configuration의 Database 요소&#40;DTA&#41;](../../tools/dta/database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a>설명  
 **Server** 요소에 하나의 **Configuration** 요소만 지정할 수 있습니다. **데이터베이스 엔진 튜닝 관리자 XML 스키마** 에서 이 요소의 이름은 [ServerTypecomplexType](https://go.microsoft.com/fwlink/?linkid=43100)입니다. 이 **Server** 요소와 **DTAInput** 요소의 자식 요소를 혼동하지 마십시오. 자세한 내용은 [Server 요소&#40;DTA&#41;](../../tools/dta/server-element-dta.md)를 참조하세요.  
  
## <a name="example"></a>예제  
 사용 예를 보려면 [사용자 정의 구성이 포함된 XML 입력 파일 예제&#40;DTA&#41;](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
