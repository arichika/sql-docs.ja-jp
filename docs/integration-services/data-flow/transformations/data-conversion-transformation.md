---
title: "データ変換の変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontrans.f1"
helpviewer_keywords: 
  - "データ型の変換 [Integration Services]"
  - "データ変換の変換"
  - "データ型 [Integration Services]、変換"
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 53
---
# データ変換の変換
  データ変換の変換は、入力列のデータを別のデータ型に変換し、新しい出力列にコピーします。 たとえば、パッケージで複数の変換元のデータを抽出し、この変換を使用して、列を変換先のデータ ストアで要求されるデータ型に変換できます。 1 つの入力列に複数の変換を適用できます。  
  
 この変換を使用すると、パッケージで次の種類のデータ変換を実行できます。  
  
-   データ型を変更します。 詳細については、「 [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
    > [!NOTE]  
    >  date データ型または datetime データ型にデータを変換する場合、ロケール設定で別の形式が指定されている場合でも、出力列の日付は ISO 形式になります。  
  
-   文字列データの列の長さ、および数値データの有効桁数と小数点以下桁数を設定します。 詳しくは、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」をご覧ください。  
  
-   コード ページを指定します。 詳しくは、「 [Comparing String Data](../../../integration-services/data-flow/comparing-string-data.md)」をご覧ください。  
  
    > [!NOTE]  
    >  文字列データ型の 2 つの列間でコピーを行う場合、それらの列のコード ページは同じである必要があります。  
  
 文字列データの出力列の長さが、対応する入力列の長さよりも短い場合、出力データは切り捨てられます。 詳しくは、「[データのエラー処理](../../../integration-services/data-flow/error-handling-in-data.md)」をご覧ください。  
  
 この変換は、1 つの入力、1 つの出力、および 1 つのエラー出力をとります。  
  
## 関連タスク  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。 SSIS デザイナーでデータ変換の変換を使用する方法については、「[データ変換の変換を使用してデータを別のデータ型に変換する](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)」および「[[データ変換変換エディター]](../../../integration-services/data-flow/transformations/data-conversion-transformation-editor.md)」をご覧ください。 プログラムによるこの変換のプロパティの設定については、「[共通プロパティ](../Topic/Common%20Properties.md)」および「[変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)」をご覧ください。  
  
## 関連コンテンツ  
 blogs.msdn.com のブログ「 [SSIS 2008 のデータ型の変換手法間のパフォーマンス比較](http://go.microsoft.com/fwlink/?LinkId=220823)」  
  
## 参照  
 [高速解析](../Topic/Fast%20Parse.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  