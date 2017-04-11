---
title: "テーブル、列、または行のフィルターのマッピングの変更 (SSAS テーブル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2124c526-5772-4f84-a019-9dd3e906e8dd
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# テーブル、列、または行のフィルターのマッピングの変更 (SSAS テーブル)
  このトピックでは、[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] の **[テーブルのプロパティの編集]** ダイアログ ボックスを使用して、テーブル、列、または行のフィルターのマッピングを変更する方法について説明します。  
  
 **[テーブルのプロパティの編集]** ダイアログ ボックスのオプションは、最初にデータをインポートしたときに一覧からテーブルを選択したか SQL クエリを使用したかによって異なります。 最初にデータをインポートするときに一覧から選択した場合は、**[テーブルのプロパティの編集]** ダイアログ ボックスにテーブルのプレビュー モードが表示されます。 このモードでは、ソース テーブルの最初の 50 行に制限されたサブセットのみが表示されます。 最初にデータをインポートするときに SQL ステートメントを使用した場合は、**[テーブルのプロパティの編集]** ダイアログ ボックスには SQL ステートメントのみが表示されます。 SQL クエリ ステートメントを使用すると、フィルターをデザインするか、SQL ステートメントを手動で編集することによって、行のサブセットを取得することもできます。  
  
 現在のテーブルと異なる列を持つテーブルにソースを変更すると、列が異なることを示す警告メッセージが表示されます。 現在のテーブルに含める列を選択し、 **[保存]**をクリックします。 テーブルの左側にあるチェック ボックスをオンにすると、テーブル全体を置換できます。  
  
> [!NOTE]  
>  テーブルに複数のパーティションがある場合、[テーブルのプロパティの編集] ダイアログ ボックスを使用して、行のフィルターのマッピングを変更することはできません。 複数のパーティションを持つテーブルについて行のフィルターのマッピングを変更するには、パーティション マネージャーを使用します。 詳細については、「[パーティション (SSAS テーブル)](../../analysis-services/tabular-models/partitions-ssas-tabular.md)」を参照してください。  
  
#### テーブル、列、または行のフィルターのマッピングを変更するには  
  
1.  モデル デザイナーでテーブルをクリックし、**[テーブル]** メニュー、**[テーブルのプロパティ]** の順にクリックします。  
  
2.  **[テーブルのプロパティの編集]** ダイアログ ボックスで、フィルターの基準とする条件を含む列を見つけ、列見出しの右側にある下矢印をクリックします。  
  
3.  **[オートフィルター]** メニューで次のいずれかの操作を行います。  
  
    -   列の値の一覧で、フィルター処理の基準にする 1 つ以上の値を選択するか、選択を解除し、[OK] をクリックします。  
  
         値の数が極端に多い場合、個々のアイテムが一覧に表示されないことがあります。 その場合は、"アイテムが多すぎるため、表示できません" というメッセージが表示されます。  
  
    -   列の種類に応じて **[数値フィルター]** または **[テキスト フィルター]** をクリックし、比較演算子コマンド ([等しい] など) のいずれかをクリックするか、[カスタム フィルター] をクリックします。 **[カスタム フィルター]** ダイアログ ボックスで、フィルターを作成し、 **[OK]**をクリックします。  
  
         設定を間違ったため最初からやり直す場合は、**[行フィルターのクリア]** をクリックします。  
  
## 参照  
 [[テーブルのプロパティの編集] ダイアログ ボックス (SSAS)](../Topic/Edit%20Table%20Properties%20Dialog%20Box%20\(SSAS\).md)  
  
  