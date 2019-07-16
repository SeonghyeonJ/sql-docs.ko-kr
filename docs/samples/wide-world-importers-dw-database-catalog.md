---
title: WideWorldImporters OLAP 데이터베이스 카탈로그-SQL | Microsoft Docs
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 08/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||>=sql-server-linux-2017||=azure-sqldw-latest||>=aps-pdw-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 7c3da2af72743cc8f89273bfce24fe74fc7e4dc1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68104293"
---
# <a name="wideworldimportersdw-database-catalog"></a>WideWorldImportersDW 데이터베이스 카탈로그
[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md](../includes/appliesto-ss-xxxx-asdw-pdw-md.md)]
스키마, 테이블 및 WideWorldImportersDW 데이터베이스의 저장된 프로시저에 대해 설명 합니다. 

WideWorldImportersDW 데이터베이스 데이터 웨어하우징 및 분석 처리에 사용 됩니다. 판매 및 구매 하는 방법에 대 한 트랜잭션 데이터 WideWorldImporters 데이터베이스에서 생성 되 고 사용 하 여 WideWorldImportersDW 데이터베이스 로드를 **일일 ETL 프로세스**합니다.

WideWorldImportersDW의 데이터를 따라서 WideWorldImporters에서의 데이터를 미러링 하지만 테이블은 서로 다르게 구성 됩니다. WideWorldImporters 정규화 된 기존 스키마에 반면 WideWorldImportersDW 사용 합니다 [별모양 스키마](https://wikipedia.org/wiki/Star_schema) 테이블 디자인에 대 한 접근 방식입니다. 팩트 및 차원 테이블을 외에도 데이터베이스는 ETL 프로세스에서 사용 되는 준비 테이블의 숫자를 포함 합니다.

## <a name="schemas"></a>스키마

다양 한 유형의 테이블은 세 개의 스키마에서 구성 됩니다.

|스키마|설명|
|-----------------------------|---------------------|
|차원|차원 테이블입니다.|
|팩트|팩트 테이블입니다.|  
|통합|테이블 및 ETL에 필요한 다른 개체를 준비 합니다.|  

## <a name="tables"></a>테이블

차원 및 팩트 테이블은 다음과 같습니다. 통합 스키마의 테이블에는 나열 되지 않은 및 ETL 프로세스에만 사용 됩니다.

### <a name="dimension-tables"></a>차원 테이블

WideWorldImportersDW 차원 테이블에 있습니다. WideWorldImporters 데이터베이스에서 원본 테이블을 사용 하 여 관계를 포함 하는 설명 합니다.

|Table|원본 테이블|
|-----------------------------|---------------------|
|City|`Application.Cities`, `Application.StateProvinces`, `Application.Countries`.|
|Customer|`Sales.Customers`, `Sales.BuyingGroups`, `Sales.CustomerCategories`.|
|Date|회계 연도 포함 하 여 날짜에 대 한 정보를 사용 하 여 새 테이블 (11 월 1 일에 따라 회계 연도 대 한 시작)입니다.|
|Employee|`Application.People`.|
|StockItem|`Warehouse.StockItems`, `Warehouse.Colors`, `Warehouse.PackageType`.|
|공급자|`Purchasing.Suppliers`, `Purchasing.SupplierCategories`에 적용되지 않습니다.|
|PaymentMethod|`Application.PaymentMethods`.|
|TransactionType|`Application.TransactionTypes`항목을 참조하세요.|

### <a name="fact-tables"></a>팩트 테이블

WideWorldImportersDW 다음 팩트 테이블에 있습니다. WideWorldImporters 데이터베이스 뿐만 아니라 각 팩트 테이블 일반적으로 사용 되는 분석/보고 쿼리의 클래스에 원본 테이블을 사용 하 여 관계를 포함 하는 설명 합니다.

|Table|원본 테이블|예제 분석|
|-----------------------------|---------------------|---------------------|
|주문|`Sales.Orders` 및 `Sales.OrderLines`|Sales 사람, 선택/packer 생산성 및에서 시간의 orders를 선택 합니다. 또한 낮은 orders를 백업 하려면 선행 품절 상황입니다.|
|판매|`Sales.Invoices` 및 `Sales.InvoiceLines`|판매 날짜, 배달 날짜, 시간에 따른 수익성, 영업 사원 수익성 합니다.|
|구매|`Purchasing.PurchaseOrderLines`|예상된 및 실제 시간이|
|트랜잭션|`Sales.CustomerTransactions` 및 `Purchasing.SupplierTransactions`|문제 날짜 및 종료 날짜 및 시간을 측정 합니다.|
|이동|`Warehouse.StockTransactions`|시간이 지남에 따라 이동 합니다.|
|주식 보유|`Warehouse.StockItemHoldings`|보유 재고 수준 및 값입니다.|

## <a name="stored-procedures"></a>저장 프로시저

저장된 프로시저는 ETL 프로세스 및 구성을 위해 주로 사용 됩니다.

샘플의 확장을 사용 하도록 합니다 `Reports` Reporting Services 보고서에 대 한 스키마 및 `PowerBI` Power BI 액세스에 대 한 스키마입니다.

### <a name="application-schema"></a>응용 프로그램 스키마

이러한 절차는 샘플 구성에 사용 됩니다. PolyBase는 추가 샘플의 스탠더드 버전에 적용 되는 enterprise edition 기능 및 ETL reseed 사용 됩니다.

|절차|용도|
|-----------------------------|---------------------|
|Configuration_ApplyPartitionedColumnstoreIndexing|팩트 테이블의 분할 및 columnstore 인덱스에 적용 됩니다.|
|Configuration_ConfigureForEnterpriseEdition|분할 인덱싱 및 메모리 내 columnstore에 적용 됩니다.|
|Configuration_EnableInMemory|통합 준비 테이블을 ETL 성능 향상을 위해 SCHEMA_ONLY 메모리 최적화 테이블을 바꿉니다.|
|Configuration_ApplyPolyBase|외부 데이터 원본, 파일 형식 및 테이블을 구성합니다.|
|Configuration_PopulateLargeSaleTable|Enterprise edition에 적용 한 다음 2012 년의 추가 기록으로 많은 양의 데이터를 채웁니다.|
|Configuration_ReseedETL|기존 데이터를 제거 하 고 ETL 시드를 다시 시작 됩니다. 따라서 OLAP 데이터베이스를 다시 채워야 OLTP 데이터베이스에서 업데이트 된 행을 일치 시킵니다.|

### <a name="integration-schema"></a>통합 스키마

ETL 프로세스에서 사용 하는 절차는 이러한 범주에 속합니다.
- ETL 패키지-모든 Get * 프로시저에 대 한 도우미 프로시저입니다.
- 모든 마이그레이션 * 프로시저-DW 테이블로 데이터를 준비 하는 ETL 패키지를 마이그레이션하는 데 사용 하는 프로시저입니다.
- `PopulateDateDimensionForYear` -1 년을 사용 하 고 해당 연도의 모든 날짜에 채워졌는지 확인 합니다 `Dimension.Date` 테이블입니다.

### <a name="sequences-schema"></a>시퀀스 스키마

데이터베이스에서 시퀀스를 구성 하는 절차입니다.

|프로시저|용도|
|-----------------------------|---------------------|
|ReseedAllSequences|프로시저 호출 `ReseedSequenceBeyondTableValue` 모든 시퀀스에 대 한 합니다.|
|ReseedSequenceBeyondTableValue|동일한 시퀀스를 사용 하는 테이블의 값 보다 큰 다음 시퀀스 값의 위치를 변경 하는 데 사용 합니다. (같은 `DBCC CHECKIDENT` 순서에 대 한 하지만 잠재적으로 여러 테이블에서 identity 열의 해당.)|
