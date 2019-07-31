---
title: 마이그레이션 평가용 PowerShell cmdlet | Microsoft 문서
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 769948242c747abdfb1fd6e32606df6a5800a9bb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054437"
---
# <a name="powershell-cmdlet-for-migration-evaluation"></a>마이그레이션 평가용 PowerShell cmdlet
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Save-SqlMigrationReport cmdlet은 SQL Server 데이터베이스에서 여러 개체의 마이그레이션 적합성을 평가하는 도구입니다. 현재 이 도구에서는 메모리 내 OLTP에 대한 마이그레이션 적합성만 평가할 수 있습니다. 이 cmdlet은 관리자 권한 Windows PowerShell 환경과 sqlps에서 모두 실행할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### <a name="parameters"></a>매개 변수  
 아래 표에서는 이 cmdlet의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|----------------|-----------------|  
|MigrationType|cmdlet의 대상인 마이그레이션 시나리오의 유형입니다. 현재 이 매개 변수에 사용 가능한 값은 기본 OLTP뿐입니다. (선택 사항)|  
|서버|대상 SQL Server 인스턴스의 이름입니다. -InputObject 매개 변수를 제공하지 않는 경우 Windows PowerShell에서 필수 항목입니다. SQLPS에서는 선택 사항입니다.|  
|데이터베이스|대상 SQL Server 데이터베이스의 이름입니다. -InputObject 매개 변수를 제공하지 않는 경우 Windows PowerShell에서 필수 항목입니다. SQLPS에서는 선택 사항입니다.|  
|Object|대상 데이터베이스 개체의 이름입니다. 테이블 또는 저장 프로시저일 수 있습니다.|  
|InputObject|cmdlet의 대상으로 지정해야 하는 SMO 개체입니다. -Server 및 -Database를 제공하지 않는 경우 Windows PowerShell에서 필수 항목입니다. SQLPS에서는 선택 사항입니다.|  
|FolderPath|cmdlet이 생성된 보고서를 저장해야 하는 폴더입니다. 필수 사항입니다.|  
  
## <a name="results"></a>결과  
 -FolderPath 매개 변수에 지정된 폴더에서 Tables 및 Stored Procedures의 두 폴더 이름이 생성됩니다. 대상 개체가 테이블이면 해당 보고서는 Tables 폴더에 저장됩니다. 그렇지 않으면 보고서가 Stored Procedures 폴더에 저장됩니다.  
  
  
