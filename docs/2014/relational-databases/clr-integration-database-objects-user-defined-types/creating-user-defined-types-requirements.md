---
title: 사용자 정의 형식 요구 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 63f297f1a2a3ae738e00e37acf381b830ced9e7b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62919666"
---
# <a name="user-defined-type-requirements"></a>사용자 정의 형식 요구 사항
  사용자 정의 형식 (UDT)에 설치를 만들 때 몇 가지 중요 한 설계 결정을 내려야 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 대부분의 UDT는 구조로 만드는 것이 좋지만 클래스로 만드는 방법도 고려해 볼 수 있습니다. UDT 정의가 UDT 생성 사양에 맞아야만 UDT 정의를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 등록할 수 있습니다.  
  
## <a name="requirements-for-implementing-udts"></a>UDT 구현을 위한 요구 사항  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDT를 실행하려면 UDT 정의에서 다음 요구 사항을 구현해야 합니다.  
  
 UDT에서 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`를 지정해야 합니다. `System.SerializableAttribute`의 사용은 옵션이지만 사용하는 것이 좋습니다.  
  
-   UDT에서 공용 `System.Data.SqlTypes.INullable`([!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic의 경우 `static`) `Shared` 메서드를 만들어 클래스나 구조체에서 `Null` 인터페이스를 구현해야 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 기본적으로 Null을 인식합니다. 이 작업은 UDT를 실행하는 코드에서 Null 값을 인식할 수 있도록 하는 데 필요합니다.  
  
-   UDT가 개체의 문자열 표현으로부터의 구문 분석을 지원하는 공용 `static`(또는 `Shared`) `Parse` 메서드와 개체의 문자열 표현으로의 변환을 위한 공용 `ToString` 메서드를 포함해야 합니다.  
  
-   사용자 정의 직렬화 형식이 포함된 UDT는 `System.Data.IBinarySerialize` 인터페이스를 구현하고 `Read` 및 `Write` 메서드를 제공해야 합니다.  
  
-   UDT에서 `System.Xml.Serialization.IXmlSerializable`을 구현해야 합니다. 또는 표준 직렬화 재정의가 필요한 경우 모든 공용 필드 및 속성이 XML로 직렬화할 수 있는 형식이거나 `XmlIgnore` 특성으로 데코레이팅되어 있어야 합니다.  
  
-   UDT 개체의 직렬화가 하나만 있어야 합니다. 직렬화 또는 역직렬화 루틴에서 특정 개체의 표현을 두 개 이상 인식하면 유효성 검사가 실패합니다.  
  
-   바이트 순서로 데이터를 비교하려면 `SqlUserDefinedTypeAttribute.IsByteOrdered`가 `true`여야 합니다. IComparable 인터페이스가 구현되지 않으며 `SqlUserDefinedTypeAttribute.IsByteOrdered`가 `false`인 경우 바이트 순서 비교가 실패합니다.  
  
-   클래스에 정의된 UDT에는 인수를 사용하지 않는 공용 생성자가 있어야 합니다. 오버로드된 추가 클래스 생성자를 만들 수도 있습니다.  
  
-   UDT가 데이터 요소를 공용 필드나 속성 프로시저로 표시해야 합니다.  
  
-   공개 이름은 128 자 보다 길 수 없습니다 하며 준수 해야 합니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 정의 된 식별자에 대 한 명명 규칙 [데이터베이스 식별자](../databases/database-identifiers.md)합니다.  
  
-   `sql_variant` 열에는 UDT의 인스턴스를 포함할 수 없습니다.  
  
-   상속된 멤버는 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 액세스할 수 없습니다. 그 이유는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 유형 시스템에서 UDT 간의 상속 계층을 인식하지 못하기 때문입니다. 그러나 클래스를 구성할 때는 상속을 사용할 수 있으며 관리 코드를 사용한 형식 구현에서 이러한 메서드를 호출할 수 있습니다.  
  
-   클래스 생성자를 제외하고는 멤버를 오버로드할 수 없습니다. 오버로드된 메서드를 만드는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 어셈블리를 등록하거나 형식을 만들 때는 오류가 발생하지 않습니다. 오버로드된 메서드는 형식이 만들어질 때가 아니라 런타임에 검색됩니다. 오버로드된 메서드를 호출하지 않는 한 오버로드된 메서드가 클래스 내에 존재할 수 있으며, 오버로드된 메서드를 호출하면 오류가 발생합니다.  
  
-   `static`(또는 `Shared`) 멤버는 상수나 읽기 전용으로 선언해야 합니다. 정적 멤버는 변경할 수 없습니다.  
  
-   `SqlUserDefinedTypeAttribute.MaxByteSize` 필드를 -1로 설정하면 직렬화된 UDT의 크기가 LOB(Large Object) 크기 제한(현재는 2GB)까지 커질 수 있습니다. UDT 크기는 `MaxByteSized` 필드에 지정된 값을 초과할 수 없습니다.  
  
> [!NOTE]  
>  서버에서 비교 작업에 사용하지는 않지만 단일 메서드 `System.IComparable`를 노출하는 `CompareTo` 인터페이스를 구현할 수도 있습니다. 이 인터페이스는 UDT 값을 정확하게 비교하거나 정렬해야 하는 경우에 클라이언트 쪽에서 사용됩니다.  
  
## <a name="native-serialization"></a>네이티브 직렬화  
 만들려는 UDT의 종류에 따라 UDT에 적합한 직렬화 특성을 선택해야 합니다. `Native` 직렬화 형식은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDT에 대한 효율적인 네이티브 표현을 디스크에 저장할 수 있게 하는 매우 간단한 구조를 사용합니다. `Native` 형식은 UDT가 간단하며 다음 유형의 필드만 포함하는 경우에 사용하는 것이 좋습니다.  
  
 **bool**, **byte**, **sbyte**, **short**, **ushort**, **int**, **uint**, **long**, **ulong**, **float**, **double**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 위 형식의 필드의 구성 된 값 형식에 적합 `Native` 형식으로 `structs` Visual C#에서는 (또는 `Structures` Visual basic에서으로). 예를 들어 `Native` 직렬화 형식을 사용하여 지정한 UDT에 마찬가지로 `Native` 형식을 사용하여 지정한 다른 UDT 필드가 포함될 수 있습니다. UDT 정의가 이보다 복잡하며 위 목록에 없는 데이터 형식을 포함할 경우 대신 `UserDefined` 직렬화 형식을 지정해야 합니다.  
  
 `Native` 형식은 다음 요구 사항을 충족해야 합니다.  
  
-   형식에서 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.MaxByteSize` 값을 지정하면 안 됩니다.  
  
