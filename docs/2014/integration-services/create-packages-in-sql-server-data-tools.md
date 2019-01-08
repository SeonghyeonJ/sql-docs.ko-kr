---
title: SQL Server Data Tools에서 패키지 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, creating
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
ms.assetid: bb3c085b-1458-49fa-8348-6a76b6e97ea6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c2748cf548a6a5c60ceab764afb27fff111f3ea1
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53372365"
---
# <a name="create-packages-in-sql-server-data-tools"></a>SQL Server Data Tools에서 패키지 만들기
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 에서 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너를 사용하여 만드는 패키지는 파일 시스템에 저장됩니다. 패키지를 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 또는 패키지 저장소에 저장하려면 패키지 복사본을 저장해야 합니다. 자세한 내용은 [패키지의 복사본 저장](../../2014/integration-services/save-a-copy-of-a-package.md)을 참조하세요.  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 다음 방법 중 하나를 사용하여 새 패키지를 만들 수 있습니다.  
  
-   [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에 포함된 패키지 템플릿을 사용합니다.  
  
-   사용자 지정 템플릿 사용  
  
     새 패키지를 만드는 데 사용자 지정 패키지를 템플릿으로 사용하려면 해당 패키지를 DataTransformationItems 폴더로 복사하면 됩니다. 기본적으로 이 폴더는 C:\Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\ProjectItems\DataTransformationProject에 있습니다.  
  
-   기존 패키지를 복사합니다.  
  
     다시 사용하려는 기능이 기존 패키지에 있는 경우 이러한 패키지의 개체를 복사하여 붙여넣으면 새 패키지에서 제어 흐름 및 데이터 흐름을 훨씬 빠르게 작성할 수 있습니다. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트에서 복사 및 붙여넣기를 사용하는 방법은 [패키지 개체 다시 사용](reuse-of-package-objects.md)을 참조하세요.  
  
     기존 패키지를 복사하거나 사용자 지정 패키지를 템플릿으로 사용하여 새 패키지를 만드는 경우 기존 패키지의 이름과 GUID도 복사됩니다. 새 패키지와 복사한 원본 패키지를 구분하려면 새 패키지의 이름 및 GUID를 업데이트해야 합니다. 예를 들어 패키지에 동일한 GUID가 포함된 경우 로그 데이터가 속한 패키지를 식별하기가 훨씬 더 어렵습니다. [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 속성 창을 사용하여 `ID` 속성에서 GUID를 다시 생성하고 `Name` 속성의 값을 업데이트할 수 있습니다. 자세한 내용은 [패키지 속성 설정](set-package-properties.md) 및 [dtutil 유틸리티](dtutil-utility.md)를 참조하세요.  
  
-   템플릿으로 지정한 사용자 지정 패키지를 사용합니다.  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 실행  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 간단한 가져오기 또는 내보내기 수행하는 완전한 패키지를 만듭니다. 이 마법사는 연결, 원본 및 대상을 구성하고 가져오기 또는 내보내기를 즉시 실행하는 데 필요한 데이터 변환을 추가합니다. 필요에 따라 나중에 다시 실행하기 위해 패키지를 저장하거나 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]에서 패키지를 향상시키고 구체화할 수 있습니다. 그러나 패키지를 저장하는 경우에는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 에서 패키지를 변경하거나 실행하기 전에 기존 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]프로젝트에 패키지를 추가해야 합니다.  
  
 다음 절차에서는 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지를 만들거나 삭제하는 방법에 대해 설명합니다.  
  
 기본 패키지 템플릿을 사용하여 기본 패키지를 만드는 방법을 보여 주는 비디오는 [기본 패키지 만들기(SQL Server 비디오)](https://go.microsoft.com/fwlink/?LinkId=131023)를 참조하세요.  
  
### <a name="to-create-a-package-in-sql-server-data-tools-using-the-package-template"></a>패키지 템플릿을 사용하여 SQL Server Data Tools에서 패키지를 만들려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 패키지를 만들려는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 **SSIS 패키지** 폴더를 마우스 오른쪽 단추로 클릭한 후 **새 SSIS 패키지**를 클릭합니다.  
  
3.  선택적으로 제어 흐름, 데이터 흐름 태스크 및 이벤트 처리기를 패키지에 추가합니다. 자세한 내용은 [제어 흐름](control-flow/control-flow.md), [데이터 흐름](data-flow/data-flow.md) 및 [Integration Services&#40;SSIS&#41; 이벤트 처리기](integration-services-ssis-event-handlers.md)를 참조하세요.  
  
4.  **파일** 메뉴에서 **선택한 항목 저장** 을 클릭하여 새 패키지를 저장합니다.  
  
    > [!NOTE]  
    >  빈 패키지를 저장할 수 있습니다.  
  
  
