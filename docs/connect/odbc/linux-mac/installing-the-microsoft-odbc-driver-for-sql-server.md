---
title: Linux 및 macOS 기반 Microsoft ODBC Driver for SQL Server 설치 | Microsoft Docs
ms.custom: ''
ms.date: 12/05/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
ms.assetid: f78b81ed-5214-43ec-a600-9bfe51c5745a
author: MightyPen
ms.author: v-jizho2
manager: kenvh
ms.openlocfilehash: 3550e17c8f4d6384ceafabb77aa9ca70cd80c44b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63190673"
---
# <a name="installing-the-microsoft-odbc-driver-for-sql-server-on-linux-and-macos"></a>Linux 및 macOS 기반 Microsoft ODBC Driver for SQL Server 설치를 참조하세요
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

이 문서에서는 Linux 및 macOS 기반 [!INCLUDE[msCoName](../../../includes/msconame_md.md)]ODBC 드라이버[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], 그리고 SQL Server용 명령줄 도구(`bcp` 및 `sqlcmd`) 및 unixODBC 개발 헤더를 설치하는 방법에 대해 설명합니다.

## <a name="microsoft-odbc-driver-17-for-sql-server"></a>Microsoft ODBC Driver 17 for SQL Server 

> [!IMPORTANT]
> 일시적으로 사용할 수 있었던 v17 `msodbcsql` 패키지를 설치한 경우 `msodbcsql17` 패키지를 설치하기 전에 제거하는 것이 좋습니다. 그래야 충돌이 방지됩니다. `msodbcsql17` 패키지는 `msodbcsql` v13 패키지와 병렬로 설치할 수 있습니다.

### <a name="debian-8-and-9"></a>Debian 8 및 9
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Debian 8
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Debian 9
curl https://packages.microsoft.com/config/debian/9/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6-and-7"></a>RedHat Enterprise Server 6 및 7
```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#RedHat Enterprise Server 6
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo

#RedHat Enterprise Server 7
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo

exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11sp4-12-and-15"></a>SUSE Linux Enterprise Server 11SP4, 12 및 15

```
sudo su

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#SUSE Linux Enterprise Server 11 SP4
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo

#SUSE Linux Enterprise Server 12
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo

#SUSE Linux Enterprise Server 15
zypper ar https://packages.microsoft.com/config/sles/15/prod.repo
SUSEConnect -p sle-module-legacy/15/x86_64

exit
sudo ACCEPT_EULA=Y zypper install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1404-1604-1710-and-1804"></a>Ubuntu 14.04, 16.04, 17.10 및 18.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

#Download appropriate package for the OS version
#Choose only ONE of the following, corresponding to your OS version

#Ubuntu 14.04
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 16.04
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 18.04
curl https://packages.microsoft.com/config/ubuntu/18.04/prod.list > /etc/apt/sources.list.d/mssql-release.list

#Ubuntu 18.10
curl https://packages.microsoft.com/config/ubuntu/18.10/prod.list > /etc/apt/sources.list.d/mssql-release.list

exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql17
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```
> [!NOTE]
> - Ubuntu 18.04를 지원하려면 드라이버 버전 17.2 이상이 필요합니다.
> - Ubuntu 18.10을 지원하려면 드라이버 버전 17.3 이상이 필요합니다.   

### <a name="os-x-1011-el-capitan-macos-1012-sierra-macos-1013-high-sierra-and-macos-1014-mojave"></a>OS X 10.11(El Capitan), macOS 10.12(Sierra), macOS 10.13(High Sierra) 및 macOS 10.14(Mojave)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql17 mssql-tools
```

## <a name="microsoft-odbc-driver-131-for-sql-server"></a>Microsoft ODBC Driver 13.1 for SQL Server 

