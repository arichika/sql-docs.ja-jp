---
title: マージ レプリケーションのバックアップと復元の方式 | Microsoft Docs
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
- recovery [SQL Server replication], merge replication
- backups [SQL Server replication], merge replication
- restoring [SQL Server replication], merge replication
- merge replication [SQL Server replication], backup and restore
ms.assetid: b8ae31c6-d76f-4dd7-8f46-17d023ca3eca
caps.latest.revision: 48
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c3e727b15d9e963996cfa4d9616ecf723bcff5e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="strategies-for-backing-up-and-restoring-merge-replication"></a>マージ レプリケーションのバックアップと復元の方式
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  マージ レプリケーションでは、次のデータベースを定期的にバックアップします。  
  
-   パブリッシャーにあるパブリケーション データベース  
  
-   ディストリビューターにあるディストリビューション データベース  
  
-   各サブスクライバーにあるサブスクリプション データベース  
  
-   パブリッシャー、ディストリビューター、およびすべてのサブスクライバーにある **master** および **msdb** システム データベース。 これらのデータベースは、相互に関連するレプリケーション データベースとして、同時にバックアップする必要があります。 たとえば、パブリッシャーでパブリケーション データベースをバックアップするときに、 **master** および **msdb** データベースも同時にバックアップします。 パブリケーション データベースを復元するときは、 **master** および **msdb** データベースのレプリケーションの構成と設定が、パブリケーション データベースと一致していることを確認します。  
  
 定期的なログ バックアップを実行する場合は、レプリケーション関連の変更をログ バックアップでキャプチャする必要があります。 ログ バックアップを実行しない場合は、レプリケーションに関連する設定を変更するたびに、バックアップを実行する必要があります。 詳細については、「 [一般にバックアップの更新が必要になるアクション](../../../relational-databases/replication/administration/common-actions-requiring-an-updated-backup.md)」を参照してください。  
  
 以下で詳しく説明するパブリケーション データベースのバックアップと復元の方法のいずれかを選択し、ディストリビューション データベースとサブスクリプション データベースに対する推奨事項に従ってください。  
  
## <a name="backing-up-and-restoring-the-publication-database"></a>パブリケーション データベースのバックアップと復元  
 マージ パブリケーション データベースの復元方法は 2 とおりあります。 バックアップからパブリケーション データベースを復元した後に、次のいずれかを実行する必要があります。  
  
-   パブリケーション データベースとサブスクリプション データベースを同期する。  
  
-   パブリケーション データベースにあるパブリケーションへのすべてのサブスクリプションを再初期化する。  
  
 これらのいずれかの方法を使用すると、復元の実行後にパブリッシャーとすべてのサブスクライバーが同期されます。  
  
> [!NOTE]  
>  ID 列を含むテーブルを使用している場合は、復元後、正しい ID 範囲を割り当てる必要があります。 詳細については、「[Replicate Identity Columns](../../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
### <a name="synchronizing-the-publication-database"></a>パブリケーション データベースの同期  
 パブリケーション データベースとサブスクリプション データベースを同期すると、パブリケーション データベースで以前に変更され、復元されたバックアップに表示されていない変更を  1 つ以上のサブスクリプション データベースからアップロードできます。 アップロードできるデータは、パブリケーションのフィルター選択方法によって次のように異なります。  
  
-   パブリケーションがフィルター選択されていない場合は、最新のサブスクライバーと同期することでパブリケーション データベースを最新の状態に更新できます。  
  
-   パブリケーションがフィルター選択されている場合は、パブリケーションを最新の状態に更新できない場合があります。 たとえば、各サブスクリプションが 1 つの地域 (北、東、南、西のいずれか) の顧客データのみを受信できるようにパーティション分割されているテーブルがあるとします。 データの各パーティションに 1 つ以上のサブスクライバーがある場合、各パーティションのサブスクライバーと同期することにより、パブリケーション データベースを最新の状態に更新できます。 ただし、たとえば、西パーティションのデータがすべてのサブスクライバーにレプリケートされていない場合は、パブリッシャーでこのデータを最新の状態に更新することはできません。  
  
> [!IMPORTANT]  
>  パブリケーション データベースとサブスクリプション データベースを同期することによって、復元対象のパブリッシュされたテーブルを、バックアップから復元されたパブリッシュされていないテーブルよりも新しい状態にすることができます。  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] よりも前のバージョンの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]を実行しているサブスクライバーと同期する場合は、サブスクリプションを匿名にすることはできません。このサブスクリプションはクライアント サブスクリプションまたはサーバー サブスクリプション (前のリリースではローカル サブスクリプションとグローバル サブスクリプションと呼ばれていました) にする必要があります。  
  
 サブスクリプションを同期するには、「 [Synchronize a Push Subscription](../../../relational-databases/replication/synchronize-a-push-subscription.md) 」および「 [Synchronize a Pull Subscription](../../../relational-databases/replication/synchronize-a-pull-subscription.md)」を参照してください。  
  
