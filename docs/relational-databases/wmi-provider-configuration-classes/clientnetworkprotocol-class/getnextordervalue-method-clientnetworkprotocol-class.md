---
title: GetNextOrderValue 메서드 (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- GetNextOrderValue Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- GetNextOrderValue method
ms.assetid: d741dc5c-c225-43d9-a730-7ad664ac525f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1f9b9a8d69dad76d2ec1d6e38f7151238d0e91c1
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73660743"
---
# <a name="getnextordervalue-method-clientnetworkprotocol-class"></a>GetNextOrderValue 메서드(ClientNetworkProtocol 클래스)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  프로토콜 목록에서 다음 위치에 있는 프로토콜을 선택합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object.GetNextOrderValue()  
```  
  
## <a name="parts"></a>부분  
 *object*  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 클라이언트에서 사용 하는 네트워크 프로토콜을 나타내는 [Clientnetworkprotocol 클래스](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) 개체입니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 **uint32** 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>관련 항목:  
 [클라이언트 프로토콜  구성](https://technet.microsoft.com/library/ms181035.aspx)  
 [클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
