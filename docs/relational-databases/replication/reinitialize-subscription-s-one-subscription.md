---
title: "[サブスクリプションの再初期化] - 1 つのサブスクリプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.reinit.single.f1"
helpviewer_keywords: 
  - "[サブスクリプションの再初期化] ダイアログ ボックス"
ms.assetid: 9b0cf0be-d1f1-4163-a0ca-d6f095aa707e
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# [サブスクリプションの再初期化] - 1 つのサブスクリプション
   **サブスクリプションの再初期化** ] ダイアログ ボックスでは、サブスクリプションの再初期化用にマークすることができます。 再初期化には、サブスクライバーへのスナップショットの適用が含まれています。トランザクション パブリケーションに対するサブスクリプションの場合はディストリビューション エージェントによって実行され、マージ パブリケーションに対するサブスクリプションの場合はマージ エージェントによって実行されます。  
  
## オプション  
 **[現在のスナップショットを使用する]**  
 このオプションを選択すると、次にディストリビューション エージェントまたはマージ エージェントが実行されたときに、現在のスナップショットがサブスクライバーに適用されます。 有効なスナップショットが使用できない場合、このオプションは選択できません。  
  
 **[新しいスナップショットを使用する]**  
 このオプションを選択すると、新しいスナップショットによってサブスクリプションが再初期化されます。 スナップショットは、スナップショット エージェントによって生成された後にだけ、サブスクライバーに適用できます。 スナップショット エージェントの実行がスケジュールに設定されている場合、次にスケジュールされたスナップショット エージェントの実行が終了するまで、サブスクリプションは再初期化されません。  
  
 スナップショット エージェントをすぐに開始するには、 **[今すぐ新しいスナップショットを生成する]** を選択します。  
  
 **[再初期化する前に、同期されていない変更をアップロード]**  
 マージ レプリケーションのみです。 このオプションを選択すると、サブスクライバーのデータがスナップショットで上書きされる前に、保留中の変更がサブスクリプション データベースからアップロードされます。  
  
 パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
 **[再初期化するように設定]**  
 クリックすると、サブスクリプションに再初期化が設定されます。 有効なスナップショットが使用できるようになった後、サブスクリプションに対してディストリビューション エージェントまたはマージ エージェントを次回実行するとき、スナップショットはサブスクライバーに適用されます。  
  
## 参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  