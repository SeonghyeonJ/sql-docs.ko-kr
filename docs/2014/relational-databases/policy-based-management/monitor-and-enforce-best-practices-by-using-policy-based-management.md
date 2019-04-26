---
title: 정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 46788407-187e-4b0b-bfe4-529af8d77c60
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: bfc7cc16c9751ebdf64a8e9cd110547255c944ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62626050"
---
# <a name="monitor-and-enforce-best-practices-by-using-policy-based-management"></a>정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용
  정책 기반 관리 기능을 사용 하면 모니터링에 대 한 모범 사례는 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 최선의 방법 정책으로 가져와서 인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체를 포함하는 대상 집합에 대해 정책을 평가할 수 있는 일련의 정책 파일을 제공합니다. 정책을 수동으로 평가하거나, 일정에 따라 대상 집합을 평가하도록 정책을 설정하거나, 이벤트에 따라 대상 집합을 평가하도록 정책을 설정할 수 있습니다. 정책 기반 관리에 대한 자세한 내용은 [정책 기반 관리를 사용하여 서버 관리](administer-servers-by-using-policy-based-management.md)를 참조하세요.  
  
## <a name="policy-and-rules-for-database-engine"></a>데이터베이스 엔진에 대한 정책 및 규칙  
 다음 표에서 설치에 포함 된 정책을 나열 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 각 정책이 평가 하는 최선의 방법 규칙에 대 한 정보를 포함 합니다. 정책은 XML 파일로 저장되며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 가져와야 합니다. 정책을 가져오는 방법은 [정책 기반 관리 정책 가져오기](import-a-policy-based-management-policy.md)를 참조하세요.  
  
