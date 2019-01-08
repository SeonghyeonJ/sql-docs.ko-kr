---
title: 게시 및 아티클 만들기, 수정 및 삭제(복제) | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], creating
- articles [SQL Server replication], defining
ms.assetid: e66d06ec-a12b-444d-875b-77f958af2f21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3849273ee37db2780e53d28933ad7f1ffd89f056
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794435"
---
# <a name="create-modify-and-delete-publications-and-articles-replication"></a>게시 및 아티클 만들기, 수정 및 삭제(복제)
  이 설명서 섹션에는 게시 생성 및 아티클 정의와 관련된 태스크에 대한 절차 정보가 포함되어 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
-   [Create a Publication](create-a-publication.md)  
  
-   [아티클 정의](define-an-article.md)  
  
-   [게시 속성 보기 및 수정](view-and-modify-publication-properties.md)  
  
-   [아티클 속성 보기 및 수정](view-and-modify-article-properties.md)  
  
-   [게시 삭제](delete-a-publication.md)  
  
-   [아티클 삭제](delete-an-article.md)  
  
-   [Oracle 데이터베이스에서 게시 만들기](create-a-publication-from-an-oracle-database.md)  
  
-   [구독에 대한 만료 기간 설정](set-the-expiration-period-for-subscriptions.md)  
  
-   [스키마 옵션 지정](specify-schema-options.md)  
  
-   [스키마 변경 내용 복제](replicate-schema-changes.md)  
  
-   [ID 열 관리](manage-identity-columns.md)  
  
-   [병합 게시에 대한 호환성 수준 설정](set-the-compatibility-level-for-merge-publications.md)  
  
## <a name="snapshot-options"></a>스냅숏 옵션  
  
-   [스냅숏 형식 지정&#40;SQL Server Management Studio&#41;](specify-snapshot-format-sql-server-management-studio.md)  
  
-   [대체 스냅숏 폴더 위치 지정&#40;SQL Server Management Studio&#41;](specify-an-alternate-snapshot-folder-location-sql-server-management-studio.md)  
  
-   [스냅숏 파일 압축&#40;SQL Server Management Studio&#41;](compress-snapshot-files-sql-server-management-studio.md)  
  
-   [스냅숏 속성 구성&#40;복제 Transact-SQL 프로그래밍&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)  
  
-   [스냅숏 적용 전후에 스크립트 실행&#40;SQL Server Management Studio&#41;](../execute-scripts-before-and-after-a-snapshot-is-applied.md)  
  
-   [FTP를 통해 스냅숏 배달](deliver-a-snapshot-through-ftp.md)  
  
## <a name="filtering-data"></a>데이터 필터링  
  
-   [열 필터 정의 및 수정](define-and-modify-a-column-filter.md)  
  
-   [정적 행 필터 정의 및 수정](define-and-modify-a-static-row-filter.md)  
  
-   [Define and Modify a Parameterized Row Filter for a Merge Article](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)  
  
-   [매개 변수가 있는 행 필터 최적화](../merge/parameterized-filters-parameterized-row-filters.md)  
  
-   [병합 아티클 사이에서 조인 필터 정의 및 수정](define-and-modify-a-join-filter-between-merge-articles.md)  
  
-   [병합 아티클 간의 조인 필터 집합 자동 생성&#40;SQL Server Management Studio&#41;](automatically-generate-join-filters-between-merge-articles.md)  
  
## <a name="transactional-replication-options"></a>트랜잭션 복제 옵션  
  
-   [트랜잭션 아티클의 데이터 변경 내용을 전파하는 방법 설정](set-the-propagation-method-for-data-changes-to-transactional-articles.md)  
  
-   [트랜잭션 게시에 대해 업데이트할 수 있는 구독 설정](enable-updating-subscriptions-for-transactional-publications.md)  
  
-   [지연 업데이트 충돌 해결 옵션 설정&#40;SQL Server Management Studio&#41;](set-queued-updating-conflict-resolution-options-sql-server-management-studio.md)  
  
-   [저장 프로시저 실행을 트랜잭션 게시로 게시&#40;SQL Server Management Studio&#41;](publish-execution-of-stored-procedure-in-transactional-publication.md)  
  
## <a name="merge-replication-options"></a>병합 복제 옵션  
  
-   [병합 테이블 아티클 간의 논리적 레코드 관계 정의](define-a-logical-record-relationship-between-merge-table-articles.md)  
  
-   [병합 테이블 아티클의 처리 순서 지정&#40;복제 Transact-SQL 프로그래밍&#41;](specify-the-processing-order-of-merge-table-articles.md)  
  
-   [새 병합 테이블 아티클을 다운로드 전용으로 지정](specify-that-a-merge-table-article-is-download-only.md)  
  
-   [병합 아티클에 대해 삭제가 추적되지 않도록 지정&#40;복제 Transact-SQL 프로그래밍&#41;](specify-that-deletes-should-not-be-tracked-for-merge-articles.md)  
  
-   [병합 아티클의 충돌 추적 및 해결 수준 지정](specify-the-conflict-tracking-and-resolution-level-for-merge-articles.md)  
  
-   [병합 아티클 해결 프로그램 지정](specify-a-merge-article-resolver.md)  
  
-   [병합 아티클에 대한 상호 충돌 해결 프로그램 지정](specify-interactive-conflict-resolution-for-merge-articles.md)  
  
## <a name="see-also"></a>관련 항목:  
 [데이터 및 데이터베이스 개체 게시](publish-data-and-database-objects.md)  
  
  
