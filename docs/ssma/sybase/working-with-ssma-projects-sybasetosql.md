---
title: SSMA 프로젝트 (SybaseToSQL) 작업 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 11091d95-c488-48c3-891a-743cac94ac93
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: eb6f035b4d597e2b648134c195b698554dc78e12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072473"
---
# <a name="working-with-ssma-projects-sybasetosql"></a>SSMA 프로젝트 작업(SybaseToSQL)
Sybase 적응형 Server Enterprise (ASE) 데이터베이스를 마이그레이션하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure 처음 만들면 SSMA 프로젝트를 합니다. 마이그레이션하려는 ASE 데이터베이스에 대 한 메타 데이터가 포함 된 파일이 프로젝트 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure 대상 인스턴스에 대 한 메타 데이터 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 마이그레이션된 개체 및 데이터를 받을 SQL Azure 또는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure 연결 정보 및 프로젝트 설정 합니다.  
  
프로젝트를 열면에서 연결이 끊어지도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure입니다. 이 기능을 사용 하면 오프 라인으로 작업할 수 있습니다. 다시 연결할 수 있습니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure입니다. 자세한 내용은 [SQL Server에 연결 &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md) / [Azure SQL DB에 연결 &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md).  
  
## <a name="reviewing-default-project-settings"></a>기본 프로젝트 설정을 검토합니다.  
SSMA 변환 하 고 데이터를 데이터베이스 개체를 로드를 마이그레이션하고 SSMA ASE를 사용 하 여 동기화에 대 한 몇 가지 옵션을 포함 하 고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure입니다. 이러한 옵션에 대 한 기본 설정은 많은 사용자에 게 적합 합니다. 그러나 새 SSMA 프로젝트를 만들기 전에 해야 옵션 검토을 원하는 경우 모든 새 프로젝트에 사용할 기본값을 변경 합니다.  
  
**기본 프로젝트 설정을 검토 하려면**  
  
1.  에 **도구** 메뉴에서 **기본 프로젝트 설정**합니다.  
  
2.  라는 프로젝트 형식을 선택 **마이그레이션 대상 버전** 설정을 보거나 변경 하는 데 필요한 되며 클릭에 대 한 드롭다운 **일반** 탭 합니다.  
  
3.  왼쪽된 창에서 클릭 **변환**합니다.  
  
