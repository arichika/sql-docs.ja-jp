---
title: "two digit year cutoff サーバー構成オプションの構成 | Microsoft Docs"
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
  - "two digit year cutoff オプション"
  - "4 桁の西暦年 [SQL Server]"
ms.assetid: d94e81b6-f2e6-47ef-b497-ec3d827a1646
caps.latest.revision: 23
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 23
---
# two digit year cutoff サーバー構成オプションの構成
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] two digit year cutoff [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。 **two digit year cutoff** オプションでは、2 桁の年を 4 桁の西暦年として解釈する場合に世紀の区切りとする年 (終了年) を 1753 ～ 9999 の整数で指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定の期間は 1950 ～ 2049 です。これは、終了年が 2049 であることを表します。 つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、2 桁表記が 49 であれば 2049 年、50 は 1950 年、99 は 1999 年と解釈されます。 旧バージョンとの互換性を保つため、この設定は既定値のままにします。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用して two digit year cutoff オプションを構成するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報**: [two digit year cutoff オプションを構成した後](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術者だけが変更するようにしてください。  
  
-   OLE オートメーション オブジェクトでは、2 桁の西暦の終了年として 2030 が使用されます。 **two digit year cutoff** オプションを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] とクライアント アプリケーションの間で日付値を一致させることができます。 ただし、あいまいな日付で混乱するのを防ぐために、2 桁より 4 桁で年を表記することをお勧めします。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### two digit year cutoff オプションを構成するには  
  
1.  オブジェクト エクスプローラーで、サーバーを右クリックし、**[プロパティ]** をクリックします。  
  
2.  **[その他のサーバーの設定]** ノードをクリックします。  
  
3.  **[2 桁の年のサポート]** の **[2 桁の年を****以下の間にある年として解釈]** ボックスに、期間の終了する年を入力または選択します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### two digit year cutoff オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して、`two digit year cutoff` オプションの値を `2030` に設定する方法を示します。  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'two digit year cutoff', 2030 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 詳細については、「[サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」を参照してください。  
  
##  <a name="FollowUp"></a> 補足情報: two digit year cutoff オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## 参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  