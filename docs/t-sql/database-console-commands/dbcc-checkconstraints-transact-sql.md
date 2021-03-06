---
title: DBCC CHECKCONSTRAINTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DBCC CHECKCONSTRAINTS
- DBCC_CHECKCONSTRAINTS_TSQL
- CHECKCONSTRAINTS
- CHECKCONSTRAINTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DBCC CHECKCONSTRAINTS statement
- consistency [SQL Server], constraints
- checking constraint consistency
- constraints [SQL Server], consistency checks
- integrity [SQL Server], constraints
ms.assetid: da6c9cee-6687-46e8-b504-738551f9068b
caps.latest.revision: 45
author: uc-msft
ms.author: umajay
manager: craigg
ms.openlocfilehash: a274fea3b1171774def99daea9248ca96cd4c365
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dbcc-checkconstraints-transact-sql"></a>DBCC CHECKCONSTRAINTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

現在のデータベースで、指定した制約や指定したテーブルのすべての制約に関する整合性をチェックします。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC CHECKCONSTRAINTS  
[   
    (   
    table_name | table_id | constraint_name | constraint_id   
    )  
]  
    [ WITH   
    [ { ALL_CONSTRAINTS | ALL_ERRORMSGS } ]  
    [ , ] [ NO_INFOMSGS ]   
    ]  
```  
  
## <a name="arguments"></a>引数  
 *table_name* | *table_id* | *constraint_name* | *constraint_id*  
 チェックするテーブルまたは制約を指定します。 *table_name* または *table_id* を指定した場合は、そのテーブルで有効な制約がすべてチェックされます。 *constraint_name* または *constraint_id* を指定した場合は、その制約のみがチェックされます。 テーブル識別子も制約識別子も指定しない場合は、現在のデータベース内にあるすべてのテーブルで有効なすべての制約がチェックされます。  
 制約名によって、その制約が属するテーブルが一意に識別されます。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
 のすべてのメンションを  
 オプションを指定可能にします。  
  
 ALL_CONSTRAINTS  
 テーブル名を指定した場合、またはすべてのテーブルがチェックされる場合、テーブルのすべての有効な制約および無効な制約がチェックされます。それ以外の場合は、有効な制約のみがチェックされます。 制約名を指定した場合、ALL_CONSTRAINTS は無効になります。  
  
 ALL_ERRORMSGS  
 チェック対象となるテーブル内の制約に違反する行をすべて返します。 既定では、先頭から 200 行までが返されます。  
  
 NO_INFOMSGS  
 すべての情報メッセージを表示しないようにします。  
  
## <a name="remarks"></a>Remarks  
DBCC CHECKCONSTRAINTS では、テーブルのすべての FOREIGN KEY 制約および CHECK 制約に対してクエリが作成され実行されます。
  
たとえば、外部キー クエリは次のような形式になります。
  
```sql
SELECT <columns>  
FROM <table_being_checked> LEFT JOIN <referenced_table>  
    ON <table_being_checked.fkey1> = <referenced_table.pkey1>   
    AND <table_being_checked.fkey2> = <referenced_table.pkey2>  
WHERE <table_being_checked.fkey1> IS NOT NULL   
    AND <referenced_table.pkey1> IS NULL  
    AND <table_being_checked.fkey2> IS NOT NULL  
    AND <referenced_table.pkey2> IS NULL  
```  
  
クエリ データは temp テーブルに格納されます。 指定したすべてのテーブルまたは制約がチェックされた後、結果セットが返されます。
DBCC CHECKCONSTRAINTS では、FOREIGN KEY 制約と CHECK 制約の整合性はチェックされますが、テーブルのディスク上のデータ構造に関する整合性はチェックされません。 このようなデータ構造のチェックは、[DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) および [DBCC CHECKTABLE](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md) で実行できます。
  
**適用対象**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
*table_name* または *table_id* が指定されており、システムのバージョン管理で有効になっている場合、DBCC CHECKCONSTRAINTS では、指定したテーブルで、テンポラル データの整合性チェックも行います。 このコマンドでは、*NO_INFOMSGS* が指定されていない場合、それぞれの整合性違反を別の行に出力します。 出力は、([pkcol1], [pkcol2]..) = (\<pkcol1_value>, \<pkcol2_value>…) AND \<what is wrong with temporal table record> になります。
  
|[確認]|チェックが失敗した場合の出力に追加の情報|  
|-----------|-----------------------------------------------|  
|PeriodEndColumn ≥ PeriodStartColumn (current)|[sys_end] = '{0}' AND MAX(DATETIME2) = '9999-12-31 23:59:59.99999'|  
|PeriodEndColumn ≥ PeriodStartColumn (current, history)|[sys_start] = '{0}' AND [sys_end] = '{1}'|  
|PeriodStartColumn < current_utc_time (current)|[sys_start] = '{0}' AND SYSUTCTIME|  
|PeriodEndColumn < current_utc_time (history)|[sys_end] = '{0}' AND SYSUTCTIME|  
|重複|(sys_start1, sys_end1) , (sys_start2, sys_end2) 2 つの重複するレコード。<br /><br /> レコードが重複している 2 以上の場合がある場合、出力は、1 組の重複を示す複数の行でがあります。|  
  
のみ一時的な整合性チェックを実行するために、constraint_name または constraint_id を指定する方法はありません。
  
## <a name="result-sets"></a>結果セット  
DBCC CHECKCONSTRAINTS では、次の列を含む行セットが返されます。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|テーブル名|**varchar**|テーブルの名前。|  
|Constraint Name|**varchar**|違反している制約の名前。|  
|場所|**varchar**|制約に違反している 1 つ以上の行を識別する列値の割り当て。<br /><br /> この列の値は、制約に違反する行をクエリする SELECT ステートメントの WHERE 句で使用できます。|  
  
## <a name="permissions"></a>アクセス許可  
**sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。
  
## <a name="examples"></a>使用例  
  
### <a name="a-checking-a-table"></a>A. テーブルをチェックする  
次の例では、`Table1` データベースにある `AdventureWorks` テーブルの制約の整合性をチェックします。
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE TABLE Table1 (Col1 int, Col2 char (30));  
GO  
INSERT INTO Table1 VALUES (100, 'Hello');  
GO  
ALTER TABLE Table1 WITH NOCHECK ADD CONSTRAINT chkTab1 CHECK (Col1 > 100);  
GO  
DBCC CHECKCONSTRAINTS(Table1);  
GO  
```  
  
### <a name="b-checking-a-specific-constraint"></a>B. 特定の制約をチェックする  
次の例では、`CK_ProductCostHistory_EndDate` 制約の整合性をチェックします。
  
```sql  
USE AdventureWorks2012;  
GO  
DBCC CHECKCONSTRAINTS ('Production.CK_ProductCostHistory_EndDate');  
GO  
```  
  
### <a name="c-checking-all-enabled-and-disabled-constraints-on-all-tables"></a>C. すべてのテーブルについて、すべての有効な制約と無効な制約をチェックする  
 次の例では、現在のデータベース内にあるすべてのテーブルが持つ、すべての有効な制約と無効な制約の整合性をチェックします。  
  
```sql  
DBCC CHECKCONSTRAINTS WITH ALL_CONSTRAINTS;  
GO  
```  
  
## <a name="see-also"></a>参照  
[DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
[DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