4.  오른쪽 창에서 필요에 따라 옵션을 변경 하 고 옵션을 검토 합니다. 이러한 옵션에 대 한 자세한 내용은 참조 하세요. [프로젝트 설정 &#40;변환&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-conversion-sybasetosql.md)합니다.  
  
5.  마이그레이션, SQL Azure, 개체 로드, GUI 및 형식 매핑 페이지에 대해 1-3 단계를 반복 합니다.  
  
    -   마이그레이션 옵션에 대 한 자세한 내용은 [프로젝트 설정 &#40;마이그레이션&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-migration-sybasetosql.md)합니다.  
  
    -   개체를 로드 하기 위한 옵션에 대 한 자세한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 참조 하세요 [프로젝트 설정 &#40;동기화&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-synchronization-sybasetosql.md).  
  
    -   GUI 옵션에 대 한 자세한 내용은 참조 하십시오 [프로젝트 설정 &#40;GUI&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-gui-sybasetosql.md)합니다.  
  
    -   데이터 형식 매핑 설정에 대 한 자세한 내용은 [프로젝트 설정 &#40;형식 매핑&#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-type-mapping-sybasetosql.md)합니다.  
  
    -   SQL Azure 옵션에 대 한 자세한 내용은 참조 하세요. [프로젝트 설정 &#40;Azure SQL DB &#41; &#40;SybaseToSQL&#41;](../../ssma/sybase/project-settings-azure-sql-db-sybasetosql.md)합니다.  
  
    > [!NOTE]  
    > SQL Azure 설정을 선택한 경우에 표시 됩니다 **SQL Azure의 마이그레이션을** 프로젝트를 만드는 동안.  
  
## <a name="creating-new-projects"></a>새 프로젝트 만들기  
ASE 데이터베이스에서 데이터를 마이그레이션하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure 있습니다 프로젝트를 먼저 만들어야 합니다.  
  
**프로젝트를 만들려면**  
  
1.  **파일** 메뉴에서 **새 프로젝트**를 선택합니다.  
  
    **새 프로젝트** 대화 상자가 나타납니다.  
  
2.  **이름** 입력란에 프로젝트 이름을  
  
3.  에 **위치** 상자에 입력 하거나 프로젝트에 대 한 폴더를 선택 합니다.  
  
4.  에 **마이그레이션에** 드롭다운, 대상의 버전을 선택 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 마이그레이션에 사용 합니다. 사용 가능한 옵션은 다음과 같습니다.  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL DB  
  
클릭 하 고 **확인**합니다.  
  
## <a name="customizing-project-settings"></a>사용자 지정 프로젝트 설정  
에 모든 새 SSMA 프로젝트에 적용 되는 기본 프로젝트 설정을 정의 하는 것 외에도 각 프로젝트에 대 한 설정을 사용자 지정할 수 있습니다. 자세한 내용은 [프로젝트 옵션 설정 &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)합니다.  
  
원본 및 대상 데이터베이스 간의 데이터 형식 매핑 사용자 지정 하는 경우 프로젝트, 데이터베이스 또는 개체 수준에서 매핑을 정의할 수 있습니다. 형식 매핑에 대 한 자세한 내용은 참조 하세요. [매핑 Sybase ASE 및 SQL Server 데이터 형식 &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)합니다.  
  
## <a name="saving-projects"></a>프로젝트를 저장합니다.  
프로젝트를 저장 하면 SSMA 프로젝트 설정 및 선택적으로 프로젝트 파일에는 데이터베이스 메타 데이터를 유지 합니다.  
  
**프로젝트를 저장 하려면**  
  
-   에 **파일** 메뉴에서 **프로젝트 저장**합니다.  
  
    데이터베이스 프로젝트 내에서 변경 또는 변환 되지 않은 경우 프로젝트에 메타 데이터를 저장 하 SSMA 메시지가 나타납니다. 메타 데이터를 저장 하면 오프 라인으로 작업 하 고 기술 지원 요원을 비롯 한 다른 사용자에 게 전체 프로젝트 파일을 보냅니다. 메타 데이터를 저장 하 라는 메시지가 나타나면 다음을 수행 합니다.  
  
    1.  각 데이터베이스의 상태를 보여 주는 **메타 데이터 누락**, 데이터베이스 이름 옆의 확인란을 선택 합니다.  
  
        메타 데이터를 저장 하면 몇 분 정도 걸릴 수 있습니다. 이 시점에서 메타 데이터를 저장 하지 않을 경우 모든 확인란을 선택 하지 마십시오.  
  
    2.  **저장** 단추를 클릭합니다.  
  
        SSMA는 Sybase ASE 스키마를 구문 분석 하 고 프로젝트 파일에 메타 데이터를 저장 합니다.  
  
## <a name="opening-projects"></a>열린 프로젝트  
ASE에서 끊어진 프로젝트를 열면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure입니다. 이 기능을 사용 하면 오프 라인으로 작업할 수 있습니다. 메타 데이터를 업데이트 하려면 데이터베이스 개체를 로드 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure입니다. 데이터를 마이그레이션하려면 ASE에 연결 해야 하 고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure입니다.  
  
**프로젝트를 열려면**  
  
1.  다음 절차 중 하나를 사용 합니다.  
  
    -   에 **파일** 메뉴에서 **최근에 사용한 프로젝트**, 다음 열려는 프로젝트를 선택 하 고 있습니다.  
  
    -   에 **파일** 메뉴에서 **프로젝트 열기**.s2ssproj 프로젝트 파일 찾기, 파일을 선택 및 클릭 **열기**.  
  
2.  ASE에 다시 연결 합니다 **파일** 메뉴에서 **Sybase에 다시 연결**합니다.  
  
3.  에 다시 연결할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 또는 SQL Azure는 **파일** 메뉴에서 **SQL Server에 다시 연결** / **SQL Azure 다시 연결**합니다.  
  
## <a name="next-step"></a>다음 단계  
마이그레이션 프로세스에서 다음 단계 [Sybase ASE에는 Connect](connecting-to-sybase-ase-sybasetosql.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
[Sybase ASE 데이터베이스를 SQL Server-Azure SQL DB로 마이그레이션 &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
[Sybase ASE에 연결 &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sybase-ase-sybasetosql.md)  
[SQL Server에 연결 &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-sql-server-sybasetosql.md)  
[Azure SQL DB에 연결 &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
