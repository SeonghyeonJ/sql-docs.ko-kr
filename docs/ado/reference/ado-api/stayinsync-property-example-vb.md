---
description: StayInSync 속성 예제(VB)
title: StayInSync 속성 예제 (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- StayInSync property [ADO], Visual Basic example
ms.assetid: b682bcc3-04b3-42b0-86f4-c17e0cd29baf
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a8a6eb8fb9d6be9433e11f641c6b29367680ba5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988644"
---
# <a name="stayinsync-property-example-vb"></a>StayInSync 속성 예제(VB)
이 예에서는 [StayInSync](./stayinsync-property.md) 속성을 통해 계층적 [레코드 집합](./recordset-object-ado.md)의 행에 쉽게 액세스 하는 방법을 보여 줍니다.  
  
 외부 루프에는 각 저자의 성과 이름, 상태 및 식별이 표시 됩니다. 각 행에 대해 추가 된 **레코드 집합** 은 [Fields](./fields-collection-ado.md) 컬렉션에서 검색 되 고 부모 **레코드 집합이** 새 행으로 이동 될 때마다 **StayInSync** 속성에 의해 자동으로 **rstTitleAuthor** 에 할당 됩니다. 내부 루프는 추가 된 레코드 집합의 각 행에서 4 개의 필드를 표시 합니다.  
  
```  
'BeginStayInSyncVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn As ADODB.Connection  
    Dim rst As ADODB.Recordset  
    Dim rstTitleAuthor As New ADODB.Recordset  
    Dim strCnxn As String  
  
    ' Open the connection with Data Shape attributes  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider=MSDataShape;Data Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Create a recordset  
    Set rst = New ADODB.Recordset  
    rst.StayInSync = True  
    rst.Open "SHAPE {select * from Authors} " & _  
                   "APPEND ( { select * from titleauthor} AS chapTitleAuthor " & _  
                   "RELATE au_id TO au_id) ", Cnxn, , , adCmdText  
  
    Set rstTitleAuthor = rst("chapTitleAuthor").Value  
    Do Until rst.EOF  
        Debug.Print rst!au_fname & " " & rst!au_lname & " " & _  
                   rst!State & " " & rst!au_id  
  
        Do Until rstTitleAuthor.EOF  
            Debug.Print rstTitleAuthor(0) & " " & rstTitleAuthor(1) & " " & _  
                   rstTitleAuthor(2) & " " & rstTitleAuthor(3)  
            rstTitleAuthor.MoveNext  
        Loop  
  
        rst.MoveNext  
    Loop  
  
    ' Clean up  
    rst.Close  
    Cnxn.Close  
    Set rst = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' Clean up  
    If Not rst Is Nothing Then  
        If rst.State = adStateOpen Then rst.Close  
    End If  
    Set rst = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndStayInSyncVB  
```  
  
## <a name="see-also"></a>참고 항목  
 [Fields 컬렉션 (ADO)](./fields-collection-ado.md)   
 [레코드 집합 개체 (ADO)](./recordset-object-ado.md)   
 [StayInSync 속성](./stayinsync-property.md)