---
title: CLR 루틴용 사용자 지정 특성 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: 1c1105579dc5da82a66fb101e559e1fb96feac1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138625"
---
# <a name="clr-integration-custom-attributes-for-clr-routines"></a>CLR 루틴용 CLR 통합 사용자 지정 특성
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  공용 언어 런타임 (CLR) 루틴, 사용자 정의 형식에 등록 된 사용자 정의 집계를 나열 된 특성을 적용할 수 있습니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]합니다. 특성이 적용되지 않으면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 기본값을 사용합니다. 나열 된 특성에 정의 된 합니다 **Microsoft.SqlServer.Server** 네임 스페이스입니다.  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a>SqlUserDefinedAggregate 특성  
 합니다 **SqlUserDefinedAggregate** 특성 메서드는 사용자 정의 집계로 등록 해야 함을 나타냅니다. 이 특성을 사용 하 여 모든 사용자 정의 집계를 주석 처리 해야 합니다.  
  
 자세한 내용은 [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)합니다.  
  
## <a name="the-sqlfunction-attribute"></a>SqlFunction 특성  
 합니다 **SqlFunction** 특성을 적절 한 함수 특성 집합을 사용 하 여 함수로 등록 해야 하는 메서드를 나타냅니다.  
  
 자세한 내용은 [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019)합니다.  
  
## <a name="the-sqlfacet-attribute"></a>SqlFacet 특성  
 합니다 **SqlFacet** 특성은 반환 형식의 사용자 정의 형식 (UDT) 식에 대 한 정보를 반환 하는 데 사용 됩니다.  
  
 자세한 내용은 [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)합니다.  
  
## <a name="the-sqlprocedure-attribute"></a>SqlProcedure 특성  
 합니다 **SqlProcedure** 특성 저장 프로시저로 등록 해야 하는 메서드를 나타냅니다. 이 특성은 Visual Studio에서 지정한 메서드를 저장 프로시저로 자동으로 등록하는 데만 사용되며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 사용되지 않습니다.  
  
 자세한 내용은 [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)합니다.  
  
## <a name="the-sqltrigger-attribute"></a>SqlTrigger 특성  
 합니다 **SqlTrigger** 특성 트리거로 등록 해야 하는 메서드를 나타냅니다.  
  
 자세한 내용은 [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) 하 고 [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898)합니다.  
  
## <a name="the-sqluserdefinedtypeattribute"></a>SqlUserDefinedTypeAttribute  
 어셈블리의 클래스 정의에 SqlUserDefinedTypeAttribute를 적용할 수 있습니다. 이렇게 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 이 사용자 지정 특성을 가진 클래스 정의에 바인딩되는 사용자 정의 형식을 만듭니다.  
  
 자세한 내용은 [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)합니다.  
  
## <a name="the-sqlmethod-attribute"></a>SqlMethod 특성  
 합니다 **SqlMethod** 특성은 UDT의 속성 또는 메서드의 결정성 및 데이터 액세스 속성을 나타내는 데 사용 됩니다.  
  
 자세한 내용은 [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [CLR 사용자 정의 집계](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md)   
 [CLR 사용자 정의 함수](../../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md)   
 [CLR 사용자 정의 형식](../../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)   
 [CLR 저장 프로시저](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [CLR 트리거](https://msdn.microsoft.com/library/302a4e4a-3172-42b6-9cc0-4a971ab49c1c)  
  
  
