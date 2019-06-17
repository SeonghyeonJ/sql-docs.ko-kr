---
title: LocalDB에 대 한 지원 | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 48c9955733672699e16cb4a00e28fa2f59717b80
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797092"
---
# <a name="support-for-localdb"></a>LocalDB 지원

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB의 경량 버전이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 사용할 수 있었던 이후 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]합니다. 이 항목에서는 LocalDB 인스턴스의 데이터베이스에 연결하는 방법에 대해 설명합니다.

## <a name="remarks"></a>Remarks

LocalDB 설치 및 LocalDB 인스턴스를 구성 하는 방법을 비롯 한 LocalDB에 대 한 자세한 내용은 참조는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서 항목에 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express LocalDB입니다.

간단히 말해, LocalDB를 사용 하 수 있습니다.

-   **sqllocaldb.exe i** 를 사용하여 기본 인스턴스의 이름을 확인할 수 있습니다.

-   **AttachDBFilename** 연결 문자열 키워드를 사용하여 서버가 연결해야 하는 데이터베이스 파일을 지정할 수 있습니다. **AttachDBFilename**을 사용할 때 **Database** 연결 문자열 키워드를 사용하여 데이터베이스 이름을 지정하지 않으면 애플리케이션이 닫힐 때 LocalDB 인스턴스에서 데이터베이스가 제거됩니다.

-   연결 문자열에 LocalDB 인스턴스를 지정합니다. 예를 들어, 다음은 샘플 SQLSRV 연결 문자열이입니다.

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    다음은 샘플 PDO_SQLSRV 연결 문자열입니다.  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

필요한 경우 sqllocaldb.exe를 사용하여 LocalDB 인스턴스를 만들 수 있습니다. 또한 sqlcmd.exe를 사용하여 LocalDB 인스턴스에서 데이터베이스를 추가하고 수정할 수 있습니다. `sqlcmd -S (localdb)\v11.0`)을 입력합니다. (명령줄에서 실행할 때와 동일한 결과 얻기 위해 올바른 계정으로 실행 해야 하는 IIS를 실행 하는 경우 참조 [를 사용 하 여 IIS에서 LocalDB 사용 전체, 2 부: 인스턴스 소유권](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) 자세한.)

다음은 연결 문자열 예 SQLSRV 드라이버를 사용 하 여 명명 된 myinstance 인스턴스는 LocalDB에서 데이터베이스에 연결 하는입니다.

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

다음은 연결 문자열 예 PDO_SQLSRV 드라이버를 사용 하 여 명명 된 myinstance 인스턴스는 LocalDB에서 데이터베이스에 연결 하는입니다.  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

LocalDB 설치에 대 한 지침을 참조 하세요. 합니다 [LocalDB 설명서](../../database-engine/configure-windows/sql-server-2016-express-localdb.md)합니다. Sqlcmd.exe를 사용 하 여 LocalDB 인스턴스에서 데이터를 수정 해야 합니다 [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)합니다.

## <a name="see-also"></a>참고 항목

[서버에 연결](../../connect/php/connecting-to-the-server.md)
