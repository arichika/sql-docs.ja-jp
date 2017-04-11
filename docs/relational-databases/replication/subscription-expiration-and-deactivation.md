---
title: "サブスクリプションの有効期限と非アクティブ化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ディストリビューター [SQL Server レプリケーション], ディストリビューション保有期間"
  - "サブスクリプション [SQL Server レプリケーション]、有効期限"
  - "パブリケーション [SQL Server レプリケーション], パブリケーション保有期間"
  - "有効期限 [SQL Server レプリケーション]"
  - "保有期間 [SQL Server レプリケーション]"
  - "パブリケーション保有期間"
  - "ディストリビューション保有期間 (distribution retention period)"
  - "サブスクリプション [SQL Server レプリケーション], 非アクティブ化"
  - "サブスクリプションの非アクティブ化"
ms.assetid: 4d03f5ab-e721-4f56-aebc-60f6a56c1e07
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# サブスクリプションの有効期限と非アクティブ化
  サブスクリプションが非アクティブ化できますまたはに同期されない場合は、有効期限が切れる内で、指定した *保有期間*します。 行われる処理は、レプリケーションの種類と保有期間が過ぎているかどうかによって異なります。  
  
 保有期間を設定するを参照してください [されたサブスクリプションの有効期間を設定](../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md), 、[#40; (&)、トランザクション パブリケーションのディストリビューションの保有期間を設定。SQL Server Management Studio と #41;](../../relational-databases/replication/set distribution retention period for transactional publications.md), 、および [パブリッシングとディストリビューション](../../relational-databases/replication/configure-publishing-and-distribution.md)します。  
  
## トランザクション レプリケーション  
 トランザクション レプリケーションでは、最大ディストリビューション保有期間 (、 **@max_distretention** のパラメーター [sp_adddistributiondb & #40 です。Transact-SQL と #41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md))パブリケーションの保有期間 (、 **@retention** のパラメーター [sp_addpublication & #40 です。Transact-SQL と #41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md))。  
  
-   最大ディストリビューション保有期間 (既定値は 72 時間) 内にサブスクリプションが同期されていないと、サブスクライバーに配信されていないディストリビューション データベース内の変更は、サブスクリプションはマークによって非アクティブ化、 **ディストリビューションのクリーンアップ** ディストリビューターで実行されるジョブです。 サブスクリプションを再初期化する必要があります。  
  
-   サブスクリプションが有効期限が切れるし、削除するパブリケーションの保有期間 (既定値は 336 時間) 内で、サブスクリプションが同期していない場合、 **期限切れサブスクリプションのクリーンアップを** 、パブリッシャーで実行されるジョブです。 サブスクリプションを再作成し、同期する必要があります。  
  
     プッシュ サブスクリプションの期限が切れた場合は完全に削除されますが、プル サブスクリプションの場合は削除されません。 プル サブスクリプションは、サブスクライバーでクリーンアップする必要があります。 詳細については、次を参照してください。 [プル サブスクリプションを削除](../../relational-databases/replication/delete-a-pull-subscription.md)します。  
  
## マージ レプリケーション  
 マージ レプリケーションでは、パブリケーションの保有期間 (、 **@retention** と **@retention_period_unit** のパラメーター [sp_addmergepublication & #40 です。Transact-SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md))。 サブスクリプションが期限切れになると、そのサブスクリプションのメタデータが削除されるため、サブスクリプションを再初期化する必要があります。 によって、再初期化されていないサブスクリプションが破棄された、 **期限切れサブスクリプションのクリーンアップを** 、パブリッシャーで実行されるジョブです。 既定では、このジョブは毎日実行されます。このジョブにより、パブリケーションの保有期間の 2 倍の期間にわたって同期されなかったすべてのプッシュ サブスクリプションが削除されます。 例:  
  
-   パブリケーションの保有期間が 14 日間である場合、サブスクリプションは 14 日以内に同期されなかった場合に期限切れになる可能性があります。  
  
     パブリッシャーが実行されている場合 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] やそれ以降のバージョンと、サブスクリプションのエージェントされて [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] または以降のバージョンのサブスクリプションのみが切れたサブスクリプションのパーティションのデータに対する変更が発生した場合。 たとえば、サブスクライバーが、ドイツの顧客に関する顧客データのみを受信するとします。 保有期間が 14 日間に設定されているとすると、最近 14 日間でドイツの顧客データに変更があった場合にのみ、このサブスクリプションは 14 日目に期限切れになります。  
  
-   最後の同期からの経過日数が 14 日から 27 日の間は、サブスクリプションを再初期化できます。  
  
-   最後の同期後 28 日目に、サブスクリプションは削除、 **期限切れサブスクリプションのクリーンアップを** ジョブです。 プッシュ サブスクリプションの期限が切れた場合は完全に削除されますが、プル サブスクリプションの場合は削除されません。 プル サブスクリプションは、サブスクライバーでクリーンアップする必要があります。 詳細については、次を参照してください。 [プル サブスクリプションを削除](../../relational-databases/replication/delete-a-pull-subscription.md)します。  
  
### マージ パブリケーションに対するパブリケーション保有期間の設定に関する注意点  
 マージ パブリケーションの保有期間を設定する場合は、以下の点に注意してください。  
  
-   マージ パブリケーションの保有期間には、異なるタイム ゾーンのサブスクライバーに対応するため、24 時間の猶予期間があります。 たとえば、保有期間を 1 日に設定した場合、実際の保有期間は 48 時間となります。  
  
-   マージ レプリケーション メタデータのクリーンアップは、パブリケーション保有期間に依存します。  
  
    -   保有期間が終了するまで、パブリケーションおよびサブスクリプション データベースでメタデータをクリーンアップすることはできません。 レプリケーション パフォーマンスを低下させる可能性があるため、保有期間に大きな値を指定する際は注意してください。 すべてのサブスクライバーが保有期間内で定期的に同期されることを確実に予測できる場合は、小さい値を使用することをお勧めします。  
  
    -   サブスクリプションの有効期限しないことを指定することは (値 0 を **@retention**) が強く推奨されてこの値は使用しないメタデータをクリーンアップできないためです。  
  
-   リパブリッシャーの保有期間は、元のパブリッシャーで設定されている保有期間以下の値に設定する必要があります。 また、すべてのパブリッシャーとその代替同期パートナーに対するパブリケーションの保有期間の値は、同じにする必要があります。 異なる値を使用すると、集約されなくなる可能性があります。 パブリケーションの保有期間の値を変更する必要がある場合は、サブスクライバーを再初期化して、データの未集約が発生しないようにします。  
  
-   クリーンアップ後、パブリケーションの保有期間を延長し、既にメタデータを削除したパブリッシャーとのマージをサブスクリプションが試行した場合、保有期間の値が増加しているため、そのサブスクリプションは期限切れになりません。 ただし、パブリッシャーには、サブスクライバーに変更をダウンロードするための十分なメタデータが存在しないため、未集約が発生します。  
  
## 参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  