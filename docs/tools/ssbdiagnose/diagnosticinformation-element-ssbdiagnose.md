---
title: DiagnosticInformation 요소 (ssbdiagnose) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fcb4b883a9fed049e38cc98800ea9a244895cae3
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733572"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a>DiagnosticInformation 요소(ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **DiagnosticInformation** 요소에는  유틸리티가 발견한 진단 정보를 보고하는 모든 요소가 포함됩니다. **DiagnosticInformation** 은 **ssbdiagnostic** XML 출력 파일의 루트 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a>요소 특성  
  
|attribute|설명|  
|---------------|-----------------|  
|**없음**|해당 사항 없음|  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|**ssbdiagnose** XML 출력 파일당 한 번|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|없음|  
|**자식 요소**|[Banner 요소&#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)<br /><br /> [Issue 요소&#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a>Remarks  
 XML 네임스페이스에 대한 자세한 내용은 [MSDN Library의](https://go.microsoft.com/fwlink/?LinkId=7341) XML 문서의 네임스페이스 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 를 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [ssbdiagnose 유틸리티&#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
