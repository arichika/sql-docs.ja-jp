---
title: "? : (条件) (SSIS 式) | Microsoft Docs"
ms.custom: 
  - "ssisdev020617"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "条件演算子 (?:)"
  - "?: (条件演算子)"
ms.assetid: d38e6890-7338-4ce0-a837-2dbb41823a37
caps.latest.revision: 49
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 49
---
# ? : (条件) (SSIS 式)
  ブール式の評価に基づいて 2 つの式のうちのいずれかの式を返します。 ブール式が TRUE に評価された場合、最初の式が評価対象となり、その結果が式の結果になります。 ブール式が FALSE に評価された場合、2 番目の式が評価対象となり、その結果が式の結果になります。  
  
## 構文  
  
```  
  
boolean_expression?expression1:expression2  
  
```  
  
## 引数  
 *boolean_expression*  
 TRUE、FALSE、または NULL に評価される、任意の有効な式です。  
  
 *expression1*  
 有効な式を指定します。  
  
 *expression2*  
 有効な式を指定します。  
  
## 戻り値の型  
 *expression1* または *expression2* のデータ型です。  
  
## 解説  
 *boolean_expression* が NULL に評価された場合、式の結果は NULL になります。 選択された式 (*expression1* または *expression2* のいずれか) が NULL の場合、結果は NULL になります。 選択された式が NULL でなく、選択されていない式が NULL の場合、結果は選択された式の値になります。  
  
 *expression1* と *expression2* のデータ型が同じ場合、結果はそのデータ型になります。 次の追加のルールが結果の型に適用されます。  
  
-   DT_TEXT データ型の場合、*expression1* と *expression2* のコード ページが同じである必要があります。  
  
-   DT_BYTES データ型の場合、結果の長さは、長いほうの引数の長さと同じです。  
  
 式セットである *expression1* および *expression2* は、有効なデータ型および次のルールのいずれかに従って評価される必要があります。  
  
-   **数値** *expression1* と *expression2* の両方が数値データ型である必要があります。 データ型の積集合は、式エバリュエーターが実行する暗黙的な数値変換に関する規則で指定されているように、数値データ型である必要があります。 2 つの数値データ型の積集合を NULL にすることはできません。 詳細については、「[式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」を参照してください。  
  
-   **文字列** *expression1* と *expression2* は、どちらも DT_STR または DT_WSTR の文字列データ型である必要があります。 2 つの式が評価される文字列データ型は、異なっていてもかまいません。 DT_WSTR データ型の結果の長さは、長いほうの引数の長さと同じです。  
  
-   **日付、時刻、または日付/時刻** *expression1* と *expression2* は、どちらも DT_DBDATE、DT_DATE、DT_DBTIME、DT_DBTIME2、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、DT_DBTIMESTAPMOFFSET、または DT_FILETIME のいずれかのデータ型に評価される必要があります。  
  
    > [!NOTE]  
    >  時刻データ型に評価される式と、日付データ型または日付/時刻データ型に評価される式との間の比較はサポートされていません。 システムによってエラーが生成されます。  
  
     式の比較の際は、次の変換規則が記載順に適用されます。  
  
    -   2 つの式が同じデータ型に評価される場合、そのデータ型の比較が実行されます。  
  
    -   一方の式が DT_DBTIMESTAMPOFFSET データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMPOFFSET に変換され、DT_DBTIMESTAMPOFFSET の比較が実行されます。 詳細については、「[式における Integration Services データ型](../../integration-services/expressions/integration-services-data-types-in-expressions.md)」を参照してください。  
  
    -   一方の式が DT_DBTIMESTAMP2 データ型の場合、もう一方の式が暗黙的に DT_DBTIMESTAMP2 に変換され、DT_DBTIMESTAMP2 の比較が実行されます。  
  
    -   一方の式が DT_DBTIME2 データ型の場合、もう一方の式が暗黙的に DT_DBTIME2 に変換され、DT_DBTIME2 の比較が実行されます。  
  
    -   一方の式が DT_DBTIMESTAMPOFFSET、DT_DBTIMESTAMP2、DT_DBTIME2 のいずれの型でもない場合、両方の式が DT_DBTIMESTAMP データ型に変換されてから比較が実行されます。  
  
     式の比較は、次の前提に基づいて実行されます。  
  
    -   それぞれの式のデータ型に秒の小数部が含まれている場合、秒の小数部の桁数が最も少ないデータ型の残りの桁の値は 0 と見なされます。  
  
    -   それぞれの式が日付データ型であり、一方のみにタイム ゾーン オフセットがある場合、タイム ゾーン オフセットがない日付データ型は協定世界時 (UTC) と見なされます。  
  
 データ型の詳細については、「[Integration Services のデータ型](../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
## 式の例  
 この例では、条件に応じて `savannah` または `unknown` に評価される式を示しています。  
  
```  
@AnimalName == "Elephant"? "savannah": "unknown"  
```  
  
 この例では、**ListPrice** 列を参照する式を示しています。 **ListPrice** のデータ型は DT_CY です。 式は **ListPrice** に .2 または .1 のどちらかを条件に応じて乗算します。  
  
```  
ListPrice < 350.00 ? ListPrice * .2 : ListPrice * .1  
```  
  
## 参照  
 [演算子の優先順位と結合規則](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [演算子 &#40;SSIS 式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  