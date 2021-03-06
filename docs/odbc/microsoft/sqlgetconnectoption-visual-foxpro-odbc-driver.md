---
title: SQLGetConnectOption (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLGetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5703eb39-f3b2-4f3a-8676-a5625ae29a41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23654dc89260423ce51fcde1fd60e554a3095209
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetconnectoption-visual-foxpro-odbc-driver"></a>SQLGetConnectOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 部分的な  
  
 レベル 1 の ODBC API への準拠:  
  
 接続オプションの現在の設定を返します。 この関数は部分的にサポートされています: ドライバーのすべての値をサポートしている、 *fOption*引数の一部でサポートされていません*vParam*の値を*fOption*引数SQL_TXN_ISOLATION です。  
  
 次の表に、これらの引数の Visual FoxPro ODBC ドライバーの実装に固有の動作とのみ**SQLGetConnectOption**です。  
  
|*fOption*|解説|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|アプリケーションのコミットまたはでトランザクションをロールバックする必要があります明示的に SQL_AUTOCOMMIT_OFF 場合は、 [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); Visual FoxPro ODBC ドライバーが完了したときに transactable ステートメントを自動的にコミットできません。 ドライバーは、トランザクションを開始するステートメントが transactable 場合。|  
|SQL_CURRENT_QUALIFIER|完全修飾データベース (.dbc ファイル) 名または完全修飾パス 0 個以上のテーブル (.dbf ファイル) を含むディレクトリを指定できます。|  
|SQL_LOGINTIMEOUT|「ドライバー対応していない」エラーが返されます。|  
|SQL_CURSORS|「ドライバー対応していない」エラーが返されます。|  
|SQL_PACKET_SIZE|「ドライバー対応していない」エラーが返されます。|  
|SQL_TXN_ISOLATION|ドライバーは、SQL_TXN_READ_COMMITTED のみを使用します。<br /><br /> 次*vParam*s はサポートされていません。<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 詳細については、次を参照してください。 [SQLGetConnectOption](../../odbc/reference/syntax/sqlgetconnectoption-function.md)で、 *ODBC プログラマ リファレンス*です。
