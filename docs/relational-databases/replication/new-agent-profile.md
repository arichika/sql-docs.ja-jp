---
title: '[新しいエージェント プロファイル] | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.profiles.newperfprofile.f1
helpviewer_keywords:
- New Agent Profile dialog box
ms.assetid: ebf59330-a421-45a5-9020-0484a96852bc
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 24a997bb8d14b331b8669fb2ce363b929a3279ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="new-agent-profile"></a>[新しいエージェント プロファイル]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[新しいエージェント プロファイル]** ダイアログ ボックスを使用すると、新しいプロファイルを作成できます。 新しいプロファイルは常に既存のプロファイルに基づきますが、アプリケーション要件に一致するように変更することもできます。 プロファイルを作成したら、 **[エージェント プロファイル]** ダイアログ ボックスで、既存のエージェントおよび今後のエージェントのジョブに適用できます。 エージェントのパラメーター値は、[\<**AgentProfileName> のプロパティ]** ダイアログ ボックスで編集できます。  
  
## <a name="options"></a>および  
 **名前**  
 プロファイルの名前を入力します。  
  
 **[説明]**  
 プロファイルの説明を入力します。  
  
 **パラメーター**  
 プロファイルに含まれるエージェント パラメーターです。 新しいプロファイルが基づくプロファイルは、必ずしもパラメーターごとの値を指定する必要はありません。 指定されたエージェントで有効なパラメーターをすべて表示するには、 **[このプロファイルに使用されているパラメーターのみ表示する]** チェック ボックスをオフにします。 各パラメーターの詳細については、次を参照してください。  
  
-   [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
-   [レプリケーション ログ リーダー エージェント](../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
-   [Replication Distribution Agent](../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
-   [レプリケーション マージ エージェント](../../relational-databases/replication/agents/replication-merge-agent.md)  
  
-   [レプリケーション キュー リーダー エージェント](../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
 **既定値**  
 各エージェント パラメーターの既定値です。  
  
 **値**  
 新しいプロファイルが基づくプロファイル内のパラメーターに対して指定された値です。 パラメーター値を変更するには、このフィールドを編集します。  
  
 **[このプロファイルに使用されているパラメーターのみ表示する]**  
 指定されたエージェントに有効なパラメーターをすべて表示するにはオフにします。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェント プロファイルの操作](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [レプリケーション エージェントの概要](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)  
  
  
