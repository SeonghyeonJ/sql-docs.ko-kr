---
title: SSVARIANT 구조 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff6e37986378a66d94dc113c4e3fe072fe3c077f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63062501"
---
# <a name="ssvariant-structure"></a>SSVARIANT 구조
  sqlncli.h에 정의되어 있는 `SSVARIANT` 구조는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB 공급자의 DBTYPE_SQLVARIANT 값에 해당합니다.  
  
 
  `SSVARIANT`는 판별 구조체입니다. vt 멤버의 값에 따라 소비자는 읽을 멤버를 결정할 수 있습니다. vt 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 해당하므로 
  `SSVARIANT` 구조는 모든 SQL Server 형식을 보유할 수 있습니다. 표준 OLE DB 형식에 대 한 데이터 구조에 대 한 자세한 내용은 [형식 표시기](https://go.microsoft.com/fwlink/?LinkId=122171)를 참조 하세요.  
  
## <a name="remarks"></a>설명  
 DataTypeCompat==80인 경우, 여러 `SSVARIANT` 하위 유형이 문자열이 됩니다. 예를 들면 다음 vt 값이 `SSVARIANT`에 VT_SS_WVARSTRING으로 나타납니다.  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 DateTypeCompat == 0인 경우, 이러한 유형은 네이티브 형식으로 나타납니다.  
  
 SSPROP_INIT_DATATYPECOMPATIBILITY에 대 한 자세한 내용은 [SQL Server Native Client 연결 문자열 키워드 사용](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)을 참조 하세요.  
  
 sqlncli.h 파일에는 `SSVARIANT` 구조에서 멤버 유형 역참조를 단순화하는 변형 액세스 매크로가 있습니다. 예로는 다음과 같이 사용 가능한 V_SS_DATETIMEOFFSET가 있습니다.  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 
  `SSVARIANT` 구조의 각 멤버에 대한 액세스 매크로 전체 집합은 sqlncli.hi 파일을 참조하십시오.  
  
 다음 표에서는 `SSVARIANT` 구조의 멤버를 설명합니다.  
  
|멤버|OLE DB 유형 표시기|OLE DB C 데이터 형식|vt 값|주석|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||
  `SSVARIANT` 구조에 포함된 값 유형을 지정합니다.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|
  `tinyint`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|
  `smallint`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|
  `int`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|
  `bigint`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|
  `real`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|
  `float`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|는 `money` 및 **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원 합니다.|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|
  `bit`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|
  `uniqueidentifier`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|
  `numeric`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|
  `date`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|
  `smalldatetime`, `datetime`, 및 `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|
  `time`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tTime2Val* (`DBTIME2`)<br /><br /> *bscale* (`BYTE`)은 *tTime2Val* 값에 대 한 소수 자릿수를 지정 합니다.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|
  `datetime2`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tsDataTimeVal* (dbtimestamp)<br /><br /> *bscale* (`BYTE`)은 *tsDataTimeVal* 값에 대 한 소수 자릿수를 지정 합니다.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|
  `datetimeoffset`
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)<br /><br /> *bscale* (`BYTE`)은 *tsoDateTimeOffsetVal* 값에 대 한 소수 자릿수를 지정 합니다.|  
|NCharVal|해당하는 OLE DB 유형 표시기 없음|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|는 `nchar` 및 **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원 합니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (`SHORT`)은 *pwchNCharVal* 가 가리키는 문자열의 실제 길이를 지정 합니다. 이 값은 0으로 끝나지 않습니다.<br /><br /> *smaxlength* (`SHORT`)는 *pwchNCharVal* 가 가리키는 문자열의 최대 길이를 지정 합니다.<br /><br /> 문자열에`WCHAR` \*대 한 *pwchNCharVal* () 포인터입니다.<br /><br /> 사용 되지 않는 멤버: *rgbReserved*, *Dwreserved*및 *pwchReserved*.|  
|CharVal|해당하는 OLE DB 유형 표시기 없음|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|는 `char` 및 **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원 합니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (`SHORT`)은 *pchcharval* 이 가리키는 문자열의 실제 길이를 지정 합니다. 이 값은 0으로 끝나지 않습니다.<br /><br /> *smaxlength* (`SHORT`)는 *pchcharval* 이 가리키는 문자열의 최대 길이를 지정 합니다.<br /><br /> 문자열에 대 한 *pchcharval* (`CHAR` \*) 포인터입니다.<br /><br /> 사용되지 않은 멤버:<br /><br /> *rgbReserved*, *Dwreserved*및 *pwchReserved*입니다.|  
|BinaryVal|해당하는 OLE DB 유형 표시기 없음|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|는 `binary` 및 **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원 합니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (`SHORT`)는 *prgbbinaryval* 이 가리키는 데이터의 실제 길이를 지정 합니다.<br /><br /> *smaxlength* (`SHORT`)는 *prgbbinaryval* 이 가리키는 데이터의 최대 길이를 지정 합니다.<br /><br /> 이진 데이터에 대 한`BYTE` \* *prgbbinaryval* () 포인터입니다.<br /><br /> 사용 되지 않는 멤버: *Dwreserved*.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>참고 항목  
 [데이터 형식 &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
