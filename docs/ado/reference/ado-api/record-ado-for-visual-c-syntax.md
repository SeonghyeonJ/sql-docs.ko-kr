---
description: 레코드(Visual C++ 구문에 대한 ADO)
title: Record (Visual C++ 구문에 대 한 ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- Record collection [ADO], ADO for Visual C++ syntax
ms.assetid: c4ce8532-a4d8-4f74-9488-9389b6695958
author: rothja
ms.author: jroth
ms.openlocfilehash: 9f4dd5b6fe3329e01710366b99142fa999a86cab
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88772642"
---
# <a name="record-ado-for-visual-c-syntax"></a>레코드(Visual C++ 구문에 대한 ADO)
## <a name="methods"></a>메서드  
  
```  
Cancel(void)  
Close(void)  
CopyRecord(BSTR Source, BSTR Destination, BSTR UserName, BSTR Password, CopyRecordOptionsEnum Options, VARIANT_BOOL Async, BSTR *pbstrNewURL)  
DeleteRecord(BSTR Source, VARIANT_BOOL Async)  
GetChildren(_ADORecordset **ppRSet)  
MoveRecord(BSTR Source, BSTR Destination, BSTR UserName, BSTR Password, MoveRecordOptionsEnum Options, VARIANT_BOOL Async, BSTR *pbstrNewURL)  
Open(VARIANT Source, VARIANT ActiveConnection, ConnectModeEnum Mode, RecordCreateOptionsEnum CreateOptions, RecordOpenOptionsEnum Options, BSTR UserName, BSTR Password)  
```  
  
## <a name="properties"></a>속성  
  
```  
get_ActiveConnection(VARIANT *pvar)  
put_ActiveConnection(BSTR bstrConn)  
putref_ActiveConnection(_ADOConnection *Con)  
get_Fields(ADOFields **ppFlds)  
get_Mode(ConnectModeEnum *pMode)  
put_Mode(ConnectModeEnum Mode)  
get_ParentURL(BSTR *pbstrParentURL)  
get_RecordType(RecordTypeEnum *pType)  
get_Source(VARIANT *pvar)  
put_Source(BSTR Source)  
putref_Source(IDispatch *Source)  
get_State(ObjectStateEnum *pState)  
```  
  
## <a name="see-also"></a>참고 항목  
 [레코드 개체(ADO)](./record-object-ado.md)