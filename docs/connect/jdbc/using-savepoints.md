---
title: セーブポイントの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3b48eb13-32ef-4fb3-8e95-dbc9468c9a44
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72b354c805a3d46dd31f6f9df308e33493c2db2c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-savepoints"></a>セーブポイントの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  セーブポイントは、トランザクションを部分的にロールバックするメカニズムです。 内で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、SAVE TRANSACTION savepoint_name ステートメントを使用してセーブポイントを作成することができます。 その後 ROLLBACK TRANSACTION savepoint_name ステートメントを実行すると、トランザクションの最初にロールバックするのではなく、セーブポイントにロールバックされます。  
  
 セーブポイントは、エラーが発生する可能性が小さい状況で役立ちます。 エラーの頻度が低い場合には、セーブポイントを使用してトランザクションの一部をロールバックする方法は、更新が有効であるかどうかを更新を行う前にトランザクションごとにテストするよりも効率的です。 更新とロールバックは負荷の大きい処理です。そのため、セーブポイントが効果を発揮するのは、エラーの発生確率が低く、なおかつ更新の有効性を事前にチェックするコストの方が高い場合に限られます。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を通じてセーブポイントの使用をサポートしている、 [setSavepoint](../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)のメソッド、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 SetSavepoint メソッドを使用すると、現在のトランザクション内で名前付きまたは名前のないセーブポイントを作成することができ、メソッドは、 [SQLServerSavepoint](../../connect/jdbc/reference/sqlserversavepoint-class.md)オブジェクト。 セーブポイントは 1 つのトランザクションに複数作成できます。 特定のセーブポイントまでに、トランザクションをロールバックするには SQLServerSavepoint オブジェクトを渡すことができます、 [rollback (java.sql.Savepoint)](../../connect/jdbc/reference/rollback-method-java-sql-savepoint.md)メソッドです。  
  
 セーブポイントの使用の 2 つのステートメントで構成されるローカル トランザクションの実行中に次の例で、`try`ブロックします。 Production.ScrapReason テーブルに対して、ステートメントを実行、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース、およびセーブポイントが 2 番目のステートメントをロールバックするために使用します。 この結果、最初のステートメントのみがデータベースにコミットされます。  
  
 [!code[JDBC#UsingSavepoints1](../../connect/jdbc/codesnippet/Java/using-savepoints_1.java)]  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーを使用したトランザクションの実行](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
  
  
