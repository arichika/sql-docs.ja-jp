---
title: getMaxRows メソッド (SQLServerStatement) |Microsoft ドキュメント
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
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d619f9505d9f6f5e9c2c6db7751ecb224fa2f5e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  行の最大数を取得する、 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これによって生成されるオブジェクト[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクトを含めることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**制限がない場合は、行、または 0 の最大数を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMaxRows メソッドは、java.sql.Statement インターフェイスの getMaxRows メソッドによって指定されます。  
  
 この getMaxRows メソッドは、常に、動的カーソルのスクロール可能な 0 を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
