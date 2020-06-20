---
title: 서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- identifiers [XML schema collections]
- XML schema collections [SQL Server], limitations
- substitution groups [XML in SQL Server]
- XML schema collections [SQL Server], guidelines
- lax validation
- enumeration facets [XML in SQL Server]
- decimal precision [XML in SQL Server]
- repeated XML schema collection values
- schema collections [SQL Server], limitations
- time zones [XML in SQL Server]
- precision decimals [XML in SQL Server]
- schema collections [SQL Server], guidelines
- lexical representation
ms.assetid: c2314fd5-4c6d-40cb-a128-07e532b40946
author: rothja
ms.author: jroth
ms.openlocfilehash: 41e27204bf472d905f420d665c206b840582e8de
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065489"
---
# <a name="requirements-and-limitations-for-xml-schema-collections-on-the-server"></a>서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항
  XSD(XML 스키마 정의 언어) 유효성 검사에는 `xml` 데이터 형식을 사용하는 SQL 열에 대한 몇 가지 제한 사항이 있습니다. 다음 표에서는 이러한 제한 사항과 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 작동할 수 있도록 XSD 스키마를 수정하는 지침을 제공합니다. 이 섹션의 다음 항목에서는 특정 제한 사항 및 이에 따른 작업 수행 지침에 대한 추가 정보를 제공합니다.  
  
