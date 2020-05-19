---
title: IRowsetFastLoad::Commit(OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- IRowsetFastLoad::Commit (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- Commit method
ms.assetid: 19de9128-b91a-4626-847f-af721edaa24e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5ffa5ebbb222af1806033d7cf7b935049f759afc
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82704848"
---
# <a name="irowsetfastloadcommit-ole-db"></a>IRowsetFastLoad::Commit(OLE DB)
  일괄 삽입되는 행의 끝을 표시하고 행을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 씁니다. 샘플은 [IRowsetFastLoad를 사용한 데이터 대량 복사&#40;OLE DB&#41;](irowsetfastload-ole-db.md) 및 [IROWSETFASTLOAD와 ISEQUENTIALSTREAM을 사용하여 SQL SERVER로 BLOB 데이터 전송&#40;OLE DB&#41;](../native-client-ole-db-how-to/send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)을 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT Commit(  
BOOL   
fDone  
);  
  
```  
  
## <a name="arguments"></a>인수  
 *fDone*[in]  
 FALSE인 경우 행 집합은 계속 유효하며 소비자가 행을 추가로 삽입할 수 있습니다. TRUE인 경우 행 집합은 유효하지 않게 되며 소비자가 행을 추가로 삽입할 수 없습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 S_OK  
 메서드가 성공했으며 삽입한 모든 데이터가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 기록되었습니다.  
  
 E_FAIL  
 공급자 관련 오류가 발생했습니다. 오류 정보에서 공급자 관련 오류 텍스트를 검색하십시오.  
  
 E_UNEXPECTED  
 이전에 **IRowsetFastLoad::Commit** 메서드에 의해 무효화된 대량 복사 행 집합에서 메서드가 호출되었습니다.  
  
## <a name="remarks"></a>설명  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 공급자 대량 복사 행 집합은 지연 업데이트 모드 행 집합으로 동작 합니다. 사용자가 행 집합을 통해 행 데이터를 삽입하면 삽입된 행은 **IRowsetUpdate**를 지원하는 행 집합에서 보류 중인 삽입과 같은 방법으로 처리됩니다.  
  
 **IRowsetUpdate::Update** 메서드를 사용하여 보류 중인 행을 SQL Server 인스턴스로 전송하는 것과 같은 방법으로 소비자는 대량 복사 행 집합에 대해 **Commit** 메서드를 호출하여 삽입된 행을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 테이블에 써야 합니다.  
  
 소비자가 **Commit** 메서드를 호출하지 않고 대량 복사 행 집합에 대한 참조를 해제하면 기존에 쓰지 않은 삽입된 행이 모두 손실됩니다.  
  
 소비자는 *fDone* 인수를 FALSE로 설정하고 **Commit** 메서드를 호출하여 삽입된 행을 일괄 처리할 수 있습니다. *fDone*을 TRUE로 설정하면 행 집합이 무효화됩니다. 무효화된 대량 복사 행 집합에는 **ISupportErrorInfo** 인터페이스 및 **IRowsetFastLoad::Release** 메서드만 지원됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IRowsetFastLoad &#40;OLE DB&#41;](irowsetfastload-ole-db.md)  
  
  
