---
title: "|| (論理 OR) (SSIS 式) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "OR 演算子"
  - "論理 OR (||)"
  - "|| (論理 OR)"
ms.assetid: a3c07c09-f121-4187-9617-b01adcf843c4
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# || (論理 OR) (SSIS 式)
  論理 OR 演算を実行します。 一方または両方の条件が TRUE の場合、式は TRUE に評価されます。  
  
## 構文  
  
```  
  
boolean_expression1 || boolean_expression2  
```  
  
## 引数  
 *boolean_expression1, boolean_expression2*  
 TRUE、FALSE、または NULL に評価される、任意の有効な式です。  
  
## 戻り値の型  
 DT_BOOL  
  
## 解説  
 次の表は、|| 演算子の結果を示します。  
  
|結果|式|式|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|TRUE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|TRUE|NULL|TRUE|  
|NULL|NULL|FALSE|  
  
## SSIS 式の例  
 この例では、 **StandardCost** 列と **ListPrice** 列を使用しています。 **StandardCost** 列の値が 300 より小さいか、または **ListPrice** 列の値が 500 より大きい場合、式は TRUE に評価されます。  
  
```  
StandardCost < 300 || ListPrice > 500  
```  
  
 この例では、数値リテラルの代わりに変数 **SPrice** と **LPrice** を使用しています。  
  
```  
StandardCost < @SPrice || ListPrice > @LPrice  
```  
  
## 参照  
 [&#124; &#40;ビット演算包含的 OR&#41; &#40;SSIS 式&#41;](../../integration-services/expressions/bitwise-inclusive-or-ssis-expression.md)   
 [^ &#40;ビット演算子排他的 OR&#41; &#40;SSIS 式&#41;](../../integration-services/expressions/bitwise-exclusive-or-ssis-expression.md)   
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  