-   모든 필드를 직렬화할 수 있어야 합니다.  
  
-   UDT가 구조체가 아니라 클래스에 정의되어 있으면 `System.Runtime.InteropServices.StructLayoutAttribute`는 `StructLayout.LayoutKindSequential`로 지정해야 합니다. 이 특성은 데이터 필드의 물리적 레이아웃을 제어하며 멤버를 멤버가 실제로 나타나는 순서대로 배치하는 데 사용됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 특성을 사용하여 값이 여러 개 포함된 UDT의 필드 순서를 결정합니다.  
  
 사용 하 여 정의 된 UDT의 예 `Native` serialization에서 Point UDT를 참조 하세요 [코딩 형식](creating-user-defined-types-coding.md)합니다.  
  
## <a name="userdefined-serialization"></a>UserDefined 직렬화  
 `UserDefined` 특성에 대한 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 형식 설정을 통해 개발자는 이진 형식을 완전히 제어할 수 있습니다. `Format` 특성의 속성을 `UserDefined`로 지정할 경우 코드에서 다음 작업을 수행해야 합니다.  
  
-   선택적 요소인 `IsByteOrdered` 특성의 속성을 지정합니다. 기본값은 `false`입니다.  
  
-   `MaxByteSize`의 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 속성을 지정합니다.  
  
