---
title: sp_fulltext_service (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_service
- sp_fulltext_service_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- full-text search [SQL Server], properties
- sp_fulltext_service
- Full-Text Search Upgrade Option
ms.assetid: 17a91433-f9b6-4a40-88c4-8c704ec2de9f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f1ed86d0b24c8479c0d3a3546845a74d5b518a36
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85757931"
---
# <a name="sp_fulltext_service-transact-sql"></a>sp_fulltext_service(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 전체 텍스트 검색의 서버 속성을 변경합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_fulltext_service [ [@action=] 'action'   
     [ , [ @value= ] value ] ]  
```  
  
## <a name="arguments"></a>인수  
`[ @action = ] 'action'`변경 하거나 다시 설정할 속성입니다. *action* 은 **nvarchar (100)** 이며 기본값은 없습니다. *C*속성의 목록, 해당 설명 및 설정할 수 있는 값에 대해서는 *값* 인수 아래에 있는 표를 참조 하십시오. 이 인수는 데이터 형식, 현재 실행 값, 최소값 또는 최대값, 사용 중단 상태(해당되는 경우)와 같은 속성을 반환합니다.  
  
`[ @value = ] value`지정 된 속성의 값입니다. *값* 은 **sql_variant**이며 기본값은 NULL입니다. @value가 null 이면 **sp_fulltext_service** 현재 설정을 반환 합니다. 이 표에서는 동작 속성, 설명 및 설정할 수 있는 값 목록을 보여 줍니다.  
  
> [!NOTE]  
>  다음 작업은의 이후 릴리스에서 제거 될 예정입니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **clean_up**, **connect_timeout**, **data_timeout**및 **resource_usage**. 향후 개발 작업에서는 이러한 동작을 사용하지 않도록 하고 현재 이러한 동작을 사용하는 애플리케이션은 수정하십시오.  
  
|작업|데이터 형식|Description|  
|------------|---------------|-----------------|  
|**clean_up**|**int**|이전 버전과의 호환성을 위해서만 지원됩니다. 값은 항상 0입니다.|  
|**connect_timeout**|**int**|이전 버전과의 호환성을 위해서만 지원됩니다. 값은 항상 0입니다.|  
|**data_timeout**|**int**|이전 버전과의 호환성을 위해서만 지원됩니다. 값은 항상 0입니다.|  
|**load_os_resources**|**int**|운영 체제 단어 분리기, 형태소 분석기 및 필터가 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 등록되어 사용되는지 여부를 나타냅니다. 다음 중 하나:<br /><br /> 0 = 이 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 연관된 필터와 단어 분리기만 사용합니다.<br /><br /> 1 = 운영 체제 필터와 단어 분리기를 로드합니다.<br /><br /> 기본적으로 이 속성은 운영 체제 업데이트 시 실수로 동작이 변경되는 것을 방지하기 위해 해제되어 있습니다. 운영 체제 리소스를 사용하도록 설정하면 설치된 인스턴스별 리소스가 없는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 인덱싱 서비스에 등록된 언어 및 문서 유형에 대한 리소스에 액세스할 수 있습니다. 운영 체제 리소스를 로드 하도록 설정 하는 경우 운영 체제 리소스가 신뢰할 수 있는 서명 된 이진 파일 인지 확인 합니다. 그렇지 않으면 **verify_signature** (아래 참조)가 1로 설정 된 경우 로드할 수 없습니다.|  
|**master_merge_dop**|**int**|마스터 병합 프로세스에서 사용할 스레드 수를 지정합니다. 이 값은 사용 가능한 CPU 또는 CPU 코어 수를 초과하면 안 됩니다.<br /><br /> 이 인수가 지정되지 않은 경우 서비스에서는 4나 사용 가능한 CPU 또는 CPU 코어 수 중에서 더 작은 수를 사용합니다.|  
|**pause_indexing**|**int**|전체 텍스트 인덱싱이 현재 실행 중인 경우 이를 일시 중지하거나, 현재 일시 중지되었다면 다시 시작할지 여부를 지정합니다.<br /><br /> 0 = 서버 인스턴스에 대한 전체 텍스트 인덱싱 작업을 다시 시작합니다.<br /><br /> 1 = 서버 인스턴스에 대한 전체 텍스트 인덱싱 작업을 일시 중지합니다.|  
|**resource_usage**|**int**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 이상 버전에서는 사용할 수 없으며 무시됩니다.|  
|**update_languages**|NULL|전체 텍스트 검색에 등록된 언어 목록과 필터를 업데이트합니다. 언어는 인덱싱을 구성할 때 전체 텍스트 쿼리에 지정됩니다. 필터 데몬 호스트는 필터 데몬 호스트에서 전체 텍스트 인덱싱에 대해 **varbinary**, **varbinary (max)**, **image**또는 **xml**과 같은 데이터 형식으로 저장 된 .docx와 같은 해당 파일 형식에서 텍스트 정보를 추출 하는 데 사용 됩니다.<br /><br /> 자세한 내용은 [등록된 필터와 단어 분리기 보기 및 변경](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)을 참조하세요.|  
|**upgrade_option**|**int**|데이터베이스를 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]에서 이상 버전으로 업그레이드할 때 전체 텍스트 인덱스를 마이그레이션하는 방법을 제어합니다. 이 속성은 데이터베이스 복사 마법사를 사용하여 데이터베이스를 연결하거나, 데이터베이스 백업 및 파일 백업을 복원하거나, 데이터베이스를 복사하여 업그레이드에 적용됩니다.<br /><br /> 다음 중 하나:<br /><br /> 0 = 향상된 새 단어 분리기를 사용하여 전체 텍스트 카탈로그를 다시 작성합니다. 인덱스를 다시 작성하면 시간이 오래 걸릴 수 있으며 업그레이드 후 CPU 및 메모리가 많이 필요할 수 있습니다.<br /><br /> 1 = 전체 텍스트 카탈로그를 다시 설정합니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 전체 텍스트 카탈로그 파일이 제거되지만 전체 텍스트 카탈로그 및 전체 텍스트 인덱스의 메타데이터는 유지됩니다. 업그레이드가 끝나면 모든 전체 텍스트 인덱스의 변경 내용 추적이 해제되고 탐색이 자동으로 시작되지 않습니다. 업그레이드가 완료된 후 전체 채우기를 수동으로 실행할 때까지 카탈로그가 비어 있습니다.<br /><br /> 2 = 전체 텍스트 카탈로그를 가져옵니다. 일반적으로 가져오기가 다시 작성보다 훨씬 빠릅니다. 예를 들어 CPU를 하나만 사용하는 경우 가져오기가 다시 작성보다 10배 정도 빠릅니다. 그러나 가져온 전체 텍스트 카탈로그에는 향상된 단어 분리기가 사용되지 않으므로 결국에는 전체 텍스트 카탈로그를 다시 작성해야 할 수 있습니다.<br /><br /> 참고: 다시 작성은 다중 스레드 모드에서 실행 될 수 있으며, 10 개 이상의 Cpu를 사용할 수 있는 경우 다시 작성을 통해 모든 Cpu를 사용할 수 있는 경우 다시 빌드가 가져오기 보다 빨리 실행 될 수 있습니다.<br /><br /> 전체 텍스트 카탈로그를 사용할 수 없는 경우 연결된 전체 텍스트 인덱스가 다시 작성됩니다. 이 옵션은 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터베이스에 대해서만 사용할 수 있습니다.<br /><br /> 전체 텍스트 업그레이드 옵션을 선택하는 방법은[전체 텍스트 검색 업그레이드](../../relational-databases/search/upgrade-full-text-search.md)를 참조하세요.<br /><br /> 참고:에서이 속성을 설정 하려면 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **전체 텍스트 업그레이드 옵션** 속성을 사용 합니다. 자세한 내용은 [서버 인스턴스의 전체 텍스트 검색 관리 및 모니터링](../../relational-databases/search/manage-and-monitor-full-text-search-for-a-server-instance.md)을 참조하세요.|  
|**verify_signature**|**int**|전체 텍스트 엔진이 서명된 이진 파일만 로드할지 여부를 나타냅니다. 기본적으로 트러스트된 서명된 이진 파일만 로드됩니다.<br /><br /> 1 = 트러스트된 서명된 이진 파일만 로드하는지 확인합니다(기본값).<br /><br /> 0 = 이진 파일의 서명 여부를 확인하지 않습니다.|  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
 None  
  
## <a name="permissions"></a>사용 권한  
 **Serveradmin** 고정 서버 역할의 멤버 또는 시스템 관리자만 **sp_fulltext_service**을 실행할 수 있습니다.  
  
## <a name="examples"></a>예제  
  
### <a name="a-updating-the-list-of-registered-languages"></a>A. 등록된 언어 목록 업데이트  
 다음 예에서는 전체 텍스트 검색에 등록된 언어 목록을 업데이트합니다.  
  
```  
EXEC sp_fulltext_service 'update_languages';  
GO  
```  
  
### <a name="b-changing-the-full-text-upgrade-option-to-reset-full-text-catalogs"></a>B. 전체 텍스트 카탈로그를 초기화하도록 전체 텍스트 업그레이드 옵션 변경  
 다음 예에서는 전체 텍스트 카탈로그를 초기화하도록 전체 텍스트 업그레이드 옵션을 변경합니다. 이렇게 하면 전체 텍스트 카탈로그가 완전히 제거됩니다. 이 예에서는 선택적 `@action` 및 `@value` 키워드를 지정합니다.  
  
```  
EXEC sp_fulltext_service @action='upgrade_option', @value=1;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [전체 텍스트 검색](../../relational-databases/search/full-text-search.md)   
 [FULLTEXTSERVICEPROPERTY 함수의 &#40;Transact-sql&#41;](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
