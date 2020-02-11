---
title: Analysis Server 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 8dbe4bc5-6aa9-48ee-857e-0b4ea764b9cb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4f083aafd2dc8718bb79798d43483c66b3520b0d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62666748"
---
# <a name="analysis-server-properties-service-tab"></a>분석 서버 속성(서비스 탭)
  이 서비스는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]입니다. 
  [!INCLUDE[ssAS](../../includes/ssas-md.md)] 가 제대로 작동하려면 이 서비스가 실행되고 있어야 합니다. 밝은 회색으로 표시된 속성 값은 이 애플리케이션을 사용하여 변경할 수 없습니다.  
  
## <a name="options"></a>옵션  
 **이진 경로**  
 이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.  
  
 **오류 제어**  
 1은 `SERVICE_ERROR_NORMAL`을 나타냅니다. 컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다. 이 값은 변경할 수 없습니다.  
  
 **종료 코드**  
 오류가 발생하면 이 상자에 오류 번호가 나타납니다. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.  
  
 **호스트 이름**  
 
  [!INCLUDE[ssAS](../../includes/ssas-md.md)]가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.  
  
 **이름**  
 서비스의 표시 이름을 나타냅니다.  
  
 **프로세스 ID**  
 이 프로그램의 프로세스를 추적하기 위해 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows에서 사용하는 번호를 표시합니다.  
  
 **SQL 서비스 유형**  
 호출 프로세스에 제공되는 서비스의 유형을 표시합니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 여러 서비스를 설치 합니다.  
  
 **시작 모드**  
 이 서비스를 다음 옵션으로 설정합니다.  
  
-   수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.  
  
-   자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.  
  
-   사용 안 함: 이 서비스를 시작할 수 없습니다.  
  
 **시스템 상태**  
 이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다.  
  
  
