---
title: マップの凡例、カラー スケール、および関連付けられているルールの変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
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
f1_keywords:
- sql13.rtp.rptdesigner.mapcolorscaleproperties.labels.f1
- sql13.rtp.rptdesigner.mappointlayerproperties.typerules.f1
- sql13.rtp.rptdesigner.shared.maprulesdistribution.f1
- "10512"
- "10539"
- "10533"
- sql13.rtp.rptdesigner.maplegendtitleproperties.general.f1
- "10534"
- "10516"
- sql13.rtp.rptdesigner.mapdistancescaleproperties.general.f1
- sql13.rtp.rptdesigner.mapcolorscaleproperties.general.f1
- sql13.rtp.rptdesigner.mapcolorscaletitleproperties.general.f1
- "10514"
- sql13.rtp.rptdesigner.mappointlayerproperties.sizerules.f1
- "10513"
- sql13.rtp.rptdesigner.shared.mapruleslegend.f1
- sql13.rtp.rptdesigner.shared.embeddedlabels.f1
- "10510"
- "10509"
- sql13.rtp.rptdesigner.maplegendproperties.general.f1
- "10540"
- "10517"
ms.assetid: a1d691b2-c5ae-420f-af60-b7c54a7385a4
caps.latest.revision: 12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 96de567e40763ca1db0b2aae8f13af3d8a17ffb5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="change-map-legends-color-scale-and-associated-rules-report-builder-and-ssrs"></a>マップの凡例、カラー スケール、および関連付けられているルールの変更 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、マップにはマップの凡例、カラー スケール、および距離スケールを含めることができます。 これらのマップ要素は、マップに表示されているデータをユーザーが解釈する際に役に立ちます。  
  
 凡例には、次のマップ要素が含まれます。  
  
-   **マップの凡例** 分析データの解釈に役立つガイドを表示します。マップ レイヤー上のマップ要素の表示は、分析データによって変化します。 マップには、複数の凡例を含めることができます。 マップ レイヤーごとに使用する凡例を指定します。 凡例では、複数のマップ レイヤーへのガイドを提供できます。  
  
-   **カラー スケール** マップ上の色の解釈に役立つガイドを表示します。 マップには、1 つのカラー スケールが含まれます。 複数のレイヤーで、カラー スケールのデータを提供できます。  
  
-   **距離スケール** マップのスケールの解釈に役立つガイドを表示します。 マップには、1 つの距離スケールが含まれます。 距離スケールは、現在のマップ ビューポートのズーム値によって決定されます。  
  
 ![rs_MapElements](../../reporting-services/report-design/media/rs-mapelements.gif "rs_MapElements")  
  
##  <a name="Viewport"></a> ビューポートを基準とする凡例の相対位置を変更するには  
  
#### <a name="to-change-the-position-of-a-legend-relative-to-the-viewport"></a>ビューポートを基準とする凡例の相対位置を変更するには  
  
1.  デザイン ビューで、凡例を右クリックし、*[\<report item>*** のプロパティ]* ページを開きます。  
  
2.  **[位置]** で、ビューポートを基準とする凡例の相対的な表示位置をクリックします。  
  
3.  凡例をビューポートの外に表示するには、**[\<report item> をビューポートの外側に表示する]** を選択します。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    > [!NOTE]  
    >  プレビューすると、凡例に関連したルールからの結果が存在する場合にのみ、マップの凡例およびカラー スケールが表示されます。 表示するアイテムが存在しない場合、表示レポートに凡例は表示されません。  
  
##  <a name="MapLegend"></a> マップの凡例のレイアウトを変更するには  
  
#### <a name="to-change-the-layout-of-a-map-legend"></a>マップの凡例のレイアウトを変更するには  
  
1.  デザイン ビューで、凡例を右クリックし、 **[凡例のプロパティ]** ページを開きます。  
  
2.  **[凡例のレイアウト]** で、凡例に使用するテーブル レイアウトをクリックします。 別のオプションをクリックすると、デザイン画面のレイアウトが変更されます。  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="MapLegendTitle"></a> マップの凡例のタイトルを表示または非表示にするには  
  
#### <a name="to-show-or-hide-a-map-legend-title"></a>マップの凡例のタイトルを表示または非表示にするには  
  
-   デザイン画面でマップの凡例を右クリックし、 **[凡例のタイトルの表示]** をクリックします。  
  
##  <a name="ColorScaleTitle"></a> カラー スケールのタイトルを表示または非表示にするには  
  
#### <a name="to-show-or-hide-a-color-scale-title"></a>カラー スケールのタイトルを表示または非表示にするには  
  
-   デザイン画面でカラー スケールを右クリックし、 **[カラー スケールのタイトルの表示]** をクリックします。  
  
