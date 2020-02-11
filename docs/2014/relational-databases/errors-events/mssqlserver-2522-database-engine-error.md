---
title: MSSQLSERVER_2522 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2522 (Database Engine error)
ms.assetid: 19b9b00c-330f-4dd3-9052-9d88bce83849
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 696a7d536dc3fbb64e08ae9ccef21adbc4d9954d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62914925"
---
# <a name="mssqlserver_2522"></a>MSSQLSERVER_2522
    
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|2522|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC_INDEX_FILEGROUP_IS_INVALID|  
|메시지 텍스트|파일 그룹 F_NAME이(가) 잘못되었으므로 테이블 O_NAME의 인덱스 I_NAME을(를) 처리할 수 없습니다.|  
  
## <a name="explanation"></a>설명  
 이 정보 메시지는 인덱스의 메타데이터에 저장된 파일 그룹 ID 중 하나가 없기 때문에 인덱스를 검사할 수 없음을 나타냅니다. 잘못된 파일 그룹 ID가 데이터 자체, LOB(Large Object) 데이터 또는 행 오버플로 데이터에 사용될 수 있습니다.  
  
 문제가 없으면 같은 개체에 대한 다른 인덱스를 모두 검사합니다.  
  
## <a name="user-action"></a>사용자 동작  
  
### <a name="look-for-hardware-failure"></a>하드웨어 오류 찾기  
 하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 애플리케이션 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오. 로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.  
  
 데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오. 시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요. 쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.  
  
 마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다. 여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.  
  
### <a name="restore-from-backup"></a>백업에서 복원  
 하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.  
  
### <a name="run-dbcc-checkdb"></a>DBCC CHECKDB 실행  
 해당 사항 없음 이 오류는 자동으로 복구할 수 없습니다.  
  
  
