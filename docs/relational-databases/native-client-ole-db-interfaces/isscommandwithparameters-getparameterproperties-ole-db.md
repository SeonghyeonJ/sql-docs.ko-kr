---
title: 'Isscommandwithparameters:: Getparameterproperties (OLE DB) | Microsoft Docs'
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
apitype: COM
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5e03e1ef1cd62dda40cd9b138c3d2ff3d7395ec
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050993"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

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
 SSPARAMPROPS 구조의 배열이 반환될 메모리에 대한 포인터입니다. 공급자는 구조에 대 한 메모리를 할당 하 고이 메모리에 주소를 반환 합니다. 사용 하 여이 메모리를 해제 하는 소비자 **imalloc:: Free** 경우 구조를 더 이상 필요 합니다. 호출 하기 전에 **imalloc:: Free** 에 대 한 *prgParamProperties*, 소비자도 호출 해야 합니다 **VariantClear** 에 대 한 합니다 *vValue* 속성 변형에 대 한 참조를 포함 하는 위치 하는 경우에서 메모리 누수를 방지 하기 위해 각 DBPROP 구조의 형식 (예: BSTR입니다.) 하는 경우 *pcParams* 는 출력 시 0이 있고 db_e_errorsoccurred 오류가 발생 한 공급자 메모리를 할당 하지 않습니다 되도록 *prgParamProperties* 출력에 null 포인터가 됩니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 합니다 **GetParameterProperties** 메서드에서 핵심 OLE DB 동일한 오류 코드도 반환 **icommandproperties:: Getproperties** 메서드는 DB_S_ERRORSOCCURRED 및 db_e_errorsoccured가 될 수 없습니다 발생합니다.  
  
## <a name="remarks"></a>설명  
 **Isscommandwithparameters:: Getparameterproperties** 기준으로 일관성 있게 동작 **GetParameterInfo**합니다. 하는 경우 [isscommandwithparameters:: Setparameterproperties](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md) 하거나 **SetParameterInfo** 호출 하지 않았거나 cparams를 0으로 **GetParameterInfo**매개 변수 정보를 파생 하 고이 반환 합니다. 하는 경우 **isscommandwithparameters:: Setparameterproperties** 하거나 **SetParameterInfo** 하나 이상의 매개 변수에 대 한 호출 된 **isscommandwithparameters:: Getparameterproperties**  는 해당 매개 변수에 속성을 반환 **isscommandwithparameters:: Setparameterproperties** 가 호출 되었습니다. 하는 경우 **isscommandwithparameters:: Setparameterproperties** 후에 호출 됩니다 **isscommandwithparameters:: Getparameterproperties** 하거나 **GetParameterInfo**, 에 대 한 후속 호출 **isscommandwithparameters:: Getparameterproperties** 는 해당 매개 변수에 대 한 재정의 값을 반환 **isscommandwithparameters::** 가 호출 되었습니다.  
  
 SSPARAMPROPS 구조는 다음과 같이 정의됩니다.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|멤버|설명|  
|------------|-----------------|  
|*iOrdinal*|전달된 매개 변수의 서수입니다.|  
|*cPropertySets*|*rgPropertySets*에 있는 DBPROPSET 구조의 개수입니다.|  
|*rgPropertySets*|DBPROPSET 구조의 배열을 반환할 메모리에 대한 포인터입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
