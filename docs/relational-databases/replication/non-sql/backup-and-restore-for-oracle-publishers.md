---
title: Oracle パブリッシャーのバックアップと復元 | Microsoft Docs
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
- recovery [SQL Server replication], Oracle publishing
- backups [SQL Server replication], Oracle publishing
- Oracle publishing [SQL Server replication], backup and restore
- restoring [SQL Server replication], Oracle publishing
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1a2febece47887fa801dc49bdbd0c4d0f2fe242e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="backup-and-restore-for-oracle-publishers"></a>Oracle パブリッシャーのバックアップと復元
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  バックアップと復元を実行する場合は、次のガイドラインに従ってください。  
  
-   パブリッシャーのバックアップ中は、ログ リーダー エージェントを実行したり、パブリッシュされたテーブルでその他のデータベースの処理を実行しないようにします。  
  
-   パブリッシャーとディストリビューターは同時にバックアップします。  
  
-   パブリッシャーまたはディストリビューターを復元する必要がある場合は、すべてのサブスクリプションを再初期化します。  
  
-   バックアップからサブスクライバーを復元するには (サブスクリプションの再初期化は不要)、前回のサブスクリプション データベースのバックアップ完了後にディストリビューション データベースに配信されたトランザクションも使用できる必要があります。 トランザクションが使用できる時間の長さは、ディストリビューションの保有期間の設定によって異なります。 これらの設定については、「[サブスクリプションの有効期限と非アクティブ化](../../../relational-databases/replication/subscription-expiration-and-deactivation.md)」を参照してください。  
  
-   データベースを復元した結果、パブリッシャーまたはディストリビューターが同期しなくなった場合は、レプリケーション エージェントによってエラー メッセージが記録されます。 この時点で、関連するパブリケーションとサブスクリプションをすべて削除して再作成する必要があります。  
  
    1.  パブリケーションおよびサブスクリプションの定義のスクリプトを作成します。 詳細については、「 [Scripting Replication](../../../relational-databases/replication/scripting-replication.md)」を参照してください。  
  
         パブリッシャーとディストリビューターの状態のバージョン間でパブリケーションの定義が変更された場合は、スクリプトを変更する必要があります。  
  
    2.  パブリケーションとサブスクリプションを削除します。  
  
    3.  手順 1. で作成したスクリプトを実行します。  
  
     パブリッシャーを削除および再構成する必要がある場合は、 **MSSQLSERVERDISTRIBUTOR** パブリック シノニムと、 **CASCADE** オプションで構成した Oracle レプリケーション ユーザーを削除して、Oracle パブリッシャーからすべてのレプリケーション オブジェクトを削除します。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータベースのバックアップと復元](../../../relational-databases/replication/administration/back-up-and-restore-replicated-databases.md)   
 [Configure an Oracle Publisher (Oracle パブリッシャーの構成)](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle パブリッシングの概要](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  
