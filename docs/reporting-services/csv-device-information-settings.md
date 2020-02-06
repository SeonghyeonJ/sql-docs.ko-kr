---
title: CSV 디바이스 정보 설정 | Microsoft Docs
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- CSV [Reporting Services]
- device information settings [Reporting Services], CSV rendering
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 9423f82e025146773c5d04a276cf15c76c6b1101
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "65571604"
---
# <a name="csv-device-information-settings"></a>CSV 디바이스 정보 설정
  CSV 렌더링 확장 프로그램에 대한 디바이스 정보 설정을 통해 구분 기호 및 한정자를 변경하고 줄 바꿈 처리를 지정할 수 있습니다. 출력에 파일 확장명과 인코딩 및 머리글 행도 포함하여 제출할 수 있습니다. 구분 기호는 특수 문자일 수 있기 때문에 설정이 XML로 작성된 경우 CDATA 섹션에서 인코딩해야 합니다.  
  
 다음 표는 텍스트 형식으로 렌더링하기 위한 디바이스 정보 설정을 나열합니다.  
  
|설정|값|  
|-------------|-----------|  
|**인코딩**|.NET Framework에서 지원하는 문자 인코딩의 IANA(Internet Assigned Numbers Authority) 이름입니다. 기본값은 **UTF-8**입니다. 다른 값의 예로 ASCII, UTF-7 및 UTF-16을 들 수 있습니다.|  
|**ExcelMode**|대상 출력이 Excel용임을 지정합니다. 기본값은 **true**입니다.|  
|**FieldDelimiter**|결과에서 사용할 구분 기호 문자열입니다. 기본값은 쉼표(,)입니다. 이 디바이스 정보의 값을 URL에 전달할 경우 URL 인코딩을 수행해야 합니다. 예를 들어 구분 기호인 탭 문자는 "%09"가 되어야 합니다.<br /><br /> 구성 파일에서 디바이스 정보 설정을 변경하여 기본 필드 구분 기호를 TAB을 비롯한 임의의 문자로 변경할 수 있습니다. 예를 들어 TAB을 사용하려면 FieldDelimiter 설정을 \<FieldDelimiter xml:space="preserve">[TAB]\</FieldDelimiter>로 업데이트합니다.<br /><br /> 이 예제에서 [TAB]은 실제 탭 문자이므로 구성 파일에는 공백으로 나타납니다. "xml:space" 특성은 공백을 보존하도록 파서에 지시합니다.|  
|**FileExtension**|결과에서 사용할 파일 확장명입니다. 기본값은 **.CSV**입니다. **FileExtension** 과 **Extension** 이 모두 지정되는 경우 **FileExtension** 이 우선합니다.|  
|**NoHeader**|머리글 행이 출력에서 제외되는지 여부를 나타냅니다. 기본 값은 **false**입니다.|  
|**한정자**|필드 구분 기호 또는 레코드 구분 기호를 포함하는 결과 주위에 사용할 한정자 문자열입니다. 결과에 한정자가 포함되어 있을 경우 해당 한정자가 반복됩니다. **Qualifier** 설정은 **FieldDelimiter** 및 **RecordDelimiter** 설정과 달라야 합니다. 기본값은 따옴표(")입니다.|  
|**RecordDelimiter**|각 레코드의 마지막에 사용할 레코드 구분 기호입니다. 기본값은 \<cr>\<lf>입니다.|  
|**SuppressLineBreaks**|출력에 포함된 데이터에서 줄 바꿈이 제거되는지 여부를 나타냅니다. 기본 값은 **false**입니다. 값이 **true**이면 **FieldDelimiter**, **RecordDelimiter**및 **Qualifier** 설정은 공백 문자가 될 수 없습니다.|  
|**UseFormattedValues**|서식 있는 문자열을 CSV 출력에 사용할지 여부를 나타냅니다. **true** 가 **ExcelMode** 인 경우 기본값은 **true**이고, 그렇지 않은 경우 **false**입니다.|  
  
## <a name="see-also"></a>참고 항목  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [디바이스 정보 설정을 렌더링 확장 프로그램에 전달](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config의 렌더링 확장 프로그램 매개 변수를 사용자 지정](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [기술 참조&#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
