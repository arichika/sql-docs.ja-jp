---
title: "media retention サーバー構成オプションの構成 | Microsoft Docs"
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
  - "バックアップ保持期間 [SQL Server]"
  - "バックアップ セット [SQL Server]、保持期間"
  - "media retention オプション"
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
caps.latest.revision: 26
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 26
---
# media retention サーバー構成オプションの構成
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 **で** または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] media retention [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。 **media retention** オプションは、各バックアップ セットを保持する期間を指定します。 このオプションを利用して、指定した日数が経過するまでバックアップが上書きされないように保護できます。 **media retention** オプションを構成すると、バックアップするたびにシステム バックアップを保持する期間を指定する必要はありません。 既定値は 0 日であり、最大値は 365 日です。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用して media retention オプションを構成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:** [media retention オプションを構成した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   設定した日数が経過する前にバックアップ メディアを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって警告メッセージが発行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から警告が発行されることはありません。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。  
  
-   **media retention** オプションは、 [BACKUP](../../t-sql/statements/backup-transact-sql.md) ステートメントの RETAINDAYS 句を使用して無効にできます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### media retention オプションを構成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックし、**[プロパティ]** をクリックします。  
  
2.  **[データベースの設定]** ノードをクリックします。  
  
3.  **[バックアップと復元]** の **[バックアップ メディアの既定の保有期間 (日)]** ボックスで、0 ～ 365 の値を入力または選択します。ここで指定した日数が、データベース バックアップまたはトランザクション ログ バックアップの後にバックアップ メディアを保持する日数となります。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### media retention オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して、`media retention` オプションの値を `60` 日に設定する方法を示します。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 詳細については、「[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」を参照してください。  
  
##  <a name="FollowUp"></a> 補足情報: media retention オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## 参照  
 [SQL Server データベースのバックアップと復元](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  