---
title: sysdac_instances_internal (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_instances_internal_TSQL
- sysdac_instances_internal
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_instances_internal
ms.assetid: d2d52cc4-3463-431a-b779-6fbfdeee1dfc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b5fcc3527880383e6a42a4c5530e2e1aeacc055b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82807214"
---
# <a name="data-tier-application-tables---sysdac_instances_internal"></a>데이터 계층 애플리케이션 테이블 - sysdac_instances_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에 배포된 DAC(데이터 계층 애플리케이션) 인스턴스마다 하나의 행을 표시합니다. 이 테이블은 msdb 데이터베이스의 dbo 스키마에 저장 됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|instance_id|**uniqueidentifier**|DAC 인스턴스의 식별자입니다.|  
|instance_name|**sysname**|인스턴스를 배포할 때 지정된 DAC 인스턴스의 이름입니다.|  
|type_name|**sysname**|DAC 패키지를 만들 때 지정된 DAC의 이름입니다.|  
|type_version|**nvarchar (64)**|DAC 패키지를 만들 때 지정된 DAC의 버전입니다.|  
|description|**nvarchar(4000)**|DAC 패키지를 만들 때 작성된 DAC에 대한 설명입니다.|  
|type_stream|**varbinary(max)**|DAC에 포함된 테이블 및 뷰와 같은 논리 개체의 인코딩된 표현을 포함하는 비트 스트림입니다.|  
|date_created|**datetime**|DAC 인스턴스를 만든 날짜와 시간입니다.|  
|created_by|**sysname**|DAC 인스턴스를 만든 사람의 로그인 정보입니다.|  
  
## <a name="remarks"></a>설명  
 Master 데이터베이스에 대 한 연결 권한이 있는 모든 사용자는이 뷰에 대 한 읽기 전용 액세스를 사용할 수 있습니다.  
  
## <a name="permissions"></a>권한  
 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 계층 응용 프로그램](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [sysdac_instances &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)  
  
  
