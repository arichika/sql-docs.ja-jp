---
title: AllMemberTranslation 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c46039bcf1d72014a12ee791484cacc205ed1f16
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="allmembertranslation-element-assl"></a>AllMemberTranslation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  すべてのメンバーのキャプションの翻訳が含まれています、[階層](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AllMemberTranslations>  
   <AllMemberTranslation xsi:type="Translation">...  
   </AllMemberTranslation>  
</AllMemberTranslations>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[翻訳](../../../analysis-services/scripting/objects/translation-element-assl.md)|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AllMemberTranslations](../../../analysis-services/scripting/collections/allmembertranslations-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素、 **AllMemberTranslations**分析管理オブジェクト (AMO) オブジェクト モデルのコレクションが<xref:Microsoft.AnalysisServices.Hierarchy>です。  
  
## <a name="see-also"></a>参照  
 [Translation 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/translation-element-assl.md)   
 [Hierarchy 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/hierarchy-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
