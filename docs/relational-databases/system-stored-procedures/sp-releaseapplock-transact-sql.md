---
title: sp_releaseapplock (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_releaseapplock_TSQL
- sp_releaseapplock
dev_langs:
- TSQL
helpviewer_keywords:
- sp_releaseapplock
ms.assetid: 51b03c2f-0d54-40f5-9172-e747942d4a46
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 6db9c114f4f3faade3334e7bf682eba197a2dbb7
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spreleaseapplock-transact-sql"></a>sp_releaseapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  アプリケーション リソースのロックを解放します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_releaseapplock [ @Resource = ] 'resource_name'   
     [ , [ @LockOwner = ] 'lock_owner' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 [ @Resource=] '*resource_name*'  
 クライアント アプリケーションによって指定されたロック リソース名を指定します。 アプリケーション側で、リソースが一意になるように管理しなければなりません。 指定した名前は内部的にハッシュされ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ロック マネージャーに格納できる値に変換されます。 *resource_name*は**nvarchar (255)** 既定値はありません。 *resource_name*はバイナリ比較、つまり現在のデータベースの照合順序の設定に関係なく大文字小文字を区別します。  
  
 [ @LockOwner=] '*lock_owner*'  
 ロックの所有者を指定します。これはロックが要求されたときの *lock_owner* 値です。 *lock_owner* は **nvarchar (32)** です。 この値は **Transaction** (既定値) または **Session** のいずれかです。 ときに、 *lock_owner*値は**トランザクション**により、既定または明示的に指定すると、sp_getapplock 必要がありますから実行するトランザクション内で。  
  
 [ @DbPrincipal=] '*database_principal*'  
 データベース内のオブジェクトに対する権限を持つユーザー、ロール、またはアプリケーション ロールを指定します。 関数を呼び出すには、*database_principal*、dbo、または固定データベース ロール db_owner のメンバーであることが必要です。 既定値は public です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 \>= 0 (成功) または < 0 (失敗)  
  
|値|結果|  
|-----------|------------|  
|0|ロックの解放が正しく行われました。|  
|-999|パラメーターの検証エラーまたはその他の呼び出しエラーです。|  
  
## <a name="remarks"></a>解説  
 アプリケーションで、同じロック リソースに対して sp_getapplock が複数回呼び出される場合は、同じ回数だけ sp_releaseapplock を呼び出して、ロックを解放する必要があります。  
  
 何かの理由でサーバーがシャットダウンすると、ロックは解放されます。  
  
## <a name="permissions"></a>権限  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、リソースの現在のトランザクションに関連付けられているロックを解放`Form1`で、`AdventureWorks2012`データベース。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'Form1',   
     @LockMode = 'Shared';  
EXEC sp_releaseapplock @DbPrincipal = 'dbo', @Resource = 'Form1';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [APPLOCK_MODE &#40;TRANSACT-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;TRANSACT-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_getapplock (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-getapplock-transact-sql.md)  
  
  
