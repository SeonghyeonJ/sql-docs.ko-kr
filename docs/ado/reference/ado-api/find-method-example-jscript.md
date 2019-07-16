---
title: Find 메서드 예제 (JScript) | Microsoft Docs
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
- Find method [ADO], JScript example
ms.assetid: adb5c37e-7874-41db-b4ee-572c1323deff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1b6a81b69fc16c587786685897c476c65937bb4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932631"
---
# <a name="find-method-example-jscript"></a>Find 메서드 예제(JScript)
이 예제에서는 합니다 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 개체의 [찾을](../../../ado/reference/ado-api/find-method-ado.md) 찾아 회사를 표시 하는 메서드를 ***Northwind*** 데이터베이스 이름이 G. 잘라내기 문자로 시작 하 고 붙여 넣습니다 다음 코드를 메모장 이나 다른 텍스트 편집기 및 저장 **붙여 넣고 FindJS.asp**합니다.  
  
```  
<!-- BeginFindJS -->  
<%@  Language=JavaScript %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<html>  
  
<head>  
<title>ADO Recordset.Find Example</title>  
<style>  
<!--  
BODY {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
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
  
<body bgcolor="white">  
  
<h1>ADO Recordset.Find Example</h1>  
<%  
    // connection and recordset variables  
    var Cnxn = Server.CreateObject("ADODB.Connection");  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsCustomers = Server.CreateObject("ADODB.Recordset");  
        // display string  
    var strMessage;      
    var strFind;  
  
    try  
    {  
            // open connection  
        Cnxn.Open(strCnxn);  
  
            //create recordset using object refs  
        SQLCustomers = "select * from Customers;";  
  
        rsCustomers.ActiveConnection = Cnxn;  
        rsCustomers.CursorLocation = adUseClient;  
        rsCustomers.CursorType = adOpenKeyset;  
        rsCustomers.LockType = adLockOptimistic;  
        rsCustomers.Source = SQLCustomers;  
  
        rsCustomers.Open();  
        rsCustomers.MoveFirst();  
  
            //find criteria  
        strFind = "CompanyName like 'g%'"  
        rsCustomers.Find(strFind);  
  
        if (rsCustomers.EOF) {  
            Response.Write("No records matched ");  
            Response.Write(SQLCustomers & "So cannot make table...");  
            Cnxn.Close();  
            Response.End();  
        }   
        else {  
            Response.Write('<table width="100%" border="2">');  
            Response.Write('<tr class="thead2">');  
            // Put Headings On The Table for each Field Name  
            for (thisField = 0; thisField < rsCustomers.Fields.Count; thisField++) {  
                fieldObject = rsCustomers.Fields(thisField);  
                Response.Write('<th width="' + Math.floor(100 / rsCustomers.Fields.Count) + '%">' + fieldObject.Name + "</th>");  
            }  
            Response.Write("</tr>");  
  
            while (!rsCustomers.EOF) {  
                Response.Write('<tr class="tbody">');  
                for(thisField=0; thisField<rsCustomers.Fields.Count; thisField++) {  
                    fieldObject = rsCustomers.Fields(thisField);  
                    strField = fieldObject.Value;  
                    if (strField == null)  
                        strField = "-Null-";  
                    if (strField == "")  
                        strField = "";  
                    Response.Write("<td>" + strField + "</td>");  
                }  
                rsCustomers.Find(strFind, 1, adSearchForward)  
                Response.Write("</tr>");  
            }  
            Response.Write("</table>");  
        }  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // clean up  
        if (rsCustomers.State == adStateOpen)  
            rsCustomers.Close;  
        if (Cnxn.State == adStateOpen)  
            Cnxn.Close;  
        rsCustomers = null;  
        Cnxn = null;  
    }  
%>  
  
</body>  
  
</html>  
<!-- EndFindJS -->  
```  
  
## <a name="see-also"></a>관련 항목  
 [Find 메서드 (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
