---
title: DataTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataTypeEnum
helpviewer_keywords:
- DataTypeEnum enumeration [ADO]
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc18212852954accfddd9f3082b5c8f8a5485b58
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140280"
---
# <a name="datatypeenum"></a>DataTypeEnum
데이터 형식을 지정 된 [필드](../../../ado/reference/ado-api/field-object.md), [매개 변수](../../../ado/reference/ado-api/parameter-object.md), 또는 [속성](../../../ado/reference/ado-api/property-object-ado.md). 해당 OLE DB 유형 표시기는 다음 표의 설명 열에 대 한 괄호 안에 표시 됩니다.  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**AdArray**|0x2000|다른 데이터 형식의 배열을 지정 하는 다른 데이터 형식 상수를 항상 함께 플래그 값입니다. ADOX에 적용 되지 않습니다.|  
|**adBigInt**|20|8 바이트 부호 있는 정수 (DBTYPE_I8)를 나타냅니다.|  
|**adBinary**|128|이진 값 (DBTYPE_BYTES)을 나타냅니다.|  
|**adBoolean**|11|나타냅니다는 **부울** 값 (DBTYPE_BOOL)입니다.|  
|**adBSTR**|8|Null로 끝나는 문자열 (DBTYPE_BSTR) (유니코드)을 나타냅니다.|  
|**adChapter**|136|자식 행 집합 (DBTYPE_HCHAPTER)의 행을 식별 하는 4 바이트 장 값을 나타냅니다.|  
|**adChar**|129|문자열 값 (DBTYPE_STR)을 나타냅니다.|  
|**adCurrency**|6|통화 값 (DBTYPE_CY)을 나타냅니다. 통화는 소수점 오른쪽 4 자리 고정 소수점 숫자입니다. 10,000 단위 배율의 8 바이트 부호 있는 정수로 저장 됩니다.|  
|**adDate**|7|날짜 값 (DBTYPE_DATE)을 나타냅니다. 날짜의 정수 부분은 1899 년 12 월 30 한 일 수는 및의 소수 부분은 하루를 분수로 double 형식으로 저장 됩니다.|  
|**adDBDate**|133|날짜 (yyyymmdd) (DBTYPE_DBDATE) 값을 나타냅니다.|  
|**adDBTime**|134|시간 값 (hhmmss) (DBTYPE_DBTIME)을 나타냅니다.|  
|**adDBTimeStamp**|135|날짜/시간 스탬프 (yyyymmddhhmmss 더하기 billionths의 비율)을 나타냅니다 (DBTYPE_DBTIMESTAMP)입니다.|  
|**adDecimal**|14|정밀도 배율이 고정 (DBTYPE_DECIMAL)을 사용 하 여 정확한 숫자 값을 나타냅니다.|  
|**adDouble**|5|배정밀도 부동 소수점 값 (DBTYPE_R8)을 나타냅니다.|  
|**adEmpty**|0|값 (DBTYPE_EMPTY)을 지정합니다.|  
|**adError**|10|32 비트 오류 코드 (DBTYPE_ERROR)를 나타냅니다.|  
|**adFileTime**|64|(DBTYPE_FILETIME) 1601 년 1 월 1 일 이후 100 나노초 간격의 수를 나타내는 64 비트 값을 나타냅니다.|  
|**adGUID**|72|전역적으로 고유 식별자 (GUID) (DBTYPE_GUID)를 나타냅니다.|  
|**adIDispatch**|9|에 대 한 포인터를 나타냅니다는 **IDispatch** COM 개체 (DBTYPE_IDISPATCH)의 인터페이스입니다.<br /><br /> **참고** 이 데이터 형식은 현재 ADO에서 지원 되지 않습니다. 사용 하면 예기치 않은 결과가 발생할 수 있습니다.|  
|**adInteger**|3|4 바이트 부호 있는 정수 (DBTYPE_I4)를 나타냅니다.|  
|**adIUnknown**|13|에 대 한 포인터를 나타냅니다는 **IUnknown** COM 개체 (DBTYPE_IUNKNOWN)의 인터페이스입니다.<br /><br /> **참고** 이 데이터 형식은 현재 ADO에서 지원 되지 않습니다. 사용 하면 예기치 않은 결과가 발생할 수 있습니다.|  
|**adLongVarBinary**|205|긴 이진 값을 나타냅니다.|  
|**adLongVarChar**|201|긴 문자열 값을 나타냅니다.|  
|**adLongVarWChar**|203|긴 null로 끝나는 유니코드 문자열 값을 나타냅니다.|  
|**adNumeric**|131|정밀도 배율이 고정 (DBTYPE_NUMERIC)를 사용 하 여 정확한 숫자 값을 나타냅니다.|  
|**adPropVariant**|138|자동화 PROPVARIANT (DBTYPE_PROP_VARIANT)를 나타냅니다.|  
|**adSingle**|4|단 정밀도 부동 소수점 값 (DBTYPE_R4)을 나타냅니다.|  
|**adSmallInt**|2|2 바이트 부호 있는 정수 (DBTYPE_I2)를 나타냅니다.|  
|**adTinyInt**|16|1 바이트 부호 있는 정수 (DBTYPE_I1)를 나타냅니다.|  
|**adUnsignedBigInt**|21|8 바이트 부호 없는 정수 (DBTYPE_UI8)를 나타냅니다.|  
|**adUnsignedInt**|19|4 바이트 부호 없는 정수 (DBTYPE_UI4)를 나타냅니다.|  
|**adUnsignedSmallInt**|18|2 바이트 부호 없는 정수 (DBTYPE_UI2)를 나타냅니다.|  
|**adUnsignedTinyInt**|17|1 바이트 부호 없는 정수 (DBTYPE_UI1)를 나타냅니다.|  
|**adUserDefined**|132|사용자 정의 변수 (DBTYPE_UDT)를 나타냅니다.|  
|**adVarBinary**|204|이진 값을 나타냅니다.|  
|**adVarChar**|200|문자열 값을 나타냅니다.|  
|**adVariant**|12|Automation 나타냅니다 **Variant** (DBTYPE_VARIANT)입니다.<br /><br /> **참고** 이 데이터 형식은 현재 ADO에서 지원 되지 않습니다. 사용 하면 예기치 않은 결과가 발생할 수 있습니다.|  
|**adVarNumeric**|139|숫자 값을 나타냅니다.|  
|**adVarWChar**|202|Null로 끝나는 유니코드 문자열을 나타냅니다.|  
|**adWChar**|130|Null로 끝나는 유니코드 문자열 (DBTYPE_WSTR)을 나타냅니다.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 해당  
 Package: **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.DataType.ARRAY|  
