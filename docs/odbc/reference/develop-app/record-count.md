---
title: レコード カウント |Microsoft ドキュメント
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
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b4ab002f144070c94a659f0b1d67d09de9ceed50
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="record-count"></a>レコード カウント
記述子の SQL_DESC_COUNT ヘッダー フィールドは、データが含まれる番号が最大レコードの 1 から始まるインデックスです。 このフィールドは、すべての列またはバインドされているパラメーターの数ではありません。 記述子が割り当てられる SQL_DESC_COUNT の初期値は 0 です。  
  
 ドライバーは、割り当てし、記述子の情報を保持するために必要な任意の記憶域の管理に必要な任意のアクションを取得します。 アプリケーションが、明示的に、記述子のサイズを指定したりする新しいレコードを割り当てます。 アプリケーションでは、番号が SQL_DESC_COUNT の値よりも大きい記述子レコードの情報を提供するときに、ドライバーは SQL_DESC_COUNT を自動的に増加します。 アプリケーションには、番号が最大の記述子レコードがバインド解除と、ドライバーで最高の残りのバインドされたレコードの数を格納する SQL_DESC_COUNT が自動的に小さくなります。
