---
title: 참조 데이터를 사용하도록 DQS 구성 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.administration.rdsconfiguration.f1
- sql13.dqs.administration.configuration.createDirectRDS.f1
- sql13.dqs.admin.config.rds.f1
ms.assetid: fae745e7-57a7-4cbc-8979-56ea8e392e4e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: eb4fec833e8782b3d7d017bbae7b5fc9c2995bda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67992341"
---
# <a name="configure-dqs-to-use-reference-data"></a>참조 데이터를 사용하도록 DQS 구성

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  이 항목에서는 데이터를 정리하는 데 참조 데이터를 사용하도록 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )를 구성하는 방법에 대해 설명합니다. Windows Azure Marketplace 또는 다이렉트 온라인 타사 참조 데이터 공급자의 참조 데이터를 사용할 수 있습니다.  

> [!IMPORTANT]
> 이 문서에서는 Azure DataMarket에서 이전에 사용할 수 있었던 타사 참조 데이터 서비스에 대해 설명합니다. 예를 들어 Melissa 주소 데이터를 포함한 DataMarket 및 Data Services는 2016년 12월 31일 이후 중단되었습니다. 따라서 DataMarket의 지정된 서비스를 사용하여 이 문서의 예제를 더 이상 실행할 수 없습니다. 타사 참조 데이터 공급자로부터 직접 온라인으로 사용할 수 있는 참조 데이터 서비스는 계속 사용할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전 주의 사항  
  
###  <a name="Prerequisites"></a> 사전 요구 사항  
 Marketplace의 참조 데이터를 사용하려면 유효한 Marketplace 계정 키가 있어야 합니다. Marketplace 계정 키를 만드는 방법은 [계정 만들기](https://go.microsoft.com/fwlink/?LinkId=212936)(https://go.microsoft.com/fwlink/?LinkId=212936) )를 참조하세요. [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **관리** 에서 **구성** 을 클릭한 다음 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 참조 데이터 **탭에서** DataMarket 계정 ID 만들기 **를 클릭하여** 내에서 Marketplace 계정 키를 만들 수도 있습니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 DQS에서 참조 데이터 서비스 설정을 구성하려면 DQS_MAIN 데이터베이스에 대한 dqs_administrator 역할이 있어야 합니다.  
  
##  <a name="Marketplace"></a> Marketplace의 참조 데이터를 사용하도록 DQS 구성  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Data Quality Client 응용 프로그램을 실행합니다](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **관리**에서 **구성**을 클릭합니다.  
  
3.  사용자 또는 사용자 조직에서 프록시 서버를 사용하여 인터넷에 연결하는 경우 **참조 데이터** 탭의 **네트워크 설정** 영역에서 **프록시 서버** 및 **포트** 상자에 적절한 값을 입력합니다.  
  
4.  **DataMarket 계정 ID** 상자에서 Marketplace 계정 키를 지정한 다음 **DataMarket 계정 ID 확인** 아이콘을 클릭하여 계정 키의 유효성을 검사합니다. 지정한 Marketplace 계정 키가 유효한지 여부를 나타내는 메시지가 표시됩니다.  
  
 이제 DQS에서 지정한 Marketplace 계정 키로 구독하는 Marketplace의 참조 데이터 서비스를 사용할 준비가 완료되었습니다.  
  
##  <a name="ThirdParty"></a> 다이렉트 온라인 타사 참조 데이터 공급자의 참조 데이터를 사용하도록 DQS 구성  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Data Quality Client 응용 프로그램을 실행합니다](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **관리**에서 **구성**을 클릭합니다.  
  
3.  사용자 또는 사용자 조직에서 프록시 서버를 사용하여 인터넷에 연결하는 경우 **참조 데이터** 탭의 **네트워크 설정** 영역에서 **프록시 서버** 및 **포트** 상자에 적절한 값을 입력합니다.  
  
4.  **다이렉트 온라인 타사 참조 데이터 서비스 설정** 영역에서 **새 참조 데이터 서비스 공급자 추가** 아이콘을 클릭합니다.  
  
5.  **새 다이렉트 온라인 타사 참조 데이터 서비스 공급자 만들기** 대화 상자에서 다음 정보를 지정합니다.  
  
    1.  **이름** 상자에 새 다이렉트 참조 데이터 서비스 공급자의 이름을 입력합니다.  
  
    2.  (선택 사항) **설명** 상자에 새 다이렉트 참조 데이터 서비스 공급자에 대한 설명을 입력합니다.  
  
    3.  **범주** 상자에 새 다이렉트 참조 데이터 서비스 공급자가 제공한 데이터의 범주를 입력합니다.  
  
    4.  스키마 상자에 다이렉트 참조 데이터 서비스 공급자에서 사용할 필드 문자열(열 이름)을 정의하는 스키마를 지정합니다. 필드 이름은 공백을 포함할 수 없으며, 필드는 쉼표로 구분되어야 합니다. 예를 들면 `FirstName, LastName, City, State`과 같습니다.  
  
    5.  **URI** 상자에 새 다이렉트 참조 데이터 서비스 공급자의 URI를 입력합니다. 보안 URI("https://"로 시작하는 주소)만 DQS에서 사용할 수 있습니다.  
  
    6.  **최대 일괄 처리 크기** 상자에 정리를 위해 참조 데이터 서비스 공급자로 보낼 일괄 처리당 최대 레코드 수를 입력합니다. 일괄 처리당 최대 100개의 레코드를 정리 작업에 지정할 수 있습니다.  
  
    7.  **계정 ID** 상자에 참조 데이터 서비스 공급자의 구독자 계정 ID를 입력합니다.  
  
6.  **확인** 을 클릭하여 데이터를 저장하고 **새 다이렉트 온라인 타사 참조 데이터 서비스 공급자 만들기** 대화 상자를 닫습니다. 새로 추가한 다이렉트 온라인 타사 참조 데이터 공급자를 DQS의 **직접 참조 데이터 서비스 공급자 표** 에서 사용할 수 있게 됩니다.  
  
 이제 DQS에서 새로 구성한 다이렉트 온라인 타사 참조 데이터 서비스 공급자의 참조 데이터 서비스를 사용할 준비가 완료되었습니다.  
  
##  <a name="FollowUp"></a> 후속 작업: 참조 데이터를 사용 하도록 DQS를 구성한 후  
 이제 방금 구성한 데이터 공급자에서 사용할 수 있는 참조 데이터에 필요한 기술 자료 도메인을 매핑해야 합니다. 이렇게 하려면 [참조 데이터에 도메인 또는 복합 도메인 연결](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)을 참조하세요.  
  
  
