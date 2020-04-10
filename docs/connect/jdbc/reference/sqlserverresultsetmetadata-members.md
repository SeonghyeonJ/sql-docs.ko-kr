---
title: SQLServerResultSetMetaData 멤버 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 37587981-2979-49a3-a6ab-df4bfb9b8748
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea6812d9a954d5aa9e19c965c9a0a1d6bce7cffe
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927094"
---
# <a name="sqlserverresultsetmetadata-members"></a>SQLServerResultSetMetaData 멤버
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  다음 표에는 [SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) 클래스에 의해 노출되는 멤버가 나와 있습니다.  
  
## <a name="constructors"></a>생성자  
 없음  
  
## <a name="fields"></a>필드  
 없음  
  
## <a name="inherited-fields"></a>상속된 필드  
  
|속성|Description|  
|----------|-----------------|  
|java.sql.ResultSetMetaData|columnNoNulls, columnNullable, columnNullableUnknown|  
  
## <a name="methods"></a>메서드  
  
|속성|Description|  
|----------|-----------------|  
|[getCatalogName](../../../connect/jdbc/reference/getcatalogname-method-sqlserverresultsetmetadata.md)|지정된 열이 포함된 테이블의 카탈로그 이름을 가져옵니다.|  
|[getColumnClassName](../../../connect/jdbc/reference/getcolumnclassname-method-sqlserverresultsetmetadata.md)|[SQLServerResultSet](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) 클래스의 [getObject](../../../connect/jdbc/reference/sqlserverresultset-class.md) 메서드를 호출하여 열에서 값을 검색할 경우 인스턴스가 생성되는 Java 클래스의 정규화된 이름을 반환합니다.|  
|[getColumnCount](../../../connect/jdbc/reference/getcolumncount-method-sqlserverresultsetmetadata.md)|결과 집합의 열 수를 반환합니다.|  
|[getColumnDisplaySize](../../../connect/jdbc/reference/getcolumndisplaysize-method-sqlserverresultsetmetadata.md)|지정된 열의 표준 최대 너비(문자 수)를 반환합니다.|  
|[getColumnLabel](../../../connect/jdbc/reference/getcolumnlabel-method-sqlserverresultsetmetadata.md)|지정된 열의 출력 및 표시에 사용되는 권장 제목을 가져옵니다.|  
|[getColumnName](../../../connect/jdbc/reference/getcolumnname-method-sqlserverresultsetmetadata.md)|지정된 열의 이름을 가져옵니다.|  
|[getColumnType](../../../connect/jdbc/reference/getcolumntype-method-sqlserverresultsetmetadata.md)|지정된 열의 SQL 형식을 검색합니다.|  
|[getColumnTypeName](../../../connect/jdbc/reference/getcolumntypename-method-sqlserverresultsetmetadata.md)|지정된 열의 데이터베이스 관련 형식 이름을 검색합니다.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverresultsetmetadata.md)|지정된 열의 자릿수를 가져옵니다.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverresultsetmetadata.md)|지정된 열의 소수점 이하 자릿수를 가져옵니다.|  
|[getSchemaName](../../../connect/jdbc/reference/getschemaname-method-sqlserverresultsetmetadata.md)|지정된 열의 테이블 스키마 이름을 가져옵니다.|  
|[getTableName](../../../connect/jdbc/reference/gettablename-method-sqlserverresultsetmetadata.md)|지정된 열의 테이블 이름을 가져옵니다.|  
|[isAutoIncrement](../../../connect/jdbc/reference/isautoincrement-method-sqlserverresultsetmetadata.md)|지정된 열이 자동으로 번호가 매겨지고 이로 인해 읽기 전용이 되는지 여부를 나타냅니다.|  
|[isCaseSensitive](../../../connect/jdbc/reference/iscasesensitive-method-sqlserverresultsetmetadata.md)|열이 대/소문자를 구분하는지 여부를 나타냅니다.|  
|[isCurrency](../../../connect/jdbc/reference/iscurrency-method-sqlserverresultsetmetadata.md)|지정된 열이 현금 값인지 여부를 나타냅니다.|  
|[isDefinitelyWritable](../../../connect/jdbc/reference/isdefinitelywritable-method-sqlserverresultsetmetadata.md)|지정된 열에 대한 쓰기 작업이 확실하게 성공할지 여부를 나타냅니다.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverresultsetmetadata.md)|지정된 열의 값에 대한 Null 허용 여부를 나타냅니다.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverresultsetmetadata.md)|지정된 열이 확실하게 쓰기 불가능한지 여부를 나타냅니다.|  
|[isSearchable](../../../connect/jdbc/reference/issearchable-method-sqlserverresultsetmetadata.md)|SQL WHERE 절에 지정된 열을 사용할 수 있는지 여부를 나타냅니다.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverresultsetmetadata.md)|지정된 열의 값이 부호 있는 숫자인지 여부를 나타냅니다.|  
|[isSparseColumnSet](../../../connect/jdbc/reference/issparsecolumnset-method-sqlserverresultsetmetadata.md)|결과 집합의 열이 스파스 열 집합인지 여부를 나타냅니다.|  
|[isWritable](../../../connect/jdbc/reference/iswritable-method-sqlserverresultsetmetadata.md)|지정된 열에 대한 쓰기 작업이 성공할 수 있는지 여부를 나타냅니다.|  
  
## <a name="inherited-methods"></a>상속된 메서드  
  
|상속하는 원본 클래스|메서드|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerResultSetMetaData 클래스](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
