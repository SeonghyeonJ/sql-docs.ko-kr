---
title: 로컬 트랜잭션 지원 | Microsoft Docs
description: SQL Server 용 OLE DB 드라이버에서 로컬 트랜잭션
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- autocommit mode
- transactions [OLE DB]
- ITransactionLocal interface
- OLE DB Driver for SQL Server, transactions
- local transactions [OLE DB]
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 9aacaf8c52ad45a3d61087d1029bdd6f7176629e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765975"
---
# <a name="supporting-local-transactions"></a>로컬 트랜잭션 지원
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  세션의 트랜잭션 범위는 OLE DB Driver for SQL Server 로컬 트랜잭션이를 구분합니다. 시기, 인스턴스에 연결된 요청을 제출는 OLE DB Driver for SQL Server 소비자의 지시에 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], SQL Server 용 OLE DB 드라이버에 대 한 작업 단위를 구성 합니다. 항상 SQL Server 세션에 대 한 로컬 트랜잭션을 단일 OLE DB 드라이버에서이 작업의 하나 이상의 단위를 래핑합니다.  
  
 기본 SQL Server용 OLE DB 드라이버 자동 커밋 모드를 사용하면 단일 작업 단위가 로컬 트랜잭션 범위로 처리됩니다. 하나의 단위만 로컬 트랜잭션에 참여합니다. 세션이 만들어지면는 OLE DB Driver for SQL Server 세션의 트랜잭션을 시작 합니다. 작업 단위가 성공적으로 완료되면 해당 작업이 커밋됩니다. 실패하면 시작된 모든 작업이 롤백되며 소비자에게 오류가 반환됩니다. 두 경우 모두 SQL Server용 OLE DB 드라이버는 모든 작업이 한 트랜잭션 내에서 수행될 수 있도록 해당 세션에 대한 새로운 로컬 트랜잭션을 만듭니다.  
  
 SQL Server용 OLE DB 드라이버 소비자는 **ITransactionLocal** 인터페이스를 사용하여 로컬 트랜잭션 범위를 더욱 정확하게 제어할 수 있습니다. 소비자 세션이 트랜잭션을 시작하면 트랜잭션 시작점과 결과 **Commit** 또는 **Abort** 메서드 호출 시점 사이에 있는 모든 세션 작업 단위는 원자 단위로 처리됩니다. OLE DB Driver for SQL Server에는 암시적으로 이렇게 하려면 소비자가 지시 하는 경우 트랜잭션을 시작 합니다. 소비자가 보존을 요청하지 않으면 세션은 일반적으로 자동 커밋 모드인 부모 트랜잭션 수준 동작으로 돌아갑니다.  
  
 OLE DB Driver for SQL Server 지원 **itransactionlocal:: Starttransaction** 다음과 같은 매개 변수입니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|*isoLevel*[in]|이 트랜잭션에 사용할 격리 수준입니다. 로컬 트랜잭션에서 OLE DB Driver for SQL Server 다음을 지원합니다.<br /><br /> **ISOLATIONLEVEL_UNSPECIFIED**<br /><br /> **ISOLATIONLEVEL_CHAOS**<br /><br /> **ISOLATIONLEVEL_READUNCOMMITTED**<br /><br /> **ISOLATIONLEVEL_READCOMMITTED**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_CURSORSTABILITY**<br /><br /> **ISOLATIONLEVEL_REPEATABLEREAD**<br /><br /> **ISOLATIONLEVEL_SERIALIZABLE**<br /><br /> **ISOLATIONLEVEL_ISOLATED**<br /><br /> **ISOLATIONLEVEL_SNAPSHOT**<br /><br /> <br /><br /> 참고: [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]부터는 데이터베이스에 버전 관리가 설정되어 있는지 여부에 관계없이 *isoLevel* 인수에 대해 ISOLATIONLEVEL_SNAPSHOT이 유효합니다. 그러나 버전 관리가 설정되어 있지 않거나 데이터베이스가 읽기 전용이 아닌 상태에서 사용자가 문을 실행하려고 하면 오류가 발생합니다. 또한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이전의 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 버전에 연결할 때 ISOLATIONLEVEL_SNAPSHOT을 *isoLevel*로 지정하면 XACT_E_ISOLATIONLEVEL 오류가 발생합니다.|  
|*isoFlags*[in]|OLE DB Driver for SQL Server는 0이 아닌 모든 값에 대 한 오류를 반환합니다.|  
|*pOtherOptions*[in]|그렇지 않은 경우 null 인 경우에 OLE DB Driver for SQL Server 인터페이스에서 옵션 개체를 요청 합니다. 경우 XACT_E_NOTIMEOUT을 반환 하는 OLE DB Driver for SQL Server 옵션 개체의 *ulTimeout* 멤버가 0이 아닙니다. OLE DB Driver for SQL Server의 값을 무시 합니다 *szDescription* 멤버입니다.|  
|*pulTransactionLevel*[out]|그렇지 않은 경우 null 인 경우에 OLE DB Driver for SQL Server에는 트랜잭션의 중첩된 수준을 반환 합니다.|  
  
 OLE DB Driver for SQL Server 로컬 트랜잭션의 경우 구현 **itransaction:: Abort** 다음과 같은 매개 변수입니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|*pboidReason*[in]|설정된 경우 무시됩니다. NULL이어도 안전합니다.|  
