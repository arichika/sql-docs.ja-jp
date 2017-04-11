---
title: "Customize the Parameters Pane in a Report (Report Builder) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ce9e8d5-911a-4422-928f-a8d005b79fc6
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 8
---
# Customize the Parameters Pane in a Report (Report Builder)
  レポート ビルダーでパラメーターを使用して改ページ調整されたレポートを作成するときに、パラメーター ペインをカスタマイズできます。 レポート デザイン ビューで、パラメーター ペインの特定の列や行にパラメーターをドラッグできます。 列を追加または削除して、ペインのレイアウトを変更することもできます。  
  
 ペイン内で新しい列や行にパラメーターをドラッグすると、 **レポート データ** ペインのパラメーターの順序が変わります。 **レポート データ** ペインでパラメーターの順序を変更すると、ペインでのパラメーターの位置が変わります。 パラメーターの順序が重要である理由の詳細については、「[レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。  
  
## パラメーター ペインをカスタマイズするには  
  
1.  **[ビュー]** タブで **[パラメーター]** チェック ボックスをオンにして、パラメーター ペインを表示します。  
  
     ![Access parameters pane from View tab](../../reporting-services/report-design/media/ssrs-customparameter-accessparameterpanedesignmode.png "Access parameters pane from View tab")  
  
     デザイン画面の上部にペインが表示されます。  
  
2.  ペインにパラメーターを追加するには、次のいずれかの操作を行います。  
  
    -   パラメーター ペインで空のセルを右クリックし、 **[パラメーターの追加]**をクリックします。  
  
         ![Add new parameter from parameters pane](../../reporting-services/report-design/media/ssrs-customizeparameter-addnewparameter.png "Add new parameter from parameters pane")  
  
    -   **レポート データ** ペインの **[パラメーター]** を右クリックし、**[パラメーターの追加]** をクリックします。  
  
3.  パラメーターをパラメーター ペインの新しい場所に移動するには、ペインの異なるセルにパラメーターをドラッグします。  
  
     ペインでパラメーターの位置を変更すると、 **レポート データ** ペインの **[パラメーター]** ボックスの一覧でパラメーターの順序が自動的に変わります。 パラメーターの順序の影響の詳細については、「[レポート パラメーターの順序の変更 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/change-the-order-of-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。  
  
4.  パラメーターのプロパティにアクセスするには、次のいずれかの操作を行います。  
  
    -   パラメーター ペインでパラメーターを右クリックし、 **[パラメーターのプロパティ]**をクリックします。  
  
         ![Access parameter properties from the parameters pane](../../reporting-services/report-design/media/ssrs-customizeparameter-accessparameterproperties-composite.png "Access parameter properties from the parameters pane")  
  
    -   **レポート データ** ペインでパラメーターを右クリックし、**[パラメーターのプロパティ]** をクリックします。  
  
5.  ペインに新しい列や行を追加するには、または既存の行や列を削除するには、パラメーター ペインのどこかを右クリックし、表示されるメニューでコマンドをクリックします。  
  
     ![Add columns and rows to the parameters pane](../../reporting-services/report-design/media/ssrs-customparameter-addcolumnsrows.png "Add columns and rows to the parameters pane")  
  
    > [!IMPORTANT]  
    >  パラメーターを含む列または行を削除すると、レポートからパラメーターが削除されます。  
  
6.  ペインとレポートからパラメーターを削除するには、次のいずれかの操作を行います。  
  
    -   パラメーター ペインでパラメーターを右クリックし、  **[削除]**をクリックします。  
  
         ![Delete parameters from the parameters pane](../../reporting-services/report-design/media/ssrs-customparameter-deleteparameter.png "Delete parameters from the parameters pane")  
  
    -   **レポート データ** ペインでパラメーターを右クリックし、**[削除]** をクリックします。  
  
## 参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)  
  
  