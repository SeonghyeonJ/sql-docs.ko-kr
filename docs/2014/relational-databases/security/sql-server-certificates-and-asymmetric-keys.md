---
title: SQL Server 인증서 및 비대칭 키 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- security [SQL Server], certificates and asymmetric keys
ms.assetid: 8519aa2f-f09c-4c1c-96b5-abc24811e60c
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: ddb7e84f69f501a7857b0d55b1b8a14d11a85694
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75244510"
---
# <a name="sql-server-certificates-and-asymmetric-keys"></a>SQL Server 인증서 및 비대칭 키
  PKI (공개 키 암호화)는 사용자가 *공개* 키와 *개인* 키를 만드는 메시지 보안 형식입니다. 프라이빗 키는 비밀을 유지하지만 퍼블릭 키는 다른 사람에게 배포할 수 있습니다. 키가 수학적으로 서로 연관되어 있더라도 퍼블릭 키로 프라이빗 키를 쉽게 이끌어 낼 수 없습니다. 퍼블릭 키는 데이터를 암호화하는 데 사용되고 프라이빗 키는 데이터의 암호를 해독하는 데 사용됩니다. 퍼블릭 키를 사용하여 암호화된 메시지는 올바른 프라이빗 키를 사용해야만 암호를 해독할 수 있습니다. 따라서 서로 다른 두 개의 키가 있을 경우 이러한 키는 *비대칭*입니다.  
  
 인증서 및 비대칭 키의 두 가지 방법 모두 비대칭 암호화를 사용합니다. 인증서는 만료 날짜 및 발급자와 같은 자세한 정보를 포함할 수 있으므로 비대칭 키의 컨테이너로 종종 사용됩니다. 암호화 알고리즘에 있어서 두 가지 메커니즘 사이에 차이점이 없고 지정된 동일한 키 길이에 지정된 강도의 차이가 없습니다. 일반적으로 인증서를 사용하여 데이터베이스에서 다른 유형의 암호화 키를 암호화하거나 코드 모듈을 서명합니다.  
  
 인증서 및 비대칭 키를 통해 다른 사용자가 암호화한 데이터를 해독할 수 있습니다. 일반적으로 비대칭 암호화를 사용하여 데이터베이스의 스토리지에 대한 대칭 키를 암호화합니다.  
  
 공개 키에는 인증서에 있을 수 있는 특정한 형식이 없고 이 키를 파일로 내보낼 수 없습니다.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에는 서버와 데이터베이스에 사용할 인증서와 키를 만들고 관리할 수 있는 기능이 들어 있습니다. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 사용할 수 없습니다.  
  
## <a name="certificates"></a>인증서  
 인증서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]퍼블릭 키(필요에 따라 프라이빗 키)가 포함된 디지털 서명된 보안 개체입니다. 외부에서 생성된 인증서를 사용할 수 있거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 인증서를 생성할 수 있습니다.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증서는 IETF X.509v3 인증서 표준을 따릅니다.  
  
 인증서는 X.509 인증서 파일로 내보내기와 가져오기 키 모두에 대한 옵션 때문에 유용합니다. 인증서 생성에 대한 구문을 통해 만료 날짜와 같이 인증서의 생성 옵션을 사용할 수 있습니다.  
  
### <a name="using-a-certificate-in-sql-server"></a>SQL Server에서 인증서 사용  
 인증서를 사용하면 데이터베이스 미러링에서 패키지 및 기타 개체를 서명하도록 안전하게 연결할 수 있으며 데이터 또는 연결을 암호화할 수 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 인증서에 대한 추가 리소스를 보여 줍니다.  
  
|항목|설명|  
|-----------|-----------------|  
|[Transact-sql&#41;인증서 &#40;만들기](/sql/t-sql/statements/create-certificate-transact-sql)|인증서를 만들기 위한 명령에 대해 설명합니다.|  
|[디지털 서명을 사용 하 여 패키지 원본 확인](../../integration-services/security/identify-the-source-of-packages-with-digital-signatures.md)|인증서를 사용하여 소프트웨어 패키지를 서명하는 방법에 대한 정보가 표시됩니다.|  
|[Transact-sql&#41;&#40;데이터베이스 미러링 끝점에 대 한 인증서 사용](../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|데이터베이스 미러링에 인증서를 사용하는 방법에 대해 설명합니다.|  
  
## <a name="asymmetric-keys"></a>비대칭 키  
 비대칭 키는 대칭 키의 보안을 설정하는 데 사용됩니다. 또한 제한된 데이터 암호화와 데이터베이스 개체의 디지털 서명에도 사용할 수 있습니다. 비대칭 키는 프라이빗 키와 해당 퍼블릭 키로 구성됩니다. 비대칭 키에 대한 자세한 내용은 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-asymmetric-key-transact-sql)입니다.  
  
 비대칭 키는 강력한 이름 키 파일에서 가져올 수 있지만 내보낼 수 없으며 만료 옵션도 없습니다. 비대칭 키는 연결을 암호화할 수 없습니다.  
  
### <a name="using-an-asymmetric-key-in-sql-server"></a>SQL Server에서 비대칭 키 사용  
 비대칭 키는 데이터에 보안을 설정하거나 일반 텍스트를 서명하는 데 사용할 수 있습니다. 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 비대칭 키에 대한 추가 리소스를 보여 줍니다.  
  
|항목|설명|  
|-----------|-----------------|  
|[Transact-sql&#41;&#40;비대칭 키 만들기](/sql/t-sql/statements/create-asymmetric-key-transact-sql)|비대칭 키를 만들기 위한 명령에 대해 설명합니다.|  
|[SIGNBYASYMKEY &#40;Transact-sql&#41;](/sql/t-sql/functions/signbyasymkey-transact-sql)|개체를 서명하는 옵션을 표시합니다.|  
  
## <a name="tools"></a>도구  
 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 에서는 인증서 및 강력한 이름 키 파일을 생성하는 도구 및 유틸리티를 제공합니다. 이러한 도구는 키 생성 프로세스에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구문보다 더 많은 융통성을 제공합니다. 이러한 도구를 사용하여 보다 복잡한 키 길이가 있는 RSA 키를 만든 다음 이 키를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로 가져올 수 있습니다. 다음 표에서는 이러한 도구를 찾을 수 있는 위치를 보여 줍니다.  
  
|||  
|-|-|  
|도구|목적|  
|[makecert.exe](https://msdn2.microsoft.com/library/bfsktky3\(VS.80\).aspx)|인증서를 만듭니다.|  
|[sn.exe](https://msdn2.microsoft.com/library/k5b5tt23\(VS.80\).aspx)|대칭 키에 대한 강력한 이름을 만듭니다.|  
  
## <a name="related-tasks"></a>관련 작업  
 [암호화 알고리즘 선택](encryption/choose-an-encryption-algorithm.md)  
  
 [Transact-sql&#41;&#40;대칭 키 만들기](/sql/t-sql/statements/create-symmetric-key-transact-sql)  
  
 [Transact-sql&#41;인증서 &#40;만들기](/sql/t-sql/statements/create-certificate-transact-sql)  
  
## <a name="see-also"></a>참고 항목  
 [sys. 인증서 &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-certificates-transact-sql)   
 [투명한 데이터 암호화 &#40;TDE&#41;](encryption/transparent-data-encryption.md)  
  
