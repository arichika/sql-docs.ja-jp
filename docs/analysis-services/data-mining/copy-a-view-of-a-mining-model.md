---
title: "マイニング モデルの表示のコピー | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クリップボード [データ マイニング]"
  - "マイニング モデル ビューアー [Analysis Services], クリップボード"
  - "マイニング モデルのクリップボードへのコピー"
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
caps.latest.revision: 38
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 38
---
# マイニング モデルの表示のコピー
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーの **[マイニング モデル ビューアー]** タブでは、マイニング モデルの種類ごとに異なるビューアーを使用します。 これらのビューアーの一部には、コンテンツをクリップボードにコピーし、そこからドキュメントやイメージ操作ソフトウェアに貼り付けるためのコンポーネントがあります。 この機能は次のコンポーネントで使用可能です。  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] クラスター ビューアーのクラスター ダイアグラムと [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアー  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] ツリー ビューアーのデシジョン ツリーと [!INCLUDE[msCoName](../../includes/msconame-md.md)] タイム シリーズ ビューアー  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] シーケンス クラスター ビューアーの状態遷移  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール ビューアーの依存関係ネットワーク、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes ビューアー、および [!INCLUDE[msCoName](../../includes/msconame-md.md)] ツリー ビューアー  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーの [ノードの詳細] ペインにあるマイニング モデル コンテンツ  
  
 マイニング モデル全体の表現をコピーすることも、ビューアーで表示している部分のみをコピーすることもできます。  
  
> [!WARNING]  
>  ビューアーを使用してモデルをコピーする場合、新しいモデル オブジェクトは作成されません。 新しいモデルを作成するには、ウィザードまたはデータ マイニング デザイナーを使用する必要があります。 詳細については、「[マイニング モデルのコピーの作成](../../analysis-services/data-mining/make-a-copy-of-a-mining-model.md)」を参照してください。  
  
### モデル全体をクリップボードにコピーするには  
  
1.  **[マイニング モデル ビューアー]** タブの **[マイニング モデル]** リストで、表示するマイニング モデルを選択します。  
  
2.  **[依存関係ネットワーク]** タブなど、適切なタブを選択してから、そのタブのツール バーで **[グラフ全体のコピー]** をクリックします。  
  
### モデルの表示部分のみをクリップボードにコピーするには  
  
1.  **[マイニング モデル ビューアー]** タブの **[マイニング モデル]** リストで、表示するマイニング モデルを選択します。  
  
2.  **[依存関係ネットワーク]** タブなど、適切なタブを選択し、モデルを拡大または縮小して、希望のレベルで表示します。  
  
3.  選択したタブのツール バーで **[グラフ ビューのコピー]** をクリックします。  
  
### マイニング モデル内容をクリップボードにコピーするには  
  
1.  **[マイニング モデル ビューアー]** タブの **[マイニング モデル]** リストで、表示するマイニング モデルを選択します。  
  
2.  **[ビューアー]** ボックスの一覧で **[Microsoft 汎用コンテンツ ツリー ビューアー]** をクリックします。  
  
3.  **[ノードのキャプション (一意の ID)]** ペインでノードをクリックします。  
  
4.  **[ノードの詳細]** ペインを右クリックし、**[すべて選択]** をクリックします。  
  
5.  **[ノードの詳細]** ペインをもう一度右クリックし、**[コピー]** をクリックします。  
  
## 参照  
 [マイニング モデル ビューアーのタスクと操作方法](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  