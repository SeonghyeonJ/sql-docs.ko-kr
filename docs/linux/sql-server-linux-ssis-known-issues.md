---
title: 제한 사항 및 Linux에서 SSIS에 대 한 알려진된 문제
description: 이 문서에서는 설명 제한 사항 및 알려진된 문제 SQL Server Integration Services (SSIS)에 대 한 Linux 컴퓨터
author: lrtoyou1223
ms.author: lle
ms.reviewer: maghan
manager: jroth
ms.date: 06/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: bc4ec7f99a8cbcf5b6bd48924f3eed1e8f10f658
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833128"
---
# <a name="limitations-and-known-issues-for-ssis-on-linux"></a>제한 사항 및 Linux에서 SSIS에 대 한 알려진된 문제

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

이 문서에서는 제한 사항 및 알려진된 문제 SQL Server Integration Services (SSIS)에 대 한 linux.

## <a name="general-limitations-and-known-issues"></a>일반적인 제한 사항 및 알려진된 문제

Linux에서 SSIS의이 릴리스에서 다음과 같은 기능이 지원 되지 않습니다.
  - SSIS 카탈로그 데이터베이스
  - SQL 에이전트에서 예약 된 패키지 실행
  - Windows 인증
  - 타사 구성 요소
  - CDC(변경 데이터 캡처)
  - SSIS Scale Out
  - Azure Feature Pack for SSIS
  - Hadoop 및 HDFS 지원
  - Microsoft Connector for SAP BW

