---
title: 'PDOStatement:: fetchObject | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 71ad1932-cab3-4c29-8950-f5e82547d3b5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 118a473e3e1675b81b732eb76f0271bbbe9d2e15
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936018"
---
# <a name="pdostatementfetchobject"></a>PDOStatement::fetchObject
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

다음 행을 개체로 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
mixed PDOStatement::fetchObject([ $class_name[,$ctor_args ]] )  
```  
  
#### <a name="parameters"></a>매개 변수  
$*class_name*: 만들 클래스의 이름을 지정하는 선택적 문자열입니다. 기본값은 stdClass입니다.  
  
$*ctor_args*: 사용자 지정 클래스 생성자에 대한 인수가 포함된 선택적 배열입니다.  
  
## <a name="return-value"></a>반환 값  
성공하면 클래스의 인스턴스와 함께 개체를 반환합니다. 속성이 열에 매핑됩니다. 실패하면 false를 반환합니다.  
  
## <a name="remarks"></a>Remarks  
PDO 지원이 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]의 버전 2.0에 추가되었습니다.  
  
## <a name="example"></a>예제  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetchObject();  
   print $result->Name;  
?>  
```  
  
## <a name="see-also"></a>참고 항목  
[PDOStatement 클래스](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
