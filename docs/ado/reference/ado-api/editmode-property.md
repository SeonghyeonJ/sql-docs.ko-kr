---
title: EditMode 속성 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::EditMode
helpviewer_keywords:
- EditMode property
ms.assetid: a1b04bb2-8c8b-47f9-8477-bfd0368b6f68
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2988d031e523c5199bed6c4a557078c803e7bd6b
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698320"
---
# <a name="editmode-property"></a>EditMode 속성
현재 레코드의 편집 상태를 나타냅니다.  
  
## <a name="return-value"></a>반환 값  
 반환 된 [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md) 값입니다.  
  
## <a name="remarks"></a>Remarks  
 ADO는 현재 레코드와 연결 된 편집 버퍼를 유지 합니다. 이 속성에는이 버퍼에 변경 사항이 있는지 여부 또는 새 레코드를 만들어졌는지를 나타냅니다. 사용 된 **EditMode** 현재 레코드의 편집 상태를 확인 하는 속성입니다. 편집 프로세스가 중단 된 보류 중인 변경 내용에 대 한 테스트를 사용 해야 하는지 여부를 확인 합니다 [업데이트](../../../ado/reference/ado-api/update-method.md) 또는 [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) 메서드.  
  
 *즉시 업데이트 모드* 는 **EditMode** 속성으로 다시 설정 됩니다 **adEditNone** 호출에 성공한 후 합니다 **업데이트** 메서드 . 호출 하 여 [삭제](../../../ado/reference/ado-api/delete-method-ado-recordset.md) 삭제 되지 않습니다 성공적으로 데이터 원본에서 레코드를 (예를 들어, 때문에 참조 무결성 위반)를 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 편집 모드로 유지 됩니다 (**EditMode** = **adEditInProgress**). 따라서 **CancelUpdate** 현재 레코드를 이동 하기 전에 호출 해야 합니다 (예를 들어 [이동](../../../ado/reference/ado-api/move-method-ado.md)하십시오 [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), 또는 [닫기](../../../ado/reference/ado-api/close-method-ado.md) ).  
  
 *일괄 업데이트 모드* (공급자는 여러 변경 내용을 캐시 및 호출 된 경우에 기본 데이터 원본에 기록 합니다 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) 메서드), 값을 **EditMode**  첫 번째 작업이 수행 되 고 호출 하 여 다시 설정 되지 않습니다 하는 경우 속성이 변경 되는 **업데이트** 메서드. 후속 작업의 값을 변경 하지 마십시오 합니다 **EditMode** 속성을 다양 한 작업을 수행 하는 경우에 합니다. 예를 들어, 첫 번째 작업은 새 레코드를 추가 하 고 두 번째 기존 변경한 경우 레코드의 속성을 **EditMode** 은 여전히 **adEditAdd**합니다. 합니다 **EditMode** 속성을 다시 설정 되지 않습니다 **adEditNone** 호출한 후 될 때까지 **UpdateBatch**합니다. 수행 된 작업을 확인 하려면 설정 합니다 [필터](../../../ado/reference/ado-api/filter-property.md) 속성을 [adFilterPending](../../../ado/reference/ado-api/filtergroupenum.md) 보류 중인 변경 내용 사용 하 여 레코드만 표시 되며 검사 되도록는 [상태](../../../ado/reference/ado-api/status-property-ado-recordset.md) 데이터에 어떤 변경 사항이 생겼는지 확인 하려면 각 레코드의 속성입니다.  
  
> [!NOTE]
>  **EditMode** 현재 레코드를 필요한 경우에 유효한 값을 반환할 수 있습니다. **EditMode** 하는 경우 오류가 반환 됩니다 [BOF 또는 EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) 가 true 이면 현재 레코드를 삭제 하는 경우.  
  
## <a name="applies-to"></a>적용 대상  
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [CursorType, LockType, EditMode 속성 예제 (VB)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vb.md)   
 [CursorType, LockType, EditMode 속성 예제 (VC + +)](../../../ado/reference/ado-api/cursortype-locktype-and-editmode-properties-example-vc.md)   
 [AddNew 메서드 (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Delete 메서드 (ADO 레코드 집합)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [CancelUpdate 메서드 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [Update 메서드](../../../ado/reference/ado-api/update-method.md)
