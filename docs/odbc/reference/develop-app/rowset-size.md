---
title: 行セット サイズ |Microsoft ドキュメント
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
- rowset size [ODBC]
- cursors [ODBC], block
- result sets [ODBC], rowset size
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 60366ae8-175c-456a-ae5e-bdd860786911
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0fa3d2feb8bcd3c4c342567e67f403edfb8029a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="rowset-size"></a>行セット サイズ
使用するには、どの行セット サイズは、アプリケーションによって異なります。 通常、画面ベースのアプリケーションでは、2 つの方法に従います。 1 つは、行セット サイズを画面に表示される行の数に設定するのにはアプリケーションをユーザーが画面を変更する場合、行セットのサイズがそれに応じて変わります。 2 番目をより大きな数値に 100 など、データ ソースへの呼び出しの数が減少行セットのサイズを設定することです。 アプリケーションでは、可能な場合は、行セット内でローカルにまでスクロールし、行セットの外部スクロール場合にのみ新しい行がフェッチされます。  
  
 レポートなど、他のアプリケーションは、アプリケーションが適切に処理できる最大行数を行セットのサイズを設定する傾向があります:、大規模な行セットの行ごとのオーバーヘッドがネットワークは縮小にことがあります。 正確に大きさを行セットを指定できますは各行と、使用可能なメモリの量のサイズによって異なります。  
  
 行セットのサイズの設定への呼び出しによって**SQLSetStmtAttr**で、*属性*引数 sql_attr_row_array_size を指定します。 アプリケーションが行セットのサイズを変更する、新しい行セットのバッファーをバインド (を呼び出して**SQLBindCol**バインディング オフセットを指定するか) の行がフェッチされた後でもまたはその両方です。 行セットのサイズの変更による影響は、関数に依存します。  
  
-   **SQLFetch**と**SQLFetchScroll**をフェッチする行数を決定する、呼び出し時に行セットのサイズを使用します。 ただし、 **SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_NEXT 増分のカーソルの行セットに基づく前回フェッチとし、フェッチの現在の行セットのサイズに基づく行セット。  
  
-   **SQLSetPos**前の呼び出しの時点で有効になっている行セットのサイズを使用して**SQLFetch**または**SQLFetchScroll**ので、 **SQLSetPos**行セットに対する動作既に設定されています。 **SQLSetPos**も場合を選択し、新しい行セット サイズを**SQLBulkOperations**が行セットのサイズが変更された後に呼び出されています。  
  
-   **SQLBulkOperations**すべてフェッチされる行セットの独立したテーブルに対する操作が実行されるため、呼び出し時に有効で、行セット サイズを使用します。
