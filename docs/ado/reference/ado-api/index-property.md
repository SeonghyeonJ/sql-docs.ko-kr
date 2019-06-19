---
title: 인덱스 속성 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 21f8ec6ea0ed9cd1af8257dcd10b18f59903c929
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694797"
---
# <a name="index-property"></a>Index 속성
적용에 대 한 현재 인덱스의 이름을 나타내는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 개체입니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환을 **문자열** 값은 인덱스의 이름입니다.  
  
## <a name="remarks"></a>Remarks  
 명명 된 인덱스는 **인덱스** 속성이 이전에 선언 해야 기본 기본 테이블에는 **레코드 집합** 개체입니다. 즉, 인덱스 선언 해야 프로그래밍 방식으로 ADOX로 [인덱스](../../../ado/reference/adox-api/index-object-adox.md) 개체 또는 기본 테이블을 만들 때.  
  
 인덱스를 설정할 수 없는 경우 런타임 오류가 발생 합니다. 합니다 **인덱스** 다음과 같은 속성을 설정할 수 없습니다.  
  
-   내에 [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) 하거나 **RecordsetChangeComplete** 이벤트 처리기입니다.  
  
-   경우는 **레코드 집합** 작업을 계속 실행 중인 (에서 확인할 수 있습니다 합니다 [상태](../../../ado/reference/ado-api/state-property-ado.md) 속성).  
  
-   필터에 설정 된 경우는 **레코드 집합** 사용 하 여 합니다 [필터](../../../ado/reference/ado-api/filter-property.md) 속성입니다.  
  
 **인덱스** 속성 수 항상 성공적으로 설정 될 경우 합니다 **레코드 집합** 닫혀 있지만 **레코드 집합** 성공적으로 열리지 것입니다 또는 인덱스를 사용할 수 없습니다. 하는 경우는 기본 공급자는 인덱스를 지원 하지 않습니다.  
  
 인덱스를 설정할 수 있는 경우 현재 행 위치가 변경 될 수 있습니다. 이렇게 하면에 대 한 업데이트를 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) 속성인 시킨다 고는 **WillChangeRecordset**, **RecordsetChangeComplete**, [WillMove ](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), 및 [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) 이벤트입니다.  
  
 인덱스를 설정할 수 있는 경우 및 [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) 속성은 **adLockPessimistic** 하거나 **adLockOptimistic**, 다음 암시적 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) 작업이 수행 됩니다. 이 현재 및 영향을 받는 그룹을 해제합니다. 기존 필터가 해제 되 고 다시 정렬된 된 첫 번째 행을 현재 행 위치가 변경 됩니다 **레코드 집합**합니다.  
  
 합니다 **인덱스** 속성은 함께에서 사용 합니다 [Seek](../../../ado/reference/ado-api/seek-method.md) 메서드. 기본 공급자를 지원 하지 않는 경우는 **인덱스** 속성 이므로 **Seek** 메서드를 사용 하는 것이 좋습니다는 [찾을](../../../ado/reference/ado-api/find-method-ado.md) 메서드 대신 합니다. 확인 여부를 합니다 **레코드 집합** 개체가 사용 하 여 인덱스를 지원 합니다 [지원](../../../ado/reference/ado-api/supports-method.md) **(adIndex)** 메서드.  
  
 기본 제공 **인덱스** 동적와 관련이 없는 속성 [최적화](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) 속성을 모두 인덱스를 사용 하 여 처리 되지만 합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [Seek 메서드 및 인덱스 속성 예제 (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Index 개체 (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek 메서드](../../../ado/reference/ado-api/seek-method.md)
