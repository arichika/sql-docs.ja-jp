---
title: "AttributeHierarchyOptimizedState 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AttributeHierarchyOptimizedState Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeHierarchyOptimizedState
helpviewer_keywords:
- AttributeHierarchyOptimizedState element
ms.assetid: d87148c8-2011-45ae-94c3-851f48babc5f
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 79b7f84f96c9921a0d1fafce4bc0c8604b5fd582
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="attributehierarchyoptimizedstate-element-assl"></a>AttributeHierarchyOptimizedState 要素 (ASSL)
  属性階層に適用される最適化のレベルを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or CubeAttribute -->  
   ...  
   <AttributeHierarchyOptimizedState>...  
   </AttributeHierarchyOptimizedState>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*FullyOptimized*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeAttribute](../../../analysis-services/scripting/data-type/cubeattribute-data-type-assl.md)、 [DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*FullyOptimized*|インスタンスによって、クエリのパフォーマンスを向上させるために属性階層のインデックスが作成されます。|  
|*NotOptimized*|追加のインデックスは作成されません。|  
  
 許可される値に対応する列挙**AttributeHierarchyOptimizedState**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.OptimizationType>します。 親に対応する要素**AttributeHierarchyOptimizedState** AMO オブジェクト モデルでは<xref:Microsoft.AnalysisServices.CubeAttribute>と<xref:Microsoft.AnalysisServices.DimensionAttribute>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  