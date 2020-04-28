---
title: Name 속성 (ADOX) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Table::PutName
- _Table::GetName
- _Key::Name
- _Key::get_Name
- _Column::GetName
- _Index::Name
- _Index::put_Name
- _Column::PutName
- _Key::put_Name
- _Table::put_Name
- _User25::PutName
- _Index::get_Name
- _Column::get_Name
- _Group25::Name
- _Group25::get_Name
- _Column::Name
- _User25::get_Name
- _Table::Name
- _Group25::GetName
- _Index::PutName
- _Column::put_Name
- _Key::GetName
- _Table::get_Name
- _User25::Name
- _User25::put_Name
- _Index::GetName
- _User25::GetName
helpviewer_keywords:
- Name property [ADOX]
ms.assetid: 81b92baf-b6b9-4f4e-9f33-4503795518cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 52808cf9e90c6779efb9f95e385f8df501bae870
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965769"
---
# <a name="name-property-adox"></a>Name 속성(ADOX)
개체의 이름을 나타냅니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 **문자열** 값을 설정 하거나 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이름은 컬렉션 내에서 고유 하지 않아도 됩니다.  
  
 **Name** 속성은 [Column](../../../ado/reference/adox-api/column-object-adox.md), [Group](../../../ado/reference/adox-api/group-object-adox.md), [Key](../../../ado/reference/adox-api/key-object-adox.md), [Index](../../../ado/reference/adox-api/index-object-adox.md), [Table](../../../ado/reference/adox-api/table-object-adox.md)및 [User](../../../ado/reference/adox-api/user-object-adox.md) 개체에 대 한 읽기/쓰기입니다. **이름** 속성은 [카탈로그](../../../ado/reference/adox-api/catalog-object-adox.md), [프로시저](../../../ado/reference/adox-api/procedure-object-adox.md)및 [뷰](../../../ado/reference/adox-api/view-object-adox.md) 개체에서 읽기 전용입니다.  
  
 읽기/쓰기 개체 (**열**, **그룹**, **키**, **인덱스**, **테이블** 및 **사용자** 개체)의 경우 기본값은 빈 문자열 ("")입니다.  
  
> [!NOTE]
>  키의 경우이 속성은 이미 컬렉션에 추가 된 **키** 개체에 대해 읽기 전용입니다. 테이블의 경우이 속성은 이미 컬렉션에 추가 된 **테이블** 개체에 대해 읽기 전용입니다.  
  
## <a name="applies-to"></a>적용 대상  
  
||||  
|-|-|-|  
|[Column 개체(ADOX)](../../../ado/reference/adox-api/column-object-adox.md)|[Group 개체(ADOX)](../../../ado/reference/adox-api/group-object-adox.md)|[Index 개체(ADOX)](../../../ado/reference/adox-api/index-object-adox.md)|  
|[Key 개체(ADOX)](../../../ado/reference/adox-api/key-object-adox.md)|[Procedure 개체(ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)|[속성 개체(ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
|[Table 개체(ADOX)](../../../ado/reference/adox-api/table-object-adox.md)|[User 개체(ADOX)](../../../ado/reference/adox-api/user-object-adox.md)|[View 개체(ADOX)](../../../ado/reference/adox-api/view-object-adox.md)|  
  
## <a name="see-also"></a>참고 항목  
 [Columns 및 Tables Append 메서드, Name 속성 예제 (VB)](../../../ado/reference/adox-api/columns-and-tables-append-methods-name-property-example-vb.md)   
 [Keys Append 메서드, Key Type, RelatedColumn, RelatedTable 및 UpdateRule 속성 예제 (VB)](../../../ado/reference/adox-api/keys-append-method-key-type-relatedcolumn-relatedtable-example-vb.md)   
 [ParentCatalog 속성 예제(VB)](../../../ado/reference/adox-api/parentcatalog-property-example-vb.md)
