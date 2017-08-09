---
title: "クラスター (DMX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Cluster
dev_langs:
- DMX
helpviewer_keywords:
- Cluster function
ms.assetid: 14b2942a-6dec-4dfa-98a6-697a3c89036a
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 65e0d6942d48657f99d5cff3365a80d4853c66d4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="cluster-dmx"></a>Cluster (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  入力ケースを含んでいる可能性が最も高いクラスターを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Cluster()  
```  
  
## <a name="applies-to"></a>適用対象  
 この関数は、基本となるデータ マイニング モデルがクラスターをサポートする場合にのみ使用できます。  
  
## <a name="return-type"></a>戻り値の型  
 **クラスター**関数では、パラメーターは必要ありません。  
  
 **クラスター**関数は、クラスター名のスカラー値を返します。 ただし、別の関数の引数としてこの関数を使用する場合は、する必要があります記事として、\<クラスター列参照 >。  
  
## <a name="remarks"></a>解説  
 **クラスター**として使用することも、`<`クラスター列参照`>`の**PredictHistogram**関数。  
  
## <a name="examples"></a>使用例  
 次の例で単一クエリを使用して、 [PredictHistogram & # #40; DMX &#41;](../dmx/predicthistogram-dmx.md)とクラスターの TM Clustering マイニング モデルと個々 のケースが各クラスターである確率の各クラスターから個々 のケースの距離を取得する関数。  
  
```  
SELECT  
  PredictHistogram(Cluster())  
FROM  
  [TM Clustering]  
  NATURAL PREDICTION JOIN  
(SELECT 28 AS [Age],  
  '2-5 Miles' AS [Commute Distance],  
  'Graduate Degree' AS [Education],  
  0 AS [Number Cars Owned],  
  0 AS [Number Children At Home]) AS t  
```  
  
## <a name="see-also"></a>参照  
 [ClusterProbability (&) #40";"DMX"&"#41;](../dmx/clusterprobability-dmx.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;関数リファレンス](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [関数 (&) #40";"DMX"&"#41;](../dmx/functions-dmx.md)   
 [一般的な予測関数 (&) #40";"DMX"&"#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
