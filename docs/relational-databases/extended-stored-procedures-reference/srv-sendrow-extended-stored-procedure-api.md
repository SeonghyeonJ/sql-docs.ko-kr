---
title: srv_sendrow(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_sendrow
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: 0209cfb01c0fa76fdf66dfe806f9d528489cfb79
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85755835"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a>srv_sendrow(확장 저장 프로시저 API)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하세요.  
  
 데이터 행을 클라이언트로 전송합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
```  
  
## <a name="arguments"></a>인수  
 *srvproc*  
 특정 클라이언트 연결에 대한 핸들(이 경우 언어 요청을 수신한 핸들)인 SRV_PROC 구조에 대한 포인터입니다. 이 구조에는 확장 저장 프로시저 API 라이브러리가 애플리케이션과 클라이언트 간 통신 및 데이터를 관리하는 데 사용하는 정보가 들어 있습니다.  
  
## <a name="returns"></a>반환  
 SUCCEED 또는 FAIL  
  
## <a name="remarks"></a>설명  
 클라이언트로 보내는 각 행에 대해 한 번씩 **srv_sendrow** 함수를 호출합니다. **srv_sendmsg**, **srv_status**또는 **srv_senddone**을 사용하여 각각 메시지, 상태 값 또는 완료 상태를 보내기 전에 모든 행을 클라이언트로 보내야 합니다.  
  
 **srv_describe** 를 사용하여 정의되지 않은 열이 포함된 행을 보내면 확장 저장 프로시저 API 애플리케이션에서 정보 오류 메시지를 발생시키고 클라이언트에 FAIL을 반환합니다. 이 경우 행이 전송되지 않습니다.  
  
> [!NOTE]  
>  확장 저장 프로시저 API를 통해서는 컴퓨팅 행을 클라이언트로 보낼 수 없습니다. 또한 **ntext**, **text**또는 **image** 데이터가 있는 행을 클라이언트로 보내는 경우 텍스트 포인터와 텍스트 타임스탬프는 제외됩니다.  
  
> [!IMPORTANT]  
>  확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다. 보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)를 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [srv_describe &#40;확장 저장 프로시저 API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
