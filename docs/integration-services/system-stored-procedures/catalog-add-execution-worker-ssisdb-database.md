---
title: catalog.add_execution_worker(SSISDB 데이터베이스) | Microsoft Docs
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d587cedd-6402-4d5c-9526-7cd25627a037
author: janinezhang
ms.author: janinez
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: a7e68b6f2ad46eb4f18bd46e0f4728bdec35d366
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65717244"
---
# <a name="catalogaddexecutionworker-ssisdb-database"></a>catalog.add_execution_worker(SSISDB 데이터베이스)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Scale Out의 실행 인스턴스에 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out 작업자를 추가합니다.

## <a name="syntax"></a>구문

```sql
catalog.add_execution_worker [@execution_id = ] execution_id, [@workeragent_id = ] workeragent_id
```

## <a name="arguments"></a>인수
[ @execution_id = ] *execution_id*  
 실행 인스턴스의 고유 식별자입니다. *execution_id*는 **bigint**입니다.  
 
[@workeragent_id = ] *workeragent_id*  
스케일 아웃 작업자의 작업자 에이전트 ID입니다. *workeragent_id*는 **uniqueIdentifier**입니다.

## <a name="return-code-value"></a>반환 코드 값  
 0(성공)  
  
## <a name="result-sets"></a>결과 집합  
 없음  

## <a name="permissions"></a>사용 권한  
 이 저장 프로시저를 실행하려면 다음 권한 중 하나가 필요합니다.  
  
-   실행 인스턴스에 대한 READ 및 MODIFY 권한  
  
-   **ssis_admin** 데이터베이스 역할에 대한 멤버 자격  
  
-   **sysadmin** 서버 역할에 대한 멤버 자격  
 
## <a name="errors-and-warnings"></a>오류 및 경고  
 다음 목록에서는 오류나 경고가 발생하는 몇 가지 조건을 설명합니다.  
 
- 사용자에게 적절한 권한이 없는 경우

- 실행 식별자가 잘못되었습니다.

- 작업자 에이전트 ID가 잘못되었습니다.

- 실행이 스케일 아웃에 없습니다.

## <a name="see-also"></a>참고 항목
[스케일 아웃에서 패키지 실행](~/integration-services/scale-out/run-packages-in-integration-services-ssis-scale-out.md).

