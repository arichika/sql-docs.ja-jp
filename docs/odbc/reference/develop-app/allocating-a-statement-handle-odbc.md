---
title: ODBC ステートメント ハンドルを割り当て |Microsoft ドキュメント
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
- SQL statements [ODBC], statement handles
- statement handles [ODBC]
- allocating statement handles [ODBC]
- handles [ODBC], statement
ms.assetid: 4ce3b446-34ab-46dc-96e5-f40ec95c267e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2d0f2bd2da071bb690443df9d5c0bdebb5a5e1e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="allocating-a-statement-handle-odbc"></a>ODBC ステートメント ハンドルを割り当てください。
アプリケーションがステートメントを実行する前に、必要があります、ステートメント ハンドルに割り当てます。  
  
1.  アプリケーションでは、HSTMT の型の変数を宣言します。 呼び出して**SQLAllocHandle**し、この変数は、ステートメント、および SQL_HANDLE_STMT オプションを割り当てる接続のハンドルのアドレスを渡します。 以下に例を示します。  
  
    ```  
    SQLHSTMT hstmt1;  
  
    SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
    ```  
  
2.  ドライバー マネージャーには、ステートメントおよび呼び出しに関する情報を格納する構造体が割り当てられます。 **SQLAllocHandle** SQL_HANDLE_STMT オプションを使用して、ドライバーでします。  
  
3.  ドライバーは、ステートメントの情報を格納するための独自の構造の割り当てし、ドライバー マネージャーにドライバーは、ステートメント ハンドルを返します。  
  
4.  ドライバー マネージャーは、アプリケーション変数にアプリケーションをドライバー マネージャーは、ステートメント ハンドルを返します。  
  
 ステートメント ハンドルでは、ODBC 関数を呼び出すときに使用する内のどのステートメントを識別します。 ステートメント ハンドルの詳細については、次を参照してください。[ステートメント ハンドル](../../../odbc/reference/develop-app/statement-handles.md)です。
