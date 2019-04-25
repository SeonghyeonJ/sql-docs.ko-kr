---
title: 변경 내용 추적(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking [SQL Server]
ms.assetid: 5e879c65-0d38-454f-9a20-62a6e72c89f7
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 77b98b635ccc8cd8e04e0c84e402be9409b27cbd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62508920"
---
# <a name="change-tracking-master-data-services"></a>변경 내용 추적(Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 변경 내용 추적 그룹을 사용하여 특성 값이 변경될 때 동작을 수행할 수 있습니다. 새 값이 무엇인지 모르지만 대신 변경이 발생했는지 알고 싶으면 변경 내용 추적을 사용합니다.  
  
## <a name="configuring-change-tracking"></a>변경 내용 추적 구성  
 변경 내용 추적을 구성하려면 변경 내용 추적 그룹에 특성을 추가합니다. 그룹에 하나 이상의 특성을 포함할 수 있습니다. 그런 다음 비즈니스 규칙을 만들어 그룹의 특성이 변경될 때 수행할 동작을 정의합니다.  
  
> [!NOTE]  
>  변경 내용 추적 비즈니스 규칙은 준비된(가져온) 데이터가 변경된다고 간주합니다.  
  
## <a name="related-tasks"></a>관련 작업  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|변경 내용 추적 그룹에 특성 추가|[변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)|  
|특성 변경을 기반으로 하는 동작을 시작하는 비즈니스 규칙을 만듭니다.|[특성 값 변경 기반 동작 시작&#40;Master Data Services&#41;](../master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)|  
  
## <a name="related-content"></a>관련 내용  
  
-   [유효성 검사&#40;Master Data Services&#41;](../master-data-services/validation-master-data-services.md)  
  
-   [비즈니스 규칙&#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
-   [특성&#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
  