|항목|제한 사항|  
|----------|----------------|  
|**minOccurs** 및 **maxOccurs**|**minOccurs** 및 **maxOccurs** 특성 값은 4바이트 정수로 구성해야 합니다. 이러한 형식을 따르지 않는 스키마는 서버에서 거부됩니다.|  
|**\<xsd:choice>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**\<xsd:choice>** 는 **minOccurs** 특성 값이 0 인 파티클을 정의 하지 않으면 자식이 없는 파티클을 포함 하는 스키마를 거부 합니다.|  
|**\<xsd:include>**|현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 이 요소를 지원하지 않습니다. 이 요소를 포함하는 XML 스키마는 서버에서 거부됩니다.<br /><br /> 솔루션으로, 지시문을 포함 하는 XML 스키마를 **\<xsd:include>** 전처리 하 여 포함 된 모든 스키마의 내용을 서버에 업로드할 단일 스키마로 복사 하 고 병합할 수 있습니다. 자세한 내용은 [포함된 스키마를 병합하기 위해 스키마 전처리](preprocess-a-schema-to-merge-included-schemas.md)를 참조하세요.|  
|**\<xsd:key>**, **\<xsd:keyref>** 및 **\<xsd:unique>**|현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 고유성을 적용하거나 키 및 키 참조를 설정하는 이러한 XSD 기반 제약 조건을 지원하지 않습니다. 이러한 요소를 포함하고 있는 XML 스키마는 등록할 수 없습니다.|  
|**\<xsd:redefine>**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 이 요소를 지원하지 않습니다. 스키마를 업데이트하는 다른 방법은 [&#60;xsd:redefine&#62; 요소](the-xsd-redefine-element.md)에서 작동할 수 있도록 XSD 스키마를 수정하는 지침을 제공합니다.|  
|**\<xsd:simpleType>** 값인|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 `xs:time` 및 `xs:dateTime`이 아닌 두 번째 구성 요소가 있는 단순 유형에 대해 밀리초 정밀도만 지원하며 `xs:time` 및 `xs:dateTime`에 대해서는 100나노초 정밀도만 지원합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 인식된 모든 XSD 단순 유형 열거를 제한합니다.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 선언에 "NaN" 값을 사용 하는 것을 지원 하지 않습니다 **\<xsd:simpleType>** .<br /><br /> 자세한 내용은[&#60;xsd:simpleType&#62; 선언의 값](values-for-xsd-simpletype-declarations.md)에서 작동할 수 있도록 XSD 스키마를 수정하는 지침을 제공합니다.|  
|**xsi:schemaLocation** 및 **xsi:noNamespaceSchemaLocation**|`xml` 데이터 형식의 열 또는 변수에 삽입된 XML 인스턴스 데이터에 이러한 특성이 존재할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 특성을 무시합니다.|  
|**xs: QName**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 XML 스키마 제한 요소를 사용 하는 **xs: QName** 에서 파생 된 형식을 지원 하지 않습니다.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 **xs: QName** 을 멤버 요소로 사용 하는 공용 구조체 형식을 지원 하지 않습니다.<br /><br /> 자세한 내용은 [The xs:QName Type](the-xs-qname-type.md)을 참조하세요.|  
|기존 대체 그룹에 멤버 추가|XML 스키마 컬렉션에서는 기존 대체 그룹에 멤버를 추가할 수 없습니다. XML 스키마의 대체 그룹은 머리글 요소와 이 요소의 모든 멤버 요소를 같은 {CREATE &#124; ALTER} XML SCHEMA COLLECTION 문에서 정의해야 한다는 점에서 제한적입니다.|  
|정규 형식 및 패턴 제한 사항|값의 정식 표현은 해당 형식의 패턴 제한 사항을 위반할 수 없습니다. 자세한 내용은 [Canonical Forms and Pattern Restrictions](canonical-forms-and-pattern-restrictions.md)을 참조하세요.|  
|열거 패싯|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 패턴 패싯 형식이나 이러한 패싯을 위반하는 열거형의 XML 스키마를 지원하지 않습니다.|  
|패싯 길이|**Length**, **minLength**및 **maxLength** 패싯은 형식으로 저장 됩니다 `long` . 이 형식은 32비트 형식입니다. 따라서 이러한 값에 허용 되는 값 범위는 2 <sup>^</sup> 31입니다.|  
|ID 특성|각 XML 스키마 구성 요소마다 ID 특성이 하나씩 있을 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 **\<xsd:attribute>** **ID** 형식의 선언에 고유성을 적용 하지만 이러한 값을 저장 하지는 않습니다. 고유성을 적용할 범위는 {CREATE &#124; ALTER} XML SCHEMA COLLECTION 문입니다.|  
|ID 형식|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 **xs: ID**, **xs: IDREF**또는 **xs: IDREFS**형식의 요소를 지원 하지 않습니다. 스키마는 이 유형의 요소나 이 유형의 제한 또는 확장에 의해 파생된 요소를 선언하지 않을 수 있습니다.|  
|로컬 네임스페이스|요소에 대해 로컬 네임 스페이스를 명시적으로 지정 해야 합니다 **\<xsd:any>** . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 빈 문자열("")을 네임스페이스 특성 값으로 사용하는 스키마를 거부합니다. 대신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 은 "##local"을 명시적으로 사용하여 비정규화된 요소 또는 특성을 와일드카드 문자의 인스턴스로 표시해야 합니다.|  
|혼합 형식 및 단순 내용|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 혼합 형식을 단순 내용으로 제한할 수 없습니다. 자세한 내용은 [Mixed Type and Simple Content](mixed-type-and-simple-content.md)을 참조하세요.|  
|NOTATION 형식|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 NOTATION 형식을 지원하지 않습니다.|  
|메모리 부족 상태|대형 XML 스키마 컬렉션을 사용할 경우 메모리가 부족해질 수 있습니다. 이 문제에 대한 해결 방법은 [대형 XML 스키마 컬렉션 및 메모리 부족 상태](large-xml-schema-collections-and-out-of-memory-conditions.md)를 참조하세요.|  
|반복 값|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 block 또는 final 특성에 "restriction restriction" 및 "extension extension" 같은 반복되는 값이 있는 스키마를 거부합니다.|  
|스키마 구성 요소 식별자|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 스키마 구성 요소 식별자의 최대 길이를 1000자(유니코드)로 제한합니다. 또한 식별자 내에 서로게이트 문자 쌍을 사용할 수 없습니다.|  
|표준 시간대 정보|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서 표준 시간대 정보는 XML 스키마 유효성 검사를 위한 `xs:date`, `xs:time` 및 `xs:dateTime` 값에 대해 완벽하게 지원됩니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 이전 버전과의 호환성 모드를 사용하면 표준 시간대 정보는 항상 Coordinated Universal Time(그리니치 표준시)로 표준화됩니다. `dateTime` 형식 요소의 경우 서버는 오프셋 값("-05:00")을 사용하고 해당 GMT 시간을 반환하여 제공되는 시간을 GMT로 변환합니다.|  
|공용 구조체 유형|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 공용 구조체 유형의 제한 사항을 지원하지 않습니다.|  
|가변 정밀도 10진수|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 가변 정밀도 10진수를 지원하지 않습니다. **xs:decimal** 형식은 임의 자릿수의 10진수를 나타냅니다. 최소로 준수하는 XML 프로세서는 최소값이 `totalDigits=18`인 10진수를 지원해야 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 `totalDigits=38,` 을 지원하지만 소수 자릿수를 10으로 제한합니다. 서버에서는 모든 **xs:decimal** 의 인스턴스화된 값을 내부적으로 SQL 유형 숫자(38, 10)를 사용하여 나타냅니다.|  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[정규 형식 및 패턴 제한 사항](canonical-forms-and-pattern-restrictions.md)|정규 형식 및 패턴 제한 사항을 설명합니다.|  
|[와일드카드 구성 요소 및 콘텐츠 유효성 검사](wildcard-components-and-content-validation.md)|와일드카드 문자, lax 유효성 검사 및 anyType 요소를 XML 스키마 컬렉션과 함께 사용할 경우 제한 사항을 설명합니다.|  
|[&#60;xsd:redefine&#62; 요소](the-xsd-redefine-element.md)|요소 사용에 대 한 제한 사항을 설명 하 \<xsd:redefine> 고 해결 방법을 설명 합니다.|  
|[The xs:QName Type](the-xs-qname-type.md)|xs:QName 유형에 대한 제한 사항을 설명합니다.|  
|[&#60;xsd:simpleType&#62; 선언의 값](values-for-xsd-simpletype-declarations.md)|선언에 적용 되는 제한 사항에 대해 설명 합니다 \<xsd:simpleType> .|  
|[열거 패싯](enumeration-facets.md)|열거 패싯에 대한 제한 사항을 설명합니다.|  
|[혼합 형식 및 단순 내용](mixed-type-and-simple-content.md)|혼합 형식을 단순 내용으로 제한하는 제한 사항을 설명합니다.|  
|[대형 XML 스키마 컬렉션 및 메모리 부족 상태](large-xml-schema-collections-and-out-of-memory-conditions.md)|대형 스키마 컬렉션을 사용할 경우 가끔 발생하는 메모리 부족 상태에 대한 해결 방법을 설명합니다.|  
|[비결 정적 콘텐츠 모델](non-deterministic-content-models.md)|비결정적 콘텐츠 모델에 대한 제한 사항을 설명합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [XML 데이터 &#40;SQL Server&#41;](xml-data-sql-server.md)   
 [형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md)   
 [XML 스키마 컬렉션에 대 한 사용 권한 부여](grant-permissions-on-an-xml-schema-collection.md)   
 [고유한 파티클 특성 제약 조건](unique-particle-attribution-constraint.md)   
 [XML 스키마 컬렉션&#40;SQL Server&#41;](xml-schema-collections-sql-server.md)  
  
  
