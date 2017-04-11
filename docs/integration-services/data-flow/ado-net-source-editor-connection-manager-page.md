---
title: "[ADO NET 変換元エディター] ([接続マネージャー] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.adonetsource.connection.f1"
ms.assetid: 7de3f438-bdd6-49b5-937a-47369e754943
caps.latest.revision: 19
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 19
---
# [ADO NET 変換元エディター] ([接続マネージャー] ページ)
  **[ADO NET 変換元エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、変換元の [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを選択できます。 さらにこのページを使用して、データベースのテーブルやビューを選択できます。  
  
 ADO NET 変換元の詳細については、「 [ADO NET Source](../../integration-services/data-flow/ado-net-source.md)」を参照してください。  
  
 **[接続マネージャー] ページを開くには**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、ADO NET 変換元を含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、ADO NET 変換元をダブルクリックします。  
  
3.  **[ADO NET 変換元エディター]** で、**[接続マネージャー]** をクリックします。  
  
## 静的オプション  
 **ADO.NET 接続マネージャー**  
 既存の接続マネージャーを一覧から選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 **新規**  
 **[ADO.NET の接続マネージャーの構成]** ダイアログ ボックスを使用して、新しい接続マネージャーを作成します。  
  
 **[データ アクセス モード]**  
 ソースからデータを選択する方法を指定します。  
  
|オプション|Description|  
|------------|-----------------|  
|[テーブルまたはビュー]|[!INCLUDE[vstecado](../../includes/vstecado-md.md)] データ ソースのテーブルまたはビューからデータを取得します。|  
|[SQL コマンド]|SQL クエリを使用して、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] データ ソースからデータを取得します。|  
  
 **プレビュー**  
 **[データ ビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 **プレビュー**では、最大で 200 行を表示できます。  
  
> [!NOTE]  
>  データをプレビューするときに、CLR ユーザー定義型を含む列にはデータが表示されません。 その代わりに、\<値が大きすぎて表示できません> または System.Byte[] が値として表示されます。 前者は、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] プロバイダーを使用してデータ ソースにアクセスする場合に表示されます。後者は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client プロバイダーを使用している場合に表示されます。  
  
## データ アクセス モードの動的オプション  
  
### [データ アクセス モード] = [テーブルまたはビュー]  
 **[テーブル名またはビュー名]**  
 データ ソースで使用できるテーブルまたはビューの一覧から、テーブルまたはビューの名前を選択します。  
  
### [データ アクセス モード] = [SQL コマンド]  
 **[SQL コマンド テキスト]**  
 SQL クエリのテキストを入力し、**[クエリの作成]** をクリックしてクエリを作成するか、**[参照]** をクリックしてクエリ テキストを含むファイルを指定します。  
  
 **[クエリの作成]**  
 SQL クエリを視覚的に作成するには、**[クエリ ビルダー]** ダイアログ ボックスを使用します。  
  
 **参照**  
 **[開く]** ダイアログ ボックスを使用して、SQL クエリのテキストが含まれているファイルを指定します。  
  
## 参照  
 [[ADO NET 変換元エディター] ([列] ページ)](../Topic/ADO%20NET%20Source%20Editor%20\(Columns%20Page\).md)   
 [[ADO NET 変換元エディター] ([エラー出力] ページ)](../Topic/ADO%20NET%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [ADO.NET 接続マネージャー](../../integration-services/connection-manager/ado-net-connection-manager.md)  
  
  