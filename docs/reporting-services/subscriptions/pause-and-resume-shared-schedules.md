---
title: "共有スケジュールを一時停止および再開する | Microsoft Docs"
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
  - "pausing schedules"
  - "report-specific schedules [Reporting Services]"
  - "shared schedules [Reporting Services], resuming"
  - "resuming schedules"
  - "continuing schedules"
  - "schedules [Reporting Services], resuming"
  - "スケジュール [Reporting Services], 一時停止"
ms.assetid: e416be75-5234-4aa6-a3de-77f60f25169a
caps.latest.revision: 36
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 36
---
# 共有スケジュールを一時停止および再開する
  使用中の共有スケジュールは、一時停止および再開することができます。 共有スケジュールを一時停止すると、レポート処理とサブスクリプションのトリガーとして使用しているスケジュールが一時的に無効になります。 一時停止や再開を行うことができるのは共有スケジュールだけです。 レポート固有のスケジュールは一時停止できません。  
  
 実行中のレポート処理は、一時停止および再開することができません。 一時停止および再開できるのは、SQL Server エージェント サービスのスケジュール キューにあるスケジュールだけです。 進行中のジョブは、スケジュール エンジンの対象外です。 詳しくは、「[実行中の処理を管理する](../../reporting-services/subscriptions/manage-a-running-process.md)」をご覧ください。  
  
 共有スケジュールを一時停止すると、その間に発生する予定の操作を無効にできます。 共有スケジュールを再開すると、サーバーのローカル時刻を使用して、次のスケジュール設定時刻にレポートおよびサブスクリプションの処理が実行されます。 ネイティブ モードのレポート サーバーまたは SharePoint サービス アプリケーションでは、スケジュールが一時停止されなければ実行される予定だった、スケジュールされていた操作については、埋め合わせるための実行は行われません。  
  
 このトピックの内容  
  
-   [共有スケジュールの一時停止と再開 (ネイティブ モード)](#bkmk_native)  
  
-   [共有スケジュールの一時停止と再開 (SharePoint モード)](#bkmk_sharepoint)  
  
##  <a name="bkmk_native"></a> 共有スケジュールの一時停止と再開 (ネイティブ モード)  
 共有スケジュールを一時停止または再開するには、レポート マネージャーの [スケジュール] ページを使用します。  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]は使用できません。これには、スケジュールを一時停止または再開するためのオプションは用意されていません。 詳細については、「 [Create, Modify, and Delete Schedules](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)」をご覧ください。  
  
#### 共有スケジュールを一時停止または再開するには  
  
1.  レポート マネージャーから、 **[サイトの設定]**をクリックします。  
  
2.  **[スケジュール]**をクリックします。  
  
3.  スケジュールを選択し、リボンで **[一時停止]** または **[再開]** をクリックします。 スケジュールが現在一時停止している場合は、 **[状態]** 列に **[一時停止]**が表示されます。  
  
##  <a name="bkmk_sharepoint"></a> 共有スケジュールの一時停止と再開 (SharePoint モード)  
 共有スケジュールを一時停止または再開するには、[サイトの設定] ページまたは PowerShell を使用します。 スケジュールは SharePoint サイトごとに管理されます。  
  
#### 共有スケジュールを一時停止または再開するには  
  
1.  **[サイトの操作]**をクリックします。  
  
2.  **[サイトの設定]**をクリックします。  
  
3.  [Reporting Services] セクションで、 **[共有スケジュールの管理]**をクリックします。  
  
4.  スケジュールを選択し、 **[選択したスケジュールの一時停止]** または **[選択したスケジュールの実行]**をクリックします。 スケジュールが現在一時停止している場合は、 **[状態]** 列に **[一時停止]**が表示されます。  
  
## 参照  
 [スケジュール](../../reporting-services/subscriptions/schedules.md)   
 [Create, Modify, and Delete Schedules](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)   
 [レポート サーバーでタイム ゾーンと時計の設定を変更する](../../reporting-services/subscriptions/change-time-zones-and-clock-settings-on-a-report-server.md)   
 [Manage a Running Process](../../reporting-services/subscriptions/manage-a-running-process.md)  
  
  