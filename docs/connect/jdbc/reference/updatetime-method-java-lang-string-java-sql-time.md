---
title: updateTime (java.lang.String, java.sql.Time) メソッド |Microsoft ドキュメント
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
- SQLServerResultSet.updateTime (java.lang.String, java.sql.Time)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fbbcef68-b903-4cfd-911c-a7e239d17c74
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 30cd816f08e8ac17c6ff5372cebdd992c9efeb73
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="updatetime-method-javalangstring-javasqltime"></a>updateTime (java.lang.String, java.sql.Time) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列を時刻の値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateTime(java.lang.String columnName,  
                       java.sql.Time x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
 *x*  
  
 時刻値です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateTime メソッドは、java.sql.ResultSet インターフェイスの updateTime メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateTime メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
