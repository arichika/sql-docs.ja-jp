---
title: SQLDriverConnect (Excel ドライバー) |Microsoft ドキュメント
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
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7e729292c826383b5dbb90a52aa05a6b92d1f92
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバーに固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 **SQLDriverConnect**データ ソース (DSN) を作成せずに、ドライバーに接続することができます。  
  
 すべてのドライバーの接続文字列で、次のキーワードはサポートされて: **DSN**、 **DBQ**、および**FIL**です。  
  
 次の表は、各ドライバーへの接続に必要な最小のキーワードを示しています、併用キーワード/値ペアの例を示します**SQLDriverConnect**です。 DRIVERID 値の一覧については、次を参照してください。 [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)です。  
  
> [!NOTE]  
>  DBQ または DefaultDir が指定されていない場合、Microsoft Excel 3.0 または 4.0 ドライバー、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|3.0 または 4.0、Microsoft Excel|ドライバー、DriverID|ドライバー {Excel ドライバー (*.xls)} を = です。DBQ = c:\temp です。DriverID 278 を =|  
|Microsoft Excel 5.0/7.0|ドライバー、DriverID、DBQ|ドライバー {Excel ドライバー (*.xls)} を = です。DBQ=c:\temp\sample.xls です。DriverID 22 を =|  
|Microsoft Excel 97 以降|ドライバー、DriverID、DBQ|ドライバー {Excel ドライバー (*.xls)} を = です。DBQ=c:\temp\sample.xls です。DriverID 790 を =|
