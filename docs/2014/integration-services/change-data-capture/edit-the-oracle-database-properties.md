---
title: Oracle 데이터베이스 속성 편집 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraProp
ms.assetid: 58dc99f1-ee6b-4508-bb66-2bc589611ff7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cfc119c031f0eeb84317cd1bcd8250f8ab803b6b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52770865"
---
# <a name="edit-the-oracle-database-properties"></a>Oracle 데이터베이스 속성 편집
  속성 편집기에서 Oracle 탭을 사용하여 새 인스턴스 마법사의 CDC 데이터베이스 만들기 페이지에 제공한 설명을 변경하고 Oracle 로그 마이닝 데이터베이스 연결 정보를 변경할 수 있습니다.  
  
 다음 표에서는 **Oracle** 탭에 표시되는 정보를 설명합니다.  
  
 **이름**  
 새 인스턴스 마법사의 CDC 데이터베이스 만들기 페이지에 입력한 CDC 인스턴스의 이름입니다. 이 필드는 읽기 전용이므로 이 정보를 편집할 수 없습니다.  
  
 **설명**  
 CDC 인스턴스를 만들 때 새 인스턴스에 대한 설명을 편집하거나 추가하지 않은 경우 설명을 편집하거나 추가할 수 있습니다.  
  
 **Oracle 연결 문자열**  
 사용 중인 Oracle 데이터베이스가 있는 컴퓨터에 대한 Oracle 연결 문자열입니다. 이 필드는 읽기 전용이므로 이 정보를 편집할 수 없습니다. 연결 문자열을 변경하면 **cdc.xdbcdc_config** 테이블에 저장된 CDC 인스턴스 상태가 손상되어 Oracle CDC 인스턴스가 완전히 다른 Oracle 데이터베이스를 가리킬 수 있습니다. 약간의 변경이 필요한 경우 SQL Server Management Studio를 사용하여 구성 테이블에서 연결 문자열을 직접 변경할 수 있습니다.  
  
 **Oracle 로그 마이닝 인증**  
 로그 마이너를 포함하는 Oracle 데이터베이스에 대한 인증 자격 증명을 입력하려면 **인증**에서 다음 중 하나를 선택합니다.  
  
-   **Windows 인증**: 현재 Windows 도메인 자격 증명을 사용하려면 선택합니다. Windows 인증을 사용하도록 Oracle 데이터베이스를 구성한 경우에만 이 옵션을 사용할 수 있습니다.  
  
-   **Oracle 인증**: 이 옵션을 선택 하는 경우 입력 해야 합니다 **사용자 이름** 및 **암호** 에 연결 하는 Oracle 데이터베이스에서 사용자에 대 한 합니다.  
  
 뷰어에서 Oracle 데이터베이스 속성을 볼 수 있습니다. 뷰어를 사용할 때 정보는 읽기 전용입니다. 또한 뷰어에는 테이블에서 캡처된 열 목록이 포함되어 있습니다. 뷰어에 액세스하는 방법은 [How to Manage a CDC Instance](manage-a-cdc-instance.md)을 참조하십시오.  
  
## <a name="see-also"></a>관련 항목:  
 [CDC Designer 콘솔에서 CDC Service를 관리하는 방법](how-to-manage-a-cdc-service-from-the-cdc-designer-console.md)   
 [Oracle 원본 데이터베이스에 연결](connect-to-an-oracle-source-database.md)   
 [Oracle에 연결](connect-to-oracle.md)  
  
  
