---
title: sys.dm_os_hosts (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_hosts_TSQL
- dm_os_hosts
- dm_os_hosts_TSQL
- sys.dm_os_hosts
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_hosts dynamic management view
ms.assetid: a313ff3b-1fe9-421e-b94b-cea19c43b0e5
caps.latest.revision: 35
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 85a739c740cb16b89d728085cbc43c386cf03654
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmoshosts-transact-sql"></a>sys.dm_os_hosts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のインスタンスに登録されているすべてのホストを返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 このビューでは、ホストで使用されているリソースも返されます。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_hosts**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**host_address**|**varbinary(8)**|ホスト オブジェクトの内部メモリ アドレス。|  
|**type**|**nvarchar(60)**|ホストされるコンポーネントの種類。 例を次に示します。<br /><br /> SOSHOST_CLIENTID_SERVERSNI = SQL Server ネイティブ インターフェイス<br /><br /> SOSHOST_CLIENTID_SQLOLEDB = SQL Server Native Client OLE DB プロバイダー<br /><br /> SOSHOST_CLIENTID_MSDART = Microsoft Data Access Run Time|  
|**name**|**nvarchar(32)**|ホストの名前。|  
|**enqueued_tasks_count**|**int**|ホストによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のキューに挿入されたタスクの合計数。|  
|**active_tasks_count**|**int**|ホストによってキューに挿入されたタスクのうち、現在実行中のタスクの数。|  
|**completed_ios_count**|**int**|ホスト経由で発行され、完了した I/O の合計数。|  
|**completed_ios_in_bytes**|**bigint**|ホスト経由で完了した I/O の合計バイト数。|  
|**active_ios_count**|**int**|現在完了を待機しているホストに関連する I/O 要求の合計数。|  
|**default_memory_clerk_address**|**varbinary(8)**|ホストに関連付けられているメモリ クラーク オブジェクトのメモリ アドレス。 詳細については、次を参照してください。 [sys.dm_os_memory_clerks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)です。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>権限

[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]が必要です、`VIEW DATABASE STATE`データベースの権限です。   

## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実行可能なコンポーネント以外の OLE DB プロバイダーなどのコンポーネントが、メモリを割り当てたりノンプリエンプティブなスケジュールに参加することが許可されます。 これらのコンポーネントがによってホストされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、され、これらのコンポーネントが割り当てられているすべてのリソースが追跡されます。 ホスティングによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の外部コンポーネントで使用されるリソースをより正確に把握できます。  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
|From|変換先|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_os_hosts. default_memory_clerk_address|sys.dm_os_memory_clerks. memory_clerk_address|一対一|  
|sys.dm_os_hosts. host_address|sys.dm_os_memory_clerks. host_address|一対一|  
  
## <a name="examples"></a>使用例  
 次の例では、ホストされるコンポーネントによって使用されているメモリの総量を調べます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|  
  
```  
SELECT h.type, SUM(mc.pages_kb) AS commited_memory  
FROM sys.dm_os_memory_clerks AS mc   
INNER JOIN sys.dm_os_hosts AS h   
    ON mc.memory_clerk_address = h.default_memory_clerk_address  
GROUP BY h.type;  
```  
  
## <a name="see-also"></a>参照  

 [sys.dm_os_memory_clerks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)   
 [SQL Server オペレーティング システム関連の動的管理ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


