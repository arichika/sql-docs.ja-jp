---
title: 標準的なプログラミング インターフェイス |Microsoft ドキュメント
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
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e820b626ce8e4f207885b8c7e5dd5cdc7050f960
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="standard-programming-interface"></a>標準的なプログラミング インターフェイス
プログラミング インターフェイスが標準化のための最も明白な候補ではおそらくです。 実際には、ODBC の開発中、時に ANSI および ISO 既に提供されている標準 embedded SQL および SQL モジュール。 CLI は、SQL アクセス グループのデータベースの標準は存在しないが、業界 consortium データベース ベンダーの —; を作成するかどうかを考えていたODBC の後の部分では、その作業の基礎になりました。  
  
 ODBC の要件の 1 つは、バイナリの 1 つのアプリケーションが複数の Dbms で作業しなければならなかったことでした。 これは、ODBC が埋め込まれた SQL またはモジュールの言語を使用していないためです。 埋め込まれた SQL およびモジュールの言語で言語が標準化が DBMS 固有 precompilers にそれぞれ関連付けられています。 したがって、各 DBMS 用アプリケーションを再コンパイルする必要があり、結果のバイナリが 1 つのデータベース管理システムでのみ動作します。 とはいえ、これはミニとメインフレーム世界で見つかった小規模なアプリケーションにとって十分な余裕がないパーソナル コンピューターの世界でします。 まず、顧客; 大量、シュリンク ラップされたソフトウェアの複数のバージョンを提供する運用大変な作業が次に、パーソナル コンピューターのアプリケーションでは、複数の Dbms を同時にアクセスする必要があります。  
  
 ライブラリ、または各ローカル コンピューター上に存在するデータベース ドライバーを使って呼び出しレベルのインターフェイスを実装する一方で、別のドライバーは、各 DBMS 必要があります。 単一のアプリケーションが再コンパイルせず、さまざまな Dbms のデータにアクセスできるおよびからデータにもアクセスできるため、最新のオペレーティング システムでは、実行時に、(ダイナミック リンク ライブラリなど、Microsoft® Windows® オペレーティング システムで) このようなライブラリを読み込むことができます、同時には複数のデータベースです。 データベースの新しいドライバーが利用可能になるようユーザーだけインストールできますがコンピューターにこれらの変更、再コンパイル、またはデータベース アプリケーションを再リンクすることがなく。 に、呼び出しレベルのインターフェイスが ODBC で有力候補がさらに、Windows — を ODBC が開発されたプラットフォーム — きたこのようなライブラリを頻繁に使用します。
