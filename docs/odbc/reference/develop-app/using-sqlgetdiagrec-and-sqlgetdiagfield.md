---
title: SQLGetDiagRec および SQLGetDiagField を使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 4f486bb1-fad8-4064-ac9d-61f2de85b68b
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 555bc3ba25ba895b54384acb8772a4b4293e61c1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-sqlgetdiagrec-and-sqlgetdiagfield"></a>SQLGetDiagRec および SQLGetDiagField を使用してください。
アプリケーションのコール**SQLGetDiagRec**または**SQLGetDiagField**診断情報を取得します。 これらの関数は、環境、接続、ステートメント、または記述子ハンドルをそのまま使用し、最後にそのハンドルを使用した関数から診断を返します。 ハンドルを使用して、新しい関数が呼び出されたときに、特定のハンドルにログオンしているため、診断が破棄されます。 関数に複数の診断レコードが返される場合は、アプリケーションが呼び出すこれらの関数複数回です。状態レコードの合計数が呼び出すことによって取得**SQLGetDiagField** SQL_DIAG_NUMBER オプションを使用してヘッダー レコード (レコード 0) です。  
  
 アプリケーションを呼び出して個々 の診断フィールドを取得する**SQLGetDiagField**を取得するフィールドを指定するとします。 特定の診断フィールドには、特定の種類のハンドルのすべての意味はありません。 診断フィールドとその意味の一覧は、次を参照してください。、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)関数の説明。  
  
 アプリケーションでは呼び出すことによって、SQLSTATE、ネイティブ エラー コード、および 1 回の呼び出しで診断メッセージが取得**SQLGetDiagRec**です。**SQLGetDiagRec**ヘッダー レコードから情報を取得するのには使用できません。  
  
 たとえば、次のコードでは、SQL ステートメントの入力を求め、それを実行します。 呼び出す場合は、診断情報が返され、 **SQLGetDiagField**状態レコードの数を取得し、 **SQLGetDiagRec**ものから、SQLSTATE、ネイティブ エラー コード、および診断メッセージを取得するにはレコードがあります。  
  
```  
SQLCHAR       SqlState[6], SQLStmt[100], Msg[SQL_MAX_MESSAGE_LENGTH];  
SQLINTEGER    NativeError;  
SQLSMALLINT   i, MsgLen;  
SQLRETURN     rc1, rc2;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement.  
GetSQLStmt(SQLStmt);  
  
// Execute the SQL statement and return any errors or warnings.  
rc1 = SQLExecDirect(hstmt, SQLStmt, SQL_NTS);  
if ((rc1 == SQL_SUCCESS_WITH_INFO) || (rc1 == SQL_ERROR)) {
   SQLLEN numRecs = 0;
   SQLGetDiagField(SQL_HANDLE_STMT, hstmt, 0, SQL_DIAG_NUMBER, &numRecs, 0, 0);
   // Get the status records.
   i = 1;  
   while (i <= numRecs && (rc2 = SQLGetDiagRec(SQL_HANDLE_STMT, hstmt, i, SqlState, &NativeError,  
            Msg, sizeof(Msg), &MsgLen)) != SQL_NO_DATA) {  
      DisplayError(SqlState,NativeError,Msg,MsgLen);  
      i++;  
   }  
}  
  
if ((rc1 == SQL_SUCCESS) || (rc1 == SQL_SUCCESS_WITH_INFO)) {  
   // Process statement results, if any.  
}  
```
