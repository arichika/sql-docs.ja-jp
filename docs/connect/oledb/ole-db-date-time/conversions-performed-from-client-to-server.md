---
title: クライアントからサーバーへの変換を実行 |Microsoft ドキュメント
description: クライアントからサーバーへの変換を実行
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
helpviewer_keywords:
- conversions [OLE DB], client to server
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: a61001b562c982d4a6b5734f5840bf3b7e22b4ee
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="conversions-performed-from-client-to-server"></a>クライアントからサーバーへの変換
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  説明の間で実行される日付/時刻変換 SQL Server の OLE DB ドライバーで作成されたクライアント アプリケーションと[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)](またはそれ以降)。  
  
## <a name="conversions"></a>コンバージョン  
 この記事では、クライアントで行われる変換について説明します。 パラメーターに対して、サーバーで定義されているのとは異なる、秒の小数部の有効桁数をクライアントで指定した場合、サーバー側で変換すると処理に成功するのに、クライアント側で変換すると処理に失敗することがあります。 一方、クライアントで秒の小数部の切り捨てをエラーとして扱う具体的には、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のラウンドの時間が最も近い全体の 2 番目の値。  
  
 場合と同様に DBTYPE_DBTIMESTAMP バインドを変換 icommandwithparameters::setparameterinfo を呼び出さない場合**datetime2**です。  
  
|変換先 -><br /><br /> From|DBDATE (date)|DBTIME (time)|DBTIME2 (time)|DBTIMESTAMP (smalldatetime)|DBTIMESTAMP (datetime)|DBTIMESTAMP (datetime2)|DBTIMESTAMPOFFSET (datetimeoffset)|STR|WSTR|SQLVARIANT<br /><br /> (sql_variant)|  
|----------------------|---------------------|---------------------|----------------------|-----------------------------------|------------------------------|-------------------------------|------------------------------------------|---------|----------|-------------------------------------|  
|[DATE]|1、2|1、3、4|4、12|1、12|1、12|1、12|1、5、12|1、12|1、12|1、12<br /><br /> datetime2(0)|  
|DBDATE|1|-|-|1、6|1、6|1、6|1、5、6|1、10|1、10|1<br /><br /> date|  
|DBTIME|-|1|1|1、7|1、7|1、7|1、5、7|1、10|1、10|1<br /><br /> Time(0)|  
|DBTIME2|-|1、3|1|1、7、10、14|1、7、10、15|1、7、10|1、5、7、10|1、10、11|1、10、11|1<br /><br /> Time (7)|  
|DBTIMESTAMP|1、2|1、3、4|1, 4, 10|1、10、14|1、10、15|1、10|1, 5, 10|1、10,11|1、10、11|1、10<br /><br /> datetime2(7)|  
|DBTIMESTAMPOFFSET|1、2、8|1、3、4、8|1、4、8、10|1、8、10、14|1、8、10、15|1, 8, 10|1、10|1、10、11|1、10、11|1、10<br /><br /> datetimeoffset(7)|  
|FILETIME|1、2|1、3、4|1, 4, 13|1、13|1、13|1、13|1, 5, 13|1、13|1、10|1、13<br /><br /> datetime2(3)|  
|BYTES|-|-|-|-|-|-|-|なし|なし|なし|  
|VARIANT|1|1|1|1、10|1、10|1、10|1、10|なし|なし|1、10|  
|SSVARIANT|1、16|1、16|1、16|1、10、16|1、10、16|1、10、16|1、10、16|なし|なし|1、16|  
|BSTR|1、9|1、9|1、9、10|1、9、10|1、9、10|1、9、10|1、9、10|なし|なし|なし|  
|STR|1、9|1、9|1、9、10|1、9、10|1、9、10|1、9、10|1、9、10|なし|なし|なし|  
|WSTR|1、9|1、9|1、9、10|1、9、10|1、9、10|1、9、10|1、9、10|なし|なし|なし|  
  
## <a name="key-to-symbols"></a>記号の説明  
  
