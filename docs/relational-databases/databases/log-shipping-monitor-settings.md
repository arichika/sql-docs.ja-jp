---
title: '[ログ配布モニターの設定] | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: log-shipping
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.databaseproperties.logshipping.settings.monitor.f1
ms.assetid: 45e2ba7d-b3aa-4643-9451-bcb991572314
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eb71c5c749845438521113ba82f86e6d096bc7d7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="log-shipping-monitor-settings"></a>[ログ配布モニターの設定]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このページを使用すると、ログ配布監視サーバーのプロパティを構成および変更できます。  
  
 ログ配布の概念については、「[ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[監視サーバー インスタンス]**  
 ログ配布構成の監視サーバーとして現在構成されているサーバー インスタンスの名前を表示します。  
  
 **のインスタンスに接続するときには、**  
 監視サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを選択して接続します。 接続に使用するアカウントは、セカンダリ サーバーのインスタンスの sysadmin 固定サーバー ロールのメンバーである必要があります。  
  
 **[ジョブのプロキシ アカウントを借用する]**  
 監視サーバー インスタンスに接続するときに、ログ配布で SQL Server エージェントのプロキシ アカウントを借用します。 バックアップ、コピー、および復元プロセスでは、監視サーバーに接続してログ配布操作の状態を更新できなければなりません。  
  
 **[次の SQL Server ログインを使用する]**  
 監視サーバー インスタンスに接続するときに、ログ配布で特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用できるようにします。 バックアップ、コピー、および復元プロセスでは、監視サーバーに接続してログ配布操作の状態を更新できなければなりません。 ログ配布で特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを使用する場合にこのオプションを選択し、ログインおよびパスワードを指定します。  
  
 **[次の期間以後の履歴を削除する]**  
 ログ配布履歴情報を削除する前に、監視サーバー上に保持する期間を指定します。  
  
 **ジョブ名**  
 バックアップまたは復元しきい値が超過したときに、警告を発行するためにログ配布によって使用される SQL Server エージェントの警告ジョブの名前を示します。 このジョブを作成しているときは、ボックスに入力することで名前を変更できます。  
  
 **[スケジュール]**  
 SQL Server エージェントの警告ジョブの現在のスケジュールを示します。  
  
 **[編集]**  
 SQL Server エージェントの警告ジョブのパラメーターを変更します。  
  
 **[このジョブを無効にする]**  
 SQL Server エージェントの警告ジョブを中断します。  
  
  
