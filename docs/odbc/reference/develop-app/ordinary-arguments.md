---
title: 通常の引数 |Microsoft ドキュメント
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
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ecdcf5e697bcf3235cadbe3d8f3f8f981406575
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ordinary-arguments"></a>通常の引数
カタログ関数の文字列引数に通常の引数がある場合は、リテラル文字列として扱われます。 通常の引数は、文字列検索パターンにも値の一覧を受け入れます。 通常の引数の場合は、重要でし、文字列の引用符文字がどおりです。 SQL_ATTR_METADATA_ID ステートメント属性が SQL_FALSE; に設定されている場合、これらの引数は通常の引数として扱われますとして扱われます識別子引数代わりにこの属性が SQL_TRUE に設定されている場合。  
  
 SQL_ERROR と SQLSTATE HY009 場合、通常の引数が null ポインターに設定されているし、引数が必要な引数、関数を返します (null ポインターの使い方が正しくありません)。 通常の引数が null ポインターに設定され、引数が必要な引数ではない場合の引数の動作はドライバーに依存します。 必須の引数は、次の表に一覧表示されます。  
  
|関数|必須の引数|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*、 *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|
