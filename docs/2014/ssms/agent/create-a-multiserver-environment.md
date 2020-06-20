---
title: 다중 서버 환경 만들기 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, multiserver environments
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- multiserver environments [SQL Server]
ms.assetid: edc2b60d-15da-40a1-8ba3-f1d473366ee6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a6920920aa603c615cdc5f84a34a93204842052d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995367"
---
# <a name="create-a-multiserver-environment"></a>다중 서버 환경 만들기
  다중 서버 관리를 위해서는 마스터 서버(MSX)와 하나 이상의 대상 서버(TSX)를 설치해야 합니다. 모든 대상 서버에서 처리되는 작업은 먼저 마스터 서버에서 정의된 다음 대상 서버로 다운로드됩니다.  
  
 마스터 서버와 대상 서버 간 연결은 기본적으로 전체 SSL(Secure Sockets Layer) 암호화 및 인증서 확인을 사용할 수 있도록 설정됩니다. 자세한 내용은 [대상 서버의 암호화 옵션 설정](set-encryption-options-on-target-servers.md)을 참조하세요.  
  
 대상 서버가 많으면 대상 서버 트래픽으로 인해 프로덕션 서버의 성능이 저하될 수 있으므로 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기능에 대한 성능 요구 사항이 중요한 프로덕션 서버에 마스터 서버를 정의하지 않는 것이 좋습니다. 또한 전용 마스터 서버로 이벤트를 전달하면 하나의 서버에서 집중 관리할 수 있습니다. 자세한 내용은 [이벤트 관리](manage-events.md)를 참조하세요.  
  
> [!NOTE]  
>  다중 서버 작업 처리를 사용하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스 계정이 마스터 서버에서 **msdb** 데이터베이스 역할인 **TargetServersRole** 의 멤버여야 합니다. 마스터 서버 마법사는 등록 과정에서 이 역할에 서비스 계정을 자동으로 추가합니다.  
  
## <a name="considerations-for-multiserver-environments"></a>다중 서버 환경 고려 사항  
 지원되는 MSX/TSX 구성은 다음 표를 참조하십시오.  
  
||**TSX = 7.0**|**TSX = 8.0 < SP3**|**TSX = 8.0 SP3 이상**|**TSX = 9.0**|**TSX = 10.0**|**TSX = 10.5**|**TSX = 11.0**|  
|-|--------------------|---------------------------|----------------------------------|--------------------|--------------------|---------------------|---------------------|  
|**MSX = 7.0**|예|예|아니요|아니요|아니요|아니요|예|  
|**MSX = 8.0 < SP3**|예|예|아니요|아니요|아니요|아니요|예|  
|**MSX = 8.0 SP3 이상**|아니요|예|예|예|예|예|예|  
|**MSX = 9.0**|아니요|아니요|예|예|예|예|예|  
|**MSX = 10.0**|아니요|아니요|아니요|예|예|예|예|  
|**MSX = 10.5**|아니요|아니요|아니요|아니요|예|예|예|  
|**MSX = 11.0**|아니요|아니요|아니요|아니요|아니요|예|예|  
  
 다중 서버 환경을 만들 때에는 다음 사항을 고려하십시오.  
  
-   각 대상 서버는 하나의 마스터 서버에만 보고합니다. 대상 서버를 다른 서버에 참여시키려면 마스터 서버에서 이 대상 서버를 제거해야 합니다.  
  
-   대상 서버의 이름을 변경할 때는 이름을 변경하기 전에 먼저 제거하고 이름을 변경한 후 다시 참여시켜야 합니다.  
  
-   다중 서버 구성을 분해하려면 마스터 서버에서 모든 대상 서버를 제거해야 합니다.  
  
-   SQL Server Integration Services는 마스터 서버 버전과 같거나 높은 버전의 대상 서버만 지원합니다.  
  
## <a name="related-tasks"></a>관련 작업  
 다음 항목에서는 다중 서버 환경을 만들기 위한 공통적인 태스크에 대해 설명합니다.  
  
|Description|항목|  
|-----------------|-----------|  
|마스터 서버를 만드는 방법에 대해 설명합니다.|[마스터 서버 만들기](make-a-master-server.md)|  
|대상 서버를 만드는 방법에 대해 설명합니다.|[대상 서버 만들기](make-a-target-server.md)|  
|마스터 서버에 대상 서버를 등록하는 방법에 대해 설명합니다.|[마스터 서버에 대상 서버 등록](enlist-a-target-server-to-a-master-server.md)|  
|마스터 서버에서 대상 서버를 제거하는 방법에 대해 설명합니다.|[Defect a Target Server from a Master Server](defect-a-target-server-from-a-master-server.md)|  
|마스터 서버에서 여러 대상 서버를 제거하는 방법에 대해 설명합니다.|[마스터 서버에서 여러 대상 서버 제거](defect-multiple-target-servers-from-a-master-server.md)|  
|대상 서버의 상태를 확인하는 방법에 대해 설명합니다.|[Transact-sql&#41;sp_help_targetserver &#40;](/sql/relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql)<br /><br /> [Transact-sql&#41;sp_help_targetservergroup &#40;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)|  
  
## <a name="see-also"></a>참고 항목  
 [프록시를 사용하는 다중 서버 작업 문제 해결](troubleshoot-multiserver-jobs-that-use-proxies.md)  
  
  
