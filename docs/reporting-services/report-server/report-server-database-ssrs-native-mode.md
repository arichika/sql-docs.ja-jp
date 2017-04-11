---
title: "レポート サーバー データベース (SSRS ネイティブ モード) | Microsoft Docs"
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
helpviewer_keywords: 
  - "データベース [Reporting Services]"
  - "レポート サーバー [Reporting Services], データベース"
  - "一時データベース [Reporting Services]"
  - "レポート サーバー データベース"
  - "reportservertempdb"
  - "reportserver データベース"
ms.assetid: 0fc5c033-3fe1-4cea-86c7-66ea5e424d65
caps.latest.revision: 48
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 48
---
# レポート サーバー データベース (SSRS ネイティブ モード)
  レポート サーバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]を使用してメタデータやオブジェクトの定義を格納するステートレス サーバーです。 ネイティブ モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールでは、一時データと永続データが 2 つのデータベースに別々に格納されます。 この 2 つのデータベースは同時に作成され、データベース名によってバインドされます。 既定では、データベース名がそれぞれ **reportserver** と **reportservertempdb** になります。  
  
 SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールでは、データ警告機能用のデータベースも作成されます。 SharePoint モードの 3 つのデータベースは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに関連付けられます。 詳細については、「[Reporting Services SharePoint サービス アプリケーションの管理](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)｣を参照してください  
  
 データベースは、ローカルまたはリモートの[!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスで実行できます。 十分なシステム リソースがある場合、またはソフトウェア ライセンスを節約したい場合は、ローカル インスタンスを選択します。ただし、データベースをリモート コンピューター上で実行した方がパフォーマンスを向上できます。  
  
 既存のレポート サーバー データベースは、以前のインストールから、または別のレポート サーバー インスタンスを使用した別のインスタンスから、移植または再利用できます。 レポート サーバー データベースのスキーマには、レポート サーバー インスタンスとの互換性が必要です。 データベースが古い形式の場合、現在の形式にアップグレードするように求められます。 新しいバージョンを古いバージョンにダウングレードすることはできません。 新しいレポート サーバー データベースを使用する場合、そのデータベースを以前のバージョンのレポート サーバー インスタンスで使用することはできません。 レポート サーバー データベースを新しい形式にアップグレードする方法の詳細については、「[レポート サーバー データベースのアップグレード](../../reporting-services/install-windows/upgrade-a-report-server-database.md)」を参照してください。  
  
> [!IMPORTANT]  
>  データベースのテーブル構造はサーバー操作用に最適化されているので、変更またはチューニングしないでください。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] では、リリースごとにテーブル構造を変更することがあります。 ユーザーがデータベースを変更または拡張すると、将来のアップグレードの実行や Service Pack の適用の際に、機能が制限されたり機能を利用できない場合があります。 また、レポート サーバーの処理を損なう変更を行う可能性もあります。 たとえば、ReportServer データベースで READ_COMMITTED_SNAPSHOT をオンにすると、対話的な並べ替え機能が無効になります。  
  
 レポート サーバー データベースへのすべてのアクセスは、レポート サーバー経由で行われる必要があります。 レポート サーバー データベースのコンテンツにアクセスするには、レポート マネージャーや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] などのレポート サーバー管理ツールを使用するか、または URL アクセス、レポート サーバー Web サービス、Windows Management Instrumentation (WMI) プロバイダーなどの、プログラマティック インターフェイスを使用します。  
  
 レポート サーバー データベースへの接続は、通常、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成マネージャーを使用して定義します。 ただし、既定の構成でインストールする場合は、セットアップ時に定義することもできます。 データベースへのレポート サーバーの接続の詳細については、「[レポート サーバー データベース接続の構成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)」を参照してください。  
  
## レポート サーバー データベース  
 レポート サーバー データベースは、以下のコンテンツを格納する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースです。  
  
-   レポート サーバーによって管理されるアイテム (レポート、リンク レポート、共有データ ソース、レポート モデル、フォルダー、リソース)、およびこれらのアイテムに関連付けられるすべてのプロパティ設定とセキュリティ設定  
  
-   サブスクリプションおよびスケジュールの定義  
  
-   レポート スナップショット (クエリ結果も含む) およびレポート履歴  
  
-   システム プロパティおよびシステムレベルのセキュリティ設定  
  
-   レポート実行ログ データ  
  
-   レポート データ ソースに対して使用する対称キー、暗号化された接続情報、および資格情報  
  
 レポート サーバー データベースには、アプリケーションの状態と永続データが格納されるため、このデータベースのバックアップ スケジュールを作成して、データの損失を防ぐ必要があります。 データベースのバックアップ方法に関する推奨事項と説明については、「[別のコンピューターへのレポート サーバー データベースの移動 (SSRS ネイティブ モード)](../../reporting-services/report-server/moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md)」を参照してください。  
  
## レポート サーバーの一時データベース  
 各レポート サーバー データベースでは、関連する一時データベースが使用され、セッション データ、実行データ、キャッシュされたレポート、およびレポート サーバーによって生成される作業テーブルが格納されます。 バックグラウンドのサーバー プロセスにより、一時データベースのテーブルから古いアイテムや未使用のアイテムが定期的に削除されます。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、一時データベースが存在しない場合、一時データベースが再作成されません。また、存在しないテーブルや変更されたテーブルも修復されません。 一時データベースには永続データが格納されませんが、それでもデータベースのコピーをバックアップすることをお勧めします。バックアップを行うことによって、障害復旧時にデータベースを再作成する必要がなくなります。  
  
 一時データベースをバックアップし、続いてデータベースを復元する場合、コンテンツを削除する必要があります。 一般的に、一時データベースのコンテンツは、いつでも安全に削除できます。 ただし、コンテンツを削除した後、レポート サーバー Windows サービスを再起動する必要があります。  
  
## 「  
 [SQL Server フェールオーバー クラスターでのレポート サーバー データベースのホスト](../../reporting-services/install-windows/host-a-report-server-database-in-a-sql-server-failover-cluster.md)   
 [暗号化されたレポート サーバー データの格納 &#40;SSRS 構成マネージャー&#41;](../../reporting-services/install-windows/store-encrypted-report-server-data-ssrs-configuration-manager.md)   
 [Reporting Services Report Server](../../reporting-services/report-server-sharepoint/reporting-services-report-server.md)   
 [レポート サーバー データベースを管理する &#40;SSRS ネイティブ モード&#41;](../../reporting-services/report-server/administer-a-report-server-database-ssrs-native-mode.md)   
 [レポート サーバー データベースの作成 &#40;SSRS構成マネージャー&#41;](../../reporting-services/install-windows/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Reporting Services のバックアップおよび復元操作](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md)  
  
  