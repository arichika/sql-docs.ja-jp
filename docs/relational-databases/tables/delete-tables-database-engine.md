---
title: "テーブルの削除 (データベース エンジン) | Microsoft Docs"
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
  - "テーブルの削除 [SQL Server]"
  - "消去、テーブル"
  - "削除、テーブル"
  - "破棄、テーブル"
ms.assetid: ca6aa3e9-9885-44c3-bafc-aec441fd97ec
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# テーブルの削除 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用してデータベースからテーブルを削除できます。  
  
> [!CAUTION]  
>  テーブルの削除については、十分に検討してください。 テーブルを参照するクエリ、ビュー、ユーザー定義関数、ストアド プロシージャ、またはプログラムがある場合は、テーブルを削除すると、各オブジェクトが無効になります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [セキュリティ](#Security)  
  
-   **テーブルを削除する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   FOREIGN KEY 制約によって参照されているテーブルを削除することはできません。 まず、参照している FOREIGN KEY 制約または参照テーブルを削除する必要があります。 参照しているテーブルと、主キーを格納しているテーブルの両方を同じ DROP TABLE ステートメントで削除する場合には、参照しているテーブルを先に指定する必要があります。  
  
-   テーブルを削除すると、そのテーブルのルールや既定値はバインドを失い、そのテーブルに関係付けられている制約やトリガーも自動的に削除されます。 テーブルを再作成する場合は、適切なルールや既定値を再バインドし、トリガーを再作成し、必要なすべての制約を追加する必要があります。  
  
-   FILESTREAM 属性が指定されている **varbinary (max)** 列を含むテーブルを削除しても、ファイル システムに保存されているデータは削除されません。  
  
-   DROP TABLE と CREATE TABLE を同じバッチ内の同じテーブルに対して実行しないでください。 実行した場合、予期しないエラーが発生する可能性があります。  
  
-   削除されたテーブルを参照しているすべてのビューとストアド プロシージャを、明示的に削除するか、変更してテーブルへの参照を削除する必要があります。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> 権限  
 テーブルが属するスキーマに対する ALTER 権限、テーブルに対する CONTROL 権限、または **db_ddladmin** 固定データベース ロールのメンバーシップが必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### データベースからテーブルを削除するには  
  
1.  オブジェクト エクスプローラーで、削除するテーブルを選択します。  
  
2.  テーブルを右クリックし、ショートカット メニューの **[削除]** をクリックします。  
  
3.  削除の確認を要求するメッセージ ボックスが表示されます。 **[はい]**をクリックします。  
  
    > [!NOTE]  
    >  テーブルを削除すると、テーブルへのリレーションシップが自動的に削除されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### クエリ エディターでテーブルを削除するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    DROP TABLE dbo.PurchaseOrderDetail;  
  
    ```  
  
 詳細については、「[DROP TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-table-transact-sql.md)」を参照してください。  
  
  