---
title: SQLTransact マッピング |Microsoft ドキュメント
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
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e938a4eb7c605d1ed9cf71c038bcc7187e1a8cb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqltransact-mapping"></a>SQLTransact マッピング
**SQLTransact**置き換わっています**SQLEndTran**です。 2 つの関数の主な違いを**SQLEndTran**引数を含む*HandleType*を実行する作業のスコープを指定します。 *HandleType*引数は、環境または接続ハンドルを指定できます。 次の呼び出しに**SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 をマップされます。  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 場合*ConnectionHandle*が SQL_NULL_HDBC と等しくありません。 *ConnectionHandle*引数の値に設定されて*hdbc*です。  
  
 **SQL_Transact**にマップされます  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 場合*ConnectionHandle* SQL_NULL_HDBC を等しきます。 *EnvironmentHandle*引数の値に設定されて*henv*です。  
  
 前のケースの両方で、 *CompletionType*引数と同じ値に設定されて*fType*です。
