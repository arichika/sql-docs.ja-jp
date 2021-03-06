---
title: サブスクリプション エージェントの情報の表示とタスクの実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: fbb59d31-2424-4552-9195-0da8d83e755f
caps.latest.revision: 37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f98dd86491561fb67197a02e228ec1b151e6e3ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="view-information-and-perform-tasks-for-subscription-agents"></a>サブスクリプション エージェントの情報の表示とタスクの実行
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  レプリケーション モニターでは、次の 2 つのタブを使用して、サブスクリプションに関連付けられているエージェントの情報にアクセスできます。  
  
-   **[すべてのサブスクリプション]**  
  
     このタブには、選択されたパブリケーションのすべてのサブスクリプションに関する情報が表示されます。  
  
-   **[サブスクリプション ウォッチ リスト]**  
  
     このタブには、選択したパブリッシャーの中で、エラーや警告が存在するパブリッシャーまたはパフォーマンスが最低のパブリッシャーで利用可能なすべてのパブリケーションから、サブスクリプションに関する情報が表示されます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]より前のバージョンを実行しているディストリビューターでは、このタブが表示されません。  
  
 それぞれのタブのオプションの詳細については、右ペインでタブをクリックしてから、メニュー バーで **[ヘルプ]** をクリックします。 レプリケーション モニターの起動の詳細については、「[Start the Replication Monitor](../../../relational-databases/replication/monitor/start-the-replication-monitor.md)」 (レプリケーション モニターの開始) を参照してください。  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-all-subscriptions-tab"></a>サブスクリプションに関連付けられているエージェントの情報を表示したりタスクを実行するには ([すべてのサブスクリプション] タブ)  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[すべてのサブスクリプション]** タブをクリックして、サブスクリプションに関する情報を表示します。 このタブで、さらに詳しい情報を表示したり、タスクを実行することができます。  
  
    -   サブスクリプションに関連するエージェントの詳細を表示するには、サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。 詳細情報には、エージェントの履歴とエラー メッセージ、トランザクション レプリケーションのパフォーマンスの統計、マージ レプリケーションのアーティクル レベルの同期の統計などが含まれます。  
  
         表示される詳細ウィンドウのタブは、サブスクリプションの種類によって異なります。スナップショット サブスクリプションの場合は **[ディストリビューターからサブスクライバーまでの履歴]** タブ、トランザクション サブスクリプションの場合は **[パブリッシャーからディストリビューターまでの履歴]** タブ、 **[ディストリビューターからサブスクライバーまでの履歴]** タブ、および **[未配布のコマンド]** タブ、マージ サブスクリプションの場合は **[同期の履歴]** タブです。  
  
    -   プッシュ サブスクリプションを同期するには、サブスクリプションを右クリックし、 **[同期の開始]** をクリックします。  
  
    -   サブスクリプションを再初期化するには、サブスクリプションを右クリックし、 **[サブスクリプションの再初期化]** をクリックします。  
  
    -   1 つのマージ サブスクリプションを検証するには、サブスクリプションを右クリックし、 **[サブスクリプションの検証]** をクリックします。 マージ パブリケーションに対するすべてのサブスクリプションを検証するには、パブリケーションを右クリックし、 **[すべてのサブスクリプションの検証]** をクリックします。トランザクション パブリケーションのすべてのサブスクリプションを検証するには、パブリケーションを右クリックし、 **[サブスクリプションの検証]** をクリックします。  
  
    -   エージェントのプロファイルを管理するには、エージェントを右クリックし、 **[エージェント プロファイル]** をクリックします。 詳細については、「[Work with Replication Agent Profiles (レプリケーション エージェント プロファイルの操作)](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)」をご覧ください。  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-subscription-subscription-watch-list-tab"></a>サブスクリプションに関連付けられているエージェントの情報を表示したりタスクを実行するには ([サブスクリプション ウォッチ リスト] タブ)  
  
1.  左ペインでパブリッシャー グループを展開してから、パブリッシャーをクリックします。  
  
2.  **[サブスクリプション ウォッチ リスト]** タブをクリックして、サブスクリプションに関する情報を表示します。 このタブで、さらに詳しい情報を表示したり、タスクを実行することができます。  
  
    -   サブスクリプションに関連するエージェントの詳細を表示するには、サブスクリプションを右クリックし、 **[詳細表示]** をクリックします。 詳細情報には、エージェントの履歴とエラー メッセージ、トランザクション レプリケーションのパフォーマンスの統計、マージ レプリケーションのアーティクル レベルの同期の統計などが含まれます。  
  
         表示される詳細ウィンドウのタブは、サブスクリプションの種類によって異なります。スナップショット サブスクリプションの場合は **[ディストリビューターからサブスクライバーまでの履歴]** タブ、トランザクション サブスクリプションの場合は **[パブリッシャーからディストリビューターまでの履歴]** タブ、 **[ディストリビューターからサブスクライバーまでの履歴]** タブ、および **[パフォーマンス]** タブ、マージ サブスクリプションの場合は **[同期の履歴]** タブです。  
  
    -   プッシュ サブスクリプションを同期するには、サブスクリプションを右クリックし、 **[同期の開始]** をクリックします。  
  
    -   サブスクリプションを再初期化するには、サブスクリプションを右クリックし、 **[サブスクリプションの再初期化]** をクリックします。  
  
    -   1 つのマージ サブスクリプションを検証するには、サブスクリプションを右クリックし、 **[サブスクリプションの検証]** をクリックします。 マージ パブリケーションに対するすべてのサブスクリプションを検証するには、パブリケーションを右クリックし、 **[すべてのサブスクリプションの検証]** をクリックします。トランザクション パブリケーションのすべてのサブスクリプションを検証するには、パブリケーションを右クリックし、 **[サブスクリプションの検証]** をクリックします。  
  
    -   エージェントのプロファイルを管理するには、エージェントを右クリックし、 **[エージェント プロファイル]** をクリックします。 詳細については、「[Work with Replication Agent Profiles (レプリケーション エージェント プロファイルの操作)](../../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
