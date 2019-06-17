---
title: CopyRecord, CopyTo 및 SaveToFile 메서드 예제 (VB) | Microsoft Docs
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
- CopyRecord method [ADO], Visual Basic example
- SaveToFile method [ADO], Visual Basic example
- CopyTo method [ADO], Visual Basic example
ms.assetid: 61a51b74-93cd-439c-877f-f3055499d39f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ea4614191ea8be88f801f92f1ca90eb5110b7dec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698602"
---
# <a name="copyrecord-copyto-and-savetofile-methods-example-vb"></a>CopyRecord, CopyTo 및 SaveToFile 메서드 예제 (VB)
이 예제를 사용 하 여 파일의 복사본을 만드는 방법을 보여 줍니다 [Stream](../../../ado/reference/ado-api/stream-object-ado.md) 하거나 [레코드](../../../ado/reference/ado-api/record-object-ado.md) 개체입니다. 인터넷 게시용 웹 폴더에 하나의 복사본이 만들어집니다. 다른 속성 및 표시 된 메서드를 포함 [Stream 형식](../../../ado/reference/ado-api/type-property-ado-stream.md)를 **열려**를 [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md), 및 [레코드 열기](../../../ado/reference/ado-api/open-method-ado-record.md)합니다.  
  
```  
'BeginCopyRecordVB  
  
'Note:  
' This sample requires that "C:\checkmrk.wmf" and  
' "https://MyServer/mywmf.wmf" exist.  
  
Option Explicit  
  
Private Sub Form_Load()  
    On Error GoTo ErrorHandler  
  
    ' Declare variables  
    Dim strPicturePath, strStreamPath, strStream2Path, _  
        strRecordPath, strStreamURL, strRecordURL As String  
    Dim objStream, objStream2 As Stream  
    Dim objRecord As Record  
    Dim objField As Field  
  
    ' Instantiate objects  
    Set objStream = New Stream  
    Set objStream2 = New Stream  
    Set objRecord = New Record  
  
    ' Initialize path and URL strings  
    strPicturePath = "C:\checkmrk.wmf"  
    strStreamPath = "C:\mywmf.wmf"  
    strStreamURL = "URL=https://MyServer/mywmf.wmf"  
    strStream2Path = "C:\checkmrk2.wmf"  
    strRecordPath = "C:\mywmf.wmf"  
    strRecordURL = "https://MyServer/mywmf2.wmf"  
  
    ' Load the file into the stream  
    objStream.Open  
    objStream.Type = adTypeBinary  
    objStream.LoadFromFile (strPicturePath)  
  
    ' Save the stream to a new path and filename  
    objStream.SaveToFile strStreamPath, adSaveCreateOverWrite  
  
    ' Copy the contents of the first stream to a second stream  
    objStream2.Open  
    objStream2.Type = adTypeBinary  
    objStream.CopyTo objStream2  
  
    ' Save the second stream to a different path  
    objStream2.SaveToFile strStream2Path, adSaveCreateOverWrite  
  
    ' Because strStreamPath is a Web Folder, open a Record on the URL  
    objRecord.Open "", strStreamURL  
  
    ' Display the Fields of the record  
    For Each objField In objRecord.Fields  
        Debug.Print objField.Name & ": " & objField.Value  
    Next  
  
    ' Copy the record to a new URL  
    objRecord.CopyRecord "", strRecordURL, , , adCopyOverWrite  
  
    ' Load each copy of the graphic into Image controls for viewing  
    Image1.Picture = LoadPicture(strPicturePath)  
    Image2.Picture = LoadPicture(strStreamPath)  
    Image3.Picture = LoadPicture(strStream2Path)  
    Image4.Picture = LoadPicture(strRecordPath)  
  
    ' clean up  
    objStream.Close  
    objStream2.Close  
    objRecord.Close  
    Set objStream = Nothing  
    Set objStream2 = Nothing  
    Set objRecord = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not objStream Is Nothing Then  
        If objStream.State = adStateOpen Then objStream.Close  
    End If  
    Set objStream = Nothing  
  
    If Not objStream2 Is Nothing Then  
        If objStream2.State = adStateOpen Then objStream2.Close  
    End If  
    Set objStream2 = Nothing  
  
    If Not objRecord Is Nothing Then  
        If objRecord.State = adStateOpen Then objRecord.Close  
    End If  
    Set objRecord = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndCopyRecordVB  
```  
  
## <a name="see-also"></a>관련 항목  
 [CopyRecord 메서드 (ADO)](../../../ado/reference/ado-api/copyrecord-method-ado.md)   
 [CopyTo 메서드 (ADO)](../../../ado/reference/ado-api/copyto-method-ado.md)   
 [LoadFromFile 메서드 (ADO)](../../../ado/reference/ado-api/loadfromfile-method-ado.md)   
 [Open 메서드 (ADO 레코드)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open 메서드 (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [레코드 개체 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [SaveToFile 메서드](../../../ado/reference/ado-api/savetofile-method.md)   
 [Stream 개체 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)   
 [Type 속성(ADO 스트림)](../../../ado/reference/ado-api/type-property-ado-stream.md)
