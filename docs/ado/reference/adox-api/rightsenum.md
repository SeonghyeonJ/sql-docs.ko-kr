---
title: RightsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RightsEnum
helpviewer_keywords:
- RightsEnum enumeration [ADOX]
ms.assetid: 55ee67c7-a583-42aa-849a-78264b4cb614
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6db3d1fecd8a2670a81fb239cb1a100389be21a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965277"
---
# <a name="rightsenum"></a>RightsEnum
개체의 그룹 또는 사용자에 대 한 권한 또는 사용 권한을 지정 합니다.  
  
|지속적임|값|Description|  
|--------------|-----------|-----------------|  
|**adRightCreate**|16384 (&H4000)|사용자 또는 그룹에이 유형의 새 개체를 만들 수 있는 권한이 있습니다.|  
|**adRightDelete**|65536 (&H10000)|사용자 또는 그룹에 개체의 데이터를 삭제할 수 있는 권한이 있습니다. **테이블과**같은 개체의 경우 사용자에 게 레코드에서 데이터 값을 삭제할 수 있는 권한이 있습니다.|  
|**adRightDrop**|256 (&H100)|사용자 또는 그룹에 카탈로그에서 개체를 제거할 수 있는 권한이 있습니다. 예를 들어 테이블 삭제 SQL 명령을 통해 **테이블** 을 삭제할 수 있습니다.|  
|**adRightExclusive**|512 (&H200)|사용자 또는 그룹에 개체에만 액세스할 수 있는 권한이 있습니다.|  
|**adRightExecute**|536870912 (&H20000000)|사용자 또는 그룹에 개체를 실행할 수 있는 권한이 있습니다.|  
|**adRightFull**|268435456 (&H10000000)|사용자 또는 그룹에는 개체에 대 한 모든 권한이 있습니다.|  
|**adRightInsert**|32768 (&H8000)|사용자 또는 그룹에 개체를 삽입할 수 있는 권한이 있습니다. **테이블과**같은 개체의 경우 사용자에 게 테이블에 데이터를 삽입할 수 있는 권한이 있습니다.|  
|**adRightMaximumAllowed**|33554432 (&H2000000)|사용자 또는 그룹에는 공급자가 허용 하는 최대 권한 수가 있습니다. 특정 사용 권한은 공급자에 따라 다릅니다.|  
|**adRightNone**|0|사용자 또는 그룹에 개체에 대 한 권한이 없습니다.|  
|**adRightRead**|-2147483648 (&H80000000)|사용자 또는 그룹에 개체를 읽을 수 있는 권한이 있습니다. [테이블과](../../../ado/reference/adox-api/table-object-adox.md)같은 개체의 경우 사용자에 게 테이블의 데이터를 읽을 수 있는 권한이 있습니다.|  
|**adRightReadDesign**|1024 (&H400)|사용자 또는 그룹에 개체에 대 한 디자인을 읽을 수 있는 권한이 있습니다.|  
|**adRightReadPermissions**|131072 (&H20000)|사용자 또는 그룹은 카탈로그의 개체에 대 한 특정 사용 권한을 볼 수 있지만 변경할 수는 없습니다.|  
|**adRightReference**|8192 (&H2000)|사용자 또는 그룹에 개체를 참조할 수 있는 권한이 있습니다.|  
|**adRightUpdate**|1073741824 (&H40000000)|사용자 또는 그룹에 개체를 업데이트할 수 있는 권한이 있습니다. **테이블과**같은 개체의 경우 사용자에 게 테이블의 데이터를 업데이트할 수 있는 권한이 있습니다.|  
|**adRightWithGrant**|4096 (&H1000)|사용자 또는 그룹에 개체에 대 한 사용 권한을 부여할 수 있는 권한이 있습니다.|  
|**adRightWriteDesign**|2048 (&H800)|사용자 또는 그룹에 개체에 대 한 디자인을 수정할 수 있는 권한이 있습니다.|  
|**adRightWriteOwner**|524288 (&H80000)|사용자 또는 그룹에 개체 소유자를 수정할 수 있는 권한이 있습니다.|  
|**adRightWritePermissions**|262144 (&H40000)|사용자 또는 그룹은 카탈로그의 개체에 대 한 특정 사용 권한을 수정할 수 있습니다.|  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[GetPermissions 메서드(ADOX)](../../../ado/reference/adox-api/getpermissions-method-adox.md)|[SetPermissions 메서드(ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)|
