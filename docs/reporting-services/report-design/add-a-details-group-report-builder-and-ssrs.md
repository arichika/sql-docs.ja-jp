---
title: "詳細グループの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 9
---
# 詳細グループの追加 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の改ページ調整されたレポートでは、レポート データセットの詳細データは、グループ式のないグループとして指定されます。 マトリックスの詳細データを表示したり、表や一覧から削除した詳細データを再び追加したり、詳細グループを追加したりするときは、既存の Tablix データ領域に詳細グループを追加します。 グループの詳細については、「[グループについて (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 詳細グループを Tablix データ領域に追加するには  
  
1.  デザイン画面で、Tablix データ領域の任意の場所をクリックして選択します。 グループ化ペインに、選択したデータ領域の行グループと列グループが表示されます。  
  
2.  [グループ化] ペインで、最も内側の子グループを右クリックします。 **[グループの追加]**をクリックし、 **[子グループ]**をクリックします。 **[Tablix のグループ]** ダイアログ ボックスが表示されます。  
  
3.  **[グループ式]**で式を空白のままにします。 詳細グループには式がありません。  
  
4.  **[詳細データの表示]**をクリックします。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     グループ化ペインで新しい詳細グループが子グループとして追加され、手順 1. で選択したグループの行ハンドルに詳細グループ アイコンが表示されます。 Tablix データ領域に関する詳細については、「[Tablix データ領域のセル、行、および列 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)」を参照してください。  
  
## 参照  
 [データ領域でのグループの追加または削除 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [グループについて (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/understanding-groups-report-builder-and-ssrs.md)   
 [Tablix データ領域 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md)   
 [テーブル (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-report-builder-and-ssrs.md) 
  [マトリックス (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [一覧 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)      
 [テーブル、マトリックス、および一覧 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  