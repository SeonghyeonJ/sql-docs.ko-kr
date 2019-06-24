---
title: 사용자 지정 키 저장소 공급자 | Microsoft Docs
ms.custom: ''
ms.date: 07/12/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a6166d7d-ef34-4f87-bd1b-838d3ca59ae7
ms.author: v-chojas
manager: jroth
author: MightyPen
ms.openlocfilehash: 84e729cd60a28ff8a58760bd3810ec538a327007
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800493"
---
# <a name="custom-keystore-providers"></a>사용자 지정 키 저장소 공급자
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="overview"></a>개요

SQL Server 2016의 열 암호화 기능에는 암호화 된 열 암호화 키 (ECEKs) 서버에 저장 된 클라이언트에서 검색 되며 다음 암호화 된 열에 저장 된 데이터에 액세스 하기 위해 열 암호화 키 (Cek)를 해독할 필요 합니다. ECEKs 열 마스터 키 (Cmk) 하 여 암호화 됩니다 이며 CMK의 보안 열 암호화 보안에 중요 합니다. CMK은 안전한 위치에 저장 해야 따라서 열 암호화 키 저장소 공급자의 목적은 ODBC 드라이버가 이러한 안전 하 게 액세스를 허용 하는 인터페이스가 Cmk 저장을 제공 하는 것입니다. 자신의 보안 저장소를 사용 하 여 사용자에 대 한 사용자 지정 키 저장소 공급자 인터페이스 CEK 암호화 및 암호 해독 하는 데 사용할 수 있는 ODBC 드라이버에 대 한 CMK의 보안 저장소에 대 한 액세스를 구현 하기 위한 프레임 워크를 제공 합니다.

포함 하 고 하나를 관리 하는 각 키 저장소 공급자 또는 공급자가 문자열 형식의-키 경로로 식별 되는 자세한 Cmk 정의 합니다. 이 공급자에 의해 정의 된 문자열도 암호화 알고리즘을 함께 사용할 수 있습니다 CEK의 암호화 및 암호 해독 된 ECEK의 수행. 데이터베이스의 암호화 메타 데이터에 알고리즘을 ECEK 및 공급자의 이름과 함께 저장 됩니다. 참조 [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) 하 고 [CREATE COLUMN ENCRYPTION KEY](../../t-sql/statements/create-column-encryption-key-transact-sql.md) 자세한 내용은 합니다. 따라서 키 관리의 두 가지 기본 작업은 다음과 같습니다.

```
CEK = DecryptViaCEKeystoreProvider(CEKeystoreProvider_name, Key_path, Key_algorithm, ECEK)

-and-

ECEK = EncryptViaCEKeystoreProvider(CEKeyStoreProvider_name, Key_path, Key_algorithm, CEK)
```

여기서는 `CEKeystoreProvider_name` 특정 열 암호화 키 저장소 공급자 (CEKeystoreProvider)를 식별 하는 다른 인수 (E) CEK 암호화/해독 하는 CEKeystoreProvider에서 사용 됩니다. 알고리즘 및 ECEK 값은 CEK 메타 데이터에서 제공 하는 동안 이름 및 keypath CMK 메타 데이터에서 제공 됩니다. 여러 키 저장소 공급자 기본 기본 제공 공급자와 함께 존재할 수 있습니다. CEK를 해야 하는 작업을 수행 하면 드라이버는 CMK 메타 데이터를 사용 하 여 이름별로 적절 한 키 저장소 공급자를 찾습니다 및으로 표현 될 수 있는 암호 해독 작업을 실행:

```
CEK = CEKeyStoreProvider_specific_decrypt(Key_path, Key_algorithm, ECEK)
```

키 관리 도구 CMK 만들기 등 회전; 작업을 구현 하려면 이렇게 해야 드라이버가 Cek를 암호화 하지 않아도 있지만 그러려면 역 작업을 수행 합니다.

```
ECEK = CEKeyStoreProvider_specific_encrypt(Key_path, Key_algorithm, CEK)
```

### <a name="cekeystoreprovider-interface"></a>CEKeyStoreProvider 인터페이스

이 문서는 CEKeyStoreProvider 인터페이스를 자세히 설명합니다. 이 인터페이스를 구현 하는 키 저장소 공급자를 SQL Server 용 Microsoft ODBC 드라이버에서 사용할 수 있습니다. CEKeyStoreProvider 구현자가이 가이드를 사용 하 여 드라이버에서 사용할 수 있는 사용자 지정 키 저장소 공급자를 개발할 수 있습니다.

