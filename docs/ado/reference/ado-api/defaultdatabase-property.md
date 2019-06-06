---
title: DefaultDatabase 속성 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2eb89353c29ae58194f89b48502f0a9cc5522b58
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66695446"
---
# <a name="defaultdatabase-property"></a>DefaultDatabase 속성
에 대 한 기본 데이터베이스 지정을 [연결](../../../ado/reference/ado-api/connection-object-ado.md) 개체입니다.  
  
## <a name="settings-and-return-values"></a>설정 및 반환 값  
 설정 하거나 반환 된 **문자열** 공급자에서 사용할 수 있는 데이터베이스의 이름으로 계산 되는 값입니다.  
  
## <a name="remarks"></a>Remarks  
 사용 된 **DefaultDatabase** 속성을 설정 하거나 특정 기본 데이터베이스의 이름을 반환할 **연결** 개체입니다.  
  
 기본 데이터베이스의 경우 SQL 문자열 개체는 데이터베이스에 액세스 하는 비 정규화 된 구문을 사용할 수 있습니다. 개체에 지정 된 것과 다른 데이터베이스에 액세스 하는 **DefaultDatabase** 속성을 원하는 데이터베이스 이름으로 개체 이름을 정규화 해야 합니다. 공급자 연결 시 기본 데이터베이스 정보를 작성 합니다 **DefaultDatabase** 속성입니다. 일부 공급자는 연결당 하나의 데이터베이스만 허용, 변경할 수 없습니다 경우에 **DefaultDatabase** 속성입니다.  
  
 일부 데이터 원본 및 공급자에는이 기능을 지원 하지 않을 수 및 오류 또는 빈 문자열을 반환할 수 있습니다.  
  
> [!NOTE]
>  **원격 데이터 서비스 사용** 이 속성은 클라이언트 쪽에서 사용할 수 없습니다 **연결** 개체입니다.  
  
## <a name="applies-to"></a>적용 대상  
 [연결 개체(ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [Provider 및 DefaultDatabase 속성 예제 (VB)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Provider 및 DefaultDatabase 속성 예제(VC++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
