---
title: "ライブ クエリ統計 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/28/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クエリ統計 [SQL Server] ライブ クエリ統計"
  - "ライブ クエリ統計"
  - "デバッグ [SQL Server]、ライブ クエリ統計"
  - "統計 [SQL Server]、ライブ クエリ統計"
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# ライブ クエリ統計
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、アクティブ クエリのライブ実行プランを表示できます。 このライブ クエリ プランでは、クエリ プラン演算子間の制御フローとして、クエリ実行プロセスをリアルタイムで洞察できます。 ライブ クエリ プランには、全体的なクエリ進捗状況と演算子レベルのランタイム実行統計が表示されます。生成された行の数、経過時間、演算子の進捗状況などです。このデータはクエリの完了を待つことなくリアルタイムで利用できるため、これらの実行統計はクエリ パフォーマンス問題のデバッグで非常に役立ちます この機能は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] から利用できますが、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] でも動作します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
> [!WARNING]  
>  この機能は、主にトラブルシューティングの目的で使用されます。 この機能を利用すると、全体的なクエリ パフォーマンスがやや遅くなることがあります。 この機能は [Transact-SQL デバッガー](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md)と共に利用できます。  
  
#### <a name="to-view-live-query-statistics"></a>ライブ クエリ統計を表示するには  
  
1.  ライブ クエリ実行プランを表示するには、ツール メニューで、 **[ライブ クエリ統計]** アイコンをクリックします。  
  
     ![Live Query Stats button on toolbar](../../relational-databases/performance/media/livequerystatstoolbar.png "Live Query Stats button on toolbar")  
  
     [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で選択したクエリを右クリックし、**[ライブ クエリ統計を含める]**をクリックしてライブ クエリ実行プランを表示することもできます。  
  
     ![Live Query Stats button on popup menu](../../relational-databases/performance/media/livequerystatsmenu.png "Live Query Stats button on popup menu")  
  
2.  クエリを実行します。 ライブ クエリ プランには、経過時間や進捗状況など、全体的なクエリ進捗状況と演算子レベルのランタイム実行統計がクエリ プラン演算子に対して表示されます。 クエリ実行の進捗中は、クエリ進捗状況情報と実行統計が定期的に更新されます。 この情報を利用して全体的なクエリ実行プロセスを理解し、実行時間の長いクエリ、無限に実行されるクエリ、tempdb オーバーフローを引き起こすクエリ、タイムアウト問題をデバッグします。  
  
     ![Live Query Stats button in showplan](../../relational-databases/performance/media/livequerystatsplan.png "Live Query Stats button in showplan")  
  
 ライブ実行プランは **利用状況モニター** からもアクセスできます。 **[Active Expensive Queries]** テーブルのクエリを右クリックします。  
  
 ![Live Query Stats button in Activity Monitor](../../relational-databases/performance/media/livequerystatsactmon.png "Live Query Stats button in Activity Monitor")  
  
## <a name="remarks"></a>解説  
 ライブ クエリ統計でクエリの進捗状況に関する情報を記録するには、この統計プロファイル インフラストラクチャを有効にする必要があります。 **で** [ライブ クエリ統計を含める] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を指定すると、現在のクエリ セッションの統計インフラストラクチャが有効になります。 
 
[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] までは、他のセッションから (たとえば、利用状況モニターから) ライブ クエリ統計を表示するための統計インフラストラクチャを有効にする方法が他に 2 つあります。  
  
-   ターゲット セッションで `SET STATISTICS XML ON;` または `SET STATISTICS PROFILE ON;` を実行します。  
  
 または  
  
-   **query_post_execution_showplan** 拡張イベントを有効にします。 これはサーバー全体の設定であり、すべてのセッションでライブ クエリ統計が有効になります。 拡張イベントを有効にする方法については、「 [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)」を参照してください。  

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 より、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、軽量版の統計プロファイル インフラストラクチャが含まれます。 他のセッションから (たとえば、利用状況モニターから) ライブ クエリ統計を表示するための軽量版統計インフラストラクチャを有効にする方法が 2 つあります。

-   グローバル トレース フラグ 7412 を使用する。  
  
 または  
  
-   **query_thread_profile** 拡張イベントを有効にする。 これはサーバー全体の設定であり、すべてのセッションでライブ クエリ統計が有効になります。 拡張イベントを有効にする方法については、「 [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)」を参照してください。
  
 > [!NOTE] ネイティブ コンパイル ストアド プロシージャはサポートされていません。  
  
## <a name="permissions"></a>アクセス許可  
 **ライブ クエリ統計** の結果ページに入力するにはデータベース レベルの **SHOWPLAN** アクセス許可が、ライブ統計を表示するにはサーバー レベルの **VIEW SERVER STATE** アクセス許可が、クエリを実行するには必要なあらゆるアクセス許可が必要になります。  
  
## <a name="see-also"></a>参照  
 [パフォーマンスの監視とチューニング](../../relational-databases/performance/monitor-and-tune-for-performance.md)   
 [パフォーマンス監視およびチューニング ツール](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)   
 [利用状況モニターを開く方法 &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)   
 [利用状況モニター](../../relational-databases/performance-monitor/activity-monitor.md)   
 [クエリのストアを使用した、パフォーマンスの監視](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)   
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)   
 [トレース フラグ](Trace%20Flags%20\(Transact-SQL\).md)