---
title: 実装に関するメモ |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7ec14b9c-69b8-4c6e-838a-88d1ebdc8725
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdb41ae80eedb2a5204ddc6769f0e90714d51585
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="implementation-notes"></a>実装に関するメモ
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このセクションでは、ODBC カーソル ライブラリを実装する方法について説明します。 カーソル ライブラリによるそのキャッシュに格納方法、SQL ステートメントを実行方法、および ODBC 関数を実装する方法を説明します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カーソル ライブラリのキャッシュ](../../../odbc/reference/appendixes/cursor-library-cache.md)  
  
-   [SQL ステートメントの処理](../../../odbc/reference/appendixes/processing-sql-statements.md)  
  
-   [ODBC 関数およびカーソル ライブラリ](../../../odbc/reference/appendixes/odbc-functions-and-the-cursor-library.md)
