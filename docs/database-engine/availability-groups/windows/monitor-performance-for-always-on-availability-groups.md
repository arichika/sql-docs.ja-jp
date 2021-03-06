---
title: Always On 可用性グループのパフォーマンスを監視する (SQL Server) | Microsoft Docs
ms.custom: ag-guide
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dfd2b639-8fd4-4cb9-b134-768a3898f9e6
caps.latest.revision: 13
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: e576153f1e9f0fc43360bc3ce25af284c402b14e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="monitor-performance-for-always-on-availability-groups"></a>Always On 可用性グループのパフォーマンスを監視する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Always On 可用性グループのパフォーマンス面は、ミッション クリティカルなデータベースに対するサービス レベル アグリーメント (SLA) を維持する上で重要です。 可用性グループがセカンダリ レプリカにログを配布する方法を理解することで、可用性実装の回復時刻の目標 (RTO) および回復ポイントの目標 (RPO) の推定、ならびにパフォーマンスに問題がある可用性グループまたはレプリカにおけるボトルネックの特定が容易になります。 この記事では、同期プロセスについて説明し、主要なメトリックの計算方法を示すと共に、一般的なパフォーマンス トラブルシューティング シナリオへのリンクをいくつか紹介します。  
  
 次のトピックが含まれています。  
  
