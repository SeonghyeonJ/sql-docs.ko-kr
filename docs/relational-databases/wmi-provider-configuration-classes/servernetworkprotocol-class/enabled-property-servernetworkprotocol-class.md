---
title: 속성 (ServerNetworkProtocol 클래스)를 사용 하도록 설정 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: a514822a-91f1-4aca-9175-2b96cff29700
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 91368428dae14aae8dc47f428cede3a0a37f9308
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071568"
---
# <a name="enabled-property-servernetworkprotocol-class"></a>Enabled 속성(ServerNetworkProtocol 클래스)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  서버 네트워크 프로토콜이 설정되었는지 여부를 지정하는 부울 속성을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>부분  
 *object*  
 A [ServerNetworkProtocol 클래스](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) 인스턴스에서 사용 하는 네트워크 프로토콜을 나타내는 개체입니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 서버 네트워크 프로토콜이 사용 되는지 여부를 지정 하는 부울 값: **true** 서버 네트워크 프로토콜을 사용 하는 경우 나 **false** 서버 네트워크 프로토콜이 해제 되었음을 나타냅니다.  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>관련 항목  
 [서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
