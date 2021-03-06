---
title: アカウントの要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0e9cda9f82df4f1b7a6d445d7cb85e69c635833f
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="account-element-assl"></a>Account 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  内の勘定科目の種類に関する詳細を含む、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Accounts>  
   <Account>  
      <AccountType>...</AccountType>  
      <AggregationFunction>...</AggregationFunction>  
            <Aliases>...</Aliases>  
            <Annotations>...</Annotations>  
   </Account>  
</Accounts>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Accounts](../../../analysis-services/scripting/collections/accounts-element-assl.md)|  
|子要素|[AccountType](../../../analysis-services/scripting/properties/accounttype-element-assl.md)、 [AggregationFunction](../../../analysis-services/scripting/properties/aggregationfunction-element-assl.md)、[エイリアス](../../../analysis-services/scripting/collections/aliases-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 ディメンションが[型](../../../analysis-services/scripting/properties/type-element-dimension-assl.md)要素に設定されている*アカウント、*ディメンションのメンバーによって表される、収益や費用などのアカウントの種類を指定する属性を持つことができます。 勘定科目の種類を使用して[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)要素が[AggregationFunction](../../../analysis-services/scripting/properties/aggregatefunction-element-assl.md)要素に設定されている*ByAccount*、ときに使用する集計関数が決定そのディメンションのメンバーを集計します。 **アカウント**要素は、1 つのアカウントの種類とそのようなメジャーで使用される集計関数を表します。  
  
 集計関数がによって使用される既定値と異なる場合は、勘定科目の種類を表示されている必要があります[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]各アカウントの種類。  
  
 有効な勘定科目の種類のセットは固定されています。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Account>します。  
  
## <a name="see-also"></a>参照  
 [Database 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
