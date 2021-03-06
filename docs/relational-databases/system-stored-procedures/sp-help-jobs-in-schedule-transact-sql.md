---
title: sp_help_jobs_in_schedule (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_jobs_in_schedule_TSQL
- sp_help_jobs_in_schedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobs_in_schedule
ms.assetid: 1168aa2c-136b-4ba3-b18e-9070d95a26fa
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78bffc1432bb650d5c1a7f37c0a712c34236dca1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpjobsinschedule-transact-sql"></a>sp_help_jobs_in_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  特定のスケジュールがアタッチされるジョブに関する情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_jobs_in_schedule   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>引数  
 [ **@schedule_id =** ] *schedule_id*  
 情報を一覧表示するスケジュールの識別子を指定します。 *schedule_id*は**int**、既定値はありません。 いずれか*schedule_id*または*schedule_name*指定することがあります。  
  
 [ **@schedule_name =** ] **'***schedule_name***'**  
 情報を一覧表示するスケジュールの名前を指定します。 *schedule_name*は**sysname**、既定値はありません。 いずれか*schedule_id*または*schedule_name*指定することがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の結果セットを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの一意な ID。|  
|**originating_server**|**nvarchar(30)**|ジョブを実行したサーバーの名前。|  
|**name**|**sysname**|ジョブの名前。|  
|**enabled**|**tinyint**|ジョブが実行可能かどうか。|  
|**説明**|**nvarchar(512)**|ジョブの説明。|  
|**start_step_id**|**int**|実行を開始するジョブ ステップの ID。|  
|**category**|**sysname**|ジョブ カテゴリ。|  
|**所有者**|**sysname**|ジョブ所有者。|  
|**notify_level_eventlog**|**int**|どのような場合に通知イベントを Microsoft Windows アプリケーション ログに記録するかを示すビットマスク。 これらの値のいずれかを指定できます。<br /><br /> **0** = なし<br /><br /> **1** = ジョブが成功した場合<br /><br /> **2** = ジョブが失敗したとき<br /><br /> **3** = (ジョブの結果に関係なく、ジョブが終了したとき|  
|**notify_level_email**|**int**|どのような場合に、ジョブの完了時に通知電子メールを送信するのかを示すビットマスク。 指定できる値は同じである**notify_level_eventlog**です。|  
|**notify_level_netsend**|**int**|どのような場合に、ジョブの完了時にネットワーク メッセージを送信するのかを示すビットマスク。 指定できる値は同じである**notify_level_eventlog**です。|  
|**notify_level_page**|**int**|どのような場合に、ジョブの完了時にページを送信するのかを示すビットマスク。 指定できる値は同じである**notify_level_eventlog**です。|  
|**notify_email_operator**|**sysname**|通知先のオペレーターの電子メール名。|  
|**notify_netsend_operator**|**sysname**|ネットワーク メッセージを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**notify_page_operator**|**sysname**|ページを送信するときに使用するコンピューターまたはユーザーの名前。|  
|**delete_level**|**int**|どのような場合に、ジョブの完了時にジョブを削除するのかを示すビットマスク。 指定できる値は同じである**notify_level_eventlog**です。|  
|**date_created**|**datetime**|ジョブを作成した日付。|  
|**date_modified**|**datetime**|ジョブを最後に変更した日付。|  
|**version_number**|**int**|ジョブのバージョン。ジョブを変更するたびに自動的に更新されます。|  
|**last_run_date**|**int**|ジョブの実行を最後に開始した日付。|  
|**last_run_time**|**int**|ジョブの実行を最後に開始した時刻。|  
|**last_run_outcome**|**int**|最後に実行したときのジョブの結果。<br /><br /> **0** = に失敗しました<br /><br /> **1** = に成功しました<br /><br /> **3** = キャンセル<br /><br /> **5** = unknown|  
|**next_run_date**|**int**|ジョブが次回実行予定日。|  
|**next_run_time**|**int**|ジョブの次回実行予定時刻。|  
|**next_run_schedule_id**|**int**|次回の実行スケジュールの識別番号。|  
|**current_execution_status**|**int**|現在の実行ステータス。|  
|**current_execution_step**|**sysname**|ジョブの現在の実行ステップ。|  
|**current_retry_attempt**|**int**|ジョブの実行中にステップを再試行した場合、現在の再試行を示します。|  
|**has_step**|**int**|ジョブのジョブ ステップ数。|  
|**has_schedule**|**int**|ジョブのジョブ スケジュール数。|  
|**has_target**|**int**|ジョブの対象サーバー数。|  
|**type**|**int**|ジョブの種類:<br /><br /> **1**ローカル ジョブを = です。<br /><br /> **2**マルチ サーバー ジョブを = です。<br /><br /> **0** = ジョブに対象サーバーがありません。|  
  
## <a name="remarks"></a>解説  
 このプロシージャでは、指定されたスケジュールにアタッチされたジョブに関する情報が一覧表示されます。  
  
## <a name="permissions"></a>権限  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 他のユーザーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb **データベースの次のいずれかの** エージェント固定データベース ロールが許可されている必要があります。  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 これらのロールの権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)」を参照してください。  
  
 メンバー **SQLAgentUserRole**自分が所有するジョブの状態だけを表示します。  
  
## <a name="examples"></a>使用例  
 次の例では、`NightlyJobs` スケジュールにアタッチされたジョブを一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobs_in_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
