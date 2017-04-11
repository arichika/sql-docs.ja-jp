---
title: "パッケージ実行のレポートのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8fc476ac-bd69-434e-9636-70776e0b3b6c
caps.latest.revision: 12
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 12
---
# パッケージ実行のレポートのトラブルシューティング
  現在のリリースの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] カタログに配置された [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの監視とトラブルシューティングに役立つ標準レポートを [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で使用できるようになりました。 これらのパッケージ レポートの中には、パッケージの実行状態を確認する場合や、実行が失敗した原因を特定する場合に特に役立つレポートが 2 つあります。  
  
-   **Integration Services ダッシュボード**: このレポートは、過去 24 時間の間に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上で実行されたすべてのパッケージに関する概要を示します。 このレポートには、各パッケージの状態、操作の種類、パッケージ名などに関する情報が表示されます。  
  
     開始時刻、終了時刻、および期間は次のように解釈できます。  
  
    -   パッケージがまだ実行されている場合は、"期間 = 現在の時刻 – 開始時刻" です。  
  
    -   パッケージが完了した場合は、"期間 = 終了時刻 – 開始時刻" です。  
  
     ダッシュ ボードでは、サーバーで実行されたそれぞれのパッケージに対し、"ズーム イン" 機能を使用して、発生した可能性のあるパッケージ実行エラーの特定の詳細を検索することができます。 たとえば、**[概要]** をクリックすると、実行に含まれるタスクの状態の概要が表示されます。**[すべてのメッセージ]** をクリックすると、パッケージの実行の一部としてキャプチャされた詳細メッセージが表示されます。  
  
     **[フィルター]** をクリックし、**[フィルターの設定]** ダイアログで条件を選択することにより、各ページに表示されるテーブルにフィルターを適用できます。 使用できるフィルター条件は、表示されるデータに依存します。 **[フィルターの設定]** ダイアログの並べ替えアイコンをクリックすることで、レポートの並べ替え順序を変更できます。  
  
-   **"利用状況 - すべての実行" レポート**: このレポートには、サーバーで実行されたすべての [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の実行に関する概要が表示されます。 この概要には、状態、開始時刻、終了時刻など、各実行の情報が表示されます。 各概要エントリには、実行中に生成されたメッセージやパフォーマンス データを含め、実行に関する詳細へのリンクが含まれます。 Integration Services ダッシュボードと同様に、テーブルにフィルターを適用して、表示される情報を絞り込むことができます。  
  
## 関連タスク  
 [Integration Services サーバーのレポートの表示](../../integration-services/performance/view-reports-for-the-integration-services-server.md)  
  
## 関連コンテンツ  
 [Integration Services サーバーのレポート](../../integration-services/performance/reports-for-the-integration-services-server.md)  
  
 [パッケージ実行のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-execution.md)  
  
  