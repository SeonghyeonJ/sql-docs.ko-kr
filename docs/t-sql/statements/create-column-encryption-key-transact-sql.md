---
title: CREATE COLUMN ENCRYPTION KEY(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE_COLUMN_ENCRYPTION_KEY_TSQL
- SQL13.SWB.NEWCOLUMNENCRYPTIONKEY.GENERAL.F1
- ENCRYPTION_KEY_TSQL
- CREATE COLUMN ENCRYPTION KEY
- ENCRYPTION KEY
- COLUMN ENCRYPTION KEY
- CREATE_COLUMN_ENCRYPTION_TSQL
- SQL13.SWB.COLUMNENCRYPTIONKEY.GENERAL.F1
- COLUMN_ENCRYPTION_KEY_TSQL
- CREATE COLUMN ENCRYPTION
dev_langs:
- TSQL
helpviewer_keywords:
- Always Encrypted, create column encryption key
- column encryption key, create
- column encryption key
- CREATE COLUMN ENCRYPTION KEY statement
ms.assetid: 517fe745-d79b-4aae-99a7-72be45ea6acb
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 5d3f9e4d405435816378141ba9e4053e8ac77a99
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012807"
---
# <a name="create-column-encryption-key-transact-sql"></a>CREATE COLUMN ENCRYPTION KEY(Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) 또는 [보안 Enclave를 사용한 Always Encrypted](../../relational-databases/security/encryption/always-encrypted-enclaves.md)의 열 암호화 키 메타데이터 개체를 만듭니다. 열 암호화 키 메타데이터 개체에는 열에 있는 데이터를 암호화하는 데 사용되는 열 암호화 키의 암호화된 값이 한 개 또는 두 개 포함되어 있습니다. 각 값은 열 마스터 키를 사용하여 암호화됩니다. 
  
![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 표기 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```syntaxsql
CREATE COLUMN ENCRYPTION KEY key_name   
WITH VALUES  
  (  
    COLUMN_MASTER_KEY = column_master_key_name,   
    ALGORITHM = 'algorithm_name',   
    ENCRYPTED_VALUE = varbinary_literal  
  )   
[, (  
    COLUMN_MASTER_KEY = column_master_key_name,   
    ALGORITHM = 'algorithm_name',   
    ENCRYPTED_VALUE = varbinary_literal  
  ) ]   
[;]  
```  
  
## <a name="arguments"></a>인수  
_key\_name_  
데이터베이스에서 열 암호화 키를 식별하는 이름입니다.  
  
_column\_master\_key\_name_ 열 암호화 키 암호화에 사용되는 사용자 지정 CMK의 이름을 지정합니다.  
  
_algorithm\_name_  
열 암호화 키를 암호화하는 데 사용된 알고리즘의 이름입니다. 시스템 공급자에 대한 알고리즘은 **RSA_OAEP**이어야 합니다.  
  
_varbinary\_literal_  
암호화된 열 암호화 키 값 BLOB입니다.  
  
> [!WARNING]  
>  이 문의 일반 텍스트 열 암호화 키 값은 절대 전달하지 마세요. 그럴 경우 이 기능의 이점을 구성하게 됩니다.  
  
## <a name="remarks"></a>설명  
`CREATE COLUMN ENCRYPTION KEY` 문에는 적어도 한 개 또는 두 개의 값이 포함되어 있어야 합니다. [ALTER COLUMN ENCRYPTION KEY(Transact-SQL)](alter-column-encryption-key-transact-sql.md). `ALTER COLUMN ENCRYPTION KEY` 문을 사용하여 값을 제거할 수도 있습니다.  
  
일반적으로 열 암호화 키는 단 하나의 암호화된 값으로 만들어집니다. 열 마스터 키를 회전시켜 현재 열 마스터 키를 새 열 마스터 키로 바꿔야 하는 경우도 있습니다. 키를 회전시켜야 하는 경우 새 열 마스터 키로 암호화된 열 암호화 키의 새 값을 추가합니다. 회전을 통해 클라이언트 애플리케이션은 열 암호화 키로 암호화된 데이터에 액세스할 수 있을 뿐만 아니라 새 열 마스터 키를 사용할 수 있게 됩니다. 새 마스터 키에 액세스할 권한이 없는 클라이언트 애플리케이션의 Always Encrypted 지원 드라이버는 이전 열 마스터 키로 암호화된 열 암호화 키 값을 사용하여 중요한 데이터에 액세스합니다.  

  
Always Encrypted 지원 암호화 알고리즘은 256비트를 가진 일반 텍스트 값을 요구합니다.  
  
SSMS(SQL Server Management Studio) 또는 PowerShell과 같은 도구를 사용하여 열 마스터 키를 관리하는 것이 좋습니다. 해당 도구는 암호화된 값을 생성하고 자동으로 `CREATE COLUMN ENCRYPTION KEY` 문을 실행하여 열 암호화 키 메타데이터 개체를 만듭니다. [SQL Server Management Studio를 사용하여 Always Encrypted 키 프로비저닝](../../relational-databases/security/encryption/configure-always-encrypted-keys-using-ssms.md) 및 [PowerShell을 사용하여 Always Encrypted 키 프로비저닝](../../relational-databases/security/encryption/configure-always-encrypted-keys-using-powershell.md)을 참조하세요. 

열 마스터 키를 보유한 키 저장소를 캡슐화하는 키 저장소 공급자를 사용하여 프로그래밍 방식으로 열 암호화 키 값을 생성할 수도 있습니다. 자세한 내용은 [Always Encrypted를 사용하여 애플리케이션 개발](../../relational-databases/security/encryption/always-encrypted-client-development.md)을 참조하세요.
  
열 암호화 키에 대한 정보를 보려면 [sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md), [sys.column_encryption_keys&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md), [sys.column_encryption_key_values&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)를 사용합니다.  
  
## <a name="permissions"></a>사용 권한  
**ALTER ANY COLUMN ENCRYPTION KEY** 권한을 요구합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-creating-a-column-encryption-key"></a>A. 열 암호화 키 만들기  
다음 예에서는 `MyCEK`라는 열 암호화 키를 만듭니다.  
  
```sql  
CREATE COLUMN ENCRYPTION KEY MyCEK   
WITH VALUES  
(  
    COLUMN_MASTER_KEY = MyCMK,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x01700000016C006F00630061006C006D0061006300680069006E0065002F006D0079002F003200660061006600640038003100320031003400340034006500620031006100320065003000360039003300340038006100350064003400300032003300380065006600620063006300610031006300284FC4316518CF3328A6D9304F65DD2CE387B79D95D077B4156E9ED8683FC0E09FA848275C685373228762B02DF2522AFF6D661782607B4A2275F2F922A5324B392C9D498E4ECFC61B79F0553EE8FB2E5A8635C4DBC0224D5A7F1B136C182DCDE32A00451F1A7AC6B4492067FD0FAC7D3D6F4AB7FC0E86614455DBB2AB37013E0A5B8B5089B180CA36D8B06CDB15E95A7D06E25AACB645D42C85B0B7EA2962BD3080B9A7CDB805C6279FE7DD6941E7EA4C2139E0D4101D8D7891076E70D433A214E82D9030CF1F40C503103075DEEB3D64537D15D244F503C2750CF940B71967F51095BFA51A85D2F764C78704CAB6F015EA87753355367C5C9F66E465C0C66BADEDFDF76FB7E5C21A0D89A2FCCA8595471F8918B1387E055FA0B816E74201CD5C50129D29C015895CD073925B6EA87CAF4A4FAF018C06A3856F5DFB724F42807543F777D82B809232B465D983E6F19DFB572BEA7B61C50154605452A891190FB5A0C4E464862CF5EFAD5E7D91F7D65AA1A78F688E69A1EB098AB42E95C674E234173CD7E0925541AD5AE7CED9A3D12FDFE6EB8EA4F8AAD2629D4F5A18BA3DDCC9CF7F352A892D4BEBDC4A1303F9C683DACD51A237E34B045EBE579A381E26B40DCFBF49EFFA6F65D17F37C6DBA54AA99A65D5573D4EB5BA038E024910A4D36B79A1D4E3C70349DADFF08FD8B4DEE77FDB57F01CB276ED5E676F1EC973154F86  
);  
GO  
```  
  
### <a name="creating-a-column-encryption-key-with-two-values"></a>2개 값을 사용하여 열 암호화 키 만들기  
다음 예에서는 2개 값을 사용해 `TwoValueCEK`라는 열 암호화 키를 만듭니다.  
  
```sql

CREATE COLUMN ENCRYPTION KEY TwoValueCEK   
WITH VALUES  
(  
    COLUMN_MASTER_KEY = CMK1,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0037006300380061003100310033003400320037003800620037003000630038003100390062003900630039003400360061006600340039006500610030003200650038006200650038003400340065006C33A82ECF04A7185824B4545457AC5244CD9C219E64067B9520C0081B8399B58C2863F7494ABE3694BD87D55FFD7576FFDC47C28F94ECC99577DF4FB8FA19AA95764FEF889CDE0F176DA5897B74382FBB22756CE2921050A09201A0EB6AF3D6091014C30146EA62635EE8CBF0A8074DEDFF125CEA80D1C0F5E8C58750A07D270E2A8BF824EE4C0C156366BF26D38CCE49EBDD5639A2DF029A7DBAE5A5D111F2F2FA3246DF8C2FA83C1E542C10570FADA98F6B29478DC58CE5CBDD407CCEFCDB97814525F6F32BECA266014AC346AC39C4F185C6C0F0A24FEC4DFA015649624692DE7865B9827BA22C3B574C9FD169F822B609F902288C5880EB25F14BD990D871B1BC4BA3A5B237AF76D26354773FA2A25CF4511AF58C911E601CFCB1905128C997844EED056C2AE7F0B48700AB41307E470FF9520997D0EB0D887DE11AFE574FFE845B7DC6C03FEEE8D467236368FC0CB2FDBD54DADC65B10B3DE6C80DF8B7B3F8F3CE5BE914713EE7B1FA5B7A578359592B8A5FDFDDE5FF9F392BC87C3CD02FBA94582AC063BBB9FFAC803FD489E16BEB28C4E3374A8478C737236A0B232F5A9DDE4D119573F1AEAE94B2192B81575AD6F57E670C1B2AB91045124DFDAEC2898F3F0112026DFC93BF9391D667D1AD7ED7D4E6BB119BBCEF1D1ADA589DD3E1082C3DAD13223BE438EB9574DA04E9D8A06320CAC6D3EC21D5D1C2A0AA484C7C  
),  
(  
    COLUMN_MASTER_KEY = CMK2,   
    ALGORITHM = 'RSA_OAEP',   
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E00740075007300650072002F006D0079002F0064006500650063006200660034006100340031003000380034006200350033003200360066003200630062006200350030003600380065003900620061003000320030003600610037003800310066001DDA6134C3B73A90D349C8905782DD819B428162CF5B051639BA46EC69A7C8C8F81591A92C395711493B25DCBCCC57836E5B9F17A0713E840721D098F3F8E023ABCDFE2F6D8CC4339FC8F88630ED9EBADA5CA8EEAFA84164C1095B12AE161EABC1DF778C07F07D413AF1ED900F578FC00894BEE705EAC60F4A5090BBE09885D2EFE1C915F7B4C581D9CE3FDAB78ACF4829F85752E9FC985DEB8773889EE4A1945BD554724803A6F5DC0A2CD5EFE001ABED8D61E8449E4FAA9E4DD392DA8D292ECC6EB149E843E395CDE0F98D04940A28C4B05F747149B34A0BAEC04FFF3E304C84AF1FF81225E615B5F94E334378A0A888EF88F4E79F66CB377E3C21964AACB5049C08435FE84EEEF39D20A665C17E04898914A85B3DE23D56575EBC682D154F4F15C37723E04974DB370180A9A579BC84F6BC9B5E7C223E5CBEE721E57EE07EFDCC0A3257BBEBF9ADFFB00DBF7EF682EC1C4C47451438F90B4CF8DA709940F72CFDC91C6EB4E37B4ED7E2385B1FF71B28A1D2669FBEB18EA89F9D391D2FDDEA0ED362E6A591AC64EF4AE31CA8766C259ECB77D01A7F5C36B8418F91C1BEADDD4491C80F0016B66421B4B788C55127135DA2FA625FB7FD195FB40D90A6C67328602ECAF3EC4F5894BFD84A99EB4753BE0D22E0D4DE6A0ADFEDC80EB1B556749B4A8AD00E73B329C95827AB91C0256347E85E3C5FD6726D0E1FE82C925D3DF4A9  
);  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
[ALTER COLUMN ENCRYPTION KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-column-encryption-key-transact-sql.md)   
[DROP COLUMN ENCRYPTION KEY&#40;Transact-SQL&#41;](../../t-sql/statements/drop-column-encryption-key-transact-sql.md)   
[CREATE COLUMN MASTER KEY&#40;Transact-SQL&#41;](../../t-sql/statements/create-column-master-key-transact-sql.md)   
[sys.column_encryption_keys&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)   
[sys.column_encryption_key_values&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-encryption-key-values-transact-sql.md)   
[sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)  
[Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md)   
[보안 enclave를 사용한 Always Encrypted](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
[Always Encrypted를 위한 키 관리 개요](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)   
[보안 Enclave를 사용한 Always Encrypted 키 관리](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)   
  
  
