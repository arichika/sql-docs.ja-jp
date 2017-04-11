---
title: "レポートへのグラフの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# レポートへのグラフの追加 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでデータをビジュアル形式でまとめるには、グラフ データ領域を使用します。 表示するデータの種類に対して適切な種類のグラフを選択することが重要です。 これにより、データをグラフ形式にした場合にどの程度わかりやすくなるかが決まります。 グラフ要素の詳細については、「[グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)」を参照してください。  
  
 グラフ データ領域をレポートに追加するには、グラフの新規作成ウィザードを実行するのが最も簡単な方法です。 このウィザードを使用して、縦棒グラフ、折れ線グラフ、円グラフ、横棒グラフ、および面グラフを作成できます。 これらのグラフおよびその他の種類のグラフは、手動で追加することもできます。  
  
 グラフ データ領域をデザイン画面に追加したら、グラフのグラフ データ ペインに数値データおよび非数値データのレポート データセット フィールドをドラッグします。 グラフをクリックすると、系列グループ、カテゴリ グループ、および値の 3 つの領域を持つグラフ データ ペインが表示されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## グラフ ウィザードを使用してグラフをレポートに追加するには  
  
1.  > [!NOTE]  
    >  グラフ ウィザードは、レポート ビルダーでのみ利用可能です。  
  
     **[挿入]** タブの **[グラフ]** をクリックし、次に **[グラフ ウィザード]** をクリックします。  
  
2.  グラフの**新規作成**ウィザードの手順に従って操作します。  
  
3.  **[ホーム]** タブで **[実行]** をクリックして、表示されたレポートを確認します。  
  
4.  レポートの作業を続行するには、**[実行]** タブで **[デザイン]** をクリックします。  
  
## レポートにグラフを追加するには  
  
1.  レポートを作成し、データセットを定義します。 詳細については、[レポート データセット &#40;SSRS&#41; ](../../reporting-services/report-data/report-datasets-ssrs.md) に関する記事を参照してください。  
  
2.  **[挿入]** タブの **[グラフ]** をクリックし、次に **[グラフの挿入]** をクリックします。  
  
3.  デザイン画面上のグラフの左上隅となる場所をクリックし、グラフの右下隅となる位置までドラッグします。  
  
     **[グラフの種類を選択]** ダイアログ ボックスが表示されます。  
  
4.  追加するグラフの種類を選択します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  グラフをクリックして、**グラフ データ** ペインを表示します。  
  
6.  1 つまたは複数のフィールドを **[値]** 領域に追加します。 この情報は値軸にプロットされます。  
  
7.  グループ化したフィールドを **[カテゴリ グループ]** 領域に追加します。 このフィールドを **[カテゴリ グループ]** 領域に追加すると、グループ化したフィールドが自動的に作成されます。 グループごとに、系列のデータ ポイントを表します。  
  
8.  カテゴリ別にデータをまとめるには、データ フィールドを右クリックし、**[系列のプロパティ]** をクリックします。 **[カテゴリ]** ボックスの一覧からカテゴリ フィールドを選択します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
9. **[ホーム]** タブで **[実行]** をクリックして、表示されたレポートを確認します。  
  
10. レポートの作業を続行するには、**[実行]** タブで **[デザイン]** をクリックします。  
  
 横棒グラフや縦棒グラフなど、軸を使用するグラフでは、カテゴリ軸にすべてのカテゴリ ラベルが表示されるとは限りません。 軸ラベルの変更方法の詳細については、「[Specify an Axis Interval &#40;Report Builder and SSRS&#41;](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)」(軸間隔の指定 &#40;レポート ビルダーおよび SSRS&#41;) を参照してください。  
  
## 参照  
 [グラフ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/chart-types-report-builder-and-ssrs.md)   
 [グラフ内の空のデータ ポイントおよび NULL データ ポイント &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [チュートリアル: レポートへの横棒グラフの追加 (レポート ビルダー)](http://go.microsoft.com/fwlink/?LinkId=198052)   
 [チュートリアル: レポートへの横棒グラフの追加 (レポート デザイナー)](http://go.microsoft.com/fwlink/?LinkId=198042)   
 [チュートリアル: レポートへの円グラフの追加 (レポート ビルダー)](http://go.microsoft.com/fwlink/?LinkId=198051)   
 [チュートリアル: レポートへの円グラフの追加 (レポート デザイナー)](http://go.microsoft.com/fwlink/?LinkId=198041)  
  
  