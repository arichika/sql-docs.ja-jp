---
title: sqlsrv_close |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_close
apitype: NA
helpviewer_keywords:
- sqlsrv_close
- API Reference, sqlsrv_close
ms.assetid: 6ac6209c-a134-4f8f-b88b-8eefaa1cbc7f
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d701050c24be7b2d05454ddd72452b31c9e4d365
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvclose"></a>sqlsrv_close
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

指定された接続を閉じ、関連付けられているリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_close( resource $conn )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: 閉じる接続。  
  
## <a name="return-value"></a>戻り値  
関数が無効なパラメーターを使用して呼び出されている場合を除き、ブール値は **true** です。 関数が無効なパラメーターで呼び出された場合、 **false** を返します。  
  
> [!NOTE]  
> この関数のパラメーターとして、**Null** は有効です。 これにより、スクリプトで複数回関数を呼び出すことが可能になります。 たとえば、エラー状態で接続を終了し、スクリプトの最後でもう一度閉じる場合、2 つ目の呼び出し**sqlsrv_close**が返されます**true**最初の呼び出しため**sqlsrv_閉じる**(エラー条件) 接続リソースに設定**null**です。  
  
## <a name="example"></a>例  
次の例では、接続を閉じます。 この例では、SQL Server がローカル コンピューターにインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/*Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection here.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
echo "Connection closed.\n";  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
