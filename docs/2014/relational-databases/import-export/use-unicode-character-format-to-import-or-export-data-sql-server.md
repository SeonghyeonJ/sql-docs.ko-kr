---
title: 유니코드 문자 형식을 사용하여 데이터 가져오기 및 내보내기(SQL Server) | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- data formats [SQL Server], Unicode character
- Unicode [SQL Server], bulk importing and exporting
ms.assetid: 74342a11-c1c0-4746-b482-7f3537744a70
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 85df40b07542e1af144796d4e8b5f9fb33cdc7c9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63065769"
---
# <a name="use-unicode-character-format-to-import-or-export-data-sql-server"></a>유니코드 문자 형식을 사용하여 데이터 가져오기 및 내보내기(SQL Server)
  확장/DBCS 문자를 포함하는 데이터 파일을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 여러 인스턴스 간에 대량 데이터 전송을 수행하는 경우에는 유니코드 문자 형식을 사용하는 것이 좋습니다. 유니코드 문자 데이터 형식을 사용하면 작업을 수행 중인 클라이언트에서 사용되는 코드 페이지와 다른 코드 페이지를 사용하여 서버에서 데이터를 내보낼 수 있습니다. 이런 경우 유니코드 문자 형식을 사용하면 다음과 같은 이점이 있습니다.  
  
-   원본 및 대상 데이터가 유니코드 데이터 형식이면 유니코드 문자 형식을 사용하여 모든 문자 데이터를 보존할 수 있습니다.  
  
-   원본 및 대상 데이터가 유니코드 데이터 형식이 아니면 유니코드 문자 형식을 사용하여 원본 데이터에 있지만 대상에서 표현할 수 없는 확장 문자의 손실을 최소화할 수 있습니다.  
  
 유니코드 문자 형식 데이터 파일은 유니코드 파일의 규칙을 따릅니다. 파일의 처음 두 바이트는 16진수 0xFFFE입니다. 이 두 바이트는 바이트 순서 표시로서 제공되며 높은 순서 바이트가 파일의 처음에 저장될지 마지막에 저장될지를 지정합니다.  
  
> [!IMPORTANT]  
>  유니코드 문자 데이터 파일에 서식 파일을 사용하려면 모든 입력 필드가 유니코드 텍스트 문자열(고정 크기 또는 문자 종료 유니코드 문자열)이어야 합니다.  
  
 유니코드 문자 형식 데이터 파일에 저장되어 있는 `sql_variant` 데이터는 데이터가 `nchar` 데이터 대신 `char`로 저장된다는 것을 제외하면 문자 형식 데이터 파일과 같은 방식으로 작동합니다. 문자 형식에 대한 자세한 내용은 [Collation and Unicode Support](../collations/collation-and-unicode-support.md)을 참조하십시오.  
  
 유니코드 문자 형식으로 제공되는 기본값과 다른 필드 또는 행 종결자를 사용하려면 [필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)을 참조하세요.  
  
## <a name="command-options-for-unicode-character-format"></a>유니코드 문자 형식의 명령 옵션  
 **bcp**, BULK INSERT 또는 INSERT... SELECT \* FROM OPENROWSET(BULK...)를 사용하여 테이블로 유니코드 원시 형식 데이터를 가져올 수 있습니다. **bcp** 명령 또는 BULK INSERT 문의 경우 명령줄에서 데이터 형식을 지정할 수 있습니다. INSERT ... SELECT * FROM OPENROWSET(BULK...) 문의 경우 서식 파일에서 데이터 형식을 지정해야 합니다.  
  
 다음 명령줄 옵션에서 유니코드 문자 형식을 사용할 수 있습니다.  
  
|Command|옵션|Description|  
|-------------|------------|-----------------|  
|**bcp**|**-w**|유니코드 문자 형식을 사용합니다.|  
|BULK INSERT|DATAFILETYPE **='** widechar **'**|대량으로 데이터를 가져올 때 유니코드 문자 형식을 사용합니다.|  
  
 자세한 내용은 [bcp 유틸리티](../../tools/bcp-utility.md), [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) 또는 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)를 참조하세요.  
  
