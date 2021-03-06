---
title: Microsoft 汎用コンテンツ ツリー ビューアーを使用してモデルを参照 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f44c1cb014ca9abcd6122f6db6ee0e33407b7d1d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="browse-a-model-using-the-microsoft-generic-content-tree-viewer"></a>Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用マイニング モデル コンテンツ ビューアーは、マイニング アルゴリズムによって発見されたパターンについての詳細情報を提供します。また、分析処理中に生成されたさまざまな統計情報へのアクセスも提供します。 情報の量と種類は、使用されたアルゴリズムによって異なりますが、次のカテゴリを含んでいます。  
  
-   データのセグメントとその特性  
  
-   各グループまたはデータセット全体に関する説明的な統計情報  
  
-   ツリー内の分岐または子ノードの数  
  
-   クラスターまたはデータセット全体に対する、分散や平均などの計算  
  
 この情報を表示すると、分析結果を理解しやすくなります。 モデルを調整および再トレーニングする方法を特定することもできます。 また、別のアルゴリズムを使用して再トレーニングすることもできます。  
  
## <a name="viewing-mining-model-content"></a>マイニング モデル コンテンツの表示  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ビューアーは、列、ルール、プロパティ、属性、ノードなど、マイニング モデルの *コンテンツ スキーマ行セット* のコンテンツを表示します。 コンテンツ スキーマ行セットは、データ マイニング モデルのコンテンツに関する詳細情報を表すための汎用フレームワークです。  
  
 この詳細情報は、モデル内のパターン、クラスター、またはツリーを表す HTML テーブルにノードとして格納されています。 各ノードをクリックして展開し、数値属性の数式や個別の値数などの詳細を表示できます。 ノード間の親子リレーションシップを調べることもできます。  
  
 マイニング モデルのコンテンツに使用されている用語の一般的な意味については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。 このトピックには、特定の種類のモデルのマイニング モデルのコンテンツに関する情報へのリンクも含まれています。 それぞれの種類のマイニング モデルにはアルゴリズムに固有の情報とデータ内で見つかったパターンが含まれるため、各モデルの種類を十分に理解するために各モデルの種類のテクニカル リファレンス トピックを参照することをお勧めします。  
  
## <a name="querying-mining-model-content"></a>マイニング モデルのコンテンツのクエリ  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 汎用コンテンツ ツリー ビューアーで表示される情報は、マイニング モデルにクエリを実行することによっても取得できます。 マイニング モデル コンテンツに対するクエリは、データ マイニング拡張機能 (DMX) ステートメントを使用して作成できます。 たとえば、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でコンテンツ クエリを実行するには、次の DMX ステートメントを実行します。  
  
```  
SELECT * FROM [<mining model name>].CONTENT  
```  
  
 詳細については、「 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Microsoft 汎用コンテンツ ツリー ビューアー (&) #40";"データ マイニング"&"#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)   
 [データ マイニング アルゴリズムと #40 です。Analysis Services - データ マイニング & #41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
  
