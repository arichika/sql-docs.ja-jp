---
title: "+ (連結) (SSIS 式) | Microsoft Docs"
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
  - "連結 [Integration Services]"
  - "+ (連結演算子)"
  - "連結演算子 (+)"
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
caps.latest.revision: 37
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 37
---
# + (連結) (SSIS 式)
  2 つの式を連結して 1 つの式にします。  
  
## 構文  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## 引数  
 *expression1、expression2*  
 データ型が DT_STR、DT_WSTR、DT_TEXT、DT_NTEXT、または DT_IMAGE である、任意の有効な式です。  
  
## 戻り値の型  
 DT_WSTR  
  
## 解説  
 この式では、DT_STR データ型および DT_WSTR データ型のいずれか一方、または両方を使用できます。  
  
 DT_STR データ型と DT_WSTR データ型を連結すると、DT_WSTR データ型の結果が返されます。 文字列の長さは、元の文字列の長さを文字数で表した値の合計です。  
  
 文字列データ型 DT_STR および DT_WSTR、または Binary Large Object Block (BLOB) データ型 DT_TEXT、DT_NTEXT、および DT_IMAGE のデータのみが連結できます。 その他のデータ型は、これらのデータ型のいずれかに明示的に変換してから連結する必要があります。 データ型間の有効なキャストの詳細については、「[Cast (SSIS 式)](../../integration-services/expressions/cast-ssis-expression.md)」を参照してください。  
  
 両方の式のデータ型は同じであるか、または一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 たとえば、文字列 "Order date is" と列 **OrderDate** を連結する場合、 **OrderDate** の値は暗黙的に文字列データ型に変換されます。 2 つの数値を連結するには、両方の数値を文字列データ型に明示的にキャストする必要があります。  
  
 BLOB データ型を連結する場合、DT_TEXT、DT_NTEXT、または DT_IMAGE のいずれか 1 つのみを連結できます。  
  
 要素のいずれかが NULL の場合、結果は NULL になります。  
  
 文字列リテラルは引用符で囲まれている必要があります。  
  
## 式の例  
 この例では、 **FirstName** 列と **LastName** 列の値を連結し、値の間にスペースを挿入します。  
  
```  
FirstName + ' ' + LastName  
```  
  
 この例では、変数 **ZIPCode** と変数 **ZIPCode+4** を連結します。 どちらの変数も文字列データ型です。 **ZIPCode+4** は、変数名にプラス記号 (+) が含まれているため、角かっこで囲む必要があります。  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## 参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 (SSIS 式)](../../integration-services/expressions/operators-ssis-expression.md)  
  
  