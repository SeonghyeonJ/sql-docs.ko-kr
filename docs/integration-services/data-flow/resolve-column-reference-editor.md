---
title: 열 참조 확인 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.resolvereferences.preview.F1
- sql13.dts.designer.resolvereferences.mapper.F1
ms.assetid: bb3ee33c-79c4-4c76-a82f-71581b4a60f1
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 28ff4c49c2b1dadcde15171a2a5102f29e3ff438
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86915359"
---
# <a name="resolve-column-reference-editor"></a>열 참조 확인 편집기

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  입력 경로의 연결이 끊어졌거나 경로에 매핑되지 않은 열이 있는 경우 해당 데이터 경로 옆에 오류 아이콘이 표시됩니다. 열 참조 오류 확인을 간소화하기 위해 참조 확인 편집기가 실행 트리의 모든 경로에 대해 매핑되지 않은 출력 열과 매핑되지 않은 입력 열을 연결하도록 지원합니다. 참조 확인 편집기는 또한 확인 중인 경로를 나타내기 위해 해당 경로를 강조 표시합니다.  
  
> [!NOTE]  
>  입력 경로의 연결이 끊긴 경우에도 구성 요소를 편집할 수 있습니다.  
  
 모든 열 참조가 확인된 후 다른 데이터 경로 오류가 없으면 데이터 경로 옆에 오류 아이콘이 표시되지 않습니다.  
  
## <a name="options"></a>옵션  
 **매핑되지 않은 출력 열(원본)**     
 현재 매핑되지 않은 업스트림 경로의 열  
  
**매핑된 열(원본)**     
 다운스트림 경로의 열에 매핑된 업스트림 경로의 열  
  
**매핑된 열(대상)**     
 다운스트림 경로의 열에 매핑된 업스트림 경로의 열  
  
**매핑되지 않은 입력 열(대상)**     
 현재 매핑되지 않은 다운스트림 경로의 열  
  
**매핑되지 않은 입력 열 삭제**  
 데이터 경로 대상에서 매핑되지 않은 열을 무시하려면 매핑되지 않은 입력 열 삭제를 선택합니다. 변경 내용 미리 보기 단추를 클릭하면 확인 단추를 누를 경우 적용되는 변경 내용 목록이 표시됩니다.  
  
  
