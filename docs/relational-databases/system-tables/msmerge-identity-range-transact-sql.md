---
title: MSmerge_identity_range (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 026774d2eae738f8641c56f923bcabc981fded1e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range**テーブルがパブリケーションに対するサブスクリプションの id 列に割り当てられている数値範囲を追跡するために使用されるレプリケーションが自動的に管理するこれらの範囲の割り当て。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|指定したサブスクリプションの一意の ID 番号です。|  
|**artid**|**uniqueidentifier**|指定したアーティクルの一意な ID 番号です。|  
|**range_begin**|**numeric(38)**|現在の範囲の開始 ID 値です。|  
|**range_end**|**numeric(38)**|現在の範囲の終了 ID 値です。|  
|**next_range_begin**|**numeric(38)**|割り当てられる次の範囲の開始 ID 値です。|  
|**next_range_end**|**numeric(38)**|割り当てられる次の範囲の終了 ID 値です。|  
|**is_pub_range**|**bit**|値**1**をパブリケーションに id 範囲が割り当てられている場合。|  
|**max_used**|**numeric(38)**|割り当てることができる ID の最大値です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
