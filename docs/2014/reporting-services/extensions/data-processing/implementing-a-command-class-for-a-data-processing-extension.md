---
title: 데이터 처리 확장 프로그램에 대한 Command 클래스 구현 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f07b9beb798b1cd33ec2fee6af890a09a516b2f5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63163986"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>데이터 처리 확장 프로그램에 대한 Command 클래스 구현
  **Command** 개체는 요청을 작성하고 이를 데이터 원본에 전달합니다. 명령 텍스트는 텍스트 및 XML을 비롯하여 다양한 구문 형식을 취할 수 있습니다. 결과가 반환될 경우 **Command** 개체는 **DataReader** 개체 형태로 결과를 반환합니다.  
  
 **Command** 클래스를 만들려면 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>를 구현합니다. <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 메서드를 구현하여 결과 집합을 **DataReader** 개체 형태로 반환합니다. <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>Command**클래스의** 메서드에는 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> 열거를 인수로 사용하는 구현이 포함되어야 합니다. 데이터 처리 확장 프로그램을 보고서 디자이너에 배포할 경우 <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> 메서드에서 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 사례를 처리하는 구현을 제공합니다. 스키마 전용 구현은 보고서 디자이너에 필드 목록을 제공하는 데 사용됩니다. **메서드를 통해 반환된**DataReader<xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> 개체에는 결과 집합에서 필드 또는 열에 대한 유형 및 이름 정보가 포함되어야 합니다.  
  
 선택적으로 **Command** 클래스는 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>를 구현할 수 있습니다. 이 인터페이스를 통해 구현 클래스에서 쿼리를 분석하고 쿼리의 매개 변수 목록을 반환할 수 있습니다. <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> 인터페이스의 기능은 보고서 디자이너에서만 사용됩니다. <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>를 구현하면 보고서가 미리 보기 모드에서 실행될 때마다 보고서 디자이너 사용자로 하여금 매개 변수를 결정하도록 할 수 있습니다. 또한 **데이터 집합** 대화 상자의 **매개 변수** 탭에서 매개 변수를 볼 수 있습니다.  
  
> [!NOTE]  
>  사용자 지정 데이터 처리 확장 프로그램에서 매개 변수를 지원하지 않는 경우 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>를 구현하면 안 됩니다.  
  
 예제 **Command** 클래스 구현은 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services 확장 프로그램](../reporting-services-extensions.md)   
 [데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md)   
 [Reporting Services 확장 라이브러리](../reporting-services-extension-library.md)  
  
  
