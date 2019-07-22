---
title: SQL Server XTP 가상 프로세서 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 0f691b3d-a8fd-4459-ad21-2cfc8574a8c0
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f9f7f51b2d0ede3bb49bb152ab08cbb2a7eb2732
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114029"
---
# <a name="sql-server-xtp-phantom-processor"></a>SQL Server XTP 가상 프로세서
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  SQL Server XTP 가상 프로세서 성능 개체에는 메모리 내 OLTP 엔진의 가상 처리 하위 시스템과 관련된 카운터가 포함됩니다. 이 구성 요소는 SERIALIZABLE 격리 수준에서 실행되는 트랜잭션에서 가상 행을 검색하고 동시성 시나리오에서 제약 조건 유효성을 검사합니다.  
  
 이 표에서는 **SQL Server XTP 가상 프로세서** 카운터에 대해 설명합니다.  
  
|카운터|설명|  
|-------------|-----------------|  
|**Dusty corner scan retries/sec (Phantom-issued)**|가상 프로세서에 의해 실행된 불량 영역 청소(dusty corner sweeps) 중 발생한 초당 검색 재시도 횟수입니다(평균). 이 카운터는 사용자용이 아닌 매우 낮은 수준의 카운터입니다.|  
|**Phantom expired rows removed/sec**|가상 검사에 의해 제거된 만료된 초당 행 수입니다(평균).|  
|**Phantom expired rows touched/sec**|가상 검사에 의해 처리된 만료된 초당 행 수입니다(평균).|  
|**Phantom expiring rows touched/sec**|가상 검사에 의해 처리된 만료되는 초당 행 수입니다(평균).|  
|**Phantom rows touched/sec**|가상 검사에 의해 처리된 초당 행 수입니다(평균).|  
|**Phantom scans started/sec**|초당 시작된 가상 검사 수입니다(평균).|  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server XTP&#40;메모리 내 OLTP&#41; 성능 카운터](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)  
  
  
