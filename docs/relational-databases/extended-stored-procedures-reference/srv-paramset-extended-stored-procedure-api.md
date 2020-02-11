---
title: srv_paramset(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramset
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: c3ec0de44aacbcfb2d4e6b96d7525da900017e01
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253549"
---
# <a name="srv_paramset-extended-stored-procedure-api"></a>srv_paramset(확장 저장 프로시저 API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]대신 CLR 통합을 사용 하세요.  
  
 원격 저장 프로시저 호출 반환 매개 변수의 값을 설정합니다. 이 함수는 **srv_paramsetoutput** 함수로 대체되었습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>인수  
 *srvproc*  
 특정 클라이언트 연결에 대한 핸들(이 경우 원격 저장 프로시저 호출을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다. 이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.  
  
 *n*  
 설정할 매개 변수의 번호를 나타냅니다. 첫 번째 매개 변수는 1입니다.  
  
 *데이터로*  
 원격 저장 프로시저에서 매개 변수를 반환할 때 다시 클라이언트로 전달될 데이터 값에 대한 포인터입니다.  
  
 *길이가*  
 반환할 데이터의 실제 길이를 지정합니다. 매개 변수의 데이터 형식이 상수 길이이고 Null 값을 허용하지 않는 경우(예: *srvbit* 또는 *srvint1*) *len*이 무시됩니다.  
  
## <a name="returns"></a>반환  
 매개 변수 값이 성공적으로 설정된 경우 SUCCEED이고, 그렇지 않으면 FAIL입니다. 현재 원격 저장 프로시저가 없는 경우, *n*번째 원격 저장 프로시저 매개 변수가 없는 경우, 매개 변수가 반환 매개 변수가 아닌 경우 및 *len* 인수가 유효하지 않은 경우 FAIL이 반환됩니다.  
  
 
  *len*이 0이면 NULL이 반환됩니다. 
  *len*을 0으로 설정해야만 클라이언트에 NULL이 반환됩니다.  
  
 매개 변수가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 데이터 형식 중 하나인 경우이 함수는 다음 값을 반환 합니다.  
  
|새 데이터 형식|반환 데이터 길이|  
|--------------------|------------------------|  
|**BITN**|**NULL:** _len_ = 0, DATA = IG, RET = 0<br /><br /> **0:** 해당 없음<br /><br /> **>= 255:** 해당 없음<br /><br /> **<255:** 해당 없음|  
|**BIGVARCHAR**|**NULL:** _len_ = 0, DATA = IG, RET = 1<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = max8k, DATA = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, DATA = valid, RET = 1|  
|**BIGCHAR**|**NULL:** _len_ = 0, DATA = IG, RET = 1<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = max8k, DATA = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, DATA = valid, RET = 1|  
|**BIGBINARY**|**NULL:** _len_ = 0, DATA = IG, RET = 1<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = max8k, DATA = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, DATA = valid, RET = 1|  
|**BIGVARBINARY**|**NULL:** _len_ = 0, DATA = IG, RET = 1<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = max8k, DATA = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, DATA = valid, RET = 1|  
|NCHAR|**NULL:** _len_ = 0, DATA = IG, RET = 1<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = max8k, DATA = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, DATA = valid, RET = 1|  
|NVARCHAR|**NULL:** _len_ = 0, DATA = IG, RET = 1<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = max8k, DATA = valid, RET = 0<br /><br /> **<255:** _len_ = <8k, DATA = valid, RET = 1|  
|**N**|**NULL:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **0:** _len_ = IG, DATA = ig, RET = 0<br /><br /> **>= 255:** _len_ = IG, DATA = ig, RET = 0<br /><br /> 255: _len_ = ig, data = ig, RET = 0 ** \<**|  
|RET = srv_paramset의 반환 값||  
|IG = 값이 무시됨||  
|valid = 데이터에 대한 유효한 포인터||  
  
## <a name="remarks"></a>설명  
 매개 변수에는 원격 저장 프로시저를 사용하여 클라이언트와 애플리케이션 간에 전달되는 데이터가 포함되어 있습니다. 클라이언트는 특정 매개 변수를 반환 매개 변수로 지정할 수 있습니다. 이러한 반환 매개 변수에는 개방형 Data Services 서버 애플리케이션이 다시 클라이언트에 전달하는 값이 포함될 수 있습니다. 반환 매개 변수를 사용하는 것은 참조로 매개 변수를 전달하는 것과 유사합니다.  
  
 반환 매개 변수로 호출되지 않은 매개 변수에 대해서는 반환 값을 설정할 수 없습니다. 
  **srv_paramstatus**를 사용하여 매개 변수가 호출된 방법을 확인할 수 있습니다.  
  
 이 함수는 매개 변수의 반환 값을 설정하지만 실제로 반환 값을 클라이언트에 보내지 않습니다. 
  **srv_paramset**으로 반환 값이 설정되었는지 여부에 관계없이 상태 플래그 SRV_DONE_FINAL이 설정된 상태로 **srv_senddone**을 호출하면 모든 반환 매개 변수가 자동으로 클라이언트에 전달됩니다.  
  
 매개 변수를 사용하여 원격 저장 프로시저를 호출하는 경우 매개 변수를 이름 또는 위치(이름 없음)로 전달할 수 있습니다. 일부 매개 변수는 이름으로 전달하고 일부 매개 변수는 위치로 전달하여 원격 저장 프로시저를 호출하면 오류가 발생합니다. SRV_RPC 처리기는 여전히 호출 되지만 매개 변수가 없는 것 처럼 표시 되 고 **srv_rpcparams** 는 0을 반환 합니다.  
  
> [!IMPORTANT]  
>  확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다. 보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://www.microsoft.com/msrc?rtc=1)를 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [srv_paramsetoutput &#40;확장 저장 프로시저 API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
