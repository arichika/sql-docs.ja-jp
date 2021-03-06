---
title: sys.sp_xtp_control_query_exec_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_query_exec_stats_TSQL
- sys.sp_xtp_control_query_exec_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_query_exec_stats
ms.assetid: 4838125d-ad1e-479e-b7d2-42655e8f4f02
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 23301458684008945c057aa1d7f9f97380a9cb68
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysspxtpcontrolqueryexecstats-transact-sql"></a>sys.sp_xtp_control_query_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  インスタンスに関するすべてのネイティブ コンパイル ストアド プロシージャ、または特定のネイティブ コンパイル ストアド プロシージャのクエリごとの統計コレクションを有効にします。  
  
 統計コレクションを有効にすると、パフォーマンスが低下します。 1 つまたは少数のネイティブ コンパイル ストアド プロシージャのみをトラブルシューティングする必要がある場合は、それらのネイティブ コンパイル ストアド プロシージャに対してのみ統計コレクションを有効にすることができます。  
  
 すべてのネイティブ コンパイル ストアド プロシージャのプロシージャ レベルで統計コレクションを有効にするを参照してください。 [sys.sp_xtp_control_proc_exec_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
sp_xtp_control_query_exec_stats [ [ @new_collection_value = ] collection_value ],  
[ [ @database_id = ] database_id   
[ , [ @xtp_object_id = ] procedure_id ] ,   
[ @old_collection_value] ]  
```  
  
## <a name="arguments"></a>引数  
 @new_collection_value = *value*  
 プロシージャ レベルの統計コレクションが有効 (1) であるか、無効 (0) であるかを示します。  
  
 @new_collection_value 0 に設定されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を開始します。  
  
 @database_id = = *database_id*、 @xtp_object_id = *procedure_id*  
 ネイティブ コンパイル ストアド プロシージャのデータベース ID とオブジェクト ID。 インスタンスの統計コレクションが有効になっている場合 ([sys.sp_xtp_control_proc_exec_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-proc-exec-stats-transact-sql.md))、ネイティブ コンパイル ストアド プロシージャの統計情報を収集します。 インスタンスに対する統計コレクションを無効にしても、個々のネイティブ コンパイル ストアド プロシージャに関する統計コレクションは無効になりません。  
  
 使用して[sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)、 [sys.procedures &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)、 [DB_ID &#40;TRANSACT-SQL&#41;](../../t-sql/functions/db-id-transact-sql.md)、または[OBJECT_ID &#40;TRANSACT-SQL&#41; ](../../t-sql/functions/object-id-transact-sql.md)データベースとストアド プロシージャの Id を取得します。  
  
 @old_collection_value = *value*  
 現在の状態を返します。  
  
## <a name="return-code"></a>リターン コード  
 成功した場合は 0。 失敗した場合は 0 以外の値。  
  
## <a name="permissions"></a>権限  
 固定 sysadmin ロールのメンバーシップが必要です。  
  
## <a name="code-sample"></a>コード サンプル  
 次のコード サンプルでは、インスタンスに関するすべてのネイティブ コンパイル ストアド プロシージャの統計コレクションを有効にする方法と、特定のネイティブ コンパイル ストアド プロシージャの統計コレクションを有効にする方法を示しています。  
  
```sql   
DECLARE @c bit  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1;  
  
EXEC sp_xtp_control_query_exec_stats @old_collection_value=@c output;  
SELECT @c AS 'collection status';  
  
EXEC [sys].[sp_xtp_control_query_exec_stats] @new_collection_value = 1,   
@database_id = 5, @xtp_object_id = 341576255;  
  
EXEC sp_xtp_control_query_exec_stats @database_id = 5,   
@xtp_object_id = 341576255, @old_collection_value=@c output;  
  
SELECT @c AS 'collection status';  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
