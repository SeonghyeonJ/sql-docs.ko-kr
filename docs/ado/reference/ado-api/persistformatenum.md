---
title: PersistFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2a26fd370e80cb288ee62b0fc53ed6670300172e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917609"
---
# <a name="persistformatenum"></a>PersistFormatEnum
저장할 형식을 지정 된 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md)합니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|Microsoft 고급 데이터 테이블 그램 (ADTG) 형식을 나타냅니다.|  
|**adPersistADO**|1|ADO의 Extensible Markup Language (XML) 형식으로 사용 됨을 나타냅니다. 이 값은 adPersistXML 동일 이며 이전 버전과 호환성에 대 한 포함 합니다.|  
|**adPersistXML**|1|Extensible Markup Language (XML) 형식을 나타냅니다.|  
|**adPersistProviderSpecific**|2|공급자가 유지 함을 나타냅니다 합니다 **레코드 집합** 자체 형식을 사용 하 여 합니다.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 해당  
 Package: **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>적용 대상  
 [Save 메서드](../../../ado/reference/ado-api/save-method.md)
