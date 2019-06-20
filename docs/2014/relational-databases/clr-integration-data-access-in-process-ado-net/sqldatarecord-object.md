---
title: SqlDataRecord 개체 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- SqlDataRecord object
- custom result sets [CLR integration]
ms.assetid: 2ed667fb-749c-4280-a8fb-650643683c8f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c688d41a1f27c6f3d620e9395d2a908d9b9cddd1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62874680"
---
# <a name="sqldatarecord-object"></a>SqlDataRecord 개체
  `SqlDataRecord` 개체는 관련 메타데이터와 함께 하나의 데이터 행을 나타냅니다.  
  
 관리되는 저장 프로시저는 `SqlDataReader`에서 제공되지 않은 결과 집합을 클라이언트로 보낼 수 있습니다. `SqlDataRecord` 클래스와 함께 `SendResultsStart` 개체의 `SendResultsRow`, `SendResultsEnd` 및 `SqlPipe` 메서드를 사용하면 저장 프로시저에서 사용자 지정 결과 집합을 클라이언트로 보낼 수 있습니다.  
  
 자세한 내용은 .NET Framework SDK 설명서의 `Microsoft.SqlServer.Server.SqlDataRecord` 클래스 참조 설명서를 참조하십시오.  
  
## <a name="example"></a>예제  
 다음 예에서는 새 직원 레코드를 만들어 호출자에게 반환합니다.  
  
 C#  
  
```  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void CreateNewRecordProc()  
{  
    // Variables.         
    SqlDataRecord record;  
  
    // Create a new record with the column metadata.  The constructor   
    // is able to accept a variable number of parameters.  
    record = new SqlDataRecord(new SqlMetaData("EmployeeID", SqlDbType.Int),  
                               new SqlMetaData("Surname", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("GivenName", SqlDbType.NVarChar, 20),  
                               new SqlMetaData("StartDate", SqlDbType.DateTime) );  
  
    // Set the record fields.  
    record.SetInt32(0, 0042);  
    record.SetString(1, "Funk");  
    record.SetString(2, "Don");  
    record.SetDateTime(3, new DateTime(2005, 7, 17));  
  
    // Send the record to the calling program.  
    SqlContext.Pipe.Send(record);  
  
}  
```  
  
 Visual Basic  
  
```  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub  CreateNewRecordVBProc ()  
    ' Variables.  
    Dim record As SqlDataRecord  
  
    ' Create a new record with the column metadata. The constructor is   
    ' able to accept a variable number of parameters  
  
    record = New SqlDataRecord(New SqlMetaData("EmployeeID", SqlDbType.Int), _  
                           New SqlMetaData("Surname", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("GivenName", SqlDbType.NVarChar, 20), _  
                           New SqlMetaData("StartDate", SqlDbType.DateTime))  
  
    ' Set the record fields.  
    record.SetInt32(0, 42)  
    record.SetString(1, "Funk")  
    record.SetString(2, "Don")  
    record.SetDateTime(3, New DateTime(2005, 7, 17))  
  
    ' Send the record to the calling program.  
    SqlContext.Pipe.Send(record)  
  
End Sub  
```  
  
## <a name="see-also"></a>관련 항목  
 [SqlPipe 개체](sqlpipe-object.md)  
  
  
