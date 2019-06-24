---
title: sqlsrv_num_rows | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- API Reference, sqlsrv_num_rows
- sqlsrv_num_rows
ms.assetid: c832210e-bb2a-47b5-a505-160b02d1d95e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b8844ad89a8f0e7c1663bc8aadf8479764987b31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66802364"
---
# <a name="sqlsrvnumrows"></a>sqlsrv_num_rows
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

결과 집합의 행 수를 보고합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sqlsrv_num_rows( resource $stmt )  
```  
  
#### <a name="parameters"></a>매개 변수  
*$stmt*: 행 수를 계산할 결과 집합입니다.  
  
## <a name="return-value"></a>반환 값  
행 수를 계산하는 중 오류가 발생하면**false** 이고, 그렇지 않으면 결과 집합의 행 수를 반환합니다.  
  
## <a name="remarks"></a>Remarks  
sqlsrv_num_rows에는 클라이언트 쪽, 정적 또는 키 집합 커서가 필요하며 정방향 커서 또는 동적 커서를 사용하는 경우 **false**를 반환합니다. (정방향 커서가 기본값입니다.) 커서에 대한 자세한 내용은 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 및 [커서 유형&#40;SQLSRV 드라이버&#41;](../../connect/php/cursor-types-sqlsrv-driver.md)를 참조하세요.  
  
## <a name="example"></a>예제  
  
```  
<?php  
   $server = "server_name";  
   $conn = sqlsrv_connect( $server, array( 'Database' => 'Northwind' ) );  
  
   $stmt = sqlsrv_query( $conn, "select * from orders where CustomerID = 'VINET'" , array(), array( "Scrollable" => SQLSRV_CURSOR_KEYSET ));  
  
   $row_count = sqlsrv_num_rows( $stmt );  
  
   if ($row_count === false)  
      echo "\nerror\n";  
   else if ($row_count >=0)  
      echo "\n$row_count\n";  
?>  
```  
  
다음 샘플에서는 결과 집합이 둘 이상인 경우(일괄 처리 쿼리) 클라이언트 쪽 커서를 사용하는 경우에만 행 수를 사용할 수 있음을 보여 줍니다.  
  
```  
<?php  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
$tsql = "select * from HumanResources.Department";  
  
// Client-side cursor and batch statements  
$tsql = "select top 2 * from HumanResources.Employee;Select top 3 * from HumanResources.EmployeeAddress";  
  
// works  
$stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"buffered"));  
  
// fails  
// $stmt = sqlsrv_query($conn, $tsql);  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"forward"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"static"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"keyset"));  
// $stmt = sqlsrv_query($conn, $tsql, array(), array("Scrollable"=>"dynamic"));  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for first result set = $row_count\n";  
  
sqlsrv_next_result($stmt);  
  
$row_count = sqlsrv_num_rows( $stmt );  
echo "\nRow count for second result set = $row_count\n";  
?>  
```  
  
## <a name="see-also"></a>참고 항목  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)  
  
