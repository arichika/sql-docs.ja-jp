---
title: "Set Thresholds and Warnings in Replication Monitor | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "alerts [SQL Server replication]"
  - "Merge Agent, thresholds and warnings"
  - "Distribution Agent, thresholds and warnings"
  - "thresholds [SQL Server replication]"
  - "Replication Monitor, thresholds and warnings"
  - "パフォーマンスの監視 [SQL Server レプリケーション], しきい値と警告"
ms.assetid: 3a409c2c-b77e-4001-b81a-1dcd918618ec
caps.latest.revision: 33
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 33
---
# Set Thresholds and Warnings in Replication Monitor
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターには、パブリケーションおよびサブスクリプションの状態情報が表示されます。 既定で表示される警告は、初期化されていないサブスクリプションに対する警告だけですが、その他の条件に対する警告を有効にすることもできます。 トポロジに対する警告を有効にすることをお勧めします。この警告を有効にすると、状態やパフォーマンスに関する情報をタイムリーに受け取ることができます。  
  
 警告を有効にする際には、しきい値を指定します。 指定したしきい値に達したり、それを超えると、警告が表示されます (それより優先度の高い問題がない場合)。 しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。 以下のような条件について、警告を有効にすることができます。  
  
-   サブスクリプションの有効期限の残り時間  
  
     すべての種類のレプリケーションに適用できます。 サブスクリプションの状態が [として表示されている場合は、指定したしきい値に達するか超過は、 **まもなく期限切れ/期限切れ**します。  
  
-   指定した待機時間 (パブリッシャーでトランザクションがコミットされてから、対応するトランザクションがサブスクライバーでコミットされるまでの経過時間) の超過  
  
     トランザクション レプリケーションに適用できます。 指定したしきい値に達したり、それを超えたりすると、サブスクリプションの状態が " **パフォーマンス クリティカル**" と表示されます。  
  
-   指定した同期時刻を超えた場合。  
  
     マージ レプリケーションに適用できます。 として状態が表示される場合は、指定したしきい値に達するか超過は、 **長期マージ**します。 ダイヤルアップ接続とローカル エリア ネットワーク (LAN) 接続にそれぞれ別のしきい値を指定できます。  
  
-   指定した数の行を特定の時間内で処理できない場合。  
  
     マージ レプリケーションに適用できます。 指定したしきい値に達したり、それを超えたりすると、状態が " **パフォーマンス クリティカル**" と表示されます。 ダイヤルアップ接続と LAN 接続にそれぞれ別のしきい値を指定できます。  
  
 詳細については、警告の **パフォーマンス クリティカル** と **長期マージ**, を参照してください [レプリケーション モニターを使用してパフォーマンスを監視する](../../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)です。  
  
 **このトピックの内容**  
  
-   [トランザクション パブリケーションのしきい値と警告を設定する](#Transactional)  
  
-   [マージ パプリケーションのしきい値および警告を設定する](#Merge)  
  
-   [スナップショット パプリケーションのしきい値および警告を設定する](#Snapshot)  
  
##  <a name="Transactional"></a> トランザクション パブリケーションのしきい値と警告を設定するには  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[警告]** タブをクリックします。 このタブの各オプションに関する情報を表示するには、メニュー バーの **[ヘルプ]** をクリックしてください。  
  
3.  **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します]** チェック ボックスまたは **[待機時間がしきい値を超えた場合に警告します]**チェック ボックスのいずれかをオンにして警告を有効にします。  
  
4.  **[しきい値]** 列で警告のしきい値を設定します。 たとえば、手順 3. で **[待機時間がしきい値を超えた場合に警告します]** チェック ボックスをオンにした場合、 **[しきい値]** 列で **60 秒** の待機時間を選択します。  
  
5.  **[変更の保存]**をクリックします。  
  
#### しきい値の警告を構成するには  
  
1.  **[警告の構成]**をクリックします。  
  
2.  **[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]**をクリックします。  
  
     このダイアログ ボックスには、監視しきい値に関連していない警告を含め、すべての種類のパブリケーションに対する警告が表示されます。 詳細については、次を参照してください。 [レプリケーション エージェント イベントに対する警告を使用する](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)です。  
  
3.  オプションを設定、 **\< AlertName> 警告のプロパティ** ] ダイアログ ボックス。  
  
    -   **[全般]** ページで **[有効化]**をクリックし、警告を適用するデータベースを指定します。  
  
    -    **応答** ] ページで、電子メールを送信するし、ジョブを実行する必要があるかどうかを指定します。  
  
    -   **[オプション]** ページで、応答のテキストをカスタマイズします。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[閉じる]**をクリックします。  
  
##  <a name="Merge"></a> マージ パプリケーションのしきい値および警告を設定する  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[警告]** タブをクリックします。 このタブの各オプションに関する情報を表示するには、メニュー バーの **[ヘルプ]** をクリックしてください。  
  
3.  適切なチェック ボックスをオンにして警告を有効にします。  
  
    -   **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します]**  
  
    -   **[ダイヤルアップ接続のマージ長がしきい値を超えた場合に警告します]**  
  
    -   **[LAN 接続のマージ長がしきい値を超えた場合に警告します]**  
  
    -   **[LAN 接続で 1 秒あたりにマージされる行数がしきい値未満の場合に警告します]**  
  
    -   **[ダイヤルアップ接続で 1 秒あたりにマージされる行数がしきい値未満の場合に警告します]**  
  
