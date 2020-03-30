---
title: 기본 데이터 형식 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 59ac80cf-fc66-4493-933d-38e479c5f54d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9374c76a76aa12f60fc3fa5f911916f39000d8b4
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028457"
---
# <a name="basic-data-types-sample"></a>기본 데이터 형식 샘플

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

이 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 샘플 애플리케이션에서는 결과 집합 getter 메서드를 사용하여 기본 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터 형식 값을 검색하는 방법과 함께 결과 집합 update 메서드를 사용하여 이러한 값을 업데이트하는 방법을 보여 줍니다.

이 샘플의 코드 파일 이름은 BasicDT.java이며 다음과 같은 위치에 있습니다.

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\datatypes
```

## <a name="requirements"></a>요구 사항

이 샘플 애플리케이션을 실행하려면 mssql-jdbc jar 파일을 포함하도록 클래스 경로를 설정해야 합니다. 또한 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 샘플 데이터베이스에 대한 액세스 권한이 필요합니다. 클래스 경로를 설정하는 방법에 대한 자세한 내용은 [JDBC 드라이버 사용](../../connect/jdbc/using-the-jdbc-driver.md)을 참조하세요.

이 샘플에서는 필요한 테이블을 만들고 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 샘플 데이터베이스에 예제 데이터를 삽입합니다.

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]는 기본 설정된 JRE(Java Runtime Environment)에 따라 사용할 수 있는 mssql-jdbc 클래스 라이브러리 파일을 제공합니다. 선택할 JAR 파일에 대한 자세한 내용은 [System Requirements for the JDBC Driver](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)(JDBC Driver 시스템 요구 사항)를 참조하세요.

## <a name="example"></a>예제

다음 예제 코드에서는 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 데이터베이스에 연결한 다음, DataTypesTable 테스트 테이블에서 단일 데이터 행을 검색합니다. 검색한 후 사용자 지정 displayRow 메서드를 호출하여 \<SQLServerResultSet[ 클래스의 다양한 get](../../connect/jdbc/reference/sqlserverresultset-class.md)Type> 메서드를 사용하여 결과 집합의 모든 데이터를 표시합니다.

그런 다음, 샘플에서는 SQLServerResultSet 클래스의 다양한 update\<Type> 메서드를 사용하여 결과 집합의 데이터를 업데이트한 후, [updateRow](../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md) 메서드를 호출하여 해당 데이터를 데이터베이스에 다시 보관합니다.

마지막으로 샘플은 결과 집합의 데이터를 새로 고친 다음, 사용자 지정 displayRow 메서드를 다시 호출하여 결과 집합에 데이터를 표시합니다.

```java
import java.sql.Connection;
import java.sql.Date;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.sql.Time;
import java.sql.Timestamp;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;

import microsoft.sql.DateTimeOffset;

public class BasicDataTypes {
    private static final String tableName = "DataTypesTable";

    public static void main(String[] args) {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>";

        try (Connection con = DriverManager.getConnection(connectionUrl);
                Statement stmt = con.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_UPDATABLE);) {

            dropAndCreateTable(stmt);
            insertOriginalData(con);

            String SQL = "SELECT * FROM " + tableName;
            ResultSet rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("ORIGINAL DATA", rs);

            // Update the data in the result set.
            rs.updateString(2, "B");
            rs.updateString(3, "Some updated text.");
            rs.updateBoolean(4, true);
            rs.updateDouble(5, 77.89);
            rs.updateDouble(6, 1000.01);
            long timeInMillis = System.currentTimeMillis();
            Timestamp ts = new Timestamp(timeInMillis);
            rs.updateTimestamp(7, ts);
            rs.updateDate(8, new Date(timeInMillis));
            rs.updateTime(9, new Time(timeInMillis));
            rs.updateTimestamp(10, ts);

            // -480 indicates GMT - 8:00 hrs
            ((SQLServerResultSet) rs).updateDateTimeOffset(11, DateTimeOffset.valueOf(ts, -480));

            rs.updateRow();

            // Get the updated data from the database and display it.
            rs = stmt.executeQuery(SQL);
            rs.next();
            displayRow("UPDATED DATA", rs);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static void displayRow(String title,
            ResultSet rs) throws SQLException {
        System.out.println(title);
        System.out.println(rs.getInt(1) + " , " +                 // SQL integer type.
                rs.getString(2) + " , " +                         // SQL char type.
                rs.getString(3) + " , " +                         // SQL varchar type.
                rs.getBoolean(4) + " , " +                        // SQL bit type.
                rs.getDouble(5) + " , " +                         // SQL decimal type.
                rs.getDouble(6) + " , " +                         // SQL money type.
                rs.getTimestamp(7) + " , " +                      // SQL datetime type.
                rs.getDate(8) + " , " +                           // SQL date type.
                rs.getTime(9) + " , " +                           // SQL time type.
                rs.getTimestamp(10) + " , " +                     // SQL datetime2 type.
                ((SQLServerResultSet) rs).getDateTimeOffset(11)); // SQL datetimeoffset type.
        System.out.println();
    }

    private static void dropAndCreateTable(Statement stmt) throws SQLException {
        stmt.executeUpdate("if object_id('" + tableName + "','U') is not null" + " drop table " + tableName);

        String sql = "create table " + tableName + " (" + "c1 int, " + "c2 char(20), " + "c3 varchar(20), " + "c4 bit, "
                + "c5 decimal(10,5), " + "c6 money, " + "c7 datetime, " + "c8 date, " + "c9 time(7), "
                + "c10 datetime2(7), " + "c11 datetimeoffset(7), " + ");";

        stmt.execute(sql);
    }

    private static void insertOriginalData(Connection con) throws SQLException {
        String sql = "insert into " + tableName + " values( " + "?,?,?,?,?,?,?,?,?,?,?" + ")";
        try (PreparedStatement pstmt = con.prepareStatement(sql)) {
            pstmt.setObject(1, 100);
            pstmt.setObject(2, "original text");
            pstmt.setObject(3, "original text");
            pstmt.setObject(4, false);
            pstmt.setObject(5, 12.34);
            pstmt.setObject(6, 56.78);
            pstmt.setObject(7, new java.util.Date(1453500034839L));
            pstmt.setObject(8, new java.util.Date(1453500034839L));
            pstmt.setObject(9, new java.util.Date(1453500034839L));
            pstmt.setObject(10, new java.util.Date(1453500034839L));
            pstmt.setObject(11, new java.util.Date(1453500034839L));
            pstmt.execute();
        }
    }
}

```

## <a name="see-also"></a>참고 항목

[데이터 형식 작업 &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)