-   `Read` 인터페이스를 구현하여 UDT에 대한 `Write` 및 `System.Data.Sql.IBinarySerialize` 메서드를 구현하는 코드를 작성합니다.  
  
 사용 하 여 정의 된 UDT의 예 `UserDefined` serialization에서 Currency UDT를 참조 하세요 [코딩 형식](creating-user-defined-types-coding.md)합니다.  
  
> [!NOTE]  
>  UDT 필드를 인덱싱하려면 UDT 필드에 네이티브 직렬화를 사용하거나 필드를 지속형 필드로 만들어야 합니다.  
  
## <a name="serialization-attributes"></a>직렬화 특성  
 특성은 직렬화를 사용하여 UDT의 저장소 표현을 생성하고 UDT를 값으로 클라이언트에 전송하는 방법을 결정합니다. UDT를 만들 때 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`를 지정해야 합니다. `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute` 특성은 클래스가 UDT임을 나타내며 UDT에 대한 저장소를 지정합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 요구 사항은 아니지만 `Serializable` 특성을 지정할 수도 있습니다.  
  
 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute`에는 다음 속성이 있습니다.  
  
 `Format`  
 직렬화 형식을 지정합니다. 직렬화 형식은 UDT의 데이터 형식에 따라 `Native` 또는 `UserDefined`가 될 수 있습니다.  
  
 `IsByteOrdered`  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 UDT에 대한 이진 비교를 수행하는 방법을 결정하는 `Boolean` 값입니다.  
  
 `IsFixedLength`  
 이 UDT의 모든 인스턴스 길이가 같은지 여부를 나타냅니다.  
  
 `MaxByteSize`  
 (바이트)에서 인스턴스의 최대 크기입니다. `MaxByteSize` 직렬화 형식과 함께 `UserDefined`를 지정해야 합니다. 를 지정 하는 사용자 정의 직렬화 된 udt `MaxByteSize` 사용자가 정의 된 대로 serialize 된 형식에서 UDT의 총 크기를 나타냅니다. `MaxByteSize` 값은 1에서 8000 사이의 값이어야 합니다. UDT가 8000바이트보다 크다는 것을 나타내려면 이 값을 -1로 설정해야 하며 총 크기는 최대 LOB 크기를 초과할 수 없습니다. 10 자 문자열의 속성을 사용 하 여 UDT는 것이 좋습니다 (`System.Char`). UDT BinaryWriter를 사용 하 여 serialize 되 면 serialize 된 문자열의 총 크기는 22 바이트: 유니코드 utf-16 문자당 2 바이트를 곱한 자와 2 컨트롤의 최대 바이트의 오버 헤드를 이진 스트림으로 직렬화 하는 작업에서 발생 합니다. 따라서 `MaxByteSize`의 값을 결정할 때 직렬화된 UDT의 전체 크기를 고려해야 합니다. 이 크기는 이진 형식으로 직렬화된 데이터의 크기와 직렬화로 인해 발생한 오버헤드를 합한 것입니다.  
  
 `ValidationMethodName`  
 UDT의 인스턴스가 유효한지 여부를 검사하는 데 사용되는 메서드의 이름입니다.  
  
### <a name="setting-isbyteordered"></a>IsByteOrdered 설정  
 `Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.IsByteOrdered` 속성을 `true`로 설정하면 이는 직렬화된 이진 데이터가 정보의 의미 정렬(semantic ordering)에 사용될 수 있도록 보장하는 것과 같습니다. 따라서 바이트 정렬 UDT 개체의 각 인스턴스는 직렬화 된 표현이 하나만 사용할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 직렬화된 바이트에 대한 비교 작업이 수행되면 그 결과는 동일한 비교 작업이 관리 코드에서 수행된 결과와 같아야 합니다. `IsByteOrdered`가 `true`로 설정된 경우 다음 기능도 지원됩니다.  
  
