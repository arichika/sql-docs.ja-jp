---
title: sys.service_queues (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.service_queues
- service_queues
- service_queues_TSQL
- sys.service_queues_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_queues catalog view
ms.assetid: 9fd9fa76-6128-410c-896f-741e6050143a
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bd452ced7da739beeb01b9295c8843473be202f5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysservicequeues-transact-sql"></a>sys.service_queues (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 行で、サービス キューとなっているデータベース内の各オブジェクトのデータを含む**sys.objects.type** SQ を = です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||このビューが継承する列の一覧は、次を参照してください。 [sys.objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)です。|  
|**max_readers**|**smallint**|キューで許可される同時読み取りの最大数です。|  
|**activation_procedure**|**nvarchar(776)**|3 つの要素で構成されるアクティブ化プロシージャの名前です。|  
|**execute_as_principal_id**|**int**|EXECUTE AS データベース プリンシパルの ID です。<br /><br /> 既定値または EXECUTE AS CALLER の場合は、NULL になります。<br /><br /> 場合は、指定したプリンシパルの ID AS SELF EXECUTE AS の実行\<プリンシパル >。<br /><br /> -2 = EXECUTE AS OWNER。|  
|**is_activation_enabled**|**bit**|1 = アクティブ化は有効です。|  
|**is_receive_enabled**|**bit**|1 = 受信は有効です。|  
|**is_enqueue_enabled**|**bit**|1 = エンキューは有効です。|  
|**is_retention_enabled**|**bit**|1 = ダイアログが終了するまでメッセージは保持されます。|  
|**is_poison_message_handling_enabled**|**bit**|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<br /><br /> 1 = 有害なメッセージの処理が有効です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