|AdoEnums.DataType.BIGINT|  
|AdoEnums.DataType.BINARY|  
|AdoEnums.DataType.BOOLEAN|  
|AdoEnums.DataType.BSTR|  
|AdoEnums.DataType.CHAPTER|  
|AdoEnums.DataType.CHAR|  
|AdoEnums.DataType.CURRENCY|  
|AdoEnums.DataType.DATE|  
|AdoEnums.DataType.DBDATE|  
|AdoEnums.DataType.DBTIME|  
|AdoEnums.DataType.DBTIMESTAMP|  
|AdoEnums.DataType.DECIMAL|  
|AdoEnums.DataType.DOUBLE|  
|AdoEnums.DataType.EMPTY|  
|AdoEnums.DataType.ERROR|  
|AdoEnums.DataType.FILETIME|  
|AdoEnums.DataType.GUID|  
|AdoEnums.DataType.IDISPATCH|  
|AdoEnums.DataType.INTEGER|  
|AdoEnums.DataType.IUNKNOWN|  
|AdoEnums.DataType.LONGVARBINARY|  
|AdoEnums.DataType.LONGVARCHAR|  
|AdoEnums.DataType.LONGVARWCHAR|  
|AdoEnums.DataType.NUMERIC|  
|AdoEnums.DataType.PROPVARIANT|  
|AdoEnums.DataType.SINGLE|  
|AdoEnums.DataType.SMALLINT|  
|AdoEnums.DataType.TINYINT|  
|AdoEnums.DataType.UNSIGNEDBIGINT|  
|AdoEnums.DataType.UNSIGNEDINT|  
|AdoEnums.DataType.UNSIGNEDSMALLINT|  
|AdoEnums.DataType.UNSIGNEDTINYINT|  
|AdoEnums.DataType.USERDEFINED|  
|AdoEnums.DataType.VARBINARY|  
|AdoEnums.DataType.VARCHAR|  
|AdoEnums.DataType.VARIANT|  
|AdoEnums.DataType.VARNUMERIC|  
|AdoEnums.DataType.VARWCHAR|  
|AdoEnums.DataType.WCHAR|  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[Append 메서드(ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[CreateParameter 메서드(ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|  
|[CreateRecordset 메서드(RDS)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|[Type 속성(ADO)](../../../ado/reference/ado-api/type-property-ado.md)|