-   이 형식의 열에 인덱스를 만들 수 있습니다.  
  
-   이 형식의 열에 CHECK 및 UNIQUE 제약 조건 뿐만 아니라 기본 및 외래 키를 만들 수 있습니다.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ORDER BY, GROUP BY 및 PARTITION BY 절을 사용하는 기능. 이러한 경우 종류의 이진 순서를 결정 하려면 사용 됩니다.  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 비교 연산자를 사용하는 기능  
  
-   이 형식의 계산된 열을 유지할 수 있습니다.  
  
 모두를 `Native` 및 `UserDefined` 직렬화 형식은 다음 비교 연산자를 지원 하면 `IsByteOrdered` 로 설정 된 `true`:  
  
-   같음 (=)  
  
-   같지 않음(!=)  
  
-   보다 큼(>)  
  
-   보다 작은 (\<)  
  
-   크거나 같음(>=)  
  
-   작거나 같음(<=)  
  
### <a name="implementing-nullability"></a>Null 허용 여부 구현  
 어셈블리의 특성을 올바르게 지정하는 것 외에도 클래스는 Null 허용 여부를 지원해야 합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 로드된 UDT는 Null을 인식하지만 UDT에서 Null 값을 인식하려면 클래스에서 `INullable` 인터페이스를 구현해야 합니다. 자세한 내용 및 UDT에서 null 허용 여부를 구현 하는 방법의 예제를 참조 하세요 [코딩 형식](creating-user-defined-types-coding.md)합니다.  
  
### <a name="string-conversions"></a>문자열 변환  
 UDT에서 문자열로의 변환 또는 문자열에서 UDT로의 변환을 지원하려면 클래스에서 `Parse` 메서드와 `ToString` 메서드를 제공해야 합니다. `Parse` 메서드는 문자열을 UDT로 변환할 수 있게 하며, `static`(Visual Basic의 경우 `Shared`)으로 선언되고 `System.Data.SqlTypes.SqlString` 유형의 매개 변수를 사용해야 합니다. 자세한 내용 및 구현 하는 방법의 예는 `Parse` 하 고 `ToString` 메서드를 참조 하세요 [코딩 형식](creating-user-defined-types-coding.md)합니다.  
  
## <a name="xml-serialization"></a>XML 직렬화  
 UDT는 XML 직렬화 계약에 따라 UDT에서 `xml` 데이터 형식으로의 변환 또는 xml 데이터 형식에서 UDT로의 변환을 지원해야 합니다. `System.Xml.Serialization` 네임 스페이스에 개체를 XML 형식 문서 또는 스트림으로 serialize 하는 데 사용 되는 클래스가 포함 되어 있습니다. XML 직렬화 및 역직렬화를 위한 사용자 지정 형식을 제공하는 `xml` 인터페이스를 사용하여 `IXmlSerializable` 직렬화를 구현할 수 있습니다.  
  
 XML 직렬화를 사용하면 UDT에서 `xml`로의 명시적 변환 외에도 다음과 같은 작업이 가능합니다.  
  
-   `Xquery` 데이터 형식으로의 변환 후 UDT 인스턴스 값에 대해 `xml`를 사용합니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 네이티브 XML 웹 서비스를 사용하여 매개 변수가 있는 쿼리 및 웹 메서드에서 UDT를 사용합니다.  
  
-   UDT를 사용하여 대량 로드된 XML 데이터를 받습니다.  
  
-   UDT 열이 있는 테이블이 포함된 데이터 집합을 직렬화합니다.  
  
 FOR XML 쿼리에서는 UDT가 직렬화되지 않습니다. UDT에 대한 XML 직렬화를 표시하는 FOR XML 쿼리를 실행하려면 SELECT 문에서 각 UDT 열을 `xml` 데이터 형식으로 명시적으로 변환합니다. UDT 열을 `varbinary`, `varchar` 또는 `nvarchar`로 명시적으로 변환할 수도 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [사용자 정의 형식 만들기](creating-user-defined-types.md)  
  
  
