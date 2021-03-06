---
title: オブジェクトとデータ マイニング ソリューションの管理 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed8768dc456f1805b139138e8591f6f9749525eb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="management-of-data-mining-solutions-and-objects"></a>データ マイニング ソリューションおよびオブジェクトの管理
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] には、既存のマイニング構造とマイニング モデルの管理に使用できるクライアント ツールがあります。 ここでは、それぞれの環境を使用して実行できる管理操作について説明します。  
  
 これらのツールに加え、AMO や [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに接続する他のクライアント (たとえば [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 用データ マイニング アドイン) を使用することで、プログラムでデータ マイニング オブジェクトを管理できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [データ マイニング オブジェクトの移動](../../analysis-services/data-mining/moving-data-mining-objects.md)  
  
 [処理の要件および注意事項 (データ マイニング)](../../analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
 [SQL Server Profiler を使用したデータ マイニングの監視 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/using-sql-server-profiler-to-monitor-data-mining-analysis-services-data-mining.md)  
  
## <a name="location-of-data-mining-objects"></a>データ マイニング オブジェクトの場所  
 処理されたマイニング構造およびマイニング モデルは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに格納されます。  
  
 データ マイニング オブジェクトを開発するときに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] イミディエイト **モードで** データベースへの接続を作成した場合、作成したオブジェクトは即座にサーバーに追加されます。 一方、 **の既定の動作である** オフライン [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]モードでデータ マイニング オブジェクトを設計した場合、作成したマイニング オブジェクトは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに配置されるまでは単なるメタデータ コンテナーです。 そのため、オブジェクトに変更を加えた場合は、オブジェクトを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] サーバーに再配置する必要があります。 データ マイニングのアーキテクチャの詳細については、「[物理アーキテクチャ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/physical-architecture-analysis-services-data-mining.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] 2007 用データ マイニング アドインなどの一部のクライアントでは、インスタンスへの接続を使用する一方でマイニング構造およびマイニング モデルをセッション中のみサーバー上に格納する、セッション マイニング モデルおよびセッション マイニング構造を作成することもできます。 これらのモデルは、クライアントを使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに格納されている構造およびモデルの場合と同じ方法で管理できますが、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスとの接続を解除したときにオブジェクトは保持されません。  
  
## <a name="managing-data-mining-objects-in-sql-server-data-tools"></a>SQL Server データ ツールでのデータ マイニング オブジェクトの管理  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] には、データ マイニング オブジェクトの作成、参照、および編集を容易にする機能が用意されています。  
  
 次のリンクでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用してデータ マイニング オブジェクトを変更する方法について説明しています。  
  
-   [マイニング構造に使用されるデータ ソース ビューの編集します。](../../analysis-services/data-mining/edit-the-data-source-view-used-for-a-mining-structure.md)  
  
-   [マイニング構造のプロパティの変更](../../analysis-services/data-mining/change-the-properties-of-a-mining-structure.md)  
  
-   [マイニング モデルのプロパティの変更](../../analysis-services/data-mining/change-the-properties-of-a-mining-model.md)  
  
-   [モデリング フラグ (&) #40";"データ マイニング"&"#41 です。 表示または変更](../../analysis-services/data-mining/view-or-change-modeling-flags-data-mining.md)  
  
-   [アルゴリズム パラメーターの表示または変更](../../analysis-services/data-mining/view-or-change-algorithm-parameters.md)  
  
 通常は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をツールとして使用して、新しいプロジェクトの開発と既存のプロジェクトへの追加を行い、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]などのツールを使用して配置されたプロジェクトとオブジェクトを管理します。  
  
 ただし、 **イミディエイト** オプションを使用し、オンライン モードでサーバーに接続すると、ssASnoversion のインスタンスに既に配置されているオブジェクトを直接変更できます。 詳細については、「 [Analysis Services データベースへのオンライン モードでの接続](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md)」を参照してください。  
  
> [!WARNING]  
>  名前や説明などのメタデータの変更を含め、マイニング構造またはマイニング モデルに対して変更を加えた場合は、構造またはモデルを再処理する必要があります。  
  
 データ マイニング プロジェクトまたはオブジェクトの作成に使用したソリューション ファイルがない場合は、Analysis Services のインポート ウィザードを使用してサーバーから既存のプロジェクトをインポートし、オブジェクトに変更を加え、 **インクリメンタル** オプションを使用して再配置できます。 詳細については、「 [Analysis Services インポート ウィザードを使用したデータ マイニング プロジェクトのインポート](../../analysis-services/data-mining/import-a-data-mining-project-using-the-analysis-services-import-wizard.md)」を参照してください。  
  
## <a name="managing-data-mining-objects-in-sql-server-management-studio"></a>SQL Server Management Studio でのデータ マイニング オブジェクトの管理  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、マイニング構造とマイニング モデルのスクリプト処理、処理、または削除を行うことができます。 オブジェクト エクスプローラーを使用した場合はプロパティ セットの一部のみが表示されます。ただし、 **[DMX クエリ]** ウィンドウを開き、マイニング構造を選択すると、マイニング モデルに関する追加のメタデータを表示できます。  
  
-   [SQL Server Management Studio で、DMX クエリを作成します。](../../analysis-services/data-mining/create-a-dmx-query-in-sql-server-management-studio.md)  
  
## <a name="managing-data-mining-objects-programmatically"></a>データ マイニング オブジェクトのプログラムによる管理  
 次のプログラミング言語を使用すると、データ マイニング オブジェクトの作成、変更、処理、および削除の操作を行うことができます。 各言語は別々のタスクを対象として設計されています。結果として、実行できる操作の種類に制限があります。 たとえば、データ マイニング オブジェクトの一部のプロパティはデータ マイニング拡張機能 (DMX) では変更できず、XMLA または AMO を使用する必要があります。  
  
### <a name="analysis-management-objects-amo"></a>分析管理オブジェクト (AMO)  
 分析管理オブジェクト (AMO) は、データ マイニング オブジェクトを完全に制御できる、XMLA に基づいて構築されたオブジェクト モデルです。 AMO を使用して、マイニング構造とマイニング モデルを作成、配置、および監視できます。  
  
-   [AMO の概念とオブジェクト モデル](../../analysis-services/multidimensional-models/analysis-management-objects/amo-concepts-and-object-model.md)  
  
-   <xref:Microsoft.AnalysisServices>  
  
 **制限事項:** なし。  
  
### <a name="data-mining-extensions-dmx"></a>データ マイニング拡張機能 (DMX)  
 データ マイニング拡張機能 (DMX) は、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] や ADOMD.Net などの他のコマンド インターフェイスと組み合わせて、マイニング構造とマイニング モデルを作成、削除、およびクエリできます。  
  
-   [データ マイニング拡張機能 (DMX) データ定義ステートメント](../../dmx/dmx-statements-data-definition.md)  
  
 **制限事項:** DMX を使用した場合、一部のプロパティを変更できません。  
  
### <a name="xml-for-analysis-xmla"></a>XML for Analysis (XMLA)  
 XML for Analysis (XMLA) は、すべての Analysis Services 用のデータ定義言語です。 XMLA を使用して、ほとんどのデータ マイニング オブジェクトとサーバーの動作を制御できます。 XMLA を使用すると、クライアントとサーバーの間で行うすべての管理操作を実行できます。 便宜上、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) を使用して XML をラップできます。  
  
 **制限事項:** [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、内部使用の目的でのみサポートされ XMLA DDL スクリプト内では使用できない XML ステートメントを生成する場合があります。  
  
## <a name="see-also"></a>参照  
 [Analysis Services の開発者向けドキュメント](../../analysis-services/analysis-services-developer-documentation.md)  
  
  
