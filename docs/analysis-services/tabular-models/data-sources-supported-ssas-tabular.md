---
title: SQL Server Analysis Services 테이블 형식 1200 모델에서 지 원하는 데이터 원본 | Microsoft Docs
ms.date: 11/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 49c63d205d2ce1b900f3b8d4ad9a08e3bf83e2f6
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269686"
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1200-models"></a>테이블 형식 1200 모델 SQL Server Analysis Services에서 지 원하는 데이터 원본
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  
이 문서 보다 낮은 호환성 수준 1200에서 테이블 형식 모델 SQL Server Analysis Services와 사용할 수 있는 데이터 원본의 형식을 설명 합니다. 

1400 호환성 수준의 모델에 대 한 참조 [SQL Server Analysis Services 테이블 형식 1400 모델에서 지 원하는 데이터 원본](data-sources-supported-ssas-tabular-1400.md)합니다.

Azure Analysis Services에 대 한 참조 [Azure Analysis Services에서 지 원하는 데이터 원본](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)합니다.
  
##  <a name="bkmk_supported_ds"></a> 메모리 내 테이블 형식 모델에 대 한 지원 되는 데이터 원본  
[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]를 설치할 경우 각 데이터 원본에 대해 나열된 공급자는 설치되지 않습니다. 일부 공급자는 컴퓨터에 다른 응용 프로그램을 사용 하 여 설치할 수 있습니다. 다른 경우를 다운로드 하 여 공급자를 설치 해야 합니다.  
  
