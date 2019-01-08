---
title: 모델 배포 옵션(Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 263bc590c43899c3b9531549f4e73eefbde81c9c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52792975"
---
# <a name="model-deployment-options-master-data-services"></a>모델 배포 옵션(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 모델 패키지 파일을 배포할 때 새 모델이나 복제된 모델을 배포할지 또는 이전에 복제된 모델을 업데이트할지 여부를 결정해야 합니다.  
  
## <a name="workflows"></a>워크플로  
 모델 패키지로 작업할 때 사용하는 두 가지 주 워크플로가 있습니다.  
  
-   테스트 환경에서 모델 패키지를 만들고 모델 복제본을 프로덕션 환경에 배포합니다. 시간이 지나면 테스트 환경에서 프로덕션 환경으로 업데이트를 배포합니다.  
  
-   모델의 패키지를 만들고 동일한 환경에 새 모델로 배포합니다. 이 경우 모델에 새 이름을 지정해야 합니다.  
  
## <a name="options"></a>변수  
 MDS 데이터베이스의 각 모델 개체에는 고유 ID(식별자)가 있습니다. 이러한 ID는 모델 배포 패키지에 포함됩니다. 패키지를 배포할 때 이러한 ID를 어떻게 처리할지 선택해야 합니다.  
  
 다음 표에는 시스템 관리의 모델 배포 마법사나 MDSModelDeploy 도구를 사용하여 모델을 배포할 때 선택할 옵션을 결정하는 데 도움이 되는 정보가 나와 있습니다.  
  
|옵션|Description|참고|  
|------------|-----------------|-----------|  
|단추를 사용하여 새|고유한 이름의 새 모델을 만듭니다. 모든 모델 개체에 대해 새 식별자가 생성됩니다.|새 식별자가 할당된 새 모델을 만들 경우 이후 모델 배포 도구를 사용하여 모델에 업데이트를 적용할 수 없습니다. 웹 애플리케이션에서 마법사를 사용하여 모델 패키지를 배포하는 경우에는 동일한 이름이나 ID를 가진 모델이 이미 있는 경우에만 새 모델을 만들 수 있습니다.|  
|복제|패키지의 모델을 그대로 복제하여 새 모델을 만듭니다. 이 방법은 해당 이름이나 식별자를 가진 모델이 대상 환경에 없는 경우에만 사용할 수 있습니다. "복제" 옵션은 동일한 모델을 여러 환경에서 사용하려고 하며 시간이 지나면 복제한 모델을 업데이트하려는 경우에 사용합니다.|웹 애플리케이션에서 마법사의 기본 동작입니다. 이름이나 ID가 같은 모델이 이미 있으면 대신 새 모델을 만들라는 메시지가 표시됩니다.|  
|Update|기존 모델을 패키지의 모델로 업데이트합니다. 두 모델의 식별자가 동일해야 합니다. 이 옵션은 이전에 복제한 모델을 업데이트하는 데 사용합니다.|이전에 복제한 모델만 업데이트할 수 있습니다. 이름과 ID가 일치해야 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [MDSModelDeploy를 사용하여 모델 배포 패키지 배포](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)   
 [마법사를 사용하여 모델 배포 패키지 배포](../../2014/master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)   
 [모델 배포&#40;Master Data Services&#41;](deploying-models-master-data-services.md)  
  
  
