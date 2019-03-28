---
title: sp_execute_external_script (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_execute_external_script_TSQL
- sys.sp_execute_external_script
- sys.sp_execute_external_script_TSQL
- sp_execute_external_script
dev_langs:
- TSQL
helpviewer_keywords:
- sp_execute_external_script
ms.assetid: de4e1fcd-0e1a-4af3-97ee-d1becc7f04df
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: f11b09d93510fe1da89abc1a723e7698f1fdd915
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531045"
---
# <a name="spexecuteexternalscript-transact-sql"></a>sp_execute_external_script (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

프로시저에는 입력 인수로 제공 된 스크립트를 실행 합니다. 스크립트를 실행 합니다 [확장성 프레임 워크](../../advanced-analytics/concepts/extensibility-framework.md)합니다. 하나 이상의 확장 하는 데이터베이스 엔진 스크립트 지원 / 등록 언어로 써야 합니다. [**R**](../../advanced-analytics/concepts/extension-r.md)하십시오 [ **Python**](../../advanced-analytics/concepts/extension-python.md), 또는 [ **Java** (SQL Server 2019에 미리 보기 전용)](../../advanced-analytics/java/extension-java.md)합니다. 

실행할 **sp_execute_external_script**에 문을 사용 하 여 외부 스크립트를 먼저 사용 해야 합니다 `sp_configure 'external scripts enabled', 1;`합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

> [!Note]
> (R 및 Python)를 학습 하 고 확장을 프로그래밍 하는 컴퓨터는 데이터베이스 엔진 인스턴스에 추가 기능으로 설치 됩니다. 특정 확장에 대 한 지원이 SQL Server 버전에 따라 다릅니다.

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax"></a>구문

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]    
    [ , @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end
::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"
## <a name="syntax-for-2017-and-earlier"></a>2017 및 이전 버전 구문

```
sp_execute_external_script   
    @language = N'language',   
    @script = N'script'  
    [ , @input_data_1 = N'input_data_1' ]   
    [ , @input_data_1_name = N'input_data_1_name' ]  
    [ , @output_data_1_name = N'output_data_1_name' ]  
    [ , @parallel = 0 | 1 ]  
    [ , @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ] 
    [ , @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]
```
::: moniker-end

## <a name="arguments"></a>인수
 **@language** = N'*language*'  
 스크립트 언어를 나타냅니다. *언어* 됩니다 **sysname**합니다.  SQL server 버전에 따라 유효한 값은 R (SQL Server 2016 이상), (SQL Server 2017 이상), Python 및 Java (SQL Server 2019 미리 보기). 
  
 **@script** = N'*스크립트*' 외부 언어 스크립트 리터럴 또는 변수 입력으로 지정 합니다. *스크립트* 됩니다 **nvarchar (max)** 합니다.  

`[ @input_data_1 =  N'input_data_1' ]` 형태로 외부 스크립트에서 사용 하는 입력된 데이터를 지정 된 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리 합니다. 데이터 형식이 *input_data_1* 됩니다 **nvarchar (max)** 합니다.

`[ @input_data_1_name = N'input_data_1_name' ]` 정의 된 쿼리를 나타내는 데 사용 된 변수의 이름을 지정 @input_data_1합니다. 외부 스크립트의 변수 데이터 형식의 언어에 따라 달라 집니다. R의 경우 입력된 변수는 데이터 프레임을 사용 합니다. Python의 경우 입력은 테이블 형식 이어야 합니다. *input_data_1_name* 됩니다 **sysname**합니다.  기본값은 *InputDataSet*합니다.  

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
`[ @input_data_1_order_by_columns = N'input_data_1_order_by_columns' ]` SQL Server 2019에만 적용 됩니다 및 파티션 별 모델을 빌드하는 데 사용 합니다. 예를 들어 제품 이름으로 결과 집합을 정렬 하는 데 사용 된 열의 이름을 지정 합니다. 외부 스크립트의 변수 데이터 형식의 언어에 따라 달라 집니다. R의 경우 입력된 변수는 데이터 프레임을 사용 합니다. Python의 경우 입력은 테이블 형식 이어야 합니다.

`[ @input_data_1_partition_by_columns = N'input_data_1_partition_by_columns' ]` SQL Server 2019에만 적용 됩니다 및 파티션 별 모델을 빌드하는 데 사용 합니다. 지리적 지역 또는 날짜와 같은 데이터를 분할 하는 데 사용 된 열의 이름을 지정 합니다. 외부 스크립트의 변수 데이터 형식의 언어에 따라 달라 집니다. R의 경우 입력된 변수는 데이터 프레임을 사용 합니다. Python의 경우 입력은 테이블 형식 이어야 합니다. 
::: moniker-end

`[ @output_data_1_name =  N'output_data_1_name' ]` 반환할 데이터를 포함 하는 외부 스크립트의 변수 이름을 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 저장된 프로시저 호출이 완료 되 면 합니다. 외부 스크립트의 변수 데이터 형식의 언어에 따라 달라 집니다. R에 대 한 출력 데이터 프레임을 이어야 합니다. Python pandas 데이터 프레임 출력 이어야 합니다. *output_data_1* 됩니다 **sysname**합니다.  기본값은 *OutputDataSet*합니다.  

`[ @parallel = 0 | 1 ]` 설정 하 여 R 스크립트의 병렬 실행을 사용 하도록 설정 된 `@parallel` 매개 변수 1로 합니다. 이 매개 변수의 기본값은 0 (병렬 처리). 하는 경우 `@parallel = 1` 클라이언트 컴퓨터에 직접 스트리밍되는 출력 및 해당 `WITH RESULT SETS` 절이 필요 하 고 출력 스키마를 지정 해야 합니다.  

 + RevoScaleR 함수를 사용 하 여 사용 하지 않는 R 스크립트를 `@parallel` 매개 변수는 스크립트는 일반적으로 병렬 처리할 수 있는 것으로 가정 하는 큰 데이터 집합을 처리 하는 것에 대 한 유용할 수 있습니다. 예를 들어, R을 사용 하는 경우 `predict` 설정에 새 예측을 생성 하는 모델을 사용 하 여 함수 `@parallel = 1` 힌트로 쿼리 엔진. 행이에 따라 분산 쿼리를 병렬 처리할 수는 **MAXDOP** 설정 합니다.  
  
 + RevoScaleR 함수를 사용 하는 R 스크립트에 대 한 병렬 처리는 자동으로 처리 하 고 지정할 수 없습니다 `@parallel = 1` 에 **sp_execute_external_script** 호출 합니다.  
  
`[ @params = N'@parameter_name data_type [ OUT | OUTPUT ] [ ,...n ]' ]` 외부 스크립트에 사용 되는 입력된 매개 변수 선언의 목록입니다.  
  
`[ @parameter1 = 'value1' [ OUT | OUTPUT ] [ ,...n ] ]` 목록에서 외부 스크립트를 사용 하는 입력된 매개 변수의 값입니다.  

## <a name="remarks"></a>Remarks

> [!IMPORTANT]
> 쿼리 트리를 통해 제어 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 쿼리에 대 한 임의 작업을 수행할 수 없습니다. 

사용 하 여 **sp_execute_external_script** 지원 되는 언어로 작성 된 스크립트를 실행 합니다. 현재 지원 되는 언어는 SQL Server 2016 R Services, Python 및 SQL Server 2017의 Machine Learning Services에 대 한 R에 대 한 R입니다. 

기본적으로이 저장된 프로시저가 반환한 결과 집합에는 명명 되지 않은 열을 사용 하 여 출력 됩니다. 열 이름은 스크립트 내에서 사용 되는 스크립팅 환경에 로컬인 및 출력된 결과 집합에 반영 되지 않습니다. 결과 집합 열 이름을 사용 합니다 `WITH RESULT SET` 절의 [ `EXECUTE` ](../../t-sql/language-elements/execute-transact-sql.md)합니다.
  
 결과 집합을 반환 하는 것 외에도 스칼라 값을 반환할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 출력 매개 변수를 사용 하 여 합니다. 다음 예제에서는 출력 매개 변수를 스크립트에 대 한 입력으로 사용 된 직렬화 된 R 모델의 사용을 보여 줍니다.  
  
외부 리소스 풀을 구성 하 여 외부 스크립트에서 사용 하는 리소스를 제어할 수 있습니다. 자세한 내용은 [CREATE EXTERNAL RESOURCE POOL&#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)을 참조하세요. 리소스 관리자 카탈로그 뷰, DMV의 및 카운터에서 워크 로드에 대 한 정보를 얻을 수 있습니다. 자세한 내용은 [리소스 관리자 카탈로그 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md), [리소스 관리자 관련 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/resource-governor-related-dynamic-management-views-transact-sql.md), 및 [ SQL Server, External Scripts 개체](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)합니다.  

### <a name="monitor-script-execution"></a>스크립트 실행 모니터링

사용 하 여 모니터링 스크립트 실행 [sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md) 하 고 [sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)합니다. 

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
### <a name="parameters-for-partition-modeling"></a>파티션 모델링에 대 한 매개 변수

 SQL Server 2019에 현재 공개 미리 보기에서 설정할 수 있습니다 분할 된 데이터에 있는 파티션 하나를 기반으로 또는 제공 되는 열 자연스럽 게 데이터 집합을 논리적 파티션으로 분할 생성 및 사용에 관한 모델링을 사용 하도록 설정 하는 두 개의 추가 매개 변수 스크립트를 실행 하는 동안에 나가, 성별, 지역, 날짜 또는 시간에 대 한 반복 되는 값을 포함 하는 열은 데이터 집합을 분할된 하는 몇 가지 예입니다.
 
 두 매개 변수가 **input_data_1_partition_by_columns** 하 고 **input_data_1_order_by_columns**결과 집합을 정렬 하려면 두 번째 매개 변수는 사용 하는 위치, 합니다. 매개 변수 입력으로 전달 됩니다 `sp_execute_external_script` 는 외부 스크립트를 실행 하 되 면 모든 파티션에 대 한 합니다. 자세한 내용 및 예제를 참조 하세요. [자습서: 파티션 기반 모델을 만들](https://docs.microsoft.com/sql/advanced-analytics/tutorials/r-tutorial-create-models-per-partition.md)합니다.

 스크립트를 지정 하 여 병렬로 실행할 수 있습니다 `@parallel=1`합니다. 입력된 쿼리를 병렬 처리할 수 하는 경우 설정 해야 `@parallel=1` 에 대 한 인수의 일부로 `sp_execute_external_script`합니다. 기본적으로 쿼리 최적화 프로그램에서 작동 `@parallel=1` 있지만이 명시적으로 처리 하려는 경우 256 개 이상의 행이 있는 테이블에서이 스크립트는 데모로 매개 변수를 포함 합니다.

 > [!Tip]
> 교육 workoads 따르면 `@parallel` 모든 임의 학습 스크립트를 사용 하 여 비 Microsoft rx 알고리즘을 사용 하는 것에 합니다. 일반적으로 (rx 접두사로) RevoScaleR 알고리즘만 SQL Server의 교육 시나리오에서 병렬 처리를 제공합니다. 하지만 SQL Server vNext의 새로운 매개 변수를 사용 하 여 해당 기능을 사용 하 여 특별히 엔지니어링 된 함수를 호출 하는 스크립트를 병렬 처리할 수 있습니다.
::: moniker-end

### <a name="streaming-execution-for-r-and-python-scripts"></a>R 및 Python 스크립트에 대 한 스트리밍 실행  

스트리밍 작업 메모리에 맞출 수 있는 수보다 더 많은 데이터를 사용 하 여 R 또는 Python 스크립트를 허용 합니다. 스트리밍 하는 동안 전달 되는 행 수를 제어 하려면 매개 변수에 정수 값을 지정할 `@r_rowsPerRead` 에 `@params` 컬렉션입니다.  예를 들어, 매우 다양 한 데이터를 사용 하는 모델을 교육 하는 경우 하나의 청크로 데이터의 모든 행을 받을 수 있는지 확인 하려면 적은 수의 행을 읽은 값을 조정할 수 있습니다. 또한 읽기 및 서버 성능 문제를 완화 하기 위해 한 번에 처리 중인 행 수를 관리 하려면이 매개 변수를 사용할 수 있습니다. 
  
모두를 `@r_rowsPerRead` 스트리밍에 대 한 매개 변수 및 `@parallel` 인수 힌트 고려해 야 합니다. 적용할 힌트에 대 한 병렬 처리를 포함 하는 SQL 쿼리 계획을 생성할 수 있어야 합니다. 없는 경우에 병렬 처리를 사용할 수 없습니다.  
  
> [!NOTE]  
>  스트리밍 및 병렬 처리는 Enterprise Edition 에서만에서 지원 됩니다. 오류가 발생 하지 않고 Standard Edition에서는 쿼리에서 매개 변수를 포함할 수 있습니다 했지만 매개 변수를 단일 프로세스에서 실행 된 R 스크립트 없고 적용 합니다.  
  
## <a name="restrictions"></a>Restrictions  


### <a name="data-types"></a>데이터 형식

데이터 형식은 입력된 쿼리 또는 매개 변수를 사용 하면 되지 **sp_execute_external_script** 프로시저와 지원 되지 않는 유형이 오류를 반환 합니다.  

대 안으로 **캐스트** 열 또는 값에서 지원 되는 형식 [!INCLUDE[tsql](../../includes/tsql-md.md)] 외부 스크립트를 보내기 전에 합니다.  
  
-   **cursor**  
  
-   **timestamp**  
  
-   **datetime2**, **datetimeoffset**, **time**  
  
-   **sql_variant**  
  
-   **text**, **image**  
  
-   **xml**  
  
-   **hierarchyid**, **geometry**, **geography**  
  
-   CLR 사용자 정의 형식

모든 결과 집합에 매핑할 수 없는 일반적으로 [!INCLUDE[tsql](../../includes/tsql-md.md)] 데이터 형식으로 NULL로 출력 됩니다.  

### <a name="restrictions-specific-to-r"></a>R 관련 제한 사항

입력에 포함 된 경우 **날짜/시간** R에서 허용 되는 값 범위의 맞지 않는 값을 값으로 변환할지 **NA**합니다. 때문에 이것이 필요 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 더 큰 범위의 값 R 언어에서 지원 되는 것을 허용 합니다.

Float 값 (예를 들어 `+Inf`, `-Inf`를 `NaN`)에서 지원 되지 않습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] IEEE 754를 사용 하는 두 언어도 합니다. 현재 동작에만 값을 보냅니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL 클라이언트에 결과적으로 직접; [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 오류를 throw 합니다. 따라서 이러한 값으로 변환할지 **NULL**합니다.

## <a name="permissions"></a>사용 권한

필요 **EXECUTE ANY EXTERNAL SCRIPT** 데이터베이스 사용 권한.  

## <a name="examples"></a>예

사용 하 여 R 또는 Python 스크립트를 실행 하려면이 저장된 프로시저를 사용할 수 있는 방법을의 예제를 포함 하는이 섹션에서는 [!INCLUDE[tsql](../../includes/tsql-md.md)]합니다.

### <a name="a-return-an-r-data-set-to-sql-server"></a>1. SQL Server에 R 데이터 집합을 반환  

다음 예제를 사용 하는 저장된 프로시저를 만듭니다 **sp_execute_external_script** R에 포함 된 Iris 데이터 집합을 반환할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  

```sql
DROP PROC IF EXISTS get_iris_dataset;  
go  
CREATE PROC get_iris_dataset
AS  
BEGIN  
 EXEC   sp_execute_external_script  
       @language = N'R'  
     , @script = N'iris_data <- iris;'
     , @input_data_1 = N''  
     , @output_data_1_name = N'iris_data'
     WITH RESULT SETS (("Sepal.Length" float not null,   
           "Sepal.Width" float not null,  
        "Petal.Length" float not null,   
        "Petal.Width" float not null, "Species" varchar(100)));  
END;
GO
```

### <a name="b-generate-an-r-model-based-on-data-from-sql-server"></a>2. SQL Server에서 데이터를 기반으로 R 모델을 생성 합니다.  

다음 예제를 사용 하는 저장된 프로시저를 만듭니다 **sp_execute_external_script** 아이리스 모델을 생성 하 고 모델을 반환 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  

> [!NOTE]
>  이 예제에는 e1071 패키지가 사전 설치를 해야합니다. 자세한 내용은 [SQL Server에 추가 R 패키지 설치](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)합니다.

```sql
DROP PROC IF EXISTS generate_iris_model;
GO
CREATE PROC generate_iris_model
AS
BEGIN
 EXEC sp_execute_external_script  
      @language = N'R'  
     , @script = N'  
          library(e1071);  
          irismodel <-naiveBayes(iris_data[,1:4], iris_data[,5]);  
          trained_model <- data.frame(payload = as.raw(serialize(irismodel, connection=NULL)));  
'  
     , @input_data_1 = N'select "Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species" from iris_data'  
     , @input_data_1_name = N'iris_data'  
     , @output_data_1_name = N'trained_model'  
    WITH RESULT SETS ((model varbinary(max)));  
END;
GO
```

Python을 사용하여 비슷한 모델을 생성하려면 언어 식별자를 `@language=N'R'`에서 `@language = N'Python'`으로 변경하고 `@script` 인수를 필요한 대로 수정합니다. 그렇지 않으면 모든 매개 변수가 R과 똑같이 작동합니다.

### <a name="c-create-a-python-model-and-generate-scores-from-it"></a>3. Python 모델을 만들고 여기에서 점수를 생성 합니다.

이 예제에서는 sp\_execute\_external\_script를 사용하여 간단한 Python 모델에서 점수를 생성하는 방법을 보여줍니다. 

```sql
CREATE PROCEDURE [dbo].[py_generate_customer_scores]
AS
BEGIN

-- Input query to generate the customer data
DECLARE @input_query NVARCHAR(MAX) = N'SELECT customer, orders, items, cost FROM dbo.Sales.Orders'

EXEC sp_execute_external_script @language = N'Python', @script = N'
import pandas as pd
from sklearn.cluster import KMeans

# Get data from input query
customer_data = my_input_data

# Define the model
n_clusters = 4
est = KMeans(n_clusters=n_clusters, random_state=111).fit(customer_data[["orders","items","cost"]])
clusters = est.labels_
customer_data["cluster"] = clusters

OutputDataSet = customer_data
'
, @input_data_1 = @input_query
, @input_data_1_name = N'my_input_data'
WITH RESULT SETS (("CustomerID" int, "Orders" float,"Items" float,"Cost" float,"ClusterResult" float));
END;
GO
```

Python 코드에 열 머리글이 없는 SQL server에 대 한 출력 따라서 문을 사용 하 여 사용 하 여 결과 열 이름 및 sql에서 사용할 데이터 형식을 지정 합니다.

점수 매기기의 경우 네이티브 [PREDICT](../../t-sql/queries/predict-transact-sql.md) 함수를 사용할 수도 있으며, 이 함수는 Python 또는 R 런타임 호출을 방지하기 때문에 일반적으로 더 빠릅니다.

## <a name="see-also"></a>참고자료

 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Python 라이브러리 및 데이터 형식](../../advanced-analytics/python/python-libraries-and-data-types.md)  
 [R 라이브러리 및 R 데이터 형식](../../advanced-analytics/r/r-libraries-and-data-types.md)  
 [SQL Server R Services](../../advanced-analytics/r/sql-server-r-services.md)   
 [SQL Server Machine Learning 서비스에 대 한 알려진된 문제](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)   
 [CREATE EXTERNAL LIBRARY &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-external-library-transact-sql.md)  
 [sp_prepare &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [External Scripts Enabled 서버 구성 옵션](../../database-engine/configure-windows/external-scripts-enabled-server-configuration-option.md)   
 [SERVERPROPERTY&#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md)   
 [SQL Server, External Scripts 개체](../../relational-databases/performance-monitor/sql-server-external-scripts-object.md)  
[sys.dm_external_script_requests](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-requests.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md) 
