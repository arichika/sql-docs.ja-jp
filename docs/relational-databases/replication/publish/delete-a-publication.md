---
title: パブリケーションの削除 | Microsoft Docs
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
- removing publications
- publications [SQL Server replication], deleting
- articles [SQL Server replication], deleting
- deleting publications
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
caps.latest.revision: 35
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d51c849d16d1bfdee09e83205c31440ab5095511
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="delete-a-publication"></a>パブリケーションの削除
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、またはレプリケーション管理オブジェクト (RMO) を使用して、パブリケーションを削除する方法について説明します。  
  
 **このトピックの内容**  
  
-   **パブリケーションを削除するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 **内の** [ローカル パブリケーション] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]フォルダーからパブリケーションを削除します。  
  
#### <a name="to-delete-a-publication"></a>パブリケーションを削除するには  
  
1.  [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]でパブリッシャーに接続し、サーバー ノードを展開します。  
  
2.  **[レプリケーション]** フォルダーを展開し、 **[ローカル パブリケーション]** フォルダーを展開します。  
  
3.  削除するパブリケーションを右クリックし、 **[削除]** をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 パブリケーションは、レプリケーションのストアド プロシージャを使用してプログラムから削除できます。 どのストアド プロシージャを使用するかは、削除するパブリケーションの種類によって異なります。  
  
> [!NOTE]  
>  パブリケーションを削除しても、パブリッシュされたオブジェクトはパブリケーション データベースから削除されず、対応するオブジェクトはサブスクリプション データベースから削除されません。 これらのオブジェクトは、必要に応じて `DROP <object>` コマンドを使用し、手動で削除します。  
  
#### <a name="to-delete-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションを削除するには  
  
1.  次のいずれかの操作を行います。  
  
    -   単一のパブリケーションを削除するには、パブリッシャーのパブリケーション データベースで [sp_droppublication](../../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md) を実行します。  
  
    -   すべてのパブリケーションを削除し、パブリッシュされたデータベースからすべてのレプリケーション オブジェクトを削除するには、パブリッシャーで [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) を実行します。 **@type** には **tran** の値を指定します。 (省略可) ディストリビューターにアクセスできない場合や、ディストリビューターのデータベース ステータスがオフラインになっている可能性がある場合は、 **@force** @type **@force**フォルダーからパブリケーションを削除します。 (省略可) パブリケーション データベースに対して **@dbname** を実行しない場合は、 [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) にデータベースの名前を指定します。  
  
        > [!NOTE]  
        >  **@force** に **1** を指定すると、レプリケーション関連のパブリッシング オブジェクトがデータベース上に残される場合があります。  
  
2.  (省略可) このデータベースに他のパブリケーションが存在しない場合は、[sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) を実行し、スナップショット レプリケーションまたはトランザクション レプリケーションを使用した、現在のデータベースのパブリケーションを無効にします。  
  
3.  (省略可) サブスクライバーのサブスクリプション データベースで [sp_subscription_cleanup](../../../relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql.md) を実行して、サブスクリプション データベースに残っているレプリケーション メタデータをすべて削除します。  
  
#### <a name="to-delete-a-merge-publication"></a>マージ パブリケーションを削除するには  
  
1.  次のいずれかの操作を行います。  
  
    -   単一のパブリケーションを削除するには、パブリッシャーのパブリケーション データベースで [sp_dropmergepublication &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md) を実行します。  
  
    -   すべてのパブリケーションを削除し、パブリッシュされたデータベースからすべてのレプリケーション オブジェクトを削除するには、パブリッシャーで [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) を実行します。 **@type** には **merge** を指定します。 (省略可) ディストリビューターにアクセスできない場合や、ディストリビューターのデータベース ステータスがオフラインになっている可能性がある場合は、 **@force** @type **@force**フォルダーからパブリケーションを削除します。 (省略可) パブリケーション データベースに対して **@dbname** を実行しない場合は、 [sp_removedbreplication](../../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) にデータベースの名前を指定します。  
  
        > [!NOTE]  
        >  **@force** に **1** を指定すると、レプリケーション関連のパブリッシング オブジェクトがデータベース上に残される場合があります。  
  
2.  (省略可) このデータベースに他のパブリケーションが存在しない場合は、[sp_replicationdboption &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md) を実行し、マージ レプリケーションを使用した、現在のデータベースのパブリケーションを無効にします。  
  
