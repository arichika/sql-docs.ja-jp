---
title: "SQL:FullTextQuery イベント クラス | Microsoft Docs"
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
  - "SQL:FullTextQuery イベント クラス"
ms.assetid: 654fb295-f0a5-4d66-93e0-5d43e4d7d535
caps.latest.revision: 31
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 31
---
# SQL:FullTextQuery イベント クラス
  SQL:FullTextQuery イベント クラスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によりフルテキスト クエリが実行されると発生します。 このイベント クラスは、フルテキスト カタログに関連する問題を監視するトレースに含めます。  
  
 SQL:FullTextQuery イベント クラスを含めると、オーバーヘッドが大きくなります。 このようなイベントが頻繁に発生すると、トレースによってパフォーマンスが大きく低下することがあります。 パフォーマンスの低下を最小限に抑えるには、短期間だけ特定の問題を監視するトレースに限定してこのイベント クラスを使用するようにします。  
  
## SQL:FullTextQuery イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|はい|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|DatabaseName|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|可|  
|Duration|**bigint**|フルテキスト クエリが完了するまでの時間。|13|いいえ|  
|EndTime|**datetime**|イベントが終了した時刻。|15|可|  
|[エラー]|**int**|エラー メッセージ番号。|31|はい|  
|EventClass|**int**|記録されるイベントの種類 = 123。|27|いいえ|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|IntegerData|**int**|返された行数。 クエリからエラーが返された場合、この値は NULL になります。 クエリから行が返されなかった場合、この値は 0 になります。|25|はい|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|LoginName|nvarchar|ユーザーのログイン名 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|可|  
|LoginSid|**image**|ログインしたユーザーのセキュリティ識別子 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|可|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|ObjectID|**int**|対象にシステムが割り当てた ID。|22|はい|  
|RequestID|**int**|フルテキスト クエリを開始した要求 ID。|49|可|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|不可|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|SPID|**int**|イベントが発生したセッションの ID。|12|はい|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|TextData|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に送信されたクエリのフルテキスト部分。|1|いいえ|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|可|  
|XactSequence|**bigint**|現在のトランザクションを説明するトークン。|50|はい|  
  
## 参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  