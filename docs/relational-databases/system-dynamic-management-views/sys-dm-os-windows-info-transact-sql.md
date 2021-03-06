---
description: sys.dm_os_windows_info(Transact-SQL)
title: sys.dm_os_windows_info (Transact-sql) | Microsoft Docs
ms.custom: ''
ms.date: 03/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_windows_info
- dm_os_windows_info_TSQL
- sys.dm_os_windows_info
- sys.dm_os_windows_info_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_windows_info dynamic management view
ms.assetid: adc81283-fdc2-46c0-bb48-abe82bbf2459
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b04ca0605a7487ba684889f4f0e84b3114d75744
ms.sourcegitcommit: 32135463a8494d9ed1600a58f51819359e3c09dc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91834396"
---
# <a name="sysdm_os_windows_info-transact-sql"></a>sys.dm_os_windows_info(Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Windows 운영 체제 버전 정보를 표시하는 행을 반환합니다.  
  
  Windows에서 실행 되는 SQL Server에만 적용 됩니다. Windows가 아닌 호스트에서 실행 되는 SQL Server에 대 한 유사한 내용은 (예: Linux)를 보려면 [sys.dm_os_host_info &#40;transact-sql&#41;](~/relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)를 사용 합니다. 
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**windows_release**|**nvarchar(256)**|Windows의 경우 릴리스 번호를 반환 합니다. 값 및 설명 목록은 [운영 체제 버전 (Windows)](/windows/desktop/SysInfo/operating-system-version)을 참조 하세요. NULL이 될 수 없습니다.|  
|**windows_service_pack_level**|**nvarchar(256)**| Windows의 경우 Service Pack 번호를 반환 합니다. NULL이 될 수 없습니다. |  
|**windows_sku**|**int**|Windows의 경우 Windows SKU (Stock 보관 단위) ID를 반환 합니다. SKU Id 및 설명 목록은 [GetProductInfo 함수](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getproductinfo)를 참조 하세요. Null을 허용 합니다. |  
|**os_language_version**|**int**| Windows의 경우 운영 체제의 Windows LCID (로캘 식별자)를 반환 합니다. LCID 값 및 설명 목록은 [Microsoft에서 할당 한 로캘 id](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c)를 참조 하세요. NULL이 될 수 없습니다.|  
  
  
## <a name="permissions"></a>사용 권한  
Sys.dm_os_windows_info에 대 한 SELECT 권한은 기본적으로 public 역할에 부여 됩니다. 해지 된 경우 서버에 대 한 VIEW SERVER STATE 권한이 필요 합니다.  

## <a name="limitations-and-restrictions"></a>제한 사항
Windows가 아닌 호스트에서 실행 되는 SQL 용 내용은 (예: Linux)를 확인 하려면 [transact-sql&#41;&#40;sys.dm_os_host_info ](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)을 사용 합니다. 
  
## <a name="examples"></a>예  
 다음 예에서는 **sys.dm_os_windows_info** 뷰에서 모든 열을 반환 합니다.  
  
```  
SELECT windows_release, windows_service_pack_level, windows_sku, os_language_version  
FROM sys.dm_os_windows_info;  
```  
  
 결과 집합의 예는 다음과 같습니다.  
  
 `windows_release  windows_service_pack_level   windows_sku   os_language_version`  
  
 `---------------  ---------------------------  ------------  -------------------`  
  
 `6.0              Service Pack 2                4            1033`  
  
## <a name="see-also"></a>참고 항목  
 [sys.dm_os_sys_info&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md)  
  
