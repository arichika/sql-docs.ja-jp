---
title: SQL Server:Workload Group Stats オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Workload Group Stats object
- 'SQLServer: Workload Group Stats'
ms.assetid: ca20e4f6-50ec-4456-900d-87d280fde2b3
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a43ca9896a3215d41bac32e01c4d3793d7fee8d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-workload-group-stats-object"></a>SQLServer:Workload Group Stats オブジェクト
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQLServer:Workload Group Stats オブジェクトには、リソース ガバナーのワークロード グループ統計に関する情報を報告するパフォーマンス カウンターが含まれています。  
  
 アクティブな各ワークロード グループでは、リソース ガバナー ワークロード グループ名と同じインスタンス名を持つ SQLServer:Workload Group Stats パフォーマンス オブジェクトのインスタンスが作成されます。 次の表では、このインスタンスでサポートされるカウンターについて説明します。  
  
|カウンター名|Description|  
|------------------|-----------------|  
|**Active parallel threads**|並列スレッド使用の現在の数。|  
|**Active requests**|このワークロード グループの現在実行中の要求数。 グループ ID でフィルター選択した sys.dm_exec_requests の行数と同じ数になります。|  
|**Blocked requests**|ワークロード グループのブロックされた要求の現在の数。 この数値を使用して負荷の特性を判別できます。|  
|**CPU delayed %**|パフォーマンス オブジェクトの指定されたインスタンス内のすべての要求を待機するシステム CPU (アクティブ時間の合計に対する割合)| 
|**CPU delayed % base**|内部使用のみです。| 
|**CPU effective %**|パフォーマンス オブジェクトの指定されたインスタンス内のすべての要求に対するシステム CPU の使用率 (アクティブ時間の合計に対する割合)| 
|**CPU effective % base**|内部使用のみです。| 
|**CPU usage %**|このワークロード グループのすべての要求による CPU 帯域幅の使用率。コンピューターを基準に測定され、システムのすべての CPU を基準に正規化されます。 この値は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスで使用できる CPU の量によって変化します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロセスに割り当てられた内容を基準にして正規化されるのではありません。| 
|**CPU usage % base**|内部使用のみです。| 
|**CPU violated %**|CPU 予約と有効なスケジュール割合の差。|  
|**Max request CPU time (ms)**|ワークロード グループの現在実行中の要求で使用される最大 CPU 時間 (ミリ秒単位)。|  
|**Max request memory grant (KB)**|1 つのクエリに対するメモリ許可の最大値 (KB 単位)。|  
|**Query optimizations/sec**|1 秒間にこのワークロード グループで行われたクエリの最適化の数。 この数値を使用して負荷の特性を判別できます。|  
|**Queued requests**|現在キューに置かれている処理待ちの要求の数。 この数は、GROUP_MAX_REQUESTS の上限に達してからスロットルが行われると、0 以外の値になることがあります。|  
|**Reduced memory grants/sec**|最適な量に満たないメモリ許可を取得している 1 秒間のクエリ数。|  
|**Requests completed/sec**|このワークロード グループの完了した要求の数。 この数は累積数です。|  
|**Suboptimal plans/sec**|1 秒間にこのワークロード グループで生成された最適ではないプランの数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQLServer:Resource Pool Stats オブジェクト](../../relational-databases/performance-monitor/sql-server-resource-pool-stats-object.md)   
 [リソース ガバナー](../../relational-databases/resource-governor/resource-governor.md)  
  
  
