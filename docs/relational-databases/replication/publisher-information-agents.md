---
title: "パブリッシャー情報、[エージェント] | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.publisherinfo.commonjobs.f1"
ms.assetid: 2346c00d-c269-45a1-af14-68e7fd7ebd7e
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# パブリッシャー情報、[エージェント]
  **[エージェント]** タブには、パブリッシャーに関連するエージェントおよびメンテナンス ジョブに関する詳細情報が表示されます。  
  
-   すべてのパブリケーションで表示されるスナップショット エージェント  
  
-   すべてのトランザクション パブリケーションで表示されるログ リーダー エージェント  
  
-   キュー更新サブスクリプション用に有効になっているトランザクション パブリケーションで表示されるキュー リーダー エージェント  
  
-   すべてのパブリケーションで表示されるメンテナンス ジョブ  
  
    -   データ検証で問題が見つかったサブスクリプションの再初期化  
  
    -   エージェント履歴のクリーンアップ: ディストリビューション  
  
    -   ディストリビューションのレプリケーション モニターの状態更新機能  
  
    -   レプリケーション エージェントの検査  
  
    -   ディストリビューションのクリーンアップ: ディストリビューション  
  
    -   有効期限が切れたサブスクリプションのクリーンアップ  
  
 これらのジョブの詳細については、次を参照してください。 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)します。  
  
## オプション  
 エージェントまたはジョブに関する情報を表示する [、 **エージェントとジョブの種類** ボックスの一覧です。 エージェントまたはジョブに関する詳細情報やタスクを調べるには、対象のエージェントまたはジョブの行を右クリックし、ショートカット メニューのオプションをクリックします。 グリッドにデータを表示する方法を変更するには、グリッドを右クリックし、次のいずれかのオプションをクリックします。  
  
-   **[並べ替え]**: **[列の並べ替え]** ダイアログ ボックスで、1 つ以上の列を基準にして並べ替えを行います。  
  
-   **[表示する列の選択]**: **[列の選択]** ダイアログ ボックスで、表示する列とその表示順序を選択します。  
  
-   **[フィルター]**: **[フィルターの設定]** ダイアログ ボックスで、列の値に基づいてグリッドの行をフィルター選択します。  
  
-   **[フィルターのクリア]**: グリッドのフィルター設定をすべてクリアします。  
  
 フィルター設定は各グリッドに固有です。 列の選択と並べ替えは、各パブリッシャーのパブリケーション グリッドなど、同じ種類のすべてのグリッドに適用されます。  
  
 この後のセクションでは、このタブでエージェントまたはジョブごとに表示されるデータについて説明します。  
  
### スナップショット エージェント  
 **[状態]**  
 エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [再試行]  
  
-   実行中  
  
-   [完了]  
  
 **パブリケーション**  
 エージェントが関連付けられているパブリケーションの名前です。  
  
 **[前回の開始時刻]**  
 前回のエージェントの開始時刻です。  
  
 **Duration**  
 エージェントが実行された時間の長さです。 この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。  
  
 **[最後のアクション]**  
 エージェントが最後に実行されたときに最後に実行されたアクションです。  
  
 **[配信率]**  
 エージェントが最後に実行されたときにディストリビューション データベースで初期化コマンドがコミットされた頻度 (1 秒あたりのコマンド数) です。  
  
 **#トランザクション**  
 エージェントが最後に実行されたときにディストリビューション データベースでコミットされたトランザクションの数です。  
  
 **#コマンド**  
 エージェントが最後に実行されたときにディストリビューション データベースでコミットされたコマンドの数です。 更新などのデータ変更がコマンドに相当します。  
  
### ログ リーダー エージェント (Log Reader Agent)  
 **[状態]**  
 エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [再試行]  
  
-   実行中  
  
-   [実行されていません]  
  
 **パブリケーション データベース**  
 エージェントが関連付けられているパブリケーションの名前です。  
  
 **[前回の開始時刻]**  
 前回のエージェントの開始時刻です。  
  
 **Duration**  
 エージェントが実行された時間の長さです。 この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。  
  
 **[最後のアクション]**  
 エージェントが最後に実行されたときに最後に実行されたアクションです。  
  
 **[配信率]**  
 ディストリビューション データベースで変更がコミットされた頻度 (1 秒あたりのコマンド数) です。  
  
 **[待機時間]**  
 パブリケーション データベースで最新の変更がコミットされてから、ディストリビューション データベースで対応するコマンドがコミットされるまでに経過した時間 (秒単位) です。  
  
 **#トランザクション**  
 エージェントが最後に実行されたときにディストリビューション データベースでコミットされたトランザクションの数です。  
  
 **#コマンド**  
 エージェントが最後に実行されたときにディストリビューション データベースでコミットされたコマンドの数です。 更新などのデータ変更がコマンドに相当します。  
  
 **Avg. #コマンド**  
 エージェントが最後に実行されたときの 1 トランザクションあたりの平均コマンド数です。  
  
### キュー リーダー エージェント (Queue Reader Agent)  
 **[状態]**  
 エージェントの状態です。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [再試行]  
  
-   実行中  
  
-   [実行されていません]  
  
 **ディストリビューション データベース**  
 エージェントが関連付けられているディストリビューション データベースの名前です。  
  
 **[前回の開始時刻]**  
 前回のエージェントの開始時刻です。  
  
 **Duration**  
 エージェントが実行された時間の長さです。 この時間は、エージェントが現在実行中の場合は経過時間、エージェントが以前に実行されている場合は合計時間を表します。  
  
 **[最後のアクション]**  
 エージェントが最後に実行されたときに最後に実行されたアクションです。  
  
 **[配信率]**  
 ディストリビューション データベースで変更がコミットされた頻度 (1 秒あたりのコマンド数) です。  
  
 **[待機時間]**  
 サブスクリプション データベースで最新の変更がコミットされてから、パブリケーション データベースで対応するコマンドがコミットされるまでに経過した時間 (秒単位) です。  
  
 **#トランザクション**  
 エージェントが最後に実行されたときにパブリケーション データベースでコミットされたトランザクションの数です。  
  
 **#コマンド**  
 エージェントが最後に実行されたときにパブリケーション データベースでコミットされたコマンドの数です。 更新などのデータ変更がコマンドに相当します。  
  
 **Avg. #コマンド**  
 エージェントが最後に実行されたときの 1 トランザクションあたりの平均コマンド数です。  
  
### メンテナンス ジョブ  
 **[状態]**  
 それぞれのジョブの状態。 表示される状態の種類を、次に示します。  
  
-   [エラー]  
  
-   [再試行]  
  
-   実行中  
  
-   [実行されていません]  
  
 **[ジョブ]**  
 ジョブの名前を指定します。  
  
 **[前回の開始時刻]**  
 前回のジョブの開始時刻。  
  
 **Duration**  
 ジョブが実行された時間の長さ。 この時間は、ジョブが現在実行されている場合は経過時間を表し、ジョブの実行が完了している場合は合計時間を表します。  
  
 **[最後のアクション]**  
 ジョブが最後に実行されたときに最後に実行されたアクションです。  
  
## 参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [情報を表示し、パブリッシャーおよび #40; のタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [情報を表示し、パブリケーションと #40; に関連付けられているエージェントのタスクを実行レプリケーション モニターと #41 です。](../../relational-databases/replication/monitor/view information and perform tasks for publication agents.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  