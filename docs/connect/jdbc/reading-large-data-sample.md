---
title: 大量のデータ サンプルを読み取る |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6c986144-3854-4352-8331-e79eccbefc28
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0037ee678766bad6786a6feb14e0bf569f9448a0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="reading-large-data-sample"></a>大きなデータを読み取るサンプル
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  これは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]サンプル アプリケーションから大きな単一列値を取得する方法を示して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを使用して、 [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)メソッドです。  
  
 このサンプルのコード ファイルは readLargeData.java という名前で、次の場所にあります。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \samples\adaptive  
  
## <a name="requirements"></a>必要条件  
 このサンプル アプリケーションを実行するにはアクセス許可が必要、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース。 また、クラスパスの設定で sqljdbc.jar ファイルまたは sqljdbc4.jar ファイルを追加する必要があります。 クラスパスに sqljdbc.jar または sqljdbc4.jar のエントリがない場合、サンプル アプリケーションで "Class not found" という一般的な例外がスローされます。 クラスパスを設定する方法の詳細については、次を参照してください。 [JDBC ドライバーを使用して](../../connect/jdbc/using-the-jdbc-driver.md)です。  
  
> [!NOTE]  
>  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Sqljdbc.jar と sqljdbc4.jar な Java ランタイム環境 (JRE) 設定によって使用されるクラス ライブラリ ファイルを提供します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
## <a name="example"></a>例  
 次の例では、サンプル コードへの接続、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]データベース。 次に、サンプル データを作成し、パラメーター化クエリを使用して Production.Document テーブルを更新します。  
  
 さらに、サンプル コードが使用してアダプティブ バッファリング モードを取得する方法を示しています、 [getResponseBuffering](../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md)のメソッド、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 JDBC Driver Version 2.0 リリース以降では、responseBuffering 接続プロパティが既定で "adaptive" に設定されていることに注意してください。  
  
 次に、SQL ステートメントを使用して、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)オブジェクト、サンプル コードは、SQL ステートメントを実行しに返されるデータを配置、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
 最後に、サンプル コードは、結果セットに含まれているデータの行を反復処理しを使用して、 [getCharacterStream](../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)メソッドが含まれているデータの一部にアクセスします。  
  
 [!code[JDBC#UsingAdaptiveBuffering1](../../connect/jdbc/codesnippet/Java/reading-large-data-sample_1.java)]  
  
## <a name="see-also"></a>参照  
 [大きなデータの処理](../../connect/jdbc/working-with-large-data.md)  
  
  
