---
title: '유효한 ID, IDREF 및 IDREFS 유형 특성을 사용 하 여 sql: prefix (SQLXML 4.0) 만들기 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- annotated XSD schemas, ID type attribute
- IDREF type attribute [SQLXML]
- annotated XSD schemas, IDREFS type attribute
- ID type attribute [SQLXML]
- sql:prefix
- prefix annotation
- IDREF relationships [SQLXML]
- IDREFS type attribute [SQLXML]
- annotated XSD schemas, IDREF type attribute
- ID relationships [SQLXML]
ms.assetid: 1c7f77d3-81f3-4820-bb63-c4aaa4ea9aa1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ba60e3b8c871f885c2cd7d4115c0ae7dc2c40433
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650440"
---
# <a name="creating-valid-id-idref-and-idrefs-type-attributes-using-sqlprefix-sqlxml-40"></a>sql:prefix(SQLXML 4.0)를 사용하여 유효한 ID, IDREF 및 IDREFS 유형 특성 만들기
  특성을 ID 유형 특성으로 지정할 수 있습니다. 그런 다음 IDREF 또는 IDREFS로 지정된 특성을 사용하여 ID 유형 특성을 참조하고 문서 간의 링크를 사용할 수 있습니다.  
  
 ID, IDREF 및 IDREFS는 몇 가지 차이점은 있지만 데이터베이스의 PK/FK(기본 키/외래 키) 관계에 해당합니다. XML 문서에서 ID 유형 특성 값은 고유해야 합니다. 하는 경우 **CustomerID** 하 고 **OrderID** XML 문서에서 ID 유형으로 이러한 값은 고유 해야 하는 특성을 지정 합니다. 하지만 데이터베이스의 CustomerID 및 OrderID 열은 동일한 값을 가질 수 있습니다. 예를 들어 CustomerID = 1 및 OrderID = 1은 데이터베이스에서 유효합니다.  
  
 ID, IDREF 및 IDREFS 특성이 유효하려면 다음 조건을 충족해야 합니다.  
  
-   ID 값이 XML 문서 내에서 고유해야 합니다.  
  
-   모든 IDREF 및 IDREFS에 대해 참조된 ID 값이 XML 문서에 있어야 합니다.  
  
-   ID, IDREF 및 IDREFS 값은 명명된 토큰이어야 합니다. 예를 들어 정수 값 101은 ID 값일 수 없습니다.  
  
-   ID, IDREF 및 IDREFS 유형의 특성은 `text`, `ntext` 또는 `image` 유형이나 다른 이진 데이터 형식(예: `timestamp`)의 열에 매핑할 수 없습니다.  
  
 XML 문서에 ID가 여러 개 포함되어 있으면 `sql:prefix` 주석을 사용하여 고유한 값을 만듭니다.  
  
 XSD 고정 특성에는 `sql:prefix` 주석을 사용할 수 없습니다.  
  
## <a name="examples"></a>예  
 다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다. 자세한 내용은 [SQLXML 예 실행에 대 한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)합니다.  
  
### <a name="a-specifying-id-and-idrefs-types"></a>1. ID 및 IDREFS 유형 지정  
 다음 스키마에는  **\<고객 >** 구성 요소는  **\<순서 >** 자식 요소입니다. 합니다  **\<순서 >** 도 요소가 자식 요소에는  **\<OrderDetail >** 요소입니다.  
  
 **OrderIDList** 특성  **\<고객 >** 참조 하는 IDREFS 형식 특성을 **OrderID** 특성은  **\< 순서 >** 요소입니다.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
                 parent="Sales.Customer"  
                 parent-key="CustomerID"  
                 child="Sales.SalesOrderHeader"  
                 child-key="CustomerID" />  
    <sql:relationship name="OrderOrderDetail"  
                 parent="Sales.SalesOrderHeader"  
                 parent-key="SalesOrderID"  
                 child="Sales.SalesOrderDetail"  
                 child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
               sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                   sql:relationship="OrderOrderDetail"   
                   maxOccurs="unbounded" >  
                  <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="ProductID" type="xsd:string" />  
                   <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
               </xsd:element>  
             </xsd:sequence>  
             <xsd:attribute name="SalesOrderID"   
                            type="xsd:ID" sql:prefix="ord-" />  
             <xsd:attribute name="OrderDate" type="xsd:date" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CustomerID" type="xsd:string" />  
    <xsd:attribute name="OrderIDList" type="xsd:IDREFS"   
                   sql:relation="Sales.SalesOrderHeader" sql:field="SalesOrderID"  
                   sql:relationship="CustOrders" sql:prefix="ord-">  
    </xsd:attribute>  
  </xsd:complexType>  
</xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>스키마에 대해 예제 XPath 쿼리를 테스트하려면  
  
1.  위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다. 파일을 sqlPrefix.xml로 저장합니다.  
  
2.  다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다. sqlPrefix.xml을 저장한 디렉터리와 같은 디렉터리에 sqlPrefixT.xml로 파일을 저장합니다.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="sqlPrefix.xml">  
        /Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     매핑 스키마(sqlPrefix.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다. 또한 다음과 같이 절대 경로를 지정할 수 있습니다.  
  
    ```  
    mapping-schema="C:\SqlXmlTest\sqlPrefix.xml"  
    ```  
  
3.  SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.  
  
     자세한 내용은 [실행 SQLXML 쿼리에 ADO를 사용 하 여](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)입니다.  
  
 다음은 결과의 일부입니다.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" OrderIDList="ord-43860 ord-44501 ord-45283 ord-46042">  
    <Order SalesOrderID="ord-43860" OrderDate="2001-08-01" CustomerID="1">  
      <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
      <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
      ...  
    </Order>  
    ...  
 </Customer>  
</ROOT>  
```  
  
  
