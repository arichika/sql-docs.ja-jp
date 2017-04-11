---
title: "データ接続を追加および確認する (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: 1d3b2573-e29d-480d-9dde-d26379c86618
caps.latest.revision: 11
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 11
---
# データ接続を追加および確認する (レポート ビルダーおよび SSRS)
  レポート ビルダーでは、レポート サーバーから共有データ ソースを追加することも、レポートで使用される埋め込みデータ ソースを作成することもできます。 レポート デザイナーでは、共有データ ソースまたは埋め込みデータ ソースを作成して、レポート サーバーに配置することができます。  
  
 レポートに共有データ ソースを追加するには、レポート サーバーを参照して共有データ ソースを選択します。 レポート内の共有データ ソースは、レポート サーバー上の共有データ ソース定義を参照しています。  
  
 埋め込みデータ ソースを作成するには、データの外部ソースへの接続情報が必要で、データへのアクセスに必要な権限を把握している必要があります。 通常、この情報は、データ ソースの所有者から得られます。 接続をテストすることによって、指定されている資格情報が十分かどうかを確認できます。  
  
 詳細については、「[レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)」および「[レポート ビルダーでの資格情報の指定](../Topic/Specify%20Credentials%20in%20Report%20Builder.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### レポート ビルダーで共有データ ソースへの接続を作成するには  
  
1.  ツール バーのレポート データ ペインで、**[新規作成]**、**[データ ソース]** の順にクリックします。 **[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[名前]** ボックスに、データ ソースの名前を入力します。  
  
    > [!NOTE]  
    >  この名前は、ローカル レポート定義に保存されます。 この名前は、レポート サーバー上の共有データ ソースの名前ではありません。  
  
3.  **[共有接続またはレポート モデルを使用する]** を選択します。 最近使用した共有データ ソースおよびレポート モデルの一覧が表示されます。 レポート サーバーから共有データ ソースを 1 つ選択するには、**[参照]** をクリックし、共有データ ソースを使用できるレポート サーバー上のフォルダーを参照します。  
  
4.  共有データ ソースを選択し、**[開く]** をクリックします。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 データ ソースがレポート データ ペインに表示されます。  
  
### データ接続を確認するには  
  
1.  レポート データ ペインのツール バーで、データ ソースをダブルクリックします。 **[データ ソースのプロパティ]** ダイアログ ボックスが表示されます。  
  
2.  **[接続テスト]** をクリックします。  
  
3.  接続に成功すると、"接続が正常に作成されました" というメッセージが表示されます。 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  接続に成功しなかった場合は、"データ ソースに接続できません。" というメッセージが表示されます。  
  
5.  **[詳細]** をクリックし、情報に基づいて問題を修正します。  
  
     詳細については、「[レポート ビルダーでの資格情報の指定](../Topic/Specify%20Credentials%20in%20Report%20Builder.md)」を参照してください。  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## 参照  
 [レポート データセット (SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20in%20Report%20Builder.md)  
  
  