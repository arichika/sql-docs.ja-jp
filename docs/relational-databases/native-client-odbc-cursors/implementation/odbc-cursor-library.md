---
title: ODBC カーソル ライブラリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], library
- SQL_CUR_USE_DRIVER option
- ODBC applications, cursors
- ODBC cursors, library
- SQL_CUR_USE_IF_NEEDED option
- SQLSetConnectAttr function
- SQL_CUR_USE_ODBC option
ms.assetid: 3c610d3d-6e06-49cf-9a40-05b6a1c83a32
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4febdebab0e8b360889ba9b26f1904cbc61cf8f4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-cursor-library"></a>ODBC カーソル ライブラリ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  一部の ODBC ドライバーは、既定のカーソル設定しかサポートします。これらのドライバーもサポートしません、カーソルの位置指定操作など**SQLSetPos**です。 ODBC カーソル ライブラリは、通常はブロック カーソルや静的カーソルがサポートされないドライバーに対して、これらのカーソルを実装するときに使用される MDAC (Microsoft Data Access Components) のコンポーネントです。 カーソル ライブラリでは、位置指定の UPDATE および DELETE ステートメントも実装しておよび**SQLSetPos**を作成するカーソル。  
  
 ODBC カーソル ライブラリは、ODBC ドライバー マネージャーと ODBC ドライバーの中間層として実装されます。 ODBC ドライバー マネージャーは、ODBC カーソル ライブラリが読み込まれると、すべてのカーソル関連コマンドをドライバーではなく、読み込んだカーソル ライブラリにルーティングします。 カーソル ライブラリでは、基になるドライバーから結果セット全体をフェッチし、その結果セットをクライアントにキャッシュすることにより、カーソルを実装します。 ODBC カーソル ライブラリを使用しているときは、アプリケーションではカーソル ライブラリのカーソル機能だけをサポートし、基になるドライバーの追加のカーソル機能はサポートしません。  
  
 ODBC カーソル ライブラリを使用する必要はほとんどありません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、ドライバーでは、ODBC カーソル ライブラリよりも多くのカーソル機能をサポートしているためです。 ODBC カーソル ライブラリを使用する唯一の理由、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ドライバーがサーバー カーソルを使用して、カーソルのサポートを実装し、サーバー カーソルはすべての SQL ステートメントをサポートしていません。 ストアド プロシージャ、バッチ、または COMPUTE、COMPUTE BY、FOR BROWSE、INTO などを含む SQL ステートメントで静的カーソルを使用する必要がある場合は、ODBC カーソル ライブラリの使用を検討してください。 ただし、カーソル ライブラリを使用する場合、結果セット全体がクライアントにキャッシュされるので、大量のメモリが使用され、パフォーマンスが低下することがあるので注意が必要です。  
  
 アプリケーションが使用して、接続の接続によってごとに、カーソル ライブラリを呼び出します[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)をデータ ソースに接続する前に SQL_ATTR_ODBC_CURSORS 接続属性を設定します。 SQL_ATTR_ODBC_CURSORS には、次の 3 つの値のいずれかを設定します。  
  
 SQL_CUR_USE_ODBC  
 このオプションを設定すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、ODBC カーソル ライブラリよりも優先、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのネイティブ カーソル サポートします。 接続で使用できるのは、カーソル ライブラリでサポートされているカーソルのみで、サーバー カーソルは使用できません。  
  
 SQL_CUR_USE_DRIVER   
 ネイティブにサポートのすべてのカーソルは、このオプションが設定されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、接続に使用することができます。 この場合、ODBC カーソル ライブラリは使用できません。 すべてのカーソルはサーバー カーソルとして実装されます。  
  
 SQL_CUR_USE_IF_NEEDED   
 結果は SQL_CUR_USE_DRIVER と共に使用する場合と同じでは、このオプションが設定されている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー。 接続時に、ODBC ドライバー マネージャーのテストに接続されている ODBC ドライバーの SQL_FETCH_PRIOR オプションでサポートされているかどうかに[SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)です。 ドライバーでこのオプションがサポートされていない場合、ODBC ドライバー マネージャーは ODBC カーソル ライブラリを読み込みます。 サポートされている場合、ODBC ドライバー マネージャーは ODBC カーソル ライブラリを読み込みません。この場合、アプリケーションではドライバーのネイティブ サポートが使用されます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーには SQL_FETCH_PRIOR がサポートしている、ODBC ドライバー マネージャーは ODBC カーソル ライブラリを読み込めません。  
  
 カーソル ライブラリにより、アプリケーションはスクロール可能なカーソルや更新可能なカーソルを使用できるだけでなく、1 つの接続に対して複数のアクティブ ステートメントを使用できます。 この機能をサポートする場合は、カーソル ライブラリを読み込む必要があります。 使用して[SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)カーソル ライブラリを使用する方法を指定して[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)カーソルの種類、同時実行性、および行セット サイズを指定します。  
  
## <a name="see-also"></a>参照  
 [カーソルの実装方法](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
