---
title: 관리 도구 명령줄 옵션
description: SQL Server Distributed Replay 관리 도구인 DReplay.exe는 Distributed Replay 컨트롤러와 통신하는 명령줄 도구입니다.
titleSuffix: SQL Server Distributed Replay
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 08/12/2016
ms.openlocfilehash: aef4e3bcf25a073fa4e09db1c90611132e0f5b06
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85681894"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>관리 도구 명령줄 옵션(Distributed Replay Utility)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 관리 도구인 **DReplay.exe**는 Distributed Replay Controller와 통신하기 위한 명령줄 도구입니다. 이 관리 도구를 사용하여 컨트롤러에서 작업을 시작, 모니터링 및 취소할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") 관리 도구 구문에서 사용되는 구문 표기 규칙에 대한 자세한 내용은 [Transact-SQL 구문 표기 규칙&#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)을 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>설명  
 **DReplay.exe**에서 다음 명령줄 옵션을 실행할 수 있습니다.  
  
 **preprocess**  
 전처리 단계를 시작합니다. 컨트롤러는 대상 서버에 대해 재생할 입력 추적 데이터(프로덕션 환경에서 캡처한 데이터)를 준비합니다.  
  
 **재생(replay)**  
 이벤트 재생 단계를 시작합니다. 컨트롤러는 재생 데이터를 지정된 클라이언트로 발송하고 분산 재생을 시작하며 클라이언트를 동기화합니다. 필요에 따라 선택된 각 클라이언트는 재생 작업을 기록하고 결과 추적 파일을 로컬에 저장합니다.  
  
 **status**  
 컨트롤러를 쿼리하여 현재 상태를 표시합니다.  
  
 **cancel**  
 컨트롤러에서 실행 중인 현재 작업을 취소합니다.  
  
 명령 인수 및 예가 포함된 자세한 구문 정보는 다음 항목을 참조하십시오.  
  
-   [전처리 옵션&#40;Distributed Replay Utility Administration Tool&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [재생 옵션&#40;Distributed Replay Administration Tool&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [상태 옵션&#40;Distributed Replay Administration Tool&#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [취소 옵션&#40;Distributed Replay Administration Tool&#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 RPC는 언어 이벤트가 아닌 RPC로 재생됩니다.  
  
## <a name="permissions"></a>사용 권한  
 관리 도구는 로컬 사용자 또는 도메인 사용자 등의 대화형 사용자 계정으로 실행해야 합니다. 로컬 사용자 계정을 사용하려면 관리 도구와 컨트롤러가 동일한 컴퓨터에서 실행되고 있어야 합니다.  
  
 자세한 내용은 [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
