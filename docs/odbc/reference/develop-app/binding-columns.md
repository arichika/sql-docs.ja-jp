---
title: 列をバインド |Microsoft ドキュメント
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
- result sets [ODBC], binding columns
- binding columns [ODBC]
ms.assetid: c4407694-c8e1-4b0b-a39d-b007e6c3b54d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b78a87884e075e4cbe3dcb914335994aba2e4159
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="binding-columns"></a>列のバインド
この目的のため、アプリケーションが割り当てられている変数のアプリケーションには、データ ソースからフェッチされたデータが返されます。 これを行うことができます、前に、アプリケーションに関連付ける必要があります、または*バインド*結果の列にこれらの変数の設定。 概念的には、このプロセスは、ステートメントのパラメーターをアプリケーション変数のバインドと同じです。 アプリケーションにバインドする変数と、結果セット列、その変数がについて説明します-アドレスやデータ型: ドライバーにします。 ドライバーでは、そのステートメントを保持し、情報を使用して、行がフェッチしたときに、列から値を返す、構造のこの情報を格納します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットの列のバインド](../../../odbc/reference/develop-app/binding-result-set-columns.md)  
  
-   [SQLBindCol の使用](../../../odbc/reference/develop-app/using-sqlbindcol.md)
