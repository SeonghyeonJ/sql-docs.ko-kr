---
title: sqlcmd 유틸리티 시작 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 00d57437-7a29-4da1-b639-ee990db055fb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec1ec91705dfb9194f42c079cb7b3d5100c9d396
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090104"
---
# <a name="start-the-sqlcmd-utility"></a>sqlcmd 유틸리티 시작
  `sqlcmd` 사용을 시작하려면 먼저 유틸리티를 시작한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결해야 합니다. 기본 인스턴스나 명명된 인스턴스에 연결할 수 있습니다. 첫 번째 단계는 `sqlcmd` 유틸리티를 시작하는 것입니다.  
  
> [!NOTE]  
>  `sqlcmd`에 대한 기본 인증 모드는 Windows 인증입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 사용하려면 **-U** 및 **-P** 옵션을 사용하여 사용자 이름과 암호를 지정해야 합니다.  
  
> [!NOTE]  
>  기본적으로 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 는 명명된 인스턴스인 **sqlexpress**로 설치됩니다.  
  
 이 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 인스턴스에 연결한 적이 없는 경우 연결을 허용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 구성해야 할 수 있습니다.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-default-instance-of-sql-server"></a>sqlcmd 유틸리티를 시작하여 SQL Server의 기본 인스턴스에 연결하려면  
  
1.  **시작** 메뉴에서 **실행**을 클릭합니다. **열기** 상자에 **cmd**를 입력한 다음 **확인** 을 클릭하여 명령 프롬프트 창을 엽니다.  
  
2.  명령 프롬프트에서 `sqlcmd`를 입력합니다.  
  
3.  Enter 키를 누릅니다.  
  
     이제 트러스트된 연결을 사용하여 컴퓨터에서 실행 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 기본 인스턴스에 연결되었습니다.  
  
     **1 >** 되는 `sqlcmd` 줄 번호를 지정 하는 프롬프트입니다. Enter 키를 누를 때마다 번호가 1씩 증가합니다.  
  
4.  종료 합니다 `sqlcmd` 세션을 입력 `EXIT` 에 `sqlcmd` 프롬프트.  
  
### <a name="to-start-the-sqlcmd-utility-and-connect-to-a-named-instance-of-sql-server"></a>sqlcmd 유틸리티를 시작하여 SQL Server의 명명된 인스턴스에 연결하려면  
  
1.  명령 프롬프트를 열고 창을 `sqlcmd -S` *myServer\instanceName*합니다. *myServer\instanceName* 을 연결하려는 컴퓨터 이름 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 바꿉니다.  
  
2.  Enter 키를 누릅니다.  
  
     합니다 `sqlcmd` 프롬프트 (1 >)의 지정 된 인스턴스에 연결 되어 있는지 나타냅니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다.  
  
    > [!NOTE]  
    >  입력한 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 버퍼에 저장되며 GO 명령이 발견되면 일괄 처리로 실행됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [sqlcmd를 사용하여 Transact-SQL 스크립트 파일 실행](sqlcmd-run-transact-sql-script-files.md)  
  
  
