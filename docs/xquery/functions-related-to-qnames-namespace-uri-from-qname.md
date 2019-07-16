---
title: 네임 스페이스-uri-에서-QName (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri-from-QName function
- namespace-uri-from-QName function
ms.assetid: 4ab3f003-2a3b-4268-9e88-b615e35701b2
author: rothja
ms.author: jroth
ms.openlocfilehash: 96edefd5409520109e2b2155507dd8879ed4b0d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946625"
---
# <a name="functions-related-to-qnames---namespace-uri-from-qname"></a>QNames 관련 함수 - namespace-uri-from-QName
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  지정 된 QName의 네임 스페이스 uri를 나타내는 문자열을 반환 *$arg*합니다. 결과 빈 시퀀스가 *$arg* 빈 시퀀스입니다.  
  
## <a name="syntax"></a>구문  
  
```  
namespace-uri-from-QName($arg as xs:QName?) as xs:string?  
```  
  
## <a name="arguments"></a>인수  
 *$arg*  
 네임스페이스 URI가 반환되는 QName입니다.  
  
## <a name="examples"></a>예  
 이 항목에서는 다양 한 저장 된 XML 인스턴스에 대 한 XQuery 예를 제공 **xml** AdventureWorks 데이터베이스의 열을 입력 합니다.  
  
### <a name="a-retrieve-the-namespace-uri-from-a-qname"></a>A. QName에서 네임스페이스 URI 검색  
 작업 샘플을 보려면 [QName의 로컬 이름 &#40;XQuery&#41;](../xquery/functions-related-to-qnames-local-name-from-qname.md)합니다.  
  
### <a name="implementation-limitations"></a>구현 시 제한 사항  
 제한 사항은 다음과 같습니다.  
  
-   합니다 **namespace-uri-from-qname ()** 함수는 xs: anyuri 대신 xs: string의 인스턴스를 반환 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [QNames 관련 함수 &#40;XQuery&#41;](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
