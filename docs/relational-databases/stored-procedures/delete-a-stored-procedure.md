---
title: "ストアド プロシージャの削除 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-stored-Procs"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "削除、ストアド プロシージャ"
  - "ストアド プロシージャ [SQL Server], 削除"
  - "消去、ストアド プロシージャ"
ms.assetid: 232dbf4d-392a-406f-af3a-579518cd8e46
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# ストアド プロシージャの削除
    
##  <a name="Top"></a> このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、[!INCLUDE[tsql](../../includes/tsql-md.md)] でストアド プロシージャを削除する方法について説明します。  
  
-   **作業を開始する準備:** [制限事項と制約事項](#Restrictions)、[セキュリティ](#Security)  
  
-   **プロシージャの削除に使用するもの:** [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
 プロシージャを削除すると、依存オブジェクトとスクリプトを更新してプロシージャの削除を反映しない限り、そのオブジェクトとスクリプトが失敗する可能性があります。 ただし、名前とパラメーターが同じである新しいプロシージャを作成し、削除したプロシージャと置き換えた場合、そのプロシージャを参照する他のオブジェクトは正常に処理されます。 詳細については、「[ストアド プロシージャの依存関係の表示](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)」を参照してください。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 プロシージャが属しているスキーマに対する ALTER 権限、またはプロシージャに対する CONTROL 権限が必要です。  
  
##  <a name="Procedures"></a> ストアド プロシージャを削除する方法  
 次のいずれかを使用します。  
  
-   [SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **オブジェクト エクスプローラーでプロシージャを削除するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、プロシージャが属するデータベースを展開し、 **[プログラミング]**を展開します。  
  
3.  **[ストアド プロシージャ]** を展開し、削除するプロシージャを右クリックして、**[削除]** をクリックします。  
  
4.  プロシージャに依存するオブジェクトを表示するには、 **[依存関係の表示]**をクリックします。  
  
5.  適切なプロシージャが選択されていることを確認して、 **[OK]**をクリックします。  
  
6.  任意の依存オブジェクトおよびスクリプトからプロシージャへの参照を削除します。  
  
###  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **クエリ エディターでプロシージャを削除するには**  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、プロシージャが属するデータベースを展開するか、ツール バーの利用可能なデータベースの一覧からデータベースを選択します。  
  
3.  [ファイル] メニューの **[新しいクエリ]**をクリックします。  
  
4.  現在のデータベースから削除するストアド プロシージャの名前を取得します。 オブジェクト エクスプローラーから、 **[プログラミング]** を展開し、 **[ストアド プロシージャ]**を展開します。 または、クエリ エディターで次のステートメントを実行します。  
  
    ```tsql  
    SELECT name AS procedure_name   
        ,SCHEMA_NAME(schema_id) AS schema_name  
        ,type_desc  
        ,create_date  
        ,modify_date  
    FROM sys.procedures;  
    ```  
  
5.  次の例をコピーしてクエリ エディターに貼り付け、現在のデータベースから削除するストアド プロシージャの名前を挿入します。  
  
    ```tsql  
    DROP PROCEDURE <stored procedure name>;  
    GO  
    ```  
  
6.  任意の依存オブジェクトおよびスクリプトからプロシージャへの参照を削除します。  
  
## 参照  
 [ストアド プロシージャの作成](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [ストアド プロシージャの変更](../../relational-databases/stored-procedures/modify-a-stored-procedure.md)   
 [ストアド プロシージャの名前の変更](../../relational-databases/stored-procedures/rename-a-stored-procedure.md)   
 [ストアド プロシージャの定義の表示](../../relational-databases/stored-procedures/view-the-definition-of-a-stored-procedure.md)   
 [ストアド プロシージャの依存関係の表示](../../relational-databases/stored-procedures/view-the-dependencies-of-a-stored-procedure.md)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-procedure-transact-sql.md)  
  
  