---
title: SQL 데이터 검색 및 분류 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 206bd656c1300a6436298c426697f6c1d47a9e86
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028377"
---
# <a name="sql-data-discovery-and-classification"></a>SQL 데이터 검색 및 분류

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

이 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 샘플 애플리케이션에서는 결과 집합 getter 메서드를 사용하여 해당 정보가 포함된 테이블에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 'SQL 데이터 검색 및 분류 정보'를 검색하는 방법을 보여줍니다.
  
이 샘플의 코드 파일 이름은 DataDiscoveryAndClassification.java이며 다음과 같은 위치에 있습니다.  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\dataclassification  
```

## <a name="requirements"></a>요구 사항  

이 샘플 애플리케이션을 실행하려면 mssql-jdbc jar 파일을 포함하도록 클래스 경로를 설정해야 합니다. 클래스 경로를 설정하는 방법에 대한 자세한 내용은 [JDBC 드라이버 사용](../../jdbc/using-the-jdbc-driver.md)을 참조하세요.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerResultSet;
import com.microsoft.sqlserver.jdbc.dataclassification.SensitivityProperty;


public class DataDiscoveryAndClassification {

    private static boolean featureSupported = false;

    public static void main(String[] args) {

        // Provides table name to be used for running test.
        String tableName = "JDBC_SQL_DATA_DISCOVERY_CLASSIFICATION";

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;username=<user>;password=<password>;";

        // Establish the connection.
        try (Connection con = DriverManager.getConnection(connectionUrl); Statement stmt = con.createStatement()) {
            verifySupportability(stmt);
            if (featureSupported) {
                createTable(stmt, tableName);
                runTests(stmt, tableName);
                drop_table(stmt, tableName);
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    /**
     * Verifies if SQL Discovery and Classification feature is applicable on target server.
     * 
     * @param stmt
     *        Statement object to work with
     */
    private static void verifySupportability(Statement stmt) {
        try {
            stmt.execute("SELECT * FROM SYS.SENSITIVITY_CLASSIFICATIONS");
            featureSupported = true;
        } catch (SQLException e) {
            // Error Code 208 : Object Not Found
            if (e.getErrorCode() == 208) {
                featureSupported = false;
                System.err.println("This feature is not supported on the target SQL Server.");
            }
        }
    }

    /**
     * Creates table for the test and sets tags for Sensitivity Classification
     * 
     * @param stmt
     *        Statement to work with
     * @param tableName
     *        Table to be created
     * @throws SQLException
     *         If an exception occurs
     */
    private static void createTable(Statement stmt, String tableName) throws SQLException {
        // Creates table for storing Supplier data
        stmt.execute("CREATE TABLE " + tableName + " (" + "[Id] [int] IDENTITY(1,1) NOT NULL,"
                + "[CompanyName] [nvarchar](40) NOT NULL," + "[ContactName] [nvarchar](50) NULL,"
                + "[ContactTitle] [nvarchar](40) NULL," + "[City] [nvarchar](40) NULL,"
                + "[Country] [nvarchar](40) NULL," + "[Phone] [nvarchar](30) MASKED WITH (FUNCTION = 'default()') NULL,"
                + "[Fax] [nvarchar](30) MASKED WITH (FUNCTION = 'default()') NULL," + "CONSTRAINT [PK_" + tableName
                + "] PRIMARY KEY CLUSTERED" + "([Id] ASC "
                + ")WITH (STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF) ON [PRIMARY]" + ") ON [PRIMARY]");

        // Set Sensitivity Classification tags to table columns
        stmt.execute("ADD SENSITIVITY CLASSIFICATION TO " + tableName
                + ".CompanyName WITH (LABEL='PII', LABEL_ID='L1', INFORMATION_TYPE='Company name', INFORMATION_TYPE_ID='COMPANY')");
        stmt.execute("ADD SENSITIVITY CLASSIFICATION TO " + tableName
                + ".ContactName WITH (LABEL='PII', LABEL_ID='L1', INFORMATION_TYPE='Person name', INFORMATION_TYPE_ID='NAME')");
        stmt.execute("ADD SENSITIVITY CLASSIFICATION TO " + tableName
                + ".Phone WITH (LABEL='PII', LABEL_ID='L1', INFORMATION_TYPE='Contact Information', INFORMATION_TYPE_ID='CONTACT')");
        stmt.execute("ADD SENSITIVITY CLASSIFICATION TO " + tableName
                + ".Fax WITH (LABEL='PII', LABEL_ID='L1', INFORMATION_TYPE='Contact Information', INFORMATION_TYPE_ID='CONTACT')");
    }

    /**
     * Runs query to fetch ResultSet from target table
     * 
     * @param stmt
     *        Statement to work with
     * @param tableName
     *        Name of table to fetch results from
     * @throws SQLException
     *         If an exception occurs
     */
    private static void runTests(Statement stmt, String tableName) throws SQLException {
        String query = "SELECT * FROM " + tableName;
        try (SQLServerResultSet rs = (SQLServerResultSet) stmt.executeQuery(query)) {
            printSensitivityClassification(rs);
        }
    }

    /**
     * Prints Sensitivity Classification data as received in ResultSet
     * 
     * @param rs
     *        Active ResultSet to read data from
     * @throws SQLException
     *         If an exception occurs
     */
    private static void printSensitivityClassification(SQLServerResultSet rs) throws SQLException {
        if (null != rs.getSensitivityClassification()) {
            for (int columnPos = 0; columnPos < rs.getSensitivityClassification().getColumnSensitivities().size();
                    columnPos++) {
                for (SensitivityProperty sp : rs.getSensitivityClassification().getColumnSensitivities().get(columnPos)
                        .getSensitivityProperties()) {
                    if (sp.getLabel() != null) {
                        System.out.println("Labels received for Column : " + columnPos);
                        System.out.println("Label ID: " + sp.getLabel().getId());
                        System.out.println("Label Name: " + sp.getLabel().getName());
                        System.out.println();
                    }

                    if (sp.getInformationType() != null) {
                        System.out.println("Information Types received for Column : " + columnPos);
                        System.out.println("Information Type ID: " + sp.getInformationType().getId());
                        System.out.println("Information Type Name: " + sp.getInformationType().getName());
                        System.out.println();
                    }
                }
            }
        }
    }

    /**
     * Drops the table created for test
     * 
     * @param stmt
     *        Statement to work with
     * @param tableName
     *        Table Name to be used
     * @throws SQLException
     *         If an exception occurs
     */
    private static void drop_table(Statement stmt, String tableName) throws SQLException {
        stmt.execute("DROP TABLE " + tableName);
    }
}
```

## <a name="see-also"></a>참고 항목

[샘플 JDBC 드라이버 애플리케이션](../../jdbc/code-samples/sample-jdbc-driver-applications.md)  
