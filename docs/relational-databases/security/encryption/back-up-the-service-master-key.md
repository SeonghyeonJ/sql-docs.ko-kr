---
title: 서비스 마스터 키 백업 | Microsoft 문서
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: aliceku
ms.author: aliceku
ms.openlocfilehash: 4a5b28fda96be3fce311abc159bbe8e94fc061ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024423"
---
# <a name="back-up-the-service-master-key"></a>서비스 마스터 키 백업
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  이 문서에서는 [!INCLUDE[tsql](../../../includes/tsql-md.md)]을 사용하여 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 서비스 마스터 키를 백업하는 방법에 대해 설명합니다. 서비스 마스터 키는 암호화 계층의 루트입니다. 이 키는 안전한 오프 사이트 위치에 백업 및 저장해야 합니다. 이러한 백업을 만드는 작업은 서버에서 수행되는 첫 번째 관리 동작 중 하나입니다.  

## <a name="before-you-begin"></a>시작하기 전 주의 사항  
  
### <a name="limitations-and-restrictions"></a>제한 사항  

- 마스터 키를 열어야 하기 때문에 백업하기 전에 암호를 해독해야 합니다. 서비스 마스터 키로 암호화된 경우 마스터 키를 명시적으로 열 필요는 없지만 마스터 키가 암호로만 암호화된 경우 명시적으로 열어야 합니다.  
  
- 마스터 키는 만들자 마자 백업하고 외부의 안전한 위치에 보관하는 것이 좋습니다.  
  
## <a name="security"></a>보안  
  
### <a name="permissions"></a>사용 권한
데이터베이스에 대한 CONTROL 권한이 필요합니다.  
  
## <a name="using-transact-sql"></a>Transact-SQL 사용  
  
### <a name="to-back-up-the-service-master-key"></a>서비스 마스터 키를 백업하려면
  
1. [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 백업할 서비스 마스터 키가 들어 있는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 연결합니다.  
  
2. 백업 미디어에 서비스 마스터 키를 암호화하는 데 사용되는 암호를 선택합니다. 이 암호의 복잡성을 확인해야 합니다. 자세한 내용은 [Password Policy](../../../relational-databases/security/password-policy.md)을 참조하세요.  
  
3. 백업 키의 복사본을 저장하기 위해 이동식 백업 미디어를 가져옵니다.  
  
4. 키의 백업을 만들 NTFS 디렉터리를 식별합니다. 다음 단계에서 지정하는 파일을 만들 위치에 해당하는 이 디렉터리는 매우 제한적인 ACL(액세스 제한 목록)로 보호되어야 합니다.  
  
5. **개체 탐색기**에서 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
6. 표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
7. 다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```sql
    -- Creates a backup of the service master key.
    USE master;
    GO
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';
    GO
    ```  
  
    > [!NOTE]  
    > 키의 경로와 암호(있는 경우)는 위에 나타난 것과 다릅니다. 둘 다 서버 및 키 설정에 대해 고유한지 확인하세요.
  
8. 파일을 백업 미디어에 복사하고 복사본을 확인합니다.  
  
9. 백업을 안전한 오프 사이트 위치에 저장합니다.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 자세한 내용은 [OPEN MASTER KEY&#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) 및 [BACKUP MASTER KEY&#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md)를 참조하세요.  