|*fRetaining*[in]|TRUE인 경우 해당 세션을 위한 새 트랜잭션이 암시적으로 시작됩니다. 이 트랜잭션은 소비자가 커밋 또는 종료해야 합니다. FALSE 인 경우에 OLE DB Driver for SQL Server 세션에 대 한 자동 커밋 모드로 되돌립니다.|  
|*fAsync*[in]|비동기 중단 SQL Server 용 OLE DB 드라이버에서 지원 되지 않습니다. OLE DB Driver for SQL Server 값 FALSE 이면 XACT_E_NOTSUPPORTED를 반환 합니다.|  
  
 OLE DB Driver for SQL Server 로컬 트랜잭션의 경우 구현 **itransaction:: Commit** 다음과 같은 매개 변수입니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|*fRetaining*[in]|TRUE인 경우 해당 세션을 위한 새 트랜잭션이 암시적으로 시작됩니다. 이 트랜잭션은 소비자가 커밋 또는 종료해야 합니다. FALSE 인 경우에 OLE DB Driver for SQL Server 세션에 대 한 자동 커밋 모드로 되돌립니다.|  
|*grfTC*[in]|비동기 및 1 단계 반환 SQL Server 용 OLE DB 드라이버에서 지원 되지 않습니다. OLE DB Driver for SQL Server xacttc_sync 값 XACT_E_NOTSUPPORTED를 반환합니다.|  
|*grfRM*[in]|0이어야 합니다.|  
  
 세션의 SQL Server용 OLE DB 드라이버 행 집합은 행 집합 속성 DBPROP_ABORTPRESERVE 및 DBPROP_COMMITPRESERVE 값에 따라 로컬 커밋 또는 중단 작업에서 보존됩니다. 기본적으로 이러한 속성은 모두 VARIANT_FALSE이며 세션의 모든 SQL Server용 OLE DB 드라이버 행 집합은 중단 또는 커밋 작업 이후에 제거됩니다.  
  
 OLE DB Driver for SQL Server를 구현 하지 않습니다 합니다 **ITransactionObject** 인터페이스입니다. 소비자가 인터페이스에 대한 참조를 얻으려고 하면 E_NOINTERFACE가 반환됩니다.  
  
 이 예에서는 **ITransactionLocal**을 사용합니다.  
  
```  
// Interfaces used in the example.  
IDBCreateSession*   pIDBCreateSession   = NULL;  
ITransaction*       pITransaction       = NULL;  
IDBCreateCommand*   pIDBCreateCommand   = NULL;  
IRowset*            pIRowset            = NULL;  
  
HRESULT             hr;  
  
// Get the command creation and local transaction interfaces for the  
// session.  
if (FAILED(hr = pIDBCreateSession->CreateSession(NULL,  
     IID_IDBCreateCommand, (IUnknown**) &pIDBCreateCommand)))  
    {  
    // Process error from session creation. Release any references and  
    // return.  
    }  
  
if (FAILED(hr = pIDBCreateCommand->QueryInterface(IID_ITransactionLocal,  
    (void**) &pITransaction)))  
    {  
    // Process error. Release any references and return.  
    }  
  
// Start the local transaction.  
if (FAILED(hr = ((ITransactionLocal*) pITransaction)->StartTransaction(  
    ISOLATIONLEVEL_REPEATABLEREAD, 0, NULL, NULL)))  
    {  
    // Process error from StartTransaction. Release any references and  
    // return.  
    }  
  
// Get data into a rowset, then update the data. Functions are not  
// illustrated in this example.  
if (FAILED(hr = ExecuteCommand(pIDBCreateCommand, &pIRowset)))  
    {  
    // Release any references and return.  
    }  
  
// If rowset data update fails, then terminate the transaction, else  
// commit. The example doesn't retain the rowset.  
if (FAILED(hr = UpdateDataInRowset(pIRowset, bDelayedUpdate)))  
    {  
    // Get error from update, then terminate.  
    pITransaction->Abort(NULL, FALSE, FALSE);  
    }  
else  
    {  
    if (FAILED(hr = pITransaction->Commit(FALSE, XACTTC_SYNC, 0)))  
        {  
        // Get error from failed commit.  
        }  
    }  
  
if (FAILED(hr))  
    {  
    // Update of data or commit failed. Release any references and  
    // return.  
    }  
  
// Release any references and continue.  
```  
  
## <a name="see-also"></a>참고 항목  
 [트랜잭션](../../oledb/ole-db-transactions/transactions.md)   
 [스냅숏 격리 작업](../../oledb/features/working-with-snapshot-isolation.md)  
  
  
