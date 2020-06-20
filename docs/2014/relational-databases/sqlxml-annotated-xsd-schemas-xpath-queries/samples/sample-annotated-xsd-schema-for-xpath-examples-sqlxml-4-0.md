---
title: XPath 예제에 대 한 주석이 추가 된 예제 XSD 스키마 (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], annotated XSD schemas in queries
- annotated XSD schemas, samples
- annotated XSD schemas, queries
ms.assetid: fefa2cc8-2d3c-4336-aeae-ce063a3a8df2
author: rothja
ms.author: jroth
ms.openlocfilehash: fe8b6dbeb50d289a1774d78bf4d2b214711b24c4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015088"
---
# <a name="sample-annotated-xsd-schema-for-xpath-examples-sqlxml-40"></a>XPath 예에 대한 주석이 추가된 예제 XSD 스키마(SQLXML 4.0)
  이 섹션의 예제 XPath 쿼리는 매핑 스키마를 참조합니다. 해당 매핑 스키마는 주석이 추가된 XSD(XML 스키마) 파일입니다. 매핑 스키마에 대 한 자세한 내용은 [주석이 추가 된 XSD 스키마 소개 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)을 참조 하세요.  
  
 주석이 추가된 XSD 스키마에 대해 XPath 쿼리를 실행하려면 다음 작업을 수행해야 합니다.  
  
-   XPath 쿼리가 포함된 템플릿을 만듭니다. 이 템플릿에서 XPath 쿼리를 실행할 대상 매핑 스키마를 지정합니다. 이 경우 템플릿 파일과 연결된 디렉터리(또는 템플릿에 상대 경로가 `mapping-schema` 특성 값으로 지정되어 있는 경우 해당 하위 디렉터리 중 하나)에 매핑 스키마를 저장해야 합니다.  
  
-   쿼리를 실행하는 데 ADO에 대한 SQLXML 확장을 사용하는 테스트 애플리케이션을 만듭니다. 자세한 내용은 [ADO를 사용 하 여 SQLXML 4.0 쿼리 실행](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)을 참조 하세요.  
  
 이 섹션의 모든 예에서는 이해를 돕기 위해 템플릿에 XPath 쿼리를 지정하고 ADO를 사용하여 템플릿을 실행합니다. 따라서 SampleSchema1.xml이라는 다음 매핑 스키마 파일을 사용해야 합니다. 이 파일을 템플릿이 저장된 디렉터리에 저장합니다.  
  
## <a name="sample-annotated-xsd-schema-sampleschema1xml"></a>주석이 추가된 예제 XSD 스키마(SampleSchema1.xml)  
  
```  
<?xml version="1.0"?>  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders" />  
     </xsd:sequence>  
     <xsd:attribute name="CustomerID" type="xsd:ID"/>  
     <xsd:attribute name="TerritoryID"/>  
     <xsd:attribute name="AccountNumber"/>  
     <xsd:attribute name="CustomerType"/>  
     <xsd:attribute name="Orders" type="xsd:IDREFS" sql:prefix="Ord-"/>  
  </xsd:complexType>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="OrderType"/>  
  
  <xsd:complexType name="OrderType">  
     <xsd:sequence>  
        <xsd:element name="OrderDetail"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOrderDetail" />  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:ID" sql:prefix="Ord-"/>  
     <xsd:attribute name="SalesPersonID"/>  
     <xsd:attribute name="OrderDate"/>  
     <xsd:attribute name="DueDate"/>  
     <xsd:attribute name="ShipDate"/>  
  </xsd:complexType>  
  
  <xsd:element name="OrderDetail" sql:relation="Sales.SalesOrderDetail" type="OrderDetailType"/>  
  
  <xsd:complexType name="OrderDetailType">  
    <xsd:attribute name="ProductID" type="xsd:IDREF"/>  
    <xsd:attribute name="UnitPrice"/>  
    <xsd:attribute name="OrderQty"/>  
    <xsd:attribute name="UnitPriceDiscount"/>  
  </xsd:complexType>  
  
  <xsd:element name="UnitPriceDiscount" sql:relation="Sales.SalesOrderDetail" type="DiscountType"/>  
  
  <xsd:complexType name="DiscountType">  
    <xsd:simpleContent>  
       <xsd:extension base="xsd:string">  
          <xsd:anyAttribute namespace="##other" processContents="lax"/>  
       </xsd:extension>  
    </xsd:simpleContent>  
  </xsd:complexType>  
  
  <xsd:element name="Contact" sql:relation="Person.Contact" type="ContactType"/>  
  
  <xsd:complexType name="ContactType">  
    <xsd:attribute name="ContactID"/>  
    <xsd:attribute name="LastName"/>  
    <xsd:attribute name="FirstName"/>  
    <xsd:attribute name="Title"/>  
  </xsd:complexType>  
  
</xsd:schema>  
```  
  
  
