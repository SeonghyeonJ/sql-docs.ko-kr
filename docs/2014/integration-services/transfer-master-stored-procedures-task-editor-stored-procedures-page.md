---
title: Master 저장 프로시저 전송 태스크 편집기 (저장 프로시저 페이지) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferstoredprocedurestask.storedprocedures.f1
helpviewer_keywords:
- Transfer Stored Procedures Task Editor
ms.assetid: 5fcf171e-cc0b-4c24-8eb5-3a4b4775e64a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f233f0730286a1623ee54c38084d07a2aba903e3
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66054855"
---
# <a name="transfer-master-stored-procedures-task-editor-stored-procedures-page"></a>master 저장 프로시저 전송 태스크 편집기(저장 프로시저 페이지)
  **master 저장 프로시저 전송 태스크 편집기** 대화 상자의 **저장 프로시저** 페이지를 사용하여 하나 이상의 사용자 정의 저장 프로시저를 **인스턴스의** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 데이터베이스에서 다른 **인스턴스의** master [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]데이터베이스로 복사하기 위한 속성을 지정할 수 있습니다. 이 태스크에 대한 자세한 내용은 [Transfer Master Stored Procedures Task](control-flow/transfer-master-stored-procedures-task.md)를 참조하십시오.  
  
> [!NOTE]  
>  이 태스크는 **dbo** 소유의 사용자 정의 저장 프로시저만 원본 서버의 **master** 데이터베이스에서 대상 서버의 **master** 데이터베이스로 전송합니다. 대상 서버의 **master** 데이터베이스에서 CREATE PROCEDURE 권한을 부여받았거나 대상 서버에서 **sysadmin** 고정 서버 역할의 멤버인 사용자만 해당 데이터베이스에 저장 프로시저를 만들 수 있습니다.  
  
## <a name="options"></a>옵션  
 **SourceConnection**  
 목록에서 SMO 연결 관리자를 선택 하거나 ** \<새 연결 ... >** 을 클릭 하 여 원본 서버에 대 한 새 연결을 만듭니다.  
  
 **DestinationConnection**  
 목록에서 SMO 연결 관리자를 선택 하거나 ** \<새 연결 ... >** 을 클릭 하 여 대상 서버에 대 한 새 연결을 만듭니다.  
  
 **IfObjectExists**  
 대상 서버의 **master** 데이터베이스에 이미 있는 같은 이름의 사용자 정의 저장 프로시저를 태스크에서 처리하는 방법을 선택합니다.  
  
 이 속성의 옵션은 다음 표에 나열되어 있습니다.  
  
|값|설명|  
|-----------|-----------------|  
|**FailTask**|대상 서버의 **master** 데이터베이스에 같은 이름의 저장 프로시저가 이미 있는 경우 태스크가 실패합니다.|  
|**언제**|대상 서버의 **master** 데이터베이스에 있는 같은 이름의 저장 프로시저를 덮어씁니다.|  
|**킵**|대상 서버의 **master** 데이터베이스에 있는 같은 이름의 저장 프로시저를 건너뜁니다.|  
  
 **TransferAllStoredProcedures**  
 원본 서버의 **master** 데이터베이스에 있는 모든 사용자 정의 저장 프로시저를 대상 서버로 복사할지 여부를 선택합니다.  
  
|값|설명|  
|-----------|-----------------|  
|**True**|**master** 데이터베이스의 모든 사용자 정의 저장 프로시저를 복사합니다.|  
|**허위**|지정한 저장 프로시저만 복사합니다.|  
  
 **StoredProceduresList**  
 원본 서버의 **master** 데이터베이스에서 대상 **master** 데이터베이스로 복사할 사용자 정의 저장 프로시저를 선택합니다. 이 옵션은 **TransferAllStoredProcedures** 를 **False**로 설정한 경우에만 사용할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [작업 Integration Services](control-flow/integration-services-tasks.md)   
 [Master 저장 프로시저 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md)   
 [식 페이지](expressions/expressions-page.md)   
 [SMO 연결 관리자](connection-manager/smo-connection-manager.md)  
  
  
