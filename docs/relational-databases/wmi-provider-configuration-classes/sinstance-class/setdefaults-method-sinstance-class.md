---
title: SetDefaults 메서드 (SInstance 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (SInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: efef6f438e63fb195b0b97332dad334f111a1658
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62515468"
---
# <a name="setdefaults-method-sinstance-class"></a>SetDefaults 메서드(SInstance 클래스)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  인스턴스에 대 한 모든 기본값을 설정 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 기존 데이터 덮어쓰기 옵션을 사용 하 여 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>부분  
 *object*  
 [SInstance 클래스](../../../relational-databases/wmi-provider-configuration-classes/sinstance-class/sinstance-class.md) 서버 인스턴스를 나타내는 개체입니다.  
  
#### <a name="parameters"></a>매개 변수  
  
|매개 변수|Description|  
|---------------|-----------------|  
|*OverwriteAll*|인스턴스의 기존 값을 덮어쓸지 여부를 지정 하는 부울 값을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 클라이언트: **true** 기존의 데이터를 덮어쓰는 경우 또는 **false** 경우 기존 데이터를 덮어쓰지 않습니다.|  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 **uint32** 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>관련 항목  
 [서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
