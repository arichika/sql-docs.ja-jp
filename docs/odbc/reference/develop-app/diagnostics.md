---
title: 診断 |Microsoft ドキュメント
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
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d2db5f46fc157015f035775ac185fb9005de8a6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="diagnostics"></a>診断
Odbc 関数では、2 つの方法で診断情報を返します。 リターン コードでは、診断レコードが、関数に関する詳細情報を提供中に、全体の成功または失敗、関数を示します。 少なくとも 1 つの診断レコード — ヘッダー レコード: 関数が成功した場合でも返されます。  
  
 診断情報は、ハード コーディングされた SQL ステートメントで無効なハンドルなどのプログラミング エラーや構文エラーをキャッチする開発時に使用されます。 ユーザーが入力した SQL ステートメントの実行時エラーとデータの切り捨て、アクセス違反、構文エラーなどの警告をキャッチする実行時に使用されます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [リターン コード](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [診断レコード](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField の使用](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField の実装](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [診断処理の例](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
