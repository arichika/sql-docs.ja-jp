---
title: sys.xml_indexes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.xml_indexes_TSQL
- xml_indexes_TSQL
- sys.xml_indexes
- xml_indexes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_indexes catalog view
ms.assetid: 3408de72-b067-4fda-b5d5-8e856dfd9db3
caps.latest.revision: 34
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bbc15a06d6179165bd2f6f1d3c19eb24d42dfcc8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysxmlindexes-transact-sql"></a>sys.xml_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML インデックスごとに 1 行のデータを返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**\<継承された列 >**||列を継承[sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)です。|  
|**using_xml_index_id**|**int**|NULL = プライマリ XML インデックス<br /><br /> Nonnull = セカンダリ XML インデックス<br /><br /> Nonnull は、プライマリ XML インデックスへの自己結合参照です。|  
|**secondary_type**|**char(1)**|セカンダリ インデックスの種類の説明。<br /><br /> P = PATH セカンダリ XML インデックス<br /><br /> V = VALUE セカンダリ XML インデックス<br /><br /> R = PROPERTY セカンダリ XML インデックス<br /><br /> NULL = プライマリ XML インデックス|  
|**secondary_type_desc**|**nvarchar(60)**|セカンダリ インデックスの種類の説明。<br /><br /> PATH = PATH セカンダリ XML インデックス<br /><br /> VALUE = VALUE セカンダリ XML インデックス<br /><br /> PROPERTY = PROPERTY セカンダリ XML インデックス<br /><br /> NULL = プライマリ XML インデックス|  
|**xml_index_type**|**tinyint**|インデックスの種類:<br /><br /> 0 = プライマリ XML インデックス<br /><br /> 1 = セカンダリ XML インデックス<br /><br /> 2 = 選択的な XML インデックス<br /><br /> 3 = 選択的セカンダリ XML インデックス|  
|**xml_index_type_description**|**nvarchar(60)**|インデックスの種類の説明。<br /><br /> PRIMARY_XML<br /><br /> セカンダリ XML インデックス<br /><br /> 選択的な XML インデックス<br /><br /> 選択的セカンダリ XML インデックス|  
|**path_id**|**int**|選択的セカンダリ XML インデックスを除くすべての XML インデックスの場合は NULL です。<br /><br /> それ以外の場合は、選択的セカンダリ XML インデックスを構築する上位変換されたパスの ID です。 この値は、sys.selective_xml_index_paths システム ビューからの path_id と同じ値です。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [オブジェクトのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
