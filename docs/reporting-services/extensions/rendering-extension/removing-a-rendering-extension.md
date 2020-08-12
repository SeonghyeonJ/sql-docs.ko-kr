---
title: 렌더링 확장 프로그램 제거 | Microsoft Docs
description: Reporting Services에서 렌더링 확장 프로그램을 제거하여 보고서 서버 및 보고서 디자이너에서 더 이상 사용할 수 없도록 하는 방법을 알아봅니다.
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: f71fceddd59141516453f9f392f8f913ba20cfad
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529439"
---
# <a name="removing-a-rendering-extension"></a>렌더링 확장 프로그램 제거
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 렌더링 확장 프로그램을 제거하려면 **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Instance Name>\Reporting Services\ReportServer** 폴더에 있는 rsreportserver.config 파일에서 렌더링 확장 프로그램의 **Extension** 요소를 제거하면 됩니다. 보고서 서버 및 보고서 디자이너에 대한 항목을 만든 경우에는 [RSReportDesigner 구성 파일](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md)에서도 **Extension** 요소를 제거합니다. 구성 정보를 제거한 후에는 구성 요소에서 렌더링 확장 프로그램을 사용할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Reporting Services 구성 파일](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [렌더링 확장 프로그램 구현](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [렌더링 확장 프로그램 개요](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [IRenderingExtension 인터페이스 구현](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [확장에 대한 보안 고려 사항](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [렌더링 확장 프로그램 배포](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
