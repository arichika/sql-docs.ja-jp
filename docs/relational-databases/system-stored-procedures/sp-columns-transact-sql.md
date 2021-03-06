---
title: sp_columns (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/17/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_columns_TSQL
- sp_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns
ms.assetid: 2dec79cf-2baf-4c0f-8cbb-afb1a8654e1e
caps.latest.revision: 45
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 784811775a3364544e67d6591de203b091ab5402
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spcolumns-transact-sql"></a>sp_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の環境でクエリできる、指定されたオブジェクトの列情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_columns [ @table_name = ] object  
     [ , [ @table_owner = ] owner ]   
     [ , [ @table_qualifier = ] qualifier ]   
     [ , [ @column_name = ] column ]   
     [ , [ @ODBCVer = ] ODBCVer ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@table_name=**] *object*  
 カタログ情報を返すために使用するオブジェクトの名前を指定します。 *オブジェクト*テーブル、ビュー、またはテーブル値関数などの列を持つ他のオブジェクトを指定できます。 *オブジェクト*は**nvarchar (384)**、既定値はありません。 ワイルドカードによるパターン照合がサポートされています。  
  
 [ **@table_owner****=**] *owner*  
 カタログ情報を返すために使用するオブジェクトの所有者を指定します。 *所有者*は**nvarchar (384)**、既定値は NULL です。 ワイルドカードによるパターン照合がサポートされています。 場合*所有者*が指定されていない、基になる DBMS の既定のオブジェクトの可視性規則が適用されます。  
  
 指定した名前のオブジェクトを現在のユーザーが所有している場合は、そのオブジェクトの列が返されます。 場合*所有者*が指定されていない、現在のユーザーが、指定したオブジェクトを所有していないと*オブジェクト*、 **sp_columns**は、指定したオブジェクトを検索*オブジェクト*データベース所有者が所有します。 存在する場合は、そのオブジェクトの列が返されます。  
  
 [ **@table_qualifier****=**] *qualifier*  
 オブジェクト識別子の名前です。 *修飾子*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 つの部分は、オブジェクトの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 製品によっては、オブジェクトのデータベース環境のサーバー名を表す場合があります。  
  
 [ **@column_name=**] *column*  
 1 つの列には、1 つだけカタログ情報の列が必要な場合に使用されます。 *列*は**nvarchar (384)**、既定値は NULL です。 場合*列*が指定されていないすべての列が返されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、*列*に記載されている列の名前を表す、 **syscolumns**テーブル。 ワイルドカードによるパターン照合がサポートされています。 相互運用可能性を最大にするため、ゲートウェイのクライアントは、SQL-92 標準のパターン照合 (% と _ ワイルドカード文字) のみを想定してください。  
  
 [  **@ODBCVer=**] *ODBCVer*  
 使用されている ODBC のバージョンです。 *ODBCVer*は**int**、既定値は 2 です。 既定値の 2 は ODBC Version 2 を示します。 有効な値は 2 または 3 です。 バージョン 2 および 3 の間での動作の違いは、ODBC を参照してください。 **SQLColumns**仕様です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
 **Sp_columns**カタログ ストアド プロシージャは等価**SQLColumns** ODBC にします。 返される結果は並べ**TABLE_QUALIFIER**、 **TABLE_OWNER**、および**TABLE_NAME**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|オブジェクト修飾子の名前です。 このフィールドには NULL を指定できます。|  
|**TABLE_OWNER**|**sysname**|オブジェクトの所有者の名前です。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|オブジェクト名です。 このフィールドは常に値を返します。|  
|**COLUMN_NAME**|**sysname**|各列の列名、 **TABLE_NAME**が返されます。 このフィールドは常に値を返します。|  
|**DATA_TYPE**|**smallint**|ODBC データ型の整数コードです。 ODBC のデータ型にマップできないデータ型の場合は、NULL になります。 ネイティブ データ型の名前が返されます、 **TYPE_NAME**列です。|  
|**TYPE_NAME**|**sysname**|データ型を表す文字列。 基になる DBMS によって、このデータ型の名前が提供されます。|  
|**PRECISION**|**int**|有効桁数です。 戻り値、**精度**列は 10 進数。|  
|**LENGTH**|**int**|データのサイズを転送します。<sup>1</sup>|  
|**小数点以下桁数**|**smallint**|小数点より右側の桁数です。|  
|**RADIX**|**smallint**|数値データ型の基数。|  
|**NULLABLE**|**smallint**|NULL 値を許容するかどうかを示します。<br /><br /> 1 = NULL 値を許容します。<br /><br /> 0 = NULL 値を許容しません。|  
|**「解説」**|**varchar(254)**|このフィールドは常に NULL を返します。|  
|**COLUMN_DEF**|**nvarchar (4000)**|列の既定値です。|  
|**SQL_DATA_TYPE**|**smallint**|記述子の TYPE フィールドでの SQL データ型の値です。 この列は、同じ、 **DATA_TYPE**列を除き、 **datetime**と sql-92**間隔**データ型。 この列は、常に値を返します。|  
|**SQL_DATETIME_SUB**|**smallint**|サブタイプ コード**datetime**と sql-92**間隔**データ型。 他のデータ型の場合、この列は NULL を返します。|  
|**CHAR_OCTET_LENGTH**|**int**|文字型または整数型の列の最大長 (バイト単位)。 他のすべてのデータ型では、この列は NULL を返します。|  
|**ORDINAL_POSITION**|**int**|オブジェクト内での列の序数です。 オブジェクト内の最初の列は 1 です。 この列は、常に値を返します。|  
|**IS_NULLABLE**|**varchar(254)**|オブジェクト内の列の NULL 値の許容属性です。 NULL 値の許容属性の検査は ISO の規則に従います。 ISO SQL に準拠している DBMS では、空文字列を返すことはできません。<br /><br /> YES = 列に NULL を含むことができます。<br /><br /> NO = 列に NULL を含むことができません。<br /><br /> NULL が許可されているかどうかがわからない列は、長さ 0 の文字列を返します。<br /><br /> この列が返される値と異なる値が返される、 **NULLABLE**列です。|  
|**SS_DATA_TYPE**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用されるデータ型は拡張ストアド プロシージャです。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。|  
  
 <sup>1</sup>詳細については、Microsoft ODBC のドキュメントを参照してください。  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT および VIEW DEFINITION 権限が必要です。  
  
## <a name="remarks"></a>解説  
 **sp_columns**区切られた識別子の要件に依存します。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
 次の例では、指定されたテーブルの列情報を返します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_columns @table_name = N'Department',  
   @table_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、指定されたテーブルの列情報を返します。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_columns @table_name = N'DimEmployee',  
   @table_owner = N'dbo';  
```  
  
## <a name="see-also"></a>参照  
 [sp_tables &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-transact-sql.md)   
 [ストアド プロシージャ カタログ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  


