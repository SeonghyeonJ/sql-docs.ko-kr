---
title: ProtocolOrder 속성 (ClientNetworkProtocol 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8bccb7109972dea4697e9e289081cbf47d2f9492
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065597"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder 속성(ClientNetworkProtocol 클래스)
  [Setordervalue 메서드 (ClientNetworkProtocol 클래스)](clientnetworkprotocol-class.md) 메서드에 지정 된 대로 현재 참조 되는 클라이언트 네트워크 프로토콜의 순서 번호를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>부분  
 *object*  
 클라이언트에서 사용 하는 네트워크 프로토콜을 나타내는 [Clientnetworkprotocol 클래스](clientnetworkprotocol-class.md) 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 `uint32` 메서드에서 설정한 현재 참조되는 클라이언트 네트워크 프로토콜의 순서 번호를 지정하는 `OrderValue` 값입니다. 클라이언트 네트워크 프로토콜이 해제된 경우 이 값은 0입니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [클라이언트 프로토콜 구성](https://technet.microsoft.com/library/ms181035.aspx)   
 [클라이언트 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
