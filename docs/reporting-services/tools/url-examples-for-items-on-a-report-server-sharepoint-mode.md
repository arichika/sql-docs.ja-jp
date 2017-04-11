---
title: "SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54cb861a-8cec-445c-875d-599fb9bd1973
caps.latest.revision: 5
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 5
---
# SharePoint モードのレポート サーバー上のパブリッシュされたレポート アイテムの URL の例 (SSRS)
  レポートおよび関連アイテムを SharePoint ライブラリにパブリッシュするには、レポート デザイナーなどの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 作成ツールを使用してコンテンツをパブリッシュするか、SharePoint サイトのアクションを使用してコンテンツをアップロードします。  
  
 SharePoint サイトでは、ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーとは異なる Web アドレスが使用されます。 SharePoint サイトの Web 階層には、SharePoint Web アプリケーション、トップレベル サイト、オプションのサブサイト、およびライブラリが含まれています。 レポートまたは関連アイテムのパブリッシュ先となる、SharePoint サーバーおよび SharePoint サイト階層内の位置を指定する URL アドレスの作成方法を知っておく必要があります。   
  
 レポートに関連するアイテムには、共有データ ソース、サブレポート、詳細レポート、およびリソース (Web ベースのイメージ ファイルなど) が含まれます。 SharePoint ライブラリにパブリッシュされたレポートは、SharePoint ライブラリ内の場所でこれらの関連アイテムを指定する必要があります。  
  
 このトピックの例は、レポート ソリューション内のレポートおよび関連アイテムの URL を作成するのに役立ちます。  
  
## サイト階層  
 レポート サーバーが SharePoint 統合モードで実行されるように構成する場合、レポート サーバーで処理および管理されるアイテムの場所の指定には、SharePoint の Web 階層を使用します。  
  
 レポート サーバー コンテンツへのアクセスおよびセキュリティ保護には、次に示す Web 階層の要素を使用します。 リストやページなどのオブジェクトは、レポート サーバーのコンテンツへのアクセスに使用されないため、この表では説明しません。  
  
|オブジェクト|Description|  
|------------|-----------------|  
|SharePoint Web アプリケーション|SharePoint Web アプリケーションは、スタンドアロン サーバーとしてインストールするか、一連の仮想サーバーを含むファームの下にインストールできます。 Web アプリケーションには http:*//servername* などの URL を指定します。複数のサイトを指定することもできます。|  
|Site|サイトは、Web アプリケーションの親サイトまたはサブサイトになります。|  
|SharePoint ライブラリ|ライブラリには、ドキュメントやフォルダーが格納されます。 レポート、レポート モデル、共有データ ソース、および外部画像を保存できるサイト オブジェクトは、ライブラリまたはライブラリ内のフォルダーのみです。|  
|アイテム|URL 内で参照できるレポート サーバーのアイテムとしては、レポートまたはサブレポートのレポート定義、レポート モデル、共有データ ソース、外部画像などがあります。|  
  
## URL の構文と規則  
 ライブラリ内の各レポート サーバー アイテムを識別するには、完全修飾 URL を使用します。完全修飾 URL は、プロトコルを表すプレフィックス、サーバー名、サイト、ライブラリ、ファイル名、ファイルの種類を示すファイル名拡張子で構成されます。  
  
### SharePoint サーバーの URL  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] からレポート サーバーに、レポート サーバー プロジェクトまたはレポート モデル プロジェクトを配置する場合は、SharePoint サーバーの URL を使用する必要があります。  
  
 使用するサーバーの名前を見つけるには、ブラウザーを開いて、レポートのパブリッシュ先として使用する SharePoint ライブラリを探します。 プロトコル プレフィックスのすぐ後に、http:*//servername* のような形式のサーバー名が表示されます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] URL プロキシ エンドポイントの使用はサポートされていません。 プロキシ エンドポイントには、http:*//servername:8080/reportserver* のようにポート番号が含まれます。  
  
### SharePoint Server サイトまたはサブサイトの URL  
 レポートまたはレポート データ ソースを配置する場合は、SharePoint サイトおよびサブサイト (ある場合) の URL を使用する必要があります。 URL ではサーバー名のすぐ後にサイト名が示されます。たとえば、http://*servername/site* または http://*servername/site/subsite* のようになります。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] Web アプリケーションでは、サイトおよびサブサイトは一般的にメイン サイトのタブに対応します。 サイト名またはサブサイト名を見つけるには、**[ホーム]** をクリックし、次に **[すべてのサイト コンテンツの表示]** をクリックします。 末尾までスクロールして **[サイトとワークスペース]** を選択します。 このセクションにサイトの一覧が表示されます。  
  