### <a name="reinitializing-all-subscriptions"></a>すべてのサブスクリプションの再初期化  
 すべてのサブスクリプションを再初期化すると、すべてのサブスクライバーを、復元されたパブリケーション データベースと一貫性のある状態に保つことができます。 特定のパブリケーション データベースのバックアップで再現される、以前の状態にトポロジ全体を戻す場合は、この方法を使用する必要があります。 たとえば、誤って実行したバッチ操作から復旧するメカニズムとして、パブリケーション データベースをより古い時点に復元する場合に、すべてのサブスクリプションを再初期化することができます。  
  
 このオプションを選択する場合には、パブリケーション データベースを復元した直後に、再初期化されたサブスクライバーに配信するための新しいスナップショットを生成します。  
  
 サブスクリプションを再初期化するには、「 [Reinitialize a Subscription](../../../relational-databases/replication/reinitialize-a-subscription.md)」を参照してください。  
  
 スナップショットを作成および適用するには、「 [初期スナップショットの作成および適用](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md) 」および「 [パラメーター化されたフィルターを使用したパブリケーションのスナップショットの作成](../../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」を参照してください。  
  
## <a name="backing-up-and-restoring-the-distribution-database"></a>ディストリビューション データベースのバックアップと復元  
 マージ レプリケーションでは、ディストリビューション データベースを定期的にバックアップする必要があります。この場合、使用されるバックアップがディストリビューターを使用するすべてのパブリケーションの最短の保有期間よりも古くない限り、特に注意することなく復元できます。 たとえば、保有期間がそれぞれ 10、20、および 30 日に設定されている 3 つのパブリケーションがある場合は、10 日より長く経過したバックアップはデータベースの復元に使用できません。 マージ レプリケーションでは、ディストリビューション データベースの役割が制限されています。変更の追跡に使用されるすべてのデータは保存されず、トランザクション レプリケーションのような、サブスクリプション データベースの転送先となるマージ レプリケーションの変更の一時的な保存場所も用意されません。  
  
## <a name="backing-up-and-restoring-a-subscription-database"></a>サブスクリプション データベースのバックアップと復元  
 サブスクリプション データベースを正常に復元するためには、サブスクライバーとパブリッシャーを同期してから、サブスクリプション データベースをバックアップする必要があります。また、サブスクリプション データベースの復元後にも同期を行う必要があります。  
  
-   サブスクリプション データベースのバックアップの前にパブリッシャーと同期することにより、サブスクライバーをバックアップから復元した場合に、サブスクリプションをパブリケーションの保有期間内の状態に保つことができます。 たとえば、保有期間が 10 日間に設定されているパブリケーションがあるとします。 最後の同期が 8 日前で、現在バックアップが実行されています。 4 日後にバックアップが復元されると、最後の同期は 12 日前に行われたことになり、保有期間は過ぎてしまいます。 この場合は、サブスクライバーを再初期化する必要があります。 バックアップの前にサブスクライバーを同期しておくと、サブスクリプション データベースを保有期間内の状態に保つことができます。  
  
     サブスクライバーがサブスクライブするすべてのパブリケーションの最短の保有期間よりも古いバックアップは使用できません。 たとえば、保有期間がそれぞれ 10、20、および 30 日に設定されている 3 つのパブリケーションをサブスクライバーがサブスクライブする場合、10 日より長く経過したバックアップはデータベースの復元に使用できません。  
  
-   復元後にサブスクリプション データベースとそれぞれのパブリケーションを同期すると、パブリッシャーのすべての変更を含む最新の状態にサブスクライバーを保つことができます。  
  
 パブリケーションの保有期間を設定する場合は、「[サブスクリプションの有効期限の設定](../../../relational-databases/replication/publish/set-the-expiration-period-for-subscriptions.md)」を参照してください。  
  
 サブスクリプションを同期するには、「 [プッシュ サブスクリプションの同期](../../../relational-databases/replication/synchronize-a-push-subscription.md) 」および「 [プル サブスクリプションの同期](../../../relational-databases/replication/synchronize-a-pull-subscription.md)」を参照してください。  
  
## <a name="backing-up-and-restoring-a-republishing-database"></a>再パブリッシュ データベースのバックアップと復元  
 あるデータベースがパブリッシャーからのデータをサブスクライブしてから、同じデータを別のサブスクリプション データベースにパブリッシュするとき、このデータベースのことを再パブリッシュ データベースと言います。 再パブリッシュ データベースを復元する場合は、このトピックの「パブリケーション データベースのバックアップと復元」および「サブスクリプション データベースのバックアップと復元」で説明されているガイドラインに従ってください。  
  
## <a name="see-also"></a>参照  
 [SQL Server データベースのバックアップと復元](../../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [Back Up and Restore Replicated Databases (レプリケートされたデータベースのバックアップと復元)](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)  
  
  
