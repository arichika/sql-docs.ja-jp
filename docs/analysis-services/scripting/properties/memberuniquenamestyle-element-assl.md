---
title: MemberUniqueNameStyle 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 36a88bce39ea5c3e7beb7834c3e2abb8de0abae5
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="memberuniquenamestyle-element-assl"></a>MemberUniqueNameStyle 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  一意の名前が決定に含まれる階層のメンバーに対して生成される、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension>  
   ...  
   <MemberUniqueNameStyle>...</MemberUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ネイティブ*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*ネイティブ*|インスタンスによって、メンバーの一意の名前が自動的に決定されます。|  
|*NamePath*|インスタンスによって、メンバーの各レベルおよびキャプションで構成される複合名が生成されます。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**MemberUniqueNameStyle**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [Cube 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [CubeDimension データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)  
  
  
