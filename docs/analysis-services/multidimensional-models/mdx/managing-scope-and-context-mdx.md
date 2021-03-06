---
title: スコープとコンテキスト (MDX) の管理 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1656ac98555d4377ec70c37a43b70217b9be759c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="managing-scope-and-context-mdx"></a>スコープとコンテキストの管理 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] では、多次元式 (MDX) スクリプトをキューブ全体に適用することも、スクリプト実行の特定の時点でキューブの特定の部分に適用することもできます。 MDX スクリプトは、計算パスを使用することにより、階層化されたアプローチでキューブ内の計算を実行することができます。  
  
> [!NOTE]  
>  計算パスが計算に及ぼす影響の詳細については、「[パス順序と解決順序の概要 (MDX)](../../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md)」をご覧ください。  
  
 MDX スクリプト内の計算パス、スコープ、およびコンテキストを制御するための具体的な方法は、CALCULATE ステートメント、**This** 関数、および SCOPE ステートメントを使用することです。  
  
## <a name="using-the-calculate-statement"></a>CALCULATE ステートメントの使用  
 CALCULATE ステートメントは、キューブ内の各セルに集計データを格納します。 たとえば、既定の MDX スクリプトの冒頭には、単一の CALCULATE ステートメントが置かれています。  
  
 CALCULATE ステートメントの構文の詳細については、「[CALCULATE ステートメント (MDX)](../../../mdx/mdx-scripting-calculate.md)」をご覧ください。  
  
> [!NOTE]  
>  スクリプトの中で CALCULATE ステートメントが SCOPE ステートメントに入れられている場合、MDX は CALCULATE ステートメントの評価を、キューブ全体に対してではなく、SCOPE ステートメントで定義されるサブキューブのコンテキストの中で行います。  
  
## <a name="using-the-this-function"></a>This 関数の使用  
 **This** 関数により、MDX スクリプトの中で現在のサブキューブを取得できます。 **This** 関数を使用すると、現在のサブキューブの中のセルの値を MDX 式にすばやく設定できます。 **This** 関数を SCOPE ステートメントと併用して、特定の計算パスの間に特定のサブキューブの内容を変更することもできます。  
  
> [!NOTE]  
>  スクリプトの中で **This** 関数が SCOPE ステートメントに入れられている場合、MDX は **This** 関数の評価を、キューブ全体に対してではなく、SCOPE ステートメントで定義されるサブキューブのコンテキストの中で行います。  
  
### <a name="this-function-example"></a>This 関数の例  
 次の MDX スクリプト コマンドの例では、**This** 関数を使用することにより、[!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] サンプル キューブにおいて、Customer ディメンションの Redmond メンバーの子に関して、Finance メジャー グループの Amount メジャーの値を 10% 増加させます。  
  
```  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 **This** 関数の構文の詳細については、「[This (MDX)](../../../mdx/this-mdx.md)」を参照してください。  
  
## <a name="using-the-scope-statement"></a>SCOPE ステートメントの使用  
 SCOPE ステートメントは、MDX スクリプト内の他の MDX 式およびステートメントが入っている現在のサブキューブを定義し、その MDX 式およびステートメントのスコープを指定します。 MDX は、このような他の MDX 式およびステートメント ( **This** 関数および CALCULATE ステートメントを含む) の評価を、サブキューブのコンテキストの中で行います。  
  
 SCOPE ステートメントは動的ですが、反復的な性質はありません。 SCOPE ステートメントに入っているステートメントは 1 回だけ実行されますが、サブキューブ自体は動的に決定されます。 たとえば、SampleCube というキューブがあるとします。 SampleCube キューブに対して以下の SCOPE ステートメントを適用し、コンテキストを Measures ディメンション内の ALLMEMBERS に定義するサブキューブを定義します。  
  
 `SCOPE([Measures].ALLMEMBERS);`  
  
 `THIS = [Measures].ALLMEMBERS.COUNT;`  
  
 `END SCOPE;`  
  
 この SCOPE ステートメント内のステートメントと式は 1 回だけ実行されます。  
  
 今度は、あるビジネス ユーザーが、ExistingMeasure という 1 つのメジャーが含まれている以下の MDX クエリを、SampleCube キューブに対して実行します。  
  
 `WITH MEMBER [Measures].[NewMeasure] AS '1'`  
  
 `SELECT`  
  
 `[Measures].ALLMEMBERS ON COLUMNS,`  
  
 `[Customer].DEFAULTMEMBER ON ROWS`  
  
 `FROM`  
  
 `[SampleCube]`  
  
 クエリは、以下の表に示す出力のようなセル セットを返します。  
  
||[ExistingMeasure]|[NewMeasure]|  
|-|-------------------------|--------------------|  
|[Customer].[All]|2|2|  
  
 返されたセル セットを見て、MDX スクリプトの SCOPE ステートメントに含まれている ExistingMeasure 値が、NewMeasure メジャーが定義された後で、どのように動的に更新されるかに注目してください。  
  
 SCOPE ステートメントを別の SCOPE ステートメント内で入れ子にすることができます。 しかし、SCOPE ステートメントは反復的でないので、SCOPE ステートメントを入れ子にする主な目的は、特別な処理のためにサブキューブをさらに細かく分割することです。  
  
### <a name="scope-statement-example"></a>SCOPE ステートメントの例  
 次の MDX スクリプトの例では、SCOPE ステートメントを使用することにより、 [!INCLUDE[ssAWDWsp](../../../includes/ssawdwsp-md.md)] サンプル キューブにおいて、Customer ディメンションの Redmond メンバーの子に関して、Finance メジャー グループの Amount メジャーの値を 10% 大きく設定します。 しかし、別の SCOPE ステートメントにより、2002 年の子の Amount メジャーが含まれるようにサブキューブが変更されます。 最終的に、Amount メジャーはこのサブキューブに関してのみ集計され、他の年の Amount メジャーの値は集計されません。  
  
```  
/* Calculate the entire cube first. */  
CALCULATE;  
/* This SCOPE statement defines the current subcube */  
SCOPE([Customer].&[Redmond].MEMBERS,   
    [Measures].[Amount], *);  
        /* This expression sets the value of the Amount measure */  
        THIS = [Measures].[Amount] * 1.1;  
END SCOPE;  
```  
  
 SCOPE ステートメントの構文の詳細については、「[SCOPE ステートメント (MDX)](../../../mdx/mdx-scripting-scope.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス & #40 です。MDX と #41 です。](../../../mdx/mdx-language-reference-mdx.md)   
 [基本的な MDX スクリプト & #40 です。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
