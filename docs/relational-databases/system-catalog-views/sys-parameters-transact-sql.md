---
title: sys.parameters (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.parameters_TSQL
- sys.parameters
- parameters
- parameters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.parameters catalog view
- table-valued parameters,sys.parameters
ms.assetid: 24e2764b-c8e5-4322-97a4-7407d8b8a92b
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2a86fe34d867fcda8e416065e73e780f2cbee851
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysparameters-transact-sql"></a>sys.parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  パラメーターを受け入れるオブジェクトのパラメーターごとに 1 行のデータを保持します。 オブジェクトがスカラー関数の場合、戻り値を説明する単一行も含まれます。 その行がある、 **parameter_id** 0 の値。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|パラメーターが属しているオブジェクトの ID。|  
|**name**|**sysname**|パラメーターの名前です。 オブジェクト内で一意です。<br /><br /> オブジェクトがスカラー関数の場合、パラメーター名は、戻り値を表す行の空の文字列になります。|  
|**parameter_id**|**int**|パラメーターの ID です。 オブジェクト内で一意です。<br /><br /> 場合は、オブジェクトがスカラー関数、 **parameter_id**戻り値 0 を = です。|  
|**system_type_id**|**tinyint**|パラメーターのシステム型の ID です。|  
|**user_type_id**|**int**|ユーザーが定義されているパラメーターの型の ID。<br /><br /> 型の名前を返すに参加させる、 [sys.types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)カタログをこの列に表示します。|  
|**max_length**|**smallint**|パラメーターの最大長 (バイト単位)。<br /><br /> 値列のデータ型がの場合は、-1 を = **varchar (max)**、 **nvarchar (max)**、 **varbinary (max)**、または**xml**です。|  
|**有効桁数 (precision)**|**tinyint**|数値ベースの場合は、パラメーターの有効桁数です。それ以外の場合は、0 です。|  
|**scale**|**tinyint**|数値ベースの場合は、パラメーターの小数点以下桁数です。それ以外の場合は、0 です。|  
|**is_output**|**bit**|1 = パラメーターは OUTPUT または RETURN です。それ以外の場合は 0 です。|  
|**is_cursor_ref**|**bit**|1 = パラメーターはカーソル参照パラメーターです。|  
|**has_default_value**|**bit**|1 = パラメーターに既定値です。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このカタログ ビュー内の CLR オブジェクトの既定値のみが保持されます。したがって、[!INCLUDE[tsql](../../includes/tsql-md.md)] オブジェクトに対してこの列の値は 0 になります。 内のパラメーターの既定値を表示する、[!INCLUDE[tsql](../../includes/tsql-md.md)]オブジェクト、クエリ、**定義**の列、 [sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)カタログ ビュー、またはを使用して、 [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)システム関数です。|  
|**is_xml_document**|**bit**|1 = 内容が完全な XML ドキュメントです。<br /><br /> 0 = コンテンツは、ドキュメント フラグメント、または列のデータ型が**xml**です。|  
|**default_value**|**sql_variant**|場合**has_default_value** 1 の場合は、この列の値のパラメーターの既定値です。 それ以外の場合は NULL です。|  
|**xml_collection_id**|**int**|パラメーターのデータ型が場合は 0 以外**xml** XML が型指定されたとします。 この値は、パラメーターの検証 XML スキーマ名前空間を含むコレクションの ID です。<br /><br /> 0 = いいえの XML スキーマ コレクションです。|  
|**is_readonly**|**bit**|1 = パラメーターは READONLY です。それ以外の場合は 0 です。|  
|**is_nullable**|**bit**|1 = パラメーターで NULL が許可されます  (既定値です)。<br /><br /> 0 = ネイティブ コンパイル ストアド プロシージャをより効率的に実行するために、パラメーターで NULL が許可されません。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server のシステム カタログよく寄せられる質問のクエリを実行します。](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.all_parameters &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-parameters-transact-sql.md)   
 [sys.system_parameters &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-system-parameters-transact-sql.md)  
  
  
