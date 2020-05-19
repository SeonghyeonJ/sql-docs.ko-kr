---
title: 데이터 원본 삭제 (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [ODBC]
ms.assetid: 910e3e16-7b91-49d8-80bb-b4243926afaa
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c87d0123c5174461e4e3470b4e77ccb4bc5b10a1
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82701890"
---
# <a name="delete-a-data-source-odbc"></a>데이터 원본 삭제(ODBC)
  ODBC 관리자를 사용 하 여 프로그래밍 방식으로 ( [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)사용) 또는 파일 (파일 데이터 원본 이름)을 삭제 하 여 데이터 원본을 삭제할 수 있습니다.  
  
### <a name="to-delete-a-data-source-by-using-odbc-administrator"></a>ODBC 관리자를 사용하여 데이터 원본을 삭제하려면  
  
1.  **제어판**에서 **관리 도구**를 연 다음 **데이터 원본 (ODBC)** 을 두 번 클릭 합니다. 또는 명령 프롬프트에서 odbcad32.exe를 실행할 수도 있습니다.  
  
2.  **사용자 dsn**, **시스템 DSN**또는 **파일 dsn** 탭을 클릭 합니다.  
  
3.  삭제할 데이터 원본을 클릭합니다.  
  
4.  **제거**를 클릭 한 다음 삭제를 확인 합니다.  
  
## <a name="example"></a>예제  
 데이터 원본을 프로그래밍 방식으로 삭제 하려면 ODBC_REMOVE_DSN 또는 ODBC_REMOVE_SYS_DSN를 두 번째 매개 변수로 사용 하 여 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md) 를 호출 합니다.  
  
 다음 예에서는 데이터 원본을 프로그래밍 방식으로 삭제하는 방법을 보여 줍니다.  
  
```  
// remove_odbc_data_source.cpp  
// compile with: ODBCCP32.lib user32.lib  
#include <iostream>  
#include <windows.h>  
#include <odbcinst.h>  
  
int main() {   
   LPCSTR provider = "SQL Server";   // Windows SQL Server Driver  
   LPCSTR provider = "SQL Server";   // Windows SQL Server driver  
   LPCSTR provider2 = "SQL Server Native Client 11.0";   // SQL Server 2012 Native Client driver  
   LPCSTR dsnname = "DSN=data2";  
   BOOL retval = SQLConfigDataSource(NULL, ODBC_REMOVE_DSN, provider, dsnname);  
   std::cout << retval;   // 1 if successful  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server ODBC 드라이버 구성 방법 도움말 항목](../../database-engine/dev-guide/configuring-the-sql-server-odbc-driver-how-to-topics.md)  
  
  
