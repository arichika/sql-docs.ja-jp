---
title: "マイニング モデルへのフィルターの適用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/19/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "モデル フィルター [データ マイニング]"
  - "フィルター [データ マイニング]"
  - "入力行のフィルター選択 [Analysis Services]"
  - "データのフィルター選択 [Analysis Services]"
ms.assetid: 4d0abeb5-e939-46d3-9097-6e0358244300
caps.latest.revision: 18
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 17
---
# マイニング モデルへのフィルターの適用
  入れ子になったテーブルがマイニング構造に含まれている場合は、ケース テーブル、入れ子になったテーブル、またはその両方にフィルターを適用できます。  
  
 次の手順は、ケース フィルター、入れ子になったテーブル行に適用するフィルターの両方を作成する方法を示しています。  
  
 ケース テーブルの条件は、収入が 30000 ～ 40000 である顧客に限定することです。 入れ子になったテーブルの条件は、特定の品目を購入していない顧客に限定することです。  
  
 この例で作成された、完全なフィルター条件は次のとおりです。  
  
```  
[Income] > '30000'   
AND  [Income] < '40000'   
AND EXISTS (SELECT * FROM [<nested table name>]   
WHERE [Model] <> 'Water Bottle' )   
```  
  
### マイニング モデルに対してケース フィルターを作成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のソリューション エクスプローラーで、フィルターを適用するマイニング モデルが含まれているマイニング構造をクリックします。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  モデルを選択し、右クリックしてショートカット メニューを開きます。  
  
     または  
  
     モデルを選択します。 次に、**[マイニング モデル]** メニューの **[モデル フィルターの設定]** をクリックします。  
  
4.  **[モデル フィルター]** ダイアログ ボックスで、**[マイニング構造列]** ボックスのグリッドの先頭行をクリックします。  
  
5.  データ ソースに 1 つのフラット テーブルが含まれる場合、ドロップダウン リストには該当のテーブルの列名のみが表示されます。  
  
     マイニング構造に複数のテーブルが含まれる場合、リストにはソース テーブルの名前が示されます。 テーブルを選択するまで列名は表示されません。  
  
     マイニング構造にケース テーブルと入れ子になったテーブルが含まれる場合は、ドロップダウン リストにケース テーブルの列、入れ子になったテーブルの名前が表示されます。  
  
6.  ドロップダウン リストから列を選択します。  
  
     テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルであるか列であるかが示されます。  
  
7.  **[演算子]** ボックスをクリックし、一覧から演算子を選択します。 有効な演算子は、選択した列のデータ型によって変わります。  
  
8.  **[値]** ボックスをクリックし、ボックスに値を入力します。  
  
     たとえば、列に **[Income]** を選択して、"次の値より大きい" 演算子 (>) を選択し、「**30000**」と入力します。  
  
9. グリッドの次の行をクリックします。  
  
     作成したフィルター条件が [式] ボックスに自動的に追加されます。 例を次に示します。 `[Income] > '30000'`  
  
10. グリッドの次の行の **[ルールの適用条件]** ボックスをクリックし、条件を追加します。  
  
     たとえば、BETWEEN 条件を作成するには、論理演算子のドロップダウン リストから **[AND]** を選択します。  
  
11. 演算子を選択し、手順 7. と手順 8. に示したように値を入力します。  
  
     たとえば、列に再度 **[Income]** を選択して、"次の値より小さい" 演算子 (<) を選択し、「**40000**」と入力します。  
  
12. グリッドの次の行をクリックします。  
  
13. [式] ボックスのフィルター条件が自動的に更新され、新しい条件が追加されます。 完成した式は次のようになります。 `[Income] > '30000'AND [Income] < '40000'`  
  
### マイニング モデルの入れ子になったテーブルにフィルターを追加するには  
  
1.  **[\<name> モデル フィルター]** ダイアログ ボックスで、**[マイニング構造列]** の下のグリッドの空の行をクリックします。  
  
2.  ドロップダウン リストから、入れ子になったテーブルの名前を選択します。  
  
     テキスト ボックスの左側のアイコンが変化して、選択されたアイテムがテーブルの名前であることが示されます。  
  
3.  **[演算子]** ボックスをクリックし、**[次の値を含む]** または **[次の値を含まない]** を選択します。  
  
     ケース テーブルでは入れ子になったテーブルの特定の値を含むケースのみに制限しているため、**[モデル フィルター]** ダイアログ ボックスで入れ子になったテーブルに対して選択できる条件はこれだけです。 次の手順で入れ子になったテーブルの条件に値を設定します。  
  
4.  **[値]** ボックスをクリックし、(**[...]**) ボタンをクリックして式を作成します。  
  
     **[\<name> フィルター]** ダイアログ ボックスが開きます。 このダイアログ ボックスでは、現在のテーブルにのみ条件を設定できます。ここでは、入れ子になったテーブルです。  
  
5.  **[マイニング構造列]** ボックスをクリックし、入れ子になったテーブル列のドロップダウン リストから列名を選択します。  
  
6.  **[演算子]** をクリックし、列に対して有効な演算子の一覧から演算子を選択します。  
  
7.  **[値]** をクリックし、値を入力します。  
  
     たとえば、**[マイニング構造列]** には、**[モデル]** を選択します。 **[演算子]** には、**<>** を選択し、「**Water Bottle**」という値を入力します。 この条件で次のフィルター式が作成されます。  
  
```  
EXISTS (SELECT * FROM [<nested table name>] WHERE [Model] <> 'Water Bottle' )   
```  
  
> [!NOTE]  
>  入れ子になったテーブルの属性数に制限はないため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では選択できる値の一覧を表示しません。 値を正確に入力する必要があります。 また、入れ子になったテーブルに LIKE 演算子を使用することはできません。  
  
1.  必要に応じて、さらに条件を追加します。**[条件]** グリッドの左側にある **[ルールの適用条件]** ボックスで **AND** または **OR** を選択して、条件を結合します。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
2.  **[モデル フィルター]** ダイアログ ボックスで、**[フィルター]** ダイアログ ボックスを使用して作成した条件を確認します。 入れ子になったテーブルの条件は、ケース テーブルの条件に追加され、フィルター条件の完全なセットは **[式]** ボックスに表示されます。  
  
3.  必要に応じて、**[クエリの編集]** をクリックして、フィルター式を手動で変更できます。  
  
    > [!NOTE]  
    >  フィルター式の一部を手動で変更すると、グリッドが無効になり、その後はテキスト編集モードでしかフィルター式を操作できなくなります。 グリッド編集モードに戻すには、フィルター式を消去して最初からやり直す必要があります。  
  
4.  
  
## 参照  
 [マイニング モデルのフィルター (Analysis Services - データ マイニング)](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [マイニング モデル タスクと操作方法](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [マイニング モデルからのフィルターの削除](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  