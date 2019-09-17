---
title: sysmail_allitems (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
author: stevestein
ms.author: sstein
ms.openlocfilehash: be5c74e58e5c107a804903ab09de38b931f676e1
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70745460"
---
# <a name="sysmail_allitems-transact-sql"></a>sysmail_allitems(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  데이터베이스 메일이 처리하는 각 메시지당 한 개의 행을 포함합니다. 모든 메시지의 상태를 확인하고자 할 때 이 뷰를 사용합니다.  
  
 실패 상태의 메시지만 보려면 [sysmail_faileditems &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)을 사용 합니다. 보내지 않은 메시지만 보려면 [sysmail_unsentitems &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)을 사용 합니다. 보낸 메시지만 보려면 [sysmail_sentitems &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md)을 사용 합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|메일 큐의 메일 항목 식별자입니다.|  
|**profile_id**|**int**|메시지를 보내는 데 사용되는 프로필의 식별자입니다.|  
|**recipients**|**varchar(max)**|메시지를 받는 사람의 전자 메일 주소입니다.|  
|**copy_recipients**|**varchar(max)**|메시지 복사본을 받는 사람의 전자 메일 주소입니다.|  
|**blind_copy_recipients**|**varchar(max)**|메시지 복사본을 받지만 메시지 머리글에 이름이 표시되지 않는 사람의 전자 메일 주소입니다.|  
|**subject**|**nvarchar(510)**|메시지의 제목 줄입니다.|  
|**body**|**varchar(max)**|메시지 본문입니다.|  
|**body_format**|**varchar(20)**|메시지 본문의 형식입니다. 가능한 값은 TEXT 및 HTML입니다.|  
|**importance**|**varchar(6)**|메시지의 **중요도** 매개 변수입니다.|  
|**sensitivity**|**varchar(12)**|메시지의 **민감도** 매개 변수입니다.|  
|**file_attachments**|**varchar(max)**|전자 메일 메시지에 첨부되는 파일 이름 목록으로 각 파일 이름은 세미콜론으로 구분되어 있습니다.|  
|**attachment_encoding**|**varchar(20)**|메일 첨부 파일의 유형입니다.|  
|**query**|**varchar(max)**|메일 프로그램이 실행하는 쿼리입니다.|  
|**execute_query_database**|**sysname**|메일 프로그램이 쿼리를 실행한 데이터베이스 컨텍스트입니다.|  
|**attach_query_result_as_file**|**bit**|값이 0이면 쿼리 결과가 전자 메일 메시지 본문의 내용 뒤에 포함됩니다. 값이 1이면 결과가 첨부 파일로 반환됩니다.|  
|**query_result_header**|**bit**|값이 1이면 쿼리 결과에 열 머리글이 포함됩니다. 값이 0이면 쿼리 결과에 열 머리글이 포함되지 않습니다.|  
|**query_result_width**|**int**|메시지의 **query_result_width** 매개 변수입니다.|  
|**query_result_separator**|**char(1)**|쿼리 출력에서 열을 구분하는 데 사용되는 문자입니다.|  
|**exclude_query_output**|**bit**|메시지의 **exclude_query_output** 매개 변수입니다. 자세한 내용은 [sp_send_dbmail &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)을 참조 하세요.|  
|**append_query_error**|**bit**|메시지의 **append_query_error** 매개 변수입니다. 0은 쿼리에 오류가 있을 때 데이터베이스 메일이 전자 메일 메시지를 보내지 않음을 나타냅니다.|  
|**send_request_date**|**datetime**|메시지가 메일 큐에 추가된 날짜와 시간입니다.|  
|**send_request_user**|**sysname**|메시지를 보낸 사용자입니다. 메시지의 보낸 사람: 필드가 아니라 데이터베이스 메일 프로시저의 사용자 컨텍스트입니다.|  
|**sent_account_id**|**int**|메시지를 보내는 데 사용되는 데이터베이스 메일 계정의 식별자입니다.|  
|**sent_status**|**varchar(8)**|메일의 상태입니다. 가능한 값은<br /><br /> **sent** -메일을 보냈습니다.<br /><br /> **보내지** 않은 데이터베이스 메일이 여전히 메시지를 보내려고 시도 하 고 있습니다.<br /><br /> 다시 **시도** 하는 중 데이터베이스 메일 메시지를 보내지 못했지만 다시 보내려고 시도 하는 중입니다.<br /><br /> **실패** -데이터베이스 메일에서 메시지를 보낼 수 없습니다.|  
|**sent_date**|**datetime**|메시지를 보낸 날짜와 시간입니다.|  
|**last_mod_date**|**datetime**|행을 마지막으로 수정한 날짜와 시간입니다.|  
|**last_mod_user**|**sysname**|행을 마지막으로 수정한 사용자입니다.|  
  
## <a name="remarks"></a>설명  
 **Sysmail_allitems** 뷰를 사용 하 여 데이터베이스 메일에서 처리 한 모든 메시지의 상태를 확인할 수 있습니다. 데이터베이스 메일 문제를 해결할 때는 이 뷰를 사용하여 보낸 메시지의 특성을 보내지 않은 메시지의 특성과 비교하여 문제의 근원을 확인할 수 있습니다.  
  
 이 뷰에 표시 되는 시스템 테이블은 모든 메시지를 포함 하며 **msdb** 데이터베이스의 증가를 일으킬 수 있습니다. 테이블 크기를 줄이려면 뷰에서 오래된 메시지를 주기적으로 삭제하십시오. 자세한 내용은 [데이터베이스 메일 메시지 및 이벤트 로그를 보관 하는 SQL Server 에이전트 작업 만들기](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)를 참조 하세요.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할 및 **DatabaseMailUserRole** 데이터베이스 역할에 부여 됩니다. **Sysadmin** 고정 서버 역할의 멤버에 의해 실행 되는 경우이 뷰는 모든 메시지를 표시 합니다. 그 밖의 다른 사용자는 자신이 제출한 메시지만 볼 수 있습니다.  
  
  
