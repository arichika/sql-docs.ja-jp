---
title: "Auto Stats イベント クラス | Microsoft Docs"
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
  - "Auto Stats イベント クラス"
ms.assetid: cd613fce-01e1-4d8f-86cc-7ffbf0759f9e
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# Auto Stats イベント クラス
  **Auto Stats** イベント クラスは、インデックス統計と列統計が自動更新されたことを示します。  
  
## Auto Stats イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|**ClientProcessID**|**int**|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターが割り当てた ID。 クライアントによりクライアント プロセス ID が指定されると、このデータ列に値が格納されます。|9|はい|  
|**DatabaseID**|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|可|  
|**DatabaseName**|**nvarchar**|ユーザーのステートメントが実行されているデータベースの名前。|35|可|  
|**Duration**|**bigint**|イベントにかかった時間 (マイクロ秒)。|13|はい|  
|**EndTime**|**datetime**|イベントの終了時刻。|15|可|  
|**[エラー]**|**int**|特定のイベントのエラー番号。 多くの場合、**sys.messages** カタログ ビューに保存されているエラー番号です。|31|はい|  
|**EventClass**|**int**|イベントの種類 = 58。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|不可|  
|**EventSubClass**|**int**|イベント サブクラスの種類。<br /><br /> 1: 統計の同期的な作成/更新。**TextData** 列に、どの統計が作成または更新されたのか、あるいはされていないのかが示されます。<br /><br /> 2: 統計の非同期更新。ジョブがキューに登録されました。<br /><br /> 3: 統計の非同期更新。ジョブが開始しました。<br /><br /> 4: 統計の非同期更新。ジョブが完了しました。|21|可|  
|**GroupID**|**int**|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|**HostName**|**nvarchar**|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|**IndexID**|**int**|イベントの影響を受けるオブジェクトに付けられたインデックスまたは統計エントリの ID。 オブジェクトのインデックス ID を特定するには、**sys.indexes** カタログ ビューの **index_id** 列を使用します。|24|可|  
|**IntegerData**|**int**|正常に更新された統計コレクションの数。|25|はい|  
|**IntegerData2**|**int**|ジョブ シーケンス番号。|55|はい|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|**LoginName**|**nvarchar**|ユーザーのログイン名 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\username という形式の Windows ログイン資格情報)。|11|可|  
|**LoginSid**|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、**sys.server_principals** カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|可|  
|**NTDomainName**|**nvarchar**|ユーザーが所属する Windows ドメイン。|7|はい|  
|**NTUserName**|**nvarchar**|Windows のユーザー名。|6|可|  
|**ObjectID**|**int**|システムによって割り当てられたオブジェクト ID。|22|はい|  
|**RequestID**|**int**|ステートメントが含まれている要求の ID。|49|可|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|不可|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|可|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|可|  
|**成功**|**int**|0 = エラー。<br /><br /> 1 = 成功。<br /><br /> 2 = サーバーの絞込みによりスキップ (MSDE)。|23|可|  
|**TextData**|**ntext**|この列の内容は、統計が同期的に更新されたのか、または非同期に更新されたのかによって異なります。同期更新の場合 **EventSubClass** は 1、非同期更新の場合 **EventSubClass** は 2、3、または 4 になります。<br /><br /> 1: 更新または作成された統計をリストで示します。<br /><br /> 2、3、または 4: NULL。**IndexID** 列には、更新された統計のインデックスまたは統計の ID が格納されます。|1|可|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
|**型**|**int**|ジョブの種類。|57|はい|  
  
## 参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  