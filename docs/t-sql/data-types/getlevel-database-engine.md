---
title: GetLevel(데이터베이스 엔진) | Microsoft Docs
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GetLevel
- GetLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- GetLevel [Database Engine]
ms.assetid: 81577d7e-8ff6-4e73-b7f4-94c03d4921e7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f05c80a78417a8b5153345466eadcd49fa810228
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68077995"
---
# <a name="getlevel-database-engine"></a>GetLevel(데이터베이스 엔진)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

트리에서 노드 *this*의 깊이를 나타내는 정수를 반환합니다.
  
## <a name="syntax"></a>구문  
  
```sql
-- Transact-SQL syntax  
node.GetLevel ( )   
```  
  
```sql
-- CLR syntax  
SqlInt16 GetLevel ( )   
```  
  
## <a name="return-types"></a>반환 형식  
**SQL Server 반환 형식: smallint**
  
**CLR 반환 형식: SqlInt16**
  
## <a name="remarks"></a>설명  
하나 이상의 노드 수준을 확인하거나 지정된 수준의 멤버로 노드를 필터링하는 데 사용됩니다. 계층의 루트는 수준 0입니다.
  
GetLevel은 너비 우선 검색 인덱스에 유용합니다. 자세한 내용은 [계층적 데이터&#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)를 참조하세요.
  
## <a name="examples"></a>예  
  
### <a name="a-returning-the-hierarchy-level-as-a-column"></a>A. 계층 수준을 열로 반환  
다음 예에서는 **hierarchyid**의 텍스트 표현을 반환한 다음, 테이블의 모든 행에 대해 **EmpLevel** 열로 계층 수준을 반환합니다.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo;  
```  
  
### <a name="b-returning-all-members-of-a-hierarchy-level"></a>B. 계층 수준의 모든 멤버 반환  
다음 예에서는 계층 수준 2에 있는 테이블의 모든 행을 반환합니다.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 2;  
```  
  
### <a name="c-returning-the-root-of-the-hierarchy"></a>C. 계층의 루트 반환  
다음 예에서는 계층 수준의 루트를 반환합니다.
  
```sql
SELECT OrgNode.ToString() AS Text_OrgNode,   
OrgNode.GetLevel() AS EmpLevel, *  
FROM HumanResources.EmployeeDemo  
WHERE OrgNode.GetLevel() = 0;  
```  
  
### <a name="d-clr-example"></a>D. CLR 예  
다음 코드 조각은 GetLevel() 메서드를 호출합니다.
  
```sql
this.GetLevel()  
```  
  
## <a name="see-also"></a>참고 항목
[hierarchyid 데이터 형식 메서드 참조](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[계층적 데이터&#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid&#40;Transact-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)
  