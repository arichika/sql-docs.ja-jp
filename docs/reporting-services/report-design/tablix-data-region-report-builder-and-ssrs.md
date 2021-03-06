---
title: Tablix データ領域 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 99f83b32-4b86-4d40-973c-9a328d23ac8b
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d5360091fbf0ece381b8b7444fdd8e225238563
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tablix-data-region-report-builder-and-ssrs"></a>Tablix データ領域 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]の Tablix データ領域は、行と列で構成されたセルにページ分割されたレポート データを表示する、汎用のレイアウト レポート アイテムです。 レポート データには、データ ソースから取得される詳細データや、指定したグループに分類される集計詳細データなどがあります。 各 Tablix セルには、テキスト ボックスや画像、Tablix 領域などの他のデータ領域、グラフ、ゲージなど、任意のレポート アイテムを含めることができます。 複数のレポート アイテムをセルに追加するには、まず、コンテナーとして機能する四角形を追加します。 次に、四角形にレポート アイテムを追加します。  
  
 テーブル、マトリックス、一覧などのデータ領域は、基になる Tablix データ領域のテンプレートによってリボン上に表されます。 これらのテンプレートのいずれかをレポートに追加すると、実際には、特定のデータ レイアウトに最適化された Tablix データ領域が追加されます。 既定では、テーブル テンプレートはグリッド レイアウトに詳細データを表示し、マトリックスはグリッド レイアウトにグループ データを表示し、一覧は自由な形式のレイアウトに詳細データを表示します。  
  
 テーブルまたはマトリックスの各 Tablix セルには、既定でテキスト ボックスが含まれます。 一覧のセルには四角形が含まれます。 既定のレポート アイテムは、別のレポート アイテム (画像など) に置き換えることができます。  
  
 テーブル、マトリックス、または一覧のグループを定義すると、グループ化されたデータを表示するための行と列が Tablix データ領域に追加されます。  
  
 Tablix データ領域の理解には、次の内容の理解が役立ちます。  
  
*   詳細データとグループ化されたデータの違い。  
  
*   グループ階層のメンバーとして構成されるグループ。水平軸に沿って構成されるグループは行グループ、垂直軸に沿って構成されるグループは列グループです。  
  
*  Tablix データ領域の 4 つの部分 (本体、行グループ ヘッダー、列グループ ヘッダー、およびコーナー) の Tablix セルの目的。  
  
