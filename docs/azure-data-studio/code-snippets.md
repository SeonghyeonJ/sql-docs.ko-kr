---
title: 재사용 가능한 코드 조각 만들기
description: 데이터베이스 및 데이터베이스 개체를 쉽게 만들 수 있도록 해 주는 Azure Data Studio SQL 코드 조각을 만들고 사용하는 방법을 알아봅니다.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: aa1826539a6b9d2a5f649159e566d3ceda8d624d
ms.sourcegitcommit: 63aef5a96905f0b026322abc9ccb862ee497eebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91364130"
---
# <a name="create-and-use-code-snippets-to-quickly-create-transact-sql-t-sql-scripts-in-azure-data-studio"></a>Azure Data Studio에서 코드 조각을 만들고 사용하여 T-SQL(Transact-SQL) 스크립트를 빠르게 만들 수 있습니다.

Azure Data Studio의 코드 조각은 데이터베이스 및 데이터베이스 개체를 쉽게 만들 수 있는 템플릿입니다. 

Azure Data Studio에서는 올바른 구문을 빠르게 생성하는 데 도움이 되는 여러 T-SQL 코드 조각을 제공합니다. 

사용자 정의 코드 조각을 만들 수도 있습니다.

## <a name="using-built-in-t-sql-code-snippets"></a>기본 제공 T-SQL 코드 조각 사용

1. 사용 가능한 코드 조각에 액세스하려면 쿼리 편집기에서 *sql*을 입력하여 목록을 엽니다.

   ![코드 조각](media/code-snippets/sql-snippets.png)

2. 사용할 코드 조각을 선택하고 T-SQL 스크립트를 생성합니다. 예를 들어 *sqlCreateTable*을 선택합니다.

   ![테이블 코드 조각 만들기](media/code-snippets/create-table.png)

3. 강조 표시된 필드를 특정 값으로 업데이트합니다. 예를 들어, *TableName* 및 *Schema*를 데이터베이스의 값으로 바꿉니다.

   ![코드 조각의 테이블](media/code-snippets/table-from-snippet.png)

   변경하려는 필드가 더 이상 강조 표시되지 않는 경우(편집기를 중심으로 커서를 이동할 때 이러한 현상이 발생함) 변경할 단어를 마우스 오른쪽 단추로 클릭하고 **모든 항목 변경**을 선택합니다.

   ![모두 변경](media/code-snippets/change-all.png)

4. 선택한 코드 조각에 필요한 추가 T-SQL을 업데이트하거나 추가합니다. 예를 들어 *Column1*, *Column2*를 업데이트하고 더 많은 열을 추가합니다.

## <a name="creating-sql-code-snippets"></a>SQL 코드 조각 만들기

사용자 고유의 코드 조각을 정의할 수 있습니다. 편집을 위해 SQL 코드 조각 파일을 열려면

1. ‘명령 팔레트’를 열고(**Shift+Ctrl+P**) *snip*를 입력한 후 **기본 설정: 사용자 코드 조각 열기**를 선택합니다.

   ![사용자 코드 조각](media/code-snippets/user-snippets.png)

2. **SQL**을 선택합니다.

   > [!NOTE]
   > Azure Data Studio는 Visual Studio Code에서 해당 코드 조각 기능을 상속하므로 이 문서에서는 특별히 SQL 코드 조각 사용 방법을 설명합니다. 자세한 내용은 Visual Studio Code 설명서에서 [사용자 고유의 코드 조각 만들기](https://code.visualstudio.com/docs/editor/userdefinedsnippets)를 참조하세요. 

   ![SQL 선택](media/code-snippets/select-sql.png)

3. 다음 코드를 *sql.json*에 붙여넣습니다.

    ```sql
    {
     "Select top 5": {
    "prefix": "sqlSelectTop5",
    "body": "SELECT TOP 5 * FROM ${1:TableName}",
    "description": "User-defined snippet example 1"
    },
    "Create Table snippet":{
    "prefix": "sqlCreateTable2",
    "body": [
    "-- Create a new table called '${1:TableName}' in schema '${2:SchemaName}'",
    "-- Drop the table if it already exists",
    "IF OBJECT_ID('$2.$1', 'U') IS NOT NULL",
    "DROP TABLE $2.$1",
    "GO",
    "-- Create the table in the specified schema",
    "CREATE TABLE $2.$1",
    "(",
    "$1Id INT NOT NULL PRIMARY KEY, -- primary key column",
    "Column1 [NVARCHAR](50) NOT NULL,",
    "Column2 [NVARCHAR](50) NOT NULL",
    "-- specify more columns here",
    ");",
    "GO"
    ],
       "description": "User-defined snippet example 2"
       }
       }
       ```

4. Save the sql.json file.

5. Open a new query editor window by clicking **Ctrl+N**.

6. Type **sql**, and you see the two user snippets you just added; *sqlCreateTable2* and *sqlSelectTop5*.

Select one of the new snippets and give it a test run!

## Next steps

For information about the SQL editor, see [Code editor tutorial](tutorial-sql-editor.md).