##  <a name="MoveItems"></a> 最初の凡例からアイテムを移動するには  
 追加の凡例を必要な数だけ作成し、各マップ レイヤーのルールを更新して、ルールの結果を表示する凡例を指定します。  
  
#### <a name="to-create-a-new-legend"></a>新しい凡例を作成するには  
  
-   デザイン ビューで、マップ ビューポートの外部でマップを右クリックし、 **[凡例の追加]** をクリックします。  
  
     新しい凡例がマップに表示されます。  
  
#### <a name="to-display-rule-results-in-a-legend"></a>ルールの結果を凡例に表示するには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  **[凡例]** をクリックします。  
  
4.  **[この凡例に表示]** ボックスの一覧で、ルールの結果を表示する凡例の名前をクリックします。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TemplateStyle"></a> テンプレート スタイルに基づいてマップ要素の色を変えるには  
  
#### <a name="to-vary-map-element-colors-based-on-a-template-style"></a>テンプレート スタイルに基づいてマップ要素の色を変えるには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  **[テンプレート スタイルを適用する]** をクリックします。  
  
     テンプレート スタイルは、フォント、罫線のスタイル、およびカラー パレットを指定します。 個々のマップ要素には、それぞれ異なる色が、マップ ウィザードまたはマップ レイヤー ウィザードで指定されたテーマのカラー パレットから割り当てられます。 関連付けられた分析データが存在しないレイヤーには常にこのオプションが適用されます。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ColorPalette"></a> カラー パレットに基づいてマップ要素の色を変えるには  
  
#### <a name="to-vary-map-element-colors-based-on-color-palette"></a>カラー パレットに基づいてマップ要素の色を変えるには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  **[色パレットを使用してデータを表示する]** をクリックします。  
  
     このオプションでは、指定したカスタムのパレットまたは組み込みのパレットが使用されます。 マップ要素には、関連する分析データに基づき、それぞれ異なる色または色の濃淡がパレットから割り当てられます。  
  
4.  色によって視覚化する分析データが格納されているフィールドの名前を **[データ フィールド]** に入力します。  
  
5.  **[パレット]** のドロップダウン リストから、使用するパレットの名前を選択します。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ColorRanges"></a> 色の範囲に基づいてマップ要素の色を変えるには  
  
#### <a name="to-vary-map-element-colors-based-on-color-ranges"></a>色の範囲に基づいてマップ要素の色を変えるには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  **[色の範囲を使用してデータを表示する]** をクリックします。  
  
     このオプションを選択すると、このページで指定された開始色、中間色、および終了色と、 **[分布]** ページで指定したオプションとに基づき、関連する分析データがいくつかの範囲に分類されます。 関連付けられているデータおよび該当する範囲に基づき、それぞれのマップ要素には適切な色がレポート プロセッサによって割り当てられます。  
  
4.  色によって視覚化する分析データが格納されているフィールドの名前を **[データ フィールド]** に入力します。  
  
5.  範囲の下限に使用する色を **[開始色]** に指定します。  
  
6.  範囲の中間に使用する色を **[中間の色]** に指定します。  
  
7.  範囲の上限に使用する色を **[終了色]** に指定します。  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="CustomColors"></a> カスタム色に基づいてマップ要素の色を変えるには  
  
#### <a name="to-vary-map-element-colors-based-on-custom-colors"></a>カスタム色に基づいてマップ要素の色を変えるには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  **[作成した色を使用してデータを表示する]** をクリックします。  
  
     このオプションを選択した場合、指定した色の一覧が使用されます。 マップ要素には、関連する分析データに基づき、一覧から色が割り当てられます。 マップ要素が多く色が足りない場合は、どの色も割り当てられません。  
  
4.  色によって視覚化する分析データが格納されているフィールドの名前を **[データ フィールド]** に入力します。  
  
5.  **[作成した色]** の **[追加]** をクリックして、個々のカスタム色を指定します。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="DistributionOptions"></a> 凡例の分布オプションを設定するには  
  
#### <a name="to-set-distribution-options-for-a-legend"></a>凡例の分布オプションを設定するには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  **[\<rule type> を使用してデータを表示する]** オプションを選択します。 分布オプションを使用するには、レイヤーに関連付けられている分析データに基づき、 **[分布]** ページで範囲を作成する必要があります。  
  
4.  **[分布]** をクリックします。  
  
