---
title: ストアド プロシージャを呼び出す |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- ODBC, stored procedures
- stored procedures [ODBC], calling
- SQL Server Native Client ODBC driver, stored procedures
- ODBC CALL escape sequence
- escape sequences [SQL Server]
- CALL statement
ms.assetid: d13737f4-f641-45bf-b56c-523e2ffc080f
caps.latest.revision: 41
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b06c46a9043c13b60d65117b3418b807107f3764
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="calling-a-stored-procedure"></a>ストアド プロシージャの呼び出し
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、両方、ODBC CALL エスケープ シーケンスをサポートしていると、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [EXECUTE](../../t-sql/language-elements/execute-transact-sql.md)ステートメントを実行するためのストアド プロシージャ以外の場合は、ODBC CALL エスケープ シーケンスは、推奨される方法です。 ODBC 構文を使用すると、アプリケーションでストアド プロシージャのリターン コードを取得できます。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行するコンピューター間のリモート プロシージャ コール (RPC) の送信向けに開発されているプロトコルを使用するように最適化されます。 この RPC プロトコルでは、サーバー側で実行されるパラメーター処理やステートメントの解析作業の多くを排除することで、パフォーマンスを向上しています。  
  
> [!NOTE]  
>  呼び出すときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ストアド プロシージャが ODBC で名前付きパラメーターの使用 (詳細については、次を参照してください。[名前 (名前付きパラメーター) でのパラメーターのバインド](http://go.microsoft.com/fwlink/?LinkID=209721))、パラメーター名の先頭は、' @' 文字です。 これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 固有の制限です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、Microsoft Data Access Components (MDAC) の場合よりも厳密にこの制限が適用されます。  
  
 プロシージャを呼び出す ODBC CALL エスケープ シーケンスは、次の構文を使用します。  
  
 {**[?=]****call***procedure_name*[([*parameter*][**,**[* parameter*]]...)]}  
  
 ここで*procedure_name*プロシージャの名前を指定し、*パラメーター*プロシージャのパラメーターを指定します。 名前付きパラメーターは、ODBC CALL エスケープ シーケンスを使用するステートメントでのみサポートされます。  
  
 プロシージャには、0 個以上のパラメーターを指定できます。 また、構文の先頭に省略可能なパラメーター マーカー ?= を指定することによって値を返すこともできます。 パラメーターが入力パラメーターまたは入出力パラメーターの場合は、リテラルまたはパラメーター マーカーを使用できます。 パラメーターが出力パラメーターの場合、出力は不明なので、パラメーター マーカーを使用する必要があります。 パラメーター マーカーにバインドする必要があります[SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)プロシージャ呼び出しの前にステートメントを実行します。  
  
 プロシージャ呼び出しでは、入力パラメーターと入出力パラメーターを省略できます。 かっこだけを指定し、パラメーターを指定しないでプロシージャを呼び出した場合、ドライバーは最初のパラメーターの既定値を使用するように、データ ソースに指示します。 以下に例を示します。  
  
 {**呼び出す*** procedure_name ***に関するページ ()**}  
  
 プロシージャにパラメーターを指定しないと、失敗する可能性があります。 かっこを付けないでプロシージャを呼び出すと、ドライバーはパラメーター値を送信しません。 以下に例を示します。  
  
 {**call** *procedure_name*}  
  
 プロシージャ呼び出しでは、入力パラメーターや入出力パラメーターとしてリテラルを指定できます。 たとえば、InsertOrder プロシージャには 5 つの入力パラメーターがあるとします。 次の InsertOrder の呼び出しでは、最初のパラメーターを省略し、2 番目のパラメーターとしてリテラルを指定して、3 番目、4 番目、5 番目のパラメーターとしてパラメーター マーカーを使用しています (パラメーターには、値 1 から始まる序数が付けられます)。  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}  
```  
  
 パラメーターを省略する場合でも、他のパラメーターとの区切りを示すコンマは省略できないことに注意してください。 入力パラメーターまたは入出力パラメーターを省略すると、プロシージャはそのパラメーターの既定値を使用します。 他の方法で入力パラメーターまたは入出力パラメーターの既定値を指定するには、そのパラメーターにバインドされる長さ/インジケーター バッファーの値を SQL_DEFAULT_PARAM に設定するか、DEFAULT キーワードを使用します。  
  
 入出力パラメーターを省略した場合、または入出力パラメーターとしてリテラルを指定した場合、ドライバーは出力値を破棄します。 同様に、プロシージャの戻り値のパラメーター マーカーを省略した場合、ドライバーは戻り値を破棄します。 最後に、値を返さないプロシージャに戻り値パラメーターを指定すると、ドライバーは、そのパラメーターにバインドされる長さ/インジケーター バッファーの値を SQL_NULL_DATA に設定します。  
  
## <a name="delimiters-in-call-statements"></a>CALL ステートメント内の区切り記号  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]既定の Native Client ODBC ドライバーには、ODBC {CALL} エスケープ シーケンスに固有の互換性オプションもサポートしています。 ドライバーは、1 組の二重引用符でストアド プロシージャ名全体を区切る CALL ステートメントを受け付けます。  
  
```  
{ CALL "master.dbo.sp_who" }  
```  
  
 また既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、ISO の規則に従い、各識別子を二重引用符で囲んだ CALL ステートメントも受け付けます。  
  
```  
{ CALL "master"."dbo"."sp_who" }  
```  
  
 ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを既定の設定で実行している場合、ISO 標準では無効とされている文字を含む識別子については、どちらの形式の引用符の使用もサポートされません。 ドライバーがという名前のストアド プロシージャにアクセスできないなど、 **"My.Proc"** 引用符付き識別子を含む CALL ステートメントを使用します。  
  
```  
{ CALL "MyDB"."MyOwner"."My.Proc" }  
```  
  
 このステートメントは、ドライバーでは次のように解釈されます。  
  
```  
{ CALL MyDB.MyOwner.My.Proc }  
```  
  
 リンク サーバーがというエラーが発生、 **MyDB**存在しません。  
  
 この問題は、角かっこで囲まれる識別子を使用すると発生しません。つまり、次のステートメントは正しく解釈されます。  
  
```  
{ CALL [MyDB].[MyOwner].[My.Table] }  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャの実行](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
  
