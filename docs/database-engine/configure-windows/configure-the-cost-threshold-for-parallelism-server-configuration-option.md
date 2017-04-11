---
title: "Configure the cost threshold for parallelism Server Configuration Option | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cost threshold for parallelism option"
ms.assetid: dad21bee-fe28-41f6-9d2f-e6ababfaf9db
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# Configure the cost threshold for parallelism Server Configuration Option
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] cost threshold for parallelism [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。 **cost threshold for parallelism** オプションによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がクエリの並列プランを作成および実行するしきい値が指定されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって、クエリの並列プランが作成および実行されるのは、同じクエリの直列プランを実行するための推定コストが **cost threshold for parallelism**に設定されている値を超える場合のみです。 コストとは、時間の単位ではなく、特定のハードウェア構成で直列プランを実行するための予想コストを表します。 **cost threshold for parallelism** オプションには、0 ～ 32,767 の範囲の値を設定できます。 既定値は 5 です。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用して cost threshold for parallelism オプションを構成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:** [cost threshold for parallelism オプションを構成した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   コストとは、予想時間の単位ではなく、抽象化されたコストの単位を表します。 **cost threshold for parallelism** は、SMP (symmetric multiprocessor) 環境でのみ設定します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では **または** の値が無視されます。  
  
    -   使用しているコンピューターに論理プロセッサが 1 つしか搭載されていない場合。  
  
    -   **関係マスク**構成オプションの設定により、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で 1 つの論理プロセッサしか使用できない場合。  
  
    -   **max degree of parallelism** オプションが 1 に設定されている場合。  
  
 論理プロセッサは、オペレーティング システムでのタスクのディスパッチまたはスレッド コンテキストの実行を可能にするプロセッサ ハードウェアの基本単位です。 各論理プロセッサは一度に 1 つのスレッド コンテキストのみを実行できます。 プロセッサのコアは、命令をデコードして実行する能力を提供する回路です。 プロセッサのコアには 1 つ以上の論理プロセッサが含まれます。 次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリは、システムの CPU 情報の取得に使用できます。  
  
```  
SELECT (cpu_count / hyperthread_ratio) AS PhysicalCPUs,   
cpu_count AS logicalCPUs   
FROM sys.dm_os_sys_info  
```  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。  
  
-   クエリのコスト プランが **cost threshold for parallelism** の現在の値より小さくても、並列プランが選択されることがあります。 並列プランまたは直列プランのどちらを使用するかが、完全な最適化が完了する前に算出されたコストの推定値に基づいて決定された場合に、このようなことが起こります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### cost threshold for parallelism オプションを構成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックし、**[プロパティ]** をクリックします。  
  
2.  **[詳細設定]** ノードをクリックします。  
  
3.  **[並列処理]**で、 **[CostThresholdForParallelism]** オプションを目的の値に変更します。 0 ～ 32767 の値を、入力または選択します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### cost threshold for parallelism オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して、`cost threshold for parallelism` オプションの値を `10` に設定する方法を示します。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'cost threshold for parallelism', 10 ;  
GO  
RECONFIGURE  
GO  
```  
  
 詳細については、「[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」を参照してください。  
  
##  <a name="FollowUp"></a> 補足情報: cost threshold for parallelism オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## 参照  
 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [クエリ ヒント &#40;Transact-SQL&#41;](../Topic/Query%20Hints%20\(Transact-SQL\).md)   
 [ALTER WORKLOAD GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-workload-group-transact-sql.md)   
 [affinity mask サーバー構成オプション](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  