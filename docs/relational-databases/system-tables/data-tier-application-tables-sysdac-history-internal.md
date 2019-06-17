---
title: sysdac_history_internal (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_history_internal
- sysdac_history_internal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_history_internal
ms.assetid: 774a1678-0b27-42be-8adc-a6d7a4a56510
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40696085bc8eb9980d1150feade91a9edd627be0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471142"
---
# <a name="data-tier-application-tables---sysdachistoryinternal"></a>데이터 계층 애플리케이션 테이블 - sysdac_history_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  DAC(데이터 계층 응용 프로그램)를 관리하기 위해 수행된 동작에 대한 정보를 포함합니다. 이 테이블에 저장 되는 **dbo** 의 스키마를 **msdb** 데이터베이스입니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**action_id**|**int**|동작의 식별자입니다.|  
|**sequence_id**|**int**|동작 내의 단계를 식별합니다.|  
|**instance_id**|**uniqueidentifier**|DAC 인스턴스의 식별자입니다. 이 열에서 조인할 수는 **instance_id** 열에서 [dbo.sysdac_instances &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md).|  
|**action_type**|**tinyint**|동작 유형의 식별자입니다.<br /><br /> **0** = deploy<br /><br /> **1** = create<br /><br /> **2** = rename<br /><br /> **3** = detach<br /><br /> **4** = delete|  
|**action_type_name**|**varchar(19)**|동작 유형의 이름입니다.<br /><br /> **deploy**<br /><br /> **create**<br /><br /> **rename**<br /><br /> **detach**<br /><br /> **delete**|  
|**dac_object_type**|**tinyint**|동작의 영향을 받는 개체의 유형에 대한 식별자입니다.<br /><br /> **0** = dacpac<br /><br /> **1** = 로그인<br /><br /> **2** = database|  
|**dac_object_type_name**|**varchar(8)**|동작의 영향을 받는 개체의 유형에 대한 이름입니다.<br /><br /> **dacpac** = DAC 인스턴스<br /><br /> **login**<br /><br /> **데이터베이스**|  
|**action_status**|**tinyint**|동작의 현재 상태를 식별하는 코드입니다.<br /><br /> **0** = pending<br /><br /> **1** = success<br /><br /> **2** = fail|  
|**action_status_name**|**varchar(11)**|동작의 현재 상태입니다.<br /><br /> **pending**<br /><br /> **success**<br /><br /> **fail**|  
|**필수**|**bit**|[!INCLUDE[ssDE](../../includes/ssde-md.md)]에서 DAC 작업을 롤백할 때 사용됩니다.|  
|**dac_object_name_pretran**|**sysname**|동작이 포함된 트랜잭션이 커밋되기 전의 개체 이름입니다. 데이터베이스 및 로그인에만 사용됩니다.|  
|**dac_object_name_posttran**|**sysname**|동작이 포함된 트랜잭션이 커밋된 후의 개체 이름입니다. 데이터베이스 및 로그인에만 사용됩니다.|  
|**sqlscript**|**nvarchar(max)**|데이터베이스 또는 로그인에서 동작을 구현하는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트입니다.|  
|**payload**|**varbinary(max)**|인코딩된 이진 문자열에 저장된 DAC 패키지 정의입니다.|  
|**설명**|**varchar(max)**|DAC 업그레이드 시 잠재적인 데이터 손실을 허용한 사용자의 로그인을 기록합니다.|  
|**error_string**|**nvarchar(max)**|동작에 오류가 발생한 경우 생성되는 오류 메시지입니다.|  
|**created_by**|**sysname**|이 항목을 만든 동작을 시작한 로그인입니다.|  
|**date_created**|**datetime**|이 항목을 만든 날짜와 시간입니다.|  
|**date_modified**|**datetime**|이 항목을 마지막으로 수정한 날짜와 시간입니다.|  
  
## <a name="remarks"></a>Remarks  
 DAC 배포 또는 삭제와 같은 DAC 관리 동작은 여러 단계를 생성합니다. 각 동작에는 동작 식별자가 할당됩니다. 각 단계 시퀀스 번호 및 행에 할당 됩니다 **sysdac_history_internal**, 여기서 단계의 상태가 기록 됩니다. 각 행은 동작 단계가 시작될 때 만들어지고 작업 상태를 반영하기 위해 필요에 따라 업데이트됩니다. 예를 들어 DAC 배포 동작은 할당할 수 없습니다 **action_id** 의 네 개 행 12 및 get **sysdac_history_internal**:  
  
|||||  
|-|-|-|-|  
|**action_id**|**sequence_id**|**action_type_name**|**dac_object_type_name**|  
|12|0|만들기|dacpac|  
|12|1|만들기|로그인|  
|12|2|만들기|database|  
|12|3|이름 바꾸기|database|  
  
 Delete 등의 DAC 작업에서 행을 제거 하지 마세요 **sysdac_history_internal**합니다. 다음 쿼리를 사용하여 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 더 이상 배포되지 않는 DAC의 행을 수동으로 삭제할 수 있습니다.  
  
```sql  
DELETE FROM msdb.dbo.sysdac_history_internal  
WHERE instance_id NOT IN  
   (SELECT instance_id  
    FROM msdb.dbo.sysdac_instances_internal);  
```  
  
 활성 DAC의 행을 삭제해도 DAC 작업에는 영향이 없고 단지 DAC에 대한 전체 기록을 보고할 수 없게 될 뿐입니다.  
  
> [!NOTE]  
>  현재 삭제 하기 위한 메커니즘이 없습니다 방법이 **sysdac_history_internal** 행 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]합니다.  
  
## <a name="permissions"></a>사용 권한  
 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다. 이 보기에 대 한 읽기 전용 액세스는 master 데이터베이스에 연결할 권한이 있는 모든 사용자에 게 제공 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 계층 응용 프로그램](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo.sysdac_instances &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)   
 [sysdac_instances_internal &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/data-tier-application-tables-sysdac-instances-internal.md)  
  
  
