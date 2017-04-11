---
title: "[新しい可用性グループ] ダイアログ ボックスの使用 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "作成する可用性グループ [SQL Server]"
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
caps.latest.revision: 40
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 40
---
# [新しい可用性グループ] ダイアログ ボックスの使用 (SQL Server Management Studio)
  このトピックでは、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] の **[新しい可用性グループ]** ダイアログ ボックスを使用して、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] が有効な [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。 *可用性グループ* は、1 つのまとまりとしてフェールオーバーする一連のユーザー データベースと、フェールオーバーをサポートする一連のフェールオーバー パートナー ( *可用性レプリカ*) を定義します。  
  
> [!NOTE]  
>  可用性グループの概要については、「[AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)」を参照してください。  
  
-   **作業を開始する準備:**  
  
     [前提条件](#PrerequisitesRestrictions)  
  
     [制限事項](#Limitations)  
  
     [セキュリティ](#Security)  
  
-   **以下を使用して可用性グループを作成するには:**  [[新しい可用性グループ] ダイアログ ボックス](#SSMSProcedure)  
  
-   **補足情報:**  [[新しい可用性グループ] ダイアログ ボックスを使用して可用性グループを作成した後](#FollowUp)  
  
> [!NOTE]  
>  可用性グループを作成する別の方法については、このトピックの後の「[関連タスク](#RelatedTasks)」を参照してください。  
  
##  <a name="BeforeYouBegin"></a> はじめに  
 可用性グループを初めて作成する場合は、あらかじめこのセクションに目を通しておくことを強くお勧めします。  
  
###  <a name="PrerequisitesRestrictions"></a> 前提条件  
  
-   可用性グループを作成する前に、可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが同じ Windows Server フェールオーバー クラスタリング (WSFC) フェールオーバー クラスター内の別の WSFC ノードに存在していることを確認します。 さらに、各サーバー インスタンスで [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]が有効であり、[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]に関するその他の前提条件がすべて満たされていることを確認します。 詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)」を参照することを強くお勧めします。  
  
-   可用性グループを作成する前に、可用性レプリカをホストするすべてのサーバー インスタンスでデータベース ミラーリング エンドポイントが完全に機能することを確認します。 詳細については、「[データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)」を参照してください。  
  
-   **[新しい可用性グループ]** ダイアログ ボックスを使用するには、可用性レプリカをホストするサーバー インスタンスの名前がわかっている必要があります。 さらに、新しい可用性グループに追加するすべてのデータベースの名前がわかっている必要があるほか、これらのデータベースが「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)」に記載されている可用性データベースの前提条件および制限を満たすことを確認する必要があります。 無効な値を入力した場合、新しい可用性グループは機能しません。  
  
###  <a name="Limitations"></a> 制限事項  
 **[新しい可用性グループ]** ダイアログ ボックスでは、次の操作を実行できません。  
  
-   [可用性グループ リスナーの作成]  
  
-   セカンダリ レプリカの可用性グループへの参加  
  
-   最初のデータの同期の実行  
  
 これらの構成タスクについては、このトピックの後の「 [補足情報: [新しい可用性グループ] ダイアログ ボックスを使用して可用性グループを作成した後](#FollowUp)」を参照してください。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限のいずれかが必要です。  
  
##  <a name="SSMSProcedure"></a> [新しい可用性グループ] ダイアログ ボックスの使用 (SQL Server Management Studio)  
 **可用性グループを作成するには**  
  
1.  オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックします。  
  
2.  **[AlwaysOn 高可用性]** ノードを展開します。  
  
3.  **[可用性グループ]** ノードを右クリックし、**[新しい可用性グループ]** コマンドを選択します。  
  
4.  **[新しい可用性グループ]** ダイアログ ボックスが開きます。  
  
5.  **[全般]** ページで、 **[可用性グループ名]** ボックスに新しい可用性グループの名前を入力します。 この名前は、WSFC クラスター内のすべての可用性グループ間で一意の有効な SQL Server 識別子である必要があります。 可用性グループ名の最大文字数は 128 文字です。  
  
6.  **[可用性データベース]** グリッドで、 **[追加]** をクリックし、この可用性グループの所属先のローカル テータベースの名前を入力します。 追加するすべてのデータベースに対してこの手順を繰り返します。 **[OK]**をクリックすると、指定したデータベースを可用性グループに参加させるための前提条件が満たされているかどうかが確認されます。 これらの前提条件については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)」を参照してください。  
  
7.  **[可用性データベース]** グリッドで、 **[追加]** をクリックし、セカンダリ レプリカをホストするサーバー インスタンスの名前を入力します。 これらのインスタンスへの接続は試行されません。 無効なサーバー名を指定した場合、セカンダリ レプリカは追加されますが、このレプリカに接続することはできません。  
  
    > [!TIP]  
    >  レプリカを追加した後ホスト サーバー インスタンスに接続できない場合は、このレプリカを削除し、新しいレプリカを追加できます。 詳細については、「[可用性グループからのセカンダリ レプリカの削除 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server.md)」および「[可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server.md)」を参照してください。  
  
8.  ダイアログ ボックスの **[ページの選択]** ペインで、 **[バックアップの設定]**をクリックします。 次に、 **[バックアップの設定]** ページで、レプリカのロールに基づいてどこでバックアップを実行するかを指定し、この可用性グループの可用性レプリカをホストするそれぞれのサーバー インスタンスにバックアップの優先順位を割り当てます。 詳細については、「[[可用性グループのプロパティ]: [新しい可用性グループ] &#40;[バックアップの設定] ページ&#41;](../Topic/Availability%20Group%20Properties:%20New%20Availability%20Group%20\(Backup%20Preferences%20Page\).md)」を参照してください。  
  
9. 可用性グループを作成するには、 **[OK]**をクリックします。 これにより、指定したデータベースが前提条件を満たしているかどうかが確認されます。  
  
     可用性グループを作成しないでダイアログ ボックスを終了するには、 **[キャンセル]**をクリックします。  
  
##  <a name="FollowUp"></a> 補足情報: [新しい可用性グループ] ダイアログ ボックスを使用して可用性グループを作成した後  
  
-   可用性グループのセカンダリ レプリカをホストするそれぞれのサーバー インスタンスに接続し、次の手順を実行する必要があります。  
  
    1.  セカンダリ レプリカを可用性グループに参加させます。 詳細については、「[可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)」を参照してください。  
  
    2.  各プライマリ データベースとそのトランザクション ログの最新のバックアップを復元します (RESTORE WITH NORECOVERY を使用)。 詳細については、「[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)」を参照してください。  
  
    3.  新しく準備された各セカンダリ データベースを可用性グループにすぐに参加させます。 詳細については、「[可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)」を参照してください。  
  
-   新しい可用性グループに対して可用性グループ リスナーを作成することをお勧めします。 そのためには、現在のプライマリ レプリカをホストするサーバー インスタンスに接続する必要があります。 詳細については、「[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)」を参照してください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
 **可用性グループおよびレプリカのプロパティを構成するには**  
  
-   [可用性レプリカの可用性モードの変更 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [可用性レプリカのフェールオーバー モードの変更 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 &#40;Always On Availability Groups&#41;](../../../database-engine/availability-groups/windows/configure flexible automatic failover policy.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
-   [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
-   [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [可用性レプリカのセッション タイムアウト期間の変更 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **可用性グループの構成を完了するには**  
  
-   [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **別の方法で可用性グループを作成する**  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [可用性グループの作成 &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [可用性グループの作成 &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
 **AlwaysOn 可用性グループを有効にするには**  
  
-   [AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **データベース ミラーリング エンドポイントを構成するには**  
  
-   [AlwaysOn 可用性グループのデータベース ミラーリング エンドポイントの作成 &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/database mirroring - always on availability groups- powershell.md)  
  
-   [Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify endpoint url - adding or modifying availability replica.md)  
  
 **AlwaysOn 可用性グループの構成のトラブルシューティング方法**  
  
-   [AlwaysOn 可用性グループの構成のトラブルシューティング &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;](../../../database-engine/availability-groups/windows/troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> 関連コンテンツ  
  
-   [高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [データベース ミラーリング エンドポイント &#40;SQL Server&#41;](../../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners, client connectivity, application failover.md)   
 [AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)  
  
  