### <a name="debian-8"></a>Debian 8
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y yum install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo yum install unixODBC-devel
```

### <a name="suse-linux-enterprise-server-11"></a>SUSE Linux Enterprise Server 11

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/11/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo
exit
sudo ACCEPT_EULA=Y zypper install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y zypper install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo zypper install unixODBC-devel
``` 

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="ubuntu-1610"></a>Ubuntu 16.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql
# optional: for bcp and sqlcmd
sudo ACCEPT_EULA=Y apt-get install mssql-tools
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
source ~/.bashrc
# optional: for unixODBC development headers
sudo apt-get install unixodbc-dev
```

### <a name="os-x-1011-el-capitan-and-macos-1012-sierra"></a>OS X 10.11(El Capitan) 및 macOS 10.12(Sierra)

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="microsoft-odbc-driver-13-for-sql-server"></a>Microsoft ODBC Driver 13 for SQL Server

### <a name="redhat-enterprise-server-6"></a>RedHat Enterprise Server 6
```
sudo su
curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="redhat-enterprise-server-7"></a>RedHat Enterprise Server 7
```
sudo su
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
exit
sudo yum update
sudo yum remove unixODBC #to avoid conflicts
sudo ACCEPT_EULA=Y yum install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
sudo yum install unixODBC-utf16-devel #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1510"></a>Ubuntu 15.10
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/15.10/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="ubuntu-1604"></a>Ubuntu 16.04
```
sudo su 
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
exit
sudo apt-get update
sudo ACCEPT_EULA=Y apt-get install msodbcsql=13.0.1.0-1 mssql-tools=14.0.2.0-1
sudo apt-get install unixodbc-dev-utf16 #this step is optional but recommended*
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12

```
sudo su 
zypper ar https://packages.microsoft.com/config/sles/12/prod.repo 
zypper update 
sudo ACCEPT_EULA=Y zypper install msodbcsql-13.0.1.0-1 mssql-tools-14.0.2.0-1
zypper install unixODBC-utf16-devel
#Create symlinks for tools
ln -sfn /opt/mssql-tools/bin/sqlcmd-13.0.1.0 /usr/bin/sqlcmd 
ln -sfn /opt/mssql-tools/bin/bcp-13.0.1.0 /usr/bin/bcp
```

