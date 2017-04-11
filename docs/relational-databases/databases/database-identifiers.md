---
title: "データベース識別子 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "標準識別子 [SQL Server]"
  - "識別子 [SQL Server]"
  - "名前 [SQL Server], 識別子"
  - "識別子 [SQL Server], 識別子について"
  - "SQL Server 識別子"
  - "Transact-SQL 識別子"
  - "名前のデータベース オブジェクト [SQL Server]"
ms.assetid: 171291bb-f57f-4ad1-8cea-0b092d5d150c
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# データベース識別子
  データベース オブジェクトの名前は識別子と呼ばれます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、すべてのオブジェクトに識別子を設定できます。 サーバーやデータベース、またはテーブル、ビュー、列、インデックス、トリガー、プロシージャ、制約、規則などのデータベース オブジェクトに対して識別子を割り当てることができます。 ほとんどのオブジェクトには識別子が必要です。ただし、制約などの一部のオブジェクトについては、識別子は省略可能です。  
  
 オブジェクトの識別子は、オブジェクトを定義するときに作成されます。 作成された識別子を使用して、そのオブジェクトを参照できます。 たとえば、次のステートメントは識別子が `TableX` であるテーブル 1 つと、識別子がそれぞれ `KeyCol`、`Description` である 2 つの列を作成します。  
  
```  
CREATE TABLE TableX  
(KeyCol INT PRIMARY KEY, Description nvarchar(80))  
```  
  
 このテーブルには名前のない制約も含まれます。 `PRIMARY KEY` 制約には識別子がありません。  
  
 識別子の照合順序は、識別子が定義されているレベルによって異なります。 ログイン名やデータベース名など、インスタンスレベルのオブジェクトの識別子には、インスタンスの既定の照合順序が指定されます。 テーブル名、ビュー名、列名など、データベース内のオブジェクトの識別子には、データベースの既定の照合順序が指定されます。 たとえば、大文字と小文字を区別する照合順序が指定されたデータベースでは、同じ名前で大文字と小文字のみが異なる 2 つのテーブルを作成できますが、大文字と小文字を区別しない照合順序が指定されたデータベースでは作成できません。  
  
> [!NOTE]  
>  変数名、関数およびストアド プロシージャのパラメーター名は、[!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子の規則に従っている必要があります。  
  
## 識別子のクラス  
 識別子のクラスには、次の 2 種類があります。  
  
 標準識別子  
 識別子の形式に関する規則に従います。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用するときは、標準識別子を区切る必要はありません。  
  
```  
SELECT *  
FROM TableX  
WHERE KeyCol = 124  
```  
  
 区切られた識別子  
 二重引用符 (") または角かっこ ([ ]) で囲まれています。 識別子の形式に関する規則に従っている識別子は、区切らなくてもかまいません。 例:  
  
```  
SELECT *  
FROM [TableX]         --Delimiter is optional.  
WHERE [KeyCol] = 124  --Delimiter is optional.  
```  
  
 識別子の規則に従わない識別子を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用する場合は、必ず区切らなければなりません。 例:  
  
```  
SELECT *  
FROM [My Table]      --Identifier contains a space and uses a reserved keyword.  
WHERE [order] = 10   --Identifier is a reserved keyword.  
```  
  
 標準識別子および区切られた識別子は、文字、記号 (_ @ #)、および数字を含む 1 ～ 128 個の文字で構成されます。 ローカル一時テーブルの場合、識別子は 116 文字以下でなければなりません。  
  
## 標準識別子に関する規則  
 変数、関数、およびストアド プロシージャの名前は、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子の規則に従っている必要があります。  
  
1.  最初の文字が次のいずれかである必要があります。  
  
    -   Unicode 規格 3.2 で定義されている文字。 Unicode の文字定義には、各国言語の文字の他に、ラテン文字 a ～ z と A ～ Z も含まれます。  
  
    -   アンダースコア (_)、アット マーク (@)、または番号記号 (#)。  
  
         [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、識別子の先頭にある一定の記号には特別な意味があります。 アット マークで始まる標準識別子は、常にローカル変数またはローカル パラメーターを表し、他の種類のオブジェクトの名前としては使用できません。 番号記号で始まる識別子は一時テーブルまたは一時プロシージャを表します。 2 つの番号記号 (##) で始まる識別子は、グローバルな一時オブジェクトを表します。 1 つまたは 2 つの番号記号で始まる名前を、他の種類のオブジェクトの名前として使用することもできますが、このような番号記号の使用はお勧めしません。  
  
         一部の [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数の名前は、2 つのアット マーク (@@) から始まります。 これらの関数との混同を避けるために、@@ から始まる名前は使用しないでください。  
  
2.  名前の先頭以外では、次の文字を使用できます。  
  
    -   Unicode 規格 3.2 で定義されている文字  
  
    -   Basic Latin スクリプトまたはその他の各国スクリプトの 10 進数  
  
    -   アット マーク、ドル記号 ($)、番号記号、またはアンダースコア  
  
3.  [!INCLUDE[tsql](../../includes/tsql-md.md)] 予約語を識別子として使用することはできません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  の予約語は、大文字、小文字ともに予約されています。 これらの規則に従っていない識別子を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用する場合は、二重引用符または角かっこで区切る必要があります。 予約語は、データベースの互換性レベルによって異なります。 このレベルは、[ALTER DATABASE](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) ステートメントを使用して設定できます。  
  
4.  埋め込み型スペースおよび特殊文字は使用できません。  
  
5.  補助文字は使用できません。  
  
 これらの規則に従っていない識別子を [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで使用する場合は、二重引用符または角かっこで区切る必要があります。  
  
> [!NOTE]  
>  標準識別子の形式に関する規則は、データベースの互換性レベルに応じて異なります。 互換性レベルは、[ALTER DATABASE](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md) を使用して設定できます。  
  
## 参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [CREATE RULE &#40;Transact-SQL&#41;](../../t-sql/statements/create-rule-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [CREATE VIEW &#40;Transact-SQL&#41;](../../t-sql/statements/create-view-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [予約済みキーワード &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  