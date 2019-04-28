---
title: 트랜잭션 데이터용 InfoSource 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ab5f23e2-cd4e-4507-83d9-ac5ef721c171
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 6d99a357c754add722fb6d5b5d880d1c472a5989
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827934"
---
# <a name="create-infosource-for-transaction-data"></a>트랜잭션 데이터용 InfoSource 만들기
  **트랜잭션 데이터용 InfoSource 만들기** 대화 상자를 사용하여 SAP Netweaver BW 시스템에서 트랜잭션 데이터용으로 새 InfoSource를 만들 수 있습니다.  
  
 **트랜잭션 데이터용 InfoSource 만들기** 대화 상자는 **SAP BW 대상 편집기** 의 **연결 관리자**페이지에서 열 수 있습니다. SAP BW 대상에 대한 자세한 내용은 [SAP BW Destination](sap-bw-destination.md)을 참조하십시오.  
  
> [!IMPORTANT]  
>  SAP BW용 Microsoft Connector 1.1 설명서는 SAP Netweaver BW 환경에 익숙한 것으로 가정합니다. SAP Netweaver BW 또는 SAP Netweaver BW 개체 및 프로세스 구성 방법에 대한 자세한 내용은 SAP 설명서를 참조하십시오.  
  
 **트랜잭션 데이터용 InfoSource 만들기 대화 상자를 열려면**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 SAP BW 대상이 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 패키지를 엽니다.  
  
2.  **데이터 흐름** 탭에서 SAP BW 대상을 두 번 클릭합니다.  
  
3.  **SAP BW 대상 편집기**에서 **연결 관리자** 를 클릭하여 편집기의 **연결 관리자** 페이지를 엽니다.  
  
4.  **연결 관리자** 페이지의 **SAP BW 개체 만들기** 그룹 상자에서 **InfoSource**를 선택한 다음 **만들기**를 클릭합니다.  
  
5.  **InfoSource 만들기** 대화 상자에서 **트랜잭션 데이터**를 선택한 다음 **확인**을 클릭합니다.  
  
## <a name="general-options"></a>일반 옵션  
 **InfoSource 이름**  
 새 InfoSource의 이름을 입력합니다.  
  
 **간단한 설명**  
 새 InfoSource에 대한 간단한 설명을 입력합니다.  
  
 **자세한 설명**  
 새 InfoSource에 대한 자세한 설명을 입력합니다.  
  
 **원본 시스템**  
 InfoSource와 연결된 원본 시스템을 선택합니다.  
  
 **저장 및 활성화**  
 새 InfoSource를 저장하고 활성화합니다.  
  
## <a name="infosource-transfer-structure-options"></a>InfoSource 전송 구조 옵션  
 InfoSource 전송 구조에서 데이터 흐름 열을 InfoSource에 연결할 수 있습니다.  
  
 **PipelineElement**  
 SAP BW 대상에 연결된 열을 데이터 흐름의 출력에 표시합니다.  
  
 **PipelineDataType**  
 데이터 흐름 열의 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 데이터 형식을 표시합니다.  
  
 **Iobject - 검색**  
 기존 InfoObject를 현재 행의 데이터 흐름 열에 연결합니다. 이 연결을 만들려면 **검색**을 클릭한 다음 **InfoObject 조회** 대화 상자를 사용하여 기존 InfoObject를 선택합니다. 이 대화 상자에 대한 자세한 내용은 [Look Up InfoObject](look-up-infoobject.md)을 참조하십시오.  
  
 기존 InfoObject를 선택한 후 **InfoObject** 및 **유형** 열이 선택한 값으로 채워집니다.  
  
 **Iobject - 새로 만들기**  
 새 InfoObject를 만들고 이 InfoObject를 현재 행의 데이터 흐름 열에 연결합니다. 새 InfoObject를 만들려면 **새로 만들기**를 클릭한 다음 **새 InfoObject 만들기** 대화 상자를 사용하여 InfoObject를 만듭니다. 이 대화 상자에 대한 자세한 내용은 [Create New InfoObject](create-new-infoobject.md)을 참조하십시오.  
  
 새 InfoObject를 만든 후 **InfoObject** 및 **유형** 열이 새 값으로 채워집니다.  
  
 **Iobject - 제거**  
 InfoObject와 현재 행의 데이터 흐름 열 간의 연결을 제거합니다. 이 연결을 제거하려면 **제거**를 클릭합니다.  
  
 **InfoObject**  
 데이터 흐름 열과 연결된 InfoObject의 이름을 표시합니다.  
  
 **유형**  
 데이터 흐름 열과 연결된 InfoObject의 유형을 표시합니다. 다음 표에서는 유형에 사용할 수 있는 값을 나열합니다.  
  
|값|Description|  
|-----------|-----------------|  
|CHA|특징|  
|UNI|단위|  
|KYF|주요 수치|  
|TIM|시간 특징|  
  
 **단위 필드**  
 InfoObject가 사용할 단위를 지정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [InfoSource 만들기](create-infosource.md)   
 [Microsoft Connector 1.1 for SAP BW F1 도움말](../microsoft-connector-for-sap-bw-f1-help.md)  
  
  
