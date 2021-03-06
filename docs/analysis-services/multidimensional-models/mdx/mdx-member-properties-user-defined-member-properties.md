---
title: ユーザー定義メンバー プロパティ (MDX) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 77ae7cf92c9384b2be79048c860ef6a8b0476535
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-member-properties---user-defined-member-properties"></a>MDX メンバーのプロパティ - ユーザー定義メンバー プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  属性リレーションシップとして、ディメンション内の指定されたレベルにユーザー定義メンバー プロパティを追加できます。 ユーザー定義メンバー プロパティは、階層の **(All)** レベル、または階層そのものには追加できません。  
  
## <a name="creating-user-defined-member-properties"></a>ユーザー定義メンバー プロパティの作成  
 以下のように、ユーザー インターフェイスを使用して、またはプログラムによって、サーバー ベースのディメンションまたはキューブにユーザー定義メンバー プロパティを追加できます。  
  
-   ユーザー インターフェイスを使用してユーザー定義メンバー プロパティを追加するには、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]でディメンション デザイナーを使用します。 詳細については、「 [属性リレーションシップの定義](../../../analysis-services/multidimensional-models/attribute-relationships-define.md)」を参照してください。  
  
-   プログラムによってユーザー定義メンバー プロパティを追加するには、アプリケーションで Analysis Manager Objects (AMO) を使用するか、XML for Analysis (XMLA) と Analysis Services Scripting Language (ASSL) を組み合わせて使用できます。 詳細については、「 [属性リレーションシップ](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)」を参照してください。  
  
## <a name="retrieving-user-defined-member-properties"></a>ユーザー定義メンバー プロパティの取得  
 ユーザー定義メンバー プロパティを取得するには、 **PROPERTIES** キーワードまたは [Properties](../../../mdx/properties-mdx.md) 関数を使用できます。  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>PROPERTIES キーワードを使用したユーザー定義メンバー プロパティの取得  
 次に示すように、ユーザー定義メンバー プロパティを取得する構文は、固有レベル メンバー プロパティを取得する構文と同様です。  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 **PROPERTIES** キーワードは、軸を指定するセット式の後に指定します。 たとえば、次の MDX クエリの **PROPERTIES** キーワードは `List Price` および `Dealer Price` ユーザー定義メンバー プロパティを取得するもので、1 月に販売された製品を示すセット式の後に指定されています。  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>Properties 関数を使用したユーザー定義メンバー プロパティの取得  
 別の方法として、 **Properties** 関数を使ってカスタム メンバー プロパティにアクセスすることもできます。 たとえば、次の MDX クエリでは、**WITH** キーワードを使用して、`List Price` メンバー プロパティで構成される計算されるメンバーを作成します。  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 計算されるメンバーの作成方法の詳細については、「[MDX での計算されるメンバーの作成 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [メンバーのプロパティ & #40; を使用します。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [プロパティ & #40 です。MDX と #41 です。](../../../mdx/properties-mdx.md)  
  
  
