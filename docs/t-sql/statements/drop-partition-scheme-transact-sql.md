---
title: DROP PARTITION SCHEME (Transact-SQL) | Microsoft Docs
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
- DROP PARTITION SCHEME
- DROP_PARTITION_SCHEME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP PARTITION SCHEME statement
- deleting partition schemes
- dropping partition schemes
- removing partition schemes
- partition schemes [SQL Server], removing
ms.assetid: 6efbc87c-1c92-4e43-96a7-e0f30f1db185
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 2fe214a36e90a61e339a3113f952d0609b8c1f76
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="drop-partition-scheme-transact-sql"></a>DROP PARTITION SCHEME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースからパーティション構成を削除します。 パーティション構成を作成するには [CREATE PARTITION SCHEME](../../t-sql/statements/create-partition-scheme-transact-sql.md) を、変更するには [ALTER PARTITION SCHEME](../../t-sql/statements/alter-partition-scheme-transact-sql.md) を使用します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
DROP PARTITION SCHEME partition_scheme_name [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *partition_scheme_name*  
 削除するパーティション構成の名前です。  
  
## <a name="remarks"></a>Remarks  
 パーティション構成を削除できるのは、現在パーティション構成を使用しているテーブルやインデックスがない場合のみです。 パーティション構成を使用しているテーブルやインデックスがある場合は、削除パーティション構成にエラーが返されます。 DROP PARTITION SCHEME では、ファイル グループそのものは削除することはありません。  
  
## <a name="permissions"></a>アクセス許可  
 DROP PARTITION SCHEME を実行すると、下記の権限を使用することができます。  
  
-   ALTER ANY DATASPACE 権限。 この権限は、既定では **sysadmin** 固定サーバー ロール、 **db_owner** 固定データベース ロール、および **db_ddladmin** 固定データベース ロールのメンバーに与えられています。  
  
-   パーティション構成が作成されたデータベースに対する CONTROL または ALTER 権限。  
  
-   パーティション構成が作成されたデータベースのサーバーに対する CONTROL SERVER または ALTER ANY DATABASE 権限。  
  
## <a name="examples"></a>使用例  
 下記は、現在のデータベースから `myRangePS1` パーティション構成を削除する例です。  
  
```  
DROP PARTITION SCHEME myRangePS1;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40;Transact-SQL&#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [sys.partition_schemes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partition-schemes-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.destination_data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-destination-data-spaces-transact-sql.md)   
 [sys.partitions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
