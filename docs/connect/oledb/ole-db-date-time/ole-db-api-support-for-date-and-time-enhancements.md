---
title: 日付と時刻の機能強化の OLE DB API によるサポート |Microsoft ドキュメント
description: 日付と時刻の機能強化の OLE DB API サポート
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: b3ccbf0a43cd64acb69c084ce75cb3673f38a8f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>日付と時刻の機能強化の OLE DB API によるサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  機能強化された日付や時刻をサポートする OLE DB API を次に示します。  
  
|関数|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|区別するアプリケーションを有効にする DBBINDING 構造体にフラグが追加**datetime**、 **datetime2**、および**smalldatetime**値。 詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IBCPSession::BCPColFmt|詳細については、次を参照してください。[強化された日付と時刻型の変更の一括コピー &#40;OLE DB&#41;](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)です。|  
|ICommandWithParameters::GetParameterInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|ICommandWithParameters::SetParameterinfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IColumnsRowset::GetColumnsRowset|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IColumnsInfo::GetColumnInfo|詳細については、次を参照してください。[パラメーターと行セットのメタデータ](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)です。|  
|IDBSchemaRowset::GetRowset|影響を受けるスキーマ行セットの詳細については、「[日付と時刻、およびスキーマ行セット](../../oledb/ole-db-date-time/metadata-date-and-time-and-schema-rowsets.md)です。|  
|IRowsetFastLoad|このインターフェイスは新しい日付と時刻の型をサポートしますが、インターフェイスに変更はありません。|  
|ITableDefinition::CreateTable|詳細については、次を参照してください。 [OLE DB の日付と時刻の強化に対するデータ型のサポート](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)です。|  
  
## <a name="see-also"></a>参照  
 [日付と時刻の強化 (&) #40";"OLE DB"&"#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
