---
title: ブックマークを取得する |Microsoft ドキュメント
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
- retrieving bookmarks [ODBC]
- result sets [ODBC], bookmarks
- bookmarks [ODBC]
ms.assetid: a34c8f09-b786-4835-a44b-b7294c970aff
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3a78b232a1cdb5564388cdf9b335a5ce06cfcb68
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-bookmarks"></a>ブックマークを取得します。
アプリケーションでのブックマークを使用する場合は、準備またはステートメントを実行する前に SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定があります。 これは、機能は、それらのビルドとメンテナンス ブックマークできる操作が実行される高価なアプリケーションを適切に行うことができる場合にのみ、ブックマークを有効にするために使用するため必要です。  
  
 ブックマークは、結果セットの列 0 として返されます。 アプリケーションが取得できる 3 つの方法があります。  
  
-   結果セットの列 0 をバインドします。 **SQLFetch**または**SQLFetchScroll**バインドされた列の他のデータと共に、行セット内の行ごとに、それらのブックマークを返します。  
  
-   呼び出す**SQLSetPos**行セット内の行に位置し、呼び出す**SQLGetData**列 0 です。 呼び出すことを常にサポートする必要があります、ドライバーは、ブックマークをサポートする場合**SQLGetData**列 0 で、アプリケーションを呼び出すことはできない場合でも**SQLGetData**最終バインドする前に他の列の列です。  
  
-   呼び出す**SQLBulkOperations**で、*操作*引数 SQL_ADD に設定し、バインドされている列 0 です。 カーソルは、行を挿入し、バインドされたバッファーの行のブックマークを返します。
