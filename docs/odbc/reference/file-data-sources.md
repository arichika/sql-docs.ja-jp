---
title: ファイル データ ソース |Microsoft ドキュメント
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
- data sources [ODBC], file
- file data sources [ODBC]
ms.assetid: db245c80-981a-4638-bd03-69d04bc67af0
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25be6ea116b5449de55aeb8a16ed1cf12e1ce418
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="file-data-sources"></a>[ファイル データ ソース]
*ファイル データ ソース*ファイルに格納され、1 人のユーザーによって繰り返し使用または複数のユーザー間で共有する接続情報を許可します。 ファイル データ ソースを使用する場合、ドライバー マネージャーは、.dsn ファイルに情報を使用してデータ ソースへの接続はします。 このファイルは、その他のファイルと同様に操作できます。 ファイル データ ソースには、データ ソース名はありませんが、コンピューターのデータ ソースと任意の 1 つのユーザーまたはコンピューターに登録されていません。  
  
 .Dsn ファイルには、呼び出しを構築する必要のある接続文字列が含まれているために、ファイル データ ソースが、接続プロセスを利用すれば、 **SQLDriverConnect**関数。 .Dsn ファイルのもう 1 つの利点をコピーできます任意のコンピューターにインストールされている適切なドライバーがある限り、同一のデータ ソースは多数のコンピューターで使用できるようにします。 ファイル データ ソースは、アプリケーションで共有できます。 共有可能なデータ ソースをネットワーク上に配置し、複数のアプリケーションで同時に使用します。  
  
 .Dsn ファイルが共有可能なことができますもあります。 共有不能な .dsn ファイルは、1 台のコンピューター上に存在し、コンピューターのデータ ソースを指します。 共有不能なファイルのデータ ソースは、ファイル データ ソースと共にのみ使用するアプリケーションを設計できるようにコンピューターのデータ ソースのファイル データ ソースへの簡単な変換を許可するには、主に存在します。 ドライバー マネージャーは、データ ソースに共有不能なファイル情報を送信するとき、必要に応じて、.dsn ファイルを指すコンピューターのデータ ソースへ接続します。  
  
 ファイルのデータ ソースの詳細については、次を参照してください。[を使用してファイル データ ソースの接続](../../odbc/reference/develop-app/connecting-using-file-data-sources.md)、または[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)関数の説明。
