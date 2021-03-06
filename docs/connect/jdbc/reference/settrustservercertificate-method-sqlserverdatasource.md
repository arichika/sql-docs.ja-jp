---
title: setTrustServerCertificate メソッド (SQLServerDataSource) |Microsoft ドキュメント
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
- setTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- setTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 6c37b518-147e-4cd9-9eff-b48a3f5888c6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bb5923c3078944a446abfc763c76122f44af2396
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="settrustservercertificate-method-sqlserverdatasource"></a>setTrustServerCertificate メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  セット、**ブール**trustServerCertificate プロパティが有効かどうかを示す値。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setTrustServerCertificate(boolean trustServerCertificate)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *TrustServerCertificate*  
  
 **true**通信レイヤーが SSL で暗号化されている場合にサーバーの Secure Sockets Layer (SSL) 証明書を自動的に信頼する必要がありますされるかどうか。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>解説  
 TrustServerCertificate プロパティ設定されている場合**true**、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]通信レイヤーが SSL で暗号化されている場合は、SSL 証明書が自動的に信頼します。 言い換えると、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]は検証されません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] SSL 証明書。 既定値は **false**です。  
  
 TrustServerCertificate プロパティ設定されている場合**false**、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]サーバー SSL 証明書を検証します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
