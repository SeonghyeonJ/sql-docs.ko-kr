---
title: 행 집합 속성 및 동작 | Microsoft Docs
description: 행 집합 속성 및 OLE DB 드라이버에서 SQL Server에 대 한 동작
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], properties
- OLE DB Driver for SQL Server, rowsets
- properties [OLE DB]
- OLE DB rowsets, properties
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: c3bb95de560e0e4ec6b5e01fda8623858a73aaf4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803807"
---
# <a name="rowset-properties-and-behaviors"></a>행 집합 속성 및 동작
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  이들은 OLE DB Driver for SQL Server 행 집합 속성입니다.  
  
|속성 ID|설명|  
|-----------------|-----------------|  
|DBPROP_ABORTPRESERVE|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 이 속성에 의해 중단 작업이 확인된 후의 행 집합 동작입니다.<br /><br /> VARIANT_FALSE:는 OLE DB Driver for SQL Server는 중단 작업 후 행 집합을 무효화 합니다. 행 집합 개체의 기능은 거의 손실됩니다. 행 집합 개체는 **IUnknown** 작업과 처리 중인 행 및 접근자 핸들의 해제만 지원합니다.<br /><br /> VARIANT_TRUE: OLE DB 드라이버 SQL Server에 대 한 유효한 행 집합을 유지 관리합니다.|  
|DBPROP_ACCESSORDER|R/w: 읽기/쓰기<br /><br /> 기본값: DBPROPVAL_AO_RANDOM<br /><br /> 설명: 액세스 순서입니다. 행 집합에서 열이 액세스되어야 하는 순서입니다.<br /><br /> DBPROPVAL_AO_RANDOM: 열 순서에 관계 없이 액세스할 수 있습니다.<br /><br /> DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS: 열 저장소 개체 열 서 수에 따라 순차적으로 액세스할 수 있습니다로 바인딩됩니다.<br /><br /> DBPROPVAL_AO_SEQUENTIAL: 모든 열은 열 서수에 의해 결정되는 순서에 따라 액세스해야 합니다.|  
|DBPROP_APPENDONLY|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: OLE DB 드라이버 다른 행 집합 메서드를 사용 하 여 SQL Server 저장소 개체 블록에 대 한 합니다.|  
|DBPROP_BOOKMARKS DBPROP_LITERALBOOKMARKS|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: SQL Server용 OLE DB 드라이버는 DBPROP_BOOKMARKS 또는 DBPROP_LITERALBOOKMARKS가 VARIANT_TRUE인 경우 행 집합 행 ID에 대한 책갈피를 지원합니다.<br /><br /> 두 속성 중 하나를 VARIANT_TRUE로 설정하면 책갈피를 사용한 행 집합 배치가 활성화되지 않습니다. DBPROP_IRowsetLocate 또는 DBPROP_IRowsetScroll을 VARIANT_TRUE로 설정하면 책갈피를 사용한 행 집합 배치를 지원하는 행 집합을 만들 수 있습니다.<br /><br /> OLE DB Driver for SQL Server를 사용 하는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 책갈피를 포함 하는 행 집합을 지원 하기 위해 커서입니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.<br /><br /> 참고: 이러한 속성을 다른 SQL Server용 OLE DB 드라이버 커서 정의 속성과 충돌하도록 설정하면 오류가 발생합니다. 예를 들어 DBPROP_OTHERINSERT가 VARIANT_TRUE로 설정된 상태에서 DBPROP_BOOKMARKS를 VARIANT_TRUE로 설정하면 소비자가 행 집합을 열려고 시도할 때 오류가 발생합니다.|  
|DBPROP_BOOKMARKSKIPPED|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: SQL Server용 OLE DB 드라이버는 책갈피가 표시된 행 집합을 배치 또는 검색할 때 소비자가 잘못된 책갈피를 가리키는 경우 DB_E_BADBOOKMARK를 반환합니다.|  
|DBPROP_BOOKMARKTYPE|R/w: 읽기 전용<br /><br /> 기본값: DBPROPVAL_BMK_NUMERIC<br /><br /> 설명:는 OLE DB Driver for SQL Server에는 숫자 책갈피만 구현합니다. OLE DB Driver for SQL Server 책갈피는 DBTYPE_UI4 입력 32 비트 부호 없는 정수입니다.|  
|DBPROP_CACHEDEFERRED|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_CANFETCHBACKWARDS DBPROP_CANSCROLLBACKWARDS|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 뒤로 인출 및 스크롤 비순차적 행 집합에서 지원 합니다. SQL Server용 OLE DB 드라이버는 DBPROP_CANFETCHBACKWARDS 또는 DBPROP_CANSCROLLBACKWARDS가 VARIANT_TRUE이면 커서 지원 행 집합을 만듭니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.|  
|DBPROP_CANHOLDROWS|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 현재 행 집합에 있는 행에 보류 중인 변경 내용이 있는 상태에서 소비자가 행 집합에 대해 더 많은 행을 가져오려고 시도하는 경우 SQL Server용 OLE DB 드라이버는 기본적으로 DB_E_ROWSNOTRELEASED를 반환합니다. 이 동작은 수정할 수 있습니다.<br /><br /> DBPROP_CANHOLDROWS 및 DBPROP_IRowsetChange를 모두 VARIANT_TRUE로 설정할 경우 이는 책갈피가 표시된 행 집합을 의미합니다. 두 속성이 모두 VARIANT_TRUE인 경우 행 집합에서 **IRowsetLocate** 인터페이스를 사용할 수 있으며 DBPROP_BOOKMARKS 및 DBPROP_LITERALBOOKMARKS는 모두 VARIANT_TRUE입니다.<br /><br /> OLE DB 드라이버 책갈피를 포함 하는 SQL Server 행 집합에 대 한 지 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서입니다.|  
|DBPROP_CHANGEINSERTEDROWS|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 행 집합이 키 집합 커서를 사용 중인 경우 이 속성은 VARIANT_TRUE로만 설정할 수 있습니다.|  
|DBPROP_COLUMNRESTRICT|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server 설정 속성을 variant_true로 소비자가 행 집합의 열을 변경할 수 없는 경우. 행 집합의 다른 열은 업데이트될 수 있으며 행 자체는 삭제될 수 있습니다.<br /><br /> 속성이 VARIANT_TRUE인 경우 소비자는 DBCOLUMNINFO 구조의 *dwFlags* 멤버를 검토하여 개별 열의 값을 쓸 수 있는지 여부를 확인합니다. 수정이 가능한 열의 경우 *dwFlags*는 DBCOLUMNFLAGS_WRITE를 표시합니다.|  
|DBPROP_COMMANDTIMEOUT|R/w: 읽기/쓰기<br /><br /> 기본값: 0<br /><br /> 설명: 기본적으로 OLE DB Driver for SQL Server에 제한 시간이 없음을에 **icommand:: Execute** 메서드.|  
|DBPROP_COMMITPRESERVE|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 이 속성에 의해 커밋 작업이 확인된 후의 행 집합 동작입니다.<br /><br /> VARIANT_TRUE: OLE DB 드라이버 SQL Server에 대 한 유효한 행 집합을 유지 관리합니다.<br /><br /> VARIANT_FALSE: OLE DB 드라이버 SQL Server에 대 한 커밋 작업이 완료 된 후 행 집합을 무효화 합니다. 행 집합 개체의 기능은 거의 손실됩니다. 행 집합 개체는 **IUnknown** 작업과 처리 중인 행 및 접근자 핸들의 해제만 지원합니다.|  
|DBPROP_DEFERRED|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: VARIANT_TRUE로 설정 하면 OLE DB 드라이버는 행 집합에 대해 서버 커서를 사용 하려고 하는 SQL Server에 대 한 합니다. **Text**, **ntext** 및 **image** 열은 애플리케이션에 의해 액세스될 때까지 서버에서 반환되지 않습니다.|  
|DBPROP_DELAYSTORAGEOBJECTS|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server 저장소 개체에서 즉시 업데이트 모드를 지원합니다.<br /><br /> 순차 스트림 개체의 데이터에 적용된 변경 내용은 즉시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 전송됩니다. 수정은 행 집합 트랜잭션 모드를 기반으로 커밋됩니다.|  
|DBPROP_HIDDENCOLUMNS|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_FALSE<br /><br /> **설명:** 숨겨진 열 개수<br /><br /> DBPROP_UNIQUEROWS가 VARIANT_TRUE이면 DBPROP_HIDDENCOLUMNS 속성은 공급자가 행 집합 내의 행을 고유하게 식별하기 위해 추가한 “숨겨진” 열의 수를 반환합니다. 이러한 열은 **IColumnsInfo::GetColumnInfo** 및 **IColumnsRowset::GetColumnsRowset**에 의해 반환됩니다. 그러나 **IColumnsInfo::GetColumnInfo**에 의해 반환되는 *pcColumns* 인수가 반환하는 행 수에는 이러한 열이 포함되지 않습니다.<br /><br /> 숨겨진 열을 포함하여 **IColumnsInfo::GetColumnInfo**에 의해 반환되는 *prgInfo* 구조에 표시되는 전체 열 수를 확인하기 위해 소비자는 DBPROP_HIDDENCOLUMNS 값을 *pcColumns*의 **IColumnsInfo::GetColumnInfo**에서 반환되는 열의 수에 더합니다. DBPROP_UNIQUEROWS가 VARIANT_FALSE이면 DBPROP_HIDDENCOLUMNS는 0입니다.|  
|DBPROP_IAccessor DBPROP_IColumnsInfo DBPROP_IConvertType DBPROP_IRowset DBPROP_IRowsetInfo|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 모든 행 집합에서 이러한 인터페이스를 지원합니다.|  
|DBPROP_IColumnsRowset|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명:는 OLE DB Driver for SQL Server를 지원 합니다 **IColumnsRowset** 인터페이스입니다.|  
|DBPROP_IConnectionPointContainer|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: IConnectionPointContainer 합니다. VARIANT_TRUE이면 행 집합은 지정된 인터페이스를 지원합니다. VARIANT_FALSE이면 행 집합은 지정된 인터페이스를 지원하지 않습니다. 인터페이스를 지원하는 공급자는 해당 인터페이스와 연결된 VARIANT_TRUE 값을 가진 속성을 지원해야 합니다. 이러한 속성은 주로 ICommandProperties::SetProperties를 통해 인터페이스를 요청하는 데 사용됩니다.|  
|DBPROP_IMultipleResults|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server를 지원 합니다 **IMultipleResults** 인터페이스입니다.|  
|DBPROP_IRowsetChange DBPROP_IRowsetUpdate|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server를 지원 합니다 **IRowsetChange** 하 고 **IRowsetUpdate** 인터페이스.<br /><br /> DBPROP_IRowsetChange = VARIANT_TRUE를 사용하여 만들어진 행 집합은 즉시 업데이트 모드 동작을 나타냅니다.<br /><br /> DBPROP_IRowsetUpdate가 VARIANT_TRUE이면 DBPROP_IRowsetChange도 VARIANT_TRUE입니다. 행 집합은 지연 업데이트 모드 동작을 나타냅니다.<br /><br /> OLE DB Driver for SQL Server를 사용 하는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 노출 하는 행 집합을 지원 하려면 커서 **IRowsetChange** 또는 **IRowsetUpdate**합니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.|  
|DBPROP_IRowsetIdentity|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명:는 OLE DB Driver for SQL Server를 지원 합니다 **IRowsetIdentity** 인터페이스입니다. 행 집합이 이 인터페이스를 지원하면 동일한 기본 행을 나타내는 두 개의 행 핸들은 항상 동일한 데이터 및 상태를 반영합니다. 소비자는 **IRowsetIdentity:: IsSameRow** 동일한 행 인스턴스를 참조 하는지에 두 개의 행 핸들을 비교 하는 방법입니다.|  
|DBPROP_IRowsetLocate DBPROP_IRowsetScroll|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server를 노출할 수 있습니다 합니다 **IRowsetLocate** 하 고 **IRowsetScroll** 인터페이스입니다.<br /><br /> DBPROP_IRowsetLocate가 VARIANT_TRUE이면 DBPROP_CANFETCHBACKWARDS 및 DBPROP_CANSCROLLBACKWARDS도 VARIANT_TRUE입니다.<br /><br /> DBPROP_IRowsetScroll이 VARIANT_TRUE이면 DBPROP_IRowsetLocate도 VARIANT_TRUE이며 두 인터페이스 모두 행 집합에서 사용할 수 있습니다.<br /><br /> 두 인터페이스 모두 책갈피가 필요합니다. SQL Server용 OLE DB 드라이버는 소비자가 두 인터페이스 중 하나를 요청하는 경우 DBPROP_BOOKMARKS 및 DBPROP_LITERALBOOKMARKS를 VARIANT_TRUE로 설정합니다.<br /><br /> OLE DB Driver for SQL Server를 사용 하 여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 지원 하기 위해 커서 **IRowsetLocate** 하 고 **IRowsetScroll**합니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.<br /><br /> 이러한 속성을 다른 SQL Server용 OLE DB 드라이버 커서 정의 속성과 충돌하도록 설정하면 오류가 발생합니다. 예를 들어 DBPROP_OTHERINSERT가 VARIANT_TRUE로 설정된 상태에서 DBPROP_IRowsetScroll을 VARIANT_TRUE로 설정하면 소비자가 행 집합을 열려고 시도할 때 오류가 발생합니다.|  
|DBPROP_IRowsetResynch|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server 노출 합니다 **IRowsetResynch** 주문형 인터페이스입니다. OLE DB Driver for SQL Server의 모든 행 집합 인터페이스를 노출할 수 있습니다.|  
|DBPROP_ISupportErrorInfo|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명:는 OLE DB Driver for SQL Server 노출 합니다 **ISupportErrorInfo** 행 집합의 인터페이스입니다.|  
|DBPROP_ILockBytes|이 인터페이스는 하지 SQL Server 용 OLE DB 드라이버에서 구현 됩니다. 이 속성을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_ISequentialStream|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server 노출 합니다 **ISequentialStream** 긴에 저장 된 가변 길이 데이터를 지원 하기 위해 인터페이스 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다.|  
|DBPROP_IStorage|이 인터페이스는 하지 SQL Server 용 OLE DB 드라이버에서 구현 됩니다. 이 속성을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_IStream|이 인터페이스는 하지 SQL Server 용 OLE DB 드라이버에서 구현 됩니다. 이 속성을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_IMMOBILEROWS|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: 이 속성은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 키 집합 커서에 대해서만 VARIANT_TRUE이며 다른 모든 커서에 대해서는 VARIANT_FALSE입니다.<br /><br /> VARIANT_TRUE: 행 집합은 삽입 또는 업데이트된 행을 다시 정렬하지 않습니다. **IRowsetChange::InsertRow**의 경우 행은 행 집합 끝에 표시됩니다. **IRowsetChange::SetData**의 경우 행 집합이 정렬되지 않으면 업데이트된 행의 위치는 바뀌지 않습니다. 행 집합이 정렬되고 **IRowsetChange::SetData**가 행 집합을 정렬하는 데 사용되는 열을 변경하는 경우 행은 이동하지 않습니다. 행 집합이 키 열 집합을 기반으로 만들어진 경우(일반적으로 DBPROP_OTHERUPDATEDELETE가 VARIANT_TRUE이지만 DBPROP_OTHERINSERT는 VARIANT_FALSE인 행 집합) 키 열 값을 변경하는 것은 대개 현재 행을 삭제하고 새 행을 삽입하는 것과 동일합니다. 따라서 DBPROP_OWNINSERT가 VARIANT_FALSE이면 DBPROP_IMMOBILEROWS 속성이 VARIANT_TRUE이더라도 행은 행 집합에서 이동하거나 사라진 것처럼 보일 수 있습니다.<br /><br /> VARIANT_FALSE: 행 집합이 정렬되는 경우 삽입된 행은 행 집합의 올바른 순서에 따라 표시됩니다. 행 집합이 정렬되지 않는 경우 삽입된 행은 끝에 표시됩니다. **IRowsetChange::SetData**가 행 집합을 정렬하는 데 사용되는 열을 변경하는 경우 행은 이동합니다. 행 집합이 정렬되지 않는 경우 행의 위치는 변경되지 않습니다.|  
|DBPROP_LITERALIDENTITY|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: 이 속성은 항상 VARIANT_TRUE입니다.|  
|DBPROP_LOCKMODE|R/w: 읽기/쓰기<br /><br /> 기본값: DBPROPVAL_LM_NONE<br /><br /> 설명: 행 집합에 의해 수행되는 잠금의 수준입니다(DBPROPVAL_LM_NONE, DBPROPVAL_LM_SINGLEROW).<br /><br /> 참고: 트랜잭션에서 스냅샷 격리를 사용 중이면 키 집합 또는 동적 서버 커서를 사용하여 행 집합을 열고 잠금 모드가 DBPROPVAL_LM_SINGLEROW로 설정된 경우, 트랜잭션이 시작된 이후 다른 사용자가 행을 업데이트하면 해당 행을 인출할 때 오류가 발생합니다. 다른 커서 유형 및 잠금 모드의 경우 트랜잭션이 시작된 이후 다른 사용자가 행을 업데이트해도 사용자가 행을 업데이트하려고 시도할 때까지 오류는 발생하지 않습니다. 두 경우 모두 이러한 오류는 서버에서 일으킵니다.|  
|DBPROP_MAXOPENROWS|R/w: 읽기 전용<br /><br /> 기본값: 0<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 행 집합에서 활성화 될 수 있는 행의 수를 제한 하지 않습니다.|  
|DBPROP_MAXPENDINGROWS|R/w: 읽기 전용<br /><br /> 기본값: 0<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 보류 중인 변경 내용 사용 하 여 행 집합 행 수를 제한 하지 않습니다.|  
|DBPROP_MAXROWS|R/w: 읽기/쓰기<br /><br /> 기본값: 0<br /><br /> 설명: 기본적으로 OLE DB Driver for SQL Server 제한 하지 않습니다 행 집합의 행 수 없습니다. 소비자가 DBPROP_MAXROWS를 설정하는 경우 SQL Server용 OLE DB 드라이버는 SET ROWCOUNT 문을 사용하여 행 집합의 행 수를 제한합니다.<br /><br /> SET ROWCOUNT는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 문 실행에 의도하지 않은 결과를 유발할 수 있습니다. 자세한 내용은 [SET ROWCOUNT](../../../t-sql/statements/set-rowcount-transact-sql.md)를 참조하세요.|  
|DBPROP_MAYWRITECOLUMN|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_MEMORYUSAGE|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_NOTIFICATIONGRANULARITY|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_NOTIFICATIONPHASES|R/w: 읽기 전용<br /><br /> 기본값: DBPROPVAL_NP_OKTODO &#124; DBPROPVAL_NP_ABOUTTODO &#124; DBPROPVAL_NP_SYNCHAFTER &#124; DBPROPVAL_NP_FAILEDTODO &#124; DBPROPVAL_NP_DIDEVENT<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 모든 알림 단계를 지원합니다.|  
|DBPROP_NOTIFYCOLUMNSET DBPROP_NOTIFYROWDELETE DBPROP_NOTIFYROWFIRSTCHANGE DBPROP_NOTIFYROWINSERT DBPROP_NOTIFYROWRESYNCH DBPROP_NOTIFYROWSETRELEASE DBPROP_NOTIFYROWSETFETCH-POSITIONCHANGE DBPROP_NOTIFYROWUNDOCHANGE DBPROP_NOTIFYROWUNDODELETE DBPROP_NOTIFYROWUNDOINSERT DBPROP_NOTIFYROWUPDATE|R/w: 읽기 전용<br /><br /> 기본값: DBPROPVAL_NP_OKTODO &#124; DBPROPVAL_NP_ABOUTTODO<br /><br /> 설명:는 OLE DB Driver for SQL Server 알림 단계는 표시 된 행 집합 수정을 시도 하기 전에 취소할 수 있습니다. OLE DB Driver for SQL Server는 시도가 완료 된 후 단계 취소를 지원 하지 않습니다.|  
|DBPROP_ORDEREDBOOKMARKS|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_OTHERINSERT DBPROP_OTHERUPDATEDELETE DBPROP_OWNINSERT DBPROP_OWNUPDATEDELETE|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 변경 표시 여부 속성을 설정 하면 OLE DB 드라이버를 사용 하도록 SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서를 행 집합을 지원 합니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.|  
|DBPROP_QUICKRESTART|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> OLE DB Driver for SQL Server에 대 한 VARIANT_TRUE로 설정 된 경우, 행 집합에 대 한 서버 커서를 사용 하려고 합니다.|  
|DBPROP_REENTRANTEVENTS|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: SQL Server용 OLE DB 드라이버 행 집합은 재진입용이며, 소비자가 알림 콜백에서 재진입용이 아닌 행 집합 메서드에 액세스하려고 시도하는 경우 DB_E_NOTREENTRANT를 반환할 수 있습니다.|  
|DBPROP_REMOVEDELETED|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 변경의 표시 여부에 따라 속성의 값을 변경 합니다 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 행 집합에서 제공 하는 데이터입니다.<br /><br /> VARIANT_TRUE: 소비자 또는 기타 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 사용자에 의해 삭제된 행은 행 집합을 새로 고칠 때 행 집합에서 제거됩니다. DBPROP_OTHERINSERT는 VARIANT_TRUE입니다.<br /><br /> VARIANT_FALSE: 소비자 또는 기타 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 사용자에 의해 삭제된 행은 행 집합을 새로 고칠 때 행 집합에서 제거되지 않습니다. 삭제된 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 행에 대한 행 상태 값은 DBROWSTATUS_E_DELETED입니다. DBPROP_OTHERINSERT는 VARIANT_TRUE입니다.<br /><br /> 이 속성은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서에서 지원하는 행 집합에 대한 값만 갖습니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.<br /><br /> DBPROP_REMOVEDELETED 속성이 키 집합 커서 행 집합에 구현되는 경우 삭제된 행은 인출 시에 제거되며, **GetNextRows** 및 **GetRowsAt,** 와 같은 행 인출 메서드는 S_OK와 요청된 것보다 더 적은 수의 행을 모두 반환할 수 있습니다. 이 동작은 DB_S_ENDOFROWSET 조건을 나타내지 않으며 남은 행이 있는 경우 반환되는 행의 수는 0이 되지 않습니다.|  
|DBPROP_REPORTMULTIPLECHANGES|SQL Server 용 OLE DB 드라이버에서이 행 집합 속성을 구현 되지 않았습니다. 이 속성 값을 읽거나 쓰려고 하면 오류가 생성됩니다.|  
|DBPROP_RETURNPENDINGINSERTS|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 행을 인출 하는 메서드가 호출 되는 OLE DB Driver for SQL Server 반환 하지 않습니다 보류 된 삽입 행입니다.|  
|DBPROP_ROWRESTRICT|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: SQL Server 행 집합에 대 한 OLE DB 드라이버는 행에 따라 액세스 권한을 지원 하지 않습니다. **IRowsetChange** 인터페이스가 행 집합에 노출되면 사용자가 **SetData** 메서드를 호출할 수 있습니다.|  
|DBPROP_ROWSET_ASYNCH|R/w: 읽기/쓰기<br /><br /> 기본값: 0<br /><br /> 설명: 비동기 행 집합 처리를 제공합니다. 이 속성은 Rowset 속성 그룹과 DBPROPSET_ROWSET 속성 집합에 있습니다. 형식은 VT_14입니다.<br /><br /> SQL Server에 대 한 OLE DB 드라이버에서 지 원하는 비트 마스크의 유일한 값 **DBPROPVAL_ASYNCH_INITIALIZE**합니다.|  
|DBPROP_ROWTHREADMODEL|R/w: 읽기 전용<br /><br /> 기본값: DBPROPVAL_RT_FREETHREAD<br /><br /> 설명: OLE DB 드라이버 SQL Server에 대 한 액세스를 지원 해당 개체에 단일 소비자의 여러 실행 스레드에서 합니다.|  
|DBPROP_SERVERCURSOR|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 설정하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 커서를 사용하여 행 집합을 지원합니다. 자세한 내용은 [행 집합 및 SQL Server 커서](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)를 참조하십시오.|  
|DBPROP_SERVERDATAONINSERT|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 서버 데이터에 삽입 합니다.<br /><br /> VARIANT_TRUE: 삽입이 서버로 전송될 때 공급자는 서버에서 데이터를 검색하여 로컬 행 캐시를 업데이트합니다.<br /><br /> VARIANT_FALSE: 공급자는 새로 삽입되는 행에 대한 서버 값을 검색하지 않습니다.|  
|DBPROP_STRONGIDENTITY|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: 강력한 행 id입니다. 행 집합에 대해 삽입이 허용되고(**IRowsetChange** 또는 **IRowsetUpdate**가 true) DBPROP_UPDATABILITY가 InsertRows를 지원하도록 설정되면 DBPROP_STRONGIDENTITY의 값은 DBPROP_CHANGEINSERTEDROWS 속성에 따라 달라집니다(DBPROP_CHANGEINSERTEDROWS 속성 값이 VARIANT_FALSE인 경우 VARIANT_FALSE).|  
|DBPROP_TRANSACTEDOBJECT|R/w: 읽기 전용<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명:는 OLE DB Driver for SQL Server에 트랜잭션 된 개체만 지원합니다. 자세한 내용은 [트랜잭션을](../../oledb/ole-db-transactions/transactions.md)합니다.|  
|DBPROP_UNIQUEROWS|R/w: 읽기/쓰기<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 고유한 행입니다.<br /><br /> VARIANT_TRUE: 각 행은 열 값에 의해 고유하게 식별됩니다. 행을 고유하게 식별하는 열 집합은 **GetColumnInfo** 메서드에서 반환하는 DBCOLUMNINFO 구조에 DBCOLUMNFLAGS_KEYCOLUMN이 설정되어 있습니다.<br /><br /> VARIANT_FALSE: 행은 열 값에 의해 고유하게 식별될 수도, 식별되지 않을 수도 있습니다. 키 열에는 DBCOLUMNFLAGS_KEYCOLUMN 플래그가 설정되거나 설정되지 않을 수 있습니다.|  
|DBPROP_UPDATABILITY|R/w: 읽기/쓰기<br /><br /> 기본값: 0<br /><br /> 설명:는 OLE DB Driver for SQL Server는 모든 DBPROP_UPDATABILITY 값을 지원합니다. DBPROP_UPDATABILITY를 설정해도 수정 가능한 행 집합은 만들어지지 않습니다. 행 집합을 수정 가능하게 하려면 DBPROP_IRowsetChange 또는 DBPROP_IRowsetUpdate를 설정합니다.|  
  
 SQL Server용 OLE DB 드라이버는 다음 표에 표시된 것과 같이 공급자별 속성 집합 DBPROPSET_SQLSERVERROWSET을 정의합니다.  
  
