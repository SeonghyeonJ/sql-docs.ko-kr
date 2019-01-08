---
title: 데이터 흐름의 구성 요소 연결 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 14bbe37b0b13c9325c56bd0892a4b660c202c313
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52796005"
---
# <a name="connect-components-in-a-data-flow"></a>데이터 흐름의 구성 요소 연결
  이 절차에서는 데이터 흐름의 구성 요소 출력을 동일 데이터 흐름 내의 다른 구성 요소에 연결하는 방법에 대해 설명합니다.  
  
### <a name="to-connect-components-in-a-data-flow"></a>데이터 흐름에서 구성 요소를 연결하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  **제어 흐름** 탭을 클릭한 후 구성 요소를 연결하려는 데이터 흐름이 들어 있는 데이터 흐름 태스크를 두 번 클릭합니다.  
  
4.  **데이터 흐름** 탭의 디자인 화면에서 연결하려는 변환 또는 원본을 선택합니다.  
  
5.  변환 또는 원본의 녹색 출력 화살표를 변환 또는 대상으로 끌어 옵니다. 일부 데이터 흐름 구성 요소에는 오류 출력이 포함되어 있으며 이 출력도 동일한 방법으로 연결할 수 있습니다.  
  
    > [!NOTE]  
    >  일부 데이터 흐름 구성 요소에는 여러 출력이 포함될 수 있으며 각 출력을 서로 다른 변환이나 대상으로 연결할 수 있습니다.  
  
6.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 흐름에서 구성 요소 추가 또는 삭제](data-flow.md)   
 [데이터 흐름 구성 요소에서 오류 출력 구성](../configure-an-error-output-in-a-data-flow-component.md)   
 [데이터 흐름](data-flow.md)  
  
  