|記号|意味|  
|------------|-------------|  
|-|変換はサポートされていません。 Iaccessor::createaccessor が呼び出されたときに、バインドが検証されると、DBBINDSTATUS_UPSUPPORTEDCONVERSION がで返されます*rgStatus*です。 アクセサー検証が遅延する場合は、DBSTATUS_E_BADACCESSOR が設定されます。|  
|なし|該当なし。|  
|1|指定されたデータが有効でない場合、DBSTATUS_E_CANTCONVERTVALUE が設定されます。 入力データが検証されてから変換が適用されるので、コンポーネントは後続の変換で無視されることがあっても、変換を成功させるには有効である必要があります。|  
|2|時刻フィールドは無視されます。|  
|3|秒の小数部は 0 である必要があります。そうでなければ、DBSTATUS_E_DATAOVERFLOW が設定されます。|  
|4|日付部分は無視されます。|  
|5|タイム ゾーンには、クライアントのタイム ゾーン設定が設定されます。|  
|6|時刻は 0 に設定されます。|  
|7|日付は現在の日付に設定されます。|  
|8|時刻は UTC に変換されます。 この変換中にエラーが発生した場合、DBSTATUS_E_CANTCONVERTVALUE が設定されます。|  
|9|文字列は ISO リテラルとして解析され、対象の型に変換されます。 これが失敗すると、文字列は OLE 日付リテラル (時刻要素も含む) として解析され、OLE Date (DBTYPE_DATE) から対象の型に変換されます。<br /><br /> ターゲットの型が DBTIMESTAMP 場合、 **smalldatetime**、 **datetime**、または**datetime2**、文字列は、の日付、構文に準拠する必要があります時間、または**datetime2**リテラル、または OLE で認識される構文です。 文字列が日付リテラルの場合、すべての時刻部分が 0 に設定されます。 文字列が時刻リテラルの場合、日付は現在の日付に設定されます。<br /><br /> その他の対象の型の場合、文字列は対象の型のリテラルの構文に準拠している必要があります。|  
|10|データ損失を伴って秒の小数部が切り捨てられる場合、DBSTATUS_E_DATAOVERFLOW が設定されます。 文字列変換では、文字列が ISO 構文に準拠している場合のみオーバーフロー チェックが有効になります。 文字列が OLE 日付リテラルの場合、秒の小数部は丸められます。<br /><br /> 変換 DBTIMESTAMP (datetime) から smalldatetime OLE DB Driver for SQL Server が自動的に切り捨て DBSTATUS_E_DATAOVERFLOW エラーは、秒の値。|  
|11|第 2 桁の小数部 (小数点以下桁数) の数は、変換先列のサイズから次の表に従って決定されます。 列のサイズが、テーブル内の範囲より大きい、小数点以下桁数は 9 桁と見なされます。 この変換では、秒の小数点以下桁数が 9 桁まで許容されます。これは、OLE DB で許容される最大桁数です。<br /><br /> ただし、変換元の型が DBTIMESTAMP で、秒の小数部が 0 の場合、秒の小数部または小数点は生成されません。 この動作により、以前の OLE DB プロバイダーを使用して開発されたアプリケーションの下位互換性が保証されます。<br /><br /> 列サイズが 0 より小さい場合は、OLE DB ではサイズが無制限であることを意味します (DBTIMESTAMP の 3 桁ルールが適用されなければ 9 桁)。|  
|12|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]DBTYPE_DATE に対するが保持されます。 秒の小数部は 0 に切り捨てられます。|  
|13|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]バージョンの DBTYPE_FILETIME に対するが保持されます。 Windows FileTimeToSystemTime API を使用する場合、秒の小数部の有効桁数は 1 ミリ秒に制限されます。|  
|14|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]の**smalldatetime**が保持されます。 秒は 0 に設定されます。|  
|15|前のバージョンの変換セマンティクス[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]の**datetime**が保持されます。 秒は、1/300 秒単位に丸められます。|  
|16|SSVARIANT クライアントの構造体に埋め込まれた (特定の型の) 値の変換動作は、SSVARIANT クライアントの構造体に埋め込まれていない場合の同一の値および型の動作と同じです。|  
  
||||  
|-|-|-|  
|型|長さ (文字数)|Scale|  
|DBTIME2|8, 10..18|0,1..9|  
|DBTIMESTAMP|19, 21..29|0,1..9|  
|DBTIMESTAMPOFFSET|26, 28..36|0,1..9|  
  
## <a name="see-also"></a>参照  
 [バインドと変換&#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
  
  
