---
title: Microsoft OLE DB Provider for Microsoft Jet | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet provider for OLE DB [ADO]
- providers [ADO], OLE DB provider for Microsoft Jet
- OLE DB provider for Microsoft Jet [ADO]
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 986c1bf7f604f531180a14a4456325ce01702b94
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62855496"
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Microsoft OLE DB Provider for Microsoft Jet 개요
OLE DB Provider for Microsoft Jet ADO를 Microsoft Jet 데이터베이스에 액세스할 수 있습니다.

## <a name="connection-string-parameters"></a>연결 문자열 매개 변수
 이 공급자에 연결을 설정 합니다 *공급자* 인수를 [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) 속성을 다음:

```vb
Microsoft.Jet.OLEDB.4.0
```

 읽기를 [공급자](../../../ado/reference/ado-api/provider-property-ado.md) 이 문자열도 반환 됩니다.

## <a name="typical-connection-string"></a>일반적인 연결 문자열
 이 공급자에 대 한 일반적인 연결 문자열은:

```vb
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 문자열을 이러한 키워드 이루어져 있습니다.

|키워드|설명|
|-------------|-----------------|
|**공급자**|Microsoft Jet 용 OLE DB 공급자를 지정합니다.|
|**데이터 원본**|데이터베이스 경로 파일 이름을 지정 합니다 (예를 들어 `c:\Northwind.mdb`).|
|**사용자 ID**|사용자 이름을 지정합니다. 이 키워드는 지정 하지 않으면 문자열 "`admin`", 기본적으로 사용 됩니다.|
|**암호**|사용자 암호를 지정 합니다. 이 키워드는 지정 하지 않으면 빈 문자열 ("")를 기본적으로 사용 됩니다.|

> [!NOTE]
>  지정 해야 하는 경우 Windows 인증을 지 원하는 데이터 원본 공급자에 연결 하는, **Trusted_Connection = yes** 하거나 **Integrated Security = SSPI** 사용자 ID와 암호 대신 연결 문자열에 대 한 정보입니다.

## <a name="provider-specific-connection-parameters"></a>공급자별 연결 매개 변수
 OLE DB Provider for Microsoft Jet ADO에서 정의 된 것 외에도 여러 공급자별 동적 속성을 지원 합니다. 다른 모든와 마찬가지로 **연결** 매개 변수를 설정할 수 있습니다 사용 하 여 합니다 **속성** 의 컬렉션을 **연결** 개체 또는 연결 문자열의 일부로.

 다음 표에서 해당 OLE DB 속성 이름 괄호로 함께 이러한 속성을 나열합니다.

|매개 변수|Description|
|---------------|-----------------|
|Jet OLEDB:Compact 회수 공간 크기 (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|예상 (바이트)를 데이터베이스를 압축 하 여 회수 될 수 있는 공간의 양 나타냅니다. 이 값은 데이터베이스 연결을 설정한 후에 유효 합니다.|
|Jet OLEDB:Connection 컨트롤 (DBPROP_JETOLEDB_CONNECTIONCONTROL)|사용자는 데이터베이스에 연결할 수 있는지 여부를 나타냅니다.|
|Jet OLEDB: 시스템 데이터베이스 (DBPROP_JETOLEDB_CREATESYSTEMDATABASE) 만들기|새 데이터 원본을 만들 때 시스템 데이터베이스를 만들어야 하는지 여부를 나타냅니다.|
|Jet oledb: database 잠금 모드 (DBPROP_JETOLEDB_DATABASELOCKMODE)|이 데이터베이스에 대 한 잠금 모드를 나타냅니다. 첫 번째 사용자 데이터베이스를 열 데이터베이스 열려 있는 동안 사용 되는 모드를 결정 합니다.|
|Jet oledb: database Password (DBPROP_JETOLEDB_DATABASEPASSWORD)|데이터베이스 암호를 나타냅니다.|
|Jet OLEDB: Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)에서 로캘을 복사 안 함|Jet 데이터베이스를 압축할 경우 로캘 정보를 복사 해야 하는지 여부를 나타냅니다.|
|Jet OLEDB: Database (DBPROP_JETOLEDB_ENCRYPTDATABASE)를 암호화 합니다.|압축된 된 데이터베이스를 암호화 해야 하는지 여부를 나타냅니다. 이 속성을 설정 하지 않으면 원래 데이터베이스를 암호화 하는 경우 압축된 된 데이터베이스 암호화 됩니다.|
|Jet OLEDB:Engine 형식 (DBPROP_JETOLEDB_ENGINE)|현재 데이터 저장소에 액세스 하는 데 사용 되는 저장소 엔진을 나타냅니다.|
|Jet OLEDB:Exclusive 비동기 지연 (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|시간 밀리초 Jet 데이터베이스 단독으로 열려 있을 때 디스크에 대 한 비동기 쓰기를 지연 시킬 수 있는 최대 길이 나타냅니다.<br /><br /> 이 속성은 무시 됩니다 **Jet OLEDB:Flush 트랜잭션 시간 제한** 0으로 설정 됩니다.|
|Jet OLEDB:Flush 트랜잭션 시간 제한 (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|비동기 작성에 대 한 캐시에 저장 된 데이터를 실제로 쓸 전에 대기할 시간을 나타내는 디스크에 있습니다. 이 설정에 대 한 값을 재정의 **Jet OLEDB: 공유 비동기 지연** 하 고 **Jet OLEDB:Exclusive 비동기 지연**합니다.|
|Jet OLEDB: 전역 대량 트랜잭션 (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|SQL 대량 트랜잭션이 처리 여부를 나타냅니다.|
|Jet OLEDB: 전역 부분 대량 Ops (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|데이터베이스를 열에 사용 된 암호를 나타냅니다.|
|Jet OLEDB: 암시적 커밋 동기화 (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|암시적 트랜잭션 내부에서 수행한 변경 내용을 동기 또는 비동기 모드로 쓰는지 여부를 나타냅니다.|
|Jet OLEDB:Lock 지연 (DBPROP_JETOLEDB_LOCKDELAY)|이전 시도가 실패 한 후 잠금을 획득 하려고 시도 하기 전에 대기할 시간 (밀리초)의 수를 나타냅니다.|
|Jet OLEDB:Lock 다시 시도 (DBPROP_JETOLEDB_LOCKRETRY)|잠긴된 페이지에 액세스 하려고 하는 반복 횟수를 나타냅니다.|
|Jet OLEDB:Max 버퍼 크기 (DBPROP_JETOLEDB_MAXBUFFERSIZE)|최대 크기를 나타내는 메모리 (킬로바이트)에서 Jet 있습니다 사용 하 여 변경 내용을 디스크에 플러시하기 전에 합니다.|
|(DBPROP_JETOLEDB_MAXLOCKSPERFILE) 파일 마다 jet OLEDB:Max 잠금|Jet 데이터베이스에 배치할 수 잠금의 최대 수를 나타냅니다. 기본값은 9500 합니다.|
|Jet OLEDB: 새 데이터베이스 암호 (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|이 데이터베이스에 대해 설정할 새 암호를 나타냅니다. 이전 암호에 저장 됩니다 **Jet oledb: database Password**합니다.|
|Jet OLEDB:ODBC 명령 시간 제한 (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Jet ODBC 쿼리에서 원격 (밀리초)의 수는 제한 시간을 나타냅니다.|
|테이블 잠금 (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK) jet OLEDB:Page 잠금|페이지 수가 Jet 테이블 잠금으로 잠금을 승격 하려고 하기 전에 트랜잭션 내에서 잠글 수를 나타냅니다. 이 값이 0 이면 잠금이 승격 되지 않습니다.|
|Jet OLEDB:Page 시간 제한 (DBPROP_JETOLEDB_PAGETIMEOUT)|Jet 데이터베이스 파일을 사용 하 여 만료는 캐시 인지 확인 하기 전에 대기할 시간 (밀리초)의 수를 나타냅니다.|
|Jet OLEDB:Recycle 장기 반환 페이지 (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Jet 해제 되는 경우에 페이지 BLOB를 회수 하기 위해 적극적으로 시도해 야 할지 여부를 나타냅니다.|
|Jet OLEDB:Registry 경로 (DBPROP_JETOLEDB_REGPATH)|Jet 데이터베이스 엔진에 대 한 값을 포함 하는 Windows 레지스트리 키를 나타냅니다.|
|Jet OLEDB:Reset ISAM 통계 (DBPROP_JETOLEDB_RESETISAMSTATS)|나타냅니다 여부를 스키마 **레코드 집합** 성능 정보를 반환한 DBSCHEMA_JETOLEDB_ISAMSTATS 해당 성능 카운터를 다시 설정 해야 합니다.|
|Jet OLEDB: 비동기 지연 (DBPROP_JETOLEDB_SHAREDASYNCDELAY)를 공유 합니다.|최대 크기를 나타내는 시간의 밀리초에서 Jet 다중 사용자 모드로 데이터베이스를 열 때 디스크에 대 한 비동기 쓰기를 지연 될 수 있습니다.|
|Jet oledb: 시스템 데이터베이스 (DBPROP_JETOLEDB_SYSDBPATH)|작업 그룹 정보 파일 (시스템 데이터베이스)에 대 한 경로 파일 이름을 나타냅니다.|
|Jet OLEDB:Transaction 커밋 모드 (DBPROP_JETOLEDB_TXNCOMMITMODE)|Jet 동기적으로 디스크에 데이터를 기록 하는 여부 또는 비동기적으로 트랜잭션이 커밋되기를 나타냅니다.|
|Jet OLEDB:User 커밋 동기화 (DBPROP_JETOLEDB_USERCOMMITSYNC)|트랜잭션에서 수행한 변경 내용을 동기 또는 비동기 모드로 쓰는지 여부를 나타냅니다.|

## <a name="provider-specific-recordset-and-command-properties"></a>공급자 관련 레코드 집합 및 명령 속성
 Jet 공급자에서는 여러 공급자별 **레코드 집합** 하 고 **명령** 속성입니다. 이러한 속성 액세스 및 통해 설정 합니다 **속성** 의 컬렉션을 **레코드 집합** 또는 **명령** 개체입니다. 테이블에는 ADO 속성 이름 및 해당 OLE DB 속성 이름을 괄호로 나열합니다.

|속성 이름|Description|
|-------------------|-----------------|
|Jet OLEDB:Bulk 트랜잭션 (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|SQL 대량 작업이 트랜잭션 여부를 나타냅니다. 대규모의 대량 작업 리소스 지연으로 인해 트랜잭션 하는 경우 실패할 수 있습니다.|
|Jet OLEDB:Enable Fat 커서 (DBPROP_JETOLEDB_ENABLEFATCURSOR)|원격 행 원본에 대 한 레코드 집합을 채울 때 Jet 여러 행을 캐시 해야 하는지 여부를 나타냅니다.|
|Jet OLEDB:Fat 커서 캐시 크기 (DBPROP_JETOLEDB_FATCURSORMAXROWS)|원격 데이터 저장소 행 캐싱을 사용 하는 경우 캐시 행의 수를 나타냅니다. 이 값은 무시 됩니다 **Jet OLEDB:Enable Fat 커서** 은 True입니다.|
|Jet OLEDB: 일관 되지 않은 (DBPROP_JETOLEDB_INCONSISTENT)|쿼리 결과가 일관 되지 않은 업데이트를 허용할지 여부를 나타냅니다.|
|Jet OLEDB: 잠금 세분성 (DBPROP_JETOLEDB_LOCKGRANULARITY)|테이블 행 수준 잠금을 사용 하 여 열려 있는지 여부를 나타냅니다.|
|Jet OLEDB:ODBC 통과 문 (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Jet의 SQL 텍스트를 전달 해야 한다는 의미는 **명령** 변경 되지 않은 상태로 백 엔드에는 개체입니다.|
|Jet OLEDB:Partial 대량 Ops (DBPROP_JETOLEDB_BULKPARTIAL)|SQL DML 작업에 실패 하는 경우 Jet의 동작을 나타냅니다.|
|Jet OLEDB:Pass 작동 대량 (DBPROP_JETOLEDB_PASSTHROUGHBULKOP) 쿼리를 통해|여부를 쿼리 하는 하지 않습니다 나타냅니다 반환을 **레코드 집합** 데이터 원본에 변경 되지 않은 상태로 전달 됩니다.|
|쿼리를 통해 jet OLEDB:Pass 연결 문자열 (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)|사용 된 Jet 연결 문자열을 나타내는 원격 데이터 저장소에 연결 합니다. 이 값은 무시 됩니다 **Jet OLEDB:ODBC 통과 문** 은 True입니다.|
|Jet OLEDB: (DBPROP_JETOLEDB_STOREDQUERY) 쿼리를 저장 합니다.|명령 텍스트는 SQL 명령 대신 저장 된 쿼리로 해석할지 여부를 나타냅니다.|
|Jet OLEDB: 규칙 집합 (DBPROP_JETOLEDB_VALIDATEONSET) 유효성 검사|열 데이터를 설정 하거나 변경 내용을 데이터베이스에 커밋되는 경우 Jet 유효성 검사 규칙은 평가 하는지 여부를 나타냅니다.|

 기본적으로 OLE DB Provider for Microsoft Jet는 Microsoft Jet 데이터베이스 읽기/쓰기 모드에서 엽니다. 읽기 전용 모드에서 데이터베이스 열에 설정 합니다 [모드](../../../ado/reference/ado-api/mode-property-ado.md) ADO 속성 **연결** 개체를 **adModeRead**합니다.

## <a name="command-object-usage"></a>명령 개체 사용
 명령에 텍스트를 [명령](../../../ado/reference/ado-api/command-object-ado.md) 개체가 Microsoft Jet SQL 언어를 사용 합니다. 명령 텍스트에 행을 반환 하는 쿼리, 작업 쿼리 및 테이블 이름을 지정할 수 있습니다. 그러나 저장된 프로시저는 지원 되지 않습니다 및 지정할 수 없습니다.

## <a name="recordset-behavior"></a>레코드 집합 동작
 Microsoft Jet 데이터베이스 엔진에서 동적 커서를 지원 하지 않습니다. 따라서 OLE DB Provider for Microsoft Jet 지원 하지 않습니다 합니다 **adLockDynamic** 커서 유형입니다. 공급자 키 집합 커서를 반환 하 고 재설정 동적 커서가 요청 되 면 합니다 [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) 속성의 형식을 나타내는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 반환 합니다. 업데이트할 수 있는 경우 **레코드 집합** 요청 (**LockType** 됩니다 **adLockOptimistic**를 **adLockBatchOptimistic**, 또는 **adLockPessimistic**) 공급자도 키 집합 커서를 반환 하 고 다시 설정 합니다 **CursorType** 속성입니다.

## <a name="dynamic-properties"></a>동적 속성
 여러 동적 속성을 삽입 하는 OLE DB Provider for Microsoft Jet 합니다 **속성** 컬렉션을 아직 열지 않은 [연결](../../../ado/reference/ado-api/connection-object-ado.md)를 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md), 및 [명령](../../../ado/reference/ado-api/command-object-ado.md) 개체입니다.

 다음 테이블은 각 동적 속성에 대 한 OLE DB 및 ADO 이름의 상호는 인덱스입니다. OLE DB 프로그래머 참조 이름을 참조 하는 ADO 속성 라는 용어로, "Description"로 지정 합니다. OLE DB 프로그래머 참조에서 이러한 속성에 대 한 자세한 정보를 찾을 수 있습니다.

## <a name="connection-dynamic-properties"></a>연결의 동적 속성
 다음 속성에 추가 됩니다는 **속성** 의 컬렉션을 **연결** 개체입니다.

|ADO 속성 이름|OLE DB 속성 이름|
|-----------------------|--------------------------|
|Active Sessions|DBPROP_ACTIVESESSIONS|
|비동기 가능 중단|DBPROP_ASYNCTXNABORT|
|비동기 가능 커밋|DBPROP_ASYNCTNXCOMMIT|
|격리 수준 자동 커밋|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|카탈로그 위치|DBPROP_CATALOGLOCATION|
|카탈로그 용어|DBPROP_CATALOGTERM|
|열 정의|DBPROP_COLUMNDEFINITION|
|현재 카탈로그|DBPROP_CURRENTCATALOG|
|데이터 원본|DBPROP_INIT_DATASOURCE|
|Data Source Name|DBPROP_DATASOURCENAME|
|데이터 소스 개체 스레딩 모델|DBPROP_DSOTHREADMODEL|
|DBMS 이름|DBPROP_DBMSNAME|
|DBMS 버전|DBPROP_DBMSVER|
|GROUP BY 지원|DBPROP_GROUPBY|
|유형이 다른 테이블 지원|DBPROP_HETEROGENEOUSTABLES|
|식별자 대/소문자 구분|DBPROP_IDENTIFIERCASE|
|격리 수준|DBPROP_SUPPORTEDTXNISOLEVELS|
|격리 보존|DBPROP_SUPPORTEDTXNISORETAIN|
|로캘 ID|DBPROP_INIT_LCID|
|최대 인덱스 크기|DBPROP_MAXINDEXSIZE|
|최대 행 크기|DBPROP_MAXROWSIZE|
|BLOB 포함 최대 행 크기|DBPROP_MAXROWSIZEINCLUDESBLOB|
|SELECT의 최대 테이블|DBPROP_MAXTABLESINSELECT|
|모드|DBPROP_INIT_MODE|
|여러 매개 변수 집합|DBPROP_MULTIPLEPARAMSETS|
|여러 결과|DBPROP_MULTIPLERESULTS|
|여러 저장소 개체|DBPROP_MULTIPLESTORAGEOBJECTS|
|여러 테이블 업데이트|DBPROP_MULTITABLEUPDATE|
|NULL 정렬 순서|DBPROP_NULLCOLLATION|
|NULL 연결 동작|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB 버전|DBPROP_PROVIDEROLEDBVER|
|OLE 개체 지원|DBPROP_OLEOBJECTS|
|행 집합 열기 지원|DBPROP_OPENROWSETSUPPORT|
|선택 목록의 열을 기준으로 정렬|DBPROP_ORDERBYCOLUMNSINSELECT|
|출력 매개 변수 가용성|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Ref 접근자로 전달|DBPROP_BYREFACCESSORS|
|암호|DBPROP_AUTH_PASSWORD|
|영구 ID 형식|DBPROP_PERSISTENTIDTYPE|
|중단 동작 준비|DBPROP_PREPAREABORTBEHAVIOR|
|커밋 동작 준비|DBPROP_PREPARECOMMITBEHAVIOR|
|프로시저 용어|DBPROP_PROCEDURETERM|
|프롬프트|DBPROP_INIT_PROMPT|
|공급자 이름|DBPROP_PROVIDERFRIENDLYNAME|
|Provider Name|DBPROP_PROVIDERFILENAME|
|공급자 버전|DBPROP_PROVIDERVER|
|읽기 전용 데이터 원본|DBPROP_DATASOURCEREADONLY|
|명령 시 행 집합 변환|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|스키마 용어|DBPROP_SCHEMATERM|
|스키마 사용|DBPROP_SCHEMAUSAGE|
|SQL 지원|DBPROP_SQLSUPPORT|
|구조적된 저장소|DBPROP_STRUCTUREDSTORAGE|
|하위 쿼리 지원|DBPROP_SUBQUERIES|
|테이블 용어|DBPROP_TABLETERM|
|트랜잭션 DDL|DBPROP_SUPPORTEDTXNDDL|
|User ID|DBPROP_AUTH_USERID|
|사용자 이름|DBPROP_USERNAME|
|창 핸들|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>레코드 집합 동적 속성
 다음 속성에 추가 됩니다는 **속성** 의 컬렉션을 **레코드 집합** 개체입니다.

|ADO 속성 이름|OLE DB 속성 이름|
|-----------------------|--------------------------|
|액세스 순서|DBPROP_ACCESSORDER|
|추가 전용 행 집합|DBPROP_APPENDONLY|
|저장소 개체 차단|DBPROP_BLOCKINGSTORAGEOBJECTS|
|책갈피 형식|DBPROP_BOOKMARKTYPE|
|책갈피를 설정할|DBPROP_IROWSETLOCATE|
|순서 있는 책갈피|DBPROP_ORDEREDBOOKMARKS|
|지연 된 열을 캐시 합니다.|DBPROP_CACHEDEFERRED|
|삽입된 행 변경|DBPROP_CHANGEINSERTEDROWS|
|열 권한|DBPROP_COLUMNRESTRICT|
|열 설정 알림|DBPROP_NOTIFYCOLUMNSET|
|쓰기 가능한 열|DBPROP_MAYWRITECOLUMN|
|열 지연|DBPROP_DEFERRED|
|저장소 개체 업데이트 연기|DBPROP_DELAYSTORAGEOBJECTS|
|뒤로 페치|DBPROP_CANFETCHBACKWARDS|
|행 고정|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Immobile Rows|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|리터럴 책갈피|DBPROP_LITERALBOOKMARKS|
|리터럴 행 Id|DBPROP_LITERALIDENTITY|
|최대 열린 행 수|DBPROP_MAXOPENROWS|
|최대 보류 중인 행|DBPROP_MAXPENDINGROWS|
|최대 행 수|DBPROP_MAXROWS|
|메모리 사용량|DBPROP_MEMORYUSAGE|
|알림 단위|DBPROP_NOTIFICATIONGRANULARITY|
|알림 단계|DBPROP_NOTIFICATIONPHASES|
|트랜잭션 개체|DBPROP_TRANSACTEDOBJECT|
|다른 사용자 변경 내용 표시|DBPROP_OTHERUPDATEDELETE|
|다른 사용자 삽입 내용 표시|DBPROP_OTHERINSERT|
|내 변경 내용 표시|DBPROP_OWNUPDATEDELETE|
|내 삽입 내용 표시|DBPROP_OWNINSERT|
|중단 시 유지|DBPROP_ABORTPRESERVE|
|커밋 시 유지|DBPROP_COMMITPRESERVE|
|빠른 다시 시작|DBPROP_QUICKRESTART|
|재진입 이벤트|DBPROP_REENTRANTEVENTS|
|삭제 된 행 제거|DBPROP_REMOVEDELETED|
|여러 변경 내용 보고|DBPROP_REPORTMULTIPLECHANGES|
|보류 중인 삽입 반환|DBPROP_RETURNPENDINGINSERTS|
|행 삭제 알림|DBPROP_NOTIFYROWDELETE|
|행 처음 변경 알림|DBPROP_NOTIFYROWFIRSTCHANGE|
|행 삽입 알림|DBPROP_NOTIFYROWINSERT|
|행 권한|DBPROP_ROWRESTRICT|
|행 다시 동기화 알림|DBPROP_NOTIFYROWRESYNCH|
|행 스레딩 모델|DBPROP_ROWTHREADMODEL|
|행 변경 취소 알림|DBPROP_NOTIFYROWUNDOCHANGE|
|행 삭제 취소 알림|DBPROP_NOTIFYROWUNDODELETE|
|행 삽입 취소 알림|DBPROP_NOTIFYROWUNDOINSERT|
|행 업데이트 알림|DBPROP_NOTIFYROWUPDATE|
|행 집합 페치 위치 변경 알림|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|행 집합 릴리스 알림|DBPROP_NOTIFYROWSETRELEASE|
|뒤로 스크롤|DBPROP_CANSCROLLBACKWARDS|
|삭제 한 책갈피 건너뛰기|DBPROP_BOOKMARKSKIPPED|
|강력한 행 Id|DBPROP_STRONGITDENTITY|
|업데이트 허용|DBPROP_UPDATABILITY|
|책갈피 사용|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>명령 동적 속성
 다음 속성에 추가 됩니다는 **속성** 의 컬렉션을 **명령** 개체입니다.

|ADO 속성 이름|OLE DB 속성 이름|
|-----------------------|--------------------------|
|액세스 순서|DBPROP_ACCESSORDER|
|추가 전용 행 집합|DBPROP_APPENDONLY|
|저장소 개체 차단|DBPROP_BLOCKINGSTORAGEOBJECTS|
|책갈피 형식|DBPROP_BOOKMARKTYPE|
|책갈피를 설정할|DBPROP_IROWSETLOCATE|
|삽입된 행 변경|DBPROP_CHANGEINSERTEDROWS|
|열 권한|DBPROP_COLUMNRESTRICT|
|열 설정 알림|DBPROP_NOTIFYCOLUMNSET|
|열 지연|DBPROP_DEFERRED|
|저장소 개체 업데이트 연기|DBPROP_DELAYSTORAGEOBJECTS|
|뒤로 페치|DBPROP_CANFETCHBACKWARDS|
|행 고정|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Immobile Rows|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|리터럴 책갈피|DBPROP_LITERALBOOKMARKS|
|리터럴 행 Id|DBPROP_LITERALIDENTITY|
|잠금 모드|DBPROP_LOCKMODE|
|최대 열린 행 수|DBPROP_MAXOPENROWS|
|최대 보류 중인 행|DBPROP_MAXPENDINGROWS|
|최대 행 수|DBPROP_MAXROWS|
|알림 단위|DBPROP_NOTIFICATIONGRANULARITY|
|알림 단계|DBPROP_NOTIFICATIONPHASES|
|트랜잭션 개체|DBPROP_TRANSACTEDOBJECT|
|다른 사용자 변경 내용 표시|DBPROP_OTHERUPDATEDELETE|
|다른 사용자 삽입 내용 표시|DBPROP_OTHERINSERT|
|내 변경 내용 표시|DBPROP_OWNUPDATEDELETE|
|내 삽입 내용 표시|DBPROP_OWNINSERT|
|중단 시 유지|DBPROP_ABORTPRESERVE|
|커밋 시 유지|DBPROP_COMMITPRESERVE|
|빠른 다시 시작|DBPROP_QUICKRESTART|
|재진입 이벤트|DBPROP_REENTRANTEVENTS|
|삭제 된 행 제거|DBPROP_REMOVEDELETED|
|여러 변경 내용 보고|DBPROP_REPORTMULTIPLECHANGES|
|보류 중인 삽입 반환|DBPROP_RETURNPENDINGINSERTS|
|행 삭제 알림|DBPROP_NOTIFYROWDELETE|
|행 처음 변경 알림|DBPROP_NOTIFYROWFIRSTCHANGE|
|행 삽입 알림|DBPROP_NOTIFYROWINSERT|
|행 권한|DBPROP_ROWRESTRICT|
|행 다시 동기화 알림|DBPROP_NOTIFYROWRESYNCH|
|행 스레딩 모델|DBPROP_ROWTHREADMODEL|
|행 변경 취소 알림|DBPROP_NOTIFYROWUNDOCHANGE|
|행 삭제 취소 알림|DBPROP_NOTIFYROWUNDODELETE|
|행 삽입 취소 알림|DBPROP_NOTIFYROWUNDOINSERT|
|행 업데이트 알림|DBPROP_NOTIFYROWUPDATE|
|행 집합 페치 위치 변경 알림|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|
|행 집합 릴리스 알림|DBPROP_NOTIFYROWSETRELEASE|
|뒤로 스크롤|DBPROP_CANSCROLLBACKWARDS|
|삽입의 서버 데이터|DBPROP_SERVERDATAONINSERT|
|삭제 한 책갈피 건너뛰기|DBPROP_BOOKMARKSKIP|
|강력한 행 Id|DBPROP_STRONGIDENTITY|
|업데이트 허용|DBPROP_UPDATABILITY|
|책갈피 사용|DBPROP_BOOKMARKS|

 특정 구현 세부 정보 및 기능 정보 OLE DB Provider for Microsoft Jet [Jet 공급자](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) OLE DB 설명서에서.