3.  (省略可) サブスクライバー側のサブスクリプション データベースに対して [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql.md) を実行し、サブスクリプション データベースに残っているレプリケーション メタデータをすべて削除します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例は、トランザクション パブリケーションを削除し、データベースのトランザクション パブリッシングを無効にする方法を示しています。 すべてのサブスクリプションがあらかじめ削除されていることを想定しています。 詳細については、「 [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) 」または「 [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md)」を参照してください。  
  
 [!code-sql[HowTo#sp_droppublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_1.sql)]  
  
 次の例は、マージ パブリケーションを削除し、データベースのマージ パブリッシングを無効にする方法を示しています。 すべてのサブスクリプションがあらかじめ削除されていることを想定しています。 詳細については、「 [Delete a Pull Subscription](../../../relational-databases/replication/delete-a-pull-subscription.md) 」または「 [Delete a Push Subscription](../../../relational-databases/replication/delete-a-push-subscription.md)」を参照してください。  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../relational-databases/replication/codesnippet/tsql/delete-a-publication_2.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
 レプリケーション管理オブジェクト (RMO) を使用することで、プログラムによってパブリケーションを削除できます。 パブリケーションの削除に使用する RMO クラスは、削除するパブリケーションの種類によって異なります。  
  
#### <a name="to-remove-a-snapshot-or-transactional-publication"></a>スナップショット パブリケーションまたはトランザクション パブリケーションを削除するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.TransPublication> クラスのインスタンスを作成します。  
  
3.  パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、パブリケーションが存在することを確認します。 このプロパティの値が **false**である場合は、手順 3. でパブリケーション プロパティが不適切に定義されたか、パブリケーションが存在していません。  
  
5.  <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> メソッドを呼び出します。  
  
6.  (省略可) このデータベースに他のトランザクション パブリケーションが存在する場合は、次に示すように、トランザクション パブリッシングに対してデータベースを無効にすることができます。  
  
    1.  <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのインスタンスを作成します。 手順 1. の <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> インスタンスを <xref:Microsoft.SqlServer.Management.Common.ServerConnection> プロパティに設定します。  
  
    2.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。 このメソッドにより **false**が返された場合は、データベースが存在することを確認してください。  
  
    3.  パブリケーションの <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> プロパティを **false**フォルダーからパブリケーションを削除します。  
  
    4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。  
  
7.  接続を閉じます。  
  
#### <a name="to-remove-a-merge-publication"></a>マージ パブリケーションを削除するには  
  
1.  <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスを使用して、パブリッシャーへの接続を作成します。  
  
2.  <xref:Microsoft.SqlServer.Replication.MergePublication> クラスのインスタンスを作成します。  
  
3.  パブリケーションの <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> プロパティおよび <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> プロパティを設定し、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティに手順 1. で作成した接続を設定します。  
  
4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> プロパティをチェックして、パブリケーションが存在することを確認します。 このプロパティの値が **false**である場合は、手順 3. でパブリケーション プロパティが不適切に定義されたか、パブリケーションが存在していません。  
  
5.  <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> メソッドを呼び出します。  
  
6.  (省略可) このデータベースに他のマージ パブリケーションが存在する場合は、次に示すように、マージ パブリッシングに対してデータベースを無効にすることができます。  
  
    1.  <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> クラスのインスタンスを作成します。 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティを、手順 1. の <xref:Microsoft.SqlServer.Management.Common.ServerConnection> のインスタンスに設定します。  
  
    2.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> メソッドを呼び出します。 このメソッドが **false**を返す場合、データベースが存在するかどうかを確認してください。  
  
    3.  パブリケーションの <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> プロパティを **false**フォルダーからパブリケーションを削除します。  
  
    4.  <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> メソッドを呼び出します。  
  
7.  接続を閉じます。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次の例では、トランザクション パブリケーションを削除します。 このデータベースに対して他のトランザクション パブリケーションが存在しない場合は、トランザクション パブリッシングも無効になります。  
  
 [!code-cs[HowTo#rmo_DropTranPub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 次の例では、マージ パブリケーションを削除します。 このデータベースに対して他のマージ パブリケーションが存在しない場合は、マージ パブリッシングも無効になります。  
  
 [!code-cs[HowTo#rmo_DropMergePub](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## <a name="see-also"></a>参照  
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
