---
title: ISSCommandWithParameters::GetParameterProperties(OLE DB) | Microsoft Docs
description: ISSCommandWithParameters::GetParameterProperties는 OLE DB Driver for SQL Server에서 각 UDT 또는 XML 매개 변수에 하나씩 속성 집합 구조체의 배열을 반환합니다.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8631c9c1beed054b57fd368dd567e3568c213b50
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862140"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties(OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  각 UDT 또는 XML 매개 변수당 SSPARAMPROPS 속성 집합을 하나씩 반환하는 방식으로 SSPARAMPROPS 속성 집합 구조의 배열을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
HRESULT GetParameterProperties(  
      DB_UPARAMS *pcParams,  
      SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>인수  
 *pcParams*[out][in]  
 *prgParamProperties*에 반환된 SSPARAMPROPS 구조의 개수를 포함하는 메모리에 대한 포인터입니다.  
  
 *prgParamProperties*[out]  
 SSPARAMPROPS 구조의 배열이 반환될 메모리에 대한 포인터입니다. 공급자는 구조에 사용할 메모리를 할당하고 이 메모리에 대한 주소를 반환합니다. 소비자는 구조가 더 이상 필요 없게 되면 `IMalloc::Free`I를 사용하여 이 메모리를 해제합니다. 변형에 BSTR과 같은 참조 형식이 포함되어 있는 경우 메모리 누수를 방지하려면 소비자는 *prgParamProperties*에 대해 `IMalloc::Free`를 호출하기 전에 각 DBPROP 구조의 *vValue* 속성에 대해 `VariantClear`를 호출해야 합니다. 출력에서 *pcParams*가 0이거나 DB_E_ERRORSOCCURRED 외의 오류가 발생하는 경우 공급자는 메모리를 할당하지 않으며 출력에서 *prgParamProperties*가 Null 포인터인지 확인합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 `GetParameterProperties` 메서드는 DB_S_ERRORSOCCURRED 및 DB_E_ERRORSOCCURED를 발생시킬 수 없다는 점을 제외하고 핵심 OLE DB `ICommandProperties::GetProperties` 메서드와 동일한 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 `ISSCommandWithParameters::GetParameterProperties` 메서드는 `GetParameterInfo`에 따라 일정하게 동작합니다. [`ISSCommandWithParameters::SetParameterProperties`](../../oledb/ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) 또는 `SetParameterInfo`가 호출되지 않았거나 cParams가 0인 상태로 호출된 경우 `GetParameterInfo`가 매개 변수 정보 를 파생시켜 반환합니다. 하나 이상의 매개 변수에 대해 `ISSCommandWithParameters::SetParameterProperties` 또는 `SetParameterInfo`가 호출된 경우 `ISSCommandWithParameters::GetParameterProperties` 메서드는 `ISSCommandWithParameters::SetParameterProperties`가 호출된 매개 변수에 대해서만 속성을 반환합니다. `ISSCommandWithParameters::SetParameterProperties`가 `ISSCommandWithParameters::GetParameterProperties` 또는 `GetParameterInfo` 이후에 호출된 경우 `ISSCommandWithParameters::GetParameterProperties`에 대한 후속 호출은 `ISSCommandWithParameters::SetParameterProperties` 메서드가 호출된 매개 변수에 대해 재정의된 값을 반환합니다.  
  
 SSPARAMPROPS 구조는 다음과 같이 정의됩니다.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|멤버|Description|  
|------------|-----------------|  
|*iOrdinal*|전달된 매개 변수의 서수입니다.|  
|*cPropertySets*|*rgPropertySets*에 있는 DBPROPSET 구조의 개수입니다.|  
|*rgPropertySets*|DBPROPSET 구조의 배열을 반환할 메모리에 대한 포인터입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [ISSCommandWithParameters&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
