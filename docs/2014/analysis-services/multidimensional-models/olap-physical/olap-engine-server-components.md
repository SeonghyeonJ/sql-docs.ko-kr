---
title: OLAP 엔진 서버 구성 요소 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0537be8bda9c367fc381140183b10ddf383cf16a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68889530"
---
# <a name="olap-engine-server-components"></a>OLAP 엔진 서버 구성 요소
  의 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 서버[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]구성 요소는 Windows 서비스로 실행 되는 msmdsrv.ini 응용 프로그램입니다. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 이 애플리케이션은 보안 구성 요소, XMLA(XML for Analysis) 수신기 구성 요소, 쿼리 프로세서 구성 요소 및 다음 기능을 수행하는 다른 많은 내부 구성 요소로 이루어집니다.  
  
-   클라이언트로부터 수신한 문 구문 분석  
  
-   메타데이터 관리  
  
-   트랜잭션 처리  
  
-   계산 처리  
  
-   차원 및 셀 데이터 저장  
  
-   집계 생성  
  
-   쿼리 일정 예약  
  
-   개체 캐싱  
  
-   서버 리소스 관리  
  
## <a name="architectural-diagram"></a>아키텍처 다이어그램  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스는 독립 실행형 서비스로 실행되며 서비스와의 통신은 HTTP 또는 TCP를 사용하는 XMLA(XML for Analysis)를 통해 이루어집니다. AMO는 사용자 애플리케이션과 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 사이에 있는 계층으로, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 관리 개체에 대한 액세스를 제공합니다. AMO는 클라이언트 애플리케이션에서 명령을 가져와서 이 명령을 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스에 대한 XMLA 메시지로 변환하는 클래스 라이브러리이며, 명령을 실행하는 메서드 멤버 및 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 개체에 대한 데이터를 포함하는 속성 멤버와 함께 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 개체를 최종 사용자에게 클래스로 표시합니다.  
  
 다음 그림은 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 인스턴스 내에서 실행되는 모든 주요 요소와 이 인스턴스와 상호 작용하는 모든 사용자 구성 요소를 비롯한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 구성 요소 아키텍처를 보여 줍니다. 또한 HTTP 또는 TCP를 사용하는 XMLA(XML for Analysis) 수신기를 통해서만 이 인스턴스에 액세스할 수 있음을 보여 줍니다.  
  
 ![Analysis Services 시스템 아키텍처 다이어그램](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Analysis Services 시스템 아키텍처 다이어그램")  
  
## <a name="xmla-listener"></a>XMLA 수신기  
 XMLA 수신기 구성 요소는 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 와 클라이언트 간의 모든 XMLA 통신을 처리합니다. Msmdsrv.ini 파일의 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 구성 설정을 사용 하 여 인스턴스가 수신 하는 포트를 지정할 수 있습니다. `Port` [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 이 파일의 값이 0이면 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 는 기본 포트에서 수신합니다. 달리 지정하지 않는 한 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 에서는 다음 기본 TCP 포트를 사용합니다.  
  
|포트|Description|  
|----------|-----------------|  
|2383|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 기본 인스턴스|  
|2382|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 다른 인스턴스에 대한 리디렉터|  
|서버 시작 시 동적으로 할당됩니다.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]의 명명된 인스턴스|  
  
 자세한 내용은 [Analysis Services 액세스를 허용 하도록 Windows 방화벽 구성을](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [개체 명명 규칙 &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md)   
 [물리적 아키텍처&#40;Analysis Services - 다차원 데이터&#41;](understanding-microsoft-olap-physical-architecture.md)   
 [논리적 아키텍처 &#40;Analysis Services-다차원 데이터&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
