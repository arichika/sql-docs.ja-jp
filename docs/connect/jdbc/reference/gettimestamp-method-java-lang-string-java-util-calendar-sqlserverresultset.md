---
title: getTimestamp (java.lang.String, java.util.Calendar) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTimestamp (java.lang.String, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 44474000-8951-49ee-93a5-c8cb879eaf55
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00d77a3dcd8ae8a6666ee5419cd0b49be921d93f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="gettimestamp-method-javalangstring-javautilcalendar-sqlserverresultset"></a>getTimestamp (java.lang.String, java.util.Calendar) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトを Java プログラミング言語の予定表オブジェクトを使用しての java.sql.Timestamp オブジェクトとして。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Timestamp getTimestamp(java.lang.String colName,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ColName*  
  
 A**文字列**列の名前を格納しています。  
  
 *cal*  
  
 予定表オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 タイムスタンプ オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTimestamp メソッドは、java.sql.ResultSet インターフェイスの getTimestamp メソッドによって指定されます。  
  
 このメソッドからのみ値を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]datetime および smalldatetime の列です。  
  
## <a name="see-also"></a>参照  
 [getTimestamp メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
