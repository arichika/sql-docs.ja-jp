---
title: updateNClob (int, java.sql.NClob) メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6e9bca18-f64e-46a4-8541-2c9c39b393b5
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5861db060d978a912d973cda179cc1e878da481b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="updatenclob-method-int-javasqlnclob"></a>updateNClob (int, java.sql.NClob) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の更新、 **NClob**値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateNClob(int columnIndex,  
                        java.sql.NClob nClob)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnIndex*  
  
 列インデックスを示す **int** です。  
  
 *NClob*  
  
 NClob オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateNClob メソッドは、java.sql.ResultSet インターフェイスの updateNClob メソッドによって指定されます。  
  
 このメソッドでのみサポートされて**nvarchar (max)**、 **ntext**、および**xml**列です。 このメソッドを他のデータ型で使用すると、例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [updateNClob メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
