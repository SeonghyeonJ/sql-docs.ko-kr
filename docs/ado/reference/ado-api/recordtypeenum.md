---
description: RecordTypeEnum
title: RecordTypeEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordTypeEnum
helpviewer_keywords:
- RecordTypeEnum enumeration [ADO]
ms.assetid: f557e537-015d-4ba7-8a41-a6f00b366a91
author: rothja
ms.author: jroth
ms.openlocfilehash: ded4106b770ff62edd4b79401885ee5ce3101798
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989664"
---
# <a name="recordtypeenum"></a>RecordTypeEnum
[Record](./record-object-ado.md) 개체의 유형을 지정 합니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|**adSimpleRecord**|0|*단순* 레코드 (자식 노드를 포함 하지 않음)를 나타냅니다.|  
|**adCollectionRecord**|1|*컬렉션* 레코드 (자식 노드 포함)를 나타냅니다.|  
|**adRecordUnknown**|-1|이 **레코드** 의 형식을 알 수 없음을 나타냅니다.|  
|**adStructDoc**|2|COM 구조적 문서를 나타내는 *컬렉션* 레코드의 특수 한 종류를 나타냅니다.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 동급  
 이러한 상수에는 ADO/WFC 해당 항목이 없습니다.  
  
## <a name="applies-to"></a>적용 대상  
 [RecordType 속성(ADO)](./recordtype-property-ado.md)