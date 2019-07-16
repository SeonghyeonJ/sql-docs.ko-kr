---
title: Open 메서드 (ADO 레코드) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_Open
- _Record::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: ab79a623-88a9-40b6-a017-a658bf19b778
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97c7f1c143c83dd35ca5ff17e9776d79fb734ff9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67917918"
---
# <a name="open-method-ado-record"></a>Open 메서드(ADO 레코드)
기존 열립니다 [레코드](../../../ado/reference/ado-api/record-object-ado.md) 개체 또는 새 항목으로 표시를 **레코드**, 예: 파일 또는 디렉터리입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Open Source, ActiveConnection, Mode, CreateOptions, Options, UserName, Password  
```  
  
#### <a name="parameters"></a>매개 변수  
 *원본*  
 (선택 사항) A **Variant** 이 표시 될 엔터티의 URL을 나타낼 수는 **레코드** 개체를 **명령**, 개방적이 고 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 또는 다른 **레코드** 개체를 SQL SELECT 문 이거나 테이블 이름이 들어 있는 문자열입니다.  
  
 *ActiveConnection*  
 (선택 사항) A **Variant** 열거나 연결 문자열을 나타내는 [연결](../../../ado/reference/ado-api/connection-object-ado.md) 개체입니다.  
  
 *모드*  
 (선택 사항) A [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) 결과 대 한 액세스 모드를 지정 하는 값 **레코드** 개체입니다. 기본값은 **adModeUnknown**합니다.  
  
 *CreateOptions*  
 (선택 사항) A [RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md) 기존 파일 또는 디렉터리를 열어야 합니다 또는 새 파일 또는 디렉터리를 만들어야 하는지 여부를 지정 하는 값입니다. 기본값은 **adFailIfNotExists**합니다. 기본 값으로 설정 하는 경우 액세스 모드에서 가져온은 [모드](../../../ado/reference/ado-api/mode-property-ado.md) 속성입니다. 이 매개 변수가 무시 됩니다 때 합니다 *원본* 매개 변수를 URL 없습니다.  
  
 *옵션*  
 (선택 사항) A [함께 사용할 수](../../../ado/reference/ado-api/recordopenoptionsenum.md) 열기 위한 옵션을 지정 하는 값을 **레코드**합니다. 기본값은 **adOpenRecordUnspecified**합니다. 이러한 값을 결합할 수 있습니다.  
  
 *UserName*  
 (선택 사항) A **문자열** 필요한 경우에 대 한 액세스 권한을 부여 하는 사용자 ID를 포함 하는 값 *원본*합니다.  
  
 *암호*  
 (선택 사항) A **문자열** 필요한 경우를 확인 하는 암호가 포함 된 값 *UserName*합니다.  
  
## <a name="remarks"></a>설명  
 *원본* 될 수 있습니다.  
  
-   URL입니다. Http URL에 대 한 프로토콜을 사용 하는 경우 인터넷 공급자가 기본적으로 호출 됩니다. URL는 실행 가능한 스크립트를 포함 하는 노드를 가리키는 경우 (예는 합니다. ASP 페이지의 경우)를 **레코드** 실행 하는 대신 소스를 포함 하는 내용을 기본적으로 열립니다. 사용 된 *옵션* 이 동작을 수정 하는 인수입니다.  
  
-   A **레코드** 개체입니다. A **레코드** 개체에서 다른 열 **레코드** 원래 복제 됩니다 **레코드** 개체입니다.  
  
-   A **명령** 개체입니다. 열린 **레코드** 개체를 실행 하 여 반환 된 단일 행을 나타내는 합니다 **명령**입니다. 결과 둘 이상의 행이 있을 경우 첫 번째 행의 내용을 레코드에 배치 되 고 오류가 추가 될 수 있습니다 합니다 **오류** 컬렉션입니다.  
  
-   SQL SELECT 문입니다. 열린 **레코드** 개체는 문자열의 내용을 실행 하 여 반환 된 단일 행을 나타냅니다. 결과 둘 이상의 행이 있을 경우 첫 번째 행의 내용을 레코드에 배치 되 고 오류가 추가 될 수 있습니다 합니다 **오류** 컬렉션입니다.  
  
-   테이블 이름입니다.  
  
 경우는 **레코드** 개체 URL을 사용 하 여 액세스할 수 없는 엔터티를 나타냅니다 (예를 들어, 행을 **레코드 집합** 데이터베이스에서 파생)의 값이 모두는 [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)속성 및 사용 하 여 액세스할 필드를 **adRecordURL** 상수 null입니다.  
  
> [!NOTE]
>  Http 체계를 사용 하 여 Url은 자동으로 호출 합니다 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)합니다. 자세한 내용은 [절대 및 상대 Url](../../../ado/guide/data/absolute-and-relative-urls.md)합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [레코드 개체(ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [Open 메서드 (ADO 연결)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open 메서드 (ADO 레코드 집합)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open 메서드 (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema 메서드](../../../ado/reference/ado-api/openschema-method.md)
