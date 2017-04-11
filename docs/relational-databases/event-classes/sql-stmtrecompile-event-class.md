---
title: "SQL:StmtRecompile イベント クラス | Microsoft Docs"
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
  - "SQL:StmtRecompile イベント クラス"
ms.assetid: 3a134751-3e93-4fe8-bf22-1e0561189293
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# SQL:StmtRecompile イベント クラス
  SQL:StmtRecompile イベント クラスは、ストアド プロシージャ、トリガー、アドホック バッチ、クエリなど、すべての種類のバッチに起因するステートメント レベルの再コンパイルが発生したことを示します。 クエリは、sp_executesql、動的 SQL、Prepare メソッド、Execute メソッド、または同様のインターフェイスを使用して送信できます。 SP:Recompile イベント クラスでなく、SQL:StmtRecompile イベント クラスを使用してください。  
  
## SQL:StmtRecompile イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**| [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|ClientProcessID|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりプロセス ID が指定されている場合は、このデータ列に値が格納されます。|9|はい|  
|DatabaseID|**int**|ストアド プロシージャが実行されているデータベースの ID。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|DatabaseName|**nvarchar**|ストアド プロシージャが実行されているデータベースの名前。|35|可|  
|EventSequence|**int**|要求内にあるイベントのシーケンス。|51|不可|  
|EventSubClass|**int**|再コンパイルの原因を示します。<br /><br /> 1 = スキーマの変更<br /><br /> 2 = 統計の変更<br /><br /> 3 = コンパイルの遅延<br /><br /> 4 = Set オプションの変更<br /><br /> 5 = Temp テーブルの変更<br /><br /> 6 = リモート行セットの変更<br /><br /> 7 = 参照権限の変更<br /><br /> 8 = クエリ通知環境の変更<br /><br /> 9 = パーティション ビューの変更<br /><br /> 10 = カーソル オプションの変更<br /><br /> 11 = オプション (再コンパイル) の要求|21|可|  
|GroupID|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|**nvarchar**|このステートメントを送信したクライアントが実行されているコンピューターの名前。 このデータ列にはクライアントからホスト名が提供されている場合に値が格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|可|  
|IntegerData2|**int**|再コンパイルの原因となったストアド プロシージャまたはバッチ内のステートメントの終了オフセット。 ステートメントがそのバッチの最後のステートメントである場合、終了オフセットは -1 です。|55|はい|  
|IsSystem|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。<br /><br /> 1 = システム<br /><br /> 0 = ユーザー|60|可|  
|LineNumber|**int**|バッチ内のこのステートメントのシーケンス番号 (該当する場合)。|5|はい|  
|LoginName|**nvarchar**|このバッチを送信したログインの名前。|11|可|  
|LoginSid|**image**|現在ログインしているユーザーのセキュリティ識別子 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|NestLevel|**int**|ストアド プロシージャ コールの入れ子レベル。 たとえば、my_proc_a ストアド プロシージャは my_proc_b を呼び出します。 この場合、my_proc_a の NestLevel は 1 で、my_proc_b の NestLevel は 2 です。|29|可|  
|NTDomainName|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|NTUserName|**nvarchar**|接続しているユーザーの Windows ユーザー名。|6|可|  
|ObjectID|**int**|再コンパイルの原因となったステートメントを含むオブジェクトのシステムによって割り当てられた識別子。 このオブジェクトは、ストアド プロシージャ、トリガー、またはユーザー定義関数です。 アドホック バッチまたは準備された SQL の場合、ObjectID および ObjectName は NULL 値を返します。|22|はい|  
|ObjectName|**nvarchar**|ObjectID によって識別されるオブジェクトの名前。|34|可|  
|ObjectType|**int**|イベントに関係するオブジェクトの種類を表す値。 詳細については、「[ObjectType トレース イベント列](../../relational-databases/event-classes/objecttype-trace-event-column.md)」を参照してください。|28|はい|  
|Offset|**int**|再コンパイルの原因となったストアド プロシージャまたはバッチ内のステートメントの開始オフセット。|61|はい|  
|RequestID|**int**|ステートメントが含まれている要求の ID。|49|可|  
|ServerName|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前。|26|不可|  
|SessionLoginName|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|SPID|**int**|接続のサーバー プロセス ID。|12|はい|  
|SqlHandle|**varbinary**|64 ビット ハッシュ。アドホック クエリやデータベースのテキスト、および SQL オブジェクトのオブジェクト ID に基づいています。 この値を sys.dm_exec_sql_text に渡して、関連付けられている SQL テキストを取得できます。|63|いいえ|  
|StartTime|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|TextData|**ntext**|再コンパイルされた Transact-SQL ステートメントのテキスト。|1|可|  
|TransactionID|**bigint**|システムによって割り当てられたトランザクション ID。|4|可|  
|XactSequence|**bigint**|現在のトランザクションを説明するトークン。|50|はい|  
  
## 参照  
 [SP:Recompile イベント クラス](../../relational-databases/event-classes/sp-recompile-event-class.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  