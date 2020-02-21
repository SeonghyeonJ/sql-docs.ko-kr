---
title: 기본 SQL Server 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: 65c7c211-96d3-4e65-a1de-1fe8d21348e7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 69c138e7eb5d2c4f6dbace0db59ce235e1c0a5f9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67993662"
---
# <a name="default-sql-server-data-types"></a>기본 SQL Server 데이터 형식
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

데이터를 서버에 보낼 때 사용자가 SQL Server 데이터 형식을 지정하지 않은 경우 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 는 데이터를 해당 PHP 데이터 형식에서 SQL Server 데이터 형식으로 변환합니다. 다음 표는 PHP 데이터 형식(서버에 전송할 데이터 형식) 및 기본 SQL Server 데이터 형식(데이터가 변환되는 데이터 형식)을 나열합니다. 서버에 데이터를 보낼 때 데이터 형식을 지정하는 방법에 대한 자세한 내용은 [방법: SQLSRV 드라이버를 사용하여 SQL Server 데이터 형식 지정](../../connect/php/how-to-specify-sql-server-data-types-when-using-the-sqlsrv-driver.md)을 참조하세요.  
  
|PHP 데이터 형식|SQLSRV 드라이버에서 기본 SQL Server 형식|PDO_SQLSRV 드라이버에서 기본 SQL Server 형식|  
|-----------------|------------------------------------------------|-----------------------------------------------------|  
|NULL|varchar(1)|지원되지 않음|  
|부울|bit|bit|  
|정수|int|int|  
|Float|float(24)|지원되지 않음|  
|String(8000바이트보다 작은 길이)|varchar(<string length>)|varchar(<string length>)|  
|문자열(8,000바이트를 초과하는 길이)|varchar(max)|varchar(max)|  
|리소스|지원되지 않습니다.|지원되지 않습니다.|  
|Stream(인코딩: 이진 아님)|varchar(max)|varchar(max)|  
|Stream(인코딩: 이진)|varbinary|varbinary|  
|Array|지원되지 않습니다.|지원되지 않습니다.|  
|Object|지원되지 않습니다.|지원되지 않습니다.|  
|DateTime(1)|Datetime|지원되지 않습니다.|  
  
## <a name="see-also"></a>참고 항목  
[상수&#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[데이터 형식 변환](../../connect/php/converting-data-types.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)

[PHP 형식](https://php.net/manual/language.types.php)

[데이터 형식(Transact-SQL)](https://docs.microsoft.com/sql/t-sql/data-types/data-types-transact-sql)  
  
