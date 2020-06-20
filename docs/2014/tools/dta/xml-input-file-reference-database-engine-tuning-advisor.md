---
title: XML 입력 파일 참조(데이터베이스 엔진 튜닝 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database Engine Tuning Advisor [SQL Server], XML input files
- input file reference [Database Engine Tuning Advisor]
- XML input files [Database Engine Tuning Advisor]
ms.assetid: 05e5e5f0-d6df-4336-b18e-e9bc2835a766
author: stevestein
ms.author: sstein
ms.openlocfilehash: b7712605a27a5cec798633bf9846a23a31e95a17
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85057723"
---
# <a name="xml-input-file-reference-database-engine-tuning-advisor"></a>XML 입력 파일 참조(데이터베이스 엔진 튜닝 관리자)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자는 XML 입력 파일을 사용하여 데이터베이스를 튜닝할 수 있습니다. 이 XML 파일은 튜닝 세션에 사용할 데이터베이스, 테이블, 작업 파일 또는 테이블 및 튜닝 옵션을 지정합니다. 또한 이 파일을 사용하면 "가정(what-if)" 분석을 수행하기 위한 사용자 지정 구성을 지정할 수 있습니다.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 입력 파일은 튜닝 세션 설정을 지정하는 텍스트 또는 기타 요소가 각각 포함되어 있는 XML 요소의 계층을 포함합니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 입력 파일은 올바른 형식의 XML에 대한 표준을 따라야 하므로 모든 요소 이름이 대/소문자를 구분합니다. 요소는 파스칼 대/소문자를 사용하여 지정하는 데 이는 첫 글자가 대문자이고 이후의 모든 연결 단어의 첫 글자가 대문자라는 것을 의미합니다.  
  
 모든 요소 값은 XML 명명 규칙을 따라야 합니다. 이러한 규칙에 대한 자세한 내용은 MSDN Library에서 [XML 텍스트 콘텐츠(XML Textual Content)](https://go.microsoft.com/fwlink/?LinkId=7614) 를 참조하십시오.  
  
 이 참조에서 전체 내용을 다루지는 않습니다. XML 입력을 정의하는 데 사용할 수 있는 모든 요소에 대한 자세한 내용은 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 튜닝 관리자 XML 스키마 DTASchema.xsd를 참조하십시오.  
  
## <a name="xml-declaration"></a>XML 선언  
  
-   [XML 데이터&#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md)  
  
## <a name="dtaxml-root-element"></a>DTAXML 루트 요소  
  
-   [DTAXML 요소&#40;DTA&#41;](dtaxml-element-dta.md)  
  
## <a name="dtainput-elements"></a>DTAInput 요소  
  
-   [DTAInput 요소&#40;DTA&#41;](dtainput-element-dta.md)  
  
-   [Server 요소&#40;DTA&#41;](server-element-dta.md)  
  
-   [Workload 요소&#40;DTA&#41;](workload-element-dta.md)  
  
-   [TuningOptions 요소&#40;DTA&#41;](tuningoptions-element-dta.md)  
  
-   [Configuration 요소&#40;DTA&#41;](configuration-element-dta.md)  
  
## <a name="server-elements"></a>Server 요소  
  
-   [Server의 Name 요소&#40;DTA&#41;](name-element-for-server-dta.md)  
  
-   [Server의 Database 요소&#40;DTA&#41;](database-element-for-server-dta.md)  
  
## <a name="workload-elements"></a>Workload 요소  
  
-   [File 요소&#40;DTA&#41;](file-element-dta.md)  
  
-   [Workload의 Database 요소&#40;DTA&#41;](database-element-for-workload-dta.md)  
  
-   [EventString 요소&#40;DTA&#41;](eventstring-element-dta.md)  
  
## <a name="tuning-options-elements"></a>튜닝 옵션 요소  
  
-   [TuningTimeInMin 요소&#40;DTA&#41;](tuningtimeinmin-element-dta.md)  
  
-   [StorageBoundInMB 요소&#40;DTA&#41;](storageboundinmb-element-dta.md)  
  
-   [TestServer 요소&#40;DTA&#41;](testserver-element-dta.md)  
  
-   [FeatureSet 요소&#40;DTA&#41;](featureset-element-dta.md)  
  
-   [Partitioning 요소&#40;DTA&#41;](partitioning-element-dta.md)  
  
-   [DropOnlyMode 요소&#40;DTA&#41;](droponlymode-element-dta.md)  
  
-   [KeepExisting 요소&#40;DTA&#41;](keepexisting-element-dta.md)  
  
-   [OnlineIndexOperation 요소&#40;DTA&#41;](onlineindexoperation-element-dta.md)  
  
-   [DatabaseToConnect 요소&#40;DTA&#41;](databasetoconnect-element-dta.md)  
  
## <a name="configuration-elements"></a>Configuration 요소  
  
-   [Configuration의 Server 요소&#40;DTA&#41;](server-element-for-configuration-dta.md)  
  
-   [Configuration의 Database 요소&#40;DTA&#41;](database-element-for-configuration-dta.md)  
  
-   [Recommendation 요소&#40;DTA&#41;](recommendation-element-dta.md)  
  
-   [Create 요소&#40;DTA&#41;](create-element-dta.md)  
  
-   [Index 요소&#40;DTA&#41;](index-element-dta.md)  
  
-   [Index의 Name 요소&#40;DTA&#41;](name-element-for-index-dta.md)  
  
-   [Index의 Column 요소&#40;DTA&#41;](column-element-for-index-dta.md)  
  
-   [Column의 Name 요소&#40;DTA&#41;](name-element-for-column-dta.md)  
  
-   [Index의 Filegroup 요소&#40;DTA&#41;](filegroup-element-for-index-dta.md)  
  
## <a name="database-elements"></a>Database 요소  
  
-   [Database의 Name 요소&#40;DTA&#41;](name-element-for-database-dta.md)  
  
-   [Database의 Schema 요소&#40;DTA&#41;](schema-element-for-database-dta.md)  
  
-   [Schema의 Name 요소&#40;DTA&#41;](name-element-for-schema-dta.md)  
  
-   [Schema의 Table 요소&#40;DTA&#41;](table-element-for-schema-dta.md)  
  
-   [Table의 Name 요소&#40;DTA&#41;](name-element-for-table-dta.md)  
  
## <a name="see-also"></a>참고 항목  
 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
