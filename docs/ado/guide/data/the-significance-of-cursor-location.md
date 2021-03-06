---
title: カーソル位置の有意性 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- server-side cursors [ADO]
- cursors [ADO], client-side
- client-side cursors [ADO]
- cursors [ADO], server-side
ms.assetid: 70ef5b1c-0459-41a1-b796-031f61a29a8a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5699c8c7bc3ab1ed54d9411ff889e43e8cf334d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="the-significance-of-cursor-location"></a>カーソル位置の有意性
すべてのカーソルは、そのデータを保持するために一時的なリソースを使用します。 これらのリソースには、メモリ、ディスク ページング ファイル、一時ディスク ファイル、またはデータベースにも一時ストレージを指定できます。 カーソルと呼びます、*クライアント側*カーソルこれらのリソースがクライアント コンピューター上にある場合。 カーソルと呼びます、*サーバー側*カーソルこれらのリソースがサーバー上にある場合。  
  
## <a name="client-side-cursors"></a>クライアント側カーソル  
 ADO では、呼び出しでクライアント側カーソルを使用して、 **adUseClient CursorLocationEnum です。** キーセット カーソル以外のクライアント側のカーソルでは、サーバーは、結果セット全体をネットワーク経由でクライアント コンピューターを送信します。 クライアント コンピューターは、提供し、カーソルと結果セットに必要な一時的なリソースを管理します。 クライアント側のアプリケーションは、結果セット全体を必要とする行を決定するを参照できます。  
  
 静的およびキーセット ドリブンのクライアント側カーソルが、ワークステーション上の大きな負荷を配置するには、多くの行が含まれる場合。 すべてのカーソル ライブラリは、数千行にカーソルを作成できるが、アプリケーションがこのような大規模な行セットをフェッチするように設計が発揮しません。 もちろん、例外があります。 一部のアプリケーションで大規模なクライアント側のカーソルは完全に切になるし、パフォーマンスが問題にならない可能性があります。  
  
 クライアント側カーソルの 1 つの明確な利点は、迅速な応答です。 結果セットは、クライアント コンピューターにダウンロードされたが後、は、非常に高速では行を参照します。 クライアントごとに異なると、サーバーではなく、カーソルのリソース要件が配置されているために、アプリケーションは通常、クライアント側のカーソルでスケーラブルなです。  
  
## <a name="server-side-cursors"></a>サーバー側カーソル  
 ADO では、呼び出しによってサーバー側カーソルを使用して、 **adUseServer CursorLocationEnum です。** サーバー側カーソルでは、サーバーは、使用して結果セットのサーバー コンピューターによって提供されるリソースを管理します。 サーバー側のカーソルは、ネットワーク経由で要求されたデータのみを返します。 この種類のカーソルでは、過剰なネットワーク トラフィックが、問題の状況では特に、クライアント側カーソルよりも優れたパフォーマンスを提供できる場合があります。  
  
 ただし、これはサーバー側カーソルは、ことを指摘する — 少なくとも一時的に — すべてのアクティブなクライアント貴重なサーバー リソースを消費します。 サーバー ハードウェアがすべてのアクティブなクライアントから要求されたサーバー側カーソルを管理できることを確認するそれに従って計画する必要があります。 また、サーバー側カーソルが遅くなる 1 つの行にしかアクセスを提供するため、使用できる batch カーソルはありません。  
  
 サーバー側のカーソルは挿入、更新、またはレコードを削除する場合に便利です。 サーバー側のカーソルで同じ接続で複数のアクティブ ステートメントを持つことができます。
