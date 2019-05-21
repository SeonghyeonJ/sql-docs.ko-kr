---
title: sys.dm_exec_xml_handles (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_xml_handles
- dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles_TSQL
- sys.dm_exec_xml_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_xml_handles dynamic management function
ms.assetid: a873ce0f-6955-417a-96a1-b2ef11a83633
author: pmasl
ms.author: pelopes
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ed7479109ef50ee3744b3a9acafc17a799670cd1
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65944487"
---
# <a name="sysdmexecxmlhandles-transact-sql"></a>sys.dm_exec_xml_handles(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  으로 열린 활성 핸들에 대 한 정보를 반환 **sp_xml_preparedocument**합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
dm_exec_xml_handles (session_id | 0 )  
```  
  
## <a name="arguments"></a>인수  
 *session_id* | 0,  
 세션의 ID입니다. 하는 경우 *session_id* 을 지정 하면이 함수는 지정된 된 세션에서 XML 핸들에 대 한 정보를 반환 합니다.  
  
 0을 지정하면 모든 세션의 모든 XML 핸들에 대한 정보가 반환됩니다.  
  
## <a name="table-returned"></a>반환된 테이블  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|이 XML 문서 핸들을 보유한 세션의 세션 ID입니다.|  
|**document_id**|**int**|반환 된 XML 문서 핸들 ID **sp_xml_preparedocument**합니다.|  
|**namespace_document_id**|**int**|세 번째 매개 변수로 전달 된 관련된 네임 스페이스 문서에 사용 되는 내부 핸들 ID **sp_xml_preparedocument**합니다. 네임스페이스 문서가 없으면 NULL이 됩니다.|  
|**sql_handle**|**varbinary(64)**|해당 핸들이 정의된 SQL 코드 텍스트에 대한 핸들입니다.|  
|**statement_start_offset**|**int**|현재 실행 중인 문자 수가 일괄 처리 또는 저장된 프로시저는 합니다 **sp_xml_preparedocument** 호출이 발생 합니다. 와 함께 사용할 수는 **sql_handle**의 **statement_end_offset**, 및 **sys.dm_exec_sql_text** 검색을 위한 동적 관리 함수는 현재 요청에 대해 문을 실행 합니다.|  
|**statement_end_offset**|**int**|현재 실행 중인 문자 수가 일괄 처리 또는 저장된 프로시저는 합니다 **sp_xml_preparedocument** 호출이 발생 합니다. 와 함께 사용할 수는 **sql_handle**의 **statement_start_offset**, 및 **sys.dm_exec_sql_text** 검색을 위한 동적 관리 함수는 현재 요청에 대해 문을 실행 합니다.|  
|**creation_time**|**datetime**|타임 스탬프 때 **sp_xml_preparedocument** 호출 되었습니다.|  
|**original_document_size_bytes**|**bigint**|구문 분석되지 않은 XML 문서의 크기(바이트)입니다.|  
|**original_namespace_document_size_bytes**|**bigint**|구문 분석되지 않은 XML 네임스페이스 문서의 크기(바이트)입니다. 네임스페이스 문서가 없으면 NULL이 됩니다.|  
|**num_openxml_calls**|**bigint**|이 문서 핸들을 사용하는 OPENXML 호출 수입니다.|  
|**row_count**|**bigint**|이 문서 핸들에 대해 이전의 모든 OPENXML 호출에서 반환된 행 수입니다.|  
|**dormant_duration_ms**|**bigint**|마지막 OPENXML 호출 이후의 시간(밀리초)입니다. OPENXML 호출 되지 않았습니다, 이후의 밀리초를 반환 합니다 **sp_xml_preparedocumen**호출 합니다.|  
  
## <a name="remarks"></a>Remarks  
 수명을 **sql_handles** 호출을 실행 하는 SQL 텍스트를 검색 하는 데 **sp_xml_preparedocument** 쿼리를 실행 하는 데 사용 하는 캐시 된 계획 보다 깁니다. 캐시에서 쿼리 텍스트를 사용할 수 없는 경우에는 함수 결과에 제공된 정보를 사용하여 데이터를 검색할 수 없습니다. 많은 대용량 일괄 처리를 실행할 때 이러한 문제가 발생할 수 있습니다.  
  
## <a name="permissions"></a>사용 권한  
 호출자가 소유하지 않은 세션 또는 세션 ID를 모두 보려면 서버에 대한 VIEW SERVER STATE 권한이 필요합니다. 호출자는 항상 자신의 현재 세션 ID를 볼 수 있습니다.      
  
## <a name="examples"></a>예  
 다음 예에서는 활성 핸들을 모두 선택합니다.  
  
```  
SELECT * FROM sys.dm_exec_xml_handles(0);  
```  
  
## <a name="see-also"></a>관련 항목  
 <br>[동적 관리 뷰 및 함수 (TRANSACT-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
 <br>[실행 관련 동적 관리 뷰 및 함수 (TRANSACT-SQL)](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
 <br>[sp_xml_preparedocument (Transact-SQL)](../system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[sp_xml_removedocument (Transact-SQL)](../system-stored-procedures/sp-xml-removedocument-transact-sql.md)


 
  
  
