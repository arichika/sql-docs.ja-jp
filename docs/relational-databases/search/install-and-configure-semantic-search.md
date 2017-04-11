---
title: "セマンティック検索のインストールと構成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-search"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "セマンティック検索 [SQL Server], インストール"
  - "セマンティック検索 [SQL Server], 構成"
ms.assetid: 2cdd0568-7799-474b-82fb-65d79df3057c
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# セマンティック検索のインストールと構成
  統計的セマンティック検索の前提条件と、これらをインストールまたは確認する方法について説明します。  
  
## セマンティック検索のインストール  
  
###  <a name="HowToCheckInstalled"></a> 方法: セマンティック検索がインストールされているかどうかを確認する  
 [SERVERPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/serverproperty-transact-sql.md) メタデータ関数の **IsFullTextInstalled** プロパティに対してクエリを実行します。  
  
 戻り値 1 は、データベースに対してフルテキスト検索とセマンティック検索がインストールされていることを示します。戻り値 0 は、フルテキスト検索とセマンティック検索がインストールされていないことを示します。  
  
```tsql  
SELECT SERVERPROPERTY('IsFullTextInstalled');  
GO  
```  
  
###  <a name="BasicsSemanticSearch"></a> 方法: セマンティック検索をインストールする  
 セマンティック検索をインストールするには、セットアップ中、**[インストールする機能]** ページで **[検索のためのフルテキスト抽出とセマンティック抽出]** を選択します。  
  
 セマンティック検索はフルテキスト検索に依存します。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 2 つのオプション機能は一緒にインストールされます。  
  
## セマンティック言語統計データベースをインストールまたは削除する  
 セマンティック検索は、別途、"セマンティック言語統計データベース" と呼ばれる外部の機能に依存しています。 このデータベースには、セマンティック検索で必要な統計的言語モデルが含まれています。 1 つのセマンティック言語統計データベースには、セマンティック インデックス作成でサポートされるすべての言語の言語モデルが含まれています。  
  
###  <a name="HowToCheckDatabase"></a> 方法: セマンティック言語統計データベースがインストールされているかどうかを確認する  
 カタログ ビュー [sys.fulltext_semantic_language_statistics_database &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md) に対してクエリを実行します。  
  
 実行対象のインスタンスにセマンティック言語統計データベースがインストールされ登録されている場合、クエリ結果には、そのデータベースに関する単一行から成る情報が格納されています。  
  
```tsql  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
###  <a name="HowToInstallModel"></a> 方法: セマンティック言語統計データベースをインストール、アタッチ、および登録する  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ プログラムでは、セマンティック言語統計データベースはインストールされません。 セマンティック インデックス作成の前提条件であるセマンティック言語統計データベースをセットアップするには、次の作業を実行します。  
  
 **1.セマンティック言語統計データベースをインストールします。**  
 1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール メディアでセマンティック言語統計データベースを見つけるか、Web からダウンロードします。  
  
    -   **のインストール メディアで** SemanticLanguageDatabase.msi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] という名前の Windows インストーラー パッケージを見つけます。  
  
    -   [ダウンロード センターの「](http://go.microsoft.com/fwlink/?LinkID=296743) Microsoft® SQL Server® 2014 Semantic Language Statistics [!INCLUDE[msCoName](../../includes/msconame-md.md)] 」ページからインストーラー パッケージをダウンロードします。  
  
2.  **SemanticLanguageDatabase.msi** Windows インストーラー パッケージを実行して、データベースおよびログ ファイルを抽出します。  
  
     抽出先のディレクトリは必要に応じて変更できます。 既定では、Program Files フォルダー内の **Microsoft Semantic Language Database** という名前のフォルダーにファイルが抽出されます。 MSI ファイルには、圧縮データベース ファイルおよびログ ファイルが格納されます。  
  
3.  抽出されたデータベース ファイルとログ ファイルを、ファイル システム内の適切な場所に移動します。  
  
     ファイルを既定の場所に残した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の別のインスタンスのデータベースの別のコピーを抽出できません。  
  
> [!IMPORTANT]  
>  セマンティック言語統計データベースの抽出時に、ファイル システム内の既定の場所にあるデータベース ファイルおよびログ ファイルに制限付きの権限が割り当てられます。 そのため、データベースを既定の場所に残した場合、ユーザーによってはデータベースにアタッチする権限がない可能性があります。 データベースをアタッチしようとしたときにエラーが発生した場合は、ファイルを移動するか、ファイル システムの権限を確認し、必要に応じて修正してください。  
  
 **2.セマンティック言語統計データベースをアタッチします。**  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を使用するか、[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) を **FOR ATTACH** 構文で呼び出して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータベースをアタッチします。 詳細については、「[データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)」を参照してください。  
  
 既定では、データベースの名前が **semanticsdb**になります。 データベースをアタッチする際、必要に応じて、別の名前を付けてください。 この名前は、後続の手順でデータベースを登録する際に必要になります。  
  
```tsql  
CREATE DATABASE semanticsdb  
            ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb.mdf' )  
            LOG ON ( FILENAME = 'C:\Microsoft Semantic Language Database\semanticsdb_log.ldf' )  
            FOR ATTACH;  
