---
title: クエリ軸 (MDX) の内容を指定する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bceafa9fb8ddd89162deca105404c317001a86bb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-query-and-slicer-axes---specify-the-contents-of-a-query-axis"></a>MDX クエリ軸とスライサー軸、クエリ軸の内容を指定します。
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  クエリ軸は、多次元式 (MDX) の SELECT ステートメントから返されるセル セットの範囲を指定します。 セル セットの範囲を指定することで、返されるデータのうち、クライアントで表示するデータを限定できます。  
  
 クエリ軸を指定するには、 `<SELECT query axis clause>` を使用して特定のクエリ軸にセットを割り当てます。 それぞれの `<SELECT query axis clause>` の値によって、1 つのクエリ軸を定義します。 データセットの軸の数は、SELECT ステートメントの `<SELECT query axis clause>` 値の数と同じです。  
  
## <a name="query-axis-syntax"></a>クエリ軸の構文  
 `<SELECT query axis clause>`の構文は以下のとおりです。  
  
```  
  
<SELECT query axis clause> ::=  
   [ NON EMPTY ] Set_Expression [ <SELECT dimension property list clause> ] [<HAVING clause>]  
   ON {  
      Integer_Expression |   
      AXIS( Integer_Expression ) |   
      {COLUMNS | ROWS | PAGES | SECTIONS | CHAPTERS}     
      }  
  
```  
  
 各クエリ軸には番号が付いており、0 は X 軸、1 は Y 軸、2 は Z 軸のようになっています。 `<SELECT query axis clause>`の構文では、 `Integer_Expression` の値によって軸の番号を指定します。 MDX クエリでは、最大 128 個まで軸を指定できます。ただし、5 つを超える軸を使用する MDX クエリはほとんどありません。 最初の 5 つの軸については、COLUMNS、ROWS、PAGES、SECTIONS、CHAPTERS という別名を使用することも可能です。  
  
 MDX クエリは、クエリ軸をスキップできません。 つまり、1 つ以上のクエリ軸を含むクエリでは、番号の小さい方の軸または中間の軸を除外できません。 たとえば、クエリで COLUMNS 軸を除外して ROWS 軸を指定することや、ROWS 軸を除外して COLUMNS 軸と PAGES 軸を指定することはできません。  
  
 ただし、軸を指定しない SELECT 句、つまり空の SELECT 句は指定できます。 この場合、すべてのディメンションがスライサー ディメンションになり、MDX クエリは 1 つのセルを選択します。  
  
 上記のクエリ軸の構文では、 `Set_Expression` の値によって、クエリ軸の内容を定義するセットを指定します。 セットの詳細については、「[メンバー、組、およびセットの操作 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の単純な SELECT ステートメントは、COLUMNS 軸で Internet Sales Amount メジャーを返し、MDX の MEMBERS 関数を使って、ROWS 軸で Date ディメンションの Calendar 階層のすべてのメンバーを返します。  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 以下の 2 つのクエリは、まったく同じ結果を返しますが、軸の別名ではなく番号を使用する方法を示しています。  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON 0,  
{[Date].[Calendar].MEMBERS} ON 1  
FROM [Adventure Works]  
  
SELECT {[Measures].[Internet Sales Amount]} ON AXIS(0),  
{[Date].[Calendar].MEMBERS} ON AXIS(1)  
FROM [Adventure Works]  
  
```  
  
 セットの定義の前に NON EMPTY キーワードを使用すると、軸からすべての空の組を簡単に削除できます。 たとえば、これまでの例では、キューブ内に 2004 年 8 月以降のデータがありませんでした。 どの列にもデータがないすべての行をセルセットから削除するには、ROWS 軸のセットの定義の前に、以下のように NON EMPTY を追加します。  
  
```  
SELECT {[Measures].[Internet Sales Amount]} ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].MEMBERS} ON ROWS  
FROM [Adventure Works]  
  
```  
  
 NON EMPTY は、クエリのすべての軸で使用できます。 以下の 2 つのクエリの結果を比較してみましょう。最初のクエリは NON EMPTY を使っておらず、2 番目のクエリでは両方の軸で使用しています。  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
SELECT NON EMPTY {[Measures].[Internet Sales Amount]}   
* [Promotion].[Promotion].[Promotion].MEMBERS  
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Calendar Year].MEMBERS} ON ROWS  
FROM [Adventure Works]  
WHERE([Product].[Subcategory].&[19])  
  
```  
  
 軸の内容を特定の条件に基づいてフィルター選択するために、HAVING 句を使用できます。FILTER 関数のような、同じ結果が得られる他の方法ほど柔軟性がありませんが、使用方法が簡単です。 次の例は、Internet Sales Amount が 15,000 ドルより大きい日付だけを返します。  
  
```  
SELECT {[Measures].[Internet Sales Amount]}   
ON COLUMNS,  
NON EMPTY  
{[Date].[Calendar].[Date].MEMBERS}   
HAVING [Measures].[Internet Sales Amount]>15000  
ON ROWS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [スライサー軸 & #40; の内容の指定MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)  
  
  