4.  **[しきい値]** 列で警告のしきい値を設定します。 たとえば、手順 3. で **[ダイヤルアップ接続のマージ長がしきい値を超えた場合に警告します]** を選択した場合、 **[しきい値]** 列では **[10 分]** を選択します。  
  
5.  **[変更の保存]**をクリックします。  
  
#### しきい値の警告を構成するには  
  
1.  **[警告の構成]**をクリックします。  
  
2.  **[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]**をクリックします。  
  
     このダイアログ ボックスには、監視しきい値に関連していない警告を含め、すべての種類のパブリケーションに対する警告が表示されます。  
  
3.  オプションを設定、 **\< AlertName> 警告のプロパティ** ] ダイアログ ボックス。  
  
    -   **[全般]** ページで **[有効化]**をクリックし、警告を適用するデータベースを指定します。  
  
    -    **応答** ] ページで、電子メールを送信するし、ジョブを実行する必要があるかどうかを指定します。  
  
    -   **[オプション]** ページで、応答のテキストをカスタマイズします。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[閉じる]**をクリックします。  
  
##  <a name="Snapshot"></a> スナップショット パプリケーションのしきい値および警告を設定する  
  
1.  左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。  
  
2.  **[警告]** タブをクリックします。 このタブの各オプションに関する情報を表示するには、トップ メニューの **[ヘルプ]** をクリックしてください。  
  
3.  **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します。]**チェック ボックスをオンにし、警告を有効にします。  
  
4.  **[しきい値]** 列で警告のしきい値を設定します。 たとえば、 **[しきい値]** 列で **[70%]** の値を選択できます。  
  
5.  **[変更の保存]**をクリックします。  
  
#### しきい値の警告を構成するには  
  
1.  **[警告の構成]**をクリックします。  
  
2.  **[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]**をクリックします。  
  
     このダイアログ ボックスには、監視しきい値に関連していない警告を含め、すべての種類のパブリケーションに対する警告が表示されます。 詳細については、次を参照してください。 [レプリケーション エージェント イベントに対する警告を使用する](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)です。  
  
3.  オプションを設定、 **\< AlertName> 警告のプロパティ** ] ダイアログ ボックス。  
  
    -   **[全般]** ページで **[有効化]**をクリックし、警告を適用するデータベースを指定します。  
  
    -    **応答** ] ページで、電子メールを送信するし、ジョブを実行する必要があるかどうかを指定します。  
  
    -   **[オプション]** ページで、応答のテキストをカスタマイズします。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **[閉じる]**をクリックします。  
  
## 参照  
 [レプリケーションの監視](../../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  