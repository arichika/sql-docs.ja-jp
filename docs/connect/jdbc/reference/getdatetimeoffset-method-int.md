---
title: getDateTimeOffset (int) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8bb00356-4d6e-4625-b924-67646930fdf2
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 133bafcb02c1a9ae7fbff4a037eeb038e751b426
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="getdatetimeoffset-method-int"></a>getDateTimeOffset (int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  このメソッドで追加された[!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 です。  
  
 として指定されたパラメーターの値を取得、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)Java プログラミング言語のインデックス内のオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int index)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *インデックス*  
  
 1 から始まるパラメーターの序数。  
  
## <a name="return-value"></a>戻り値  
 A [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 設定することができます、 [DateTimeOffset クラス](../../../connect/jdbc/reference/datetimeoffset-class.md)のパラメーター値[sqlservercallablestatement.setdatetimeoffset を使用して](../../../connect/jdbc/reference/setdatetimeoffset-method-sqlservercallablestatement.md)です。  
  
## <a name="see-also"></a>参照  
 [getDateTimeOffset メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getdatetimeoffset-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
