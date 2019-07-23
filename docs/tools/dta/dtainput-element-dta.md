---
title: DTAInput 요소 (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAInput element
ms.assetid: 40c19abf-ded5-43de-be96-5b43b1b81b03
author: markingmyname
ms.author: maghan
ms.openlocfilehash: cb75df038dd0108b930af25fad9177ec9a437145
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132750"
---
# <a name="dtainput-element-dta"></a>DTAInput 요소(DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  데이터베이스 엔진 튜닝 관리자에 대한 XML 입력의 정의를 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<DTAXML>  
    <DTAInput>  
    ...code removed here...  
    </DTAInput>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|---------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|**DTAXML** 요소마다 한 번만 지정할 수 있습니다(옵션).|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[DTAXML 요소&#40;DTA&#41;](../../tools/dta/dtaxml-element-dta.md)|  
|**자식 요소**|[Server 요소&#40;DTA&#41;](../../tools/dta/server-element-dta.md)<br /><br /> [Workload 요소&#40;DTA&#41;](../../tools/dta/workload-element-dta.md)<br /><br /> [TuningOptions 요소&#40;DTA&#41;](../../tools/dta/tuningoptions-element-dta.md)<br /><br /> [Configuration 요소&#40;DTA&#41;](../../tools/dta/configuration-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 이 요소는 데이터베이스 엔진 튜닝 관리자 입력 스키마 계층의 루트입니다. 데이터베이스 엔진 튜닝 관리자에 대한 입력은 튜닝할 데이터베이스가 있는 서버, 작업, 튜닝 옵션 또는 사용자 지정 구성을 지정하는 인수가 될 수 있습니다.  
  
## <a name="example"></a>예제  
 **DTAInput** 요소의 사용 예를 보려면 [단순 XML 입력 파일 샘플&#40;DTA&#41;](../../tools/dta/simple-xml-input-file-sample-dta.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
