---
title: XOR (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9115fc1e226e05c788206706d59a5435bfd1c5d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743851"
---
# <a name="xor-mdx"></a>XOR (MDX)


  2 つの数値式の排他的論理和演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Expression1 XOR Expression2  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Expression1*  
 数値を返す有効な多次元式 (MDX) 式です。  
  
 *Expression2*  
 数値を返す有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 ブール値を返す**true**に、1 つの引数が評価された場合**true**、それ以外の**false**です。  
  
## <a name="remarks"></a>コメント  
 **XOR**演算子はブール値として両方のパラメーターを処理 (つまり、0 として**false**、それ以外の**true**) 排他的論理和を実行します。 次の表に示しますが、どのように**XOR**論理和を実行します。  
  
|*Expression1*|*Expression2*|戻り値|  
|-------------------|-------------------|------------------|  
|**true**|**true**|**false**|  
|**true**|**false**|**true**|  
|**false**|**true**|**true**|  
|**false**|**false**|**false**|  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