|속성 ID|설명|  
|-----------------|-----------------|  
|SSPROP_COLUMN_ID|열: ColumnID<br /><br /> R/w: 읽기 전용<br /><br /> 형식: VT_U12 &#124; VT_ARRAY<br /><br /> 기본값: VT_EMPTY<br /><br /> 설명: 현재 [!INCLUDE[tsql](../../../includes/tsql-md.md)] SELECT 문 내 COMPUTE 절 결과 열의 서수 위치(1-기반)를 나타내는 정수 배열입니다. 이는 OLE DB Driver for SQL Server ODBC SQL_CA_SS_COLUMN_ID 특성에 해당 합니다.|  
|SSPROP_DEFERPREPARE|열: 아니요<br /><br /> R/w: 읽기/쓰기<br /><br /> 형식: VT_BOOL<br /><br /> 기본값: VARIANT_TRUE<br /><br /> 설명: VARIANT_TRUE: 준비된 실행에서 명령 준비는 **ICommand::Execute**가 호출되거나 메타 속성 작업이 수행될 때까지 지연됩니다. 속성 설정에 따른 동작은 다음과 같습니다.<br /><br /> VARIANT_FALSE: 명령문은 **ICommandPrepare::Prepare**가 실행될 때 준비됩니다.|  
|SSPROP_IRowsetFastLoad|열: 아니요<br /><br /> R/w: 읽기/쓰기<br /><br /> 형식: VT_BOOL<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 이 속성을 VARIANT_TRUE로 설정하면 **IOpenRowset::OpenRowset**을 통해 빠른 로드 행 집합을 열 수 있습니다. **ICommandProperties::SetProperties**에서는 이 속성을 설정할 수 없습니다.|  
|SSPROP_ISSAsynchStatus|열: 아니요.<br /><br /> R/w: 읽기/쓰기<br /><br /> 형식: VT_BOOL<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: 이 속성을 VARIANT_TRUE로 설정하면 [ISSAsynchStatus](../../oledb/ole-db-interfaces/issasynchstatus-ole-db.md) 인터페이스를 사용한 비동기 작업을 활성화할 수 있습니다.|  
|SSPROP_MAXBLOBLENGTH|열: 아니요<br /><br /> R/w: 읽기/쓰기<br /><br /> 형식: VT_I4<br /><br /> 기본값: 공급자는 서버에서 반환되는 텍스트의 크기를 제한하지 않으며 속성 값은 해당 최댓값으로 설정됩니다. 2147483647).<br /><br /> 설명: SQL Server용 OLE DB 드라이버는 SET TEXTSIZE 문을 실행하여 SELECT 문에서 반환되는 BLOB(Binary Large Object) 데이터의 길이를 제한합니다.|  
|SSPROP_NOCOUNT_STATUS|열: NoCount<br /><br /> R/w: 읽기 전용<br /><br /> 형식: VT_BOOL<br /><br /> 기본값: VARIANT_FALSE<br /><br /> 설명: [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]의 SET NOCOUNT ON/OFF 상태를 나타내는 부울 값입니다.<br /><br /> VARIANT_TRUE: SET NOCOUNT ON인 경우<br /><br /> VARIANT_FALSE: SET NOCOUNT OFF인 경우|  
|SSPROP_QP_NOTIFICATION_MSGTEXT|열: 아니요<br /><br /> R/w: 읽기/쓰기<br /><br /> 형식: VT_BSTR(1-2000자 허용)<br /><br /> 기본값: 빈 문자열<br /><br /> 설명: 쿼리 알림의 메시지 텍스트입니다. 사용자가 정의하며 정의된 형식은 없습니다.|  
|SSPROP_QP_NOTIFICATION_OPTIONS|열: 아니요<br /><br /> R/w: 읽기/쓰기<br /><br /> 유형: VT_BSTR<br /><br /> 기본값: 빈 문자열<br /><br /> 설명: 쿼리 알림 옵션입니다. 이러한 옵션은 `name=value`가 포함된 문자열로 지정됩니다. 사용자가 서비스를 만들고 큐에서 알림을 읽어야 합니다. 쿼리 알림 옵션 문자열의 구문은 다음과 같습니다.<br /><br /> `service=<service-name>[;(local database=<database>&#124;broker instance=<broker instance>)]`<br /><br /> 예를 들어<br /><br /> `service=mySSBService;local database=mydb`|  
|SSPROP_QP_NOTIFICATION_TIMEOUT|열: 아니요<br /><br /> R/w: 읽기/쓰기<br /><br /> 형식: VT_UI4<br /><br /> 기본값: 432000 초 (5 일)<br /><br /> 최소: 1 시간 (초)<br /><br /> 최대: 2 ^31-1 시간 (초)<br /><br /> 설명: 쿼리 알림이 활성 상태로 유지되는 시간(초)입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [행 집합](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
