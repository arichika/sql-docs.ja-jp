---
title: "主キーの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "主キー [SQL Server], 作成"
ms.assetid: 85c623ca-4656-4d70-a9db-ee4d897cd214
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# 主キーの作成
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して主キーを定義できます。 主キーを作成すると、対応する一意なクラスター化または非クラスター化インデックスが自動的に作成されます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **主キーを変更する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   テーブルに含めることができる PRIMARY KEY 制約は 1 つだけです。  
  
-   PRIMARY KEY 制約中で定義する列はすべて、NOT NULL として定義する必要があります。 NULL 値を許容するかどうかを指定しない場合、PRIMARY KEY 制約の影響を受けるすべての列は NOT NULL に設定されます。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 主キーが設定された、新しいテーブルを作成するには、データベースの CREATE TABLE 権限と、テーブルを作成するスキーマの ALTER 権限が必要です。  
  
 既存のテーブルに主キーを作成するには、テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### 主キーを作成するには  
  
1.  オブジェクト エクスプローラーで、UNIQUE 制約を追加するテーブルを右クリックし**、[デザイン]** をクリックします。  
  
2.  **テーブル デザイナー**で、主キーとして定義するデータベース列の行セレクターをクリックします。 複数列を選択する場合は、Ctrl キーを押しながら、他の列の行セレクターをクリックします。  
  
3.  列の行セレクターを右クリックし、**[主キーの設定]** をクリックします。  
  
> [!CAUTION]  
>  主キーを再定義する場合は、新しい主キーを作成する前に、既存の主キーに対するリレーションシップをすべて削除する必要があります。 再定義中に、既存のリレーションシップが自動的に削除されることを警告するメッセージが表示されます。  
  
 主キー列は、行セレクターに主キーの記号で示されます。  
  
 主キーが複数の列で構成される場合、1 つの列では重複した値が許可されますが、主キーのすべての列の値の組み合わせは一意である必要があります。  
  
 複合キーを定義する場合は、主キーの列の順序が、テーブルに表示される列の順序と同じになります。 ただし、主キー作成後に列の順序を変更することもできます。 詳細については、「[主キーの変更](../../relational-databases/tables/modify-primary-keys.md)」を参照してください。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### 既存のテーブルに主キーを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 この例では、 `TransactionID`列で主キーを作成します。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE Production.TransactionHistoryArchive   
    ADD CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID);  
    GO  
  
    ```  
  
#### 新しいテーブルに主キーを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。 次の例では、テーブルを作成して `TransactionID` 列に主キーを定義します。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE Production.TransactionHistoryArchive1  
    (  
       TransactionID int NOT NULL,  
       CONSTRAINT PK_TransactionHistoryArchive_TransactionID PRIMARY KEY CLUSTERED (TransactionID)  
    );  
    GO  
  
    ```  
  
     詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」、「[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)」、および「[table_constraint &#40;Transact-SQL&#41;](../Topic/table_constraint%20\(Transact-SQL\).md)」を参照してください。  
  
###  <a name="TsqlExample"></a>  