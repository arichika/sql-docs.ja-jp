---
title: "Tablix データ領域に表示するデータの準備 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
caps.latest.revision: 5
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 5
---
# Tablix データ領域に表示するデータの準備 (レポート ビルダーおよび SSRS)
  Tablix データ領域には、データセットのデータが表示されます。 データセットに取得されたすべてのデータを表示することも、フィルターを作成してデータのサブセットのみを表示することもできます。 NULL 値に入力する条件式を追加したり、データセットのクエリを変更して既存の列の並べ替え順序を定義する列を含めることもできます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## NULL および空白のフィールド値の操作  
 データセット内のフィールド コレクションのデータには、実行時にデータ ソースから取得されたすべてのデータが含まれます。これには、NULL 値と空白の値も含まれます。 通常、NULL 値と空白の値は区別できませんが、 ほとんどの場合、この動作は適切です。 たとえば、[Sum](../../reporting-services/report-design/sum-function-report-builder-and-ssrs.md) や [Avg](../../reporting-services/report-design/avg-function-report-builder-and-ssrs.md) などの数値の集計関数では、NULL 値は無視されます。 詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)」を参照してください。  
  
 NULL 値を他の方法で処理する場合は、条件式またはカスタム コードを使用して、NULL 値をカスタム値で置き換えます。 たとえば、次の式は、フィールド `Null` に NULL 値がある場合にテキスト `[Size]` に置き換えます。  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリを使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] データ ソースからデータを取得する前にデータから NULL 値を削除する方法の詳細については、[SQL Server オンライン ブック](http://go.microsoft.com/fwlink/?linkid=120955)にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマニュアルの「NULL 値」および「NULL 値と結合」を参照してください。  
  
## NULL フィールド名の処理  
 フィールド自体がクエリ結果セット内に存在していれば、式で NULL 値のテストを行うことに問題はありません。 カスタム コードを使用して、実行時にデータ ソースから返されるコレクション フィールドにフィールド自体が存在するかどうかをテストできます。 詳細については、「[データセット フィールド コレクションの参照 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/dataset-fields-collection-references-report-builder-and-ssrs.md)」を参照してください。  
  
## [並べ替え順序] 列の追加  
 既定では、データセット フィールドの値をアルファベット順に並べ替えることができます。 別の順序で並べ替えるには、データ領域で目的の並べ替え順序を定義する新しい列をデータセットに追加します。 たとえば、フィールド `[Color]` を並べ替えて、白と黒のアイテムを最初に表示するには、次のクエリのように、列 `[ColorSortOrder]` を追加します。  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 この並べ替え順序に従ってテーブル データ領域を並べ替えるには、詳細グループの並べ替え式を `=Fields!ColorSortOrder.Value` に設定します。 詳細については、「[データ領域内のデータの並べ替え &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md)」を参照してください。  
  
## 参照  
 [データセット フィールド コレクション &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  