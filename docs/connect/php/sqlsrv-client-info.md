---
title: sqlsrv_client_info | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_client_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_client_info
- sqlsrv_client_info
ms.assetid: 3e2d3679-436a-45d8-8bdc-7c633b65a720
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 861e686d4a64b1030224b8ec35551fade4188ca5
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67992834"
---
# <a name="sqlsrv_client_info"></a>sqlsrv_client_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

연결 및 클라이언트 스택에 대한 정보를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sqlsrv_client_info( resource $conn)  
```  
  
#### <a name="parameters"></a>매개 변수  
*$conn*: 클라이언트가 연결된 연결 리소스입니다.  
  
## <a name="return-value"></a>Return Value  
아래 표에 설명된 키가 있는 결합형 배열이거나 연결 리소스가 null인 경우 **false** 입니다.  
  
**SQL Server 버전 3.2 및 3.1용 PHP**:  
  
|키|Description|  
|-------|---------------|  
|DriverDllName|MSODBCSQL11.DLL(ODBC Driver 11 for SQL Server)|  
|DriverODBCVer|ODBC 버전(xx.yy)|  
|DriverVer|ODBC Driver 11 for SQL Server DLL 버전:<br /><br />xx.yy.zzzz([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 버전 3.2 또는 3.1)|  
|ExtensionVer|php_sqlsrv.dll 버전:<br /><br />3.2.xxxx.x([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 버전 3.2)<br /><br />3.1.xxxx.x([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 버전 3.1)|  
  
**SQL Server 3.0 및 2.0 버전용 PHP**:  
  
|키|Description|  
|-------|---------------|  
|DriverDllName|SQLNCLI10.DLL([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 버전 2.0)|  
|DriverODBCVer|ODBC 버전(xx.yy)|  
|DriverVer|다음은 SQL Server Native Client DLL 버전입니다.<br /><br />10.50.xxx([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 버전 2.0)|  
|ExtensionVer|php_sqlsrv.dll 버전:<br /><br />2.0.xxxx.x([!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 버전 2.0)|  
  
## <a name="example"></a>예제  
다음 예제에서는 명령줄에서 예제가 실행될 때 콘솔에 클라이언트 정보를 씁니다. 이 예제에서는 SQL Server가 로컬 컴퓨터에 설치된 것으로 가정합니다. 모든 출력은 명령줄에서 예제가 실행될 때 콘솔에 기록됩니다.  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
if( $client_info = sqlsrv_client_info( $conn))  
{  
       foreach( $client_info as $key => $value)  
      {  
              echo $key.": ".$value."\n";  
      }  
}  
else  
{  
       echo "Client info error.\n";  
}  
  
/* Close connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>참고 항목  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)

[설명서의 코드 예제 정보](../../connect/php/about-code-examples-in-the-documentation.md)  
  