5.  次のいずれかの分布タイプを選択します。  
  
    -   **[等間隔]**。 データを一定の間隔に区分する範囲を指定します。  
  
    -   **[均等割り付け]**。 個々のアイテム数が均等になるようにデータを区分する範囲を指定します。  
  
    -   **[最適]**。 釣り合いのとれた部分範囲を形成するように分布が自動的に調整されます。  
  
    -   **[カスタム]**。 範囲の数を独自に指定して、値の分布を制御します。  
  
     分布のオプションの詳細については、「[ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。  
  
6.  **[部分範囲の数]** に、使用する部分範囲の数を入力します。 分布タイプが **[最適]** の場合は、部分範囲の数が自動的に計算されます。  
  
7.  **[範囲の開始]** に範囲の最小値を入力します。 この値よりも小さい値はすべて、範囲の下限と同じと見なされます。  
  
8.  **[範囲の終了]** に範囲の最大値を入力します。 この値を超える値はすべて、範囲の上限と同じと見なされます。  
  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="RuleLegend"></a> ルールの凡例の内容を変更するには  
  
#### <a name="to-change-the-contents-of-a-color-size-width-or-marker-type-legend"></a>色、サイズ、幅、またはマーカーの種類の凡例の内容を変更するには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>***のルール]** をクリックします。  
  
3.  **[***rule type* を使用してデータを表示する]\< が選択されていることを確認します。  
  
4.  **[データ フィールド]** で、レイヤー上に視覚化しようとしている分析データが選択されていることを確認します。  
  
    > [!NOTE]  
    >  ドロップダウン リストにフィールドが表示されない場合は、レイヤーを右クリックし、 **[レイヤー データ]** をクリックして [分析データ] ([マップ レイヤー データのプロパティ] ダイアログ ボックス) ページを開き、このレイヤーに対する分析データが指定されていることを確認します。  
  
5.  **[凡例]** をクリックします。  
  
6.  **[この凡例に表示]** で、ルールの結果を表示するのに使用するマップの凡例を選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ColorScale"></a> カラー スケールの内容を変更するには  
  
#### <a name="to-change-the-contents-of-the-color-scale-or-a-color-legend"></a>カラー スケールまたは色の凡例の内容を変更するには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>* **の色のルール]** をクリックします。  
  
3.  使用する色ルールを選択します。 マップの凡例またはカラー スケールにアイテムを表示するには、**[\<rule type> を使用してデータを表示する]** のいずれかのオプションを選択する必要があります。  
  
4.  **[データ フィールド]** で、レイヤー上に視覚化しようとしている分析データが選択されていることを確認します。  
  
    > [!NOTE]  
    >  ドロップダウン リストにフィールドが表示されない場合は、レイヤーを右クリックし、 **[レイヤー データ]** をクリックして [分析データ] ([マップ レイヤー データのプロパティ] ダイアログ ボックス) ページを開き、このレイヤーに対する分析データが指定されていることを確認します。  
  
5.  **[凡例]** をクリックします。  
  
6.  ルールの結果をカラー スケールに表示するには、 **[カラー スケールのオプション]** で **[カラー スケールに表示]** を選択します。 このオプションは複数の色ルールに対して指定できます。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="HideItems"></a> すべてのアイテムを凡例から削除するには  
  
#### <a name="to-hide-items-based-on-a-rule"></a>ルールに基づいてアイテムを非表示にするには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>***のルール]** をクリックします。  
  
3.  **[凡例]** をクリックします。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="ChangeFormatItems"></a> 凡例の内容の書式を変更するには  
 マップの凡例に関連付けられているルールの凡例オプションを設定します。  
  
#### <a name="to-change-the-format-of-content-in-a-legend"></a>凡例の内容の書式を変更するには  
  
1.  デザイン ビューで、マップ ペインが表示されるまでマップをクリックします。  
  
2.  必要なデータが存在するレイヤーを右クリックし、*[\<マップ要素の種類>***のルール]** をクリックします。  
  
3.  **[凡例]** をクリックします。  
  
4.  **[凡例のテキスト]** には、凡例に表示するデータを指定するキーワードが表示されます。 マップ キーワードとカスタム書式を使用すると、凡例のテキストの書式を制御できます。 たとえば、 #FROMVALUE {C2} は小数点以下 2 桁の通貨書式を示します。 詳細については、「 [ルールおよび分析データを使用した多角形、線、およびポイントの表示の変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)」を参照してください。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [マップ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [マップまたはマップ レイヤーの追加、変更、または削除 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-a-map-or-map-layer-report-builder-and-ssrs.md)   
 [マップまたはマップ レイヤーのデータと表示のカスタマイズ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/customize-the-data-and-display-of-a-map-or-map-layer-report-builder-and-ssrs.md)   
 [レポートのトラブルシューティング: マップ レポート (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)   
 [マップ ウィザードおよびマップ レイヤー ウィザードのページ &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)  
  
  
