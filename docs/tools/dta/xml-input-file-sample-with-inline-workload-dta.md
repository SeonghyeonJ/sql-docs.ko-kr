---
title: 인라인 워크로드가 포함된 XML 입력 파일 샘플
titleSuffix: DTA
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: b12c6f285a7c9eb1e32c33332b00ec624092c3c6
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75258025"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a>인라인 작업이 포함된 XML 입력 파일 예제(DTA)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**EventString** 요소를 사용하여 작업을 지정하는 XML 입력 파일의 이 예제를 복사한 다음 자주 사용하는 XML 편집기나 텍스트 편집기에 붙여넣습니다. **EventString** 요소를 사용하면 별개의 작업 파일을 사용하는 대신에 XML 입력 파일에 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트 작업을 지정할 수 있습니다. 이 예제를 편집 도구에 복사한 후에 **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**및 **TuningOptions** 요소에 지정된 값을 특정 튜닝 세션에 대한 값으로 바꿉니다. 이러한 요소에 사용할 수 있는 모든 특성 및 자식 요소에 대한 자세한 내용은 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)를 참조하세요. 다음 예에서는 사용 가능한 특성 및 자식 요소 옵션의 하위 집합만 사용합니다.

## <a name="code"></a>코드

[!code-xml[InputFileSamples#InlineWorkloadInputFile](../../tools/dta/codesnippet/xml/xml-input-file-sample-wi_1.xml)]

## <a name="comments"></a>주석

`USE database_name` EventString **요소에 포함된 인라인 작업에서** 문을 지정할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [데이터베이스 엔진 튜닝 관리자 시작 및 사용](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)
- [데이터베이스 엔진 튜닝 관리자의 출력 보기 및 작업](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md)
- [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)