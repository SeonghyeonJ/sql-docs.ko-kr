---
description: sys.service_contract_usages(Transact-SQL)
title: sys. service_contract_usages (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contract_usages
- sys.service_contract_usages
- sys.service_contract_usages_TSQL
- service_contract_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_usages catalog view
ms.assetid: 20af425e-1152-4a46-b1ac-94cff5fc9f02
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1b44ee215023a33cb27c73e16933bfafd9839703
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539551"
---
# <a name="sysservice_contract_usages-transact-sql"></a>sys.service_contract_usages(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  이 카탈로그 뷰에는 각 서비스-계약 쌍에 대한 행이 포함되어 있습니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|계약을 사용하는 서비스의 식별자입니다. NULL을 허용하지 않습니다.|  
|**service_contract_id**|**int**|서비스에서 사용하는 계약의 식별자입니다. NULL을 허용하지 않습니다.|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
  
