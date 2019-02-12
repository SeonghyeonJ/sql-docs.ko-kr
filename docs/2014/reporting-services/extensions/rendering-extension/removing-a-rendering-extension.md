---
title: 렌더링 확장 프로그램 제거 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5c8f55dd0fa663d5516938e9ca39b5a6dc2caed9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014634"
---
# <a name="removing-a-rendering-extension"></a>렌더링 확장 프로그램 제거
  제거할를 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 렌더링 확장 프로그램 제거 하기만 하면 합니다 `Extension` 요소에 있는 rsreportserver.config 파일에서 렌더링 확장 프로그램에 대해 **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< 인스턴스 이름 > \reporting** 폴더입니다. 보고서 서버 뿐만 아니라 보고서 디자이너에 대 한 항목을 만든 경우 제거 합니다 `Extension` 요소를 [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md) 도 합니다. 구성 정보를 제거한 후에는 구성 요소에서 렌더링 확장 프로그램을 사용할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Reporting Services 구성 파일](../../report-server/reporting-services-configuration-files.md)   
 [렌더링 확장 프로그램 구현](implementing-a-rendering-extension.md)   
 [렌더링 확장 프로그램 개요](rendering-extensions-overview.md)   
 [IRenderingExtension 인터페이스 구현](implementing-the-irenderingextension-interface.md)   
 [확장에 대한 보안 고려 사항](../security-considerations-for-extensions.md)   
 [렌더링 확장 프로그램 배포](deploying-a-rendering-extension.md)  
  
  
