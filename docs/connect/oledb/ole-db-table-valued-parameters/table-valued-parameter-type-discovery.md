---
title: テーブル値パラメーターの種類の探索 |Microsoft ドキュメント
description: テーブル値パラメーターの種類を使用した検出 OLE DB Driver for SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a5a15814b615f9775f9a70d2e24cc9dbb1db6365
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="table-valued-parameter-type-discovery"></a>テーブル値パラメーターの型の検出
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  コンシューマー — SQL Server の OLE DB Driver を使用して、クライアント アプリケーションは、-、コマンド テキストが OLE DB プロバイダーに指定された場合、各コマンド パラメーターの型を検出できます。 テーブル値パラメーターの型がわかったら、コンシューマーは、テーブル値パラメーターの各列のメタデータ情報を検出できます。  
  
 プロシージャのパラメーターの型情報はサポートされて icommandwithparameters::getparameterinfo によってほとんどのパラメーターの型。 以降で[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]、ユーザー定義型の導入に伴い、 **xml**データ型、GetParameterInfo メソッドがないこの目的のための十分なため、ユーザー定義型を提供することはできませんでした情報 (名前、スキーマ、およびカタログ) ICommandWithParameters を通じてします。 ISSCommandWithParameters の新しいインターフェイスは、拡張された型情報を提供する定義されました。  
  
 テーブル値パラメーターのも、ISSCommandWithParameters インターフェイスを使用する詳細情報を確認します。 クライアントは、コマンド オブジェクトを準備した後、ISSCommandWithParameters::GetParameterInfo を呼び出します。 テーブル値パラメーターの*wType* DBPARAMINFO 構造体のメンバーは、プロバイダーによって DBTYPE_TABLE に設定します。 *UlParamSize* DBPARAMINFO 構造体のフィールドの値を持つ ~ 0 です。  
  
 コンシューマーは ISSCommandWithParamters を使用して、追加のプロパティ (テーブル値パラメーターの型のカタログ名、テーブル値パラメーターの型のスキーマ名、テーブル値パラメーターの型名、列の順序、および既定の列) を要求し、:。GetParameterProperties です。  
  
 型名がわかったら、コンシューマーは、呼び出す必要がありますか、個々 の列情報を取得する IOpenRowset::OpenRowsetor 取得、DBSCHEMA_TABLE_TYPE_COLUMNS 行セット テーブル名とテーブル値パラメーターの型名を指定することによってです。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  