### SharePoint ライブラリの URL  
 レポートまたは関連アイテムを SharePoint ライブラリに配置する場合は、SharePoint ライブラリの URL を使用する必要があります。 ライブラリに使用する URL は、使用している SharePoint のバージョンによって異なります。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] 3.0 または [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] では、ライブラリはサーバー名の後に示されます。たとえば、http://*servername/*Shared Documents のようになります。  
  
 [!INCLUDE[offSPServ](../../includes/offspserv-md.md)] 2007 または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] では、ライブラリはサイトおよびサブサイトの後に示されます。 たとえば、http://*servername/site/*Documents のようになります。  
  
 新しい SharePoint ライブラリまたは使用したことがないサイトのパス情報を見つけるには、ブラウザーを開き、レポートのパブリッシュ先として使用する SharePoint ライブラリを探します。 ライブラリが空である場合は、任意のファイルをアップロードします。 ファイルを右クリックして **[プロパティ]** をクリックし、**[プロパティ]** ウィンドウを開きます。 ファイルのアドレスには、パブリッシュ操作に必要な URL 値が含まれています。  
  
### SharePoint サイトのアイテムに使用する完全修飾 URL  
 SharePoint ライブラリに保存されているアイテムの場所は、必ず完全修飾 URL で指定します。先頭にはルート ノードとして Web アプリケーションを指定し (http://*server* など)、参照するファイルの名前を最後に指定します。  
  
 URL 内に指定するファイル名にはファイル名拡張子が必要です。  
  
 SharePoint サイトにパブリッシュするレポート内の依存アイテムには、相対 URL は使用できません。 たとえば相対 URL で共有データ ソース、レポート モデル、またはサブレポートを参照することはできません。 各アイテムには常に、SharePoint ライブラリへの完全修飾 URL を指定する必要があります。 サイトには、URL 形式の解析に使用できるような事前定義された階層はないため、依存ファイルの場所を予測することはできません。  
  
 依存アイテムが含まれているレポートをパブリッシュまたはアップロードする場合は、レポートをパブリッシュした後で依存アイテムへの参照を設定する必要があります。 参照がレポート デザイナーのプレビュー モードで正しく機能しても、レポートをパブリッシュした後に正しく機能するとは限りません。 詳細については、このトピックの「[作成ツールから SharePoint ライブラリへのパブリッシュ](#publishingToDocLib)」を参照してください。  
  
### 外部画像の URL  
 レポート定義には、外部ファイルとして保存されている画像ファイルを含めることができます。 レポート定義内に画像ファイルの参照情報として、ファイルへの完全修飾 URL を設定します。 画像ファイルは、SharePoint サイトまたはリモート コンピューターに保存できます。  
  
> [!IMPORTANT]  
>  外部 URL が SharePoint サイト上の画像を指している場合、レポート ビルダーでレポートをプレビューすると壊れた画像アイコンが表示されます。 "**アイテムの表示**" 権限のみが与えられている場合に SharePoint サイトにレポートをアップロードし、接続モードでレポートを表示すると、壊れた画像アイコンが表示されます。  
  
 レポート内の外部画像ファイルへの参照は、レポート サーバーのモードに関係なく、完全修飾 URL にする必要があります。 また、外部画像ファイルを参照する場合、通常は自動レポート処理アカウントを構成する必要があります。  
  
### サブレポートと詳細レポートの指定  
 サブレポートは、メイン レポートと同じフォルダーに存在している必要があります。 相対フォルダーを指定することはできません。  
  
 詳細レポートを指定するには、式に URL を含めます。 たとえば、SalesDetails という名前のレポートを詳細レポートとして指定するには、テキスト ボックスまたはプレースホルダー テキストのアクションで、ReportName を次の式に設定します。  
  
```  
="http://site/subsite/documentlibrary/SalesDetails.rdl"  
```  
  
### SharePoint サイトの予約名  
 SharePoint サイト上のアイテムの URL を作成する場合、**Personal** および **Sites** という語はどちらも既定サイト内の予約名であることに注意してください。  
  
## URL の例  
 アイテムを SharePoint ライブラリにパブリッシュする場合は、完全修飾 URL をターゲット ライブラリに指定する必要があります。 完全修飾 SharePoint URL は、SharePoint Web アプリケーション、サイト、ライブラリ、フォルダー、ファイル、およびファイル名拡張子で構成されます。フォルダーは省略可能です。 使用可能な構文の例をいくつか次に示します。  
  
|移行先|URL の例|  
|------------|-----------------|  
|SharePoint サーバー|http://TestServer|  
|SharePoint サーバー サイトまたはサブサイト|http://TestServer/toplevelsite/subsite|  
|[!INCLUDE[winSPServ](../../includes/winspserv-md.md)] または [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 配置上の **Shared Documents** 内の Company Sales サンプル レポート。|http://TestServer/TestSite/Shared%20Documents/Company%20Sales.rdl|  
|[!INCLUDE[offSPServ](../../includes/offspserv-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] インスタンス上の **Documents/Doc** フォルダー内の Company Sales サンプル レポート。|http://TestServer/TestSite/Documents/Doc/Company%20Sales.rdl|  
|[!INCLUDE[offSPServ](../../includes/offspserv-md.md)] または [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] インスタンス上の **Report Center** 内の Company Sales サンプル レポート。|http://TestServer/TestSite/Reports/Doc/Company%20Sales.rdl|  
  
##  <a name="publishingToDocLib"></a> 作成ツールから SharePoint ライブラリへのパブリッシュ  
 レポート作成ツールを使用してレポートと関連ファイルをライブラリにパブリッシュする場合、ファイルは検証されてから追加されます。 SharePoint ライブラリで **[アップロード]** アクションを使用してレポートと関連ファイルをアップロードする場合、検証チェックは行われません。 ファイルが有効かどうかは、管理、編集、または実行のためにレポートにアクセスするまで知ることができません。  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] から SharePoint サイトにレポートをパブリッシュするとき、場合によっては、Internet Explorer ブラウザーの信頼できる場所のリストに SharePoint サイトを追加する必要があります。  
  
### 共有データ ソース  
 共有データ ソースをレポート作成ツールからパブリッシュする場合は、プロジェクト プロパティ **TargetDataSourceFolder** を設定します。 ターゲット データ ソース フォルダーは、SharePoint ライブラリへの URL である必要があります。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードの場合と異なり、相対パスは有効ではなく、相対フォルダーは指定できません。 ドキュメント ライブラリ パス内のフォルダーが存在しない場合は、フォルダーが作成されます。  
  
 共有データ ソース (.rds) ファイルを SharePoint サイトにパブリッシュすると、データ ソース ファイル名拡張子が .rsds に変更されます。 .rsds ファイルは SharePoint サイトからローカルに保存することも、既存の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] プロジェクトにインポートすることもできません。 ファイル名拡張子 .rds の共有データ ソースと .rsds の共有データ ソースを入れ替えることはできません。  
  
#### 共有データ ソース (レポート デザイナーから)  
 レポート デザイナー プロジェクトから共有データ ソースをパブリッシュする場合は、ターゲット ライブラリを指定する URL を使用するか、プロパティを空白のままにすることができます。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モードの場合と異なり、相対パスは有効ではなく、相対フォルダーは指定できません。 ドキュメント ライブラリ パス内のフォルダーが存在しない場合は、フォルダーが作成されます。 ターゲット データ ソース フォルダーを空のままにした場合、データ ソースはターゲット レポート フォルダーにパブリッシュされます。  
  
### ファイル名  
 レポート アイテムに対して URL 内に指定するファイル名にはファイル名拡張子が必要です。 ファイル名拡張子によってファイルの種類が識別されます。 レポート アイテムをレポート作成ツールからパブリッシュする場合は、ファイル名拡張子が自動的に含まれます。 レポート アイテムを SharePoint ライブラリにアップロードする場合は、ファイル名拡張子を含める必要があります。  
  
 SharePoint サイトにアップロードするアイテムにファイル名拡張子を指定しないと、**rsInvalidDataSourceReference** エラーが発生します。 SharePoint アプリケーションで有効なファイル名文字として認識されない文字を、ファイル名に含めることはできません。 # % & * : \< > ?  / { | } は、使わないでください。  
  
## アップロードとパブリッシュの相違点  
 レポート デザイナーまたはレポート ビルダーを使用してレポートと関連ファイルをライブラリにパブリッシュする場合、ファイルは検証されてから追加されます。 SharePoint ライブラリで **[アップロード]** アクションを使用してレポートと関連ファイルをアップロードする場合、検証チェックは行われません。 ファイルが有効かどうかは、管理、編集、または実行のためにレポートにアクセスするまで知ることができません。  
  
## パブリッシュされたアイテムの更新  
 SharePoint ライブラリにアイテムをパブリッシュまたはアップロードした後、アイテムを更新するときは、まずアイテムをライブラリからチェックアウトする必要があります。 レポートがチェックアウトされている間、他のユーザーはこのレポートを変更できなくなります。 変更が終わったら、レポートを再びチェックインします。  
  
 最初にドキュメントをチェックアウトせずにレポートをアップロードまたはパブリッシュした場合 (既存のアイテムと同じ名前のアイテムをアップロードした場合など) は、レポート サーバーで自動的にアイテムがチェックアウトされ、既存アイテムの新しいバージョンとして更新後のレポートが追加された後、ドキュメントが再びチェックインされます。  
  
## リソースとしての外部画像  
 ネイティブ モードで実行しているレポート サーバーでは、リソースという概念がサポートされます。リソースとは、レポート サーバー上に保存されてセキュリティで保護されていても、レポート サーバーによる処理は行われないファイルのことです。 ネイティブ モードでは、どのような種類のファイルもリソースになります。  
  
 SharePoint 統合モードで実行しているレポート サーバーでは、リソースの概念は狭義になります。 この場合、レポート サーバーのリソースとは、外部画像を参照するレポートの保存場所を指します。 レポートが内部用のスナップショットまたはコピーとして保持されている場合がこれに該当します。  
  
## 参照  
 [SharePoint ライブラリへのレポートのパブリッシュ](../../reporting-services/reports/publish-a-report-to-a-sharepoint-library.md)   
 [SharePoint ライブラリへの共有データ ソースのパブリッシュ](../../reporting-services/reports/publish-a-shared-data-source-to-a-sharepoint-library.md)   
 [[プロパティ ページ] ダイアログ ボックス](../Topic/Project%20Property%20Pages%20Dialog%20Box.md)  
  
  