키 저장소 공급자 라이브러리 ("공급자 라이브러리")는 ODBC 드라이버에서 로드할 수 있는 동적 연결 라이브러리 하며 하나 이상의 키 저장소 공급자를 포함 합니다. 기호 `CEKeystoreProvider` 공급자 라이브러리를 통해 내보내야 하며 null로 끝나는 배열에 대 한 포인터의 주소가 될 `CEKeystoreProvider` 라이브러리 내에서 각 키 저장소 공급자에 대 한 구조입니다.

`CEKeystoreProvider` 구조 단일 키 저장소 공급자의 진입점을 정의 합니다.

```
typedef struct CEKeystoreProvider {
    wchar_t *Name;
    int (*Init)(CEKEYSTORECONTEXT *ctx, errFunc *onError);
    int (*Read)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int *len);
    int (*Write)(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len);
    int (*DecryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *ecek,
                        unsigned short ecekLen,
                        unsigned char **cekOut,
                        unsigned short *cekLen);
    int (*EncryptCEK)(  CEKEYSTORECONTEXT *ctx,
                        errFunc *onError,
                        const wchar_t *keyPath,
                        const wchar_t *alg,
                        unsigned char *cek,
                        unsigned short cekLen,
                        unsigned char **ecekOut,
                        unsigned short *ecekLen);
    void (*Free)();
} CEKEYSTOREPROVIDER;
```

|필드 이름|설명|
|:--|:--|
|`Name`|키 저장소 공급자의 이름입니다. 않아야 드라이버에 의해 또는이 라이브러리에 있는 이전에 로드 하는 다른 키 저장소 공급자와 동일 합니다. Null로 종료된 와이드 문자*열입니다.|
|`Init`|초기화 함수입니다. 초기화 함수를 필요 하지 않은 경우이 필드는 null 일 수 있습니다.|
|`Read`|공급자 함수를 읽습니다. 필요 하지 않은 경우 null 일 수 있습니다.|
|`Write`|공급자 쓰기 함수입니다. 읽기 null이 아닌 경우 필요 합니다. 필요 하지 않은 경우 null 일 수 있습니다.|
|`DecryptCEK`|ECEK 암호 해독 함수입니다. 이 함수는 키 저장소 공급자의 존재 여부에 대 한 이유 이며 null 일 수 없습니다.|
|`EncryptCEK`|CEK 암호화 함수입니다. 드라이버는이 함수를 호출 하지 않습니다 하지만 ECEK 생성에 프로그래밍 방식으로 액세스할 수 있도록 키 관리 도구에서 제공 됩니다. 필요 하지 않은 경우 null 일 수 있습니다.|
|`Free`|종료 함수입니다. 필요 하지 않은 경우 null 일 수 있습니다.|

