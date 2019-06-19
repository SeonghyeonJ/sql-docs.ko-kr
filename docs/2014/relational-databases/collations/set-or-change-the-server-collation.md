---
title: 서버 데이터 정렬 설정 또는 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- server collations [SQL Server]
- collations [SQL Server], server
ms.assetid: 3242deef-6f5f-4051-a121-36b3b4da851d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d4501bc77a28746de3b0ce97b7b619889093650d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62918579"
---
# <a name="set-or-change-the-server-collation"></a>서버 데이터 정렬 설정 또는 변경
  서버 데이터 정렬은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 설치된 모든 시스템 데이터베이스와 새로 만든 사용자 데이터베이스의 기본 데이터 정렬로 적용됩니다. 서버 데이터 정렬은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 설치 과정에서 지정됩니다. 자세한 내용은 [Collation and Unicode Support](collation-and-unicode-support.md)을(를) 참조하세요.  
  
## <a name="changing-the-server-collation"></a>서버 데이터 정렬 변경  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 기본 데이터 정렬을 변경하는 작업은 복잡할 수 있으며 다음과 같은 단계가 포함됩니다.  
  
-   사용자 데이터베이스와 그 안의 모든 개체를 다시 만드는 데 필요한 정보나 스크립트가 모두 있는지 확인합니다.  
  
-   [bcp Utility](../../tools/bcp-utility.md)등의 도구를 사용하여 모든 데이터를 내보냅니다. 자세한 내용은 [데이터 대량 가져오기 및 내보내기&#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)를 참조하세요.  
  
-   모든 사용자 데이터베이스를 삭제합니다.  
  
-   **setup** 명령의 SQLCOLLATION 속성에 새 데이터 정렬을 지정하여 master 데이터베이스를 다시 작성합니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.  
  
    ```  
    Setup /QUIET /ACTION=REBUILDDATABASE /INSTANCENAME=InstanceName   
    /SQLSYSADMINACCOUNTS=accounts /[ SAPWD= StrongPassword ]   
    /SQLCOLLATION=CollationName  
    ```  
  
     자세한 내용은 [시스템 데이터베이스 다시 작성](../databases/system-databases.md)을 참조하세요.  
  
-   모든 데이터베이스와 그 안의 모든 개체를 만듭니다.  
  
-   모든 데이터를 가져옵니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스의 기본 데이터 정렬을 변경하는 대신 사용자가 만드는 각각의 새 데이터베이스에 대해 기본 데이터 정렬을 지정할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Collation and Unicode Support](collation-and-unicode-support.md)   
 [데이터베이스 데이터 정렬 설정 또는 변경](set-or-change-the-database-collation.md)   
 [열 데이터 정렬 설정 또는 변경](set-or-change-the-column-collation.md)   
 [시스템 데이터베이스 다시 작성](../databases/system-databases.md)  
  
  
