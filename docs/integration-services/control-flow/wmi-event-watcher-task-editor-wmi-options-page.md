---
title: "[WMI イベント監視タスク エディター] ([WMI オプション] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.wmieventwatcher.wmiquery.f1"
helpviewer_keywords: 
  - "WMI イベント監視タスク エディター"
ms.assetid: 525f3de7-a021-4e52-9939-3a83c88f131a
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# [WMI イベント監視タスク エディター] ([WMI オプション] ページ)
  **[WMI イベント監視タスク エディター]** ダイアログ ボックスの **[WMI オプション]** ページを使用すると、WQL (Windows Management Instrumentation Query Language) クエリのソースや、WMI イベント監視タスクがどのように WMI (Microsoft Windows Instrumentation) イベントに応答するかを指定できます。  
  
 このタスクの詳細については、「 [WMI Event Watcher Task](../../integration-services/control-flow/wmi-event-watcher-task.md)」を参照してください。 WQL (WMI Query Language) の詳細については、MSDN ライブラリにある Windows Management Instrumentation のトピック「[WQL を使用したクエリ](http://go.microsoft.com/fwlink/?LinkId=79045)」を参照してください。  
  
## 静的オプション  
 **[WMIConnectionName]**  
 WMI 接続マネージャーを一覧から選択するか、**[\<新しい WMI 接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [WMI 接続マネージャー](../../integration-services/connection-manager/wmi-connection-manager.md)、[WMI 接続マネージャー エディター](../../integration-services/connection-manager/wmi-connection-manager-editor.md)  
  
 **[WQLQuerySourceType]**  
 タスクで実行する WQL クエリのソースの種類を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|ソースを WQL クエリに設定します。 この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。|  
|**[ファイル接続]**|WQL クエリを含むファイルを選択します。 この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。|  
|**変数**|ソースを、WQL クエリを定義する変数に設定します。 この値を選択すると、動的オプションの **[WQLQuerySource]** が表示されます。|  
  
 **[ActionAtEvent]**  
 WMI イベントをログに記録すると共に [!INCLUDE[ssIS](../../includes/ssis-md.md)] アクションを実行するか、単にイベントをログに記録するだけにするかを指定します。  
  
 **[AfterEvent]**  
 WMI イベントを受け取った後にタスクを成功または失敗させるか、イベントの発生をタスクで引き続き監視するかを指定します。  
  
 **[ActionAtTimeout]**  
 WMI クエリのタイムアウトをログに記録すると共に [!INCLUDE[ssIS](../../includes/ssis-md.md)] イベントを発生させるか、単にタイムアウトをログに記録するだけにするかを指定します。  
  
 **[AfterTimeout]**  
 タイムアウトに対してタスクを成功または失敗させるか、別のタイムアウトの発生をタスクで引き続き監視するかを指定します。  
  
 **[NumberOfEvents]**  
 監視するイベントの数を指定します。  
  
 **Timeout**  
 イベントが発生するのを待機する秒数を指定します。 値 0 は、タイムアウトを設定しないことを意味します。  
  
## [WQLQuerySource] の動的オプション  
  
### [WQLQuerySource] = [直接入力]  
 **[WQLQuerySource]**  
 クエリを指定します。または、参照ボタン ([...]) をクリックし、**[WQL クエリ]** ダイアログ ボックスを使用してクエリを入力します。  
  
### [WQLQuerySource] = [ファイル接続]  
 **[WQLQuerySource]**  
 ファイル接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### [WQLQuerySource] = [変数]  
 **[WQLQuerySource]**  
 変数を一覧から選択するか、**[\<新しい変数>]** をクリックして新しい変数を作成します。  
  
 **関連トピック:** [Integration Services (SSIS) 変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](../Topic/Add%20Variable.md)  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[WMI イベント監視タスク エディター] ([全般] ページ)](../Topic/WMI%20Event%20Watcher%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [WMI データ リーダー タスク](../../integration-services/control-flow/wmi-data-reader-task.md)  
  
  