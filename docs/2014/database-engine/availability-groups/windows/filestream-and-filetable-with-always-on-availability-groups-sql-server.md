---
title: FILESTREAM 및 FileTable AlwaysOn 가용성 그룹 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], Availability Groups
- FILESTREAM [SQL Server], Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: fdceda9a-a9db-4d1d-8745-345992164a98
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3fa149aa47c99418bd3109829bfffee698ab3f6e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814145"
---
# <a name="filestream-and-filetable-with-alwayson-availability-groups-sql-server"></a>AlwaysOn 가용성 그룹의 FILESTREAM 및 FileTable(SQL Server)
  이 항목에는 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]과 함께 FILESTREAM 및 FileTable 기능 사용에 대한 정보가 포함되어 있습니다.  
  
 모든 FILESTREAM 기능이 지원됩니다. 장애 조치(Failover) 이후 FILESTREAM 데이터는 읽기 가능한 두 보조 복제본 및 새로운 주 복제본에서 액세스할 수 있습니다.  
  
 FileTable 기능은 부분적으로 지원됩니다. 장애 조치(Failover) 이후 FileTable 데이터는 주 복제본에서 액세스할 수 있지만 FileTable 데이터를 읽기 가능한 보조 복제본에서는 액세스할 수 없습니다.  
  
 **항목 내용:**  
  
-   [필수 구성 요소](#Prerequisites)  
  
-   [FILESTREAM 및 FileTable 액세스를 위한 VNN(가상 네트워크 이름) 사용](#vnn)  
  
-   [관련 작업](#RelatedTasks)  
  
-   [관련 내용](#RelatedContent)  
  
##  <a name="Prerequisites"></a> 사전 요구 사항  
  
-   FileTable을 포함하거나 포함하지 않고 FILESTREAM을 사용하는 데이터베이스를 가용성 그룹에 추가하려면 먼저 가용성 그룹에 대한 가용성 복제본을 호스팅하는 모든 서버 인스턴스에 FILESTREAM이 설정되었는지 확인합니다. 자세한 내용은 [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)을 참조하세요.  
  
##  <a name="vnn"></a> FILESTREAM 및 FileTable 액세스를 위한 VNN(가상 네트워크 이름) 사용  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]인스턴스에 FILESTREAM을 설정하면 FILESTREAM 데이터에 대한 액세스를 제공하도록 인스턴스 수준의 공유가 만들어집니다. 이 공유에는 다음 형식의 컴퓨터 이름을 사용하여 액세스합니다.  
  
 `\\<computer_name>\<filestream_share_name>`  
  
 하지만 AlwaysOn 가용성 그룹에서 컴퓨터 이름은 VNN(가상 네트워크 이름)을 사용하여 가상화됩니다. 컴퓨터가 가용성 그룹에서 주 복제본이고, 가용성 그룹의 데이터베이스에 FILESTREAM 데이터가 포함되어 있으면 FILESTREAM 데이터에 대한 액세스를 제공하도록 VNN 범위의 공유도 만들어집니다. 이러한 동작은 FILESTREAM 데이터에 대한 Transact-SQL 액세스에 영향을 주지 않습니다. 하지만 파일 시스템 API를 사용하는 애플리케이션은 다음 형식의 경로가 포함된 VNN 범위의 공유를 사용해야 합니다.  
  
 `\\<VNN>\<filestream_share_name>`  
  
 이 VNN 범위의 공유는 다음 이벤트 중 하나가 발생할 때 만들어집니다.  
  
-   FILESTREAM 데이터가 포함된 데이터베이스를 주 복제본의 AlwaysOn 가용성 그룹에 추가합니다. 이 경우 `\\<computer_name>\<filestream_share_name>` 공유는 이미 존재합니다. `\\<VNN>\<filestream_share_name>` 공유가 만들어집니다.  
  
-   가용성 그룹이 포함된 주 복제본에서 파일 입/출력 스트리밍 액세스를 위해 FILESTREAM을 설정합니다. 다음 공유가 만들어집니다.  
  
    1.  `\\<computer_name>\<filestream_share_name>`  
  
    2.  `\\<VNN1>\<filestream_share_name>` - 가용성 그룹 1  
  
    3.  `\\<VNN2>\<filestream_share_name>` - 가용성 그룹 2  
  
 이러한 VNN 범위의 공유는 모든 보조 복제본에도 전파됩니다.  
  
 FILESTREAM 또는 FileTable 데이터가 포함된 데이터베이스가 AlwaysOn 가용성 그룹에 속하는 경우  
  
-   FILESTREAM 및 FileTable 함수가 컴퓨터 이름 대신 VNN(가상 네트워크 이름)을 사용하거나 반환합니다. 이러한 함수에 대한 자세한 내용은 [Filestream 및 FileTable 함수&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/filestream-and-filetable-functions-transact-sql)를 참조하세요.  
  
-   파일 시스템 API를 통한 FILESTREAM 또는 FileTable 데이터에 대한 모든 액세스에는 컴퓨터 이름 대신 VNN이 사용되어야 합니다.  
  
 데이터베이스가 가용성 그룹에 속할 때 애플리케이션이 `\\<computer_name>\<filestream_share_name>` 형식의 컴퓨터 이름을 사용하여 공유에 액세스하려고 시도하면 오류가 발생합니다.  
  
 데이터베이스가 가용성 그룹에 속하지 않을 때 애플리케이션이 VNN 범위의 경로를 사용하여 공유에 액세스하려고 시도하면 요청이 성공할 수 있습니다. 이 경우 가상 네트워크 이름은 컴퓨터 이름으로 확인됩니다. 하지만 이러한 사용 방식은 가용성 그룹이 삭제될 경우 VNN 범위의 경로가 작동을 중지할 수 있기 때문에 사용하지 않는 것이 좋습니다.  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [Enable and Configure FILESTREAM](../../../relational-databases/blob/enable-and-configure-filestream.md)  
  
-   [FileTable의 필수 구성 요소를 사용하도록 설정](../../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
##  <a name="RelatedContent"></a> 관련 내용  
 없음  
  
## <a name="see-also"></a>관련 항목  
 [AlwaysOn 가용성 그룹 개요 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
  
