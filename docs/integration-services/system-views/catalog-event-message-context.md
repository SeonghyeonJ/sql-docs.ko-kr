---
title: catalog.event_message_context | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 273a54f8-b107-4f36-9461-2b475644760d
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b074634cb838b81c6e5e544d2d1b0be87ba15d9d
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2019
ms.locfileid: "58272889"
---
# <a name="catalogeventmessagecontext"></a>catalog.event_message_context
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버의 실행에 대한 실행 이벤트 메시지와 연결된 조건에 대한 정보를 표시합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|Context_id|BIGINT|오류 컨텍스트의 고유 ID입니다.|  
|Event_message_id|BIGINT|컨텍스트와 관련된 메시지의 고유 ID입니다.|  
|Context_depth|ssNoversion|수준이 증가함에 따라 컨텍스트가 오류에서 더 멀어집니다. 오류가 발생하면 컨텍스트 수준이 1에서 시작합니다. 값 0은 실행이 시작되기 전의 패키지 상태를 나타냅니다.|  
|Package_path|Nvarchar(max)|컨텍스트 원본의 패키지 경로입니다.|  
|Context_type|SMALLINT|컨텍스트의 원본인 개체의 유형입니다. 컨텍스트 유형 목록은 **주의** 섹션을 참조하십시오.|  
|Context_source_name|Nvarchar(4000)|컨텍스트의 원본인 개체의 이름입니다.|  
|Context_source_id|Nvarchar(38)|컨텍스트의 원본인 개체의 고유 ID입니다.|  
|Property_name|Nvarchar(4000)|컨텍스트의 원본에 연결된 속성의 이름입니다.|  
|Property_value|Sql_variant|컨텍스트의 원본에 연결된 속성 값입니다.|  
  
## <a name="remarks"></a>Remarks  
 다음 표에서는 컨텍스트 유형을 나열합니다.  
  
||||  
|-|-|-|  
|컨텍스트 유형 값|유형 이름|설명|  
|10|태스크|오류가 발생할 당시의 태스크 상태입니다.|  
|20|파이프라인|파이프라인 구성 요소의 오류: 원본, 대상 또는 변환 구성 요소.|  
|30|시퀀스|시퀀스의 상태입니다.|  
|40|For 루프|For Loop의 상태입니다.|  
|50|Foreach 루프|Foreach Loop의 상태입니다.|  
|60|패키지|오류가 발생할 당시의 패키지 상태입니다.|  
|70|변수|변수 값|  
|80|ODBC 대상 편집기|연결 관리자의 속성입니다.|  
  
## <a name="permissions"></a>사용 권한  
 이 뷰를 보려면 다음 권한 중 하나가 필요합니다.  
  
-   작업에 대한 READ 권한  
  
-   **ssis_admin** 데이터베이스 역할에 대한 멤버 자격  
  
-   **sysadmin** 서버 역할에 대한 멤버 자격  
  
  