### <a name="offline-installation"></a>오프라인 설치
[!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC 드라이버 13을 인터넷 연결이 없는 컴퓨터에 설치하는 것을 선호하거나/그렇게 설치해야 하는 경우 패키지 종속성을 수동으로 해결해야 합니다. [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC 드라이버 13에는 다음과 같은 직접 종속성이 있습니다.
- Ubuntu: libc6(>= 2.21), libstdc++6(>= 4.9), libkrb5-3, libcurl3, openssl, debconf(>= 0.5), unixodbc(>= 2.3.1-1)
- Red Hat: ```glibc, e2fsprogs, krb5-libs, openssl, unixODBC```
- SuSE: ```glibc, libuuid1, krb5, openssl, unixODBC```

위의 각 패키지는 차례로 자체의 종속성이 있으며, 시스템에 해당 종속성이 있을 수도 있고 없는 경우도 있습니다. 이 문제에 대한 일반적인 해결 방법은 [Redhat](https://wiki.centos.org/HowTos/CreateLocalRepos), [Ubuntu](https://unix.stackexchange.com/questions/87130/how-to-quickly-create-a-local-apt-repository-for-random-packages-using-a-debian) 및 [SUSE](https://en.opensuse.org/Portal:Zypper) 등 사용하는 배포의 패키지 관리 설명서를 참조하세요.

또한 수동으로 모든 종속성 패키지를 다운로드하고 설치 컴퓨터에 함께 저장한 다음, 수동으로 각 패키지를 차례로 설치하여 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 패키지를 완성하는 것이 일반적인 방법입니다.

#### <a name="redhat-linux-enterprise-server-7"></a>Redhat Linux Enterprise Server 7
  - 최신 `msodbcsql` `.rpm` 다운로드 위치: https://packages.microsoft.com/rhel/7/prod/
  - 종속성 및 드라이버 설치
  
```
yum install glibc e2fsprogs krb5-libs openssl unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

#### <a name="ubuntu-1604"></a>Ubuntu 16.04
- 최신 `msodbcsql` `.deb` 다운로드 위치: https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql/ 
- 종속성 및 드라이버 설치 

```
sudo apt-get install libc6 libstdc++6 libkrb5-3 libcurl3 openssl debconf unixodbc unixodbc-dev #install dependencies
sudo dpkg -i msodbcsql_13.1.X.X-X_amd64.deb #install the Driver
```

#### <a name="suse-linux-enterprise-server-12"></a>SUSE Linux Enterprise Server 12
- 최신 `msodbcsql` `.rpm` 다운로드 위치: https://packages.microsoft.com/sles/12/prod/
- 종속성 및 드라이버 설치

```
zypper install glibc, libuuid1, krb5, openssl, unixODBC unixODBC-devel #install dependencies
sudo rpm -i  msodbcsql-13.1.X.X-X.x86_64.rpm #install the Driver
```

패키지 설치를 완료한 후 ldd를 실행하고 해당 출력에서 없는 라이브러리를 검사하여 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC 드라이버 13에서 모든 종속성을 발견할 수 있는지 확인할 수 있습니다.
```
ldd /opt/microsoft/msodbcsql/lib64/libmsodbcsql-*
```
  
## <a name="microsoft-odbc-driver-11-for-sql-server-on-linux"></a>Linux 기반 Microsoft ODBC Driver 11 for SQL Server

드라이버를 사용하려면 먼저 unixODBC 드라이버 관리자를 설치합니다. 자세한 내용은 [드라이버 관리자 설치](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)를 참조하세요.

**설치 단계**  

> [!IMPORTANT]  
> 이러한 지침은 Red Hat Linux용 설치 파일인 `msodbcsql-11.0.2270.0.tar.gz`를 참조합니다. SUSE Linux용 미리 보기를 설치하는 경우 파일 이름은 `msodbcsql-11.0.2260.0.tar.gz`입니다.  
  
드라이버를 설치하려면

1.  루트 권한이 있는지 확인합니다.  

2.  다운로드할 때 `msodbcsql-11.0.2270.0.tar.gz` 파일을 저장한 디렉터리로 변경합니다. Linux 버전과 일치하는 \*.tar.gz 파일이 있는지 확인합니다. 파일을 추출하려면 `tar xvzf msodbcsql-11.0.2270.0.tar.gz` 명령을 실행합니다.  
  
3.  `msodbcsql-11.0.2270.0` 디렉터리로 변경하면 **install.sh**라는 파일이 나타납니다.  
  
4.  사용 가능한 설치 옵션 목록을 보려면 다음 명령을 실행합니다. **./install.sh**  
  
5.  **odbcinst.ini**의 백업을 만듭니다. 드라이버 설치에서 **odbcinst.ini**를 업데이트합니다. odbcinst.ini에는 unixODBC 드라이버 관리자에 등록된 드라이버 목록이 있습니다. 컴퓨터에서 odbcinst.ini의 위치를 검색하려면 ```odbc_config --odbcinstini``` 명령을 실행합니다.  
  
6.  드라이버를 설치하기 전에 `./install.sh verify` 명령을 실행합니다. `./install.sh verify` 출력은 컴퓨터가 Linux 기반 ODBC 드라이버를 지원하는 데 필요한 소프트웨어가 있는지 보고합니다.  
  
7.  Linux 기반 ODBC 드라이버를 설치할 준비가 되면 `./install.sh install` 명령을 실행합니다. 설치 명령(`bin-dir` 또는 `lib-dir`)을 지정해야 하는 경우 **install** 옵션 다음에 명령을 지정합니다.  
  
8.  사용권 계약을 검토한 후 **YES** 를 입력하여 설치를 계속합니다.  
  
설치 시 드라이버는 `/opt/microsoft/msodbcsql/11.0.2270.0`에 저장됩니다. 드라이버 및 해당 지원 파일은 `/opt/microsoft/msodbcsql/11.0.2270.0`에 있어야 합니다.  
  
Linux 기반 Microsoft ODBC 드라이버가 제대로 등록되었는지 확인하려면 ```odbcinst -q -d -n "ODBC Driver 11 for SQL Server"``` 명령을 실행합니다.  
  
[Linux 기반 ODBC 드라이버에 대해 기존 MSDN C++ ODBC 샘플 사용](https://blogs.msdn.com/b/sqlblog/archive/2012/01/26/use-existing-msdn-c-odbc-samples-for-microsoft-linux-odbc-driver.aspx) 에서는 Linux 기반 ODBC 드라이버를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 연결하는 코드 샘플을 보여 줍니다.  
  
**제거**  
  
다음 명령을 실행하여 Linux 기반 ODBC 드라이버 11을 제거할 수 있습니다.  
  
1.  `rm -f /usr/bin/sqlcmd`
  
2.  `rm -f /usr/bin/bcp`  
  
3.  `rm -rf /opt/microsoft/msodbcsql`  
  
4.  `odbcinst -u -d -n "ODBC Driver 11 for SQL Server"`
  
## <a name="troubleshooting-connection-problems"></a>연결 문제 해결  
ODBC 드라이버를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 연결할 수 없는 경우 다음 정보를 사용하여 문제를 확인합니다.  
  
가장 일반적인 연결 문제는 UnixODBC 드라이버 관리자의 복사본이 두 개 설치되는 것입니다. libodbc\*.so\*에 대해 /usr을 검색합니다. 둘 이상의 파일 버전이 표시되면 둘 이상의 드라이버 관리자가 설치된 것일 수 있습니다. 애플리케이션이 잘못된 버전을 사용할 수 있습니다.
  
`/etc/odbcinst.ini` 파일을 이러한 항목과 함께 다음 섹션이 포함되도록 편집하여 연결 로그를 사용하도록 설정합니다.

```
[ODBC]
Trace = Yes
TraceFile = (path to log file, or /dev/stdout to output directly to the terminal)
```  
  
다른 연결 오류가 발생하고 로그 파일이 표시되지 않으면 컴퓨터에 드라이버 관리자의 복사본이 두 개 있을 수 있습니다. 그렇지 않으면 로그 출력은 다음과 같은 형태가 됩니다.  
  
```  
[ODBC][28783][1321576347.077780][SQLDriverConnectW.c][290]  
        Entry:  
            Connection = 0x17c858e0  
            Window Hdl = (nil)  
            Str In = [DRIVER={ODBC Driver 13 for SQL Server};SERVER={contoso.com};Trusted_Connection={YES};WSID={mydb.contoso.com};AP...][length = 139 (SQL_NTS)]  
            Str Out = (nil)  
            Str Out Max = 0  
            Str Out Ptr = (nil)  
            Completion = 0  
        UNICODE Using encoding ASCII 'UTF8' and UNICODE 'UTF16LE'  
```  
  
예를 들어 ASCII 문자 인코딩이 UTF-8이 아닌 경우 
  
```  
UNICODE Using encoding ASCII 'ISO8859-1' and UNICODE 'UCS-2LE'  
```  
  
설치된 드라이버 관리자가 둘 이상이면 애플리케이션에서 잘못된 관리자를 사용 중이거나 드라이버 관리자가 올바르게 빌드되지 않은 것입니다.  
  
연결 오류를 해결하는 방법에 대한 자세한 내용은 다음을 참조하세요.  
  
-   [SQL 연결 문제를 해결하는 단계](https://blogs.msdn.com/b/sql_protocols/archive/2008/04/30/steps-to-troubleshoot-connectivity-issues.aspx)  
  
-   [SQL Server 2005 연결 문제 해결 - 1부](https://blogs.msdn.com/b/sql_protocols/archive/2005/10/22/sql-server-2005-connectivity-issue-troubleshoot-part-i.aspx)  
  
-   [연결 링 버퍼를 사용하여 SQL Server 2008의 연결 문제 해결](https://blogs.msdn.com/b/sql_protocols/archive/2008/05/20/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer.aspx)  
  
-   [SQL Server 인증 문제 해결사](https://blogs.msdn.com/b/sqlsecurity/archive/2010/03/29/sql-server-authentication-troubleshooter.aspx)  
  
-   [오류 세부 정보(https://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=11001)](https://www.microsoft.com/products/ee/transform.aspx?ProdName=Microsoft+SQL+Server&EvtSrc=MSSQLServer&EvtID=001)  
  
    URL(11001)에서 지정된 오류 번호가 표시되는 오류와 일치하도록 변경되어야 합니다.  
  
## <a name="driver-files"></a>드라이버 파일
Linux 및 MacOS 기반 ODBC 드라이버는 다음 구성 요소로 구성됩니다.

### <a name="linux"></a>Linux

|구성 요소|설명|  
|---------------|-----------------|  
|libmsodbcsql-17.X.so.X.X 또는 libmsodbcsql-13.X.so.X.X|드라이버 기능이 모두 포함된 공유 개체(`so`) 동적 라이브러리 파일입니다. 이 파일은 드라이버 17의 경우 `/opt/microsoft/msodbcsql17/lib64/` 및 드라이버 13의 경우 `/opt/microsoft/msodbcsql/lib64/`에 설치됩니다.|  
|`msodbcsqlr17.rll` 또는 `msodbcsqlr13.rll`|드라이버 라이브러리에 대한 해당 리소스 파일입니다. 이 파일은 `[driver .so directory]../share/resources/en_US/`에 설치됩니다.| 
|msodbcsql.h|드라이버를 사용하는 데 필요한 새 정의를 모두 포함하는 헤더 파일입니다.<br /><br /> **참고:**  동일한 프로그램에서 msodbcsql.h 및 odbcss.h를 참조할 수 없습니다.<br /><br /> msodbcsql.h는 드라이버 17의 경우 `/opt/microsoft/msodbcsql17/include/` 및 드라이버 13의 경우 `/opt/microsoft/msodbcsql/include/`에 설치됩니다. |
|LICENSE.txt|최종 사용자 사용권 계약의 사용 약관을 포함하는 텍스트 파일입니다. 이 파일은 드라이버 17의 경우 `/usr/share/doc/msodbcsql17/` 및 드라이버 13의 경우 `/usr/share/doc/msodbcsql/`에 저장됩니다.|
|RELEASE_NOTES|릴리스 정보를 포함하는 텍스트 파일입니다. 이 파일은 드라이버 17의 경우 `/usr/share/doc/msodbcsql17/` 및 드라이버 13의 경우 `/usr/share/doc/msodbcsql/`에 저장됩니다.|


### <a name="macos"></a>MacOS

|구성 요소|설명|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib 또는 libmsodbcsql.13.dylib|드라이버 기능이 모두 포함된 동적 라이브러리(`dylib`) 파일입니다. 이 파일은 `/usr/local/lib/`에 설치됩니다.|  
|`msodbcsqlr17.rll` 또는 `msodbcsqlr13.rll`|드라이버 라이브러리에 대한 해당 리소스 파일입니다. 이 파일은 드라이버 17의 경우 `[driver .dylib directory]../share/msodbcsql17/resources/en_US/` 및 드라이버 13의 경우 `[driver .dylib directory]../share/msodbcsql/resources/en_US/`에 설치됩니다. | 
|msodbcsql.h|드라이버를 사용하는 데 필요한 새 정의를 모두 포함하는 헤더 파일입니다.<br /><br /> **참고:**  동일한 프로그램에서 msodbcsql.h 및 odbcss.h를 참조할 수 없습니다.<br /><br /> msodbcsql.h는 드라이버 17의 경우 `/usr/local/include/msodbcsql17/` 및 드라이버 13의 경우 `/usr/local/include/msodbcsql/`에 설치됩니다. |
|LICENSE.txt|최종 사용자 사용권 계약의 사용 약관을 포함하는 텍스트 파일입니다. 이 파일은 드라이버 17의 경우 `/usr/local/share/doc/msodbcsql17/` 및 드라이버 13의 경우 `/usr/local/share/doc/msodbcsql/`에 저장됩니다. |
|RELEASE_NOTES|릴리스 정보를 포함하는 텍스트 파일입니다. 이 파일은 드라이버 17의 경우 `/usr/local/share/doc/msodbcsql17/` 및 드라이버 13의 경우 `/usr/local/share/doc/msodbcsql/`에 저장됩니다. |

## <a name="resource-file-loading"></a>리소스 파일 로드

드라이버가 작동하려면 리소스 파일을 로드해야 합니다. 이 파일의 이름은 드라이버 버전에 따라 `msodbcsqlr17.rll` 또는 `msodbcsqlr13.rll`입니다. `.rll` 파일의 위치는 위의 표에서 설명했듯이 드라이버 자체(`so` 또는 `dylib`)의 위치에 대한 상대 위치입니다. 버전 17.1 현재 `.rll`을 상대 경로에서 로드하는 데 실패한 경우 기본 디렉터리에서도 로드를 시도합니다. 기본 리소스 파일 경로:

Linux: `/opt/microsoft/msodbcsql17/share/resources/en_US/`

MacOS: `/usr/local/share/msodbcsql17/resources/en_US/`


  
## <a name="see-also"></a>참고 항목

[드라이버 관리자 설치](../../../connect/odbc/linux-mac/installing-the-driver-manager.md)

[릴리스 정보](../../../connect/odbc/linux-mac/release-notes-odbc-sql-server-linux-mac.md)

[시스템 요구 사항](../../../connect/odbc/linux-mac/system-requirements.md)
