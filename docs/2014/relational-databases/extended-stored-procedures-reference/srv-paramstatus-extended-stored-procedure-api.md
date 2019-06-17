---
title: srv_paramstatus(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramstatus
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramstatus
ms.assetid: 86cecd45-0b09-42e9-8152-32a12a1c2b7a
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 57e5ed3215391d3a1b134db471e2f4f0393f4443
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127122"
---
# <a name="srvparamstatus-extended-stored-procedure-api"></a>srv_paramstatus(확장 저장 프로시저 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하세요.  
  
 특정 원격 저장 프로시저 호출 매개 변수의 상태를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
int srv_paramstatus (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
  
```  
  
## <a name="arguments"></a>인수  
 *srvproc*  
 특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다. 이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.  
  
 *n*  
 매개 변수의 번호를 나타냅니다. 첫 번째 매개 변수의 번호는 1입니다.  
  
## <a name="returns"></a>반환 값  
 매개 변수의 상태 플래그가 들어 있는 `int`입니다. 현재는 플래그가 하나만 있습니다. 0 비트가 1로 설정 된 경우 반환 매개 변수가입니다. *n*번째 매개 변수가 없거나 원격 저장 프로시저가 없으면 -1이 반환됩니다.  
  
## <a name="remarks"></a>Remarks  
 이 루틴은 원격 저장 프로시저 호출 매개 변수의 상태 플래그를 반환합니다.  
  
 매개 변수에는 원격 저장 프로시저를 사용하여 클라이언트와 애플리케이션 간에 전달되는 데이터가 포함되어 있습니다. 클라이언트는 특정 매개 변수를 반환 매개 변수로 지정할 수 있습니다. 이러한 반환 매개 변수에는 애플리케이션이 다시 클라이언트에 전달하는 값이 포함될 수 있습니다.  
  
 현재 유일한 상태 플래그는 매개 변수가 반환 매개 변수인지 여부를 나타내는 상태 플래그입니다.  
  
 매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다. 일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다. 오류가 발생해도 SRV_RPC 처리기는 계속 호출되지만 매개 변수가 없는 것과 같이 처리되며 **srv_rpcparams** 는 0을 반환합니다.  
  
> [!IMPORTANT]  
>  확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다. 보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409 https://msdn.microsoft.com/security/)를 참조하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [srv_rpcparams(확장 저장 프로시저 API)](srv-rpcparams-extended-stored-procedure-api.md)  
  
  
