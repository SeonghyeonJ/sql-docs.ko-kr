---
title: UDT(사용자 정의 데이터 형식)에 대한 FOR XML 지원 | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f6731d73830fe4f79525e05110920c6a3e6c2a1e
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509860"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>사용자 정의 데이터 형식(UDT)에 대한 FOR XML 지원
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  FOR XML은 CLR(공용 언어 런타임) UDT(사용자 정의 데이터 형식)를 지원하지 않습니다.  
  
 CLR 사용자 정의 데이터 형식으로 FOR XML을 사용하려면 데이터 형식에 XML 직렬화가 있는지 확인하고 FOR XML 선택 절의 XML로의 명시적 캐스트를 사용합니다.  
  
## <a name="see-also"></a>참고 항목  
 [다양한 SQL Server 데이터 형식에 대한 FOR XML 지원](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
