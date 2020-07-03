---
title: sys. sp_cdc_generate_wrapper_function (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_generate_wrapper_function_TSQL
- sp_cdc_generate_wrapper_function
- sys.sp_cdc_generate_wrapper_function_TSQL
- sys.sp_cdc_generate_wrapper_function
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_generate_wrapper_function
- sp_cdc_generate_wrapper_function
ms.assetid: 85bc086d-8a4e-4949-a23b-bf53044b925c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 68dbfaed63677a7d64c489646592fe35745ff3b1
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891121"
---
# <a name="syssp_cdc_generate_wrapper_function-transact-sql"></a>sys.sp_cdc_generate_wrapper_function(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 사용할 수 있는 변경 데이터 캡처 쿼리 함수에 대한 래퍼 함수를 만드는 스크립트를 생성합니다. 생성된 래퍼에서 지원되는 API를 사용하면 쿼리 간격을 날짜/시간 간격으로 지정할 수 있습니다. 이렇게 하면 변경 데이터 캡처 기술을 사용하여 증분 로드를 결정하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지 디자이너가 개발하는 웨어하우징 애플리케이션을 비롯한 많은 웨어하우징 애플리케이션에서 함수 사용이 용이해집니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sys.sp_cdc_generate_wrapper_function  
    [ [ @capture_instance sysname = ] 'capture_instance'  
    [ , [ @closed_high_end_point = ] closed_high_end_pt  
    [ , [ @column_list = ] 'column_list'  
```  
  
```  
  
[ , [ @update_flag_list = ] 'update_flag_list'  
```  
  
## <a name="arguments"></a>인수  
 [ @capture_instance =] '*capture_instance*'  
 스크립트를 생성할 캡처 인스턴스입니다. *capture_instance* 는 **sysname** 이며 기본값은 NULL입니다. 값이 생략되거나 NULL로 명시적으로 설정된 경우 모든 캡처 인스턴스에 대해 래퍼 스크립트가 생성됩니다.  
  
 [ @closed_high_end_point =] *high_end_pt_flag*  
 생성된 프로시저가 커밋 시간이 상위 엔드포인트와 같은 변경 내용을 추출 간격에 포함할지 여부를 나타내는 플래그 비트입니다. *high_end_pt_flag* 은 **bit** 이며 기본값은 끝점을 포함 해야 함을 나타내는 1입니다. 값 0은 모든 커밋 시간이 상위 엔드포인트보다 낮아야 함을 나타냅니다.  
  
 [ @column_list =] '*column_list*'  
 래퍼 함수가 반환하는 결과 집합에 포함할 캡처된 열 목록입니다. *column_list* 은 **nvarchar (max)** 이며 기본값은 NULL입니다. NULL을 지정하면 캡처된 모든 열이 포함됩니다.  
  
 [ @update_flag_list =] '*update_flag_list*'  
 래퍼 함수가 반환하는 결과 집합에 업데이트 플래그가 포함되는 포함 열 목록입니다. *update_flag_list* 은 **nvarchar (max)** 이며 기본값은 NULL입니다. NULL을 지정하면 업데이트 플래그가 포함되지 않습니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 0(성공) 또는 1(실패)  
  
## <a name="result-sets"></a>결과 집합  
  
|열 이름|열 유형|설명|  
|-----------------|-----------------|-----------------|  
|**function_name**|**nvarchar (145)**|생성된 함수의 이름입니다.|  
|**create_script**|**nvarchar(max)**|캡처 인스턴스 래퍼 함수를 만드는 스크립트입니다.|  
  
## <a name="remarks"></a>설명  
 캡처 인스턴스에 대한 모든 변경 쿼리를 래핑하는 함수를 만드는 스크립트는 항상 생성됩니다. 캡처 인스턴스가 순 변경 쿼리를 지원하는 경우 이 쿼리에 대한 래퍼를 생성하는 스크립트도 생성됩니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `sys.sp_cdc_generate_wrapper_function`을 사용하여 모든 변경 데이터 캡처 함수에 대한 래퍼를 만드는 방법을 보여 줍니다.  
  
```  
DECLARE @wrapper_functions TABLE (  
    function_name sysname,  
    create_script nvarchar(max));  
  
INSERT INTO @wrapper_functions  
EXEC sys.sp_cdc_generate_wrapper_function;  
  
DECLARE @create_script nvarchar(max);  
DECLARE #hfunctions CURSOR LOCAL fast_forward  
FOR   
    SELECT create_script FROM @wrapper_functions;  
  
OPEN #hfunctions;  
FETCH #hfunctions INTO @create_script;  
WHILE (@@fetch_status <> -1)  
BEGIN  
    EXEC sp_executesql @create_script  
    FETCH #hfunctions INTO @create_script  
END;  
  
CLOSE #hfunctions;  
DEALLOCATE #hfunctions;  
```  
  
## <a name="see-also"></a>참고 항목  
 [Transact-sql&#41;&#40;변경 데이터 캡처 저장 프로시저](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [변경 데이터 캡처 &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)  
  
  
