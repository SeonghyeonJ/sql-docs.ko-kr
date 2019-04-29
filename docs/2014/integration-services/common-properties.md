---
title: 공용 속성 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- external metadata column properties [Integration Services]
- output properties [Integration Services]
- data types [Integration Services], properties
- input properties [Integration Services]
- component properties [Integration Services]
ms.assetid: 51973502-5cc6-4125-9fce-e60fa1b7b796
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ab92e158fe5da6312959cc0797ff48e1c44e0080
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62835230"
---
# <a name="common-properties"></a>공용 속성
   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델의 데이터 흐름 개체에는 구성 요소 수준, 입/출력 수준 및 입/출력 열 수준의 공통 속성과 사용자 지정 속성이 있습니다. 많은 속성은 데이터 흐름 엔진이 런타임에 할당하는 읽기 전용 값을 갖습니다.  
  
 이 항목에서는 데이터 흐름 개체의 공용 속성을 나열하고 설명합니다.  
  
-   [Components](#components)  
  
-   [입력](#inputs)  
  
-   [Input columns](#inputcolumns)  
  
-   [Outputs](#outputs)  
  
-   [출력 열](#outputcolumns)  
  
 사용자 지정 속성에 자세한 내용은 다음 항목을 참조하십시오.  
  
-   [ADO.NET 사용자 지정 속성](data-flow/ado-net-custom-properties.md)  
  
-   [CDC 제어 태스크 사용자 지정 속성](control-flow/cdc-control-task-custom-properties.md)  
  
-   [CDC 원본 사용자 지정 속성](data-flow/cdc-source-custom-properties.md)  
  
-   [데이터 마이닝 모델 학습 대상 사용자 지정 속성](data-flow/data-mining-model-training-destination-custom-properties.md)  
  
-   [DataReader 대상 사용자 지정 속성](data-flow/datareader-destination-custom-properties.md)  
  
-   [차원 처리 대상 사용자 지정 속성](data-flow/dimension-processing-destination-custom-properies.md)  
  
-   [Excel 사용자 지정 속성](data-flow/excel-custom-properties.md)  
  
-   [플랫 파일 사용자 지정 속성](data-flow/flat-file-custom-properties.md)  
  
-   [ODBC 대상 사용자 지정 속성](data-flow/odbc-destination-custom-properties.md)  
  
-   [ODBC 원본 사용자 지정 속성](data-flow/odbc-source-custom-properties.md)  
  
-   [OLE DB Custom Properties](data-flow/ole-db-custom-properties.md)OLE DB 사용자 지정 속성  
  
-   [파티션 처리 대상 사용자 지정 속성](data-flow/partition-processing-destination-custom-properties.md)  
  
-   [원시 파일 사용자 지정 속성](data-flow/raw-file-custom-properties.md)  
  
-   [레코드 집합 대상 사용자 지정 속성](data-flow/recordset-destination-custom-properties.md)  
  
-   [SQL Server Compact Edition 대상 사용자 지정 속성](data-flow/sql-server-compact-edition-destination-custom-properties.md)  
  
-   [SQL Server 대상 사용자 지정 속성](data-flow/sql-server-destination-custom-properties.md)  
  
-   [변환 사용자 지정 속성](data-flow/transformations/transformation-custom-properties.md)  
  
-   [XML 원본 사용자 지정 속성](data-flow/xml-source-custom-properties.md)  
  
##  <a name="components"></a> 구성 요소 속성  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 데이터 흐름의 구성 요소는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 인터페이스를 구현합니다.  
  
 다음 표에서는 데이터 흐름 구성 요소의 속성에 대해 설명합니다. 일부 속성에는 데이터 흐름 엔진이 런타임에 할당한 읽기 전용 값이 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|ComponentClassID|문자열|구성 요소의 CLSID입니다.|  
|ContactInfo|문자열|구성 요소 개발자의 연락처 정보입니다.|  
|Description|문자열|데이터 흐름 구성 요소에 대한 설명입니다. 이 속성의 기본값은 데이터 흐름 구성 요소의 이름입니다.|  
|ID|정수|구성 요소의 인스턴스를 고유하게 식별하는 값입니다.|  
|IdentificationString|문자열|구성 요소를 식별합니다.|  
|IsDefaultLocale|Boolean|구성 요소가 속해 있는 데이터 흐름 태스크의 로캘이 구성 요소에 사용되는지 여부를 나타냅니다.|  
|LocaleID|정수|패키지가 실행될 때 데이터 흐름 구성 요소에서 사용하는 로캘입니다. 데이터 흐름 구성 요소에는 모든 Windows 로캘을 사용할 수 있습니다.|  
|이름|문자열|데이터 흐름 구성 요소의 이름입니다.|  
|PipelineVersion|정수|구성 요소가 내부에서 실행되도록 디자인된 데이터 흐름 태스크의 버전입니다.|  
|UsesDispositions|Boolean|구성 요소에 오류 출력이 있는지 여부를 나타냅니다.|  
|ValidateExternalMetadata|Boolean|외부 열 메타데이터의 유효성이 검사되었는지 여부를 나타냅니다. 이 속성의 기본값은 `True`입니다.|  
|버전|정수|구성 요소의 버전입니다.|  
  
##  <a name="inputs"></a> 입력된 속성  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 변환 및 대상은 입력을 포함합니다. 데이터 흐름 구성 요소의 입력은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInput100> 인터페이스를 구현합니다.  
  
 다음 표에서는 데이터 흐름 구성 요소의 입력 속성에 대해 설명합니다. 일부 속성에는 데이터 흐름 엔진이 런타임에 할당한 읽기 전용 값이 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|Description|문자열|입력에 대한 설명입니다.|  
|ErrorOrTruncationOperation|문자열|행을 처리할 때 발생할 수 있는 오류 또는 잘림 유형을 지정하는 선택적 문자열입니다.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|오류 처리를 지정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다.|  
|HasSideEffects|Boolean|다운스트림 구성 요소에 연결 되지 않은 경우 데이터 흐름의 실행 계획에서 구성 요소를 제거할 수 있는지 여부를 나타냅니다 `RunInOptimizedMode` 는 `true`합니다.|  
|ID|정수|입력을 고유하게 식별하는 값입니다.|  
|IdentificationString|문자열|입력을 식별하는 문자열입니다.|  
|IsSorted|Boolean|입력의 데이터가 정렬되었는지 여부를 나타냅니다.|  
|이름|문자열|입력의 이름입니다.|  
|SourceLocale|정수|입력 데이터의 LCID(로캘 ID)입니다.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|행을 처리할 때 발생하는 잘림을 구성 요소가 처리하는 방법을 결정하는 값입니다. . 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다.|  
  
 대상 및 일부 변환은 오류 출력을 지원하지 않으므로 이러한 구성 요소의 ErrorRowDisposition 및 TruncationRowDisposition 속성은 읽기 전용입니다.  
  
###  <a name="inputcolumns"></a> 입력된 열 속성  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 입력은 입력 열 모음을 포함합니다. 데이터 흐름 구성 요소의 입력 열은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSInputColumn100> 인터페이스를 구현합니다.  
  
 다음 표에서는 데이터 흐름 구성 요소의 입력 열 속성에 대해 설명합니다. 일부 속성에는 데이터 흐름 엔진이 런타임에 할당한 읽기 전용 값이 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|ComparisonFlags|정수|문자 데이터 형식을 갖는 열의 비교를 지정하는 플래그 집합입니다. 자세한 내용은 [Comparing String Data](data-flow/comparing-string-data.md)을(를) 참조하세요.|  
|Description|문자열|입력 열에 대해 설명합니다.|  
|ErrorOrTruncationOperation|문자열|행을 처리할 때 발생할 수 있는 오류 또는 잘림 유형을 지정하는 선택적 문자열입니다.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|오류 처리를 지정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다.|  
|ExternalMetadataColumnID|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100>|입력 열에 할당된 외부 메타데이터 열의 ID입니다.|  
|ID|정수|입력 열을 고유하게 식별하는 값입니다.|  
|IdentificationString|문자열|입력 열을 식별하는 문자열입니다.|  
|LineageID|정수|업스트림 열의 ID입니다.|  
|이름|문자열|입력 열의 이름입니다.|  
|SortKeyPosition|정수|열 정렬 여부, 정렬 순서 및 여러 열이 정렬되는 순서를 나타내는 값입니다. 값 **0** 은 열이 정렬되어 있지 않음을 나타냅니다.  자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|행을 처리할 때 발생하는 잘림을 구성 요소가 처리하는 방법을 결정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다.|  
|UpstreamComponentName|문자열|업스트림 구성 요소의 이름입니다.|  
|UsageType|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType>|입력 열이 구성 요소에서 사용되는 방식을 결정하는 값입니다.|  
  
 입력 열은 "데이터 형식 속성"에 설명된 데이터 형식 속성도 포함합니다.  
  
##  <a name="outputs"></a> 출력 속성  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 원본 및 변환은 출력을 포함합니다. 데이터 흐름 구성 요소의 출력은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> 인터페이스를 구현합니다.  
  
 다음 표에서는 데이터 흐름 구성 요소의 출력 속성에 대해 설명합니다. 일부 속성에는 데이터 흐름 엔진이 런타임에 할당한 읽기 전용 값이 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|DeleteOutputOnPathDetached|Boolean|경로에서 출력이 분리될 경우 데이터 흐름 엔진이 출력을 삭제할지 여부를 결정하는 값입니다.|  
|Description|문자열|출력에 대해 설명합니다.|  
|ErrorOrTruncationOperation|문자열|행을 처리할 때 발생할 수 있는 오류 또는 잘림 유형을 지정하는 선택적 문자열입니다.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|오류 처리를 지정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다.|  
|ExclusionGroup|정수|함께 사용할 수 없는 출력 그룹을 식별하는 값입니다.|  
|HasSideEffects|Boolean|구성 요소가 업스트림 구성 요소에 연결되어 있지 않은 경우 및 `RunInOptimizedMode`가 `true`일 경우 데이터 흐름의 실행 계획에서 구성 요소를 제거할 수 있는지 여부를 나타내는 값입니다.|  
|ID|정수|출력을 고유하게 식별하는 값입니다.|  
|IdentificationString|문자열|출력을 식별하는 문자열입니다.|  
|IsErrorOut|Boolean|출력이 오류 출력인지 여부를 나타냅니다.|  
|IsSorted|Boolean|출력이 정렬되었는지 여부를 나타냅니다. 기본값은 `False`입니다.<br /><br /> **\*\* 중요 \* \***  의 값을 설정 합니다 `IsSorted` 속성을 `True` 해도 데이터가 정렬 되지는 않습니다. 이 속성은 데이터가 이전에 정렬되었다는 정보를 다운스트림 구성 요소에 제공하기만 합니다. 자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.|  
|이름|문자열|출력의 이름입니다.|  
|SynchronousInputID|정수|출력과 동시에 수행되는 입력의 ID입니다.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|행을 처리할 때 발생하는 잘림을 구성 요소가 처리하는 방법을 결정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다.|  
  
###  <a name="outputcolumns"></a> 출력 열 속성  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 출력은 출력 열 모음을 포함합니다. 데이터 흐름 구성 요소의 출력 열은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100> 인터페이스를 구현합니다.  
  
 다음 표에서는 데이터 흐름 구성 요소의 출력 열 속성에 대해 설명합니다. 일부 속성에는 데이터 흐름 엔진이 런타임에 할당한 읽기 전용 값이 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|ComparisonFlags|정수|문자 데이터 형식을 갖는 열의 비교를 지정하는 플래그 집합입니다. 자세한 내용은 [Comparing String Data](data-flow/comparing-string-data.md)을(를) 참조하세요.|  
|Description|문자열|출력 열에 대해 설명합니다.|  
|ErrorOrTruncationOperation|문자열|행을 처리할 때 발생할 수 있는 오류 또는 잘림 유형을 지정하는 선택적 문자열입니다.|  
|ErrorRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|오류 처리를 지정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다. 기본값은 `Fail component`입니다.|  
|ExternalMetadataColumnID|정수|입력 열에 할당된 외부 메타데이터 열의 ID입니다.|  
|ID|정수|출력 열을 고유하게 식별하는 값입니다.|  
|IdentificationString|문자열|출력 열을 식별하는 문자열입니다.|  
|LineageID|정수|출력 열의 ID입니다. 다운스트림 구성 요소는 이 값을 사용하여 열을 참조합니다.|  
|이름|문자열|출력 열의 이름입니다.|  
|SortKeyPosition|정수|열 정렬 여부, 정렬 순서 및 여러 열이 정렬되는 순서를 나타내는 값입니다. 값 **0** 은 열이 정렬되어 있지 않음을 나타냅니다. 자세한 내용은 [병합 및 병합 조인 변환을 위한 데이터 정렬](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)을 참조하세요.|  
|SpecialFlags|정수|출력 열의 특수 플래그를 포함하는 값입니다.|  
|TruncationRowDisposition|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSRowDisposition>|행을 처리할 때 발생하는 잘림을 구성 요소가 처리하는 방법을 결정하는 값입니다. 가능한 값은 `Fail component`, `Ignore failure` 및 `Redirect row`입니다. 기본값은 `Fail component`입니다.|  
  
 출력 열은 데이터 형식 속성 집합도 포함합니다.  
  
## <a name="external-metadata-column-properties"></a>외부 메타데이터 열 속성  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 개체 모델에서 입력 및 출력은 외부 메타데이터 열 모음을 포함할 수 있습니다. 데이터 흐름 구성 요소의 외부 메타데이터 열은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumn100> 인터페이스를 구현합니다.  
  
 다음 표에서는 데이터 흐름 구성 요소의 외부 메타데이터 열 속성에 대해 설명합니다. 일부 속성에는 데이터 흐름 엔진이 런타임에 할당한 읽기 전용 값이 있습니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|Description|문자열|외부 열에 대해 설명합니다.|  
|ID|정수|열을 고유하게 식별하는 값입니다.|  
|IdentificationString|문자열|열을 식별하는 문자열입니다.|  
|이름|문자열|외부 열의 이름입니다.|  
  
 외부 메타데이터 열은 데이터 형식 속성 집합도 포함합니다.  
  
## <a name="data-type-properties"></a>데이터 형식 속성  
 출력 열과 외부 메타데이터 열은 데이터 형식 속성 집합을 포함합니다. 열의 데이터 형식에 따라 읽기/쓰기 속성 또는 읽기 전용 속성이 될 수 있습니다.  
  
 다음 표에서는 출력 열 및 외부 메타데이터 열의 데이터 형식 속성에 대해 설명합니다.  
  
|속성|데이터 형식|Description|  
|--------------|---------------|-----------------|  
|CodePage|정수|유니코드가 아닌 문자열 데이터에 대한 코드 페이지를 지정합니다.|  
|DataType|Integer(열거형)|열의 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 데이터 형식입니다. 자세한 내용은 [Integration Services Data Types](data-flow/integration-services-data-types.md)을 참조하세요.|  
|길이|정수|열의 길이(문자 수)입니다.|  
|전체 자릿수|정수|숫자 열의 전체 자릿수입니다.|  
|소수 자릿수|정수|숫자 열의 소수 자릿수입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [데이터 흐름](data-flow/data-flow.md)   
 [변환 사용자 지정 속성](data-flow/transformations/transformation-custom-properties.md)   
 [경로 속성](../../2014/integration-services/path-properties.md)   
 [식을 사용하여 설정할 수 있는 데이터 흐름 속성](../../2014/integration-services/data-flow-properties-that-can-be-set-by-using-expressions.md)  
  
  
