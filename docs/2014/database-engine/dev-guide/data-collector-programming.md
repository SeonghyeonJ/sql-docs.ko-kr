---
title: 데이터 수집기 프로그래밍 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- data collector [SQL Server], programming
ms.assetid: 53b4752b-055d-4716-b2bc-75b4cce84101
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 889158e04cbadb63c712ead73a61a7002ea61eae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175372"
---
# <a name="data-collector-programming"></a>데이터 수집기 프로그래밍
  <xref:Microsoft.SqlServer.Management.Collector>에서 데이터 수집기 API를 사용하면 개체 모델을 통해 모든 구성 작업을 프로그래밍 방식으로 제어할 수 있습니다. 또한 API를 사용하는 데이터 수집 작업은 대부분 서버에 설치되는 저장 프로시저로 구현됩니다.

 다음 그림에서는 데이터 컬렉션 개체 모델의 중요 요소를 보여 줍니다.

 ![데이터 수집기 개체 모델](../../../2014/database-engine/dev-guide/media/dc-objectmodel.gif "데이터 수집기 개체 모델")


