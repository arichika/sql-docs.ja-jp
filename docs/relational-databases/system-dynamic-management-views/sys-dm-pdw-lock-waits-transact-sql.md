---
title: sys.dm_pdw_lock_waits (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 8ef966f8-d14e-40d3-9626-3508ada9b8fb
caps.latest.revision: 8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 30ef8fd780fbac0eb2d0ae231c982a0fb781ebe7
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmpdwlockwaits-transact-sql"></a>sys.dm_pdw_lock_waits (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  ロックを待機している要求についての情報を保持します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|wait_id|**bigint**|待機リスト内の要求の位置。|0 から始まる序数です。 これは、待機のすべてのエントリでない一意です。|  
|session_id|**nvarchar(32)**|待機状態が発生したセッションの ID。|Session_id を参照してください[sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)です。|  
|型|**nvarchar (255)**|このエントリが表す待機の種類。|有効値は次のとおりです。<br /><br /> Shared<br /><br /> SharedUpdate<br /><br /> ExclusiveUpdate<br /><br /> [Exclusive]|  
|object_type|**nvarchar (255)**|待機によって影響を受けるオブジェクトの型。|有効値は次のとおりです。<br /><br /> OBJECT<br /><br /> DATABASE<br /><br /> SYSTEM<br /><br /> SCHEMA<br /><br /> APPLICATION|  
|object_name|**nvarchar(386)**|名前または待機の影響を受けたを指定したオブジェクトの GUID。|3 部構成の名前では、テーブルとビューが表示されます。<br /><br /> 4 部構成の名前は、インデックスと統計情報が表示されます。<br /><br /> 名前、プリンシパル、およびデータベースは、文字列名です。|  
|request_id|**nvarchar(32)**|待機状態が発生した要求の ID。|要求の ID。<br /><br /> これは、読み込み要求の GUID です。|  
|request_time|**datetime**|ロックまたはリソースが要求される時刻。||  
|acquire_time|**datetime**|これで、ロックまたはリソースが取得された時刻です。||  
|state|**nvarchar (50)**|待機状態の状態です。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
|priority|**int**|待機中の項目の優先度。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
## <a name="see-also"></a>参照  
 [SQL データ ウェアハウスと並列データ ウェアハウスの動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
