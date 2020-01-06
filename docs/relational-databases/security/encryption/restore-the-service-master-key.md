---
title: 서비스 마스터 키 복원 | Microsoft 문서
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: e27516fb2b0931c2df8f4a76a4153ee8c38616b9
ms.sourcegitcommit: 39ea690996a7390e3d13d6fb8f39d8641cd5f710
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74957391"
---
# <a name="restore-the-service-master-key"></a>서비스 마스터 키 복원
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 을 사용하여 [!INCLUDE[tsql](../../../includes/tsql-md.md)]에서 서비스 마스터 키를 복원하는 방법에 대해 설명합니다.  
  
> [!WARNING]  
> 이 키는 복원할 필요가 거의 없습니다. 만약 키를 복원할 경우 각별히 주의해야 합니다. 자세한 내용은 [Back Up the Service Master Key](../../../relational-databases/security/encryption/back-up-the-service-master-key.md)을 참조하세요.  
  
## <a name="before-you-begin"></a>시작하기 전에  
  
### <a name="limitations-and-restrictions"></a>제한 사항  
  
- 서비스 마스터 키가 복원되면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 는 현재 서비스 마스터 키로 암호화된 모든 키 및 암호를 해독한 다음 백업 파일에서 로드된 서비스 마스터 키로 암호화합니다.  
  
- 암호 해독 중 하나가 실패하면 복원이 실패합니다. 오류를 무시하기 위해 FORCE 옵션을 사용할 수 있지만 이 옵션을 사용하면 암호를 해독할 수 없는 데이터를 손실할 수 있습니다.  
  
- 암호화 계층을 다시 생성하는 작업에는 리소스가 많이 소비됩니다. 이 작업은 사용량이 적은 기간 동안에 실행하도록 예약해야 합니다.  
  
> [!CAUTION]  
> 서비스 마스터 키는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 암호화 계층의 루트입니다. 서비스 마스터 키는 트리에 있는 모든 다른 키를 직접 또는 간접적으로 보호합니다. 강제 복원 중에 종속 키의 암호를 해독할 수 없으면 해당 키로 보호되는 데이터가 손실됩니다.  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>사용 권한  
서버에 대한 CONTROL SERVER 권한이 필요합니다.  
  
## <a name="using-transact-sql"></a>Transact-SQL 사용  
  
### <a name="to-restore-the-service-master-key"></a>서비스 마스터 키를 복원하려면  
  
1. 물리적 백업 미디어 또는 로컬 파일 시스템의 디렉터리에서 백업한 서비스 마스터 키의 복사본을 검색합니다.  
  
2. **개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
3. 표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
4. 다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    > 키의 경로와 암호(있는 경우)는 위에 나타난 것과 다릅니다. 둘 다 서버 및 키 설정에 대해 고유한지 확인하세요.
