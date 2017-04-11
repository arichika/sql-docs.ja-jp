---
title: "可用性グループ リスナーの削除 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.availabilitygroup.removeaglistener.default.f1"
helpviewer_keywords: 
  - "可用性グループ [SQL Server]、リスナー"
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
caps.latest.revision: 14
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 14
---
# 可用性グループ リスナーの削除 (SQL Server)
  このトピックでは、[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループから可用性グループ リスナーを削除する方法について説明します。  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [推奨事項](#Recommendations)  
  
     [セキュリティ](#Security)  
  
-   **リスナーを削除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
###  <a name="Recommendations"></a> 推奨事項  
 可用性グループ リスナーを削除する前に、それを使用しているアプリケーションがないことを確認するようにお勧めします。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **可用性グループ リスナーを削除するには**  
  
1.  オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックしてサーバー ツリーを展開します。  
  
2.  **[Always On 高可用性]** ノードと **[可用性グループ]** ノードを展開します。  
  
3.  可用性グループのノード、 **[可用性グループ リスナー]** ノードの順に展開します。  
  
4.  削除するリスナーを右クリックし、**[削除]** をクリックします。  
  
5.  これにより、 **[可用性グループからのリスナーの削除]** ダイアログ ボックスが開きます。 詳細については、このトピックの「 [[可用性グループからのリスナーの削除]](#AgListenerPropertiesDialog)」を参照してください。  
  
###  <a name="AgListenerPropertiesDialog"></a> [可用性グループからのリスナーの削除] (ダイアログ ボックス)  
 **名前**  
 削除するリスナーの名前です。  
  
 **結果**  
 **[成功]** または **[エラー]** のリンクが表示されます。リンクをクリックすると、詳細が表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **可用性グループ リスナーを削除するには**  
  
1.  プライマリ レプリカをホストするサーバー インスタンスに接続します。  
  
2.  [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) ステートメントを使用します。次にその例を示します。  
  
     ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **‘***dns_name***’**  
  
     *group_name* の部分には、可用性グループの名前を指定します。*dns_name* の部分には、可用性グループ リスナーの DNS 名を指定します。  
  
     次の例では、`AccountsAG` 可用性グループのリスナーを削除します。 DNS 名は AccountsAG_Listener です。  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER ‘AccountsAG_Listener’;  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell の使用  
 **可用性グループ リスナーを削除するには**  
  
1.  既定 (**cd**) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。  
  
2.  組み込みの **Remove-Item** コマンドレットを使用して、リスナーを削除します。 たとえば、次のコマンドは、`MyListener` という名前のリスナーを `MyAg` という名前の可用性グループから削除します。  
  
    ```  
    Remove-Item `   
    SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で **Get-Help** コマンドレットを使用します。 詳細については、「 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)」を参照してください。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [可用性グループ リスナーのプロパティの表示 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-listener-properties-sql-server.md)  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners, client connectivity, application failover.md)  
  
  