*  静的および動的な行と列、およびこれらの行および列とグループとの間の関係。  
  
 この記事ではこれらの概念を明確にし、テンプレートの追加とグループの作成を行う際にレポート ビルダーまたはレポート デザイナーによって自動的に追加される構造について説明します。これにより、独自のニーズに合わせてその構造を変更することができます。 レポート ビルダーおよびレポート デザイナーには、Tablix データ領域の構造の把握に役立つ複数の視覚インジケーターが用意されています。 詳細については、「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="understanding-detail-and-grouped-data"></a>詳細データとグループ化されたデータについて  
 詳細データとは、データ ソースから取得されたレポート データセットのすべてのデータです。 通常、詳細データは、データセット クエリを実行する際にクエリ デザイナーの結果ペインに表示されます。 実際の詳細データには、作成した計算フィールドが含まれており、データセット、データ領域、および詳細グループで設定されているフィルターによって制限されます。 [Quantity] などの簡単な式を使用して、詳細行に詳細データを表示できます。 レポートを実行すると、実行時にクエリ結果の行ごとに詳細行が 1 回繰り返されます。  
  
 グループ化されたデータとは、[SalesOrder] などのグループ定義で指定する値によって分類された詳細データです。 グループ化されたデータをグループ行およびグループ列に表示するには、[Sum(Quantity)] など、グループ化されたデータを集計する簡単な式を使用します。 詳細については、「[グループについて &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="understanding-group-hierarchies"></a>グループ階層について  
 グループは、グループ階層のメンバーとして構成されます。 行グループと列グループの階層は、異なる軸に沿った同一の構造です。 行グループはページを垂直に展開したもの、列グループはページを水平に展開したものと考えることができます。  
  
 ツリー構造は、親子リレーションシップを持つ入れ子になった行および列グループを表します。カテゴリとサブカテゴリなどがその例です。 親グループはツリーのルートであり、子グループはその分岐です。 区域別の売上高や年度別の売上高など、グループには、独立した隣接するリレーションシップが存在する場合もあります。 関連しない複数のツリー階層をフォレストと呼びます。 Tablix データ領域の場合、行グループと列グループはそれぞれ、独立したフォレストとして表されます。 詳細については、「[グループについて &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="understanding-tablix-data-region-areas"></a>Tablix データ領域部分について  
 Tablix データ領域には 4 つのセル領域 (Tablix コーナー、Tablix 行グループ階層、Tablix 列グループ階層、Tablix 本体) があります。 Tablix 本体は常に存在します。 その他の領域は省略可能です。  
  
 Tablix 本体領域のセルには、詳細データとグループ データが表示されます。  
  
 行グループを作成すると、セルが行グループ領域に自動的に作成されます。 これらは行グループ ヘッダー セルであり、既定で行グループ インスタンス値が表示されます。 たとえば、[SalesOrder] でグループ化した場合、グループ インスタンス値は、グループ化された個々の販売注文です。  
  
 列グループを作成すると、セルが列グループ領域に自動的に作成されます。 これらは列グループ ヘッダー セルであり、既定で列グループ インスタンス値が表示されます。 たとえば、[Year] でグループ化した場合、グループ インスタンス値は、グループ化された個々の年度です。  
  
 行グループと列グループの両方を定義すると、Tablix コーナー領域にセルが自動的に作成されます。 この領域のセルはラベルを表示したり、セルを結合してタイトルを作成したりできます。  
  
 詳細については、「[Tablix データ領域部分 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-areas-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="understanding-static-and-dynamic-rows-and-columns"></a>静的および動的な行と列について  
 Tablix データ領域では、セルが、グループに関連付けられた行と列に分類されます。 行グループと列グループのグループ構造は同じです。 この例では行グループを使用しますが、同じ概念を列グループにも適用できます。  
  
 行には静的なものと動的なものがあります。 静的な行は、グループに関連付けられていません。 レポートを実行すると、静的な行は 1 回表示されます。 テーブル ヘッダーとテーブル フッターは静的な行です。 静的な行にはラベルや合計が表示されます。 静的な行のセルのスコープは、データ領域に設定されます。  
  
 動的な行は、1 つまたは複数のグループに関連付けられています。 動的な行は、最も内側のグループの一意のグループ値ごとに 1 回表示されます。 動的な行内のセルのスコープは、そのセルが属する最も内側の行グループおよび列グループに設定されます。  
  
 デザイン画面にテーブルまたは一覧を追加すると、動的な詳細行は、自動的に生成される詳細グループに関連付けられます。 定義上、詳細グループは、Tablix データ領域の最も内側のグループです。 詳細行内のセルには詳細データが表示されます。  
  
 既存の Tablix データ領域に行グループまたは列グループを追加すると、動的なグループ行が作成されます。 動的なグループ行内のセルには、既定のスコープの集計値が表示されます。  
  
 [合計の追加] 機能によって、そのグループにスコープが設定されている値を表示するための行が、現在のグループの外側に自動的に作成されます。 静的な行および動的な行は、手動で追加することもできます。 視覚インジケーターは、静的な行と動的な行を見分けるのに便利です。 詳細については、「[Tablix データ領域のセル、行、および列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [同じデータセットへの複数のデータ領域のリンク &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)   
 [レポート ページでの Tablix データ領域の表示の制御 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/controlling-the-tablix-data-region-display-on-a-report-page.md)   
 [Tablix データ領域の柔軟性について &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
