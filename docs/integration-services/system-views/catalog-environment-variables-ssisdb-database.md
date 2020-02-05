---
title: catalog.environment_variables(SSISDB 데이터베이스) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 45f5aacd-505a-443b-8fc2-c7929e78cff8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fdb7a7c325a6189feaea690fe2cc22d685ba86e6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296653"
---
# <a name="catalogenvironment_variables-ssisdb-database"></a>catalog.environment_variables(SSISDB 데이터베이스)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 카탈로그에 있는 모든 환경에 대한 환경 변수 정보를 표시합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|variable_id|**bigint**|환경 변수의 고유 식별자(ID)입니다.|  
|environment_id|**bigint**|변수가 연결된 환경의 고유 ID입니다.|  
|name|**sysname**|환경 변수의 이름입니다.|  
|description|**nvarchar(1024)**|환경 변수에 대한 설명입니다.|  
|type|**nvarchar(128)**|환경 변수의 데이터 형식입니다.|  
|sensitive|**bit**|값이 `1`이면 변수가 중요하며 저장될 때 암호화됩니다. 값이 `0`이면 변수가 중요하지 않으며 값이 일반 텍스트로 저장됩니다.|  
|값|**sql_variant**|환경 변수의 값입니다. sensitive가 `0`이면 일반 텍스트 값이 표시됩니다. sensitive가 `1`이면 **NULL** 값이 표시됩니다.|  
  
## <a name="remarks"></a>설명  
 이 뷰는 카탈로그에 있는 각 환경 변수에 대한 행을 표시합니다.  
  
## <a name="permissions"></a>사용 권한  
 이 뷰를 보려면 다음 권한 중 하나가 필요합니다.  
  
-   해당 환경에 대한 READ 권한  
  
-   **ssis_admin** 데이터베이스 역할에 대한 멤버 자격  
  
-   **sysadmin** 서버 역할에 대한 멤버 자격  
  
> [!NOTE]  
>  서버에서 작업을 수행할 권한이 있으면 작업에 대한 정보를 볼 수 있는 권한도 있습니다. 행 수준 보안이 적용됩니다. 따라서 볼 수 있는 권한이 있는 행만 표시됩니다.  
  
  
