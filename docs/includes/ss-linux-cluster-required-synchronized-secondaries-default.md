---
ms.openlocfilehash: 2dc81d434714e0a13912fa6f14e1194df5e5afe3
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68215600"
---
> [!NOTE]
> 리소스를 만들 때와 이후 정기적으로 Pacemaker 리소스 에이전트는 가용성 그룹에서 `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT`의 값을 가용성 그룹의 구성을 바탕으로 자동으로 설정합니다. 예를 들어 가용성 그룹에 세 개의 동기 복제본이 있는 경우 에이전트는 `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT`을 `1`로 설정합니다. 자세한 내용 및 추가 구성 옵션은 [High availability and data protection for availability group configurations](../linux/sql-server-linux-availability-group-ha.md)(가용성 그룹 구성을 위한 고가용성 및 데이터 보호)를 참조하세요. 