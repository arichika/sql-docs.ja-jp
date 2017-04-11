---
title: "[履歴クリーンアップ タスク] (メンテナンス プラン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.maint.historycleanup.f1"
helpviewer_keywords: 
  - "[履歴クリーンアップ タスク] ダイアログ ボックス"
ms.assetid: 66bb6c39-958c-4053-a27f-b1118d2567f5
caps.latest.revision: 21
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 21
---
# [履歴クリーンアップ タスク] (メンテナンス プラン)
  **[履歴クリーンアップ タスク]** ダイアログ ボックスを使用すると、msdb データベースのテーブルに含まれる古い履歴情報を破棄できます。 このタスクでは、バックアップと復元の履歴、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ履歴、メンテナンス プランの履歴の削除がサポートされます。  
  
 このステートメントでは、**sp_purge_jobhistory** ステートメントおよび **sp_delete_backuphistory** ステートメントが使用されます。  
  
## UI 要素の一覧  
 **接続**  
 このタスクを実行するときに使用するサーバー接続を選択します。  
  
 **新規**  
 このタスクを実行するときに使用する新しいサーバー接続を作成します。 **[新しい接続]** ダイアログ ボックスについては、このトピックで説明しています。  
  
 **[バックアップおよび復元の履歴]**  
 最新のバックアップを作成したときのレコードを保存しておくと、データベースの復元時に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で復元プランを作成するのに役立ちます。 保存期間は、データベースの完全バックアップを実行する間隔以上にする必要があります。  
  
 **[SQL Server エージェントのジョブ履歴]**  
 この履歴を利用して、失敗したジョブをトラブルシューティングしたり、データベース アクションの発生原因を調べたりできます。  
  
 **[メンテナンス プランの履歴]**  
 この履歴を利用して、失敗したメンテナンス プラン ジョブをトラブルシューティングしたり、データベース アクションの発生原因を調べたりできます。  
  
 **[これより古い履歴データの削除]**  
 削除するアイテムの古さを指定します。  
  
 **[T-SQL の表示]**  
 選択したオプションに基づき、このタスクでサーバーに対して実行される [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを表示します。  
  
> [!NOTE]  
>  影響を受けるオブジェクトが大量にある場合は、表示にかなりの時間を要する場合があります。  
  
## [新しい接続] ダイアログ ボックス  
 **[接続名]**  
 新しい接続の名前を入力します。  
  
 **[サーバー名の選択または入力]**  
 このタスクを実行するときに接続するサーバーを選択します。  
  
 **[更新]**  
 使用できるサーバーの一覧を表示します。  
  
 **[サーバーにログオンするための情報の入力]**  
 サーバーの認証情報を指定します。  
  
 **[Windows NT の統合セキュリティを使用する]**  
 Microsoft Windows 認証を使用して、SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
 **[特定のユーザー名とパスワードを使用する]**  
 SQL Server 認証を使用して、SQL Server [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。 このオプションは利用できません。  
  
 **ユーザー名**  
 認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。 このオプションは利用できません。  
  
 **Password**  
 認証に使用するパスワードを指定します。 このオプションは利用できません。  
  
## 参照  
 [sp_purge_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-purge-jobhistory-transact-sql.md)   
 [sp_delete_backuphistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)  
  
  