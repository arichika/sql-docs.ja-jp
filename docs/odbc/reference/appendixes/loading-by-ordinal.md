---
title: 序数で読み込み |Microsoft ドキュメント
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
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e37cd9754b402960ca12b0dbdbeaf43a5f2aee61
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="loading-by-ordinal"></a>序数で読み込む
ODBC 2 です。*x*、接続処理のパフォーマンスを向上させるために序数で読み込みを実行する可能性があります。 ODBC 2 です。*x*ドライバーは、序数に基づく 199 でダミー関数をエクスポート以外の場合は、名前ではなく序数で ODBC 関数のアドレスを解決が、ドライバー マネージャーがそれを検出します。 ODBC 2 では、この機能はサポートされても。*x*ドライバーは ODBC 3 のサポートされていませんが、*.x*ドライバー。