-   [データ同期プロセス](#BKMK_DATA_SYNC_PROCESS)  
  
-   [フロー制御ゲート](#BKMK_FLOW_CONTROL_GATES)  
  
-   [フェールオーバー時間 (RTO) の推定](#BKMK_RTO)  
  
-   [データ損失の可能性 (RPO) の推定](#BKMK_RPO)  
  
-   [RTO と RPO の監視](#BKMK_Monitoring_for_RTO_and_RPO)  
  
-   [パフォーマンスのトラブルシューティング シナリオ](#BKMK_SCENARIOS)  
  
-   [有用な拡張イベント](#BKMK_XEVENTS)  
  
##  <a name="BKMK_DATA_SYNC_PROCESS"></a> データ同期プロセス  
 完全に同期するまでの時間を推定し、ボトルネックを特定するには、同期プロセスを理解する必要があります。 パフォーマンスのボトルネックはプロセス内の任意の箇所で発生する可能性があります。ボトルネックの場所を特定することで、基になっている問題をさらに詳しく調べることができます。 次の図と表に、データの同期プロセスを示します。  
  
 ![可用性グループのデータ同期](media/always-onag-datasynchronization.gif "可用性グループのデータ同期")  
  
|||||  
|-|-|-|-|  
|**Sequence**|**ステップの説明**|**コメント**|**有用なメトリック**|  
|@shouldalert|ログの生成|ログ データがディスクにフラッシュされます。 このログはセカンダリ レプリカにレプリケートする必要があります。 ログ レコードによって送信キューが入力されます。|[SQL Server: データベース > Log bytes flushed\sec](~/relational-databases/performance-monitor/sql-server-databases-object.md)|  
|2|キャプチャ|各データベースに関するログがキャプチャされ、対応するパートナー キュー (データベース レプリカ ペアごとに 1 つ) に送信されます。 このキャプチャ プロセスは、可用性レプリカが接続されていて何らかの理由でデータ移動が中断されていない限り、継続されます。データベース レプリカのペアは同期中または同期済みのいずれかであると表示されます。 キャプチャ プロセスによるメッセージのスキャンおよびエンキューに時間がかかる場合は、ログ送信キューがビルドされます。|[SQL Server: 可用性レプリカ > レプリカに送信されたバイト数\秒](~/relational-databases/performance-monitor/sql-server-availability-replica.md)。可用性レプリカのキューに配置されたすべてのデータベース メッセージの合計を集計したものです。<br /><br /> プライマリ レプリカの [log_send_queue_size](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) (KB) と[log_bytes_send_rate](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) (KB/秒)。|  
|3|Send|各データベース レプリカ キュー内のメッセージがデキューされ、それぞれのセカンダリ レプリカにネットワーク経由で送信されます。|[SQL Server: 可用性レプリカ > トランスポートに送信されたバイト数\秒](~/relational-databases/performance-monitor/sql-server-availability-replica.md) および [SQL Server: 可用性レプリカ > メッセージ確認応答時間](~/relational-databases/performance-monitor/sql-server-availability-replica.md) (ms)|  
|4|受信とキャッシュ|各セカンダリ レプリカがメッセージを受信しキャッシュします。|パフォーマンス カウンター [SQL Server: 可用性レプリカ > Log Bytes Received/sec](~/relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|5|書き込み|書き込みのためログがセカンダリ レプリカにフラッシュされます。 ログのフラッシュ後、プライマリ レプリカに確認応答が返送されます。<br /><br /> ログが書き込まれると、データ損失は回避されます。|パフォーマンス カウンター [SQL Server: データベース > Log Bytes Flushed/sec](~/relational-databases/performance-monitor/sql-server-databases-object.md)<br /><br /> 待機の種類 [HADR_LOGCAPTURE_SYNC](~/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)|  
|6|やり直し|セカンダリ レプリカでページのフラッシュを再実行します。 再実行されるのを待機する間、ページは再実行キューに保持されます。|[SQL Server: データベース レプリカ > Redone Bytes/sec](~/relational-databases/performance-monitor/sql-server-database-replica.md)<br /><br /> [redo_queue_size](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) (KB) と [redo_rate](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)。<br /><br /> 待機の種類 [REDO_SYNC](~/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)|  
  
##  <a name="BKMK_FLOW_CONTROL_GATES"></a> フロー制御ゲート  
 プライマリ レプリカではフロー制御ゲートを使用して可用性グループが設計されています。このため、すべての可用性レプリカ上でネットワークやメモリ リソースなどのリソースが過剰消費されるのを回避することができます。 このようなフロー制御ゲートは、可用性レプリカの同期の正常性状態に影響を及ぼしませんが、可用性データベースの全体的なパフォーマンス (RPO を含む) には影響する可能性があります。  
  
 次の表に示すように、ログはプライマリ レプリカ上でキャプチャされると、フロー制御の 2 つのレベルの影響を受けるようになります。  
  
|||||  
|-|-|-|-|  
|**Level**|**ゲート数**|**メッセージ数**|**有用なメトリック**|  
|[Transport]|可用性レプリカごとに 1 つ|8192|拡張イベント **database_transport_flow_control_action**|  
|[データベース]|可用性データベースごとに 1 つ|11200 (x64)<br /><br /> 1600 (x86)|[DBMIRROR_SEND](~/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)<br /><br /> 拡張イベント **hadron_database_flow_control_action**|  
  
 いずれかのゲートのメッセージしきい値に達すると、ログ メッセージは特定のレプリカ、または特定のデータベースに送信されなくなります。 送信するメッセージに対して確認応答メッセージが受信され、結果として送信メッセージの数がしきい値を下回ると、メッセージを送信できるようになります。  
  
 フロー制御ゲートに加えて、ログ メッセージの送信を回避することができる要素がもう 1 つあります。 レプリカを同期すると、メッセージは確実にログ シーケンス番号 (LSN) の順序で送信および適用されます。 ログ メッセージが送信される前に、その LSN は最小の確認応答 LSN 番号と突き合わせてチェックされ、いずれかのしきい値を下回っているかどうかが確認されます (メッセージの種類に応じて)。 2 つの LSN 番号間の差がしきい値よりも大きい場合、メッセージは送信されません。 番号間の差が再びしきい値を下回ると、メッセージは送信されます。  
  
 2 つの有用なパフォーマンス カウンターである [SQL Server: 可用性レプリカ > フロー制御/秒](~/relational-databases/performance-monitor/sql-server-availability-replica.md)と [SQL Server: 可用性レプリカ > フロー制御時間 (ミリ秒/秒)](~/relational-databases/performance-monitor/sql-server-availability-replica.md)では、最後の 1 秒以内に、フロー制御がアクティブになった回数とフロー制御を待機していた時間を示します。 フロー制御の待機時間が長いと、RPO が大きくなります。 フロー制御の待機時間を長くする可能性のある問題の種類の詳細については、[Troubleshoot: Availability group exceeded RPO](troubleshoot-availability-group-exceeded-rpo.md) (トラブルシューティング: 可用性グループが RPO を超過した) を参照してください。  
  
##  <a name="BKMK_RTO"></a> フェールオーバー時間 (RTO) の推定  
 SLA での RTO は、特定の時点での Always On 実装のフェールオーバー時間に依存し、次の数式で表すことができます。  
  
 ![可用性グループの RTO の計算](media/always-on-rto.gif "可用性グループの RTO の計算")  
  
> [!IMPORTANT]  
>  可用性グループに複数の可用性データベースが含まれている場合、Tfailover が最も高い可用性データベースは RTO 準拠の制限値になります。  
  
 障害検出時間 Tdetection は、システムが障害を検出するのにかかる時間です。 この時間は、個々の可用性レプリカではなく、クラスター レベルの設定に依存します。 構成されている自動フェールオーバーの条件に応じて、SQL Server での重大な内部エラー (孤立したスピンロックなど) への瞬時の応答として、フェールオーバーをトリガーすることができます。 この場合、[sp_server_diagnostics &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md) エラー レポートが WSFC クラスターに送信されるのと同じ速さで検出が行われます (既定の間隔は正常性チェックのタイムアウトの 1/3)。 クラスターの正常性チェックのタイムアウトの時間 (既定では 30 秒) が経過したり、リソース DLL と SQL Server インスタンス間のリースの有効期限 (既定では 20 秒) が切れたりなど、タイムアウトが原因でフェールオーバーがトリガーされることもあります。 この場合、検出時間はタイムアウト間隔と同じ長さとなります。 詳細については、「[可用性グループの自動フェールオーバーのための柔軟なフェールオーバー ポリシー &#40;SQL Server&#41;](https://msdn.microsoft.com/library/hh710061(SQL.120).aspx)」を参照してください。  
  
 フェールオーバーの準備を整えるためにセカンダリ レプリカで実行する必要があることは、再実行でログの末尾をキャッチアップすることだけです。 再実行時間 Tredo は次の式を使用して計算します。  
  
 ![可用性グループの再実行時間の計算](media/always-on-redo.gif "可用性グループの再実行時間の計算")  
  
 ここで、*redo_queue* は [redo_queue_size](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) 内の値であり、*redo_rate* は [redo_rate](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) 内の値です。  
  
 フェールオーバーのオーバーヘッド時間 Toverhead には、WSFC クラスターをフェールオーバーしてデータベースをオンラインにするのにかかる時間が含まれます。 この時間は通常は短く一定です。  
  
##  <a name="BKMK_RPO"></a> データ損失の可能性 (RPO) の推定  
 SLA での RPO は、特定の時点での Always On 実装のデータ損失の可能性に依存します。 このデータ損失の可能性は次の式で表すことができます。  
  
 ![可用性グループの RPO の計算](media/always-on-rpo.gif "可用性グループの RPO の計算")  
  
 ここで、*log_send_queue* は、[log_send_queue_size](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) の値であり、*ログ生成速度*は、[SQL Server: データベース > Log Bytes Flushed/sec](~/relational-databases/performance-monitor/sql-server-databases-object.md) の値です。  
  
> [!WARNING]  
>  可用性グループに 1 つ以上の可用性データベースが含まれている場合、最高 Tdata_loss で可用性データベースの RPO 対応制限値になります。  
  
 ログ送信キューは、重大なエラーによって失われる可能性のあるすべてのデータを表します。 一見して、ログ送信速度 ([log_send_rate](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) を参照) ではなく、ログ生成速度が使用されているのは興味深いことです。 なお、RPO ではデータを同期する速度ではなく、データを生成する速度に基づいてデータ損失が測定されるにも関わらず、ログ送信速度を使用した場合は同期のための時間しか得られません。  
  
 Tdata_loss を推定するには、[last_commit_time](~/relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md) を使用する方法が簡単です。 プライマリ レプリカ上の DMV は、この値をすべてのレプリカにレポートします。 プライマリ レプリカの値とセカンダリ レプリカの値との差を計算することで、セカンダリ レプリカ上のログがプライマリ レプリカに追いつく速さを推定することができます。 前述のように、この計算からは、ログが生成される速度に基づいたデータ損失の可能性は得られませんが、近似値を指定する必要があります。  
  
##  <a name="BKMK_Monitoring_for_RTO_and_RPO"></a> RTO と RPO の監視  
 このセクションでは、可用性グループの RTO および RPO メトリックを監視する方法を実演します。 この実演の内容は、「[The Always On health model, part 2: Extending the health model](http://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)」 (Always On 正常性モデル、パート 2: 正常性モデルの拡張) で提供している GUI のチュートリアルに類似しています。  
  
 [フェールオーバー時間 (RTO) の推定](#BKMK_RTO) および[データ損失の可能性 (RPO) の推定](#BKMK_RPO) におけるフェールオーバー時間の計算およびデータ損失の可能性の計算の要素は、ポリシー管理ファセット "**データベース レプリカ状態**" の中でパフォーマンス メトリックとして便利に提供されています (「[SQL Server オブジェクトのポリシー ベースの管理ファセットの表示](~/relational-databases/policy-based-management/view-the-policy-based-management-facets-on-a-sql-server-object.md)」を参照)。 この 2 つのメトリックはスケジュールに従って監視することができます。メトリックが指定の RTO および RPO を超えた場合はそれぞれアラートが返されます。  
  
 デモ スクリプトでは、以下の特性を備え、それぞれのスケジュールに従って実行される 2 つのシステム ポリシーが作成されます。  
  
-   RTO ポリシーは 5 分ごとに評価され、推定フェールオーバー時間が 10 分を超えると失敗します。  
  
-   RPO ポリシーは 30 分ごとに評価され、推定データ損失が 1 時間を超えると失敗します。  
  
-   2 つのポリシーの構成は、すべての可用性レプリカ上で同じです。  
  
-   ポリシーはすべてのサーバー上で評価されますが、可用性グループ上ではローカルの可用性レプリカがプライマリ レプリカである場合にのみ評価されます。 ローカルの可用性レプリカがプライマリ レプリカでない場合、ポリシーは評価されません。  
  
-   プライマリ レプリカ上で Always On ダッシュボードを表示すると、ポリシー エラーを容易に確認できます。  

ポリシーを作成するには、可用性グループに参加しているすべてのサーバー インスタンス上で次の手順を実行します。  

1.  まだ開始していない場合は、[SQL Server エージェント サービスを開始](~/ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)します。  
  
2.  SQL Server Management Studio で、**[ツール]** メニューの **[オプション]** をクリックします。  
  
3.  **[SQL Server Always On]** タブで **[ユーザー定義の Always On ポリシーを有効にする]** を選択し、**[OK]** をクリックします。  
  
     この設定により、適切に構成されたカスタム ポリシーを Always On ダッシュボードに表示できるようになります。  
  
4.  次の仕様に基づいて[ポリシー ベースの管理条件](~/relational-databases/policy-based-management/create-a-new-policy-based-management-condition.md)を作成します。  
  
    -   **名前**: `RTO`  
  
    -   **ファセット**: **データベース レプリカ状態**  
  
    -   **フィールド**: `Add(@EstimatedRecoveryTime, 60)`  
  
    -   **演算子**: **<=**  
  
    -   **値**: `600`  
  
     この条件は、潜在的なフェールオーバー時間が 10 分 (エラー検出とフェールオーバーの両方ための 60 秒のオーバーヘッドも含まれる) を超えると失敗します。  
  
5.  次の仕様に基づいて 2 番目の[ポリシー ベースの管理条件](~/relational-databases/policy-based-management/create-a-new-policy-based-management-condition.md)を作成します。  
  
    -   **名前**: `RPO`  
  
    -   **ファセット**: **データベース レプリカ状態**  
  
    -   **フィールド**: `@EstimatedDataLoss`  
  
    -   **演算子**: **<=**  
  
    -   **値**: `3600`  
  
     この条件は、データ損失の可能性が 1 時間を超えると失敗します。  
  
6.  次の仕様に基づいて 3 番目の[ポリシー ベースの管理条件](~/relational-databases/policy-based-management/create-a-new-policy-based-management-condition.md)を作成します。  
  
    -   **名前**: `IsPrimaryReplica`  
  
    -   **ファセット**: **可用性グループ**  
  
    -   **フィールド**: `@LocalReplicaRole`  
  
    -   **演算子**: **=**  
  
    -   **値**: `Primary`  
  
     この条件では、特定の可用性グループのローカルの可用性レプリカがプライマリ レプリカであるかどうかがチェックされます。  
  
7.  次の仕様に基づいて[ポリシー ベースの管理ポリシー](~/relational-databases/policy-based-management/create-a-policy-based-management-policy.md)を作成します。  
  
    -   **[全般]** ページ:  
  
        -   **名前**: `CustomSecondaryDatabaseRTO`  
  
        -   **条件の確認**: `RTO`  
  
        -   **対象**: **IsPrimaryReplica AvailabilityGroup** の**すべての DatabaseReplicaState**  
  
             この設定により、ポリシーは必ず、ローカルの可用性レプリカがプライマリ レプリカである可用性グループのみで評価されます。  
  
        -   **評価モード**: **スケジュールで実行**  
  
        -   **スケジュール**: **CollectorSchedule_Every_5min**  
  
        -   **有効**: **選択**  
  
    -   **[説明]** ページ:  
  
        -   **カテゴリ**: **可用性データベースの警告**  
  
             この設定により、Always On ダッシュボードにポリシーの評価結果を表示できるようになります。  
  
        -   **説明**: **検出とフェールオーバーのオーバーヘッドが 1 分であると仮定すると、現在のレプリカの RTO は 10 分を超えています。すぐに、それぞれのサーバー インスタンスでのパフォーマンスの問題を調査する必要があります。**  
  
        -   **表示するテキスト**: **RTO を超過しました!**  
  
8.  次の仕様に基づいて 2 番目の[ポリシー ベースの管理ポリシー](~/relational-databases/policy-based-management/create-a-policy-based-management-policy.md)を作成します。  
  
    -   **[全般]** ページ:  
  
        -   **名前**: `CustomAvailabilityDatabaseRPO`  
  
        -   **条件の確認**: `RPO`  
  
        -   **対象**: **IsPrimaryReplica AvailabilityGroup** の**すべての DatabaseReplicaState**  
  
        -   **評価モード**: **スケジュールで実行**  
  
        -   **スケジュール**: **CollectorSchedule_Every_30min**  
  
        -   **有効**: **選択**  
  
    -   **[説明]** ページ:  
  
        -   **カテゴリ**: **可用性データベースの警告**  
  
        -   **説明**: **可用性データベースは、1 時間の RPO を超過しています。すぐに、可用性レプリカでのパフォーマンスの問題を調査する必要があります。**  
  
        -   **表示するテキスト**: **RPO を超過しました!**  
  
 完了すると、2 つの新しい SQL Server エージェント ジョブが作成されます (各ポリシー評価スケジュールに対して 1 つ)。 これらのジョブの名前は、**syspolicy_check_schedule** で始める必要があります。  
  
 評価結果を検査するために、ジョブの履歴を表示することができます。 評価エラーは、イベント ID 34052 で Windows アプリケーション ログ (イベント ビューアー内) にも記録されます。 また、ポリシー エラー発生時にアラートを送信するように SQL Server エージェントを構成することもできます。 詳細については、「[ポリシー管理者にポリシー エラーを通知する警告の構成](~/relational-databases/policy-based-management/configure-alerts-to-notify-policy-administrators-of-policy-failures.md)」を参照してください。  
  
##  <a name="BKMK_SCENARIOS"></a> パフォーマンスのトラブルシューティング シナリオ  
 次の表に、一般的なパフォーマンスに関連するトラブルシューティング シナリオを示します。  
  
|シナリオ|Description|  
|--------------|-----------------|  
|[トラブルシューティング: 可用性グループ接続の超過 RTO ](troubleshoot-availability-group-exceeded-rto.md)|データ損失のない自動フェールオーバーまたは計画的な手動フェールオーバーの後で、フェールオーバー時間が RTO を超過します。 または、同期コミット セカンダリ レプリカのフェールオーバー時間を推定したとき (自動フェールオーバー パートナーなど)、RTO を超過していることが判明します。|  
|[トラブルシューティング: 可用性グループ接続の超過 RPO ](troubleshoot-availability-group-exceeded-rpo.md)|強制的な手動フェールオーバーを実行した後で、データ損失が RPO より大きくなります。 または、非同期コミット セカンダリ レプリカのデータ損失の可能性を計算したとき、計算結果が RPO を超過していることが判明します。|  
|[トラブルシューティング: プライマリ上の変更がセカンダリ レプリカに反映されない](troubleshoot-primary-changes-not-reflected-on-secondary.md)|クライアント アプリケーションは、プライマリ レプリカの更新を正常に完了しますが、セカンダリ レプリカのクエリを実行すると、変更が反映されていないことが示されます。|  
  
##  <a name="BKMK_XEVENTS"></a> 有用な拡張イベント  
 **同期中の**状態にあるレプリカのトラブルシューティングを行う場合は、次の拡張イベントは便利です。  
  
|イベント名|カテゴリ|Channel|可用性レプリカ|  
|----------------|--------------|-------------|--------------------------|  
|redo_caught_up|トランザクション|デバッグ|セカンダリ|  
|redo_worker_entry|トランザクション|デバッグ|セカンダリ|  
|hadr_transport_dump_message|`alwayson`|デバッグ|プライマリ|  
|hadr_worker_pool_task|`alwayson`|デバッグ|プライマリ|  
|hadr_dump_primary_progress|`alwayson`|デバッグ|プライマリ|  
|hadr_dump_log_progress|`alwayson`|デバッグ|プライマリ|  
|hadr_undo_of_redo_log_scan|`alwayson`|分析|セカンダリ|  
  
  