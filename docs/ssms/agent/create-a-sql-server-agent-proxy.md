---
title: SQL Server エージェント プロキシの作成 | Microsoft Docs
ms.custom: ''
ms.date: 05/04/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- proxies [SQL Server Agent], creating
ms.assetid: 142e0c55-a8b9-4669-be49-b9dc602d5988
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 90acdf01a88ad5ae7e85775b5229df1a152a3669
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-sql-server-agent-proxy"></a>Create a SQL Server Agent Proxy
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql_md.md)]で SQL Server エージェント プロキシを作成する方法について説明します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント プロキシ アカウントは、ジョブ ステップを実行できるセキュリティ コンテキストを定義します。 各プロキシには対応するセキュリティ資格情報が 1 つあります。 特定のジョブ ステップに権限を設定するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サブシステムに必要な権限のあるプロキシを作成し、このプロキシをジョブ ステップに割り当てます。  
  
**このトピックの内容**  
  
-   **作業を開始する準備:**  
  
    [制限事項と制約事項](#Restrictions)  
  
    [Security](#Security)  
  
-   **SQL Server エージェント プロキシを作成する方法:**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>はじめに  
  
### <a name="Restrictions"></a>制限事項と制約事項  
  
-   資格情報を用意していない場合は、プロキシを作成する前に、まず資格情報を作成する必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント プロキシは、資格情報を使用して Windows ユーザー アカウントに関する情報を格納します。 資格情報で指定されたユーザーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] が実行されているコンピューターでの "ネットワーク経由でコンピューターへアクセス" アクセス許可 (SeNetworkLogonRight) を持っている必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは、ジョブ ステップを実行するごとに、プロキシからサブシステムへのアクセス許可を確認し、アクセスを確立します。 プロキシにサブシステムへのアクセス許可がない場合、ジョブ ステップは失敗します。 プロキシにアクセス許可がある場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントはプロキシで指定されているユーザーの権限を借用してジョブ ステップを実行します。  
  
-   プロキシを作成しても、そのプロキシの資格情報で指定したユーザーの権限は変更されません。 たとえば、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のインスタンスに接続する権限を持たないユーザーのプロキシを作成できます。 この場合、このプロキシを使用するジョブ ステップから [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]に接続することはできません。  
  
-   ユーザーのログインにプロキシへのアクセス許可がある場合、またはプロキシへのアクセス許可のあるロールにユーザーが属している場合、このユーザーはジョブ ステップでプロキシを使用できます。  
  
### <a name="Security"></a>Security  
  
#### <a name="Permissions"></a>Permissions  
  
-   **sysadmin** 固定サーバー ロールのメンバーだけに、プロキシ アカウントを作成、変更、または削除できる権限があります。 固定サーバー ロール **sysadmin** のメンバーではないユーザーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] msdb **データベースの** エージェント固定データベース ロールである **SQLAgentUserRole**、 **SQLAgentReaderRole**、または **SQLAgentOperatorRole**のいずれかに追加されないと、プロキシを使用できません。  
  
-   プロキシに加えて資格情報を作成する場合は、 **ALTER ANY CREDENTIAL** 権限が必要です。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>SQL Server エージェント プロキシを作成するには  
  
1.  **オブジェクト エクスプ ローラー**で、SQL Server エージェント プロキシを作成するサーバーをプラス記号をクリックして展開します。  
  
2.  プラス記号をクリックして **[SQL Server エージェント]** を展開します。  
  
3.  **[プロキシ]** フォルダーを右クリックし、 **[新しいプロキシ]** を選択します。  
  
4.  **[新しいプロキシ アカウント]** ダイアログ ボックスの **[全般]** ページで、 **[プロキシ名]** ボックスにプロキシ アカウントの名前を入力します。  
  
5.  **[資格情報名]** ボックスに、プロキシ アカウントが使用するセキュリティ資格情報の名前を入力します。  
  
6.  **[説明]** ボックスに、プロキシ アカウントの説明を入力します。  
  
7.  **[以下のサブシステムに対してアクティブ]** から、このプロキシ用の適切なサブシステムを選択します (複数選択可能)。  
  
8.  **[プリンシパル]** ページで、プロキシ アカウントへのアクセスを許可するログインまたはロールを追加するか、あるいは拒否するログインまたはロールを削除します。  
  
9. 完了したら、 **[OK]** をクリックします。  
  
## <a name="TsqlProcedure"></a>Transact-SQL の使用  
  
#### <a name="to-create-a-sql-server-agent-proxy"></a>SQL Server エージェント プロキシを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    -- creates credential CatalogApplicationCredential  
    USE msdb ;  
    GO  
    CREATE CREDENTIAL CatalogApplicationCredential WITH IDENTITY = 'REDMOND/TestUser',   
        SECRET = 'G3$1o)lkJ8HNd!';  
    GO  
    -- creates proxy "Catalog application proxy" and assigns
    -- the credential 'CatalogApplicationCredential' to it.  
    EXEC dbo.sp_add_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 1,  
        @description = 'Maintenance tasks on catalog application.',  
        @credential_name = 'CatalogApplicationCredential' ;  
    GO  
    -- grants the proxy "Catalog application proxy" access to 
    -- the ActiveX Scripting subsystem.  
    EXEC dbo.sp_grant_proxy_to_subsystem  
        @proxy_name = N'Catalog application proxy',  
        @subsystem_id = 2 ;  
    GO  
    ```  
  
詳細については、以下をご覧ください。  
  
-   [CREATE CREDENTIAL (Transact-SQL)](http://msdn.microsoft.com/en-us/d5e9ae69-41d9-4e46-b13d-404b88a32d9d)  
  
-   [sp_add_proxy (Transact-SQL)](http://msdn.microsoft.com/en-us/cb59df37-f103-439b-bec1-2871fb669a8b)  
  
-   [sp_grant_proxy_to_subsystem (Transact-SQL)](http://msdn.microsoft.com/en-us/866aaa27-a1e0-453a-9b1b-af39431ad9c2)  
  
