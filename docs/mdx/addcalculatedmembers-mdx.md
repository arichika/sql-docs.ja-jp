---
title: AddCalculatedMembers (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 18ccf4ad808c15945d82f1ca05616f0da878a7ca
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739391"
---
# <a name="addcalculatedmembers-mdx"></a>AddCalculatedMembers (MDX)


  計算されるメンバーを指定されたセットに追加して生成したセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
AddCalculatedMembers(Set_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>コメント  
 既定では、セット関数を解決する際、計算されるメンバーは除外されます。 **AddCalculatedMembers**関数がで指定されたセット式を調べ*Set_Expression、* スコープ内に含まれるメンバーの兄弟である計算されるメンバーが含まれていますとそのセット式のです。  
  
> [!NOTE]  
>  この関数で使用できるのは、1 次元のセット式だけです。  
  
## <a name="examples"></a>使用例  
 この関数の使用例を以下に示します。  
  
```  
-- This query returns the calculated members for the cube  
-- by retrieving all members, and then excluding non-calculated members.  
SELECT   
   AddCalculatedMembers(  
      {[Measures].Members}  
      )-[Measures].Members ON COLUMNS  
FROM [Adventure Works]   
```  
  
 次の例を返します、`Measures.[Unit Price]`内のすべての計算されるメンバーだけでなく、メンバー、**メジャー**ディメンションから、 **Adventure Works**キューブ。  
  
```  
SELECT  
   AddCalculatedMembers({Measures.[Unit Price]}) ON COLUMNS  
FROM   
   [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
