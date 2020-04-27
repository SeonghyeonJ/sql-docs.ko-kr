---
title: SQL Server 매개 변수 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Engine analysis [Upgrade Advisor]
- SQL Server Upgrade Advisor, Database Engine
- Upgrade Advisor [SQL Server], Database Engine
- analyzing system [Upgrade Advisor], Database Engine
ms.assetid: 44a18bfe-e593-47a5-995f-382c01d3f618
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e528b94e51238a06a9776e58693c3093f4bfb831
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66091876"
---
# <a name="sql-server-parameters"></a>SQL Server 매개 변수
  이 페이지에서는 분석기가 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 분석에 사용할 매개 변수를 설정합니다. 데이터베이스 하나, 여러 개 또는 모두를 분석하고, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 만든 추적 파일을 분석하며, SQL 배치 파일을 분석할 수 있습니다.  
  
> [!NOTE]  
>  추적 파일이나 SQL 배치 파일을 분석하기 위해 전송할 경우에만 일부 업그레이드 문제가 감지될 수 있습니다.  
  
## <a name="options"></a>옵션  
 **분석할 데이터베이스**  
 모든 데이터베이스를 분석 하려면 **모든 데이터베이스** 확인란을 선택 합니다. 일부 데이터베이스를 분석하려면 분석할 각 데이터베이스 옆에 있는 확인란을 선택합니다.  
  
 **추적 파일 분석**  
 파일 시스템에 있는 추적 파일을 분석하려면 이 확인란을 선택합니다.  
  
 **추적 파일의 경로**  
 하나 이상의 파일을 분석할 수 있습니다. 위치를 찾아 여러 개의 파일을 선택하거나 파일 이름을 여러 개 입력할 수 있습니다. 각 파일의 전체 경로 이름(파일 이름 포함)을 사용하고 파이프 문자(|)로 각 항목을 구분합니다.  
  
 **추적 파일 분석**을 사용 하도록 설정 하는 경우 경로 이름과 파일 이름을 입력할 때까지 **다음** 을 사용할 수 없습니다.  
  
 **배치 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 파일 분석**  
 파일 시스템에 있는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 배치 파일을 분석하려면 이 확인란을 선택합니다.  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 배치 파일의 경로**  
 하나 이상의 배치 파일을 분석할 수 있습니다. 위치를 찾아 여러 개의 파일을 선택하거나 파일 이름을 여러 개 입력할 수 있습니다. 각 파일의 전체 경로 이름(파일 이름 포함)을 사용하고 파이프 문자(|)로 각 항목을 구분합니다.  
  
 **SQL 배치 파일 분석**을 사용 하도록 설정 하는 경우 경로 이름과 파일 이름을 입력할 때까지 **다음** 단추를 사용할 수 없습니다.  
  
 **SQL 일괄 처리 구분 기호**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 일괄 처리를 구분하는 데 사용되는 텍스트입니다. 기본값은 **GO**입니다.  
  
## <a name="see-also"></a>참고 항목  
 [업그레이드 관리자 작업](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [업그레이드 관리자 사용자 인터페이스 참조](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
