---
title: IndexNulls 속성 예제 (VB) | Microsoft Docs
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
- IndexNulls property [ADOX], Visual Basic example
ms.assetid: 45204669-32c0-4690-aab9-ddf0fd71ae48
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 895082ffe456e38ccaf120688e2bf77c1b410344
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63213340"
---
# <a name="indexnulls-property-example-vb"></a>IndexNulls 속성 예제(VB)
이 예제에서는 합니다 [IndexNulls](../../../ado/reference/adox-api/indexnulls-property-adox.md) 의 속성을 [인덱스](../../../ado/reference/adox-api/index-object-adox.md)합니다. 코드는 새 인덱스를 만들고 값을 설정 **IndexNulls** (list1 목록 상자)에서 사용자 입력을 기반으로 합니다. 그런 다음, **인덱스** 에 추가 됩니다 합니다 **직원** [테이블](../../../ado/reference/adox-api/table-object-adox.md) 에 *Northwind* [카탈로그](../../../ado/reference/adox-api/catalog-object-adox.md)합니다. 새 **인덱스** 에 적용 되는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 기반으로 **직원** 테이블 및 **레코드 집합** 열려 합니다. 새 레코드에 추가 됩니다는 **직원** 테이블을 사용 하 여를 **Null** 인덱싱된 필드의 값입니다. 설정에 따라 새 레코드가 표시 되는지 여부를 **IndexNulls** 속성입니다.  
  
```  
' BeginIndexNullsVB  
Private Sub cmdIndexNulls_Click()  
    IndexNullsX  
End Sub  
  
Sub IndexNullsX()  
  
    Dim cnn As New ADODB.Connection  
    Dim catNorthwind As New ADOX.Catalog  
    Dim idxNew As New ADOX.Index  
    Dim rstEmployees As New ADODB.Recordset  
    Dim varBookmark As Variant  
  
    ' Connect the catalog.  
    cnn.Open "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "data source=c:\Program Files\" & _  
        "Microsoft Office\Office\Samples\Northwind.mdb;"  
  
    Set catNorthwind.ActiveConnection = cnn  
  
    ' Append Country column to new index  
    idxNew.Columns.Append "Country"  
    idxNew.Name = "NewIndex"  
  
    ' Set IndexNulls based on user selection in listbox List1  
    Select Case List1.List(List1.ListIndex)  
        Case "Allow"  
            idxNew.IndexNulls = adIndexNullsAllow  
        Case "Ignore"  
            idxNew.IndexNulls = adIndexNullsIgnore  
        Case Else  
            End  
    End Select  
  
    'Append new index to Employees table  
    catNorthwind.Tables("Employees").Indexes.Append idxNew  
  
    rstEmployees.Index = idxNew.Name  
    rstEmployees.Open "Employees", cnn, adOpenKeyset, _  
        adLockOptimistic, adCmdTableDirect  
  
    With rstEmployees  
        ' Add a new record to the Employees table.  
        .AddNew  
        !FirstName = "Gary"  
        !LastName = "Haarsager"  
        .Update  
  
        ' Bookmark the newly added record  
        varBookmark = .Bookmark  
  
        ' Use the new index to set the order of the records.  
        .MoveFirst  
  
        Debug.Print "Index = " & .Index & _  
            ", IndexNulls = " & idxNew.IndexNulls  
        Debug.Print "  Country - Name"  
  
        ' Enumerate the Recordset. The value of the  
        ' IndexNulls property will determine if the newly  
        ' added record appears in the output.  
        Do While Not .EOF  
            Debug.Print "    " & _  
                IIf(IsNull(!Country), "[Null]", !Country) & _  
                " - " & !FirstName & " " & !LastName  
            .MoveNext  
        Loop  
  
        ' Delete new record because this is a demonstration.  
        .Bookmark = varBookmark  
        .Delete  
  
        .Close  
    End With  
  
    ' Delete new Index because this is a demonstration.  
    catNorthwind.Tables("Employees").Indexes.Delete idxNew.Name  
    Set catNorthwind = Nothing  
  
End Sub  
' EndIndexNullsVB  
```  
  
## <a name="see-also"></a>관련 항목  
 [Index 개체 (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [IndexNulls 속성(ADOX)](../../../ado/reference/adox-api/indexnulls-property-adox.md)
