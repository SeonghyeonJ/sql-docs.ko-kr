---
title: 사용자 지정 어셈블리 개체 초기화 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 97ee8e554fa246848b64ebafb0961f35d65f15c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63264717"
---
# <a name="initializing-custom-assembly-objects"></a>사용자 지정 어셈블리 개체 초기화
  사용자 지정 어셈블리 클래스를 인스턴스화할 때 속성 및 필드 값을 초기화해야 하는 경우가 있습니다. 대개 보고서의 전역 개체 컬렉션에서 제공되는 값으로 사용자 지정 클래스를 초기화해야 합니다. 이 작업은 보고서 **Code** 개체의 **OnInit** 메서드를 다시 정의하여 수행합니다. **OnInit**에 액세스하려면 보고서 정의의 **Code** 요소를 사용합니다. 초기화 속성 또는 보고서에 사용 하려는 사용자 지정 어셈블리의 클래스의 필드 값에 대 한 두 가지 기술이 있습니다. 선언 하 고 사용 하 여 클래스의 새 인스턴스를 만들거나 **OnInit**, 또는 사용 하 여 공개적으로 사용 가능한 메서드를 호출할 수 있습니다 **OnInit**합니다.  
  
## <a name="global-object-collections-and-initialization"></a>전역 개체 컬렉션 및 초기화  
 사용자 지정 클래스 변수를 초기화하는 데 사용할 수 있는 컬렉션이 다수 있으며, **Globals** 및 **User** 컬렉션을 사용할 수 있습니다. **Parameters**, **Fields** 및 **ReportItems** 컬렉션은 **OnInit** 메서드가 호출될 때 보고서 수명 주기의 시점에서 사용할 수 없습니다. 공유 컬렉션인 **Globals** 또는 **User**를 사용하려면 **Report** 개체 참조를 포함시켜야 합니다. 예를 들어, 보고서에 액세스하는 사용자의 현재 언어를 기반으로 사용자 지정 클래스를 초기화하려면 **Code** 요소가 다음과 같을 수 있습니다.  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 위에 제시한 대로 클래스의 속성 및 필드 값을 초기화하는 한 가지 방법은 다시 정의된 생성자를 호출하여 클래스를 선언하고 이 클래스의 새 인스턴스를 만드는 것입니다.  
  
 사용자 지정 어셈블리에서 클래스의 속성 및 필드 값을 초기화하는 또 하나의 방법은 **OnInit** 메서드에서 정의하는 공용으로 사용 가능한 메서드를 호출하는 것입니다. 먼저 보고서 정의 파일에서 클래스에 대한 인스턴스 이름을 추가해야 합니다. 올바른 어셈블리 참조 및 인스턴스 이름을 추가하고 나면 초기화 메서드를 호출하여 클래스에 대한 속성 및 필드 값을 초기화할 수 있습니다. **OnInit** 메서드는 다음과 같습니다.  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 사용자 지정 클래스의 어셈블리 참조 및 인스턴스 이름을 추가하는 방법은 [보고서에 어셈블리 참조 추가(&#40;SSRS&#41;)](../report-design/add-an-assembly-reference-to-a-report-ssrs.md)를 참조하세요.  
  
 전역 개체 컬렉션에 대한 자세한 내용은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [보고서에서 사용자 지정 어셈블리 사용](using-custom-assemblies-with-reports.md)  
  
  