기타 제한 사항 및 Linux에서 SSIS 사용 하 여 알려진된 문제에 대 한 참조를 [릴리스](sql-server-linux-release-notes.md#ssis)합니다.

## <a name="components"></a> 지원 되거나 지원 되지 않는 구성 요소

다음 기본 제공 Integration Services 구성 요소는 Linux에서 지원 됩니다. 그 중 일부는 Linux 플랫폼에서 제한이 있습니다. 여기에 나열 되지 않은 기본 제공 구성 요소는 Linux에서 지원 되지 않습니다.

## <a name="supported-control-flow-tasks"></a>제어 흐름 태스크를 지원합니다.
- 대량 삽입 태스크
- 데이터 흐름 태스크
- 데이터 프로파일링 태스크
- SQL 실행 태스크
- T-SQL 문 실행 태스크
- 식 태스크
- FTP 태스크
- 웹 서비스 태스크
- XML 태스크

## <a name="control-flow-tasks-supported-with-limitations"></a>제어 흐름 태스크 제한 사항과 함께 지원

| 태스크 | 제한 사항 |
|------------|---|
| 프로세스 실행 태스크 | In-process 모드에만 지원합니다. |
| 파일 시스템 태스크 | 합니다 *이동 디렉터리* 하 고 *파일 특성을 설정할* 동작은 지원 되지 않습니다. |
| 스크립트 태스크 | 표준.NET Framework Api만 지원합니다. |
| 메일 보내기 태스크 | 익명 사용자 모드에만 지원합니다. |
| 데이터베이스 전송 태스크 | UNC 경로는 지원되지 않습니다. |
| | |

## <a name="supported-and-unsupported-maintenance-plan-tasks"></a>지원 되거나 지원 되지 않는 유지 관리 계획 태스크

SQL Server 유지 관리 계획에서 다양 한 SSIS 작업을 일반적으로 사용할 수 있습니다.

다음 유지 관리 계획 태스크는 Linux에서 지원 되지 않습니다.
- 운영자에 게 알림
- SQL Server 에이전트 작업 실행

다음 유지 관리 계획 태스크는 Linux에서 지원 됩니다.
- 데이터베이스 무결성 검사
- 데이터베이스 축소
- 인덱스 다시 구성
- 인덱스 다시 작성
- 통계 업데이트
- 기록 정리
- 데이터베이스 백업
- T-SQL 문

## <a name="supported-control-flow-containers"></a>제어 흐름 컨테이너를 지원합니다.
- 시퀀스 컨테이너
- For 루프 컨테이너
- Foreach 루프 컨테이너

## <a name="supported-data-flow-sources-and-destinations"></a>지원 되는 데이터 흐름 원본 및 대상
- 원시 파일 원본 및 대상
- XML 원본

## <a name="data-flow-sources-and-destinations-supported-with-limitations"></a>데이터 흐름 원본 및 대상을 제한 사항과 함께 지원

| 구성 요소 | 제한 사항 |
|------------|---|
| ADO.NET 원본 및 대상 | SQLClient 데이터 공급자만 지원 합니다. |
| 플랫 파일 원본 및 대상 | 기본 경로 매핑 규칙이 적용 되는 Windows 스타일 파일 경로 지원 합니다. 예를 들어 `D:\home\ssis\travel.csv` 가 `/home/ssis/travel.csv`합니다. |
| OData 원본 | 기본 인증만을 지원 합니다. |
| ODBC 원본 및 대상 | Linux에서 64 비트 유니코드 ODBC 드라이버를 지원합니다. Linux에서 UnixODBC 드라이버 관리자에 따라 달라 집니다. |
| OLE DB 원본 및 대상 | SQL Server에 대 한 SQL Server Native Client 11.0 및 Microsoft OLE DB Provider를만 지원 합니다. |
| | |

## <a name="supported-data-flow-transformations"></a>지원 되는 데이터 흐름 변환
- 집계
- 감사
- 분산 데이터 배포자
- 문자표 변환
- 조건부 분할
- 열 복사
- 데이터 변환
- 파생 열
- 열 내보내기
- 유사 항목 그룹화
- 유사 항목 조회
- 열 가져오기
- 조회
- 병합
- 병합 조인
- 멀티 캐스트
- Pivot
- 행 개수
- 느린 변경 차원
- 정렬
- 용어 조회
- Union All
- 피벗 해제

## <a name="data-flow-transformations-supported-with-limitations"></a>데이터 흐름 변환 제한 사항과 함께 지원

| 구성 요소 | 제한 사항 |
|------------|---|
| OLE DB 명령 변환 | OLE DB 원본 및 대상으로 동일한 제한 사항이 있습니다. |
| 스크립트 구성 요소 | 표준.NET Framework Api만 지원합니다. |
| | |

## <a name="supported-and-unsupported-log-providers"></a>지원 되거나 지원 되지 않는 로그 공급자
기본 제공 SSIS 로그 공급자는 Linux에서 지원 되는 모든 Windows 이벤트 로그 공급자를 제외 하 고 있습니다.

SQL Server 로그 공급자는 SQL 인증만 지원 합니다. Windows 인증을 지원 하지는 않습니다.

텍스트 파일, XML 파일 및 SQL Server Profiler에 대 한 SSIS 로그 공급자를 지정 하는 파일에 해당 출력을 씁니다. 파일 경로에 다음과 같은 고려 사항이 적용 됩니다.
-   경로 제공 하지 않으면 로그 공급자는 호스트의 현재 디렉터리에 씁니다. 현재 사용자에 호스트의 현재 디렉터리에 쓸 수 있는 권한이 없으면 로그 공급자 오류가 발생 했습니다.
-   환경 변수 파일 경로 사용할 수 없습니다. 환경 변수를 지정 하는 경우 지정 된 리터럴 텍스트 파일 경로에 표시 됩니다. 예를 들어 지정할 `%TMP%/log.txt`, 리터럴 텍스트를 추가 하는 로그 공급자 `/%TMP%/log.txt` 현재 호스트 디렉터리에 있습니다.

## <a name="related-content-about-ssis-on-linux"></a>Linux에서 SSIS에 대 한 관련된 콘텐츠
-   [추출, 변환 및 SSIS와 Linux에서 데이터 로드](sql-server-linux-migrate-ssis.md)
-   [Linux의 SQL Server Integration Services (SSIS)를 설치 합니다.](sql-server-linux-setup-ssis.md)
-   [Conf ssis를 사용 하 여 Linux에서 SQL Server Integration Services 구성](sql-server-linux-configure-ssis.md)
-   [일정 SQL Server Integration Services 패키지 cron 사용 하 여 Linux에서 실행](sql-server-linux-schedule-ssis-packages.md)