|||||  
|-|-|-|-|  
|원본|버전|파일 유형|공급자|  
|Access 데이터베이스|Microsoft Access 2010 이상|.accdb 또는 .mdb|ACE 14 OLE DB provider <sup> [1](#dnu)</sup>|  
|SQL Server 관계형 데이터베이스|SQL Server 2008 이상, SQL Server 데이터 웨어하우스 2008 및 이후, Azure SQL Database, Azure SQL Data Warehouse, Analytics Platform System (APS)<br /><br /> <br /><br /> Analytics Platform System (APS) SQL Server 병렬 데이터 웨어하우스 (PDW) 명칭은 였습니다. 원래는 PDW에서 Analysis Services에 연결하려면 특수한 데이터 공급자가 필요했습니다. 이 공급자는 SQL Server 2012에서 바뀌었습니다. SQL Server 2012부터는 PDW/APS에 대한 연결에 SQL Server Native Client가 사용됩니다. |(해당 사항 없음)|OLE DB Provider for SQL Server<br /><br /> SQL Server Native Client OLE DB 공급자<br /><br /> SQL Server Native 10.0 Client OLE DB 공급자<br /><br /> .NET Framework Data Provider for SQL Client|  
|Oracle 관계형 데이터베이스|Oracle 9i 이상.|(해당 사항 없음)|Oracle OLE DB 공급자<br /><br /> .NET Framework Data Provider for Oracle Client<br /><br /> .NET Framework Data Provider for SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Teradata 관계형 데이터베이스|Teradata V2R6 이상|(해당 사항 없음)|TDOLEDB OLE DB 공급자<br /><br /> .Net Data Provider for Teradata|  
|Informix 관계형 데이터베이스||(해당 사항 없음)|Informix OLE DB 공급자|  
|IBM DB2 관계형 데이터베이스|8.1|(해당 사항 없음)|DB2OLEDB|  
|Sybase 적응형 Server Enterprise (ASE) 관계형 데이터베이스|15.0.2|(해당 사항 없음)|Sybase OLE DB 공급자|  
|기타 관계형 데이터베이스|(해당 사항 없음)|(해당 사항 없음)|OLE DB 공급자 또는 ODBC 드라이버|  
|텍스트 파일|(해당 사항 없음)|.txt, .tab, .csv|ACE 14 OLE DB provider <sup> [1](#dnu)</sup> |  
|Microsoft Excel 파일|Excel 2010 이상|.xlsx, xlsm, .xlsb, .xltx, .xltm|ACE 14 OLE DB provider <sup> [1](#dnu)</sup>|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서(workbook)|Microsoft SQL Server 2008 이상 Analysis Services|.xlsx, xlsm, .xlsb, .xltx, .xltm|ASOLEDB 10.5<br /><br /> ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 가 설치된 SharePoint 팜에 게시된 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 통합 문서에만 사용)|  
|Analysis Services 큐브|Microsoft SQL Server 2008 이상 Analysis Services|(해당 사항 없음)|ASOLEDB 10|  
|데이터 피드<br /><br /> (Reporting Services 보고서, Atom 서비스 문서, Microsoft Azure Marketplace DataMarket 및 단일 데이터 피드에서 데이터를 가져오는 데 사용됨)|Atom 1.0 형식<br /><br /> 모든 데이터베이스 또는 WCF(Windows Communication Foundation) 데이터 서비스(이전 ADO.NET Data Services)로 노출되는 문서입니다.|`.atomsvc` 하나 이상의 피드를 정의 하는 서비스 문서에 대 한<br /><br /> Atom 웹 피드 문서용 .atom|Microsoft Data Feed Provider for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> .NET Framework 데이터 피드 데이터 공급자 - [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Office 데이터베이스 연결 파일||.odc||  
 
<a name="dnu">[1] </a> 사용 하 여 **ACE 14 OLE DB 공급자** 파일 데이터 형식에 연결할 **좋지 않습니다**합니다. 테이블 형식 1200 및 낮은 호환성 수준 모델을 유지 해야 하는 경우 csv 파일 형식으로 데이터를 내보낼 SQL database로 가져오기 및 다음에 연결한 후 데이터베이스에서 가져옵니다. 그러나 것이 좋습니다 (SQL Server 2017 이상) 테이블 형식 1400 호환성 수준으로 업그레이드 하 고 사용 하 여 **데이터 가져오기** 를 선택 하 여 파일 데이터 원본을 가져올 SSDT에서 합니다. 데이터는 구조화 된 데이터 원본 연결을 파워 쿼리 데이터 엔진에 의해 제공 된 ACE 14 OLE DB 공급자 연결 보다 더 안정 된를 가져옵니다.  


##  <a name="bkmk_supported_ds_dq"></a> DirectQuery 모델에 대해 지원되는 데이터 원본  
 메모리 내 스토리지 모드 대신 사용할 수 있는 DirectQuery는 모든 데이터를 모델 내에 저장하고 모델이 로드된 후에는 모든 데이터를 RAM에 저장하는 대신 백 엔드 데이터 시스템으로 쿼리를 라우팅하고 결과를 해당 시스템에서 직접 반환합니다. Analysis Services 네이티브 데이터베이스 쿼리 구문에서 쿼리를 작성 하는 데 있어이 모드에 대 한 데이터 원본 중 일부만 사용할 수 있습니다.  
  
데이터 원본   |버전  |공급자
---------|---------|---------
Microsoft SQL Server    |  2008 이상      |       OLE DB Provider for SQL Server, SQL Server Native Client OLE DB 공급자, .NET Framework Data Provider for SQL Client  
Microsoft Azure SQL Database    |   All      |  OLE DB Provider for SQL Server, SQL Server Native Client OLE DB 공급자, .NET Framework Data Provider for SQL Client            
Microsoft Azure SQL Data Warehouse     |   All     |  SQL Server Native Client OLE DB 공급자, .NET Framework Data Provider for SQL Client       
Microsoft SQL APS(분석 플랫폼 시스템)     |   All      |  OLE DB Provider for SQL Server, SQL Server Native Client OLE DB 공급자, .NET Framework Data Provider for SQL Client       
Oracle 관계형 데이터베이스     |  Oracle 9i 이상       |  Oracle OLE DB 공급자       
Teradata 관계형 데이터베이스    |  Teradata V2R6 이상     | .Net Data Provider for Teradata    

  
##  <a name="bkmk_tips"></a> 데이터 원본 선택 시 유용한 정보  
  
모델 디자이너에서 테이블 간의 관계를 만들기 위해 가져오기를 수행하는 동안 *외래 키* 관계를 사용하기 때문에 관계형 데이터베이스에서 테이블을 가져오면 작업 단계가 줄어듭니다.  
  
여러 테이블을 가져온 다음 필요 없는 테이블을 삭제하여 작업 단계를 줄일 수도 있습니다. 테이블을 한 번에 하나씩 가져오는 경우 테이블 간의 관계를 수동으로 만들어야 할 수 있습니다.  
  
여러 데이터 원본의 유사 데이터를 포함하는 열은 모델 디자이너에서 관계를 만들 때 기반이 됩니다. 다른 유형의 데이터 원본을 사용하는 경우 동일하거나 비슷한 데이터가 포함되어 있는 다른 데이터 원본의 테이블에 매핑할 수 있는 열이 있는 테이블을 선택하십시오.  
  
OLE DB 공급자는 대규모 데이터에 대 한 성능 향상을 제공할 경우에 따라 수 있습니다. 동일한 데이터 원본에 대해 여러 공급자 중에서 하나를 선택하는 경우 OLE DB 공급자를 먼저 사용해 보는 것이 좋습니다.  

## <a name="see-also"></a>참고자료

[1400 테이블 형식 모델 SQL Server Analysis Services에서 지 원하는 데이터 원본](data-sources-supported-ssas-tabular-1400.md)

[Azure Analysis Services에서 지 원하는 데이터 원본](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   
