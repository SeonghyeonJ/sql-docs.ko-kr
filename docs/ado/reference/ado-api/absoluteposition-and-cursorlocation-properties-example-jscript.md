---
title: AbsolutePosition 및 CursorLocation 속성 예제 (JScript) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- AbsolutePosition property [ADO], JScript example
- CursorLocation property [ADO], JScript example
ms.assetid: bff98617-a6ba-4f41-9c5f-915161e3ea31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f252bf8a7c4fb7ecac2b226f669f5bd114b90574
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156653"
---
# <a name="absoluteposition-and-cursorlocation-properties-example-jscript"></a>AbsolutePosition 및 CursorLocation 속성 예제 (JScript)
이 예제에서는 하는 방법을 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) 속성의 모든 레코드를 열거 하는 루프의 진행률을 추적할 수는 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)합니다. 사용 합니다 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) 속성을 사용 합니다 **AbsolutePosition** 클라이언트 커서에 커서를 설정 하 여 속성입니다. 잘라내기 및 메모장 이나 다른 텍스트 편집기에 다음 코드를 붙여넣고,으로 저장 **AbsolutePositionJS.asp**합니다.  
  
```  
<!-- BeginAbsolutePositionJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
  
<head>  
<title>AbsolutePosition and CursorLocation Properties Example (JScript)</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>AbsolutePosition and CursorLocation Properties Example (JScript)</h1>  
<%  
    // connection and recordset variables  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsEmployee = Server.CreateObject("ADODB.Recordset");  
        // display string  
    var strMessage;          
  
    try  
    {  
        // Open a recordset on the Employee table using  
        // a client-side cursor to enable AbsolutePosition property.  
        rsEmployee.CursorLocation = adUseClient;  
        rsEmployee.Open("employees", strCnxn, adOpenStatic, adLockOptimistic, adCmdTable);  
  
        // Write beginning of table to the document.  
        Response.Write('<table border="0" align="center">');  
        Response.Write('<tr class="thead2">');  
        Response.Write("<th>AbsolutePosition</th><th>Name</th><th>Hire Date</th></tr>");  
  
        while (!rsEmployee.EOF)  
        {  
            strMessage = "";  
  
            // Start a new table row.  
            strMessage = '<tr class="tbody">';  
  
            // First column in row contains AbsolutePosition value.  
            strMessage += "<td>" + rsEmployee.AbsolutePosition + " of " + rsEmployee.RecordCount + "</td>"  
  
            // First and last name are in first column.  
            strMessage += "<td>" + rsEmployee.Fields("FirstName") + " ";  
            strMessage += rsEmployee.Fields("LastName") + " " + "</td>";  
  
            // Hire date in second column.  
            strMessage += "<td>" + rsEmployee.Fields("HireDate") + "</td>";  
  
            // End the row.  
            strMessage += "</tr>";  
  
            // Write line to document.  
            Response.Write(strMessage);  
  
            // Get next record.  
            rsEmployee.MoveNext;  
        }  
  
        // Finish writing document.  
        Response.Write("</table>");  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // 'clean up  
        if (rsEmployee.State == adStateOpen)  
            rsEmployee.Close;  
        rsEmployee = null;  
    }  
%>  
  
</html>  
<!-- EndAbsolutePositionJS -->  
```  
  
## <a name="see-also"></a>관련 항목  
 [AbsolutePosition 속성 (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [CursorLocation 속성 (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)   
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
