---
title: 記述子およびデスクトップ データベース ドライバー |Microsoft ドキュメント
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
- desktop database drivers [ODBC], descriptors
- Jet-based ODBC drivers [ODBC], descriptors
- descriptors [ODBC], Jet-supported descriptor fields
- ODBC desktop database drivers [ODBC], descriptors
ms.assetid: 9ae2d9b5-365f-4f0a-9116-defe9498b401
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62d827aecfb8b8fdf593291ce179f5c93d638dc1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="descriptors-and-desktop-database-drivers"></a>記述子およびデスクトップ データベース ドライバー
記述子は、列のデータまたは動的パラメーターのいずれかに関する情報を保持するデータ構造です。 **Sqlgetdescfield による**以下に示すサポートされる記述子を取得するために使用できます。 実装パラメーター記述子 (IPD) が自動的に作成されないため**SQLDescribeParam**はサポートされていません。 Jet (SQL_DESC_BASE_TABLE_NAME) などで使用できない記述子フィールドもサポートされません。  
  
 記述子の Jet でサポートされているフィールドの詳細については、次を参照してください。、 *Microsoft Jet データベース エンジン プログラマ ガイド*です。  
  
 記述子の詳細については、「記述子」の下にあるトピックを参照してください、 *ODBC プログラマ リファレンス*です。  
  
|記述子フィールド|サポート レベル|  
|-----------------------|-------------------|  
|SQL_DESC_ALLOC_TYPE|Supported|  
|SQL_DESC_ARRAY_SIZE|ARD でのみサポート|  
|SQL_DESC_ARRAY_STATUS_PTR|Supported|  
|SQL_DESC_BIND_OFFSET_PTR|Supported|  
|SQL_DESC_BIND_TYPE|Supported|  
|SQL_DESC_COUNT|Supported|  
|SQL_DESC_ROWS_PROCESSED_PTR|ARD でのみサポート|  
|SQL_DESC_AUTO_UNIQUE_VALUE|Supported|  
|SQL_DESC_BASE_COLUMN_NAME|サポート (新規)|  
|SQL_DESC_BASE_TABLE_NAME|サポート (新規)|  
|SQL_DESC_CASE_SENSITIVE|常に FALSE|  
|SQL_DESC_CATALOG_NAME|サポートされていません|  
|SQL_DESC_CONCISE_TYPE|Supported|  
|SQL_DESC_DATA_PTR|Supported|  
|SQL_DESC_DATETIME_INTERVAL_CODE|Supported|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|間隔の C 型のサポート|  
|SQL_DESC_DISPLAY_SIZE|Supported|  
|SQL_DESC_FIXED_PREC_SCALE|サポートされている (TRUE money の)|  
|SQL_DESC_INDICATOR_PTR|Supported|  
|SQL_DESC_LABEL|Supported|  
|SQL_DESC_LENGTH|Supported|  
|SQL_DESC_LITERAL_PREFIX|Supported|  
|SQL_DESC_LITERAL_SUFFIX|Supported|  
|SQL_DESC_LOCAL_TYPE_NAME|(空の文字列を返します) はサポートされていません|  
|SQL_DESC_NAME|Supported|  
|SQL_DESC_NULLABLE|Supported<br /><br /> **注**Jet 4.0 の前のバージョンでサポートされていません。|  
|SQL_DESC_NUM_PREC_RADIX|Supported|  
|SQL_DESC_OCTET_LENGTH|Supported|  
|SQL_DESC_OCTET_LENGTH_PTR|Supported|  
|SQL_DESC_PARAMETER_TYPE|入力パラメーターのみ|  
|SQL_DESC_PRECISION|Supported|  
|SQL_DESC_SCALE|Supported|  
|SQL_DESC_SCHEMA_NAME|サポートされていません|  
|SQL_DESC_SEARCHABLE|Supported|  
|SQL_DESC_TABLE_NAME|サポートされていません|  
|SQL_DESC_TYPE|Supported|  
|SQL_DESC_TYPE_NAME|Supported|  
|SQL_DESC_UNNAMED|Supported|  
|SQL_DESC_UNSIGNED|Supported|  
|SQL_DESC_UPDATABLE|Supported|
