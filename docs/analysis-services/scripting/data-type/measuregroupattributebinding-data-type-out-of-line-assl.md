---
title: MeasureGroupAttributeBinding データ型 (の不一致) (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 35b695ea029d78211a0042d330a961bfcb95a494
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="measuregroupattributebinding-data-type-out-of-line-assl"></a>MeasureGroupAttributeBinding データ型 (不一致) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  メジャー グループに含まれているディメンション内の属性の不一致バインドを表す派生データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroupAttributeBinding>  
   <!-- The following elements extend Binding -->  
   <DatabaseID>...</DatabaseID>  
   <CubeID>...</CubeID>  
   <MeasureGroupID>...</MeasureGroupID>  
   <GranularityAttributeID>...</GranularityAttributeID>  
   <Source>...</Source>  
</MeasureGroupAttributeBinding>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|[バインド](../../../analysis-services/scripting/data-type/binding-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[CubeID](../../../analysis-services/scripting/properties/cubeid-element-assl.md)、 [DatabaseID](../../../analysis-services/xmla/xml-elements-properties/databaseid-element-xmla.md)、 [MeasureGroupID](../../../analysis-services/scripting/properties/measuregroupid-element-assl.md)、 [GranularityAttributeID](../../../analysis-services/scripting/properties/granularityattributeid-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)|  
|派生要素|[バインド](../../../analysis-services/xmla/xml-elements-properties/binding-element-xmla.md)([バインド](../../../analysis-services/scripting/collections/attributes-element-assl.md)コレクションの XML for Analysis (XMLA)[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)と[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンド)|  
  
## <a name="remarks"></a>解説  
 アウトオブ ライン バインドの詳細については、次を参照してください。[データ ソースとのバインド & #40 です。SSAS 多次元 & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