GO  
```  
  
 このコード例では、データベースを既定の場所から新しい場所に移動済みであることを前提としています。  
  
 **3.セマンティック言語統計データベースを登録します。**  
 データベースのアタッチ時に指定した名前を使用して、ストアド プロシージャ [sp_fulltext_semantic_register_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-register-language-statistics-db-transact-sql.md) を次のように呼び出します。  
  
```tsql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = N'semanticsdb';  
GO  
```  
  
###  <a name="HowToUnregister"></a> 方法: セマンティック言語統計データベースを登録解除、デタッチ、および削除する  
 **セマンティック言語統計データベースを登録解除します。**  
 ストアド プロシージャ [sp_fulltext_semantic_unregister_language_statistics_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-semantic-unregister-language-statistics-db-transact-sql.md) を呼び出します。 セマンティック言語統計データベースは 1 つのインスタンスにつき 1 つしか存在しないため、データベースの名前を指定する必要はありません。  
  
```tsql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
 **セマンティック言語統計データベースをデタッチします。**  
 ストアド プロシージャ [sp_detach_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md) を呼び出し、データベース名を指定します。  
  
```tsql  
USE master;  
GO  
  
EXEC sp_detach_db @dbname = N'semanticsdb';  
GO  
```  
  
 **セマンティック言語統計データベースを削除します。**  
 データベースの登録を解除し、デタッチした後は、データベース ファイルを簡単に削除できます。 アンインストール プログラムはありません。また、コントロール パネルの **[プログラムと機能]** のエントリもありません。  
  
###  <a name="reqinstall"></a> セマンティック言語統計データベースをインストールおよび削除するための要件と制限  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスでアタッチおよび登録できるセマンティック言語統計データベースは 1 つのみです。  
  
     1 台のコンピューターに存在する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各インスタンスには、それぞれ、セマンティック言語統計データベースの物理コピーが必要です。 個々のコピーをそれぞれのインスタンスにアタッチしてください。  
  
-   登録されている有効なセマンティック言語統計データベースをデタッチし、同じ名前の任意のデータベースに置き換えることはできません。 このような操作を行うと、アクティブなインデックス作成およびそれ以降のインデックス作成が失敗します。  
  
-   セマンティック言語統計データベースは読み取り専用です。 このデータベースはカスタマイズできません。 なんらかの方法でデータベースのコンテンツを変更すると、今後のセマンティック インデックス作成の結果が不明確になります。 このデータの元の状態を復元するには、変更後のデータベースを削除して、データベースの変更されていない新しいコピーをダウンロードおよびアタッチします。  
  
-   セマンティック言語統計データベースはデタッチまたは削除することができます。 アクティブなインデックス作成操作があり、データベースが読み取りロックされている場合、デタッチおよび削除の操作は失敗またはタイムアウトになります。 これは、従来と同じ動作です。 データベースが削除された後は、セマンティック インデックス作成操作が失敗します。  
  
## 新しいドキュメントの種類のオプション サポートをインストールする  
  
###  <a name="office"></a> 方法: Microsoft Office およびその他の Microsoft ドキュメントの種類の最新のフィルターをインストールする  
 このリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] の最新のワード ブレーカーとステマーがインストールされますが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office ドキュメントおよびその他の [!INCLUDE[msCoName](../../includes/msconame-md.md)] ドキュメントの種類の最新のフィルターはインストールされません。 これらのフィルターは、最新バージョンの [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office およびその他の [!INCLUDE[msCoName](../../includes/msconame-md.md)] アプリケーションで作成されたドキュメントのインデックスを作成するために必要です。 最新のフィルターをダウンロードするには、「 [Microsoft Office 2010 フィルター パック](http://go.microsoft.com/fwlink/?LinkId=218293)」を参照してください。  
  
  