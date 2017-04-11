---
title: "Reporting Services モバイル レポートの共有データセットからデータを取得する | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/30/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b846451-c8d0-412c-802d-a42bb1ff8c63
caps.latest.revision: 18
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 16
---
# Reporting Services モバイル レポートの共有データセットからデータを取得する
[!INCLUDE[PRODUCT_NAME](../../includes/product-name.md)] では、[Excel ファイルからのデータの読み込み](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md)以外にも、ほぼすべてのソースからのデータにアクセスできます。 データへのアクセスには、[!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] [!INCLUDE[ssRSWebPortal](../../includes/ssrswebportal.md)] で構成された共有データ ソースが必要です。 詳細については、[共有データ ソースの作成](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)についてのページと、[共有データセットの作成](../../reporting-services/report-data/manage-shared-datasets.md)についてのページを参照してください。  
  
共有データ ソースと共有データセットを [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] サーバー上で構成した後、[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] で作成したモバイル レポート内でそれらを使用できます。   
  
[!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] から [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] サーバーへの接続が完了したら、モバイル レポートを共有データセットに接続するのは簡単です。   
  
1. **[データ]** タブで **[データの追加]** を選択します。  
  
2. **[レポート サーバー]** を選択します。   
  
3.  サーバーに接続するのが初めての場合、サーバー名、名前、パスワードを入力します。 次の形式でサーバー アドレス ボックスにサーバー名を入力します。  
  
    \<"サーバー名">/reports/  
  
    この例では、次の点に注意してください。  
       
    ![SSMRP_ConnectToServer](../../reporting-services/mobile-reports/media/ssmrp-connecttoserver.png)  
      
  
4. [!INCLUDE[PRODUCT_NAME](../../includes/ssrsnoversion.md)] サーバーを選択すると、フォルダー内の利用可能なデータセットが表示されます。 [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] にデータをインポートするデータセットを選択します。  
  
   ![SS_MRP_ServerData](../../reporting-services/mobile-reports/media/ss-mrp-serverdata.png)  
  
データセットのインポートが完了したら、シミュレートされたデータや Excel ファイルからのローカル データの場合と同様に、モバイル レポートをデザインできます。  
  
既定では共有データセットは常に最新の状態であり、最新のデータが含まれています。これは、だれかがそのデータセットに基づいたモバイル レポートを表示するたびに、SQL Server が基になるクエリを実行して最新のデータを返すためです。 多くの人がモバイル レポートを表示する場合、これが望ましくない場合があることは明らかです。そのため、キャッシュを設定して、クエリを定期的に実行し、返されるデータセットをキャッシュできます。 このブログ投稿では、[Web ポータルでのキャッシュとデータ更新のしくみ](http://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/)について説明されています。  
  
## レポート サーバーの追加、編集、削除  
  
既にレポート サーバーに接続している場合は、[データ] タブで **[データの追加]** を選択しても、別のレポート サーバーを追加するオプションは表示されません。 代わりに、次の手順を実行します。  
  
1. 左上隅の **[接続]** を選択します。  
  
   ![SSMRP_AddConnectionIcon](../../reporting-services/mobile-reports/media/ssmrp-addconnectionicon.png)  
     
   [サーバー接続] ペインが右側に開きます。  
     
   ![SSMRP_ServerConnectnPane](../../reporting-services/mobile-reports/media/ssmrp-serverconnectnpane.png)  
     
2. 新しいサーバー接続を追加するか、既存の接続を編集または削除します。  
  
### 参照  
- [Create and publish mobile reports with SQL Server Mobile Report Publisher (SQL Server Mobile Report Publisher でモバイル レポートを作成し発行する)](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
-  [Reporting Services Web ポータル](../../reporting-services/web-portal-ssrs-native-mode.md)  
-  [iPad アプリ (Power BI for iOS) で SQL Server モバイル レポートと KPI を表示する](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-ipad-kpis-mobile-reports)  
-  [iPhone アプリ (Power BI for iOS) で SQL Server モバイル レポートと KPI を表示する](https://pbiwebprod-docs.azurewebsites.net/en-us/documentation/powerbi-mobile-iphone-kpis-mobile-reports)  
  
  
  
  