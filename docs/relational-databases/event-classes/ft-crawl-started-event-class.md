---
title: "FT:Crawl Started イベント クラス | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Crawl Started イベント クラス"
ms.assetid: 2535b856-97e8-4fb2-8ba0-5d5446355fa6
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# FT:Crawl Started イベント クラス
  **FT:Crawl Started** イベント クラスは、フルテキスト クロール (作成) が開始されたことを示します。 このイベント クラスを使用して、クロール要求がワーカー タスクによって実際に取得されたかどうかを確認します。  
  
## FT:Crawl Started イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|フルテキスト クロールが開始されたデータベースの ID です。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|**EventClass**|**int**|イベントの種類 = 155。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|**ObjectID**|**int**|システムによって割り当てられたオブジェクト ID。 フルテキスト クロールは、このオブジェクトのフルテキスト インデックスで開始されました。|22|可|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログインの両方が表示されます。|64|可|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|**TextData**|**ntext**|フルテキスト クロールの種類です。 値は、Full、Incremental、Manual、または Auto です。|1|可|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
  
## 参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  