---
title: 인라인 XDR 스키마 생성 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- XDR schemas [SQL Server]
- inline XDR schema generation [SQL Server]
- XMLDATA option
- FOR XML clause, inline XDR schema generation
ms.assetid: 2a40d617-9724-4f7d-80a4-a85c702f14d0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f93170d78512ba3c79e1dfa4b8e5e9aae83a4862
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527705"
---
# <a name="generate-an-inline-xdr-schema"></a>인라인 XDR 스키마 생성
  FOR XML의 **XMLDATA** 지시어는 쿼리 결과와 함께 인라인 XDR 스키마를 반환합니다. 하지만 XDR 스키마는 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이상 버전에서 제공되는 새로운 데이터 형식과 기타 향상된 기능 중 일부를 지원하지 않습니다. 대신 [XMLSCHEMA](generate-an-inline-xsd-schema.md)지시어를 사용하여 인라인 XSD 스키마를 요청할 수 있습니다.  
  
> [!IMPORTANT]  
>  XMLDATA 지시어에 FOR XML 옵션은 더 이상 사용되지 않습니다. RAW 및 AUTO 모드의 경우 XSD 생성을 사용하세요. EXPLICIT 모드의 XMLDATA 지시어의 경우에는 대체할 옵션이 없습니다. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 또한 인라인 XDR 스키마 지원에 대한 다음 정보를 참조하십시오.  
  
-   FOR XML 쿼리 결과에 **xml** 유형의 열이 포함되어 있고 인라인 XDR 스키마를 요청하면 오류가 반환됩니다. 인라인 XDR은 이러한 유형을 지원하지 않습니다.  
  
-   **(n)varchar(max)** 및 **(n)varbinary(max)** 유형은 각각 **(n)varchar(n)** 및 **varbinary(n)** 으로 매핑됩니다.  
  
-   호환성 모드가 90 이상으로 설정된 경우 **timestamp** 값은 **varbinary(8)** 데이터로 간주되며 이진 데이터와 같이 취급되고 다음과 같이 결과에 반환됩니다.  
  
    -   **binary base64** 가 지정된 경우 Base 64 인코딩이 사용됩니다.  
  
    -   **binary base64** 가 지정되지 않은 경우 URL 인코딩이 AUTO 모드로 사용됩니다.  
  
  
