---
title: 데이터베이스 메일을 통해 보낸 메일 메시지의 상태 확인 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- e-mail [SQL Server], status information
- mail [SQL Server], status information
- Database Mail [SQL Server], message status
- status information [Database Mail]
ms.assetid: eb290f24-b52f-46bc-84eb-595afee6a5f3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 73d0cf3a374a7f3dda7797238d2c1702360aa955
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62872332"
---
# <a name="check-the-status-of-e-mail-messages-sent-with-database-mail"></a>데이터베이스 메일을 통해 보낸 전자 메일 메시지의 상태 확인
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용하여 데이터베이스 메일로 보낸 전자 메일 메시지의 상태를 확인하는 방법에 대해 설명합니다.  
  
-   **시작하기 전 주의 사항:**  
  
-   **다음을 사용하여 데이터베이스 메일을 통해 전송된 메일의 상태 보기:**  [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
 데이터베이스 메일은 보내는 전자 메일 메시지의 복사본을 유지하고 **msdb**데이터베이스의 **sysmail_allitems**, **sysmail_sentitems**, **sysmail_unsentitems** , **sysmail_faileditems** 뷰에 표시합니다. 데이터베이스 메일 외부 프로그램은 작업을 기록하고 Windows 애플리케이션 이벤트 로그와 **msdb** 데이터베이스의 **sysmail_event_log** 뷰를 통해 로그를 표시합니다. 전자 메일 메시지의 상태를 확인하려면 이 뷰에 대한 쿼리를 실행하세요. 전자 메일 메시지에는 **sent**, **unsent**, **retrying**및 **failed**의 4가지 가능한 상태 중 하나가 있습니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **데이터베이스 메일을 사용하여 보낸 전자 메일의 상태를 보려면**  
  
> [!NOTE]  
>  이 절차에 대한 예는 이 섹션의 뒷부분에 나오는 [예제(Transact-SQL)](#TsqlExample)을 참조하세요.  
  
1.  
  **sysmail_allitems** 테이블에서 **mailitem_id** 또는 **sent_status**로 메시지를 선택합니다.  
  
2.  전자 메일 메시지에 대해 외부 프로그램에서 반환된 상태를 확인하려면 다음 섹션에 나열된 방법으로 **sysmail_allitems** 를 **mailitem_id** 열의 **sysmail_event_log** 뷰에 조인합니다.  
  
     기본적으로 외부 프로그램은 성공적으로 전송된 메시지에 대한 정보를 기록하지 않습니다. 모든 메시지를 기록하려면 **데이터베이스 메일 구성 마법사** 의 **시스템 매개 변수 구성**페이지를 사용하여 로깅 수준을 자세히로 설정하세요.  
  
###  <a name="TsqlExample"></a> 예(Transact-SQL)  
 다음 예에서는 `danw` 로 전송되었지만 외부 프로그램에서 성공적으로 보내지 못한 모든 전자 메일 메시지에 대한 정보를 나열합니다. 이 문은 제목, 외부 프로그램에서 메시지를 보내지 못한 날짜와 시간, 데이터베이스 메일 로그의 오류 메시지를 나열합니다.  
  
```  
USE msdb ;  
GO  
  
-- Show the subject, the time that the mail item row was last  
-- modified, and the log information.  
-- Join sysmail_faileditems to sysmail_event_log   
-- on the mailitem_id column.  
-- In the WHERE clause list items where danw was in the recipients,  
-- copy_recipients, or blind_copy_recipients.  
-- These are the items that would have been sent  
-- to danw.  
  
SELECT items.subject,  
    items.last_mod_date  
    ,l.description FROM dbo.sysmail_faileditems as items  
INNER JOIN dbo.sysmail_event_log AS l  
    ON items.mailitem_id = l.mailitem_id  
WHERE items.recipients LIKE '%danw%'    
    OR items.copy_recipients LIKE '%danw%'   
    OR items.blind_copy_recipients LIKE '%danw%'  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 메일 로그 및 감사](database-mail-log-and-audits.md)  
  
  
