---
title: XQuery의 형식 캐스팅 규칙 | Microsoft Docs
description: XQuery에서 한 데이터 형식에서 다른 데이터 형식으로 명시적 또는 암시적으로 캐스팅할 때 적용 되는 규칙에 대해 알아봅니다.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, type casting
- casting rules [XML in SQL Server]
- explicit casting [SQL Server]
- type casting rules [XML in SQL Server]
- cast as operator
- implicit casting
ms.assetid: f2e91306-2b1b-4e1c-b6d8-a34fb9980057
author: rothja
ms.author: jroth
ms.openlocfilehash: e7de4ccd0a7bba950767d9d9028e4635a10ee25d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759460"
---
# <a name="type-casting-rules-in-xquery"></a>XQuery의 캐스트 규칙
[!INCLUDE [SQL Server Azure SQL Database ](../includes/applies-to-version/sqlserver.md)]

  다음 W3C XQuery 1.0 및 XPath 2.0 함수 및 연산자 사양 다이어그램에서는 기본 제공 기본 유형 및 파생된 유형을 포함한 기본 제공 데이터 형식을 보여 줍니다.  
  
 ![XQuery 1.0 유형 계층](../xquery/media/xquery-typing-rules.gif "XQuery 1.0 유형 계층")  
  
 이 항목에서는 다음 중 한 가지 방법으로 유형 간 변환할 때 적용되는 캐스트 규칙에 대해 설명합니다.  
  
-   **Cast as** 또는 형식 생성자 함수 (예:)를 사용 하 여 수행 하는 명시적 캐스팅 `xs:integer("5")`  
  
-   유형 승격 중 발생하는 암시적 캐스트  
  
## <a name="explicit-casting"></a>명시적 캐스트  
 다음 표에서는 기본 제공 기본 유형 간에 허용되는 캐스트에 대한 개요를 보여 줍니다.  
  
 ![XQuery에 대한 캐스팅 규칙 설명](../xquery/media/casting-builtin-types.gif "XQuery에 대한 캐스팅 규칙 설명")  
  
-   표의 규칙에 따라 기본 제공 기본 유형 간에 캐스트가 가능합니다.  
  
-   기본 유형은 해당 기본 유형에서 파생된 모든 유형으로 캐스팅될 수 있습니다. 예를 들어 **xs: decimal** 에서 **xs: integer**로 캐스팅 하거나 **xs: decimal** 에서 **xs: long**으로 캐스팅할 수 있습니다.  
  
-   파생된 유형은 기본 제공 기본 유형에 이르기까지 유형 계층에서 상위에 있는 모든 유형으로 캐스팅될 수 있습니다. 예를 들어 **xs: token** 에서 **xs: normalizedstring에서는** 또는 **xs: string**으로 캐스팅할 수 있습니다.  
  
-   파생된 유형은 해당 기본 상위 유형이 대상 유형으로 캐스팅될 수 있는 경우 기본 유형으로 캐스팅될 수 있습니다. 예를 들어 xs: **decimal**, **xs: integer**의 기본 상위 항목이 xs: **string**으로 캐스팅 될 수 있기 때문에 **xs: integer**, 파생 형식을 **xs: string**, 기본 형식으로 캐스팅할 수 있습니다.  
  
-   파생된 유형은 원본 유형의 기본 상위 유형이 대상 유형의 기본 상위 유형으로 캐스팅될 경우 다른 파생된 유형으로 캐스팅될 수 있습니다. 예를 들어 xs: **decimal** 에서 xs: **string**으로 캐스팅 될 수 있기 때문에 xs **: integer** 에서 **xs: token**로 캐스팅할 수 있습니다.  
  
-   사용자 정의 유형을 기본 제공 유형으로 캐스팅하는 규칙은 기본 제공 유형에 대한 규칙과 같습니다. 예를 들어 **xs: integer** 형식에서 파생 된 **myinteger** 형식을 정의할 수 있습니다. 그런 다음 **Myinteger** 를 xs: **token**로 캐스팅할 수 있습니다. xs: **decimal** 은 xs: **string**으로 캐스팅 될 수 있습니다.  
  
 다음은 지원되지 않는 캐스트의 종류입니다.  
  
-   목록 유형과의 상호 캐스트는 허용되지 않습니다. 여기에는 사용자 정의 목록 형식과 **xs: IDREFS**, **xs: ENTITIES**및 **xs: NMTOKENS**와 같은 기본 제공 목록 형식이 모두 포함 됩니다.  
  
-   **Xs: QName** 으로의 캐스트는 지원 되지 않습니다.  
  
-   **xs: NOTATION** 및 전체 정렬 된 duration, **xdt: yearMonthDuration** 및 **xdt: daytimeduration**의 하위 유형이 지원 되지 않습니다. 따라서 이러한 유형과의 상호 캐스트는 지원되지 않습니다.  
  
 다음 예에서는 명시적 캐스트를 보여 줍니다.  
  
### <a name="example-a"></a>예 1  
 다음 예에서는 xml 유형 변수를 쿼리합니다. 이 쿼리는 xs:string으로 형식화된 단순 유형 값의 시퀀스를 반환합니다.  
  
