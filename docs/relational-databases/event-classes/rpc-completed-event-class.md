---
title: "RPC:Completed イベント クラス | Microsoft Docs"
ms.custom: ""
ms.date: "12/04/2015"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "RPC:Completed イベント クラス"
ms.assetid: 0d526201-94c9-4e4c-afb1-4213df1815ba
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# RPC:Completed イベント クラス
  RPC:Completed イベント クラスは、リモート プロシージャ コールが完了したことを示します。  
  
## RPC:Completed イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|BinaryData|**image**|トレースでキャプチャされたイベント クラスに依存するバイナリ値。|2|はい|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|可|  
|CPU|**int**|イベントによって使用された CPU 時間。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]からは、マイクロ秒単位。 それより前のバージョンではミリ秒単位。|18|可|  
|DatabaseID|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|DatabaseName|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|可|  
|Duration|**bigint**|イベントによって使用された時間。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]からは、マイクロ秒単位。 それより前のバージョンではミリ秒単位。|13|はい|  
|EndTime|**datetime**|リモート プロシージャ コールの終了時刻。|15|可|  
|[エラー]|**int**|特定のイベントのエラー番号。<br /><br /> 0 = OK<br /><br /> 1 = エラー<br /><br /> 2 = 中止<br /><br /> 3 = スキップ|31|はい|  
|EventClass|**int**|イベントの種類 = 10。|27|いいえ|  
|EventSequence|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|可|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|LoginName|**nvarchar**|ユーザーのログイン名 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログイン資格情報)。|11|可|  
|LoginSid|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|可|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|NTUserName|**nvarchar**|Windows のユーザー名。|6|可|  
|ObjectName|**nvarchar**|参照されているオブジェクトの名前。|34|はい|  
|Reads|**bigint**|リモート プロシージャ コールによって実行されたページ読み取りの回数。|16|はい|  
|RequestID|**int**|ステートメントが含まれている要求の ID。|49|はい|  
|RowCounts|**bigint**|RPC バッチに含まれる行数。|48|はい|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26||  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|SPID|**int**|イベントが発生したセッションの ID。|12|はい|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|TextData|**ntext**|リモート プロシージャ コールのテキスト。|1|可|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
|Writes|**bigint**|リモート プロシージャ コールによって実行されたページ書き込みの回数。|17|はい|  
|XactSequence|**bigint**|現在のトランザクションを説明するトークン。|50|はい|  
  
## 参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  