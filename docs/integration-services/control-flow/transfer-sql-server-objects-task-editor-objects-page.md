---
title: "[SQL Server オブジェクトの転送タスク エディター] ([オブジェクト] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transfersqlserverobjects.objects.f1"
helpviewer_keywords: 
  - "SQL Server オブジェクトの転送タスク エディター"
ms.assetid: 8cc09118-70ac-4013-8308-d87f8411ca0c
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# [SQL Server オブジェクトの転送タスク エディター] ([オブジェクト] ページ)
  **[SQL Server オブジェクトの転送タスク エディター]** ダイアログ ボックスの **[オブジェクト]** ページを使用すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス間で 1 つまたは複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトをコピーするためのプロパティを指定できます。 コピーできる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトには、テーブル、ビュー、ストアド プロシージャ、およびユーザー定義関数などがあります。 このタスクの詳細については、「 [Transfer SQL Server Objects Task](../../integration-services/control-flow/transfer-sql-server-objects-task.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクを作成するユーザーは、転送元サーバー オブジェクトをコピー用に選択するために必要な権限と、オブジェクトの転送先の転送先サーバー データベースにアクセスするために必要な権限を持っている必要があります。  
  
## 静的オプション  
 **SourceConnection**  
 SMO 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックしてコピー元のサーバーへの新しい接続を作成します。  
  
 **[SourceDatabase]**  
 オブジェクトのコピー元の転送元サーバー上のデータベースを選択します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックしてコピー先のサーバーへの新しい接続を作成します。  
  
 **[DestinationDatabase]**  
 オブジェクトのコピー先の転送先サーバー上のデータベースを選択します。  
  
 **[DropObjectsFirst]**  
 選択したオブジェクトをコピーを開始する前に転送先サーバー上で削除するかどうかを選択します。  
  
 **[IncludeExtendedProperties]**  
 転送元サーバーから転送先サーバーにオブジェクトをコピーするときに拡張プロパティを含めるかどうかを選択します。  
  
 **[CopyData]**  
 転送元サーバーから転送先サーバーにオブジェクトをコピーするときにデータを含めるかどうかを選択します。  
  
 **[ExistingData]**  
 転送先サーバーにデータをどのようにコピーするかを指定します。 このプロパティには、次の表に示すオプションがあります。  
  
|値|Description|  
|-----------|-----------------|  
|**[置換]**|転送先サーバー上のデータは上書きされます。|  
|**追加**|転送元サーバーからコピーされたデータは、転送先サーバー上の既存のデータに追加されます。|  
  
> [!NOTE]  
>  **[ExistingData]** オプションは、 **[CopyData]** が **[True]** に設定されている場合にのみ使用できます。  
  
 **[CopySchema]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトの転送タスクによる処理中にスキーマをコピーするかどうかを選択します。  
  
> [!NOTE]  
>  **[CopySchema]** は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのみ使用できます。  
  
 **[UseCollation]**  
 転送元サーバー上で指定されている照合順序をオブジェクトの転送に含めるかどうかを選択します。  
  
 **[IncludeDependentObjects]**  
 コピーの対象として選択されたオブジェクトをコピーするときに、そのオブジェクトに依存している他のオブジェクトもコピーするかどうかを選択します。  
  
 **[CopyAllObjects]**  
 指定した転送元データベース内のすべてのオブジェクトをコピーするか、選択したオブジェクトだけをコピーするかを選択します。  このオプションを [False] に設定すると、オブジェクトを転送するためのオプションが表示され、さらに **[CopyAllObjects]**セクションに動的オプションが表示されます。  
  
 **[ObjectsToCopy]**  
 **[ObjectsToCopy]** を展開して、転送元データベースから転送先データベースにコピーするオブジェクトを指定します。  
  
> [!NOTE]  
>  **[ObjectsToCopy]** は、**[CopyAllObjects]** が **[False]** に設定されている場合にのみ使用できます。  
  
 次の種類のオブジェクトをコピーするオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 アセンブリ  
  
 パーティション関数  
  
 パーティション構成  
  
 スキーマ  
  
 ユーザー定義集計  
  
 ユーザー定義データ型  
  
 XML スキーマ コレクション  
  
 **[CopyDatabaseUsers]**  
 データベース ユーザーを転送に含めるかどうかを指定します。  
  
 **[CopyDatabaseRoles]**  
 データベース ロールを転送に含めるかどうかを指定します。  
  
 **[CopySqlServerLogins]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを転送に含めるかどうかを指定します。  
  
 **[CopyObjectLevelPermissions]**  
 オブジェクトレベルの権限を転送に含めるかどうかを指定します。  
  
 **[CopyIndexes]**  
 インデックスを転送に含めるかどうかを指定します。  
  
 **[CopyTriggers]**  
 トリガーを転送に含めるかどうかを指定します。  
  
 **[CopyFullTextIndexes]**  
 フルテキスト インデックスを転送に含めるかどうかを指定します。  
  
 **[CopyPrimaryKeys]**  
 主キーを転送に含めるかどうかを指定します。  
  
 **[CopyForeignKeys]**  
 外部キーを転送に含めるかどうかを指定します。  
  
 **[GenerateScriptsInUnicode]**  
 転送スクリプトを Unicode 形式で生成するかどうかを指定します。  
  
## 動的オプション  
  
### [CopyAllObjects] = [False]  
 **[CopyAllTables]**  
 指定した転送元データベース内のすべてのテーブルをコピーするか、選択したテーブルだけをコピーするかを選択します。  
  
 **[TablesList]**  
 **[テーブルの選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllViews]**  
 指定した転送元データベース内のすべてのビューをコピーするか、選択したビューだけをコピーするかを選択します。  
  
 **[ViewsList]**  
 **[ビューの選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllStoredProcedures]**  
 指定した転送元データベース内のすべてのユーザー定義ストアド プロシージャをコピーするか、選択したプロシージャだけをコピーするかを選択します。  
  
 **[StoredProceduresList]**  
 **[ストアド プロシージャの選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllUserDefinedFunctions]**  
 指定した転送元データベース内のすべてのユーザー定義関数 (UDF) をコピーするか、選択した UDF だけをコピーするかを選択します。  
  
 **[UserDefinedFunctionsList]**  
 **[ユーザー定義関数の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllDefaults]**  
 指定した転送元データベース内のすべての既定値をコピーするか、選択した既定値だけをコピーするかを選択します。  
  
 **[DefaultsList]**  
 **[既定値の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllUserDefinedDataTypes]**  
 指定した転送元データベース内のすべてのユーザー定義データ型をコピーするか、選択したユーザー定義データ型だけをコピーするかを選択します。  
  
 **[UserDefinedDataTypesList]**  
 **[ユーザー定義データ型の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllPartitionFunctions]**  
 指定した転送元データベース内のすべてのユーザー定義パーティション関数をコピーするか、選択したパーティション関数だけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[PartitionFunctionsList]**  
 **[パーティション関数の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllPartitionSchemes]**  
 指定した転送元データベース内のすべてのパーティション構成をコピーするか、選択したパーティション構成だけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[PartitionSchemesList]**  
 **[パーティション構成の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllSchemas]**  
 指定した転送元データベース内のすべてのスキーマをコピーするか、選択したスキーマだけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[SchemasList]**  
 **[スキーマの選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllSqlAssemblies]**  
 指定した転送元データベース内のすべての SQL アセンブリをコピーするか、選択した SQL アセンブリだけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[SqlAssembliesList]**  
 **[SQL アセンブリの選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllUserDefinedAggregates]**  
 指定した転送元データベース内のすべてのユーザー定義集計をコピーするか、選択したユーザー定義集計だけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[UserDefinedAggregatesList]**  
 **[ユーザー定義集計の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllUserDefinedTypes]**  
 指定した転送元データベース内のすべてのユーザー定義型 (UDT) をコピーするか、選択した UDT だけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[UserDefinedTypes]**  
 **[ユーザー定義型の選択]** ダイアログ ボックスが開きます。  
  
 **[CopyAllXmlSchemaCollections]**  
 指定した転送元データベース内のすべての XML スキーマ コレクションをコピーするか、選択した XML スキーマ コレクションだけをコピーするかを選択します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]でのみサポートされます。  
  
 **[XmlSchemaCollectionsList]**  
 **[XML スキーマ コレクションの選択]** ダイアログ ボックスが開きます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [[SQL Server オブジェクトの転送タスク エディター] &#40;[全般] ページ&#41;](../Topic/Transfer%20SQL%20Server%20Objects%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [SQL Server インストールにおけるセキュリティの考慮事項](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  