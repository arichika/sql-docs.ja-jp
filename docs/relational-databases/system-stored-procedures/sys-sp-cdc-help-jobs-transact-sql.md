---
title: sys.sp_cdc_help_jobs (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_cdc_help_jobs
- sys.sp_cdc_help_jobs_TSQL
- sp_cdc_help_jobs_TSQL
- sys.sp_cdc_help_jobs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_help_jobs
ms.assetid: 9399b4bc-8293-408f-b3cb-f904e0657fb5
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1f193f632ca8095e42bb73eb76f8b283382a5069
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysspcdchelpjobs-transact-sql"></a>sys.sp_cdc_help_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースを対象に、変更データ キャプチャのすべてのクリーンアップ ジョブまたはキャプチャ ジョブについての情報をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_cdc_help_jobs  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|ジョブの ID。|  
|**job_type**|**nvarchar(20)**|ジョブの種類。|  
|**maxtrans**|**int**|各スキャン サイクルで処理する最大トランザクション数。<br /><br /> **maxtrans**はキャプチャ ジョブでのみ有効です。|  
|**maxscans**|**int**|ログからすべての行を抽出するために実行する最大スキャン サイクル数。<br /><br /> **maxscans**はキャプチャ ジョブでのみ有効です。|  
|**継続的です**|**bit**|キャプチャ ジョブを連続的に実行するか (1)、1 回だけ実行するか (0) を示すフラグ。 詳細については、次を参照してください。 [sys.sp_cdc_add_job &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)です。<br /><br /> **継続的な**はキャプチャ ジョブでのみ有効です。|  
|**pollinginterval**|**bigint**|ログ スキャン サイクル間の秒数。<br /><br /> **pollinginterval**はキャプチャ ジョブでのみ有効です。|  
|**保有期間**|**bigint**|変更行が変更テーブルに保持される分数。<br /><br /> **保有期間**はクリーンアップ ジョブでのみ有効です。|  
|**threshold**|**bigint**|クリーンアップ時に 1 つのステートメントを使用して削除できる最大削除エントリ数。|  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、 **db_owner**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例は、`AdventureWorks2012` データベースに定義されているキャプチャ ジョブおよびクリーンアップ ジョブについての情報を返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_help_jobs;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [dbo.cdc_jobs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys.sp_cdc_add_job & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
