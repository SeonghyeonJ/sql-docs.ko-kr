---
title: bcp_getcolfmt | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_getcolfmt
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 40e7f63438bbe6ff68284aa573e1307b17087234
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71707541"
---
# <a name="bcp_getcolfmt"></a>bcp_getcolfmt
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  열 형식 속성 값을 찾는 데 사용됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
RETCODE bcp_getcolfmt (  
        HDBC hdbc,  
        INT field,  
        INT property,  
        void* pValue,  
        INT cbvalue,  
        INT* pcbLen);  
```  
  
## <a name="arguments"></a>인수  
 *hdbc*  
 대량 복사가 가능한 ODBC 연결 핸들입니다.  
  
 *field*  
 속성을 검색할 열 번호입니다.  
  
 *속성*  
 속성 상수 중 하나입니다.  
  
 *pValue*  
 검색할 속성 값이 있는 버퍼에 대한 포인터입니다.  
  
 *cbValue*  
 속성 버퍼의 길이(바이트)입니다.  
  
 *pcbLen*  
 속성 버퍼에서 반환되는 데이터의 길이에 대한 포인터입니다.  
  
## <a name="returns"></a>반환 값  
 SUCCEED 또는 FAIL  
  
## <a name="remarks"></a>설명  
 열 형식 속성 값은 [bcp_setcolfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-setcolfmt.md) 항목에 나와 있습니다. 열 형식 속성 값은 **bcp_setcolfmt** 함수를 호출하여 설정되고 **bcp_getcolfmt** 함수는 열 형식 속성 값을 찾는 데 사용됩니다.  
  
 이전 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 버전과 비교해서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이상 버전의 서버 컴퓨터에 연결할 때 동작 변경 내용이 관찰될 수 있습니다. 자세한 내용은 [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md)를 참조하십시오.  
  
## <a name="bcp_getcolfmt-support-for-enhanced-date-and-time-features"></a>향상된 날짜 및 시간 기능에 대한 bcp_getcolfmt 지원  
 날짜/시간 형식에 대 한 **BCP_FMT_TYPE** 속성과 함께 사용 되는 형식은 향상 된 [날짜 및 시간 &#40;형식 OLE DB 및 ODBC&#41;에 대해 대량 복사 변경 내용](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)에 지정 되어 있습니다.  
  
 자세한 내용은 [ODBC&#41;의 날짜 및 시간 기능 향상 &#40;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [대량 복사 함수](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
