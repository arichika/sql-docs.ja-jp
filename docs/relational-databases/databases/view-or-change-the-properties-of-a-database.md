---
title: "データベースのプロパティの表示または変更 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベースの表示"
  - "データベース表示 [SQL Server]"
  - "データベース [SQL Server], 表示"
  - "データベースの確認"
ms.assetid: 9e8ac097-84b7-46c7-85e3-c1e79f94d747
caps.latest.revision: 42
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# データベースのプロパティの表示または変更
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]のデータベースのプロパティを表示または変更する方法について説明します。 データベースのプロパティを変更すると、変更は直ちに有効になります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用してデータベースのプロパティを表示または変更するには:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   AUTO_CLOSE が ON の場合、データベースからデータを取得できないため、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューの一部の列、および DATABASEPROPERTYEX 関数は、NULL を返します。 これを解決するには、データベースを開きます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 データベースのプロパティを変更するには、データベースに対する ALTER 権限が必要です。 データベースのプロパティを表示するには、少なくとも public データベース ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### データベースのプロパティを表示または変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]** を展開し、表示するデータベースを右クリックします。次に **[プロパティ]** をクリックします。  
  
3.  **[データベースのプロパティ]** ダイアログ ボックスで、任意のページを選択して、対応する情報を表示します。 たとえば、データおよびログ ファイルの情報を表示するには、 **[ファイル]** ページをクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 Transact-SQL を使用すると、さまざまな方法でデータベースのプロパティを表示および変更できます。 データベースのプロパティを表示するには、 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md) 関数と [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューを使用します。 データベースのプロパティを変更するには、自分の環境に合う ALTER DATABASE ステートメントのバージョン ([ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md) または [ALTER DATABASE &#40;Azure SQL データベース&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)) を使用できます。 データベース スコープのプロパティを表示するには、[sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) カタログ ビューを使用します。データベース スコープのプロパティを変更するには、[ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md) ステートメントを使用します。  
  
#### DATABASEPROPERTYEX 関数を使用してデータベースのプロパティを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続し、プロパティを表示するデータベースに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースの AUTO_SHRINK データベース オプションのステータスを、[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) システム関数を使用して取得します。 戻り値が 1 の場合はオプションがオンに、戻り値が 0 の場合はオフに設定されていることを意味します。  
  
    ```tsql  
    SELECT DATABASEPROPERTYEX('AdventureWorks2012', 'IsAutoShrink');  
    ```  
  
#### sys.databases をクエリすることによってデータベースのプロパティを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続し、プロパティを表示するデータベースに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューをクエリして、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースのいくつかのプロパティを表示します。 この例では、データベースの ID 番号 (`database_id`)、データベースが読み取り専用か読み取り/書き込み可能かの情報 (`is_read_only`)、データベースの照合順序 (`collation_name`)、データベースの互換性レベル (`compatibility_level`) を取得します。  
  
    ```tsql  
    SELECT database_id, is_read_only, collation_name, compatibility_level  
    FROM sys.databases WHERE name = 'AdventureWorks2012';  
    ```  
  
#### sys.databases_scoped_configuration を照会してデータベース スコープの構成のプロパティを表示するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続し、プロパティを表示するデータベースに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、[sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md) カタログ ビューのクエリを実行し、現在のデータベースのいくつかのプロパティを表示します。  
  
    ```tsql  
    SELECT configuration_id, name, value, value_for_secondary  
    FROM sys.database_scoped_configurations;  
    ```  
  
     詳細については、「[sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)」を参照してください。  
  
#### ALTER DATABASE を使用して SQL Server 2016 データベースのプロパティを変更するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーし、クエリ ウィンドウに貼り付けます。 この例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベース上のスナップショット分離の状態を確認し、プロパティの状態を変更した後、変更内容を確認します。  
  
     スナップショット分離の状態を確認するには、まず `SELECT` ステートメントを選択し、 **[実行]**をクリックします。  
  
     スナップショット分離の状態を変更するには、 `ALTER DATABASE` ステートメントを選択し、 **[実行]**をクリックします。  
  
     変更内容を確認するには、2 つ目の `SELECT` ステートメントを選択し、 **[実行]**をクリックします。  
  
     [!code-sql[DatabaseDDL#AlterDatabase9](../../relational-databases/databases/codesnippet/tsql/view-or-change-the-prope_1.sql)]  
  
#### ALTER DATABASE SCOPED CONFIGURATION を使用してデータベース スコープのプロパティを変更するには  
  
1.  SQL Server インスタンスのデータベースに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーし、クエリ ウィンドウに貼り付けます。 次の例では、セカンダリ データベースの MAXDOP をプライマリ データベースの値に設定しています。  
  
    ```  
    ALTER DATABASE SCOPED CONFIGURATION FOR SECONDARY SET MAXDOP=PRIMARY   
    ```  
  
## 参照  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [ALTER DATABASE &#40;Azure SQL データベース&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [ALTER DATABASE SCOPED CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [sys.database_scoped_configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-scoped-configurations-transact-sql.md)  

  
  