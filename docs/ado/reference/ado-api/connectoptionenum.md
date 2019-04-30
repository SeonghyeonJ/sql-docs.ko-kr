---
title: ConnectOptionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ConnectOptionEnum
helpviewer_keywords:
- ConnectOptionEnum enumeration [ADO]
ms.assetid: bff07eeb-dee3-4e4e-9b2d-d56061ea744d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9df3fd695e9bf281133dabf436e5e8b5de7e0b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309152"
---
# <a name="connectoptionenum"></a>ConnectOptionEnum
지정 여부를 [열기](../../../ado/reference/ado-api/open-method-ado-connection.md) 메서드를 [연결](../../../ado/reference/ado-api/connection-object-ado.md) 개체 연결 (동기적으로) 한 후 또는 그 이전에 반환 해야 (비동기).  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**adAsyncConnect**|16|연결을 비동기적으로 엽니다. 합니다 [ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md) 연결 수를 결정 하는 이벤트를 사용할 수 있습니다.|  
|**adConnectUnspecified**|-1|기본. 동기적으로 연결을 엽니다.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 해당  
 Package: **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.ConnectOption.ASYNCCONNECT|  
|AdoEnums.ConnectOption.CONNECTUNSPECIFIED|  
  
## <a name="applies-to"></a>적용 대상  
 [Open 메서드(ADO 연결)](../../../ado/reference/ado-api/open-method-ado-connection.md)