```  
declare @x xml  
set @x = '<e>1</e><e>2</e>'  
select @x.query('/e[1] cast as xs:string?')  
go  
```  
  
### <a name="example-b"></a>예 2  
 다음 예에서는 형식화된 xml 변수를 쿼리합니다. 먼저 XML 스키마 컬렉션을 만든 다음 그 XML 스키마 컬렉션을 사용하여 형식화된 xml 변수를 만듭니다. 이 스키마에서는 해당 변수에 할당된 XML 인스턴스에 대한 형식화 정보를 제공합니다. 그러면 해당 변수에 대해 쿼리가 지정됩니다.  
  
```  
create xml schema collection myCollection as N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      <xs:element name="root">  
            <xs:complexType>  
                  <xs:sequence>  
                        <xs:element name="A" type="xs:string"/>  
                        <xs:element name="B" type="xs:string"/>  
                        <xs:element name="C" type="xs:string"/>  
                  </xs:sequence>  
            </xs:complexType>  
      </xs:element>  
</xs:schema>'  
go  
```  
  
 다음 쿼리는 `root` 문서 인스턴스에> 요소가 <최상위 수준 수를 알 수 없기 때문에 정적 오류를 반환 합니다.  
  
```  
declare @x xml(myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>  
          <root><A>4</A><B>5</B><C>6</baz></C>'  
select @x.query('/root/A cast as xs:string?')  
go  
```  
  
 식에 singleton <> 요소를 지정 하면 `root` 쿼리가 성공 합니다. 이 쿼리는 xs:string으로 형식화된 단순 유형 값의 시퀀스를 반환합니다.  
  
```  
declare @x xml(myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>  
              <root><A>4</A><B>5</B><C>6</C></root>'  
select @x.query('/root[1]/A cast as xs:string?')  
go  
```  
  
 다음 예에서 xml 유형 변수에는 XML 스키마 컬렉션을 지정하는 문서 키워드가 포함됩니다. 이는 XML 인스턴스가 단일 최상위 수준의 요소가 있는 문서여야 한다는 의미입니다. XML 인스턴스에서 두 개의 <`root`> 요소를 만들면 오류가 반환 됩니다.  
  
```  
declare @x xml(document myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>  
              <root><A>4</A><B>5</B><C>6</C></root>'  
go  
```  
  
 최상위 수준의 요소를 하나만 포함하도록 인스턴스를 변경하면 쿼리가 작동합니다. 이 쿼리는 xs:string으로 형식화된 단순 유형 값의 시퀀스를 다시 반환합니다.  
  
```  
declare @x xml(document myCollection)  
set @x = '<root><A>1</A><B>2</B><C>3</C></root>'  
select @x.query('/root/A cast as xs:string?')  
go  
```  
  
## <a name="implicit-casting"></a>암시적 캐스트  
 암시적 캐스트는 숫자 유형 및 형식화되지 않은 원자 유형에 대해서만 허용됩니다. 예를 들어 다음 **min ()** 함수는 두 값의 최소값을 반환 합니다.  
  
```  
min(xs:integer("1"), xs:double("1.1"))  
```  
  
 이 예에서는 XQuery **min ()** 함수에 전달 된 두 값의 형식이 서로 다릅니다. 따라서 **정수** 형식이 **double** 로 승격 되 고 두 **double** 값이 비교 되는 경우 암시적 변환이 수행 됩니다.  
  
 이 예에 설명된 대로 유형 승격은 다음 규칙을 따릅니다.  
  
-   기본 제공 파생된 숫자 유형은 기본 유형으로 승격될 수 있습니다. 예를 들어 **정수** 는 **decimal**로 승격 될 수 있습니다.  
  
-   **Decimal** 은 **float** 로 승격 될 수 있으며 **float** 는 **double**로 승격 될 수 있습니다.  
  
 암시적 캐스트는 숫자 유형에 대해서만 허용되므로 다음은 허용되지 않습니다.  
  
-   문자열 유형에 대한 암시적 캐스트는 허용되지 않습니다. 예를 들어 두 **문자열** 형식이 예상 되 고 **문자열과** **토큰**을 전달 하는 경우 암시적 캐스팅이 발생 하지 않으며 오류가 반환 됩니다.  
  
-   숫자 유형에서 문자열 유형으로 암시적 캐스팅하는 것은 허용되지 않습니다. 예를 들어 정수 유형 값을 문자열 유형 매개 변수를 예상하는 함수로 전달하는 경우 암시적 캐스트가 발생하지 않고 오류가 반환됩니다.  
  
## <a name="casting-values"></a>값 캐스팅  
 한 유형에서 다른 유형으로 캐스팅할 때 실제 값은 원본 유형의 값 공간에서 대상 유형의 값 공간으로 변환됩니다. 예를 들어 xs:decimal에서 xs:double로 캐스팅하면 decimal 값이 double 값으로 변환됩니다.  
  
 일부 변환 규칙은 다음과 같습니다.  
  
