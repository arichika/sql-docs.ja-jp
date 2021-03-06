---
title: パブリケーション情報、[警告] (スナップショット パブリケーション、SQL Server 2005 以降) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
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
- sql13.rep.monitor.publicationinfo.warningsandagents.snapshot.f1
ms.assetid: 7aa2eb52-b6b7-4dd3-8483-8ef00d9f0435
caps.latest.revision: 26
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26bfecdfdf47b3626128392223977af22a4f01b3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="publication-information-warnings-snapshot-publication-sql-server-2005-and-later"></a>パブリケーション情報、[警告] \(スナップショット パブリケーション、SQL Server 2005 以降)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **以降を実行しているディストリビューターでは、** [警告] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] タブを使用できます。 **[警告]** タブでは、選択されているパブリケーションに対して次の操作を実行できます。  
  
-   警告を有効にする。  
  
-   警告に関連するしきい値を指定する。  
  
-   警告に関連する通知を定義する。  
  
## <a name="warnings-thresholds-and-alerts"></a>警告、しきい値、および通知  
 既定では、レプリケーション モニターは、初期化されていないサブスクリプションに対して警告を表示します。サブスクリプション情報を含むページの **[状態]** 列に、警告として **[初期化されていないサブスクリプション]** という状態が表示されます。 スナップショット パブリケーションの場合は、 **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します]** オプションを設定することで、サブスクリプションの有効期限が差し迫っている場合に警告を生成するように指定することもできます。 指定したしきい値に到達するか、しきい値を超過すると、(より優先度が高い問題を表示する必要がない限り) **[まもなく期限切れ/期限切れ]** というサブスクリプション状態が表示されます。  
  
 しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。 通知を定義するには、 **[警告の構成]** をクリックし、 **[レプリケーションの警告の構成]** ダイアログ ボックスに情報を入力します。  
  
## <a name="options"></a>および  
 **有効**  
 警告を有効にする場合に選択します。その場合は、しきい値を指定します。  
  
 **警告**  
 しきい値に関連付けられている警告の説明です。  
  
 **しきい値**  
 しきい値の値を指定します。  
  
 **[警告の構成]**  
 **[警告]** グリッドの行を選択し、 **[警告の構成]** をクリックすると、 **[レプリケーションの警告の構成]** ダイアログ ボックスが表示されます。 このダイアログ ボックスでは、選択したしきい値および警告に関連付けた通知を定義できます。  
  
 **[変更の破棄]**  
 クリックすると、警告およびしきい値に対する変更が破棄されます。  
  
> [!NOTE]  
>  **[変更の破棄]** をクリックしても、 **[レプリケーションの警告の構成]** ダイアログ ボックスに定義されている通知は影響を受けません。  
  
 **[変更の保存]**  
 クリックすると、警告およびしきい値に対する変更が保存されます。  
  
## <a name="see-also"></a>参照  
 [レプリケーション モニターの開始](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [パブリケーションの情報の表示とタスクの実行 &#40;レプリケーション モニター&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [レプリケーションの監視](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
