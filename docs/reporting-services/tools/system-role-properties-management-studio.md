---
title: "システム ロールのプロパティ (Management Studio) | Microsoft Docs"
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
f1_keywords: 
  - "sql13.swb.reportserver.systemroleproperties.f1"
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
caps.latest.revision: 30
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 30
---
# システム ロールのプロパティ (Management Studio)
  [システム ロール] ページは、レポート サーバーで現在定義されているシステム ロールの定義を表示するために使用します。 システム ロールの定義には、個別のアイテムではなく、サイト全体に関連して実行される名前付きのタスクのコレクションが含まれています。 ロールの定義は、ロールの割り当てを作成するために、ユーザーまたはグループに割り当てられます。 ロールの定義のタスクには、ユーザーまたはグループが実行できる操作を指定します。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、 **システム管理者** と **システム ユーザー**という 2 つのシステム ロールがあらかじめ定義されています。 タスクの一覧を変更することにより、ロールの定義を変更できます。また、異なるタスクの組み合わせをサポートする新しいシステム ロールを作成できます。 ロールの定義を編集すると、そのロールの定義を含むすべてのロールの割り当てに反映されます。  
  
> [!NOTE]  
>  システム ロールの割り当ては、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。  
  
## オプション  
 **名前**  
 システム ロールの定義名を指定します。  
  
 **Description**  
 システム ロール定義の説明が表示されます。  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]では、この説明は、このページにのみ表示されます。 レポート マネージャーを使用してこのアイテムを表示すると、フォルダー階層を参照しているときにこの説明が表示される場合があります。  
  
 **タスク**  
 このロール定義で選択できるシステムレベルのタスクがすべて一覧表示されます。 定義済みタスクの一覧にアイテムを追加または一覧から削除することで、ユーザーがこのロールを使用して特定のアイテムにアクセスする方法を定義できます。 新しいタスクを作成したり、既存のタスクを変更したりすることはできません。  
  
 **Description**  
 各タスクに関する情報が表示されます。 タスクの説明を変更することはできません。  
  
## 参照  
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [システムレベルのタスク](../../reporting-services/security/system-level-tasks.md)   
 [タスクと権限](../../reporting-services/security/tasks-and-permissions.md)   
 [Predefined Roles](../../reporting-services/security/predefined-roles.md)  
  
  