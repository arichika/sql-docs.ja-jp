---
title: アクティブなクエリの並列データ ウェアハウスの監視 |Microsoft ドキュメント
description: 管理コンソールと並列データ ウェアハウス システム ビューを使用すると、分析プラットフォーム システム上のアクティブなクエリを監視できます。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 057e5448b68ea7a7f8f23bc57d1a3b0308b300d2
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>アクティブなクエリの並列データ ウェアハウスの監視
この記事では、管理コンソールと、SQL Server PDW システム ビューを使用して、アクティブなクエリを監視する方法を示します。 参照してください[アプライアンスを管理コンソールを使用して監視](monitor-the-appliance-by-using-the-admin-console.md)と[システム ビュー](tsql-system-views.md)についてこれらのツールです。  
  
## <a name="prerequisites"></a>前提条件  
アクティブなクエリを監視するために使用するメソッドにかかわらず、ログインが「すべての 管理コンソールを使用して」で説明されているアクセス許可を持っている[管理コンソールを使用するアクセス許可を付与](grant-permissions.md#grant-permissions-to-use-the-admin-console)です。  
  
## <a name="PermsAdminConsole"></a>モニターのアクティブなクエリ  
アクティブなクエリを監視する管理コンソールと、SQL Server PDW システム ビューの両方を使用できます。 次の手順に従います。  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>管理コンソールを使用してアクティブなクエリを監視するには  
  
1.  管理コンソールにログオンします。 参照してください[アプライアンスを管理コンソールを使用して監視](monitor-the-appliance-by-using-the-admin-console.md)手順についてはします。  
  
2.  上部のメニューをクリックして**クエリ**です。 クエリ、クエリとクエリの現在の状態の開始と終了時刻を送信したログインを含め、アプライアンスの最新のクエリに関する基本情報を含むテーブルが表示されます。  
  
3.  マウス ポインターを合わせるクエリ ID は、その行の左の列に、クエリ コマンドを参照してください。  
  
    特定のクエリに関する詳しい情報を表示するには、クエリの ID をクリックします。 完全なクエリ、クエリの実行の各ステップのステータス情報、クエリ プランなどの情報が表示されます。 すべてのエラーが返された場合も表示できます詳細エラーをします。 <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>システム ビューを使用してアクティブなクエリを監視するには  
プライマリ システム ビューのクエリを監視するには、 [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)です。 このシステム ビューを使用して、検索、`request_id`クエリ テキストに基づくアクティブまたは最新のクエリにします。  
  
たとえば、次のクエリの検索、`request_id`と現在`status`からすべての列を選択するクエリに対して、`memberAddresses`テーブル。  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE ‘%SELECT * FROM db1..memberAddresses%’;  
```  
  
後に、`request_id`されました内の他の情報を使用して、クエリで特定された、`dm_pdw_exec_requests`をクエリの処理について調べるにはテーブルの使用または[sys.dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md)個別のクエリの状態を表示するにはクエリの実行の手順を説明します。  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
