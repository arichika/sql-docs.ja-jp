---
title: "SQL Server Data Tools (SSDT) の変更ログ | Microsoft Docs"
ms.custom: 
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssdt
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b071f8b8-c8e5-44e0-bbb6-04804dd1863a
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8798c5319cdce7b68f71868722aacfbf4cb34d9f
ms.lasthandoff: 04/11/2017

---
# <a name="changelog-for-sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT) の変更ログ
この変更ログは、[Visual Studio 2015 用 SQL Server Data Tools (SSDT)](https://msdn.microsoft.com/library/mt204009.aspx) ([SQL Server 2016](https://msdn.microsoft.com/library/ms130214.aspx) と共にリリースされる) のものです。  
  
新機能および変更点の詳細については、[SSDT チーム ブログ](https://blogs.msdn.microsoft.com/ssdt/)を参照してください。  

## <a name="ssdt-165-for-sql-server-2016"></a>SSDT 16.5 (SQL Server 2016 用)
リリース日: 2016 年 10 月 20 日

ビルド番号: 14.0.61021.0

**新機能**


### <a name="connection-improvements"></a>接続の強化

* **[参照]** タブの新しい検索ボックスを使用すると、ローカル サーバー、ネットワーク サーバー、および Azure SQL データベースをフィルター処理できます。 これは、多数のサーバーまたはデータベースがリストに表示される場合に便利です。
* **[履歴]** タブには、お気に入りをピン留めする、またはピン留めを外すための右クリック メニュー オプションと、履歴から接続を削除するための新しいオプションがあります。

### <a name="sqlpackage-and-dacfx-api-improvements"></a>SqlPackage および DacFx API の強化

SqlPackage.exe と DacFx API を使用すると、配置レポートと配置スクリプトの生成、およびデータベースへの発行を 1 回のアクションで実行できるようになりました。 これは、配置時に発行された内容のレポートを保持する場合に時間の節約になります。 もう 1 つのメリットとして、Azure のシナリオにおいて、マスター データベース用のスクリプトと配置ターゲット用のスクリプトが個別に作成されます。 これまでは 1 つのスクリプトが作成されており、配置を繰り返し行う際には役立ちませんでした。

SqlPackage の発行アクションとスクリプト アクションには、2 つの新しい引数が追加されました。

* DeployScriptPath (省略名: dsp):  これは、配置スクリプトの書き込み先のパスです (省略可能)。 Azure の配置では、DB を作成または変更するための TSQL コマンドがある場合に、マスター スクリプトが同じパスに書き込まれますが、出力ファイル名として “Filename_Master.sql” が使用されます。
* DeployReportPath (省略名: drp):  これは、配置レポートの書き込み先のパスです (省略可能)。

スクリプト アクションの場合は、既存の出力パス引数または新しいスクリプト/レポート固有の引数を使用する必要があります。ただし、両方を使用することはできません。

使用例:

**発行アクション**

```Sqlpackage.exe /a:Publish /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

**スクリプト アクション**

```Sqlpackage.exe /a:Script /tsn:(localdb)\ProjectsV13 /tdn:MyDatabase /deployscriptpath:”My\DeployScript.sql” /deployreportpath:”My\DeployReport.xml”```

DacFx では、2 つの新しい API (DacServices.Publish() および DacServices.Script()) が追加されました。 これらは、発行 + スクリプト + レポートの各アクションを 1 回の操作で実行できるようサポートします。 使用例:

```
DacServices service = new DacServices(connectionString);
using(DacPackage package = DacPackage.Load(@"C:\My\db.dacpac")) {
var options = new PublishOptions() {
    GenerateDeploymentScript = true, // Should a deployment script be created?
    GenerateDeploymentReport = true, // Should an xml deploy report be created?
    DatabaseScriptPath = @"C:\My\OutputScript.sql", // optional path to save script to
    MasterDbScriptPath = @"C:\My\OutputScript_Master.sql", // optional path to save master script to
    DeployOptions = new DacDeployOptions()
};

// Call publish and receive deployment script & report in the results
PublishResult result = service.Publish(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);

// Call script and receive deployment script & report in results
result = service.Script(package, "TargetDb", options);
Console.WriteLine(result.DatabaseScript);
Console.WriteLine(result.MasterDbScript);
Console.WriteLine(result.DeploymentReport);
```

**Analysis Services と Reporting Services**

SSAS 表形式デザイナーの DAX パーサーにおいて、大きな DAX 式を使用する際のパフォーマンスが向上しました。
詳しくは、[Analysis Services に関するブログ記事](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/)をご覧ください。

### <a name="fixed--improved-this-month"></a>今月の修正点/強化点

**データベース ツール**

* [接続のバグ 3055711](https://connect.microsoft.com/SQLServer/feedback/details/3055711/columns-cannot-be-selected-from-cross-apply-openjson-with-explicit-schema) – 明示的なスキーマを使用する CROSS APPLY OPENJSON から列を選択できません。
* 修正 – 自動生成された履歴テーブルのインデックスに関する問題。再配置の際に DacFx がインデックスを削除します。
* 修正 – DacFx のバッチ パーサーがエスケープした角かっこ (]) を解析しない問題。これにより、発行が失敗していました。
* 強化 – SqlPackage のヘルプ出力に各アクションの説明が含まれるようになりました。
* 修正 – [詳細設定] オプションの編集時、および発行、スキーマ比較、その他のファイルに保存された接続文字列の編集時に、接続ダイアログの [パスワードを記憶する] オプションが保持されていませんでした。
* 修正 – [履歴] タブに表示される接続で IntegratedAuthentication=true の場合、接続プロパティの [認証] フィールドが空白のままになっていました。 現在は、想定どおり、[Windows 認証] と表示されます。
* 修正 – [ツール] -> [オプション] -> [テキスト エディター] で、SQL Server Tools の Intellisense の設定に対する変更が保持されていませんでした。
* 強化 – [履歴] タブの接続ダイアログにある [ピン留め]/[ピン留めを外す] ボタンがコンパクトになり、スクロール バーが表示される可能性が少なくなりました。
* 修正 – 接続ダイアログのアクセシビリティに関するいくつかの問題が修正されました。

**Analysis Services と Reporting Services**

* SSDT AS のテーブル デザイナーにおいて、特定の状況でデータ グリッドのスクロール バーのつまみをクリックするとクラッシュしていた問題を修正しました。
* SSDT AS のテーブルで接続を現在のユーザーとして偽装するオプションを使用できない問題を修正しました。
* SSDT AS のテーブル デザイナーにおいて、数式バーを大きく展開しすぎると、プロジェクトを再度開けなくなる問題を修正しました。
* SSDT AS のテーブル デザイナーにおいて、テーブル タブが選択された場合にキーを押すとクラッシュが発生する問題を修正しました。
* SSDT AS のプロジェクトにおいて、[Excel で分析] から下位の AS サーバー バージョンに接続できない問題を修正しました。

**統合サービス**

* 接続のバグ [1608896](https://connect.microsoft.com/SQLServer/feedback/details/1608896/move-multiple-integration-service-package-tasks) の修正: 複数の統合サービス パッケージのタスクの移動





## <a name="ssdt-164-for-sql-server-2016"></a>SSDT 16.4 (SQL Server 2016 用)
リリース日: 2016 年 9 月 20 日

ビルド番号: 14.0.60918

**新機能**

SqlPackage.exe および Data-Tier Application Framework (DacFx) API でスキーマ比較がサポートされるようになりました。 詳しくは、「[Schema Compare in SqlPackage and the Data-Tier Application Framework](https://blogs.msdn.microsoft.com/ssdt/2016/09/20/schema-compare-in-sqlpackage-and-the-data-tier-application-framework-dacfx/)」(SqlPackage および Data-Tier Application Framework におけるスキーマ比較) をご覧ください。

**Analysis Services – SSDT テーブル (SSAS) 統合のワークスペース モード**

SSDT テーブルに内部 SSAS インスタンスが含まれるようになりました。これにより、統合ワークスペース モードが有効な場合は、SSDT テーブルがバックグラウンドで自動的に起動するため、テーブル、列、データをモデル デザイナーで追加および表示できます。外部のワークスペース サーバー インスタンスを指定する必要はありません。 統合ワークスペース モードを使用しても、SSDT テーブルがワークスペース サーバーおよびデータベースと連動するしくみは変わりません。 変わるのは、SSDT テーブルがワークスペース データベースをホストする場所です。 統合ワークスペース モードを有効にするには、新しい表形式プロジェクトの作成時に表示される [テーブル モデル デザイナー] ダイアログ ボックスの [統合ワークスペース] オプションを選択します。 明示的なワークスペース サーバーを現在使用している既存の表形式プロジェクトの場合は、[プロパティ] ウィンドウで [統合ワークスペース モード] パラメーターを True に設定して統合ワークスペース モードに切り替えることができます。このパラメーターは、ソリューション エクスプローラーで Model.bim ファイルを選択すると表示されます。 詳しくは、[Analysis Services に関するブログ記事](https://blogs.msdn.microsoft.com/analysisservices/2016/09/20/introducing-integrated-workspace-mode-for-sql-server-data-tools-for-analysis-services-tabular-projects-ssdt-tabular/)をご覧ください。

**データベース ツールの更新および修正点**
**:**

- [接続の問題 3087775](https://connect.microsoft.com/SQLServer/feedback/details/3087775): VS データ ツールの 7 月の更新 14.0.60629.0 では、テンポラル テーブルが破損していました ("値を null にすることはできません。 パラメーター名: reportedElement")。
- [接続の問題 1026648](https://connect.microsoft.com/SQLServer/feedback/details/1026648): SSDT 比較では IsPersistedNullable が異なるものとして表示されます。
- [接続の問題 2054735](https://connect.microsoft.com/SQLServer/feedback/details/2054735): BACPAC のインポート時に ID がリセットされます。
- [接続の問題 2900167](https://connect.microsoft.com/SQLServer/feedback/details/2900167): SSDT 単体テストを実行すると一時ファイルが残ります。
- [接続の問題 1807712](https://connect.microsoft.com/SQLServer/feedback/details/1807712): 下位互換性が確保されません – AppLocal と NuGet 化

**Analysis Services と Reporting Services**

* SSDT において、DirectQuery の計算列での DAX の編集時にエラーのヒントのポップアップが邪魔になる問題を修正しました。
* SSDT AS 表形式グリッドにおいて、Windows スケール ファクターが高 DPI (200% 以上) に設定されている場合に KPI アイコンがメジャー グリッドに表示されない問題を修正しました。
* SSDT AS において、大きなテーブル データを貼り付けると表形式プロジェクトが応答しなくなる問題を修正しました。
* SSDT AS のテーブル モデル エディターにおいて、接続フレンドリ名の変更時に、変更の保存が必要であるとモデルがマークされる問題を修正しました。
* SSDT AS の表形式プロジェクトにおいて、リレーションシップの管理ダイアログの列の幅を変更できない問題を修正しました。
* SSDT AS の 1200 レベルの表形式モデルにおいて、ドイツ語などのロケール設定を使用して Excel からデータを貼り付けると、コンマが小数点として正しく処理されない問題を修正しました。
* KPI アイコンが設定されている SSDT AS のプロジェクトにおいて、"このビジュアルのデータを取得できませんでした" というエラーが生成される問題を修正しました。
* 高 DPI スケールでサイズ変更する際に正しく固定される SSDT AS のプロジェクトのプロパティダイアログに関する問題を修正しました。
* SSDT AS のプロジェクトにおいて、貼り付けられたテーブルを含む特定のモデルのアップグレード中にエラーが発生する問題を修正しました。
* SSDT AS において、Excel からシート行全体を貼り付ける処理が非常に遅く、不要な多数の列が作成される問題を修正しました。
* SSDT AS において、静的な大きい DataTable式の解析と強調表示が非常に遅い、またはハングする問題を修正しました。
* SSDT AS において、エディターで選択した現在のパースペクティブにメジャーと KPI 値を追加する際の問題を修正しました。
* SSDT において、SQL Azure から AS プロジェクトへのデータのインポートで "dbo" 以外のスキーマの種類がサポートされない問題を修正しました。



## <a name="ssdt-163-for-sql-server-2016"></a>SSDT 16.3 (SQL Server 2016 用)
リリース日: 2016 年 8 月 15 日

ビルド番号: 14.0.60812.0  

**新機能**

- **リリース バージョン管理と番号付け:** 月別ではなく数値でリリースがタグ付けされるようになりました。 これは新しい SSMS ポリシーに準拠したもので、リリースや修正プログラムが 1 か月に複数ある場合の処理が簡略化されます。 このリリースは 16.3 であり、RTM リリース後の 3 回目の更新であることを意味します。 修正プログラムは 16.3.1 のように表記され、次回の更新 (来月を予定) は 16.4 になります。
- **Analysis Services – 表形式モデル エクスプローラー:** 表形式モデル エクスプローラーを使用すると、モデル内のさまざまなメタデータ オブジェクト (データ ソース、テーブル、メジャー、リレーションシップなど) 間を移動できます。 このエクスプローラーは個別のツール ウィンドウとして実装されます。Visual Studio の [表示] メニューを開いて [その他のウィンドウ] をポイントし、[表形式モデル エクスプローラー] をクリックすると表示できます。 既定では、表形式モデル エクスプローラーは個別のタブのソリューション エクスプローラー領域に表示されます。 表形式モデル エクスプローラーでは、メタデータ オブジェクトが、表形式モデル 1200 のスキーマによく似たツリー構造で表示されます。また、多数の新機能も追加されています。
- **データベース ツール – Always Encrypted**:  このリリースには、新しい [Always Encrypted キー管理](https://msdn.microsoft.com/library/mt708953.aspx)ダイアログが用意されています。これにより、データベース プロジェクトまたは SQL Server オブジェクト エクスプローラーのライブ データベースに列マスター キーまたは列暗号化キーを簡単に追加できます。 このリリースは、Windows 証明書ストアの証明書をサポートしています。 今後のリリースでは、Azure Key Vault および CNG プロバイダーがサポートされる予定です。
    - 列マスター キーまたは列暗号化キーを作成する際、[データベースの更新] のクリック直後に SQL Server オブジェクト エクスプローラーに変更が反映されない可能性があります。 この問題を回避するには、SQL Server オブジェクト エクスプローラーでデータベース ノードを更新します。
    - SQL Server オブジェクト エクスプローラーからデータを含むテーブル内の列を暗号化しようとすると、エラーが発生する可能性があります。 現在、この機能は SSDT データベース プロジェクトと SSMS でのみサポートされています。 SQL Server オブジェクト エクスプローラーのサポートは今後のリリースで有効になる予定です。


**更新と修正点**
* **データベース ツール:**
    - **SSDT:**
        - 接続のバグ 1898001 [列の説明の 128 文字制限に関する問題を修正しました](https://connect.microsoft.com/SQLServer/feedback/details/1898001/column-description-limited-to-128-characters)。
        - VS からのデータベースの発行で発行プロファイル xml の DatabaseServiceObjective プロパティが適用されない問題を修正しました。
        - 接続のバグ 2900167 [単体テストの際に一時ファイルが正しく残らない問題を修正しました](http://connect.microsoft.com/SQLServer/feedback/details/2900167/running-ssdt-unit-tests-leaves-temp-files-behind)。
        - [データベースの設定] の [保有期間] コンボ ボックスが切り捨てられる問題を修正しました。
        - パスワードの変更時に、SQL CLR プロジェクトのプロパティで空の古いパスワードの検証が行われない問題を修正しました。
    - **DACFx:**
        - DACFx 互換性レベルが SqlAzureV12 エラーのために更新されない問題を修正しました。
        - IsAutoGeneratedHistoryTable プロパティがモデルの比較から正しく除外されない問題を修正しました。

- **Analysis Services と Reporting Services**
    - **SSDT:**
        - サーバー接続が失われると表形式モデルを保存できない問題を修正しました。
        - AS の無限ループの問題が原因で SSDT が応答しなくなる問題を修正しました。
        - 式のコミット方法に基づく動作の不一致の原因となる DAX 式の問題を修正しました。
        - KPI 作成時の VS のクラッシュの問題を修正しました。
        - SQL Server 2008 R2、2012、および 2014 用の無効なレポートが生成される問題を修正しました。
        - .dwpro プロジェクトの無限ループ エラーの原因となる階層順の問題を修正しました。
        - RDL のダウングレードの際に完全なリビルドが必要になり、ユーザーの混乱を招く RS RDL の問題を修正しました。
        - [クライアント ツールに非表示] が無効になる KPI の問題を修正しました。
        

 
  
## <a name="ssdt-july-for-sql-server-2016"></a>SSDT 7 月 (SQL Server 2016 用)  
リリース日: 2016 年 6 月 30 日  
  
ビルド番号: 14.0.60629.0  
  
**新機能**  
* **Always Encrypted のサポート:** Always Encrypted の列を格納するデータベースについては、このリリースのコア API とコマンド ライン ツール (SqlPackage.exe) を通じて Always Encrypted が完全にサポートされます。 Always Encrypted のすべての機能が完全にサポートされた状態でデータベース プロジェクトをビルドして発行できます。  
* **テンポラル テーブルのサポートの強化:** テンポラル テーブルが完成したら、変更および再リンクの前にそのテーブルのリンクを解除することで処理が簡略化されます。 つまり、サポートされる操作に関して、テンポラル テーブルが他の種類のテーブル (標準、メモリ内) と同等になります。 
* **SqlPackage.exe とインストールの変更:** SSDT を SQL Server エンジンと SSMS の更新から切り離すための変更が行われました。 詳しくは、「[Changes to SSDT and SqlPackage.exe installation and updates](https://blogs.msdn.microsoft.com/ssdt/2016/06/30/changes-to-ssdt-and-sqlpackage-exe-installation-and-updates/)」(SSDT と SqlPackage.exe のインストールおよび更新の変更) をご覧ください。

 

**更新と修正点**
* **データベース ツール:**
    * 今後、SSDT がデータベースで Transparent Data Encryption (TDE) を無効にすることはありません。 これまでは、プロジェクトのデータベース設定における既定の暗号化オプションが無効であると、暗号化がオフになっていました。 この修正により、暗号化を有効にすることができ、発行中に無効になることはありません。 
    * 初期接続時の Azure SQL DB 接続の再試行の回数が増えて、回復性が向上しました。
    * 既定のファイル グループが PRIMARY でない場合は、Azure V12 へのインポート/発行が失敗していました。 現在では、発行時にこの設定が無視されるようになりました。
    * 引用符で囲まれた識別子がオンになっているオブジェクトを含むデータベースのエクスポート時に、一部のインスタンスでエクスポートの検証が失敗する問題を修正しました。
    * Hekaton テーブルの作成用の TEXTIMAGE_ON オプションが許可されていない場合に正しく追加されない問題を修正しました。
    * データ フェーズの完了後の model.xml ファイルへの書き込みによってファイルの内容の書き換えが発生するため、大量のデータを使用したエクスポートに時間がかかる問題を修正しました。
    * Azure SQL DW および APS 接続用のセキュリティ フォルダーにユーザーが表示されない問題を修正しました。


 * **Analysis Services と Reporting Services:**
    * MSOLAP OLEDB プロバイダーに関する SxS の問題を修正しました。この場合、32 ビット プロバイダーだけがインストールされて、SQL Server 2014 に接続する 64 ビットの Excel 2016 に影響を及ぼします (Office365 からの ClickOnce のインストールでは再現せず、MSI Excel のインストールでのみ発生します)。
    * 貼り付けられたテーブルを含む AS モデルを 1103 から 1200 互換性レベルにアップグレードすると、"リレーションシップで無効な列 ID が使用されています" というエラーが発生し、コーナー ケースがより強固になる問題を修正しました。
    * SSDT-BI 2013 が同じコンピューター上にある場合の SxS の問題を修正しました。この場合、SSDT 2015 のアンインストール後に AS モデル内のデータをインポートできません (カートリッジ共有のレジストリ設定)。
    * AS エンジンへの接続が失われた場合 (SSDT を一晩中開いたままにしておく、AS サーバーをリサイクルする、、または接続が一時的に失われるその他のケース) の問題/クラッシュに対処するための堅牢性が強化されました。 
    * マルチモニターを使用する場合に、VS ではなく別の画面でダイアログが開く問題を修正しました。 
    * AS モデルの貼り付けられたテーブルでの HTML テーブル (グリッド データ) からの貼り付けのサポートを修正/有効にしました。 
    * 空の貼り付けられたテーブルの 1200 へのアップグレードが失敗する (メジャー用のコンテナー テーブルとしてのみ使用されます) 問題を修正しました。 
    * 貼り付けられたテーブルを含む AS 表形式モデルの 1200 へのアップグレードに関する問題を修正しました。このアップグレードは、(1200 の貼り付けられたテーブルに使用する) 計算テーブルに関する AS エンジンの問題を回避し、アップグレード後に新しい計算テーブルでプロセスを実行するための処理です。 
    * 不完全な DAX 式を含む新しい AS 1200 モデルの計算テーブルの作成を取り消す際にクラッシュが発生する問題を修正しました。 
    * DB 名とテーブル名が同じ場合に、AS サーバーから SSDT AS プロジェクトに 1200 モデルをインポートする際の問題を修正しました。 
    * 1103 表形式モデルの KPI メジャーの編集に関する問題を修正しました。 
    * AS 1200 モデルのグリッドに KPI メジャーを貼り付ける際に、オブジェクト参照が設定されていないという例外が発生する問題を修正しました。 
    * 計算テーブル内の列を 1200 モデルのダイアグラム ビューから削除できない問題を修正しました。 
    * コード ビューで model.bim プロジェクト ファイルのプロパティを表示する際に発生するオブジェクト参照が設定されていないという例外を修正しました。 
    * 貼り付けされたテーブルを作成するために AS モデルのグリッドにデータを貼り付けると、コンマを小数点として使用する国際ロケールで正しくない値が生成される問題を修正しました。 
    * SSDT で 2008 RS プロジェクトを開き、そのプロジェクトをアップグレードしないよう選択する際の問題を修正しました。 
    * 1200 互換性レベル モデルの計算テーブルの UI において、列の種類の既定の書式設定を使用して UI から書式設定の種類の変更を許可する際の問題を修正しました。 
    

## <a name="ssdt-june-for-sql-server-2016"></a>SSDT 6 月 (SQL Server 2016 用)  
リリース日: 2016 年 6 月 1 日  
  
ビルド番号: 14.0.60525.0 

SSDT の一般提供 (GA) がリリースされました。 2016 年 6 月の SSDT GA の更新では、SQL Server 2016 RTM の最新の更新プログラムのサポートとさまざまなバグ修正が追加されました。 詳しくは、「[SQL Server Data Tools GA update for June 2016](https://blogs.msdn.microsoft.com/ssdt/2016/06/01/sql-server-data-tools-ga-update-for-june-2016/)」(2016 年 6 月の SQL Server Data Tools の GA 更新) をご覧ください。

      

## <a name="ssdt-april-for-sql-server-2016-rc3"></a>SSDT 4 月 (SQL Server 2016 RC3 用)  
リリース日: 2016 年 4 月 15 日  
  
ビルド番号: 14.0.60413.0  
  
**SQL Server データベース**  
* **Always Encrypted のサポート:** Always Encrypted の列を格納するデータベースについては、SSDT と DacFx を使用したデータベースの表示と編集、およびデータベース プロジェクトからデータベースへの発行が可能です。 列暗号化が存在する列の変更のサポートは、今後のリリースで導入される予定です。  
* **接続ダイアログと SQL Server オブジェクト エクスプローラー:** 複数の修正と強化が行われました。  
    * 接続の詳細プロパティを表示する [詳細] ページが見直され、複数行のボックスに接続文字列全体を表示し、高 DPI のコンピューターにおけるサポートを強化しました。  
    * 詳細な接続エラーを含む従来のエラー ダイアログに戻しました。 これにより、わかりやすいエラー メッセージとスタック トレースを使用してログインの問題を診断できるため、問題の診断に必要な情報を DBA または CSS で取得できます。  
    * 最小限のアクセス許可を持つユーザーについて、接続ダイアログと SQL Server オブジェクト エクスプローラーにおけるデータベースの表示やセキュリティ フォルダーの表示などに関するいくつかの問題を修正しました。  
    * データベース ノードを展開してすべての DB を表示する際の Azure SQL DB のパフォーマンスを改善しました。  
* **SSDT のインストーラー:**  
    * アンインストール時に .NET がダウンロードされる問題を修正しました。  
    * 現在は、高 DPI のコンピューターでインストーラーのサイズが正しく設定されています。  
    * 新しいバージョンの SQL Server が存在する場合に SSDT のインストールをブロックするバージョン チェックを削除しました。  
    * スキーマ比較: Visual Studio において複数の項目のチェック/チェック解除に時間がかかるパフォーマンスの問題を修正しました。  
    * x86 バージョンの SQL Server 2016 が存在しないため、x86 コンピューターでは LocalDB 2014 の使用がサポートされます。  
* **ビルドと配置:**  
    * テンポラル テーブルで計算列がサポートされない問題を修正しました。  
    * Azure V12 への配置の際には、[シングル ユーザー モードで配置スクリプトを実行する] オプションが無視されます (クラウド環境ではこのオプションがサポートされないため)。  
  
  
## <a name="ssdt-hotfix-for-sql-server-2016-rc2"></a>SSDT 修正プログラム (SQL Server 2016 RC2 用)  
リリース日: 2016 年 4 月 5 日  
  
ビルド番号: 14.0.60329.0  
  
このビルドには、SQL Server Integration Services 用の機能を提供する SSDT のバージョンの修正プログラムが含まれています。 また、ビルド 14.0.60316.0 を SQL Server 2016 の Analysis Services および Reporting Services と共に使用することもできます。   
  
この修正プログラムを取得するには、[このブログ投稿のダウンロード リンク](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/)を使用してください。  
  
レポート開発者がこのビルドの SSDT を使用して新しいレポートを作成する場合は、この修正プログラムにのみ見られる SSRS レポートにおける一時的な問題について、[既知の問題と回避策をご覧ください](https://blogs.msdn.microsoft.com/ssdt/2016/04/05/ssdt-preview-update-rc2/)。  
  
## <a name="ssdt-hotfix-for-sql-server-2016-rc0"></a>SSDT 修正プログラム (SQL Server 2016 RC0 用)  
リリース日: 2016 年 3 月 18 日  
  
ビルド番号: 14.0.60316.0  
  
このビルドには、SQL Server 2016 RC0 用の機能を提供する SSDT のバージョンの修正プログラムが含まれています。 現時点では、SSDT の RC1 バージョンはありません。 ビルド 14.0.60316.0 は、RC0 または RC1 の SQL Server 2016 と共に使用することができます。  
      
## <a name="ssdt-february-2016-preview-for-sql-server-2016-rc0"></a>SSDT 2016 年 2 月プレビュー (SQL Server 2016 RC0 用)  
リリース日: 2016 年 3 月 7 日  
  
ビルド番号: 14.0.60305.0  
  
-   **SQL Server プロジェクト テンプレート**  
  
    この SSDT プレビュー リリースに関するお知らせはありません。 このリリースのその他の機能については、「[データベース エンジンの新機能](https://msdn.microsoft.com/library/bb510411.aspx)」をご覧ください。  
  
-   **SSIS パッケージ プロジェクト テンプレート**  
  
    SSIS デザイナーは、SQL Server 2016、2014、または 2012 用のパッケージを作成および管理します。 新しいテンプレートは、パーツとして名前が変更されました。 SSIS の Hadoop コネクタは ORC 形式をサポートします。 詳しくは、「[Integration Services の新機能](https://msdn.microsoft.com/library/bb522534.aspx)」を覧ください。  
  
-   **SSAS プロジェクト テンプレート (表形式モデル プロジェクト)**  
  
    Analysis Services に対する今月の更新では、表形式モデル用の表示フォルダーのサポートを提供します。また、新しい SQL Server 2016 互換性レベルで作成されたモデルが SSIS パッケージでサポートされるようになりました。 詳しくは、 「[Analysis Services の新機能 (ブログ投稿)](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx)」をご覧ください。  
  
-   **SSRS レポート プロジェクト テンプレート**  
  
    この SSDT プレビュー リリースに関するお知らせはありません。 このリリースのその他の機能については、「[Reporting Services の新機能](https://msdn.microsoft.com/library/ms170438.aspx)」をご覧ください。  
  
## <a name="ssdt-january-2016-preview"></a>SSDT 2016 年 1 月プレビュー  
リリース日: 2016 年 2 月 4 日  
  
ビルド番号: 14.0.60203.0  
  
-   **SQL Server プロジェクト テンプレート**  
  
    この SSDT プレビュー リリースに関するお知らせはありません。 この CTP のその他の機能については、「[データベース エンジンの新機能](https://msdn.microsoft.com/library/bb510411.aspx)」をご覧ください。  
  
-   **SSIS パッケージ プロジェクト テンプレート**  
  
    ODBC 入力元と変換先コンポーネント、CDC 制御タスク、  
      CDC ソースと分割コンポーネント、Microsoft Connector for SAP BW、Integration Services Feature Pack for Azure のサポートが追加されています。 詳しくは、「[Integration Services の新機能](https://msdn.microsoft.com/library/bb522534.aspx)」を覧ください。  
  
-   **SSAS プロジェクト テンプレート**  
  
    互換性レベル 1200 の表形式モデル、DirectQuery モードのモデルの計算列と行レベルのセキュリティ、モデル メタデータの翻訳、SSIS Analysis Services DDL 実行タスクでの TMSL スクリプトの実行の機能強化に加え多くのバグ修正が含まれています。  
    詳しくは、「[Analysis Services の新機能 (msdn)](https://msdn.microsoft.com/library/bb522628.aspx)」または「[Analysis Services の新機能 (ブログ投稿)](http://blogs.msdn.com/b/analysisservices/archive/2016/01/28/what-s-new-for-sql-server-2016-analysis-services-in-ctp3-3.aspx)」をご覧ください。  
  
-   **SSRS レポート プロジェクト テンプレート**  
  
    この SSDT プレビュー リリースに関するお知らせはありません。 この CTP のその他の機能については、「[Reporting Services の新機能](https://msdn.microsoft.com/library/ms170438.aspx)」をご覧ください。  
  
## <a name="ssdt-december-2015-preview"></a>SSDT 2015 年 12 月プレビュー  
  
-   **SQL Server プロジェクト テンプレート**では以下のバグ修正が含まれています。[接続] ダイアログ ボックス。最近の履歴リスト。データベース一覧の読み込み時における接続プロパティに設定されている認証コンテキストの正しい使用。  
  
    -   テスト接続タイムアウト値を 15 秒に変更しました。  
  
    -   データベース一覧を読み込むときにクライアント IP が登録されていない場合は Azure SQL Database サーバーのファイアウォール ルールを作成します。  
  
    -   SQL Server 2016 CTP3.2 機能のプログラミング サポート。  
  
-   **SSAS プロジェクト テンプレート**では、モデル内で定義済みの DAX 式やその他のオブジェクトに基づく計算テーブルの作成がサポートされるようになりました。  
  
-   **SSIS パッケージ プロジェクト テンプレート**の追加機能には、Avro ファイル形式と Kerberos 認証用の SSIS Hadoop コネクタのサポートが含まれています。   
    SSIS 2012 と 2014 に対する SSIS デザイナーのサポートは、この更新プログラムにはまだ含まれていません。  
  
## <a name="ssdt-november-2015-preview"></a>SSDT 2015 年 11 月プレビュー  
  
-   **SQL Server プロジェクト テンプレート**:  SQL Server と Azure SQL Database の接続エクスペリエンス向上のプレビュー。  
  
-   **SSIS パッケージ プロジェクト テンプレート**:  SSIS カタログのパフォーマンス向上: SSIS 管理者以外のユーザーのための SSIS カタログ ビューのほとんどで、パフォーマンスが向上しています。  
  
-   **SSAS プロジェクト テンプレート**には、Analysis Services の表形式モデル プロジェクトの機能強化が含まれています。 **[コードの表示]** コマンドを使って JSON でのモデル定義を表示できます。 JSON エディターを使うには、フル機能エディションの Visual Studio 2015 を入手する必要があります。 [Visual Studio Community エディション](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx)を無料でダウンロードできます。  
  
## <a name="ssdt-october-2015-preview"></a>SSDT 2015 年 10 月プレビュー  
  
-   BI 用の新しいプロジェクト テンプレート (Analysis Services モデル、Reporting Services レポート、Integration Services パッケージ)。 すべての SQL Server プロジェクト テンプレートが 1 つの SSDT でそろうようになりました。  
  
-   SSIS の新機能 (Hadoop コネクタ、制御フロー テンプレート、データ フロー タスクの最大バッファー サイズの緩和など)。  
  
-   SQL Server 2016 CTP 3.0 機能をリレーショナル データベース プロジェクトに対してサポート。  
  
-   SSIS でのさまざまなバグ修正と Windows 7 OS のサポート。  
  
## <a name="ssdt-september-2015-preview"></a>SSDT 2015 年 9 月プレビュー  
  
-   複数言語サポートがこのプレビューで新たに追加されました。  
  
## <a name="ssdt-august-2015-preview"></a>SSDT 2015 年 8 月プレビュー  
  
-   SSDT をインストールするための新しいスタンドアロンの Setup.exe。  変更済みバージョンの SQL Server セットアップを使う必要はなくなりました。 このバージョンの SSDT には、SQL Server または Azure SQL Database に配置されるリレーショナル データベースを構築するためのプロジェクト テンプレートが含まれています。  
  
## <a name="see-also"></a>参照  
[SQL Server Data Tools &#40;SSDT&#41; のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)  
[以前のリリースの SQL Server Data Tools (SSDT と SSDT-BI)](../ssdt/previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md)  
[データベース エンジンの新機能](https://msdn.microsoft.com/library/bb510411.aspx)  
[Analysis Services の新機能](https://msdn.microsoft.com/library/bb522628.aspx)  
[Integration Services の新機能](https://msdn.microsoft.com/library/bb522534.aspx)  
  
