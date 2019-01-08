---
title: '부록 g: 이전 버전과 호환성에 대 한 드라이버 지침 | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d78de7b3bd1d91351a4159847d6605e30cc1353d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516897"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>부록 g: 이전 버전과 호환성에 대 한 드라이버 지침
이 부록에서는 ODBC 3에서 작동 하는 드라이버 작성자에 대 한 정보를 제공 합니다. *x* ODBC 2를 지원 해야 하는 드라이버. *x* 응용 프로그램입니다. 이전 버전과 호환성에 대 한 자세한 내용은 참조 하세요. [이전 버전과 호환성 및 표준 준수](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)합니다.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [블록 커서, 스크롤 가능 커서 및 ODBC 3.x 드라이버에 대 한 이전 버전과 호환성](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) -새 기능은 ODBC 3에 존재 하는 기능. *x* 하며 되지 않는 ODBC 2. *x*합니다. ODBC 3입니다. *x* 드라이버 일반적으로 없는 때문에 새로운 기능을 사용 하 여 이전 버전과 호환성에 대 한 걱정 ODBC 2. *x* 응용 프로그램에서 하지 사용 합니다. 이에 대 한 유일한 예외는 관련 된 기능 **SQLFetch**, **SQLFetchScroll**합니다 **SQLSetPos**, 및 **SQLExtendedFetch**; 자세한 내용은 내용은이 부록의 뒷부분에 나오는 참조 하십시오입니다.  
  
-   [사용 되지 않는 함수 매핑](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) -중복 기능은 ODBC 3에서 다르게 구현 되는 기능. *x* 및 ODBC 2. *x*합니다. ODBC 3입니다. *x* 드라이버를 드라이버 관리자는 항상 ODBC 2 매핑되기 때문에 중복 된 기능을 사용 하 여 이전 버전과 호환성에 걱정할 필요가 없습니다. *x* 기능을 ODBC 3. *x* 기능이 호출 하는 ODBC 3. *x* 드라이버입니다. 따라서 ODBC 3입니다. *x* 드라이버 확인만 ODBC 3. *x* 기능입니다. 자세한 내용은 이러한 매핑에 대 한 참조를이 부록의 뒷부분에 나오는.  
  
-   [동작 변경 내용 및 ODBC 3.x 드라이버](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) -동작 변경이 ODBC 3에서 다르게 처리 되는 기능. *x* 및 ODBC 2. *x*합니다. ODBC 3입니다. *x* 드라이버 동작 변경 내용에 걱정 하 고 응용 프로그램에 의해 설정 된 SQL_ATTR_ODBC_VERSION 환경 특성에 대 한 응답을 수행 해야 합니다.
