---
title: PredictHistogram (DMX) |Microsoft ドキュメント
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e7129985eac09d741ea9d00c551a9507ee92c9
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34842145"
---
# <a name="predicthistogram-dmx"></a>PredictHistogram (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定された列の予測のためのヒストグラムを表すテーブルを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PredictHistogram(<scalar column reference> | <cluster column reference>)  
```  
  
## <a name="applies-to"></a>適用対象  
 スカラー列参照またはクラスター列参照です。 除くすべての種類のアルゴリズムで使用できる、[!INCLUDE[msCoName](../includes/msconame-md.md)]アソシエーション アルゴリズムです。  
  
## <a name="return-type"></a>戻り値の型  
 テーブルです。  
  
## <a name="remarks"></a>コメント  
 ヒストグラムは統計情報列を生成します。 返されたヒストグラムの列構造で使用される列参照の種類によって異なります、 **PredictHistogram**関数。  
  
## <a name="scalar-columns"></a>スカラー列  
 \<スカラー列参照 >、ヒストグラムを**PredictHistogram**関数の戻り値は、次の列で構成されます。  
  
-   予測される値。  
  
-   **$Support**  
  
-   **$Probability**  
  
-   **$ProbabilityVariance**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] データ マイニング アルゴリズムをサポートしていない **$ProbabilityVariance**です。 この列は、0 を常に含まれています。[!INCLUDE[msCoName](../includes/msconame-md.md)]アルゴリズムです。  
  
-   **$ProbabilityStdev**  
  
     [!INCLUDE[msCoName](../includes/msconame-md.md)] データ マイニング アルゴリズムをサポートしていない **$ProbabilityStdev**です。 この列は、0 を常に含まれています。[!INCLUDE[msCoName](../includes/msconame-md.md)]アルゴリズムです。  
  
-   **$AdjustedProbability**  
  
     **$AdjustedProbability**列は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]拡張機能を[!INCLUDE[msCoName](../includes/msconame-md.md)]OLE DB for Data Mining 仕様です。  
  
## <a name="cluster-columns"></a>クラスター列  
 ヒストグラムを**PredictHistogram**関数を返します、\<クラスター列参照 > は、次の列で構成されます。  
  
-   **$Cluster** (クラスター名を表します)  
  
-   **$Distance**  
  
-   **$Probability**  
  
## <a name="examples"></a>使用例  
 次の例は、単一クエリに対して Bike Buyer 列の予測された状態を返します。 クエリを使用して取得調整済みの確率に基づいて、Bike Buyer 属性の上位 2 最も可能性の高い状態も返されます、 **PredictHistogram**関数。  
  
```  
SELECT  
  [TM Decision Tree].[Bike Buyer],  
  TopCount(PredictHistogram([Bike Buyer]),$AdjustedProbability,3)  
From  
  [TM Decision Tree]  
NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [クラスター &#40;DMX&#41;](../dmx/cluster-dmx.md)   
 [ClusterProbability &#40;DMX&#41;](../dmx/clusterprobability-dmx.md)   
 [PredictAdjustedProbability &#40;DMX&#41;](../dmx/predictadjustedprobability-dmx.md)   
 [PredictProbability &#40;DMX&#41;](../dmx/predictprobability-dmx.md)   
 [PredictStdev &#40;DMX&#41;](../dmx/predictstdev-dmx.md)   
 [PredictSupport &#40;DMX&#41;](../dmx/predictsupport-dmx.md)   
 [PredictVariance &#40;DMX&#41;](../dmx/predictvariance-dmx.md)   
 [データ マイニング アルゴリズム&#40;Analysis Services - データ マイニング&#41;](../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データ マイニング拡張機能&#40;DMX&#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