##### <a name="casting-a-value-from-a-string-or-untypedatomic-type"></a>문자열 또는 untypedAtomic 유형에서 값 캐스팅  
 문자열 또는 untypedAtomic 유형으로 캐스팅되는 값은 대상 유형의 규칙에 따라 값의 유효성을 검사하는 것과 같은 방법으로 변환됩니다. 여기에는 결과 패턴 및 공백 처리 규칙이 포함됩니다. 예를 들어 다음이 성공적으로 수행되고 double 값 1.1e0이 생성됩니다.  
  
 `xs:double("1.1")`  
  
 문자열 또는 untypedAtomic 유형에서 xs:base64Binary 또는 xs:hexBinary와 같은 이진 유형으로 캐스팅할 때 입력 값은 각각 Base64 또는 16진수 인코딩이어야 합니다.  
  
##### <a name="casting-a-value-to-a-string-or-untypedatomic-type"></a>문자열 또는 untypedAtomic 유형으로 값 캐스팅  
 문자열 또는 untypedAtomic 유형으로 캐스팅하면 값이 XQuery 정식 어휘 표현으로 변환됩니다. 이는 특히 입력 중 특정 패턴이나 기타 제약 조건에 맞는 값이 해당 제약 조건에 따라 표현되지 않음을 의미합니다.  이에 대 한 정보를 사용자에 게 알리기 위해 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 해당 형식이 스키마 컬렉션에 로드 될 때 경고를 제공 하 여 형식 제약 조건이 문제가 될 수 있는 형식에 플래그를 지정할 수 있습니다.  
  
 xs:float 유형 또는 xs:double 유형이나 그 하위 유형 중 하나의 값을 문자열 또는 untypedAtomic 유형으로 캐스팅할 때 해당 값은 과학적 표기법으로 표시됩니다. 이는 해당 값의 절대값이 1.0E-6 미만이거나 1.0E6 이상일 때만 수행됩니다. 즉, 과학적 표기법에 따라 0이 0.0E0으로 직렬화됩니다.  
  
 예를 들어 `xs:string(1.11e1)`은 문자열 값 `"11.1"`을 반환하지만 `xs:string(-0.00000000002e0)`은 문자열 값 `"-2.0E-11"`을 반환합니다.  
  
 xs:base64Binary 또는 xs:hexBinary와 같은 이진 유형을 문자열 또는 untypedAtomic 유형으로 캐스팅할 때 이진 값은 각각 Base64 또는 16진수 인코딩 형식으로 표현됩니다.  
  
##### <a name="casting-a-value-to-a-numeric-type"></a>숫자 유형으로 값 캐스팅  
 하나의 숫자 유형 값을 다른 숫자 유형 값으로 캐스팅할 때 값은 문자열 직렬화를 거치지 않고 하나의 값 공간에서 다른 값 공간으로 매핑됩니다. 이 값이 대상 유형의 제약 조건을 충족하지 않는 경우 다음 규칙이 적용됩니다.  
  
-   원본 값이 이미 숫자이고 대상 유형이 xs:float이거나 -INF 또는 INF 값을 허용하는 그 하위 유형이며 원본 숫자 값의 캐스트에 따라 오버플로가 발생하는 경우 해당 값이 양수일 때는 값이 INF로 매핑되고 해당 값이 음수일 때는 -INF로 매핑됩니다. 대상 유형에서 INF 또는 -INF를 허용하지 않고 오버플로가 발생하는 경우 캐스트는 실패하고 이 SQL Server 릴리스에서는 결과가 빈 시퀀스로 표시됩니다.  
  
-   원본 값이 이미 숫자이고 대상 유형이 승인된 값 범위 내에 0, -0e0 또는 0e0을 포함하는 숫자 유형이며 원본 숫자 값의 캐스트에 따라 언더플로가 발생하는 경우 해당 값은 다음 방식으로 매핑됩니다.  
  
    -   decimal 대상 유형의 경우 값이 0으로 매핑됩니다.  
  
    -   값이 음수 언더플로인 경우 -0e0으로 매핑됩니다.  
  
    -   값이 float 또는 double 대상 유형에 대한 양수 언더플로인 경우 0e0으로 매핑됩니다.  
  
     대상 유형의 값 공간에 0이 없는 경우 캐스트가 실패하고 빈 시퀀스가 나타납니다.  
  
     xs:float, xs:double 또는 이들의 하위 유형 중 하나와 같은 이진 부동 소수점 유형으로 값을 캐스팅하는 경우 전체 자릿수가 줄어들 수 있습니다.  
  
## <a name="implementation-limitations"></a>구현 시 제한 사항  
 제한 사항은 다음과 같습니다.  
  
-   부동 소수점 값 NaN은 지원되지 않습니다.  
  
-   캐스팅할 수 있는 값은 대상 유형 구현 제한 사항으로 제한됩니다. 예를 들어 음수 연도가 있는 날짜 문자열을 **xs: date**로 캐스팅할 수 없습니다. 이러한 캐스트는 런타임에 값이 제공될 경우 런타임 오류를 발생시키는 대신 빈 시퀀스를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [XML 데이터 직렬화 정의](../relational-databases/xml/define-the-serialization-of-xml-data.md)  
  
  
