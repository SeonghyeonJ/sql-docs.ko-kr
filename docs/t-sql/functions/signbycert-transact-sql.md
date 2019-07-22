---
title: SIGNBYCERT(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SIGNBYCERT
- SIGNBYCERT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- text signing [SQL Server]
- encryption [SQL Server], certificates
- certificates [SQL Server], text signing
- SignByCert function
- signing text [SQL Server]
- SIGNBYCERT function
- cryptography [SQL Server], certificates
ms.assetid: b4c6bced-4473-4bae-85b9-56deced495f9
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 56d4af001c84fd4f175c0c2504bef39a12015e7d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139138"
---
# <a name="signbycert-transact-sql"></a>SIGNBYCERT(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  인증서를 사용하여 일반 텍스트에 서명하고 서명을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
SignByCert ( certificate_ID , @cleartext [ , 'password' ] )  
```  
  
## <a name="arguments"></a>인수  
 *certificate_ID*  
 현재 데이터베이스에 있는 인증서 ID입니다. *certificate*_ID는 **int**입니다.  
  
 *@cleartext*  
 서명될 데이터가 들어 있는 **nvarchar**, **char**, **varchar** 또는 **nchar** 형식의 변수입니다.  
  
 **'** *password* **'**  
 인증서 프라이빗 키를 암호화할 때 사용한 암호입니다. *암호*는 **nvarchar(128)** 입니다.  
  
## <a name="return-types"></a>반환 형식  
 최대 크기가 8,000바이트인 **varbinary**입니다.  
  
## <a name="remarks"></a>Remarks  
 인증서에 대한 CONTROL 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `@SensitiveData` 인증서를 사용하여 `ABerglundCert07`의 텍스트에 서명합니다. 이 인증서는 먼저 암호 "pGFD4bb925DGvbd2439587y"를 사용하여 해독해야 합니다. 그런 다음 `SignedData04` 테이블에 일반 텍스트와 서명을 삽입합니다.  
  
```  
DECLARE @SensitiveData nvarchar(max);  
SET @SensitiveData = N'Saddle Price Points are   
    2, 3, 5, 7, 11, 13, 17, 19, 23, 29';  
INSERT INTO [SignedData04]  
    VALUES( N'data signed by certificate ''ABerglundCert07''',  
    @SensitiveData, SignByCert( Cert_Id( 'ABerglundCert07' ),   
    @SensitiveData, N'pGFD4bb925DGvbd2439587y' ));  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [VERIFYSIGNEDBYCERT &#40;Transact-SQL&#41;](../../t-sql/functions/verifysignedbycert-transact-sql.md)   
 [CERT_ID &#40;Transact-SQL&#41;](../../t-sql/functions/cert-id-transact-sql.md)   
 [CREATE CERTIFICATE&#40;Transact-SQL&#41;](../../t-sql/statements/create-certificate-transact-sql.md)   
 [ALTER CERTIFICATE&#40;Transact-SQL&#41;](../../t-sql/statements/alter-certificate-transact-sql.md)   
 [DROP CERTIFICATE&#40;Transact-SQL&#41;](../../t-sql/statements/drop-certificate-transact-sql.md)   
 [암호화 계층](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
