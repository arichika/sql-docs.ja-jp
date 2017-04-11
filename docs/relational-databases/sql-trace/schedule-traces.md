---
title: "トレースのスケジュール設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フィルター [SQL Server], イベント"
  - "トレース [SQL Server]"
  - "トレース [SQL Server], 停止"
  - "イベント [SQL Server], フィルター"
  - "トレースのスケジュール設定 [SQL Server]"
  - "トレース [SQL Server], スケジュール設定"
  - "トレースの停止"
ms.assetid: 620b79db-924b-4502-8af3-39efcfca245d
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# トレースのスケジュール設定
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でトレースのスケジュールを設定するには、次の 2 つの方法があります。 可能な代替手段としては以下の方法があります。  
  
-   トレース停止時刻を有効にする。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してトレースのスケジュールを設定する。  
  
## トレース停止時刻の指定  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャまたは [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用する場合は、トレース停止時刻を指定できます。 停止時刻は、トレースを最初に構成する際に設定する必要があります。  
  
## SQL Server エージェントを使用したトレースのスケジュール設定  
 トレースのスケジュールを設定する最善の方法は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用してトレースを開始してから、[!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャ **sp_trace_setstatus** または [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] を使用してトレース停止時刻を指定する方法です。  
  
 **トレースの終了時刻フィルターを設定するには**  
  
 [イベントの終了時刻に基づいたフィルターでのイベントの選択 &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)  
  
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
## 参照  
 [管理タスクの自動化 &#40;SQL Server エージェント&#41;](../../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  