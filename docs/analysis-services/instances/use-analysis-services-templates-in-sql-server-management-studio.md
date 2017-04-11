---
title: "SQL Server Management Studio での Analysis Services テンプレートの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54ad1954-22e2-4628-b334-8fad8e9433b8
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 12
---
# SQL Server Management Studio での Analysis Services テンプレートの使用
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、XMLA スクリプト、DMX クエリ、または MDX クエリの迅速な作成、キューブまたはテーブル モデルの KPI の作成、バックアップ操作および復元操作のスクリプト作成、および他の多数のタスクを実行するためのテンプレートのセットを提供します。 テンプレートは、[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] の**テンプレート エクスプローラー**にあります。  
  
 このトピックでは、多次元モデルとテーブル モデルのテンプレートの一覧を示し、メタデータ エクスプローラーとテンプレート エクスプローラーを使用して MDX クエリと XMLA ステートメントを構築する方法の例を示します。  
  
 このトピックのセクションは次のとおりです。  
  
 [Analysis Services テンプレートとして開く](#bkmk_usingTE)  
  
 [テンプレートを使用してテーブル モデルで MDX クエリを構築および実行する](#BKMK_Building_Queries)  
  
 [テンプレートから XMLA スクリプトを作成する](#bkmk_backup)  
  
 [XMLA テンプレートを使用してスキーマ行セット クエリを生成する](#bkmk_schemarowset)  
  
 [Analysis Services テンプレート リファレンス](#bkmk_Ref)  
  
 このトピックでは、DMX テンプレートについては説明しません。 テンプレートを使用してデータ マイニング クエリを作成する方法の例については、「[SQL Server Management Studio で DMX クエリを作成する](../../analysis-services/data-mining/create-a-dmx-query-in-sql-server-management-studio.md)」または「[テンプレートからの単一予測クエリの作成](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)」をご覧ください。  
  
##  <a name="bkmk_usingTE"></a> Analysis Services テンプレートとして開く  
 データベース エンジン クエリおよび Analysis Services クエリとコマンドのすべてのテンプレートは、テンプレート エクスプローラーで利用可能です。  
  
 **テンプレート エクスプローラー**を開くには、**[表示]** メニューから選択します。 次に、キューブ アイコンをクリックして、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で使用できるテンプレートの一覧を表示します。  
  
 ![Analysis Services 用にフィルター処理されたテンプレート エクスプローラー](../../analysis-services/instances/media/ssas-templateexplorer.gif "Analysis Services 用にフィルター処理されたテンプレート エクスプローラー")  
  
 テンプレートを開くには、テンプレート名を右クリックして **[開く]** をクリックするか、開いているクエリ ウィンドウにテンプレートをドラッグします。 クエリ ウィンドウが開かれた後は、ツール バーまたは [クエリ] メニューのコマンドを使用してステートメントを構築できます。  
  
-   クエリの構文を検査するには、**[解析]** をクリックします。  
  
-   クエリを実行するには、**[実行]** をクリックします。  
  
     実行中のクエリを停止するには、**[クエリ実行のキャンセル]** をクリックします。  
  
-   画面の下部の **[結果]** タブに表示されるクエリの結果を確認します。  
  
     **[メッセージ]** タブに切り替えて、クエリの実行に関連付けられている、返されるレコード、エラー、クエリ ステートメント、その他のメッセージの数を確認します。 たとえば、Direct Query モードで実行されるモデルに対して DAX ステートメントを実行した場合、xVelocity メモリ内分析エンジン (VertiPaq) によって生成される Transact-SQL ステートメントを確認できます。  
  
##  <a name="BKMK_Building_Queries"></a> テンプレートを使用してテーブル モデルで MDX クエリを構築および実行する  
 この例では、テーブル モデル データベースをデータ ソースとして使用することで、SQL Server Management Studio で MDX クエリを作成する方法を示しています。 お使いのコンピューターでこの例を繰り返すには、[Adventureworks テーブル モデル サンプル プロジェクトをダウンロード](http://go.microsoft.com/fwlink/?LinkId=231183)してください。  
  
> [!WARNING]  
>  直接クエリ モードで配置されているテーブル モデルに対して MDX クエリを使用することはできません。 ただし、EVALUATE コマンドと DAX テーブル クエリを使用して、同等のクエリを送信することができます。 詳細については、「[DAX クエリのパラメーター](http://msdn.microsoft.com/ja-jp/c5841b4e-3395-4237-815b-9822a691e544)」を参照してください。  
  
#### MDX クエリをテンプレートから作成する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、クエリするテーブル モデルが含まれているインスタンスを開きます。 データベース アイコンを右クリックし、**[新しいクエリ]** をポイントして **[MDX]** をクリックします。  
  
2.  テンプレート ブラウザーで、Analysis Services テンプレートで **[MDX]** を開き、**[クエリ]** を開きます。 クエリ ウィンドウに **[基本のクエリ]** をドラッグします。  
  
3.  **メタデータ エクスプローラー**を使用して、次のフィールドとメジャーをクエリ テンプレートにドラッグします。  
  
    1.  \<row_axis, mdx_set> を **[Product Category].[Product Category Name]** に置換します。  
  
    2.  \<column_axis, mdx_set> を **[Date].[Calendar Year].[Calendar Year]** に置換します。  
  
    3.  \<from_clause, mdx_name> を **[Internet Sales]** に置換します。  
  
    4.  \<where_clause, mdx_set> を **[Measures].[Internet Total Sales]** に置換します。  
  
4.  クエリはそのまま実行できますが、特定のメンバーを返す関数を追加するなど、変更を加えることもできます。 たとえば、**[Product Category].[Product Category Name]** の後に「**.members**」と入力します。 詳細については、「[メンバー式の使用](../../mdx/using-member-expressions.md)」をご覧ください。  
  
##  <a name="bkmk_backup"></a> テンプレートから XMLA スクリプトを作成する  
 テンプレート エクスプローラーで提供される XMLA コマンド テンプレートは、インスタンスが多次元モード、データ マイニング モード、テーブル モードのいずれにあっても、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの監視と更新のためのスクリプトの作成に使用できます。 **XMLA** テンプレートには、次の種類のスクリプトのサンプルが含まれます。  
  
-   バックアップ操作、復元操作、および同期操作  
  
-   指定されたプロセスまたはコマンドのキャンセル  
  
-   オブジェクトの処理  
  
-   スキーマ行セットの検出  
  
-   サーバーの状態 (ジョブ、接続、トランザクション、メモリ、パフォーマンス カウンターなど) の監視  
  
#### バックアップ コマンド スクリプトをテンプレートから作成する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、クエリするデータベースが含まれているインスタンスを開きます。 データベース アイコンを右クリックし、**[新しいクエリ]** をポイントして **[XMLA]** をクリックします。  
  
    > [!WARNING]  
    >  制限リストを変更することで、または接続ダイアログでデータベースを指定することで、XMLA クエリのコンテキストを設定することはできません。 クエリを行うデータベースから XMLA クエリ ウィンドウを開く必要があります。  
  
2.  **バックアップ** テンプレートを空のクエリ ウィンドウにドラッグします。  
  
3.  \<DatabaseID>要素内でテキストをダブルクリックします。  
  
4.  オブジェクト エクスプローラーで、バックアップするデータベースを選択し、DatabaseID 要素の角かっこの間にデータベースをドラッグ アンド ドロップします。  
  
5.  \<File> 要素内でテキストをダブルクリックします。 ファイル拡張子として .abf を使用し、バックアップ ファイル名を入力します。 既定のバックアップの場所を使用しない場合は、ファイルの完全パスを指定します。 詳細については、「[データベースのバックアップ、復元、および同期 (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)」をご覧ください。  
  
##  <a name="bkmk_schemarowset"></a> XMLA テンプレートを使用してスキーマ行セット クエリを生成する  
 **テンプレート エクスプローラー**には、スキーマ行セット クエリのテンプレートが 1 つだけ含まれています。 このテンプレートを使用するには、必要な要素、制限として使用できる列など、使用する個々のスキーマ行セットの要件を把握している必要があります。 詳細については、「[Analysis Services のスキーマ行セット](../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)」をご覧ください。  
  
 使いやすさのために、スキーマ行セットの多くが動的管理ビュー (DMV) としても公開されています。 対応する DMV を使用することで、Transact-SQL などの構文を使用してスキーマ行セットのクエリを実行できます。 たとえば、次のクエリは同じ結果を返しますが、1 つは XML 形式で、1 つはテーブル形式で返されます。 DMV の詳細については、「[動的管理ビュー (DMV) を使用した Analysis Services の監視](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)」をご覧ください。  
  
 DMV として使用できるすべてのスキーマ行セットの一覧を返す DMV:   
  
```  
SELECT * FROM $system.DISCOVER_SCHEMA_ROWSETS  
```  
  
 使用できるすべてのスキーマ行セットの一覧を返す XMLA コマンド:   
  
```  
<Discover xmlns="urn:schemas-microsoft-com:xml-analysis">  
<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>  
    <Restrictions>  
<RestrictionList>  
</RestrictionList>  
</Restrictions>  
    <Properties>  
<PropertyList>  
   </PropertyList>  
</Properties>  
</Discover>  
```  
  
#### スキーマ行セット クエリを使用してテーブル モデルのデータ ソースの一覧を取得する  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、クエリするデータベースが含まれているインスタンスを開きます。 データベース アイコンを右クリックし、**[新しいクエリ]** をポイントして **[XMLA]** をクリックします。  
  
    > [!WARNING]  
    >  制限リストを変更することで、または接続ダイアログでデータベースを指定することで、XMLA クエリのコンテキストを設定することはできません。 クエリを行うデータベースから XMLA クエリ ウィンドウを開く必要があります。  
  
2.  **テンプレート エクスプローラー**を開き、**[スキーマ行セットの発見]** テンプレートを空のクエリ ウィンドウにドラッグします。  
  
3.  テンプレートで、[RequestType 要素 (XMLA)](../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) を次のテキストに置換します。 `<RequestType>MDSCHEMA_INPUT_DATASOURCES</RequestType>`  
  
4.  **[実行]**をクリックします。  
  
     期待される結果:  
  
    ```  
    <CATALOG_NAME>AW Internet Sales Tabular Model_ 24715b71-ea74-4828-aefc-d4c12c15db64</CATALOG_NAME>   
    <DATASOURCE_NAME>SqlServer localhost AdventureWorksDW2012</DATASOURCE_NAME>   
    <DATASOURCE_TYPE>Relational</DATASOURCE_TYPE>   
    <CREATED_ON>2011-10-12T20:27:05.196667</CREATED_ON>   
    <LAST_SCHEMA_UPDATE>2011-10-12T20:27:05.196667</LAST_SCHEMA_UPDATE>   
    <DESCRIPTION />   
    <TIMEOUT>0</TIMEOUT>   
    <DBMS_NAME>Microsoft SQL Server</DBMS_NAME>   
    <DBMS_VERSION>11.00.1724</DBMS_VERSION>  
  
    ```  
  
##  <a name="bkmk_Ref"></a> Analysis Services テンプレート リファレンス  
 次のテンプレートは、Analysis Services データベースや、マイニング構造、マイニング モデル、キューブ、テーブル モデルなどのデータベース内のオブジェクトと一緒に使用するように提供されています。  
  
|カテゴリ|項目テンプレート|Description|  
|--------------|-------------------|-----------------|  
|DMX\モデル コンテンツ|コンテンツ クエリ|DMX SELECT FROM *\<model>*.CONTENT ステートメントを使用して、指定されたマイニング モデルのマイニング モデル スキーマ行セットの内容を取得する方法を示します。|  
||連続列値|DMX SELECT DISTINCT FROM *\<model>* ステートメントを DMX の **RangeMin** 関数および **RangeMax** 関数で使用して、指定されたマイニング モデルの連続列から指定された範囲の値のセットを取得する方法を示します。|  
||不連続列値|DMX SELECT DISTINCT FROM *\<model>* ステートメントを使用して、指定されたマイニング モデルの不連続列から値の完全なセットを取り出す方法を示します。|  
||ドリルスルー クエリ|DMX SELECT * FROM Model.CASES ステートメントを DMX IsInNode 関数と共に使用してドリルスルー クエリを実行する方法を示します。|  
||モデル属性|DMX System.GetModelAttributes 関数を使用して、モデルで使用される属性の一覧を返す方法を示します。|  
||PMML コンテンツ|DMX SELECT \* FROM *\<model>*.PMML ステートメントを使用して、Predictive Model Markup Language (PMML) 表記をサポートするアルゴリズムで使用する、マイニング モデルの Predictive Model Markup Language (PMML) 表記を取得する方法を示します。|  
|DMX\モデル管理|モデルの追加|DMX ALTER MINING MODEL STRUCTURE ステートメントを使用してマイニング モデルを追加する方法を示します。|  
||モデルの削除|DMX DELETE * FROM MINING MODEL ステートメントを使用して、指定されたマイニング モデルのコンテンツを削除する方法を示します。|  
||構造ケースの削除|DMX DELETE FROM MINING STRUCTURE ステートメントを使用して、マイニング モデル構造ケースを削除する方法を示します。|  
||構造の削除|DMX DELETE FROM MINING STRUCTURE ステートメントを使用してマイニング モデル構造を削除する方法を示します。|  
||PMML からの作成|DMX CREATE MINING MODEL ステートメントで FROM PMML 句を使用して、PMML 表記からマイニング モデルを作成する方法を示します。|  
||入れ子になった構造の作成|DMX CREATE MINING STRUCTURE ステートメントを、入れ子になった列の定義リストと共に使用して、入れ子になった列を持つマイニング モデルを作成する方法を示します。|  
||構造の作成|DMX CREATE MINING STRUCTURE ステートメントを使用して、マイニング モデルを作成する方法を示します。|  
||モデルの削除|DMX DROP MINING MODEL ステートメントを使用して、既存のマイニング モデルを削除する方法を示します。|  
||構造の削除|DMX DROP MINING STRUCTURE ステートメントを使用して、既存のマイニング構造を削除する方法を示します。|  
||モデルのエクスポート|DMX EXPORT MINING MODEL ステートメントで WITH DEPENDENCIES および PASSWORD 句を使用し、マイニング モデルが依存しているデータ ソースおよびデータ ソース ビューを含むマイニング モデルをファイルにエクスポートする方法を示します。|  
||構造のエクスポート|DMX EXPORT MINING STRUCTURE ステートメントで WITH DEPENDENCIES 句を使用し、マイニング構造に含まれるすべてのマイニング モデルや、マイニング構造が依存しているデータ ソースおよびデータ ソース ビューなどのマイニング構造をファイルにエクスポートする方法を示します。|  
||[インポート]|DMX IMPORT FROM ステートメントで WITH PASSWORD 句を使用して、インポートを実行する方法を示します。|  
||モデルの名前変更|DMX RENAME MINING MODEL ステートメントを使用して、既存のマイニング モデルの名前を変更する方法を示します。|  
||構造名の変更|DMX RENAME MINING STRUCTURE ステートメントを使用して、既存のマイニング構造の名前を変更する方法を示します。|  
||モデルのトレーニング|DMX INSERT INTO MINING MODEL ステートメントを使用して、以前にトレーニングした構造の内部のマイニング モデルをトレーニングする方法を示します。|  
||入れ子になった構造のトレーニング|DMX INSERT INTO MINING STRUCTURE ステートメントを SHAPE ソース データ クエリと組み合わせ、クエリを使用して既存のデータ ソースから取得した、入れ子になったテーブルを含んでいるデータで、入れ子になった列を含んでいるマイニング モデルをトレーニングする方法を示します。|  
||構造のトレーニング|DMX INSERT INTO MINING STRUCTURE 構造と OPENQUERY ソース データ クエリを組み合わせ、マイニング構造をトレーニングする方法を示します。|  
|DMX\予測クエリ|基本予測|DMX SELECT FROM *\<model>* PREDICTION JOIN ステートメントを OPENQUERY ソース データ クエリと組み合わせ、既存のデータ ソースからクエリを使用して取り出したデータを使用して、マイニング モデルに対して予測クエリを実行する方法を示します。|  
||入れ子になった予測|DMX SELECT FROM *\<model>* PREDICTION JOIN ステートメントを SHAPE および OPENQUERY ソース データ クエリと組み合わせ、既存のデータ ソースからクエリを使用して取り出した、入れ子になったテーブルを含むデータを使用して、マイニング モデルに対して予測クエリを実行する方法を示します。|  
||入れ子になった単一予測|DMX SELECT FROM *\<model>* NATURAL PREDICTION JOIN 句を使用して、予測クエリの列で明示的に指定された 1 つの値を使用して、マイニング モデルに対して予測クエリを実行する方法を示します。この列は、マイニング モデルの列と名前が一致し、また、UNION ステートメントを使用して作成された、入れ子になったテーブルの値のセットが含まれます。このテーブルの名前もマイニング モデルの入れ子になった列に一致します。|  
||単一予測|DMX SELECT FROM \<model> NATURAL PREDICTION JOIN ステートメントを使用して、予測クエリで明示的に指定され、列の名前がマイニング モデル内の列と一致する列にある 1 つの値を使用して、マイニング モデルに対して予測クエリを実行する方法を示します。|  
||ストアド プロシージャ コール|DMX CALL ステートメントを使用してストアド プロシージャを呼び出す方法を示します。|  
|MDX\式|移動平均 - 固定|MDX の **ParallelPeriod** 関数および **CurrentMember** 関数を自然な順序のセットと共に使用して、時間ディメンションの階層の一定期間においてメジャーの移動平均を提供する、計算メジャーの作成方法を示します。|  
||移動平均 - 可変|**Avg** 関数内の MDX の **CASE** ステートメントを使用して、時間ディメンションの階層の可変期間においてメジャーの移動平均を提供する、計算メジャーの作成方法を示します。|  
||期間取得|計算メンバー内の MDX の **PeriodsToDate** 関数の使用方法を示します。|  
||親に対する比率|MDX の **Parent** 関数を使用して、指定された階層内の親メンバーのそれぞれの子のメジャーの比率を表す、計算メジャーを作成する方法を示します。|  
||合計に対する比率|すべてのメンバーを使用して、指定された階層内の各メンバーのメジャーの比率を表す、計算メジャーを作成する方法を示します。|  
|MDX\クエリ|基本のクエリ|MDX クエリの構築に使用する基本の MDX SELECT ステートメントを示します。|  
||KPI クエリ|MDX の **KPIValue** 関数と **KPIGoal** 関数を使用して、MDX クエリ内の主要業績評価指標 (KPI) 情報を取得する方法を示します。|  
||副選択クエリ|別の SELECT ステートメントによって定義されたサブキューブから情報を取得する MDX SELECT ステートメントを作成する方法を示します。|  
||計算されるメンバーあり|SELECT ステートメントで MDX WITH 句を使用して、MDX クエリの計算メンバーを定義する方法を示します。|  
||名前付きセットあり|SELECT ステートメントで MDX WITH 句を使用して、MDX クエリの名前付きセットを定義する方法を示します。|  
|XMLA\管理|バックアップ|XMLA の **Backup** コマンドを使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースをファイルにバックアップする方法を示します。|  
||キャンセル|XMLA の **Cancel** コマンドを使用して、現在のセッション、データベース、またはインスタンス上で実行しているすべての操作を取り消す方法を示します。現在のセッションは管理者またはサーバーの管理者以外のユーザー、データベースは管理者、インスタンスはサーバー管理者がキャンセルできます。|  
||リモート パーティション データベースの作成|XMLA の **Create** コマンドを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) データベース要素と共に使用して、リモート パーティションを保存する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースおよびデータ ソースを作成する方法を示します。|  
||Del|XMLA の **Delete** コマンドを使用して、既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを削除する方法を示します。|  
||ディメンションの処理|XMLA の **Batch** コマンドを **Parallel** 要素および **Process** コマンドと組み合わせ、並列バッチ操作を使用してディメンションの属性を更新する方法を示します。|  
||パーティションの処理|XMLA の **Batch** コマンドを **Parallel** 要素および **Process** コマンドと組み合わせ、並列バッチ操作を使用してパーティションを完全に処理する方法を示します。|  
||復元|XMLA の **Restore** コマンドを使用して、既存のバックアップ ファイルから [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する方法を示します。|  
||同期|XMLA の **Synchronize** コマンドで、SynchronizeSecurity タグの SkipMembership オプションを使用して別の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを現在の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースと同期させる方法を示します。|  
|XMLA\スキーマ行セット|スキーマ行セットの発見|XMLA の **Discover** メソッドを使用して、DISCOVER_SCHEMA_ROWSETS スキーマ行セットの内容を取得する方法を示します。|  
|XMLA\サーバー ステータス|接続|XMLA の **Discover** メソッドを使用して、DISCOVER_CONNECTIONS スキーマ行セットの内容を取得する方法を示します。|  
||ジョブ|XMLA の **Discover** メソッドを使用して、DISCOVER_JOBS スキーマ行セットの内容を取得する方法を示します。|  
||[場所]|XMLA の **Discover** メソッドを使用して、場所バックアップ ファイルのパスを指定して DISCOVER_LOCATIONS スキーマ行セットの内容を取得する方法を示します。|  
||Locks|XMLA の **Discover** メソッドを使用して、DISCOVER_LOCKS スキーマ行セットの内容を取得する方法を示します。|  
||メモリ許可|XMLA の **Discover** メソッドを使用して、DISCOVER_MEMORYGRANT スキーマ行セットの内容を取得する方法を示します。|  
||パフォーマンス カウンター|XMLA の **Discover** メソッドを使用して、DISCOVER_PERFORMANCE_COUNTERS スキーマ行セットの内容を取得する方法を示します。|  
||セッション|XMLA の **Discover** メソッドを使用して、DISCOVER_SESSIONS スキーマ行セットの内容を取得する方法を示します。|  
||トレース|XMLA の **Discover** メソッドを使用して、DISCOVER_TRACES スキーマ行セットの内容を取得する方法を示します。|  
||トランザクション|XMLA の **Discover** メソッドを使用して、DISCOVER_TRANSACTION スキーマ行セットの内容を取得する方法を示します。|  
  
## 参照  
 [多次元式 (MDX) リファレンス](../../mdx/multidimensional-expressions-mdx-reference.md)   
 [データ マイニング拡張機能 (DMX) リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)   
 [Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)  
  
  