---
description: sysmail_sentitems(Transact-SQL)
title: sysmail_sentitems (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_sentitems_TSQL
- sysmail_sentitems
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_sentitems database mail view
ms.assetid: 16eb2a44-cebb-4cec-93ac-e2498c39989f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 36846ca8cba5022bc1d4bc431419c6687a4af003
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546683"
---
# <a name="sysmail_sentitems-transact-sql"></a>sysmail_sentitems(Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  데이터베이스 메일에서 보내는 각 메시지당 한 개의 행을 포함합니다. 성공적으로 전송 된 메시지를 확인 하려는 경우 **sysmail_sentitems** 를 사용 합니다.  
  
 데이터베이스 메일에서 처리 되는 모든 메시지를 보려면 [transact-sql&#41;&#40;sysmail_allitems ](../../relational-databases/system-catalog-views/sysmail-allitems-transact-sql.md)를 사용 합니다. 실패 상태의 메시지만 보려면 [transact-sql&#41;&#40;sysmail_faileditems ](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md)을 사용 합니다. 보내지 않았거나 다시 시도 하는 메시지만 보려면 [sysmail_unsentitems &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md)를 사용 합니다. 전자 메일 첨부 파일을 보려면 [sysmail_mailattachments &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sysmail-mailattachments-transact-sql.md)를 사용 합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|메일 큐의 메일 항목 식별자입니다.|  
|**profile_id**|**int**|메시지를 보내는 데 사용되는 프로필의 식별자입니다.|  
|**사람과**|**varchar(max)**|메시지를 받는 사람의 전자 메일 주소입니다.|  
|**copy_recipients**|**varchar(max)**|메시지 복사본을 받는 사람의 전자 메일 주소입니다.|  
|**blind_copy_recipients**|**varchar(max)**|메시지 복사본을 받지만 메시지 머리글에 이름이 표시되지 않는 사람의 전자 메일 주소입니다.|  
|**subject**|**nvarchar (510)**|메시지의 제목 줄입니다.|  
|**body**|**varchar(max)**|메시지의 본문입니다.|  
|**body_format**|**varchar (20)**|메시지 본문의 형식입니다. 가능한 값은 **TEXT** 및 **HTML**입니다.|  
|**importance**|**varchar (6)**|메시지의 **중요도** 매개 변수입니다.|  
|**우편물**|**varchar (12)**|메시지의 **민감도** 매개 변수입니다.|  
|**file_attachments**|**varchar(max)**|전자 메일 메시지에 첨부되는 파일 이름 목록으로 각 파일 이름은 세미콜론으로 구분되어 있습니다.|  
|**attachment_encoding**|**varchar (20)**|메일 첨부 파일의 유형입니다.|  
|**쿼리**|**varchar(max)**|메일 프로그램이 실행하는 쿼리입니다.|  
|**execute_query_database**|**sysname**|메일 프로그램이 쿼리를 실행한 데이터베이스 컨텍스트입니다.|  
|**attach_query_result_as_file**|**bit**|값이 0이면 쿼리 결과가 전자 메일 메시지 본문의 내용 뒤에 포함됩니다. 값이 1이면 결과가 첨부 파일로 반환됩니다.|  
|**query_result_header**|**bit**|값이 1이면 쿼리 결과에 열 머리글이 포함됩니다. 값이 0이면 쿼리 결과에 열 머리글이 포함되지 않습니다.|  
|**query_result_width**|**int**|메시지의 **query_result_width** 매개 변수입니다.|  
|**query_result_separator**|**char(1)**|쿼리 출력에서 열을 구분하는 데 사용되는 문자입니다.|  
|**exclude_query_output**|**bit**|메시지의 **exclude_query_output** 매개 변수입니다. 자세한 내용은 [sp_send_dbmail &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)를 참조 하세요.|  
|**append_query_error**|**bit**|메시지의 **append_query_error** 매개 변수입니다. 0은 쿼리에 오류가 있을 때 데이터베이스 메일이 전자 메일 메시지를 보내지 않음을 나타냅니다.|  
|**send_request_date**|**datetime**|메시지가 메일 큐에 추가된 날짜와 시간입니다.|  
|**send_request_user**|**sysname**|메시지를 보낸 사용자입니다. 메시지의 보낸 사람: 필드가 아니라 데이터베이스 메일 프로시저의 사용자 컨텍스트입니다.|  
|**sent_account_id**|**int**|메시지를 보내는 데 사용되는 데이터베이스 메일 계정의 식별자입니다.|  
|**sent_status**|**varchar (8)**|메일의 상태입니다. 이 뷰에 대해 항상 **전송** 됩니다.|  
|**sent_date**|**datetime**|메시지를 보낸 날짜와 시간입니다.|  
|**last_mod_date**|**datetime**|행을 마지막으로 수정한 날짜와 시간입니다.|  
|**last_mod_user**|**sysname**|행을 마지막으로 수정한 사용자입니다.|  
  
## <a name="remarks"></a>설명  
 데이터베이스 메일 문제를 해결할 때는 이 뷰를 통해 성공적으로 보낸 메시지의 특성을 보고 문제의 근원을 확인할 수 있습니다. 데이터베이스 메일은 메시지가 SMTP 메일 서버로 성공적으로 제출되면 해당 메시지를 보낸 것으로 표시합니다. 보통 전자 메일은 몇 분 안에 도착하지만 SMTP 서버 문제로 인해 지연될 수 있습니다. 데이터베이스 메일은 SMTP 메일 서버에서 메시지를 수신하면 해당 메시지를 보낸 것으로 표시합니다. 배달할 수 없는 수신인 전자 메일 주소와 같이 SMTP 메일 서버에서 발생하는 전자 메일 오류는 데이터베이스 메일로 반환됩니다. 이러한 전자 메일은 배달되지 않아도 보낸 것으로 기록됩니다. 이러한 유형의 오류는 SMTP 서버에서 해결합니다. 또한 SMTP 메일 서버는 데이터베이스 메일 계정의 회신 전자 메일 주소로 배달할 수 없는 메시지 알림을 보냅니다.  
  
## <a name="permissions"></a>사용 권한  
 **Sysadmin** 고정 서버 역할 및 **databasemailuserrole** 데이터베이스 역할에 부여 됩니다. **Sysadmin** 고정 서버 역할의 멤버에 의해 실행 되는 경우이 뷰는 보낸 모든 메시지를 표시 합니다. 그 밖의 다른 사용자는 자신이 보낸 메시지만 볼 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 메일 메시징 개체](../../relational-databases/database-mail/database-mail-messaging-objects.md)  
  
  
