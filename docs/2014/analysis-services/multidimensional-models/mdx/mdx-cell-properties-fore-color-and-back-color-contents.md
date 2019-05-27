---
title: FORE_COLOR 및 BACK_COLOR Contents (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- FORE_COLOR contents
- backgrounds [MDX]
- cells [MDX]
- colors [MDX]
- storing cell color information
- cell backgrounds
- BACK_COLOR contents
ms.assetid: ff8f40cb-2ac4-4fc2-9761-7f1b14c17c8c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecd8bb157d7b501d29230c91d87f148ae738ff45
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66074406"
---
# <a name="forecolor-and-backcolor-contents-mdx"></a>FORE_COLOR 및 BACK_COLOR 내용(MDX)
  `FORE_COLOR` 및 `BACK_COLOR` 셀 속성은 셀의 텍스트 및 배경의 색 정보를 Microsoft Windows 운영 체제의 빨간색-녹색-파란색(RGB) 형식으로 저장합니다.  
  
 일반적인 RGB 색의 유효 범위는 0부터 16,777,215(&H00FFFFFF)까지입니다. 이 범위에 속하는 숫자의 상위 바이트는 항상 0이며 최하위부터 최상위에 이르는 하위 3바이트가 빨간색, 녹색, 파란색의 양을 결정합니다. 빨간색, 녹색, 파란색 구성 요소는 각각 0부터 255(&HFF) 사이의 숫자로 표시됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [셀 속성 사용&#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)  
  
  
