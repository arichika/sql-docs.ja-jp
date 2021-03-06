---
title: データ マイニング プロジェクト |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1e7a4ea87642ba31693eeea6ea17bedb14c20a24
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="data-mining-projects"></a>データ マイニング プロジェクト
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  データ マイニング プロジェクトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ソリューションの一部です。 デザイン プロセス時に、このプロジェクトで作成したオブジェクトをワークスペース データベースの一部としてテストおよびクエリに使用できます。 ユーザーがプロジェクト内のオブジェクトをクエリまたは参照できるようにするには、多次元モードで実行している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスにプロジェクトを配置する必要があります。  
  
 ここでは、データ マイニング プロジェクトを理解し、作成するために必要な基本的な情報を提供します。  
  
 [データ マイニング プロジェクトの作成](#bkmk_Overview)  
  
 [データ マイニング プロジェクト内のオブジェクト](#bkmk_Objects)  
  
-   [[データ ソース]](#bkmk_DataSources)  
  
-   [データ ソース ビュー](#bkmk_DSV)  
  
-   [マイニング構造](#bkmk_Structures)  
  
-   [[マイニング モデル]](#bkmk_Models)  
  
 [完成したデータ マイニング プロジェクトの使用](#bkmk_Complete)  
  
-   [モデルの表示および調査](#bkmk_ViewExplore)  
  
-   [モデルのテストおよび検証](#bkmk_Validate)  
  
-   [予測の作成](#bkmk_Predict)  
  
 [データ マイニング プロジェクトへのプログラムによるアクセス](#bkmk_API)  
  
##  <a name="bkmk_Overview"></a> データ マイニング プロジェクトの作成  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、" **OLAP およびデータ マイニング プロジェクト**" テンプレートを使用して、データ マイニング プロジェクトを作成します。 AMO を使用して、プログラムでデータ マイニング プロジェクトを作成することもできます。 個々のデータ マイニング オブジェクトは、Analysis Services スクリプト言語 (ASSL) を使用してスクリプト化できます。 詳細については、「[Multidimensional Model Data Access (Analysis Services - Multidimensional Data)](../../analysis-services/multidimensional-models/mdx/multidimensional-model-data-access-analysis-services-multidimensional-data.md)」(多次元モデルのデータ アクセス (Analysis Services - 多次元データ)) を参照してください。  
  
 既存のソリューション内にデータ マイニング オブジェクトを作成する場合、既定では、データ マイニング オブジェクトはソリューション ファイルと同じ名前の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに配置されます。 この名前および対象サーバーは、**[プロジェクトのプロパティ]** ダイアログ ボックスを使用して変更できます。 詳細については、「[Configure Analysis Services Project Properties (SSDT)](../../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)」(Analysis Services プロジェクトのプロパティの構成 (SSDT)) を参照してください。  
  
> [!WARNING]  
>  プロジェクトを正常に作成して配置するには、OLAP/データ マイニング モードで実行されている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスにアクセスできる必要があります。 テーブル モデルをサポートする [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスでは、データ マイニング ソリューションを開発または配置することはできません。また、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックのデータまたはメモリ内データ ストアを使用するテーブル モデルのデータを直接使用することもできません。 使用する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスがデータ マイニングをサポートできるかどうかを判断するには、「 [Determine the Server Mode of an Analysis Services Instance](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)」(Analysis Services インスタンスのサーバー モードの決定) を参照してください。  
  
 作成する各データ マイニング プロジェクト内で、次の手順を実行します。  
  
1.  キューブ、データベース、Excel ファイル、テキスト ファイルなど、モデルの作成に使用する生データが含まれている *データ ソース*を選択します。  
  
2.  分析に使用するデータ ソース内のデータのサブセットを定義し、それを *データ ソース ビュー*として保存します。  
  
3.  モデリングをサポートするように *マイニング構造* を定義します。  
  
4.  *アルゴリズム* を選択し、そのアルゴリズムによるデータの処理方法を指定して、 *マイニング モデル* をマイニング構造に追加します。  
  
5.  選択したデータまたはフィルター選択されたデータのサブセットをモデルに設定して、モデルをトレーニングします。  
  
6.  モデルを調査、テスト、および再構築します。  
  
 プロジェクトが完成したら、そのプロジェクトをユーザーが参照またはクエリできるように配置したり、アプリケーションのプログラムからマイニング モデルにアクセスできるようにしたりして、予測や分析をサポートすることができます。  
  
  
##  <a name="bkmk_Objects"></a> データ マイニング プロジェクト内のオブジェクト  
 すべてのデータ マイニング プロジェクトには、次の 4 種類のオブジェクトが含まれます。 どの種類のオブジェクトも複数含めることができます。  
  
-   [データ ソース]  
  
-   データ ソース ビュー  
  
-   マイニング構造  
  
-   [マイニング モデル]  
  
 たとえば、1 つのデータ マイニング プロジェクトに、それぞれが複数のデータ ソース ビューをサポートしている複数のデータ ソースへの参照を含めることができます。 さらに、各データ ソース ビューは、それぞれが多数のマイニング モデルに関連付けられている複数のマイニング構造をサポートできます。  
  
 また、プロジェクトには、プラグイン アルゴリズム、カスタム アセンブリ、またはカスタム ストアド プロシージャを含めることもできます。ただし、ここでは、これらのオブジェクトについて説明しません。 詳細については、「 [開発者ガイド (Analysis Services)](../../analysis-services/analysis-services-developer-documentation.md)」を参照してください。  
  
  
###  <a name="bkmk_DataSources"></a> Data Sources  
 データ ソースでは、データ ソースへの接続に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーで使用する接続文字列および認証情報を定義します。 データ ソースには、複数のテーブルまたはビューを含めることができます。また、1 つの Excel ブックやテキスト ファイルのように単純なものや、オンライン分析処理 (OLAP) データベースや大規模なリレーショナル データベースのように複雑なものを指定することもできます。  
  
 1 つのデータ マイニング プロジェクトで、複数のデータ ソースを参照できます。 マイニング モデルで一度に使用できるデータ ソースは 1 つだけですが、異なるデータ ソースを利用する複数のモデルをプロジェクトに含めることができます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではさまざまな外部プロバイダーのデータをサポートしており、SQL Server データ マイニングではデータ ソースとしてリレーショナル データとキューブ データの両方を使用できます。 ただし、両方の種類のプロジェクト (リレーショナル ソースに基づくモデルと OLAP キューブに基づくモデル) を開発する場合は、それらを別々のプロジェクトで開発して管理できます。  
  
-   通常、OLAP キューブに基づくモデルは、OLAP デザイン ソリューション内で開発する必要があります。 その理由の 1 つとして、キューブに基づくモデルでは、データを更新するためにキューブを処理する必要があることが挙げられます。 一般に、キューブ データを使用する必要があるのは、それがデータを保存およびアクセスするための主な手段である場合、または多次元プロジェクトで作成された集計、ディメンション、および属性が必要な場合だけです。  
  
-   プロジェクトでリレーショナル データのみを使用する場合は、その他のオブジェクトを不必要に再処理しないように、独立したプロジェクト内でリレーショナル モデルを作成する必要があります。 多くの場合、キューブの作成をサポートするために使用されるステージング データベースまたはデータ ウェアハウスには、データ マイニングの実行に必要なビューが既に含まれています。そのため、キューブ内の集計やディメンションではなく、それらのビューを使用して、データ マイニングを実行できます。  
  
-   メモリ内データまたは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データを直接使用して、データ マイニング モデルを作成することはできません。  
  
 データ ソースでは、サーバーまたはプロバイダーと、一般的な種類のデータのみが識別されます。 データの書式および集計を変更する必要がある場合は、データ ソース ビュー オブジェクトを使用します。  
  
 データ ソースのデータの処理方法を制御するには、派生列または計算の追加、集計の変更、またはデータ ソース ビュー内のデータの列名の変更を行います (また、マイニング構造列を変更するか、マイニング モデル列のレベルでモデリング フラグおよびフィルターを使用することで、下流のデータを操作することもできます)。  
  
 データ クレンジングが必要な場合、またはデータ ウェアハウス内のデータを変更して、追加の変数の作成、データの種類の変更、または代替の集計の作成を行う必要がある場合は、データ マイニングをサポートする追加のプロジェクトの種類を作成する必要があります。 これらの関連するプロジェクトの詳細については、「 [Related Projects for Data Mining Solutions](../../analysis-services/data-mining/related-projects-for-data-mining-solutions.md)」(データ マイニング ソリューションの関連プロジェクト) を参照してください。  
  
  
###  <a name="bkmk_DSV"></a> Data Source Views  
 データ ソースへの接続を定義した後、モデルに関連する特定のデータを確認するビューを作成します。  
  
 データ ソース ビューでは、データ ソース内のデータをマイニング モデルに入力する方法をカスタマイズすることもできます。 プロジェクトとの関連性をより高めるためにデータの構造を変更したり、特定の種類のデータのみを選択したりできます。  
  
 たとえば、データ ソース ビュー エディターを使用して、次のことができます。  
  
-   日付要素、サブストリングなどの派生列を作成する  
  
-   GROUP BY などの [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用して値を集計する  
  
-   データを一時的に制限する、またはデータをサンプリングする  
  
 データ ソース ビュー内のデータを変更する方法については、「 [多次元モデルのデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)」を参照してください。  
  
> [!WARNING]  
>  データのフィルター選択はデータ ソース ビューで行うことができますが、マイニング モデルのレベルでデータに対するフィルターを作成することもできます。 フィルターの定義はマイニング モデルと共に格納されるため、モデル フィルターを使用すると、モデルのトレーニングに使用したデータを簡単に特定できます。 また、さまざまなフィルター条件を使用して、複数の関連モデルを作成することもできます。 詳細については、「[マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)」を参照してください。  
  
 作成したデータ ソース ビューには、分析に直接使用されない追加のデータを含めることができます。 たとえば、テスト、予測、またはドリルスルーに使用するデータをデータ ソース ビューに追加できます。 これらの使用方法の詳細については、「[テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)」と「[ドリルスルー](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)」を参照してください。  
  
  
###  <a name="bkmk_Structures"></a> Mining Structures  
 データ ソースとデータ ソース ビューを作成したら、プロジェクト内に *マイニング構造* を定義して、ビジネス上の問題に最も関連するデータの列を選択する必要があります。 マイニング構造によって、モデリング、トレーニング、およびテストに実際に使用するデータ ソース ビューのデータの列をプロジェクトに指示します。  
  
 新しいマイニング構造を追加するには、データ マイニング ウィザードを起動します。 ウィザードでは、自動的にマイニング構造が定義されます。手順に従ってデータを選択しますが、必要に応じて初期マイニング モデルを構造に追加することもできます。 マイニング構造内で、データ ソース ビューまたは OLAP キューブのテーブルおよび列を選択し、データに入れ子になったテーブルが含まれている場合は、テーブル間のリレーションシップを定義します。  
  
 データ マイニング ウィザードでは、リレーショナル データ ソースを使用するか、オンライン分析処理 (OLAP) データ ソースを使用するかによって、データの選択は大きく異なります。  
  
-   リレーショナル データ ソースからデータを選択する場合、マイニング構造の設定は簡単です。データ ソース ビューのデータから列を選択し、別名などの追加のカスタマイズを設定したり、列内の値をグループ化またはビン分割する方法を定義したりします。 詳細については、「 [Create a Relational Mining Structure](../../analysis-services/data-mining/create-a-relational-mining-structure.md)」(リレーショナル マイニング構造の作成) を参照してください。  
  
-   OLAP キューブのデータを使用する場合、マイニング構造は OLAP ソリューションと同じデータベース内に存在する必要があります。  マイニング構造を作成するには、OLAP ソリューションのディメンションと関連するメジャーから属性を選択します。 通常、数値はメジャーにあり、カテゴリ変数はディメンションにあります。 詳細については、「 [Create an OLAP Mining Structure](../../analysis-services/data-mining/create-an-olap-mining-structure.md)」(OLAP マイニング構造の作成) を参照してください。  
  
-   DMX を使用して、マイニング構造を定義することもできます。 詳細については、「[データ マイニング拡張機能 (DMX) データ定義ステートメント](../../dmx/dmx-statements-data-definition.md)」を参照してください。  
  
 初期のマイニング構造を作成した後、構造列のコピー、変更、および別名の指定を行うことができます。  
  
 各マイニング構造には、複数のマイニング モデルを含めることができます。 そのため、マイニング構造を作成後に再度開き、 [Data Mining Designer](../../analysis-services/data-mining/data-mining-designer.md) を使用して、マイニング モデルをマイニング構造に追加できます。  
  
 また、モデルの作成に使用するトレーニング データセットと、マイニング モデルのテストまたは検証に使用する予約データセットにデータを分割することもできます。  
  
> [!WARNING]  
>  タイム シリーズ モデルなど、一部のモデルの種類では、トレーニング用に連続する一連のデータが必要なため、予約データセットの作成はサポートされていません。 詳しくは、「 [Training and Testing Data Sets](../../analysis-services/data-mining/training-and-testing-data-sets.md)」をご覧ください。  
  
  
###  <a name="bkmk_Models"></a> Mining Models  
 マイニング モデルでは、アルゴリズム、つまりデータに対して使用する分析の方法を定義します。 それぞれのマイニング構造に、1 つ以上のマイニング モデルを追加します。  
  
 必要に応じて、複数のモデルを 1 つのプロジェクトにまとめることや、モデルや分析タスクの種類ごとに別々のプロジェクトを作成することができます。  
  
 構造とモデルを作成したら、データの数学的モデルを生成するアルゴリズムを使用して、データ ソース ビューのデータを実行することで各モデルを *処理* します。 このプロセスは、*モデルのトレーニング*とも呼ばれます。 詳細については、「[処理の要件および注意事項 (データ マイニング)](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)」を参照してください。  
  
 モデルを処理した後、マイニング モデルの視覚的な調査およびマイニング モデルに対する予測クエリの作成を行うことができます。 トレーニング処理のデータがキャッシュされていると、 *ドリルスルー* クエリによって、モデルで使用されたケースに関する詳細情報を返すことができます。  
  
 モデルを実稼働環境で (予測の作成、一般のユーザーによる調査などに) 使用する場合、モデルを別のサーバーに配置できます。 後でモデルを再処理する必要がある場合は、基になるマイニング構造の定義 (必要な場合は、さらにデータ ソースとデータ ソース ビューの定義) を同時にエクスポートする必要もあります。  
  
 モデルを配置する場合は、構造およびモデルに適切な処理オプションが設定されていること、およびクエリの実行、モデルの表示、および構造またはモデル データへのドリルスルーに必要な権限が潜在的なユーザーに与えられていることも確認する必要があります。 詳細については、「[Security Overview (Data Mining)](../../analysis-services/data-mining/security-overview-data-mining.md)」(セキュリティの概要 (データ マイニング)) を参照してください。  
  
  
##  <a name="bkmk_Complete"></a> 完成したデータ マイニング プロジェクトの使用  
 ここでは、完成したデータ マイニング プロジェクトを使用する方法について説明します。 精度チャートを作成し、データを調査および検証し、データ マイニング パターンをユーザーが使用できるようにすることができます。  
  
> [!WARNING]  
>  データ マイニング モデルで使用するチャート、クエリ、および視覚エフェクトは、データ マイニング プロジェクトの一部として保存されず、配置することもできません。 これらのオブジェクトを保持する必要がある場合は、表示される内容を保存するか、各オブジェクトの説明に従ってスクリプト化する必要があります。  
  
  
###  <a name="bkmk_ViewExplore"></a> View and Explore Models  
 モデルを作成した後、ビジュアル ツールおよびクエリを使用して、モデル内のパターンを調査し、基になるパターンと統計値を詳細に分析することができます。 データ マイニング デザイナーの **[マイニング モデル ビューアー]** タブでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されているマイニング モデルの種類ごとのビューアーを使用して、マイニング モデルを調べることができます。  
  
 これらの視覚エフェクトは一時的なもので、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]とのセッションを終了すると、保存されずに閉じられます。 そのため、プレゼンテーションや追加の分析のために、これらの視覚エフェクトを別のアプリケーションにエクスポートする必要がある場合は、ビューアー インターフェイスの各タブまたはペインに用意されている **[コピー]** を使用します。  
  
 また、Excel 用データ マイニング アドインでは、Visio テンプレートが提供されます。それを使用して、Visio の図でモデルを表現し、Visio のツールを使用して図に注釈を付けたり、変更したりできます。 詳細については、「 [Microsoft Office 2007 用 Microsoft SQL Server 2008 データ マイニング アドイン](http://go.microsoft.com/fwlink/?LinkID=123146)」を参照してください。  
  
  
###  <a name="bkmk_Validate"></a> Test and Validate Models  
 モデルを作成した後、結果を調査して、最もパフォーマンスの良いモデルを決定できます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、さまざまなチャートが用意されています。それらを使用して、マイニング モデルを直接比較したり、最も正確または有用なマイニング モデルを選択したりできるツールを提供できます。 これらのツールには、リフト チャート、利益チャート、および分類マトリックスが含まれます。 データ マイニング デザイナーの **[マイニング精度チャート]** タブ使ってこれらのグラフを生成できます。  
  
 相互検証レポートを使用して、データの反復サブサンプリングを実行することで、モデルが特定のデータに偏っていないかどうかを判断することもできます。 このレポートで提供される統計情報を使用すると、モデルを客観的に比較したり、トレーニング データの質を評価したりできます。  
  
 これらのレポートおよびチャートは、プロジェクトまたは ssASnoversion データベースに保存されません。そのため、その結果を保持または複製する必要がある場合は、結果を保存するか、DMX または AMO を使用してオブジェクトをスクリプト化する必要があります。 クロス検証にストアド プロシージャを使用することもできます。  
  
 詳細については、「[テストおよび検証 (データ マイニング)](../../analysis-services/data-mining/testing-and-validation-data-mining.md)」を参照してください。  
  
  
###  <a name="bkmk_Predict"></a> Create Predictions  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、予測を作成するための基礎であり、簡単にスクリプト化できるデータ マイニング拡張機能 (DMX) と呼ばれるクエリ言語が用意されています。 DMX 予測クエリの作成を支援するために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で使用できるクエリ ビルダーが用意されています。 また、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のクエリ エディター用の DMX テンプレートも多数あります。予測クエリを初めて作成する場合は、データ マイニング デザイナーと [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の両方に用意されているクエリ ビルダーを使用することをお勧めします。 詳しくは、「 [Data Mining Tools](../../analysis-services/data-mining/data-mining-tools.md)」をご覧ください。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で作成した予測は保存されません。そのため、クエリが複雑な場合、または結果を再現する必要がある場合は、予測クエリを DMX クエリ ファイルに保存するか、スクリプト化するか、Integration Services パッケージの一部としてそのクエリを埋め込むことをお勧めします。  
  
  
##  <a name="bkmk_API"></a> データ マイニング オブジェクトへのプログラムによるアクセス  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データ マイニング プロジェクトおよびその中のオブジェクトをプログラムで操作に使用できるいくつかのツールを提供します。 DMX 言語に用意されているステートメントを使用して、データ ソースおよびデータ ソース ビューを作成することや、データ マイニング構造およびモデルを作成、トレーニング、および使用することができます。 詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
 また、これらの作業は、Analysis Services スクリプト言語 (ASSL) または分析管理オブジェクト (AMO) を使用して実行することもできます。 詳細については、「 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)」を参照してください。  
  
  
## <a name="related-tasks"></a>関連タスク  
 次のトピックでは、データ マイニング ウィザードを使用して、データ マイニング プロジェクトおよび関連するオブジェクトを作成する方法について説明しています。  
  
|処理手順|トピック|  
|-----------|------------|  
|マイニング構造列を操作する方法について説明します。|[リレーショナル マイニング構造を作成します。](../../analysis-services/data-mining/create-a-relational-mining-structure.md)|  
|新しいマイニング モデルを追加し、構造とモデルを処理する方法について詳しく説明します。|[マイニング モデル構造体 & #40; を追加します。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md)|  
|マイニング モデルを作成するアルゴリズムのカスタマイズに役立つリソースへのリンクを提供します。|[マイニング モデルおよび構造体をカスタマイズします。](../../analysis-services/data-mining/customize-mining-models-and-structure.md)|  
|各マイニング モデル ビューアーに関する情報へのリンクを提供します。|[データ マイニング モデル ビューアー](../../analysis-services/data-mining/data-mining-model-viewers.md)|  
|リフト チャート、利益チャート、または分類マトリックスを作成する方法、またはマイニング構造をテストする方法について説明します。|[テストおよび検証 &#40;データ マイニング&#41;](../../analysis-services/data-mining/testing-and-validation-data-mining.md)|  
|処理オプションと権限について説明します。|[データ マイニング オブジェクトの処理](../../analysis-services/data-mining/processing-data-mining-objects.md)|  
|Analysis Services について詳しく説明します。|[多次元モデル データベース ](../../analysis-services/multidimensional-models/multidimensional-model-databases-ssas.md)|  
  
## <a name="see-also"></a>参照  
 [データ マイニング デザイナー](../../analysis-services/data-mining/data-mining-designer.md)   
 [SQL Server Data Tools & #40; を使用して多次元モデルを作成します。SSDT & #41;](../../analysis-services/multidimensional-models/creating-multidimensional-models-using-sql-server-data-tools-ssdt.md)   
 [ワークスペース データベース](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)  
  
  
