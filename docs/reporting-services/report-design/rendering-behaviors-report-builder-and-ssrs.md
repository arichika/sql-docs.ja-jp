---
title: "レンダリングの動作 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f873ef9-27a3-40e5-b58b-6774f8027a58
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# レンダリングの動作 (レポート ビルダーおよび SSRS)
  選択したレンダラーによっては、レポートをレンダリングする際に、レポート本文とそのコンテンツに特定の規則が適用されます。 レポート アイテムが 1 ページにまとめられる際の方法は、次に示す要因の組み合わせによって決まります。  
  
-   レンダリングの規則。  
  
-   レポート アイテムの幅と高さ。  
  
-   レポート本文のサイズ。  
  
-   ページの幅と高さ。  
  
-   レンダラー固有の改ページ調整。  
  
 このトピックでは、Reporting Services で適用される一般的な規則について説明します。 詳細については、「[レポート アイテムのレンダリング &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/rendering-report-items-report-builder-and-ssrs.md)」、「[データ領域の表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/rendering-data-regions-report-builder-and-ssrs.md)」、「[データの表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/rendering-data-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## HTML、MHTML、Word、および Excel の一般的な動作 (ソフト改ページ レンダラー)  
 HTML 形式や MHTML 形式でエクスポートされたレポートは、コンピューター画面での操作性を重視して最適化され、ページの長さは固定的ではありません。 改ページは、レポート本文内のおおよその位置に、垂直方向にのみ挿入されます。 おおよその位置は、[プロパティ] ペインにある対話的な高さ設定によって決まります。 たとえば、対話的な高さが 5 インチに設定されているとします。 レポートをレンダリングすると、このページの高さは約 5 インチになります。 Word および Excel の改ページは論理的な改ページによって調整されるため、対話的な高さの設定は無視されます。  
  
> [!NOTE]  
>  ソフト改ページ レンダラーでレポートがどのように表示されるかを確認するには、レポートのプレビューを使用します。 HTML、MHTML、Word、または Excel 形式で表示した場合と同じように、レポートが表示されます。  
  
 レポートを HTML、MHTML、Word、または Excel にエクスポートする場合は、次の一般的な規則が適用されます。  
  
-   レポート アイテムには、論理的な改ページ (明示的に挿入した改ページ) が適用されます。 たとえば、各グループ間に改ページを挿入した場合、これらの改ページが、レポートのレンダリング時に適用されます。  
  
-   ページの高さとレポート アイテムの出現回数に基づいて、おおよそのレイアウトが作成されます。 たとえば、テキスト ボックスの高さが 0.5 インチで、繰り返し 5 回出現する場合、2.5 インチが確保されます。  
  
-   対話的な高さの設定に基づいて、複数のソフト改ページが挿入されます。 HTML および ReportViewer コントロールでこの動作を抑制し、明示的な改ページでのみ制御するようにする場合は、**対話的な高さ**の値を 0 または極端に大きな値に設定します。  
  
    > [!NOTE]  
    >  ソフト改ページ レンダラーでは、対話的な幅の設定は使用されません。  
  
-   ひとまとまりとして扱う必要のあるウィンドウ、孤立したアイテム、およびレポート アイテムがきちんと収まるように、レポート ページが拡大される場合があります。 そのため、レポートが画面の幅を超えることもありますが、その場合はスライダー バーを使って閲覧できます。  
  
-   レポートには、垂直方向にのみ改ページが適用されます。  
  
-   ページ余白は適用されません。  
  
## PDF、画像、および印刷の一般的な動作 (ハード改ページ レンダラー)  
 PDF および画像を使ってエクスポートされたレポートでは、書籍のように、常に一定のページ サイズで閲覧される印刷物としての見やすさが重視されます。 改ページは、レポート本文内の特定の位置に、垂直方向および水平方向に挿入されます。 その位置は、ページの幅と高さの設定によって決まります。  
  
> [!NOTE]  
>  ハード改ページ レンダラーでレポートがどのように表示されるかを確認するには、印刷プレビューを使用します。 PDF 形式または画像形式で表示した場合と同じようにレポートが表示されます。  
  
-   ページ番号は、左から右、次に、上から下へと付けられます。  
  
-   レポート アイテムには、論理的な改ページ (明示的に挿入した改ページ) が適用されます。 このような改ページによって、レポート アイテムが強制的に次のページに移動される場合があります。  
  
-   ひとまとまりとして扱う必要のあるレポート アイテムの途中で、物理的な改ページが生じる場合は、それらのアイテムを次のページに移動する必要があります。  
  
-   ページ サイズの制約により、アイテムをすべてまとめて表示したり、繰り返し表示したりできない場合があります。 その場合、レポート アイテムをページ上に収める関係上、他のアイテムと一緒に繰り返し表示するための特定の規則が無視される場合があります。  
  
-   テキスト ボックスが大きすぎて縦方向の使用可能なページ領域内に収まらないなど、アイテムを 1 つにまとめることができなかった場合、そのアイテムは、ページの物理的な境界でクリッピングされ、残りの部分が次のページから表示されます。  
  
-   レポートには、垂直方向と水平方向の改ページが適用されます。  
  
    > [!NOTE]  
    >  ハード改ページ レンダラーでは、対話的な幅の設定は使用されません。  
  
## レポート アイテム間の最小間隔  
 レポート本文内のレポート アイテムは、その内容に合わせて拡大されます。 たとえば、マトリックス データ領域は通常、レポートのレンダリング時にページの境界を越えて拡大されます。また、テキスト ボックスの高さは、式から返されたデータに応じて調整されます。  
  
 レポート レイアウトで定義された、レポート アイテム間の最小間隔は維持されます。 レポート レイアウト上で、あるレポート アイテムを別のレポート アイテムに隣接するように配置した場合、レポート アイテム間の距離には最小距離が適用され、レポートが上下左右に拡大されても、この距離が保たれます。 たとえば、レポートにマトリックス データ領域を追加した後、そのマトリックスの 0.25 インチ右側に四角形を追加した場合、マトリックスのサイズが大きくなっても、その間隔が維持されます。 各アイテムは、左側にあるアイテムとの間の最小距離が維持されるように右に移動します。  
  
## ページ ヘッダーとページ フッター  
 ページ ヘッダーとページ フッターは、レンダリングされた各ページの最上部と最下部に表示されます。 ページ ヘッダーとページ フッターには、罫線の色、罫線のスタイル、および罫線の幅を定義できます。 背景色や背景画像を追加することもできます。 選択した形式によっては、これらの書式設定オプションがすべてレンダリングされます。  
  
 HTML 形式または MHTML 形式でレンダリングした場合、ページ ヘッダーおよびページ フッターには次の規則が適用されます。  
  
> [!NOTE]  
>  Excel でのヘッダーとフッターの表示方法の詳細については、「[Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)」(Microsoft Excel へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;) を参照してください。 Word でのヘッダーとフッターの表示方法の詳細については、「[Exporting to Microsoft Word &#40;Report Builder and SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)」(Microsoft Word へのエクスポート &#40;レポート ビルダーおよび SSRS&#41;) を参照してください。  
  
-   ヘッダーとフッターが存在する場合、すべてのページの使用可能なページ領域内の最上部と最下部にレンダリングされます。  
  
-   ヘッダーまたはフッターが非表示にされているページでは、それらがレンダリングされなくても、使用可能なページ領域内には、ヘッダーまたはフッターの高さに必要な領域が確保されます。  
  
-   ヘッダーまたはフッターの内容がその境界を越えた場合、ヘッダーまたはフッターのサイズがその内容に応じて拡大されます。  
  
 PDF 形式または画像形式でレンダリングした場合、ページ ヘッダーおよびページ フッターには次の規則が適用されます。  
  
-   ヘッダーまたはフッターは、すべてのページの使用可能なページ領域内の最上部と最下部にレンダリングされます。  
  
-   ヘッダーまたはフッターが非表示にされているページでは、それらがレンダリングされなくても、使用可能なページ領域内には、ヘッダーまたはフッターの高さに必要な領域が確保されます。  
  
-   ヘッダーとフッターは拡大も縮小もされません。 ヘッダーまたはフッターは、その作成時に指定された高さですべてのページにレンダリングされます。  
  
-   レポート内の列数に関係なく、1 ページあたりに存在するヘッダーとフッターはそれぞれ 1 つだけです。  
  
-   ヘッダーまたはフッターの内容がその境界を越えた場合、内容がクリッピングされます。  
  
-   レポートをサブレポートとしてレンダリングした場合、元の RDL ファイル内で定義されたヘッダーおよびフッターはレンダリングされません。  
  
## 論理的な改ページ  
 論理的な改ページとは、ユーザーによってレポート アイテムやレポート グループの前または後に挿入される改ページをいいます。 改ページを使用することにより、レポートのレンダリング時またはエクスポート時に最も見やすくなるような形で、その内容をレポート ページに収めることができます。  
  
 論理的な改ページのレンダリングには、次の規則が適用されます。  
  
-   常に非表示になるレポート アイテムや、可視性が別のレポート アイテムのクリックによって制御されるレポート アイテムでは、論理的な改ページが無視されます。  
  
-   表示と非表示が条件に応じて変わるアイテムには、レポートをレンダリングした時点で可視状態であった場合に、論理的な改ページが適用されます。  
  
-   論理的な改ページが適用されたレポート アイテムと、そのピア レポート アイテム間のスペースは確保されます。  
  
-   レポート アイテムの前に論理的な改ページが挿入されている場合、そのレポート アイテムは強制的に次のページに移動されます。 レポート アイテムは、次のページの一番上にレンダリングされます。  
  
-   テーブル セルまたはマトリックス セル内のアイテムで定義された論理的な改ページは保持されません。 これは、一覧にあるアイテムには当てはまりません。  
  
## 参照  
 [さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/interactive functionality - different report rendering extensions.md)   
 [HTML での表示 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/rendering-to-html-report-builder-and-ssrs.md)   
 [ページ レイアウトとレンダリング &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  