---
title: SSVARIANT 구조 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3dffb546620f7a67f3dc8502d7a8e8b389d9ae7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128488"
---
# <a name="ssvariant-structure"></a>SSVARIANT 구조
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  합니다 **SSVARIANT** DBTYPE_SQLVARIANT 값에 해당 하는 sqlncli.h에 정의 된 구조는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLEDB 공급자입니다.  
  
 **SSVARIANT** 는 판별 구조체입니다. vt 멤버의 값에 따라 소비자는 읽을 멤버를 결정할 수 있습니다. vt 값은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식에 해당하므로 **SSVARIANT** 구조는 모든 SQL Server 형식을 보유할 수 있습니다. 표준 OLE DB 형식에 대 한 데이터 구조에 대 한 자세한 내용은 참조 하세요. [유형 표시기](https://go.microsoft.com/fwlink/?LinkId=122171)합니다.  
  
## <a name="remarks"></a>설명  
 DataTypeCompat==80인 경우, 여러 **SSVARIANT** 하위 유형이 문자열이 됩니다. 예를 들면 다음 vt 값이 **SSVARIANT**에 VT_SS_WVARSTRING으로 나타납니다.  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 DateTypeCompat == 0인 경우, 이러한 유형은 네이티브 형식으로 나타납니다.  
  
 SSPROP_INIT_DATATYPECOMPATIBILITY에 대 한 자세한 내용은 참조 하세요. [SQL Server Native Client를 사용 하 여 연결 문자열 키워드를 사용 하 여](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)입니다.  
  
 Sqlncli.h 파일에서 멤버 유형 역참조를 단순화 하는 변형 액세스 매크로가 포함 된 **SSVARIANT** 구조입니다. 예로는 다음과 같이 사용 가능한 V_SS_DATETIMEOFFSET가 있습니다.  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 각 멤버에 대 한 액세스 매크로 전체 집합에 대 한 합니다 **SSVARIANT** 구조체은 sqlncli.hi 파일을 참조 하세요.  
  
 다음 표에서는 **SSVARIANT** 구조의 멤버를 설명합니다.  
  
|멤버|OLE DB 유형 표시기|OLE DB C 데이터 형식|vt 값|주석|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||**SSVARIANT** 구조에 포함된 값 유형을 지정합니다.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|지원 합니다 **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|지원 합니다 **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|지원 합니다 **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|지원 합니다 **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|지원 합니다 **실제** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|지원 합니다 **부동 소수점** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|지원 합니다 **money** 하 고 **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|지원 합니다 **비트** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|지원 합니다 **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|지원 합니다 **숫자** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|**date**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식을 지원합니다.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|지원 합니다 **smalldatetime**를 **datetime**, 및 **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|지원 합니다 **시간** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**바이트**)에 대 한 소수 자릿수를 지정 *tTime2Val* 값입니다.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|지원 합니다 **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**바이트**)에 대 한 소수 자릿수를 지정 *tsDataTimeVal* 값입니다.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|지원 합니다 **datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**바이트**)에 대 한 소수 자릿수를 지정 *tsoDateTimeOffsetVal* 값입니다.|  
|NCharVal|해당하는 OLE DB 유형 표시기 없음|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|지원 합니다 **nchar** 하 고 **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (**짧은**)는 문자열에 대 한 실제 길이 지정 *pwchNCharVal* 지점입니다. 이 값은 0으로 끝나지 않습니다.<br /><br /> *sMaxLength* (**짧은**)는 문자열에 대 한 최대 길이 지정 *pwchNCharVal* 지점입니다.<br /><br /> *pwchNCharVal* (**WCHAR** \*) 문자열에 대 한 포인터입니다.<br /><br /> 사용 되지 않은 멤버: *rgbReserved*를 *dwReserved*, 및 *pwchReserved*합니다.|  
|CharVal|해당하는 OLE DB 유형 표시기 없음|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|지원 합니다 **char** 하 고 **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (**짧은**)는 문자열에 대 한 실제 길이 지정 *pchCharVal* 지점입니다. 이 값은 0으로 끝나지 않습니다.<br /><br /> *sMaxLength* (**짧은**)는 문자열에 대 한 최대 길이 지정 *pchCharVal* 지점입니다.<br /><br /> *pchCharVal* (**CHAR** \*) 문자열에 대 한 포인터입니다.<br /><br /> 사용되지 않은 멤버:<br /><br /> *rgbReserved*하십시오 *dwReserved*, 및 *pwchReserved*합니다.|  
|BinaryVal|해당하는 OLE DB 유형 표시기 없음|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|지원 합니다 **이진** 하 고 **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식입니다.<br /><br /> 포함되는 멤버는 다음과 같습니다.<br /><br /> *sActualLength* (**짧은**)는 데이터에 대 한 실제 길이 지정 *prgbBinaryVal* 지점입니다.<br /><br /> *sMaxLength* (**짧은**)는 데이터에 대 한 최대 길이 지정 *prgbBinaryVal* 지점입니다.<br /><br /> *prgbBinaryVal* (**바이트** \*) 이진 데이터에 대 한 포인터입니다.<br /><br /> 사용 되지 않은 멤버: *dwReserved*합니다.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>관련 항목  
 [데이터 형식 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  
