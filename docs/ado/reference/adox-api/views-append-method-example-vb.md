---
title: Views Append 메서드 예제 (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b5b4c082-ac29-4f49-a8b8-e21b554c9b0d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5651edc56fbffd1c49373374123e8a030be675dc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281402"
---
# <a name="views-append-method-example-vb"></a>Views Append 메서드 예제(VB)
다음 코드를 사용 하는 방법에 설명를 [명령](../../../ado/reference/ado-api/command-object-ado.md) 개체와 [뷰](../../../ado/reference/adox-api/views-collection-adox.md) 컬렉션 [추가](../../../ado/reference/adox-api/append-method-adox-views.md) 기본 데이터 원본에 새 보기를 만드는 방법.  
  
```  
' BeginCreateViewVB  
Sub Main()  
    On Error GoTo CreateViewError  
  
    Dim cmd As New ADODB.Command  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Create the command representing the view.  
    cmd.CommandText = "Select * From Customers"  
  
    ' Create the new View  
    cat.Views.Append "AllCustomers", cmd  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set cmd = Nothing  
    Exit Sub  
  
CreateViewError:  
  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateViewVB  
```  
  
## <a name="see-also"></a>관련 항목  
 [ActiveConnection 속성 (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Append 메서드 (ADOX Views)](../../../ado/reference/adox-api/append-method-adox-views.md)   
 [Catalog 개체 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [뷰 개체 (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)   
 [Views 컬렉션(ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
