---
title: 부록-1 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: c6a30367-d56f-4fcc-8920-c6a6b0335a67
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 70d916526f5b7d7d36c9237624ef311befca39c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67938354"
---
# <a name="appendix---1-db2tosql"></a>부록-1 (DB2ToSQL)
SSMA 콘솔 명령줄 옵션에 대 한 빠른 보기:  
  
|Sl 합니다. 아니요.|스위치|필수 여부|스위치 인수|허용 되는 값|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|예|scriptfile|올바른 XML 파일 이름입니다.<br /><br />콘솔 스크립트 정의 파일입니다.|  
|2|-v/variable|아니요|variablevaluefile|올바른 XML 파일 이름입니다.<br /><br />스크립트 파일에서 변수를 사용 하는이 파일을 지정 해야 합니다.|  
|3|-c/serverconnection|아니요|serverconnectionfile|올바른 XML 파일 이름입니다.<br /><br />이 파일 서버 연결 정보를 포함 합니다.|  
|4|-x/xmloutput|아니요|xmloutputfile|이 옵션은 XML 형식으로 콘솔 출력을 나타냅니다. 이 옵션을 지정 하지 않으면 기본 출력을 텍스트 형식으로 됩니다.<br /><br />Xmloutputfile를 지정 하지 않은 경우 XML 출력은 STDOUT으로 전송 됩니다.<br /><br />Xmloutputfile에는 콘솔 출력은 XML 형식으로 기록 되는 파일의 이름입니다.|  
|5|-l/log|아니요|logfile|유효한 파일 이름입니다.|  
|6|-e/projectenvironment|아니요|projectenvironmentfolder|SSMA 프로젝트 환경 파일이 포함 된 올바른 폴더 이름입니다.|  
|7|-p/securepassword|아니요|-추가 {< server_id > [,... n] &#124; 모든}-c&#124;serverconnection < 서버 연결 파일 > [-v&#124;변수 < 변수 값 파일 >] [-o/덮어쓰기]<br /><br />로 구분하거나 여러<br /><br />-추가 {< server_id > [,... n] &#124; 모든}-s&#124;스크립트 < 스크립트 파일 > [-v&#124;변수 < 변수 값 파일 >] [-o/덮어쓰기]<br /><br />-r/remove {<server_id> [, ...n] &#124; all}<br /><br />-l/list<br /><br />-e 내보낼 {< 서버 id > [,... n] &#124; 모든} < 암호화 암호-파일 ><br /><br />-i 가져오기 / {< 서버 id > [,... n] &#124; 모든} < 암호화 암호-파일 >|를 지정 하는 경우이 옵션 다른 옵션과 함께 사용할 수 없습니다.<br /><br />server-id: {문자열} 서버에 대해 제공 된 고유 ID<br /><br />서버 연결 파일: 서버 정의 파일 (serverconnectionfile 또는 scriptfile).<br /><br />파일-변수-값: 변수 정의 파일이 하 고 서버 연결 파일에 사용 합니다.<br /><br />암호화 암호-파일: 사용자가 지정한 암호를 사용 하 여 암호화 하는 서버 암호 파일입니다.|  
|8|-?|아니요|해당 사항 없음|해당 사항 없음|  
  
## <a name="see-also"></a>관련 항목  
[SSMA 콘솔 실행](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
