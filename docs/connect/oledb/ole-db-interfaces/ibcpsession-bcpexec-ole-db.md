---
title: IBCPSession::BCPExec(OLE DB) | Microsoft Docs
description: IBCPSession::BCPExec(OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPExec (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPExec method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 6ace2ccd8fbba9c8c3566ad706754ed314152d4a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015489"
---
# <a name="ibcpsessionbcpexec-ole-db"></a>IBCPSession::BCPExec(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  대량 복사 작업을 수행합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT BCPExec(   
      DBROWCOUNT *pRowsCopied);  
```  
  
## <a name="remarks"></a>설명  
 **BCPExec** 메서드는 *IBCPSession::BCPInit* 메서드에 사용된 [eDirection](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) 매개 변수 값에 따라 데이터를 사용자 파일에서 데이터베이스 테이블로 복사하거나 그 반대로 복사합니다.  
  
 **BCPExec**를 호출하기 전에 올바른 사용자 파일 이름을 지정하여 **BCPInit** 메서드를 호출합니다. 그렇게 하지 않으면 오류가 반환됩니다. 단, 쿼리를 대량 복사하기(bulk copy out) 작업에 사용할 경우는 예외입니다. 이 경우 **BCPInit** 메서드에서 테이블 이름에 NULL을 지정한 다음, BCP_OPTION_HINTS 옵션을 사용하여 쿼리를 지정합니다.  
  
 **BCPExec** 메서드는 무한정 보류될 수 있는 유일한 대량 복사 메서드입니다. 따라서 비동기 모드를 지원하는 유일한 대량 복사 메서드입니다. 비동기 모드를 사용하려면 **BCPExec** 메서드를 호출하기 전에 공급자별 세션 속성 SSPROP_ASYNCH_BULKCOPY를 VARIANT_TRUE로 설정합니다. 이 속성은 DBPROPSET_SQLSERVERSESSION 속성 집합에서 사용할 수 있습니다. 완료를 테스트하려면 같은 매개 변수를 사용하여 **BCPExec**를 호출합니다. 대량 복사가 완료되지 않은 경우 **BCPExec** 메서드는 DB_S_ASYNCHRONOUS를 반환합니다. 또한 이 메서드는 서버로 전송하거나 서버에서 수신한 행 수에 대한 상태 개수를 *pRowsCopied* 인수에 반환합니다. 서버로 전송된 행은 일괄 처리의 끝에 도달할 때까지 커밋되지 않습니다.  
  
## <a name="arguments"></a>인수  
 *pRowsCopied*[out]  
 DWORD에 대한 포인터입니다. **BCPExec** 메서드는 성공적으로 복사된 행 수로 DWORD를 채웁니다. *pRowsCopied* 인수를 NULL로 설정하면 **BCPExec** 메서드에서 이 인수를 무시합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 S_OK  
 메서드가 성공했습니다.  
  
 E_FAIL  
 공급자 관련 오류가 발생했습니다. 자세한 내용을 보려면 [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) 인터페이스를 사용하세요.  
  
 E_UNEXPECTED  
 예기치 않은 메서드가 호출되었습니다. 예를 들어 이 메서드를 호출하기 전에 **BCPInit** 메서드를 호출하지 않았습니다. BCP_OPTION_ABORT 옵션을 사용하여 작업이 중단된 이후에 **BCPExec** 메서드를 호출한 경우에도 발생합니다.  
  
 E_OUTOFMEMORY  
 메모리 부족 오류가 발생했습니다.  
  
 DB_S_ENDOFROWSET  
 대량 복사 작업이 완료되었고 데이터 전송이 모두 완료되었습니다.  
  
 DB_S_ASYNCHRONOUS  
 행의 현재 일괄 처리가 복사되었습니다. 다음 일괄 처리를 전송하려면 **BCPExec** 메서드를 다시 호출합니다.  
  
 DB_S_ERRORSOCCURRED  
 대량 복사 작업 동안 오류가 발생하여 일부 행이 복사되지 않았습니다. 오류 수는 아직 허용되는 최대 오류 수보다 적습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [대량 복사 작업 수행](../../oledb/features/performing-bulk-copy-operations.md)  
  
  
