---
title: SQLXML 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 7c67be98-efb5-446c-a0e3-ee67c43cb170
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f235525e7a633bc0c49d39f8bec6bf4a79c0885d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006024"
---
# <a name="sqlxml-interface"></a>SQLXML 인터페이스

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

JDBC 드라이버에서는 java.sql.SQLXML 인터페이스를 소개하는 JDBC 4.0 API가 지원됩니다. SQLXML 인터페이스는 XML 데이터에 대한 상호 작용 및 조작을 수행하는 메서드를 정의합니다. **SQLXML** 데이터 형식은 **xml** 데이터 형식에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]매핑됩니다.  
  
SQLXML 인터페이스는 XML 값에 **문자열**, **판독기** 또는 **작성기**또는 **스트림으로**액세스 하기 위한 메서드를 제공 합니다. XML 값은 또한 **Source**를 통해 액세스하거나 **Result**로 설정할 수 있는데 이들은 DOM(문서 개체 모델), SAX(Simple API for XML), StAX(Streaming API for XML)와 같은 XML 파서와 XSLT 변환 및 XPath와 함께 사용할 수 있습니다.  
  
## <a name="remarks"></a>Remarks  

다음 표에서는 SQLXML 인터페이스에 정의된 메서드에 대해 설명합니다.  
  
|메서드 구문|메서드 설명|  
|-------------------|------------------------|  
|[void free()](https://go.microsoft.com/fwlink/?LinkId=131685)|이 메서드는 SQLXML 개체 및 이 개체가 보유한 리소스를 해제합니다.|  
|[InputStream getBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131754)|SQLXML에서 데이터를 읽기 위한 입력 스트림을 반환합니다.|  
|[Reader getCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131755)|**XML** 데이터를 java.io.Reader 개체 또는 문자 스트림으로 반환합니다.|  
|[T extends Source T getSource(Class\<T> sourceClass)](https://go.microsoft.com/fwlink/?LinkId=131756)|이 **SQLXML** 개체로 지정 된 **XML** 값을 읽기 위한 **원본을** 반환 합니다.<br /><br /> **참고:** getSource 메서드는 원본 javax.xml.transform.dom.DOMSource, javax.xml.transform.sax.SAXSource, javax.xml.transform.stax.StAXSource 및 java.io.InputStream을 지원합니다.|  
|[String getString()](https://go.microsoft.com/fwlink/?LinkId=131757)|이 SQLXML 개체가 지정하는 **XML** 값의 문자열 표현을 반환합니다.|  
|[OutputStream setBinaryStream()](https://go.microsoft.com/fwlink/?LinkId=131758)|이 SQLXML 개체가 나타내는 **XML** 값을 쓰는 데 사용할 수 있는 스트림을 검색합니다.|  
|[Writer setCharacterStream()](https://go.microsoft.com/fwlink/?LinkId=131759)|이 SQLXML 개체가 나타내는 **XML** 값을 쓰는 데 사용할 스트림을 반환합니다.|  
|[T extends Result T setResult(Class\<T> resultClass)](https://go.microsoft.com/fwlink/?LinkId=131760)|이 **SQLXML** 개체로 지정 된 **XML** 값을 설정 하는 **결과** 를 반환 합니다.<br /><br /> **참고:** setResult 메서드는 원본 javax.xml.transform.dom.DOMResult, javax.xml.transform.sax.SAXResult, javax.xml.transform.stax.StaxResult 및 java.io.OutputStream을 지원합니다.|  
|[void setString(String value)](https://go.microsoft.com/fwlink/?LinkId=131762)|이 SQLXML 개체가 지정하는 XML 값을 지정된 **String** 표현으로 설정합니다.|  
  
응용 프로그램은 SQLXML 개체에 XML 값을 한 번만 읽고 쓸 수 있습니다.  
  
free() 메서드가 호출되면 SQLXML 개체가 더 이상 유효하지 않고 읽거나 쓸 수 없게 됩니다. 애플리케이션이 해당 SQLXML 개체에 대해 free() 메서드 이외의 메서드를 호출하려고 시도하면 예외가 throw됩니다.  
  
응용 프로그램이 getSource, getCharacterStream, getBinaryStream 및 getString의 getter 메서드를 호출할 때 SQLXML 개체를 읽거나 쓸 수 없게 됩니다.  
  
응용 프로그램에서 setResult, setCharacterStream, setBinaryStream 및 Setresult과 같은 setter 메서드를 호출할 때 SQLXML 개체는 쓰기 불가능 하거나 읽을 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  

[XML 데이터 지원](../../connect/jdbc/supporting-xml-data.md)  
