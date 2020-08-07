---
title: 법적 고 지 사항 (MySQLToSql) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: d514c622-2c0d-4f41-80d2-66add4d113b1
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: aaf9660b77e943e2350c2dc32c73f013ae68dde8
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935311"
---
# <a name="legal-notice-mysqltosql"></a>법적 고지 사항(MySQLToSql)
포함된 예제 애플리케이션을 포함하여 이 설명서는 정보 제공의 목적으로만 제공되며 Microsoft 및 그 공급자는 이 설명서에 대해서 어떠한 명시적이거나 묵시적인 보증도 하지 않습니다. URL 및 기타 인터넷 웹 사이트 참조를 포함하여, 이 설명서의 내용은 예고 없이 변경될 수 있습니다. 이 설명서의 사용이나 사용 결과에 따른 책임은 전적으로 사용자에게 있습니다.  
  
이 설명서에 포함된 예제는 주로 특정 문이나 절의 개념을 설명하거나 적당한 사용법을 보여 주기 위한 것입니다. 특정 개념이나 문에 대한 예제를 중점적으로 제공하기 위해 일반적인 데이터 유효성 검사 및 오류 처리의 일부가 제거되었으므로 대부분의 예제에 전체 프로덕션 시스템에서 일반적으로 찾을 수 있는 모든 코드가 포함되어 있지는 않습니다. 이러한 예제나 포함된 원본 코드에 대한 기술 지원은 받을 수 없습니다.  
  
다른 설명이 없는 한, 용례에 사용된 회사, 기관, 제품, 도메인 이름, 전자 메일 주소, 사람, 장소 및 이벤트 등은 실제 데이터가 아닙니다. 어떠한 실제 회사, 기관, 제품, 도메인 이름, 전자 메일 주소, 사람, 장소 또는 이벤트와도 연관시킬 의도가 없으며 그렇게 유추해서도 안 됩니다. 해당 저작권법을 준수하는 것은 사용자의 책임입니다. 저작권에서의 권리와는 별도로, 이 설명서의 어떠한 부분도 Microsoft의 명시적인 서면 승인 없이는 어떠한 형식이나 수단(전기적, 기계적, 복사기에 의한 복사, 디스크 복사 또는 다른 방법) 또는 목적으로도 복제되거나, 검색 시스템에 저장 또는 도입되거나, 전송될 수 없습니다.  
  
Microsoft가 이 설명서 본안에 관련된 특허권, 상표권, 저작권, 또는 기타 지적 재산권 등을 보유할 수도 있습니다. 서면 사용권 계약에 따라 Microsoft로부터 귀하에게 명시적으로 제공된 권리 이외에, 이 설명서의 제공은 귀하에게 이러한 특허권, 상표권, 저작권, 또는 기타 지적 재산권 등에 대한 어떠한 사용권도 허여하지 않습니다.  
  
© 2016 Microsoft Corporation. All rights reserved.  
  
Microsoft, Windows, Windows NT, Windows Server, Active Directory, ActiveX, BackOffice, bCentral, BizTalk, DirectX, Excel, Hotmail, IntelliSense, J/Direct, Jscript, Microsoft Press, MSDN, MS-DOS, Outlook, PivotChart, PivotTable, PowerPoint, SharePoint, SQL Server, Visual Basic, Visual C#, Visual C++, Visual FoxPro, Visual InterDev, Visual J#, Visual J++, Visual SourceSafe, Visual Studio, Win32, Win32s, Windows Mobile, Windows Server System 및 WinFX는 미국, 대한민국 및/또는 기타 국가에서의 Microsoft Corporation 등록 상표 또는 상표입니다.  
  
SAP NetWeaver는 독일 및 기타 여러 국가/지역에서 SAP AG의 등록 상표입니다.  
  
다른 모든 상표는 해당 소유자의 자산입니다.  
  
## <a name="documentation-policy-for-sql-server-support-and-upgrade"></a>SQL Server 지원 및 업그레이드에 대한 설명서 정책  
SQL Server 설명서의 콘텐츠는 충분한 테스트를 거친 후에만 게시됩니다. 제품 설명서-SQL Server 온라인 설명서, 추가 정보 파일, 알려진 문제점 문서 및 기술 자료 문서에는 모든 고객이 일반적으로 사용 하기에 안전 하 게 사용할 수 있는 강력한 기능 SQL Server 기능에 대 한 내용이 포함 되어 있습니다. 이 정책은 릴리스 및 서비스 팩에 대한 추가 정보 파일을 포함한 모든 SQL Server 설명서에 적용됩니다. 추가 정보 파일은 온라인 설명서의 확장으로 간주합니다.  
  
경우에 따라 특정 기능은 고객의 직접 사용이 금지되므로 문서화되지 않습니다. Microsoft에서 게시한 SQL Server 설명서에서도 해당 기능을 설명하는 경우 이외에는 타사 서적 또는 웹 사이트의 콘텐츠는 Microsoft 고객 지원에서 지원하지 않으므로 프로덕션 데이터베이스 또는 애플리케이션에 사용하지 않아야 합니다.  
  
고객은 저장 프로시저, 확장 저장 프로시저, 기능, 뷰, 테이블, 열, 속성 또는 메타데이터 등을 포함하여 문서화되지 않은 API를 사용하지 않아야 합니다. Microsoft 고객 지원에서는 문서화되지 않은 진입점을 활용 또는 사용하는 데이터베이스 또는 애플리케이션을 지원하지 않습니다.  
  
문서화되지 않은 진입점을 사용하는 애플리케이션 및 데이터베이스의 경우 SQL Server의 나중 버전으로 서버 및 데이터베이스를 업그레이드하지 못할 수 있습니다. SQL Server 기능의 사용은 Microsoft SQL Server 설명서에 포함된 기능으로 제한되어야 합니다. 기능이 Microsoft SQL Server 설명서에 문서화되어 있지 않은 경우는 SQL Server의 지원되는 부분이 아닙니다.  
  
