---
title: getBinaryStream (java.lang.String) メソッド |Microsoft ドキュメント
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
- SQLServerResultSet.getBinaryStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 149609b5-a6de-4e23-a440-7061775d0899
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3054c8af398a2158b9fd779c668593ee7dc86fde
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getbinarystream-method-javalangstring"></a>getBinaryStream (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして解釈されないバイトのバイナリ ストリーム。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.InputStream getBinaryStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getBinaryStream メソッドは、java.sql.ResultSet インターフェイスの getBinaryStream メソッドによって指定されます。  
  
 このメソッドでのみ使用できます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]binary、varbinary、varbinary (max)、およびイメージのデータ型。 他のデータ型で使用すると、例外がスローされます。  
  
 このメソッドで値をストリームとして取得した後は、ストリームからこの値をチャンク単位で読み取ることができます。 このメソッドは、大きな LONGVARBINARY 値を取得する場合に適しています。  
  
> [!NOTE]  
>  返されたストリーム内のデータはすべて、他の列の値を取得する前に読み取る必要があります。 次に getter メソッドを呼び出すと、ストリームは暗黙的に閉じます。 また、ストリーム 0 を返します InputStream.available メソッドが呼び出されると、データが使用できるかどうかどうか。  
  
## <a name="see-also"></a>参照  
 [getBinaryStream メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
