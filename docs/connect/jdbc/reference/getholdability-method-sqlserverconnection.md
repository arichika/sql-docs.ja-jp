---
title: getHoldability メソッド (SQLServerConnection) |Microsoft ドキュメント
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
- SQLServerConnection.getHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b1644791-c36a-4837-86c4-9299537ee1c2
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2aa0c83ab2fc5148194a402359e445984369cc9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getholdability-method-sqlserverconnection"></a>getHoldability メソッド (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在の保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これを使用して作成されたオブジェクト[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>戻り値  
 **Int**保持機能レベルは次のいずれかを含む値です。  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getHoldability メソッドは、java.sql.Connection インターフェイスの getHoldability メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
