---
title: 사용자 지정 워크플로 XML 설명
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: reference
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f7c49f9b2831942552844e6bb479d139988d84c7
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85897427"
---
# <a name="create-a-custom-workflow---xml-description"></a>사용자 지정 워크플로 만들기 - XML 설명

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  에서 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130)) 는 워크플로가 시작 될 때 MDS 워크플로 통합 서비스를 SQL Server 하 여 호출 하는 것입니다. 이 메서드는 워크플로 비즈니스 규칙을 트리거한 항목에 대한 메타데이터 및 데이터를 XML 블록으로 받습니다. 워크플로 처리기를 구현하는 예제 코드는 [사용자 지정 워크플로 예제&#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)를 참조하세요.  
  
 다음 예제에서는 워크플로 처리기로 전송되는 XML을 보여 줍니다.  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 다음 표에서는 이 XML에 포함되는 태그 일부에 대해 설명합니다.  
  
|태그|설명|  
|---------|-----------------|  
|\<Type>|로드할 사용자 지정 워크플로 어셈블리를 식별하기 위해 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **워크플로 유형** 입력란에 입력한 텍스트입니다.|  
|\<SendData>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **메시지에 멤버 데이터 포함** 확인란으로 제어하는 부울 값입니다. 값이 1 이면 \<MemberData> 섹션이 전송 되 고, 그렇지 않으면 \<MemberData> 섹션이 전송 되지 않습니다.|  
|<Server_URL>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **워크플로 사이트** 입력란에 입력한 텍스트입니다.|  
|<Action_ID>|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]에서 **워크플로 이름** 입력란에 입력한 텍스트입니다.|  
|\<MemberData>|워크플로 동작을 트리거한 멤버의 데이터를 포함합니다. 의 값이 1 인 경우에만 포함 됩니다 \<SendData> .|  
|\<Enter*xxx*>|이 태그 집합에는 멤버 생성에 대한 메타데이터(예: 만든 날짜, 만든 사람 등)가 포함됩니다.|  
|\<LastChg*xxx*>|이 태그 집합에는 멤버에 적용된 마지막 변경 내용에 대한 메타데이터(예: 변경 내용을 적용한 날짜, 변경 내용을 적용한 사람 등)가 포함됩니다.|  
|\<Name>|변경된 멤버의 첫 번째 특성입니다. 이 예제 멤버에는 Name 및 Code 특성만 포함되어 있습니다.|  
|\<Code>|변경된 멤버의 다음 특성입니다. 이 예제 멤버에 더 많은 특성이 포함될 경우 해당 특성은 이 특성 다음에 오게 됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 워크플로 &#40;MDS(Master Data Services)를 만듭니다&#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)   
 [사용자 지정 워크플로 예제&#40;Master Data Services&#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)  
  
  
