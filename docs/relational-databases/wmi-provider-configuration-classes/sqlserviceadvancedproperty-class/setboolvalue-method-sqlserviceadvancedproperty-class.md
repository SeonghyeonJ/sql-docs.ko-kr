---
description: SetBoolValue 메서드(SqlServiceAdvancedProperty 클래스)
title: SetBoolValue 메서드 (SqlServiceAdvancedProperty)
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetBoolValue Method (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetBoolValue method
ms.assetid: 5252b439-fce5-446a-8e57-99e3054bee69
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1df2d43182d0f3f096ca6ccc4ddec6a7f5de2896
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546973"
---
# <a name="setboolvalue-method-sqlserviceadvancedproperty-class"></a>SetBoolValue 메서드(SqlServiceAdvancedProperty 클래스)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  속성의 부울 값을 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
object.SetBoolValue [= value]  
```  
  
## <a name="parts"></a>부분  
 *object*  
 고급 속성을 나타내는 [SqlServiceAdvancedProperty 클래스](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) 개체입니다.  
  
#### <a name="parameters"></a>매개 변수  
  
|매개 변수|Description|  
|---------------|-----------------|  
|*BoolValue*|고급 속성의 값을 지정하는 부울 값입니다.|  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 **uint32** 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.  
  
## <a name="remarks"></a>설명  
 속성을 부울 값으로 설정하려면 속성 값 형식이 부울이어야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [서비스 시작 및 중지](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
