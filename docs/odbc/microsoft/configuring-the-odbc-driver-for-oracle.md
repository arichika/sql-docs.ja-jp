---
title: Oracle 用の ODBC ドライバーの構成 |Microsoft ドキュメント
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
- configuring ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], configuring
ms.assetid: 0a5f827c-0b80-4627-85cb-f10292b9fb33
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a98cdab1143e48148aaacba56a0a83b99c5d294
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-the-odbc-driver-for-oracle"></a>Oracle ODBC ドライバーを構成します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 Oracle 用の ODBC ドライバーのパフォーマンスを制御するにはデータ環境を知ることを正しく使用してデータ ソース接続のパラメーターを設定、 [ODBC データ ソース アドミニストレーター](../../odbc/admin/odbc-data-source-administrator.md)  ダイアログ ボックスまたはを介して次のように接続します。文字列パラメーター。 ダイアログ ボックスが、ダイアログ ボックスを使用してデータ ソースに接続するため、次のコントロールを提供またはを使用して接続文字列。  
  
-   **[ユーザー DSN] タブ**コンピューターに対してローカルなデータ ソースの名前を一覧表示します。  
  
-   **システム DSN タブ**を追加またはシステム データ ソースを削除することができます。 システム データ ソースは、ローカル コンピューター上のすべてのユーザーによってアクセスできます。  
  
-   **ファイル DSN タブ**を追加またはローカル コンピューターからファイル データ ソースを削除することができます。 ファイルのデータ ソースは、同じドライバーがインストールされているすべてのユーザーで共有できます。  
  
-   **[ドライバー] タブ**インストールされている ODBC ドライバーの一覧を表示します。  
  
-   **[トレース] タブ**ODBC ドライバー マネージャーが ODBC 関数呼び出しをトレースする方法を指定することができます。 別にインストールされている各 ODBC アプリケーションのトレースを構成することができます。  
  
-   **接続プール タブ**インストールされている各ドライバーの接続オプションを選択することができます。  
  
-   **タブに関する**ODBC コンポーネントのインストール ファイルを一覧表示します。  
  
 使用することができます、データ ソースを追加した後、 **ODBC データ ソース アドミニストレーター**ダイアログ ボックスを使用するデータ ソースへのアクセスを構成します。 データ ソースを選択し、編集、または情報を確認するには、タブのいずれかをクリックします。
