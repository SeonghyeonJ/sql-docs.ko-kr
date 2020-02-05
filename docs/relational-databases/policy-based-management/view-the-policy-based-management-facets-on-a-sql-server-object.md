---
title: 개체의 정책 기반 관리 패싯 보기
description: SSMS(SQL Server Management Studio)에서 특정 SQL Server 개체에 적용된 정책 기반 관리 팩트를 모두 보는 방법을 설명합니다.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, view facets
ms.assetid: 5f423b9f-a6c4-41a7-9d8d-8f4926ce1fb4
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 9284388a56014084b2478d6d805ff3fc917459d1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558120"
---
# <a name="view-policy-based-management-facets-on-a-sql-server-object"></a>SQL Server 개체의 정책 기반 관리 패싯 보기
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 특정 SQL Server 개체에 적용되는 모든 정책 기반 관리 패싯을 보는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [보안](#Security)  
  
-   **다음을 사용하여 개체의 모든 패싯을 보려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 권한  
 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-view-all-of-the-facets-in-an-object"></a>개체의 모든 패싯을 보려면  
  
1.  개체 탐색기에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체를 마우스 오른쪽 단추로 클릭한 다음 **패싯**을 클릭합니다.  
  
2.  **패싯 보기 –** _object_name_ 대화 상자의 **패싯** 목록에서 해당 속성을 보려면 패싯을 선택합니다. 이 대화 상자에서 사용할 수 있는 옵션에 대한 자세한 내용은 [View Facets Dialog Box](../../relational-databases/policy-based-management/view-facets-dialog-box.md)를 참조하세요.  
  
3.  완료되었으면 **확인**을 클릭합니다.  
  
  
