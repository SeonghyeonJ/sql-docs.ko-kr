---
title: '3단계: ADO.NET을 사용하여 SQL에 연결하는 개념 증명 | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: aebe3dc6-3ee4-4d11-8e43-5d32b3f91490
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 743eab241fa9feb4a622054b3be48b887b804813
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957612"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-adonet"></a>3단계: ADO.NET을 사용하여 SQL에 연결하는 개념 증명

- 이전 문서:&nbsp;&nbsp;&nbsp;[2단계: ADO.NET 개발을 위한 SQL 데이터베이스 만들기](step-2-create-a-sql-database-for-ado-net-development.md)  
- 다음 문서:&nbsp;&nbsp;&nbsp;[4단계: ADO.NET을 사용하여 탄력적으로 SQL에 연결](step-4-connect-resiliently-to-sql-with-ado-net.md)  

  
이 C# 코드 예제는 개념 증명 으로만 간주 해야 합니다. 이 샘플 코드는 명확 하 게 하기 위해 단순화 되었으며 Microsoft에서 권장 하는 모범 사례를 나타내지는 않습니다.  
  
## <a name="step-1-connect"></a>1 단계: 연결
  
**SqlConnection** 메서드는 SQL 데이터베이스에 연결 하는 데 사용 됩니다.  


```csharp
    // C# , ADO.NET  
    using System;
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
  
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    Press any key to finish...  
    ****/  
```  


## <a name="step-2--execute-a-query"></a>2단계: 쿼리 실행  
  
ExecuteReader 메서드는 다음과 같습니다.  
  
- Sql SELECT 문을 SQL 시스템에 발급 합니다.  
- 결과 행에 대 한 액세스를 제공 하기 위해 SqlDataReader의 인스턴스를 반환 합니다.  
  
  
  
```csharp
    using System;  // C# , ADO.NET  
    using DT = System.Data;            // System.Data.dll  
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.SelectRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void SelectRows(QC.SqlConnection connection)  
            {  
                using (var command = new QC.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = DT.CommandType.Text;  
                    command.CommandText = @"  
    SELECT  
        TOP 5  
            COUNT(soh.SalesOrderID) AS [OrderCount],  
            c.CustomerID,  
            c.CompanyName  
        FROM  
                            SalesLT.Customer         AS c  
            LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh  
                ON c.CustomerID = soh.CustomerID  
        GROUP BY  
            c.CustomerID,  
            c.CompanyName  
        ORDER BY  
            [OrderCount] DESC,  
            c.CompanyName; ";  
      
                    QC.SqlDataReader reader = command.ExecuteReader();  
      
                    while (reader.Read())  
                    {  
                        Console.WriteLine("{0}\t{1}\t{2}",  
                            reader.GetInt32(0),  
                            reader.GetInt32(1),  
                            reader.GetString(2));  
                    }  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    1       29736   Action Bicycle Specialists  
    1       29638   Aerobic Exercise Company  
    1       29546   Bulk Discount Store  
    1       29741   Central Bicycle Specialists  
    1       29612   Channel Outlet  
    Press any key to finish...  
    ****/  
```  
  
  
  
## <a name="step-3-insert-a-row"></a>3 단계: 행 삽입  
  
  
이 예에서는 다음을 수행하는 방법을 보여 줍니다.  
  
- 매개 변수를 전달 하 여 SQL INSERT 문을 안전 하 게 실행 합니다.  
  - 매개 변수를 사용 하면 SQL 삽입 공격 으로부터 보호 됩니다.  
- 자동 생성 된 값을 검색 합니다.  
  
  
  
```csharp
    using System;  // C# , ADO.NET  
    using DT = System.Data;            // System.Data.dll  
    using QC = System.Data.SqlClient;  // System.Data.dll  
      
    namespace ProofOfConcept_SQL_CSharp  
    {  
        public class Program  
        {  
            static public void Main()  
            {  
                using (var connection = new QC.SqlConnection(  
                    "Server=tcp:YOUR_SERVER_NAME_HERE.database.windows.net,1433;" +
                    "Database=AdventureWorksLT;User ID=YOUR_LOGIN_NAME_HERE;" +
                    "Password=YOUR_PASSWORD_HERE;Encrypt=True;" +
                    "TrustServerCertificate=False;Connection Timeout=30;"  
                    ))  
                {  
                    connection.Open();  
                    Console.WriteLine("Connected successfully.");  
      
                    Program.InsertRows(connection);  
      
                    Console.WriteLine("Press any key to finish...");  
                    Console.ReadKey(true);  
                }  
            }  
      
            static public void InsertRows(QC.SqlConnection connection)  
            {  
                QC.SqlParameter parameter;  
      
                using (var command = new QC.SqlCommand())  
                {  
                    command.Connection = connection;  
                    command.CommandType = DT.CommandType.Text;  
                    command.CommandText = @"  
    INSERT INTO SalesLT.Product  
            (Name,  
            ProductNumber,  
            StandardCost,  
            ListPrice,  
            SellStartDate  
            )  
        OUTPUT  
            INSERTED.ProductID  
        VALUES  
            (@Name,  
            @ProductNumber,  
            @StandardCost,  
            @ListPrice,  
            CURRENT_TIMESTAMP  
            ); ";  
      
                    parameter = new QC.SqlParameter("@Name", DT.SqlDbType.NVarChar, 50);  
                    parameter.Value = "SQL Server Express 2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@ProductNumber", DT.SqlDbType.NVarChar, 25);  
                    parameter.Value = "SQLEXPRESS2014";  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@StandardCost", DT.SqlDbType.Int);  
                    parameter.Value = 11;  
                    command.Parameters.Add(parameter);  
      
                    parameter = new QC.SqlParameter("@ListPrice", DT.SqlDbType.Int);  
                    parameter.Value = 12;  
                    command.Parameters.Add(parameter);  
      
                    int productId = (int)command.ExecuteScalar();  
                    Console.WriteLine("The generated ProductID = {0}.", productId);  
                }  
            }  
        }  
    }  
    /**** Actual output:  
    Connected successfully.  
    The generated ProductID = 1000.  
    Press any key to finish...  
    ****/  
```
