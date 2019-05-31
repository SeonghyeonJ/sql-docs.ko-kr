---
title: '예: ID 및 IDREFS 지시어 지정 | Microsoft Docs'
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREFS directive
- ID directive
ms.assetid: 99b9f0d8-ecbb-4225-859f-881066c09785
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7636828b19d156c9d4a2c9b8503fd81a9d1ec01d
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175394"
---
# <a name="example-specifying-the-id-and-idrefs-directives"></a>예: ID 및 IDREFS 지시어 지정

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

요소 특성을 **ID** 유형의 특성으로 지정한 다음 **IDREFS** 특성을 사용하여 이 특성을 참조할 수 있습니다. 이러한 방식은 문서 간 연결을 설정하며 관계형 데이터베이스의 기본 키 및 외래 키 관계와 비슷합니다.  
  
 이 예에서는 **ID** 및 **IDREFS** 지시어를 사용하여 **ID** 및 **IDREFS** 유형의 특성을 만드는 방법을 보여 줍니다. ID는 정수 값일 수 없기 때문에 이 예에서는 ID 값이 변환됩니다. 즉, 다른 유형으로 캐스팅됩니다. ID 값에는 접두사가 사용됩니다.  
  
 다음과 같이 XML을 생성한다고 가정해 보십시오.  
  
```xml
<Customer CustomerID="C1" SalesOrderIDList=" O11 O22 O33..." >
    <SalesOrder SalesOrderID="O11" OrderDate="..." />  
    <SalesOrder SalesOrderID="O22" OrderDate="..." />  
    <SalesOrder SalesOrderID="O33" OrderDate="..." />  
    ...  
</Customer>  
```  
  
`<Customer>` 요소의 `SalesOrderIDList` 특성은 `<SalesOrder>` 요소의 `SalesOrderID` 특성을 참조하는 다중 값 특성입니다. 이 연결을 구성하려면 `SalesOrderID` 특성이 `ID` 유형으로 선언되어야 하며 `<Customer>` 요소의 `SalesOrderIDList` 특성이 `IDREFS` 유형으로 선언되어야 합니다. 한 고객이 여러 개의 주문을 요청할 수 있으므로 `IDREFS` 유형이 사용됩니다.
  
 **IDREFS** 유형의 요소에는 또한 두 개 이상의 값이 포함됩니다. 따라서 같은 태그, 부모 및 키 열 정보를 다시 사용하는 별개의 SELECT 절을 사용해야 합니다. 그런 다음 `ORDER BY` 에서 **IDREFS** 값을 구성하는 행 시퀀스가 해당 부모 요소 아래에 함께 그룹화되어 표시되도록 해야 합니다.  
  
 이 쿼리는 원하는 XML을 생성합니다. 이 쿼리는 `ID` 및 `IDREFS` 지시어를 사용하여 열 이름(`SalesOrder!2!SalesOrderID!ID`, `Customer!1!SalesOrderIDList!IDREFS`)에 있는 유형을 덮어씁니다.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID   [Customer!1!CustomerID],  
        NULL           [Customer!1!SalesOrderIDList!IDREFS],
        NULL           [SalesOrder!2!SalesOrderID!ID],  
        NULL           [SalesOrder!2!OrderDate]  
FROM   Sales.Customer C   

UNION ALL   
SELECT  1 as Tag,  
        0 as Parent,  
        C.CustomerID,  
        'O-'+CAST(SalesOrderID as varchar(10)),   
        NULL,  
        NULL  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID  

UNION ALL  
SELECT 2 as Tag,  
       1 as Parent,  
        C.CustomerID,  
        NULL,  
        'O-'+CAST(SalesOrderID as varchar(10)),  
        OrderDate  
FROM   Sales.Customer AS C  
INNER JOIN Sales.SalesOrderHeader AS SOH  
    ON  C.CustomerID = SOH.CustomerID
ORDER BY [Customer!1!CustomerID] ,
         [SalesOrder!2!SalesOrderID!ID],  
         [Customer!1!SalesOrderIDList!IDREFS]  
FOR XML EXPLICIT;  
```  
  
## <a name="see-also"></a>참고 항목  
 [FOR XML에서 EXPLICIT 모드 사용](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
