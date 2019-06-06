---
title: CancelBatch 메서드 (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 572738c966651e35f2980ea75c3770ddc4bd029d
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66696173"
---
# <a name="cancelbatch-method-ado"></a>CancelBatch 메서드(ADO)
보류 중인 일괄 처리 업데이트를 취소합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>매개 변수  
 *AffectRecords*  
 (선택 사항) [AffectEnum](../../../ado/reference/ado-api/affectenum.md) 레코드 수를 나타내는 값을 **CancelBatch** 메서드 적용 됩니다.  
  
## <a name="remarks"></a>Remarks  
 사용 하 여는 **CancelBatch** 에서 보류 중인 업데이트를 취소 하는 메서드를 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 일괄 업데이트 모드에서. 경우는 **Recordset** 즉시 업데이트 모드에 호출 **CancelBatch** 없이 **adAffectCurrent** 오류가 발생 합니다.  
  
 현재 레코드를 편집 하거나 호출 하는 경우 새 레코드를 추가 하는 경우 **CancelBatch**, ADO 첫 번째 호출을 [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) 캐시 된 변경 사항을 취소 하는 방법입니다. 그런 다음 모든 보류 중인 변경 내용을 합니다 **레코드 집합** 취소 됩니다.  
  
 현재 레코드 수 확인할 수 없습니다는 **CancelBatch** 새 레코드를 추가 하 고 있는 경우에 특히를 호출 합니다. 이러한 이유로 것이 좋습니다에 알려진된 위치에 현재 레코드 위치를 설정 하는 **레코드 집합** 후 합니다 **CancelBatch** 호출 합니다. 예를 들어 호출 된 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) 메서드.  
  
 공급자 경고를 반환 합니다 (예: 다른 사용자가 레코드를 삭제 된 경우) 기본 데이터 충돌로 인해 실패 하면 보류 중인 업데이트를 취소 하려고 합니다 [오류](../../../ado/reference/ado-api/errors-collection-ado.md) 컬렉션 중단 하지는 않습니다 하지만 프로그램 실행 합니다. 런타임 오류는 요청 된 모든 레코드에 충돌이 있는 경우에 발생 합니다. 사용 합니다 [필터](../../../ado/reference/ado-api/filter-property.md) 속성 (**adFilterAffectedRecords**) 및 [상태](../../../ado/reference/ado-api/status-property-ado-recordset.md) 속성을 사용 하 여 충돌 레코드를 찾습니다.  
  
## <a name="applies-to"></a>적용 대상  
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [UpdateBatch 및 CancelBatch 메서드 예제 (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch 및 CancelBatch 메서드 예제 (VC + +)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel 메서드 (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel 메서드 (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelUpdate 메서드 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate 메서드 (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Clear 메서드 (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType 속성 (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [UpdateBatch 메서드](../../../ado/reference/ado-api/updatebatch-method.md)