> [!NOTE]  
>  서식 파일에서 필드 단위로 서식을 지정할 수도 있습니다. 자세한 내용은 [데이터를 가져오거나 내보내기 위한 서식 파일&#40;SQL Server&#41;](format-files-for-importing-or-exporting-data-sql-server.md)을 참조하세요.  
  
## <a name="examples"></a>예  
 다음 예에서는 **bcp** 를 사용하여 유니코드 문자 데이터를 대량으로 내보내는 방법과 BULK INSERT를 사용하여 동일한 데이터를 대량으로 가져오는 방법을 보여 줍니다.  
  
### <a name="sample-table"></a>예제 테이블  
 이 예에서는 `myTestUniCharData` 스키마의 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 예제 데이터베이스에 생성된 `dbo` 라는 테이블이 필요하며 예를 실행하려면 이 테이블을 만들어야 합니다. 이 테이블을 만들려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE myTestUniCharData (  
   Col1 smallint,  
   Col2 nvarchar(50),  
   Col3 nvarchar(50)  
   );   
```  
  
 이 테이블을 채우고 결과 내용을 확인하려면 다음 문을 실행합니다.  
  
```  
INSERT INTO myTestUniCharData(Col1,Col2,Col3)  
   VALUES(1,'DataField2','DataField3')   
        ,(2,'DataField2','DataField3');  
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
  
```  
  
### <a name="using-bcp-to-bulk-export-unicode-character-data"></a>bcp를 사용하여 유니코드 문자 데이터 대량 내보내기  
 테이블의 데이터를 데이터 파일로 내보내려면 **out** 옵션 및 다음 한정자가 있는 **bcp** 를 사용합니다.  
  
|한정자|Description|  
|----------------|-----------------|  
|**-w**|유니코드 문자 형식을 지정합니다.|  
|**-t** `,`|쉼표(`,`)를 필드 종결자로 지정합니다.<br /><br /> 참고: 기본 필드 종결자는 탭 유니코드 문자 (\t)입니다. 자세한 내용은 [필드 및 행 종결자 지정&#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)을 참조하세요.|  
|**-T**|**bcp** 유틸리티가 통합 보안을 사용하는 트러스트된 연결을 통해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로 연결되도록 지정합니다. **-T**를 지정하지 않은 경우 성공적으로 로그인하려면 **-U**와 **-P**를 지정해야 합니다.|  
  
 다음 예에서는 `myTestUniCharData` 테이블의 유니코드 문자 형식 데이터를 필드 종결자로 쉼표(`myTestUniCharData-w.Dat`)를 사용하는 새 데이터 파일인 `,`로 대량으로 내보냅니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 명령 프롬프트에 다음을 입력합니다.  
  
```  
bcp AdventureWorks2012..myTestUniCharData out C:\myTestUniCharData-w.Dat -w -t, -T  
  
```  
  
### <a name="using-bulk-insert-to-bulk-import-unicode-character-data"></a>BULK INSERT를 사용하여 유니코드 문자 데이터 대량 가져오기  
 다음 예에서는 `BULK INSERT`를 사용하여 `myTestUniCharData-w.Dat` 데이터 파일의 데이터를 `myTestUniCharData` 테이블로 가져옵니다. 기본 필드 종결자(`,`)가 아닌 필드 종결자는 문에서 선언해야 합니다. [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 쿼리 편집기에서 다음을 실행합니다.  
  
```  
USE AdventureWorks2012;  
GO  
BULK INSERT myTestUniCharData   
   FROM 'C:\myTestUniCharData-w.Dat'   
   WITH (  
      DATAFILETYPE='widechar',  
      FIELDTERMINATOR=','  
   );   
GO  
SELECT Col1,Col2,Col3 FROM myTestUniCharData;  
GO  
  
```  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
 **대량 가져오기 또는 대량 내보내기를 위한 데이터 형식을 사용하려면**  
  
-   [SQL Server 이전 버전으로부터 기본 및 문자 형식 데이터 가져오기](import-native-and-character-format-data-from-earlier-versions-of-sql-server.md)  
  
-   [문자 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [원시 형식을 사용하여 데이터 가져오기 또는 내보내기&#40;SQL Server&#41;](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [데이터를 가져오거나 내보내기 위해 유니코드 원시 형식 사용&#40;SQL Server&#41;](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
## <a name="see-also"></a>관련 항목  
 [bcp Utility](../../tools/bcp-utility.md)   
 [BULK INSERT&#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [OPENROWSET&#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [데이터 형식&#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [Collation and Unicode Support](../collations/collation-and-unicode-support.md)  
  
  
