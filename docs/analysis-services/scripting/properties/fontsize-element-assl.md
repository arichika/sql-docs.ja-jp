---
title: FontSize 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e83cb62a62f35d6a9f47dc9d302e6470a65c468e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="fontsize-element-assl"></a>FontSize 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  フォントに関連する表示特性を記述、 [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)または[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)親要素です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or Measure -->  
   ...  
   <FontSize>...</FontSize>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **FontSize**プロパティは多次元式 (MDX) 式を含みに適用されます**CalculationProperty**を持つ要素を[CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)の*メンバー*または*セル*です。  
  
 親に対応する要素**FontSize**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CalculationProperty>と<xref:Microsoft.AnalysisServices.Measure>です。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
