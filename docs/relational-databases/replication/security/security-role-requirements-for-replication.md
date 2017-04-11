---
title: "レプリケーションのセキュリティ ロール要件 | Microsoft Docs"
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
  - "セキュリティ [SQL Server レプリケーション], ロール"
  - "ロール [SQL Server], レプリケーション"
ms.assetid: b324a80f-4319-4cb2-847b-1910c49d90e0
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# レプリケーションのセキュリティ ロール要件
  レプリケーションでは、ユーザーのログインがマップされているロールに基づいて、ユーザーが実行できる操作が制限されます。 レプリケーションが特定の権限を与え、 **sysadmin** 固定サーバー ロール、 **db_owner** パブリケーション アクセス リスト (PAL) の固定データベース ロール、およびログインします。  
  
## レプリケーション セットアップのセキュリティ ロール要件  
 次の表に、一般的なレプリケーション セットアップ タスクに必要な認証レベルをまとめます。  
  
|セットアップ タスク|必要なメンバーシップ|  
|----------------|----------------------------|  
|ディストリビューター、パブリッシャー、またはサブスクライバーの有効化。|**sysadmin** パブリッシャーのサーバーの役割です。|  
|レプリケーション用のデータベースの有効化。|**sysadmin** パブリッシャーのサーバーの役割です。|  
|パブリケーションの作成。|**db_owner** 、パブリッシャー側でパブリケーション データベースのデータベース ロールまたは **sysadmin** パブリッシャーのサーバーの役割です。|  
|パブリケーション プロパティの表示。|パブリッシャー、PAL のメンバー **db_owner** 、パブリッシャー側でパブリケーション データベースのデータベース ロールまたは **sysadmin** パブリッシャーのサーバーの役割です。|  
|サブスクリプションの作成。|**db_owner** 、パブリッシャー側でパブリケーション データベースのデータベース ロールまたは **sysadmin** パブリッシャーのサーバーの役割です。<br /><br /> **db_owner** 、サブスクライバーでサブスクリプション データベースのデータベース ロールまたは **sysadmin** サブスクライバー上のサーバーの役割です。|  
|エージェント プロファイルの構成。|**sysadmin** 、ディストリビューター側のサーバーの役割です。|  
  
## レプリケーション メンテナンスのセキュリティ ロール要件  
 次の表に、一般的なレプリケーション メンテナンス タスクに必要な認証レベルをまとめます。  
  
|メンテナンス タスク|必要なメンバーシップ|  
|----------------------|----------------------------|  
|ディストリビューター、パブリッシャー、またはサブスクライバーの変更または削除。|**sysadmin** 適切なサーバー上のサーバーの役割です。|  
|パブリケーションの変更または削除。|**db_owner** 、パブリッシャー側でパブリケーション データベースのデータベース ロールまたは **sysadmin** パブリッシャーのサーバーの役割です。|  
|パブリッシャーでのサブスクリプションの変更または削除。|**db_owner** 、パブリッシャー側でパブリケーション データベースのデータベース ロールまたは **sysadmin** パブリッシャーのサーバーの役割です。|  
|サブスクライバーでのサブスクリプションの変更または削除。|**db_owner** 、サブスクライバーでサブスクリプション データベースのデータベース ロールまたは **sysadmin** サブスクライバー上のサーバーの役割です。|  
|サブスクリプションへの再初期化マークの設定。|プッシュ サブスクリプション: **db_owner** 、パブリッシャー側でパブリケーション データベースのデータベース ロールまたは **sysadmin** パブリッシャーのサーバーの役割です。<br /><br /> プル サブスクリプション: **db_owner** 、サブスクライバーでサブスクリプション データベース内のデータベース ロールまたは **sysadmin** サブスクライバー上のサーバーの役割です。|  
|レプリケーション モニターを使用した、レプリケーションの利用状況、エラー、および履歴の表示。 ユーザーは、そのユーザーのメンバーである限り、エージェントのプロファイル、スケジュール、および、変更できません、 **sysadmin** サーバーの役割です。|**replmonitor** 、ディストリビューターのディストリビューション データベースのデータベース ロールまたは **sysadmin** 、ディストリビューター側のサーバーの役割です。|  
|レプリケーション エージェントのメンテナンス。|**db_owner** 適切なデータベースのデータベース ロールまたは **sysadmin** 適切なサーバー上のサーバーの役割です。<br /><br /> エージェントがユーザーによって作成された場合、 **sysadmin** ロール、およびプロキシ アカウントが指定されていないエージェントは、エージェントのコンテキストで実行、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント アカウントです。 ここでのユーザーに、 **db_owner** ロールは、エージェントに関連付けられているジョブを変更できません。|  
|レプリケーション エージェントの起動または停止。|エージェント ジョブの所有者または **sysadmin** 適切なサーバー上のサーバーの役割です。|  
  
## 参照  
 [レプリケーション セキュリティの推奨事項](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [セキュリティと保護と #40 です。レプリケーションと #41 です。](../../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  