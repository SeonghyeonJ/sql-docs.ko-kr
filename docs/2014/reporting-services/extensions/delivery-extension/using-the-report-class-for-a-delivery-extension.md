---
title: 배달 확장 프로그램에 대해 Report 클래스 사용 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], report information
- Report class
ms.assetid: 1145ac63-eafd-452a-82af-16f85b1676dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a3f750c2383253636db255cbe9f1ce0ee676a9d9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63163967"
---
# <a name="using-the-report-class-for-a-delivery-extension"></a>배달 확장 프로그램에 대해 Report 클래스 사용
  <xref:Microsoft.ReportingServices.Interfaces.Report> 클래스는 보고서 서버 데이터베이스의 보고서를 나타냅니다. 구독은 특정 보고서와 연결됩니다. 보고서는 알림에 포함됩니다. 배달 확장 프로그램에서는 알림의 일부인 <xref:Microsoft.ReportingServices.Interfaces.Report> 개체를 사용하여 보고서를 렌더링합니다. <xref:Microsoft.ReportingServices.Interfaces.Report> 개체에는 보고서 이름 및 보고서 서버의 보고서 URL과 같은 보고서별 속성도 포함됩니다. 이러한 속성은 모두 배달 공급자의 일부로 사용됩니다.  
  
 <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 클래스의 <xref:Microsoft.ReportingServices.Interfaces.Report> 메서드는 보고서를 렌더링하는 데 사용할 수 있습니다. <xref:Microsoft.ReportingServices.Interfaces.Report.Render%2A> 메서드는 렌더링된 단일 보고서를 구성하는 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체 배열을 하나 이상 반환합니다. 첫 번째 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 렌더링된 보고서입니다. 다른 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 보고서 데이터(예: HTML 파일 및 연결된 이미지)와 함께 배달되어야 하는 리소스입니다. 단일 스트림 렌더링 확장 프로그램(IMAGE, PDF, MHTML 및 Excel)은 배열의 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체 중 하나만 반환합니다.  
  
 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> 개체는 보고서 스트림을 포함하며 배달의 일부가 될 수 있습니다.  
  
 <xref:Microsoft.ReportingServices.Interfaces.Report> 클래스 사용 방법에 대한 예는 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [배달 확장 프로그램 구현](implementing-a-delivery-extension.md)   
 [Reporting Services 확장 라이브러리](../reporting-services-extension-library.md)   
 [배달 확장 프로그램에 대해 RenderedOutputFile 클래스 사용](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
  
  
