---
title: sysssispackages (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 1fa0f587fc5939135b3d88b15066de29be6d8a7c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85889245"
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  에 저장 되는 각 패키지에 대해 한 행을 포함 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 합니다. 이 테이블은 **msdb** 데이터베이스에 저장 됩니다.  
  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|패키지의 고유 식별자입니다.|  
|**id**|**uniqueidentifier**|패키지의 GUID입니다.|  
|**한**|**nvarchar**|패키지에 대한 설명(옵션)입니다.|  
|**createdate**|**datetime**|패키지를 만든 날짜입니다.|  
|**folderid**|**uniqueidentifier**|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 패키지를 나열하는 논리적 폴더의 GUID입니다.|  
|**ownersid**|**varbinary**|패키지를 만든 사용자의 고유 보안 식별자입니다.|  
|**packagedata**|**image**|패키지입니다.|  
|**packageformat**|**int**|패키지가 저장되는 형식입니다.<br /><br /> 값 2는 패키지가 형식으로 저장 됨을 나타냅니다 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .<br /><br /> 값 3은 패키지가 이상 형식으로 저장 됨을 나타냅니다 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|**packagetype**|**int**|패키지를 만든 클라이언트입니다. 가능한 값은 다음과 같습니다.<br /><br /> 0(기본값)<br /><br /> 1 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사)<br /><br /> 3 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 복제)<br /><br /> 5 ( [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너)<br /><br /> 6(유지 관리 계획 디자이너 또는 마법사)<br /><br /> <br /><br /> 이 열의 값은 열거형에 해당 합니다 <xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType> .|  
|**vermajor**|**int**|패키지의 최신 주 버전입니다.|  
|**verminor**|**int**|패키지의 최신 부 버전입니다.|  
|**verbuild**|**int**|패키지의 최신 빌드입니다.|  
|**vercomments**|**nvarchar**|패키지 버전에 대한 설명입니다.|  
|**verid**|**uniqueidentifier**|패키지 버전의 GUID입니다.|  
|**isencrypted**|**bit**|패키지가 암호화되었는지 여부를 나타내는 부울입니다.|  
|**readrolesid**|**varbinary**|패키지를 로드할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 역할입니다.|  
|**writerolesid**|**varbinary**|패키지를 저장할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 역할입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Integration Services&#40;SSIS&#41; 패키지](../../integration-services/integration-services-ssis-packages.md)  
  
  