|정책 이름|최선의 방법 규칙|  
|-----------------|------------------------|  
|비대칭 키 암호화 알고리즘|[비대칭 키 암호화의 강도](asymmetric-keys-encryption-strength.md)|  
|백업 및 데이터 파일 위치|[백업 파일을 데이터베이스 파일과 별개의 장치에 두어야 함](../../database-engine/backup-files-must-be-on-separate-devices-from-the-database-files.md)|  
|데이터 및 로그 파일 위치|[데이터와 로그 파일을 별개의 드라이브에 배치](place-data-and-log-files-on-separate-drives.md)|  
|데이터베이스 자동 닫기|[AUTO_CLOSE 데이터베이스 옵션을 OFF로 설정](set-the-auto-close-database-option-to-off.md)|  
|데이터베이스 자동 축소|[AUTO_SHRINK 데이터베이스 옵션을 OFF로 설정](set-the-auto-shrink-database-option-to-off.md)|  
|데이터베이스 정렬|[master 및 model 데이터베이스와 일치하도록 사용자 정의 데이터베이스의 데이터 정렬 설정](../../database-engine/set-collation-user-defined-databases-match-master-model-databases.md)|  
|데이터베이스 페이지 확인|[PAGE_VERIFY 데이터베이스 옵션을 CHECKSUM으로 설정](set-the-page-verify-database-option-to-checksum.md)|  
|데이터베이스 페이지 상태|[주의 대상 페이지가 있는 데이터베이스의 무결성 검사](check-integrity-of-database-with-suspect-pages.md)|  
|게스트 사용 권한|[사용자 데이터베이스에 대한 게스트 사용 권한](guest-permissions-on-user-databases.md)|  
|마지막으로 성공한 백업 날짜|[오래된 백업](outdated-backup.md)|  
|Public에는 부여되지 않는 서버 사용 권한|[서버 public 사용 권한](server-public-permissions.md)|  
|SQL Server 32 비트 선호도 마스크 겹침|[올바른 선호도 마스크 및 선호도 입된/출력 마스크 겹침](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|SQL Server 64비트 선호도 마스크 겹침|[올바른 선호도 마스크 및 선호도 입된/출력 마스크 겹침](correct-affinity-mask-and-affinity-input-and-output-mask-overlap.md)|  
|SQL Server 선호도 마스크|[선호도 마스크 기본값 유지](keep-the-affinity-mask-default-value.md)|  
|SQL Server 차단된 프로세스 임계값|[차단된 프로세스 임계값 늘리기 또는 해제](increase-or-disable-blocked-process-threshold.md)|  
|SQL Server 기본 추적|[기본 추적 로그 파일 해제](default-trace-log-files-disabled.md)|  
|SQL Server 동적 잠금|[잠금 구성 옵션의 기본값 유지](keep-the-locks-configuration-option-default-value.md)|  
|SQL Server 경량 풀링|[경량 풀링 해제](disable-lightweight-pooling.md)|  
|SQL Server 로그인 모드|[인증 모드 선택](../security/choose-an-authentication-mode.md)|  
|SQL Server 최대 병렬 처리 수준|[최적 성능을 위해 최대 병렬 처리 수준 옵션 설정](set-the-max-degree-of-parallelism-option-for-optimal-performance.md)|  
|32비트 SQL Server 2000용 SQL Server 최대 작업자 스레드 수|[최대 작업자 스레드 수 설정 검사](verify-max-worker-threads-setting.md)|  
|64비트 SQL Server 2000용 SQL Server 최대 작업자 스레드 수|[최대 작업자 스레드 수 설정 검사](verify-max-worker-threads-setting.md)|  
|SQL Server 2005 이상용 SQL Server 최대 작업자 스레드 수|[최대 작업자 스레드 수 설정 검사](verify-max-worker-threads-setting.md)|  
|SQL Server 네트워크 패킷 크기|[네트워크 패킷 크기는 8060바이트를 초과할 수 없음](network-packet-size-should-not-exceed-8060-bytes.md)|  
|SQL Server 암호 만료|[SQL Server 로그인 암호 만료](sql-server-login-password-expiration.md)|  
|SQL Server 암호 정책|[SQL Server 로그인 암호 강도](sql-server-login-password-strength.md)|  
|사용자 데이터베이스용 대칭 키 암호화|[사용자 데이터베이스의 대칭 키](symmetric-keys-on-user-databases.md)|  
|master 데이터베이스용 대칭 키|[시스템 데이터베이스의 대칭 키](symmetric-keys-on-system-databases.md)|  
|시스템 데이터베이스용 대칭 키|[시스템 데이터베이스의 대칭 키](symmetric-keys-on-system-databases.md)|  
|Trustworthy 데이터베이스|[신뢰할 수 있는 비트](trustworthy-bit.md)|  
|Windows 이벤트 로그 클러스터 디스크 리소스 손상 오류|[SCSI 호스트 어댑터 문제 검색](detect-scsi-host-adapter-issues.md)|  
|Windows 이벤트 로그 디바이스 드라이버 컨트롤 오류|[장치 드라이버 컨트롤 오류](device-driver-control-error.md)|  
|Windows 이벤트 로그 디바이스 준비 안 됨 오류|[장치 준비 안 됨 오류](device-not-ready-error.md)|  
|Windows 이벤트 로그 I/O 요청 실패 오류|[실패 한 입된/출력 요청 검색](detect-failed-input-and-output-requests.md)|  
|Windows 이벤트 로그 I/O 지연 경고|[디스크 입/출력 하위 시스템에서 IO 지연 문제 확인](check-disk-input-and-output-subsystem-for-io-delay-problems.md)|  
|Windows 이벤트 로그 하드 페이지 폴트 중 I/O 오류 발생 오류|[입력 및 출력 오류 하드 페이지 폴트 중](input-and-output-error-during-hard-page-fault.md)|  
|Windows 이벤트 로그 읽기 다시 시도 오류|[읽기 다시 시도 문제에 대한 디스크 입력 출력 하위 시스템 검사](check-disk-input-output-subsystem-for-read-retry-problems.md)|  
|Windows 이벤트 로그 스토리지 시스템 I/O 제한 시간 오류|[저장소 시스템 입/출력 시간 초과](storage-system-input-output-time-out.md)|  
|Windows 이벤트 로그 시스템 실패 오류|[예기치 않은 시스템 오류](unexpected-system-failures.md)|  
  
## <a name="see-also"></a>참고 항목  
 [정책 기반 관리 패싯 작업](working-with-policy-based-management-facets.md)  
  
  
