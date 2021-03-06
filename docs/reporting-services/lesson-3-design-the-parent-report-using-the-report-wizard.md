---
title: 'レッスン 3: レポート ウィザードを使用して親レポートを設計する | Microsoft Docs'
ms.custom: ''
ms.date: 05/18/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: reporting-services
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 2f69dcd3-cd6d-45a9-a62a-ba6f5f3179d8
caps.latest.revision: 9
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 50b71b71dbd7f81fca61224071a098e1d6fcf4dc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-3-design-the-parent-report-using-the-report-wizard"></a>レッスン 3: レポート ウィザードを使用して親レポートを設計する
親レポートのデータ接続とデータ テーブルを作成した後は、レポート デザイナーのレポート ウィザードを使用して親レポートを設計します。 レポート デザイナーの詳細については、「[レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)」を参照してください。  
  
### <a name="to-design-the-parent-report-using-the-report-wizard"></a>レポート ウィザードを使用して親レポートを設計するには  
  
1.  **ソリューション エクスプローラー**でトップレベル Web サイトが選択されていることを確認します。  
  
2.  Web サイトを右クリックし、 **[新しい項目の追加]** を選択します。  
  
3.  **[新しい項目の追加]** ダイアログ ボックスで、 **[レポート ウィザード]** を選択します。レポート ファイルの名前を入力し、 **[追加]** を選択します。  
  
    これにより、レポート ウィザードが起動します。  
  
4.  **[データセットのプロパティ]** ページの **[データ ソース]** ボックスで、「 **レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する** 」で作成した [DataSet1](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)を選択します。  
  
    上の手順で作成した **DataTable** で **[使用できるデータセット]** ボックスが自動的に更新されます。  
  
5.  **[次へ]** を選択します。  
  
6.  **[フィールドの配置]** ページで、次の操作を行います。  
  
    1.  **[ProductID]**、 **[Name]**、 **[ProductNumber]**、 **[SafetyStockLevel]**、および **[ReorderLevel]** を、 **[使用できるフィールド]** から **&gt;[値]** ボックスにドラッグします。  
  
    2.  **[Sum(ProductID)]**、 **[Sum(SafetyStockLevel)]**、 **[Sum(ReorderLevel)]** の横の矢印を選択して、 **[Sum]** の選択を解除します。  
  
7.  **[次へ]** を 2 回選択し、 **[完了]** を選択して **レポート ウィザード**を閉じます。  
  
    これで、.rdlc ファイルが作成されました。 このファイルはレポート デザイナーで開くことができます。 設計した Tablix がデザイン画面に表示されます。  
  
8.  .rdlc ファイルを保存します。  
  
## <a name="next-task"></a>次の作業  
これで、レポート ウィザードを使用して親レポートを設計できました。 次は、子レポートのデータ接続とデータ テーブルを作成します。 「 [レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)」を参照してください。  
  
  
  

