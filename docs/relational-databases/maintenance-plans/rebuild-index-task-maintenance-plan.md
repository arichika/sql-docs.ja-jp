---
title: "[インデックスの再構築タスク] (メンテナンス プラン) | Microsoft Docs"
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
  - "reindex"
  - "sql13.swb.maint.reindex.f1"
helpviewer_keywords: 
  - "[インデックスの再構築タスク] ダイアログ ボックス"
ms.assetid: 33e2940b-139f-4563-b0cb-5683f08bd879
caps.latest.revision: 42
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 42
---
# [インデックスの再構築タスク] (メンテナンス プラン)
  **[インデックスの再構築タスク]** ダイアログ ボックスを使用すると、データベースのテーブルに新しい FILL FACTOR でインデックスを再作成できます。 FILL FACTOR は、後で拡張できるように、インデックスの各ページの空き領域の量を決定します。 FILL FACTOR が適用されるのはインデックスの作成時だけであるため、テーブルにデータが追加されるにつれて、各ページの空き容量は徐々に減少します。 データ ページおよびインデックス ページを再編成すると、再び空き領域を確保できます。  
  
 **[インデックスの再構築タスク]** では、ALTER INDEX ステートメントが使用されます。 このページで説明するオプションの詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)」を参照してください。  
  
## オプション  
 **接続**  
 このタスクを実行するときに使用するサーバー接続を選択します。  
  
 **新規**  
 このタスクを実行するときに使用する新しいサーバー接続を作成します。 **[新しい接続]** ダイアログ ボックスについては、後で説明します。  
  
 **データベース**  
 このタスクで操作するデータベースを指定します。  
  
-   **[すべてのデータベース]**  
  
     すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。  
  
-   **[すべてのシステム データベース]**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベース (tempdb を除く) を対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。 ユーザーが作成したデータベースではメンテナンス タスクは実行されません。  
  
-   **[すべてのユーザー データベース]**  
  
     ユーザーが作成したすべてのデータベースを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のシステム データベースではメンテナンス タスクは実行されません。  
  
-   **[これらのデータベース]**  
  
     選択されたデータベースだけを対象として、メンテナンス タスクを実行するメンテナンス プランを生成します。 このオプションをオンにする場合は、少なくとも 1 つのデータベースが一覧内で選択されている必要があります。  
  
    > [!NOTE]  
    >  メンテナンス プランは、互換性レベルが 80 以上に設定されているデータベースに対してのみ実行されます。 互換性レベルが 70 以下に設定されているデータベースは表示されません。  
  
 **オブジェクト**  
 **[選択]** グリッドでテーブル、ビュー、または両方を表示するように制限します。  
  
 **選択**  
 このタスクの対象とするテーブルまたはインデックスを指定します。 [オブジェクト] ボックスで **[テーブルとビュー]** が選択されている場合は、このオプションは利用できません。  
  
 **[ページごとの既定の空き領域]**  
 データベース内のテーブルに定義されているインデックスを削除し、インデックスの作成時に指定された FILL FACTOR を使用して、新しいインデックスを再作成します。  
  
 **[ページごとの空き領域を変更する]**  
 データベース内のテーブルに定義されているインデックスを削除し、指定した割合の空き領域が各インデックス ページに確保されるように自動的に計算される FILL FACTOR の値を使用してインデックスを再作成します。 指定するパーセント値を大きくすると、インデックス ページに確保される空き領域が増えて、より多くのデータをインデックスに追加できるようになります。 有効値は、0 ～ 100 です。  
  
 **[tempdb の結果を並べ替える]**  
 `SORT_IN_TEMPDB` オプションを使用して、インデックス作成中に生成された中間の並べ替え結果を一時的に格納する場所を決定します。 並べ替え操作が必要ない場合、または並べ替えをメモリ上で実行できる場合、 `SORT_IN_TEMPDB`オプションは無視されます。  
  
 **インデックスを埋め込む (Pad index)**  
 インデックスの埋め込みを指定します。  
  
 **[Keep index online] (オンラインのインデックスを保持する)**  
 `ONLINE` オプションを使用すると、インデックス操作の実行中に、ユーザーは基になるテーブルまたはクラスター化インデックス データ、および任意の関連付けられた非クラスター化インデックスにアクセスできます。  
  
> [!NOTE]  
>  オンラインでのインデックス操作は、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[SQL Server 2016 の各エディションがサポートする機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」を参照してください。  
  
 **[インデックスを再構築しない] | [オフラインでインデックスを再構築する]**  
 インデックスの種類がオンラインでは再構築できない場合の処理を指定します。  
  
 **MAXDOP**  
 並列プランの実行で使用されるプロセッサ数を制限する値を指定します。  
  
 **[Low Priority Used] (低優先度の使用)**  
 優先度の低いロックを待機するには、このオプションを選択します。  
  
 **[Abort after Wait] (待機後に中止)**  
 **[最長期間]** で指定した時間が経過した後に行う処理を指定します。  
  
 **[最長期間]**  
 優先度の低いロックを待機する時間を指定します。  
  
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
 Windows 認証を使用して [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスに接続します。  
  
 **[特定のユーザー名とパスワードを使用する]**  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 認証を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。 このオプションは利用できません。  
  
 **ユーザー名**  
 認証に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを指定します。 このオプションは利用できません。  
  
 **Password**  
 認証に使用するパスワードを指定します。 このオプションは利用できません。  
  
## 参照  
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [DBCC DBREINDEX &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-dbreindex-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)   
 [オンライン インデックス操作のガイドライン](../../relational-databases/indexes/guidelines-for-online-index-operations.md)   
 [オンライン インデックス操作の動作原理](../../relational-databases/indexes/how-online-index-operations-work.md)   
 [オンラインでのインデックス操作の実行](../../relational-databases/indexes/perform-index-operations-online.md)  
  
  