---
title: DROP MESSAGE TYPE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DROP_MESSAGE_TYPE_TSQL
- DROP MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- message types [Service Broker], removing
- deleting message types
- dropping message types
- DROP MESSAGE TYPE statement
- removing message types
ms.assetid: 805e8ad5-8a93-49f0-88e5-e6fca8814dd5
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 8745d96c94ac804982a5230b371059c19bdbfa1e
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="drop-message-type-transact-sql"></a>DROP MESSAGE TYPE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のメッセージ型を削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP MESSAGE TYPE message_type_name  
[ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *message_type_name*  
 削除するメッセージ型の名前を指定します。 サーバー名、データベース名、スキーマ名は指定できません。  
  
## <a name="permissions"></a>アクセス許可  
 メッセージ型を削除する権限は、既定ではメッセージ型の所有者、db_ddladmin 固定データベース ロールまたは db_owner 固定データベース ロールのメンバー、および sysadmin 固定サーバー ロールのメンバーに与えられています。  
  
## <a name="remarks"></a>Remarks  
 いずれかのコントラクトがメッセージ型を参照する場合は、そのメッセージ型を削除できません。  
  
## <a name="examples"></a>使用例  
 次の例では、データベースからメッセージ型 `//Adventure-Works.com/Expenses/SubmitExpense` を削除します。  
  
```  
DROP MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense] ;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
