---
title: "affinity64 mask サーバー構成オプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロセッサ関係 [SQL Server]"
  - "affinity64 mask オプション"
  - "プロセッサのバインド [SQL Server]"
ms.assetid: 75ed08c7-f85c-4e15-9ee1-e7bc545d3293
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# affinity64 mask サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  affinity64 mask を使用すると、affinity mask オプションと同様に、プロセッサが特定のスレッドにバインドされます。 affinity mask を使用して最初の 32 プロセッサをバインドし、affinity64 mask を使用してコンピューター上の残りのプロセッサをバインドします。 このオプションは 64 ビット版の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でのみ表示されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)] 代わりに [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md) を使用します。  
  
## 参照  
 [affinity mask サーバー構成オプション](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)  
  
  