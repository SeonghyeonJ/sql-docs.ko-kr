---
description: 데이터 원본에 연결
title: 데이터 원본에 연결 | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: rothja
ms.author: jroth
ms.openlocfilehash: 988eef3a3eb706480e50f0feb6d2fe363b4faabd
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991524"
---
# <a name="connecting-to-data-sources"></a>데이터 원본에 연결
ADO **연결** 개체는 DBMS, 파일 저장소 또는 쉼표로 구분 된 텍스트 파일을 포함 하 여 데이터 원본에 대 한 고유한 세션을 나타냅니다. 클라이언트/서버 데이터베이스 시스템의 경우 ADO 연결은 서버에 대 한 실제 네트워크 연결이 될 수 있습니다.  
  
 **Connection** 개체는 연결 구성 지정, 연결 열기 및 닫기, 데이터 원본에 대 한 명령 생성 및 실행, 스키마 행 집합 형식으로 기본 데이터 원본의 디자인에 대 한 정보 제공 등을 위한 다양 한 [속성 및 메서드](../../reference/ado-api/connection-object-properties-methods-and-events.md) 를 지원 합니다. 공급자가 지 원하는 기능에 따라 **연결** 개체의 일부 컬렉션, 메서드 또는 속성을 사용 하지 못할 수도 있습니다.  
  
 **연결** 개체를 사용 하거나 **레코드 집합** 개체를 사용 하 여 데이터 원본에 연결할 수 있습니다.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [연결 개체 사용](./using-a-connection-object.md)  
  
-   [레코드 집합 개체 사용](./using-a-recordset-object.md)  
  
-   [연결 문자열 만들기](./creating-a-connection-string.md)  
  
-   [연결 속성 지정](./specifying-connection-properties.md)  
  
-   [트랜잭션 제어](./controlling-transactions-ado.md)