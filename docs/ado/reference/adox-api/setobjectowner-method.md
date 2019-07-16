---
title: SetObjectOwner 메서드 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50a02898c1694fa43b8bf522a1a1bca65300efda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67965235"
---
# <a name="setobjectowner-method"></a>SetObjectOwner 메서드
개체의 소유자를 지정 된 [카탈로그](../../../ado/reference/adox-api/catalog-object-adox.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>매개 변수  
 *ObjectName*  
 A **문자열** 소유자를 지정 하는 개체의 이름을 지정 하는 값입니다.  
  
 *ObjectType*  
 A **긴** 하나일 수 있는 값의 합니다 [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) 소유자 형식을 지정 하는 상수입니다.  
  
 *OwnerName*  
 **문자열** 지정 하는 값을 [이름](../../../ado/reference/adox-api/name-property-adox.md) 의 [사용자](../../../ado/reference/adox-api/user-object-adox.md) 또는 [그룹](../../../ado/reference/adox-api/group-object-adox.md) 개체를 소유 합니다.  
  
 *ObjectTypeId*  
 (선택 사항) A **Variant** OLE DB 사양에 정의 되지 않은 공급자 개체 형식의 GUID를 지정 하는 값입니다. 이 매개 변수는 필요한 경우 *ObjectType* 로 설정 된 **adPermObjProviderSpecific**고, 그렇지 않으면 사용 되지 않습니다.  
  
## <a name="remarks"></a>설명  
 공급자를 지정 하 여 개체 소유자를 지원 하지 않는 경우 오류가 발생 합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [Catalog 개체(ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>관련 항목  
 [GetObjectOwner 및 SetObjectOwner 메서드 예제 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner 메서드(ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
