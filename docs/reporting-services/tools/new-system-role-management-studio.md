---
title: "[新しいシステム ロール] (Management Studio) | Microsoft Docs"
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
f1_keywords: 
  - "sql13.swb.reportserver.newsystemrole.f1"
ms.assetid: 7b4a0b98-975b-478a-8359-7db39ccbb347
caps.latest.revision: 28
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 28
---
# [新しいシステム ロール] (Management Studio)
  このページを使用すると、システムレベルのロールの定義を作成できます。 システム ロールの定義には、レポート サーバー全体に適用する、システムレベルのタスクのセットを指定します。  
  
> [!NOTE]  
>  ロールの定義は、ネイティブ モードで実行されているレポート サーバーでのみ使用されます。 レポート サーバーが SharePoint 統合モード用に構成されている場合、このページは使用できません。  
  
## オプション  
 **名前**  
 ロールの定義名を入力します。 ロールの定義名は、レポート サーバーの名前空間内で一意である必要があります。 名前には、少なくとも 1 つの英数字が含まれている必要があります。 また、スペースおよびいくつかの記号を含めることもできます。 名前を指定するときに使用できない記号は次のとおりです。  
  
 ; ? : @ & = + , $ / * \< >  
  
 " /  
  
 **Description**  
 ロールの使用方法を説明する場合やロールがサポートする内容を列挙する場合に説明を表示します。  
  
 **タスク**  
 このロールで実行できるシステムレベル タスクを選択します。 新しいタスクを作成したり、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] によってサポートされている既存のタスクを変更したりすることはできません。 システム ロール定義にはアイテムレベル タスクを選択できません。  
  
 **タスクの説明**  
 タスクでサポートされる操作または権限を列挙する、タスクの説明を表示します。  
  
## 参照  
 [Management Studio のレポート サーバーの F1 ヘルプ](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [ロールの定義](../../reporting-services/security/role-definitions.md)  
  
  