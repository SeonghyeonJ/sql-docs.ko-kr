---
title: GetObjectOwner 메서드 (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::raw_GetObjectOwner
- _Catalog::GetObjectOwner
helpviewer_keywords:
- GetObjectOwner method [ADOX]
ms.assetid: 8965adf0-9075-4125-8142-73eb700029c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ff85491cf7ca30e3f95526aa7043f321a65cccc5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67966273"
---
# <a name="getobjectowner-method-adox"></a>GetObjectOwner 메서드(ADOX)
에 있는 개체의 소유자를 반환 합니다는 [카탈로그](../../../ado/reference/adox-api/catalog-object-adox.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Owner = Catalog.GetObjectOwner(ObjectName, ObjectType [,ObjectTypeId])  
```  
  
## <a name="return-value"></a>반환 값  
 반환을 **문자열** 지정 하는 값을 [이름](../../../ado/reference/adox-api/name-property-adox.md) 의 [사용자](../../../ado/reference/adox-api/user-object-adox.md) 또는 [그룹](../../../ado/reference/adox-api/group-object-adox.md) 개체를 소유 하는 합니다.  
  
#### <a name="parameters"></a>매개 변수  
 *ObjectName*  
 A **문자열** 소유자를 반환할 개체의 이름을 지정 하는 값입니다.  
  
 *ObjectType*  
 A **긴** 하나일 수 있는 값의 합니다 [ObjectTypeEnum](../../../ado/reference/adox-api/objecttypeenum.md) 소유자를 가져올 개체의 형식을 지정 하는 상수입니다.  
  
 *ObjectTypeId*  
 (선택 사항) A **Variant** OLE DB 사양에 정의 되지 공급자 개체 형식의 GUID를 지정 하는 값입니다. 이 매개 변수는 필요한 경우 *ObjectType* 로 설정 된 **adPermObjProviderSpecific**고, 그렇지 않으면 사용 되지 않습니다.  
  
## <a name="remarks"></a>설명  
 공급자 개체 소유자 반환을 지원 하지 않는 경우 오류가 발생 합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [Catalog 개체(ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>관련 항목  
 [GetObjectOwner 및 SetObjectOwner 메서드 예제 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [SetObjectOwner 메서드](../../../ado/reference/adox-api/setobjectowner-method.md)