무료를 제외한 모든이 인터페이스의 함수 매개 변수의 쌍이 있을 **ctx** 하 고 **onError**합니다. 전자는 함수를 호출, 후자를 사용 하는 동안 오류를 보고 하는 것에 대 한 컨텍스트를 식별 합니다. 참조 [컨텍스트](#context-association) 하 고 [오류 처리](#error-handling) 아래 자세한 내용은 합니다.

```
int Init(CEKEYSTORECONTEXT *ctx, errFunc onError);
```
공급자가 정의한 초기화 함수에 대 한 자리 표시자 이름입니다. 드라이버는 공급자를 로드 되었지만 ECEK 암호를 해독 하거나 Read()/Write() 하는 데 필요한 시간 첫 번째 요청 후이 함수를 한 번 호출 합니다. 이 함수를 사용 하 여 필요한 모든 초기화를 수행 합니다. 

|인수|설명|
|:--|:--|
|`ctx`|[입력] 작업 컨텍스트입니다.|
|`onError`|[입력] 오류 보고 함수입니다.|
|`Return Value`|나타내는 성공 또는 실패를 나타내는 0 0이 아닌 값을 반환 합니다.|

```
int Read(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int *len);
```

통신 공급자가 정의한 함수에 대 한 자리 표시자 이름입니다. 드라이버 응용 프로그램 요청 (이전에 작성-간) 공급자에서 SQL_COPT_SS_CEKEYSTOREDATA 연결 특성을 사용 하 여 공급자에서 임의 데이터를 읽을 수 있게 되어 데이터를 읽을 때이 함수를 호출 합니다. 참조 [키 저장소 공급자와의 통신](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) 자세한 내용은 합니다.

|인수|설명|
|:--|:--|
|`ctx`|[입력] 작업 컨텍스트입니다.|
|`onError`|[입력] 오류 보고 함수입니다.|
|`data`|[출력] 공급자는 응용 프로그램에서 읽을 데이터를 쓰는 버퍼에 대 한 포인터입니다. CEKEYSTOREDATA 구조의 데이터 필드에 해당 합니다.|
|`len`|[InOut] 길이 값에 대 한 포인터 데이터 버퍼의 최대 길이이 입력 시 및 공급자는 쓰지 개 * len 바이트. 반환 될 때 공급자를 업데이트 해야 * len 실제로 쓴 바이트 수를 사용 하 여 합니다.|
|`Return Value`|나타내는 성공 또는 실패를 나타내는 0 0이 아닌 값을 반환 합니다.|

```
int Write(CEKEYSTORECONTEXT *ctx, errFunc onError, void *data, unsigned int len);
```
통신 공급자가 정의한 함수에 대 한 자리 표시자 이름입니다. 드라이버 응용 프로그램 요청 데이터 공급자에 임의의 데이터를 쓸 수 있게 SQL_COPT_SS_CEKEYSTOREDATA 연결 특성을 사용 하 여 공급자를 쓸 때이 함수를 호출 합니다. 참조 [키 저장소 공급자와의 통신](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#communicating-with-keystore-providers) 자세한 내용은 합니다.

|인수|설명|
|:--|:--|
|`ctx`|[입력] 작업 컨텍스트입니다.|
|`onError`|[입력] 오류 보고 함수입니다.|
|`data`|[입력] 읽을 공급자에 대 한 데이터를 포함 하는 버퍼에 대 한 포인터입니다. CEKEYSTOREDATA 구조의 데이터 필드에 해당 합니다. 공급자가이 버퍼에서 읽을 len 바이트 보다 해야 합니다.|
|`len`|[입력] 데이터의 사용 가능한 바이트의 수입니다. CEKEYSTOREDATA 구조의 dataSize 필드에 해당 합니다.|
|`Return Value`|나타내는 성공 또는 실패를 나타내는 0 0이 아닌 값을 반환 합니다.|

```
int (*DecryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen);
```
ECEK 암호 해독 공급자가 정의한 함수에 대 한 자리 표시자 이름입니다. 드라이버는 ECEK CEK이이 공급자와 연결 하는 CMK로 암호화 된 암호를 해독 하려면이 함수를 호출 합니다.

|인수|설명|
|:--|:--|
|`ctx`|[입력] 작업 컨텍스트입니다.|
|`onError`|[입력] 오류 보고 함수입니다.|
|`keyPath`|[입력] 값을 [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) CMK 지정된 ECEK가 참조에 대 한 메타 데이터 특성입니다. Null로 종료된 와이드 문자*열입니다. 이 공급자가 처리 하는 CMK를 식별 하는 것이입니다.|
|`alg`|[입력] 값을 [알고리즘](../../t-sql/statements/create-column-encryption-key-transact-sql.md) 지정된 ECEK에 대 한 메타 데이터 특성입니다. Null로 종료된 와이드 문자*열입니다. 지정 된 ECEK 암호화에 사용 된 암호화 알고리즘을 식별 하는 것이입니다.|
|`ecek`|[입력] 암호 해독 된 ECEK에 대 한 포인터입니다.|
|`ecekLen`|[입력] ECEK의 길이입니다.|
|`cekOut`|[출력] 공급자는 암호 해독 된 ECEK에 대 한 메모리를 할당 하 고 cekOut 가리키는 포인터에 대 한 해당 주소를 작성 됩니다. 이 블록을 사용 하 여 메모리를 확보 하려면 수 있어야 합니다 [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) (Linux/Mac) 함수를 무료 또는 합니다. 공급자 설정 됩니다 메모리가 없습니다. 할당 오류로 인해 이거나 인 경우 * cekOut null 포인터입니다.|
|`cekLen`|[출력] 공급자는 쓸 cekLen 가리키는 주소에 작성 하는 암호 해독 된 ECEK의 길이 * * cekOut 합니다.|
|`Return Value`|나타내는 성공 또는 실패를 나타내는 0 0이 아닌 값을 반환 합니다.|

```
int (*EncryptCEK)( CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg, unsigned char *cek,unsigned short cekLen, unsigned char **ecekOut, unsigned short *ecekLen);
```
CEK 암호화 공급자가 정의한 함수에 대 한 자리 표시자 이름입니다. 드라이버는이 함수를 호출 하지 않거나 ODBC 인터페이스를 통해 해당 기능을 노출 하지 않습니다 하지만 ECEK 생성에 프로그래밍 방식으로 액세스할 수 있도록 키 관리 도구에서 제공 됩니다.

|인수|설명|
|:--|:--|
|`ctx`|[입력] 작업 컨텍스트입니다.|
|`onError`|[입력] 오류 보고 함수입니다.|
|`keyPath`|[입력] 값을 [KEY_PATH](../../t-sql/statements/create-column-master-key-transact-sql.md) CMK 지정된 ECEK가 참조에 대 한 메타 데이터 특성입니다. Null로 종료된 와이드 문자*열입니다. 이 공급자가 처리 하는 CMK를 식별 하는 것이입니다.|
|`alg`|[입력] 값을 [알고리즘](../../t-sql/statements/create-column-encryption-key-transact-sql.md) 지정된 ECEK에 대 한 메타 데이터 특성입니다. Null로 종료된 와이드 문자*열입니다. 지정 된 ECEK 암호화에 사용 된 암호화 알고리즘을 식별 하는 것이입니다.|
|`cek`|[입력] CEK 암호화에 대 한 포인터입니다.|
|`cekLen`|[입력] CEK의 길이입니다.|
|`ecekOut`|[출력] 공급자는 암호화 된 CEK에 대 한 메모리를 할당 하 고 ecekOut 가리키는 포인터에 대 한 해당 주소를 작성 됩니다. 이 블록을 사용 하 여 메모리를 확보 하려면 수 있어야 합니다 [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) (Windows) (Linux/Mac) 함수를 무료 또는 합니다. 공급자 설정 됩니다 메모리가 없습니다. 할당 오류로 인해 이거나 인 경우 * ecekOut null 포인터입니다.|
|`ecekLen`|[출력] 공급자는 쓸 ecekLen 가리키는 주소에 기록 하기는 암호화 된 CEK의 길이 * * ecekOut 합니다.|
|`Return Value`|나타내는 성공 또는 실패를 나타내는 0 0이 아닌 값을 반환 합니다.|

```
void (*Free)();
```
공급자가 정의한 종료 함수에 대 한 자리 표시자 이름입니다. 드라이버는 프로세스의 정상 종료 시이 함수를 호출할 수 있습니다.

> [!NOTE]
> *와이드 문자 문자열은 SQL Server 저장 하는 방법으로 인해 2 바이트 문자 (u t F-16)입니다.*


### <a name="error-handling"></a>오류 처리

공급자를 처리 하는 동안 오류가 발생할 수 있습니다, 메커니즘 부울 성공/실패 보다 구체적인 세부 정보에서 오류 드라이버를 다시 보고할 수 있도록 제공 됩니다. 대부분의 함수 매개 변수의 쌍이 있을 **ctx** 하 고 **onError**, 성공/실패 반환 값 외에도이 목적을 위해 함께 사용 됨.

합니다 **ctx** 공급자 작업을 발생 하는 컨텍스트를 식별 하는 매개 변수입니다.

합니다 **onError** 매개 변수는 다음과 같은 프로토타입 사용 하 여 오류 보고 함수를 가리킵니다.

`typedef void errFunc(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...);`

|인수|설명|
|:--|:--|
|`ctx`|[입력] 오류를 보고 하는 컨텍스트.|
|`msg`|[입력] 보고서에 오류 메시지입니다. Null로 종료된 와이드 문자열입니다. 있어야 매개 변수가 있는 정보를 허용 하려면이 문자열에서 허용 하는 폼의 insert 형식 시퀀스를 포함할 수 있습니다 합니다 [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) 함수입니다. 아래 설명 된 대로이 매개 변수에서 확장 된 기능을 지정할 수 있습니다.|
|...|[입력] 적절 하 게, 메시지의 형식 지정자에 맞게 추가 variadic 매개 변수입니다.|

오류가 발생 하는 경우를 보고 하려면 드라이버 및에 서식을 지정할 선택적 추가 매개 변수를 사용 하 여 오류 메시지에서 컨텍스트 매개 변수를 제공 하는 공급자 호출 onError 공급자 함수에 전달 합니다. 공급자 하나 공급자 함수 호출 내에서 연속적으로 여러 오류 메시지를 게시 하려면이 함수의 여러 번을 호출할 수 있습니다. 예를 들어

```
    if (!doSomething(...))
    {
        onError(ctx, L"An error occurred in doSomething.");
        onError(ctx, L"Additional error message with more details.");
        return 0;
    }
```


`msg` 추가 확장을 사용할 수 있지만 매개 변수는 일반적으로 와이드 문자 문자열:

사용 하 여 특별 한 미리 정의 된 값 중 하나로 IDS_MSG 매크로 사용 하 여 이미 존재 하는 일반 오류 메시지 및 현지화 폼 드라이버에 활용할 수 있습니다. 예를 들어, 메모리 할당 실패 하면 공급자는 `IDS_S1_001` "메모리 할당 오류" 메시지를 사용할 수 있습니다.

`onError(ctx, IDS_MSG(IDS_S1_001));`

드라이버에서 인식할 수를 사용 하 여 오류를 공급자 함수는 오류를 반환 해야 합니다. 이 ODBC 작업의 컨텍스트에서 수행 되 면 게시 된 오류 표준 ODBC 진단 메커니즘을 통해 연결 하거나 문 핸들에 액세스할 수 있게 됩니다 (`SQLError`하십시오 `SQLGetDiagRec`, 및 `SQLGetDiagField`).


### <a name="context-association"></a>컨텍스트 연결

`CEKEYSTORECONTEXT` 공급자 작업이 실행 되는 ODBC 컨텍스트를 확인 하려면 오류 콜백 함수에 대 한 컨텍스트를 제공 하는 것 외에도 구조를 사용할 수도 있습니다. 예를 들어 각 이러한 컨텍스트 데이터를 연결 하는 공급자를 사용 하면이 연결 구성을 구현 하려면. 이 작업을 위해 구조 환경, 연결 및 문 컨텍스트에 해당 하는 3 불투명 포인터를 포함 합니다.

```
typedef struct CEKeystoreContext
{
void *envCtx;
void *dbcCtx;
void *stmtCtx;
} CEKEYSTORECONTEXT;
```

|필드|설명|
|:--|:--|
|`envCtx`|환경 컨텍스트입니다.|
|`dbcCtx`|한 연결 컨텍스트입니다.|
|`stmtCtx`|문 컨텍스트입니다.|

동일 하지는 않습니다 ODBC 핸들을 해당 하는 동안 사용할 수 있는 고유 식별자로 핸들에 대 한 불투명 값은 이러한 각 컨텍스트: 경우 처리할 *X* 컨텍스트 값을 사용 하 여 연결 *Y*, 한 다음 다른 환경, 연결 또는 문 핸들이 없는지와 동일한 시간에 동시에 존재 *X* 의 상황에 맞는 값이 포함 됩니다 *Y*, 다른 상황에 맞는 값이 없는와 연결 하 고 처리할 *X*합니다. 공급자 작업을 수행 중인 부족 (예: 로드 하 고 구성 공급자가 문 핸들이 없는 SQLSetConnectAttr 호출) 특정 핸들 컨텍스트를 해당 구조에 대 한 컨텍스트 값은 null입니다.


## <a name="example"></a>예제

### <a name="keystore-provider"></a>키 저장소 공급자

다음 코드는 최소한의 키 저장소 공급자 구현의 예입니다.

```
/* Custom Keystore Provider Example

Windows:   compile with cl MyKSP.c /LD /MD /link /out:MyKSP.dll
Linux/Mac: compile with gcc -fshort-wchar -fPIC -o MyKSP.so -shared MyKSP.c

 */

#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#endif

#include <stdlib.h>
#include <sqltypes.h>
#include "msodbcsql.h"
#include <sql.h>
#include <sqlext.h>

int __stdcall KeystoreInit(CEKEYSTORECONTEXT *ctx, errFunc *onError) {
    printf("KSP Init() function called\n");
    return 1;
}

static unsigned char *g_encryptKey;
static unsigned int g_encryptKeyLen;

int __stdcall KeystoreWrite(CEKEYSTORECONTEXT *ctx, errFunc *onError, void *data, unsigned int len) {
    printf("KSP Write() function called (%d bytes)\n", len);
    if (len) {
        if (g_encryptKey)
            free(g_encryptKey);
        g_encryptKey = malloc(len);
        if (!g_encryptKey) {
            onError(ctx, L"Memory Allocation Error");
            return 0;
        }
        memcpy(g_encryptKey, data, len);
        g_encryptKeyLen = len;
    }
    return 1;
}

// Very simple "encryption" scheme - rotating XOR with the key
int __stdcall KeystoreDecrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError, const wchar_t *keyPath, const wchar_t *alg,
    unsigned char *ecek, unsigned short ecekLen, unsigned char **cekOut, unsigned short *cekLen) {
    unsigned int i;
    printf("KSP Decrypt() function called (keypath=%S alg=%S ecekLen=%u)\n", keyPath, alg, ecekLen);
    if (wcscmp(keyPath, L"TheOneAndOnlyKey")) {
        onError(ctx, L"Invalid key path");
        return 0;
    }
    if (wcscmp(alg, L"none")) {
        onError(ctx, L"Invalid algorithm");
        return 0;
    }
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
#ifndef _WIN32
    *cekOut = malloc(ecekLen);
#else
    *cekOut = LocalAlloc(LMEM_FIXED, ecekLen);
#endif
    if (!*cekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *cekLen = ecekLen;
    for (i = 0; i < ecekLen; i++)
        (*cekOut)[i] = ecek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

// Note that in the provider interface, this function would be referenced via the CEKEYSTOREPROVIDER
// structure. However, that does not preclude keystore providers from exporting their own functions,
// as illustrated by this example where the encryption is performed via a separate function (with a
// different prototype than the one in the KSP interface.)
#ifdef _WIN32
__declspec(dllexport)
#endif
int KeystoreEncrypt(CEKEYSTORECONTEXT *ctx, errFunc *onError,
    unsigned char *cek, unsigned short cekLen,
    unsigned char **ecekOut, unsigned short *ecekLen) {
    unsigned int i;
    printf("KSP Encrypt() function called (cekLen=%u)\n", cekLen);
    if (!g_encryptKey) {
        onError(ctx, L"Keystore provider not initialized with key");
        return 0;
    }
    *ecekOut = malloc(cekLen);
    if (!*ecekOut) {
        onError(ctx, L"Memory Allocation Error");
        return 0;
    }
    *ecekLen = cekLen;
    for (i = 0; i < cekLen; i++)
        (*ecekOut)[i] = cek[i] ^ g_encryptKey[i % g_encryptKeyLen];
    return 1;
}

CEKEYSTOREPROVIDER MyCustomKSPName_desc = {
    L"MyCustomKSPName",
    KeystoreInit,
    0,
    KeystoreWrite,
    KeystoreDecrypt,
    0
};

#ifdef _WIN32
__declspec(dllexport)
#endif
CEKEYSTOREPROVIDER *CEKeystoreProvider[] = {
    &MyCustomKSPName_desc,
    0
};
```

### <a name="odbc-application"></a>ODBC 응용 프로그램

다음 코드는 위의 키 저장소 공급자를 사용 하는 데모 응용 프로그램입니다. 응용 프로그램 이진 파일을 동일한 디렉터리에 공급자 라이브러리와는 연결 문자열 지정 (또는 포함 하는 DSN 지정)를 실행 하는 경우 확인을 `ColumnEncryption=Enabled` 설정 합니다.

```
/*
 Example application for demonstration of custom keystore provider usage

Windows:   compile with cl /MD kspapp.c /link odbc32.lib
Linux/Mac: compile with gcc -o kspapp -fshort-wchar kspapp.c -lodbc -ldl
 
 usage: kspapp connstr

 */

#define KSPNAME L"MyCustomKSPName"
#define PROV_ENCRYPT_KEY "JHKCWYT06N3RG98J0MBLG4E3"

#include <stdio.h>
#include <stdlib.h>
#ifdef _WIN32
#include <windows.h>
#else
#define __stdcall
#include <dlfcn.h>
#endif
#include <sql.h>
#include <sqlext.h>
#include "msodbcsql.h"

/* Convenience functions */

int checkRC(SQLRETURN rc, char *msg, int ret, SQLHANDLE h, SQLSMALLINT ht) {
    if (rc == SQL_ERROR) {
        fprintf(stderr, "Error occurred upon %s\n", msg);
        if (h) {
            SQLSMALLINT i = 0;
            SQLSMALLINT outlen = 0;
            char errmsg[1024];
            while ((rc = SQLGetDiagField(
                ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
                || rc == SQL_SUCCESS_WITH_INFO) {
                fprintf(stderr, "Err#%d: %s\n", i, errmsg);
            }
        }
        if (ret)
            exit(ret);
        return 0;
    }
    else if (rc == SQL_SUCCESS_WITH_INFO && h) {
        SQLSMALLINT i = 0;
        SQLSMALLINT outlen = 0;
        char errmsg[1024];
        printf("Success with info for %s:\n", msg);
        while ((rc = SQLGetDiagField(
            ht, h, ++i, SQL_DIAG_MESSAGE_TEXT, errmsg, sizeof(errmsg), &outlen)) == SQL_SUCCESS
            || rc == SQL_SUCCESS_WITH_INFO) {
            fprintf(stderr, "Msg#%d: %s\n", i, errmsg);
        }
    }
    return 1;
}

void postKspError(CEKEYSTORECONTEXT *ctx, const wchar_t *msg, ...) {
    if (msg > (wchar_t*)65535)
        wprintf(L"Provider emitted message: %s\n", msg);
    else
        wprintf(L"Provider emitted message ID %d\n", msg);
}

int main(int argc, char **argv) {
    char sqlbuf[1024];
    SQLHENV env;
    SQLHDBC dbc;
    SQLHSTMT stmt;
    SQLRETURN rc;
    unsigned char CEK[32];
    unsigned char *ECEK;
    unsigned short ECEKlen;
#ifdef _WIN32
    HMODULE hProvLib;
#else
    void *hProvLib;
#endif
    CEKEYSTORECONTEXT ctx = {0};
    CEKEYSTOREPROVIDER **ppKsp, *pKsp;
    int(__stdcall *pEncryptCEK)(CEKEYSTORECONTEXT *, errFunc *, unsigned char *, unsigned short, unsigned char **, unsigned short *);
    int i;
    if (argc < 2) {
        fprintf(stderr, "usage: kspapp connstr\n");
        return 1;
    }

    /* Load the provider library */
#ifdef _WIN32
    if (!(hProvLib = LoadLibrary("MyKSP.dll"))) {
#else
    if (!(hProvLib = dlopen("./MyKSP.so", RTLD_NOW))) {
#endif
        fprintf(stderr, "Error loading KSP library\n");
        return 2;
    }
#ifdef _WIN32
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)GetProcAddress(hProvLib, "CEKeystoreProvider"))) {
#else
    if (!(ppKsp = (CEKEYSTOREPROVIDER**)dlsym(hProvLib, "CEKeystoreProvider"))) {
#endif
        fprintf(stderr, "The export CEKeystoreProvider was not found in the KSP library\n");
        return 3;
    }
    while (pKsp = *ppKsp++) {
        if (!memcmp(KSPNAME, pKsp->Name, sizeof(KSPNAME)))
            goto FoundProv;
    }
    fprintf(stderr, "Could not find provider in the library\n");
    return 4;
FoundProv:
    if (pKsp->Init && !pKsp->Init(&ctx, postKspError)) {
        fprintf(stderr, "Could not initialize provider\n");
        return 5;
    }
#ifdef _WIN32
    if (!(pEncryptCEK = (LPVOID)GetProcAddress(hProvLib, "KeystoreEncrypt"))) {
#else
    if (!(pEncryptCEK = dlsym(hProvLib, "KeystoreEncrypt"))) {
#endif
        fprintf(stderr, "The export KeystoreEncrypt was not found in the KSP library\n");
        return 6;
    }
    if (!pKsp->Write) {
        fprintf(stderr, "Provider does not support configuration\n");
        return 7;
    }

    /* Configure the provider with the key */
    if (!pKsp->Write(&ctx, postKspError, PROV_ENCRYPT_KEY, strlen(PROV_ENCRYPT_KEY))) {
        fprintf(stderr, "Error writing to KSP\n");
        return 8;
    }

    /* Generate a CEK and encrypt it with the provider */
    srand(time(0) ^ getpid());
    for (i = 0; i < sizeof(CEK); i++)
        CEK[i] = rand();

    if (!pEncryptCEK(&ctx, postKspError, CEK, sizeof(CEK), &ECEK, &ECEKlen)) {
        fprintf(stderr, "Error encrypting CEK\n");
        return 9;
    }

    /* Connect to Server */
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &env);
    checkRC(rc, "allocating environment handle", 2, 0, 0);
    rc = SQLSetEnvAttr(env, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0);
    checkRC(rc, "setting ODBC version to 3.0", 3, env, SQL_HANDLE_ENV);
    rc = SQLAllocHandle(SQL_HANDLE_DBC, env, &dbc);
    checkRC(rc, "allocating connection handle", 4, env, SQL_HANDLE_ENV);
    rc = SQLDriverConnect(dbc, 0, argv[1], strlen(argv[1]), NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    checkRC(rc, "connecting to data source", 5, dbc, SQL_HANDLE_DBC);
    rc = SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
    checkRC(rc, "allocating statement handle", 6, dbc, SQL_HANDLE_DBC);

    /* Create a CMK definition on the server */
    {
        static char cmkSql[] = "CREATE COLUMN MASTER KEY CustomCMK WITH ("
            "KEY_STORE_PROVIDER_NAME = 'MyCustomKSPName',"
            "KEY_PATH = 'TheOneAndOnlyKey')";
        printf("Create CMK: %s\n", cmkSql);
        SQLExecDirect(stmt, cmkSql, SQL_NTS);
    }

    /* Create a CEK definition on the server */
    {
        const char cekSqlBefore[] = "CREATE COLUMN ENCRYPTION KEY CustomCEK WITH VALUES ("
            "COLUMN_MASTER_KEY = CustomCMK,"
            "ALGORITHM = 'none',"
            "ENCRYPTED_VALUE = 0x";
        char *cekSql = malloc(sizeof(cekSqlBefore) + 2 * ECEKlen + 2); /* 1 for ')', 1 for null terminator */
        strcpy(cekSql, cekSqlBefore);
        for (i = 0; i < ECEKlen; i++)
            sprintf(cekSql + sizeof(cekSqlBefore) - 1 + 2 * i, "%02x", ECEK[i]);
        strcat(cekSql, ")");
        printf("Create CEK: %s\n", cekSql);
        SQLExecDirect(stmt, cekSql, SQL_NTS);
        free(cekSql);
#ifdef _WIN32
        LocalFree(ECEK);
#else
        free(ECEK);
#endif
    }

#ifdef _WIN32
    FreeLibrary(hProvLib);
#else
    dlclose(hProvLib);
#endif

    /* Create a table with encrypted columns */
    {
        static char *tableSql = "CREATE TABLE CustomKSPTestTable ("
            "c1 int,"
            "c2 varchar(255) COLLATE Latin1_General_BIN2 ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = CustomCEK, ENCRYPTION_TYPE = DETERMINISTIC, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256'))";
        printf("Create table: %s\n", tableSql);
        SQLExecDirect(stmt, tableSql, SQL_NTS);
    }

    /* Load provider into the ODBC Driver and configure it */
    {
        unsigned char ksd[sizeof(CEKEYSTOREDATA) + sizeof(PROV_ENCRYPT_KEY) - 1];
        CEKEYSTOREDATA *pKsd = (CEKEYSTOREDATA*)ksd;
        pKsd->name = L"MyCustomKSPName";
        pKsd->dataSize = sizeof(PROV_ENCRYPT_KEY) - 1;
        memcpy(pKsd->data, PROV_ENCRYPT_KEY, sizeof(PROV_ENCRYPT_KEY) - 1);
#ifdef _WIN32
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "MyKSP.dll", SQL_NTS);
#else
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREPROVIDER, "./MyKSP.so", SQL_NTS);
#endif
        checkRC(rc, "Loading KSP into ODBC Driver", 7, dbc, SQL_HANDLE_DBC);
        rc = SQLSetConnectAttr(dbc, SQL_COPT_SS_CEKEYSTOREDATA, (SQLPOINTER)pKsd, SQL_IS_POINTER);
        checkRC(rc, "Configuring the KSP", 7, dbc, SQL_HANDLE_DBC);
    }

    /* Insert some data */
    {
        int c1;
        char c2[256];
        rc = SQLBindParameter(stmt, 1, SQL_PARAM_INPUT, SQL_C_LONG, SQL_INTEGER, 0, 0, &c1, 0, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        rc = SQLBindParameter(stmt, 2, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_VARCHAR, 255, 0, c2, 255, 0);
        checkRC(rc, "Binding parameters for insert", 9, stmt, SQL_HANDLE_STMT);
        for (i = 0; i < 10; i++) {
            c1 = i * 10 + i + 1;
            sprintf(c2, "Sample data %d for column 2", i);
            rc = SQLExecDirect(stmt, "INSERT INTO CustomKSPTestTable (c1, c2) values (?, ?)", SQL_NTS);
            checkRC(rc, "Inserting rows query", 10, stmt, SQL_HANDLE_STMT);
        }
        printf("(Encrypted) data has been inserted into the [CustomKSPTestTable]. You may inspect the data now.\n"
            "Press Enter to continue...\n");
        getchar();
    }

    /* Retrieve the data */
    {
        int c1;
        char c2[256];
        rc = SQLBindCol(stmt, 1, SQL_C_LONG, &c1, 0, 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLBindCol(stmt, 2, SQL_C_CHAR, c2, sizeof(c2), 0);
        checkRC(rc, "Binding columns for select", 11, stmt, SQL_HANDLE_STMT);
        rc = SQLExecDirect(stmt, "SELECT c1, c2 FROM CustomKSPTestTable", SQL_NTS);
        checkRC(rc, "Retrieving rows query", 12, stmt, SQL_HANDLE_STMT);
        while (SQL_SUCCESS == (rc = SQLFetch(stmt)))
            printf("Retrieved data: c1=%d c2=%s\n", c1, c2);
        SQLFreeStmt(stmt, SQL_CLOSE);
        printf("Press Enter to clean up and exit...\n");
        getchar();
    }

    /* Clean up */
    {
        SQLExecDirect(stmt, "DROP TABLE CustomKSPTestTable", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN ENCRYPTION KEY CustomCEK", SQL_NTS);
        SQLExecDirect(stmt, "DROP COLUMN MASTER KEY CustomCMK", SQL_NTS);
        printf("Removed table, CEK, and CMK\n");
    }
    SQLDisconnect(dbc);
    SQLFreeHandle(SQL_HANDLE_DBC, dbc);
    SQLFreeHandle(SQL_HANDLE_ENV, env);
    return 0;
}

```

## <a name="see-also"></a>참고 항목

[상시 암호화와 ODBC 드라이버 사용](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md)
