---
title: グローバル設定 (ログ) (MySQLToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 0d033492-5ec3-473a-8de1-821894ec9518
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: ce835c2bab22a755fc2e4ac1693a9f42cc00210c
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776108"
---
# <a name="global-settings-logging--mysqltosql"></a>グローバル設定 (ログ) (MySQLToSQL)
使用して、**グローバル設定**ダイアログ ボックスを SSMA のログ設定を指定します。 通常、製品のサポートを使用する場合にのみこれらの設定を変更するは。  
  
このダイアログ ボックスにアクセスする、**ツール**メニューの **グローバル設定**をクリックし、**ログ**左側のウィンドウの下部にあるボタンをクリックします。  
  
## <a name="options"></a>および  
**メッセージ レベル**  
次のオプションが 利用可能な**メッセージ レベル**:  
  
|オプション|説明|  
|----------|---------------|  
|**[すべてのカテゴリ]**|次のオプションのすべてのログ記録レベルを設定するために使用します。|  
|**コレクター**|送信元スキーマについてのメタデータを収集し、プロジェクトに保存します。|  
|**コンバーター**|対応するテーブルおよびストアド プロシージャなど、ソース データベース オブジェクトの構造体に変換[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]構造体。|  
|**データの移行**|ソース データベースからデータを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|**フォーマッタ**|用のスクリプトを生成するコンバーターのサブコンポーネント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]スキーマです。|  
|**グラフィカル ユーザー インターフェイス**|SSMA ツールを使用するときに表示されるメッセージです。|  
|**リンカー**|SQL 識別子を解決し、その他のコンポーネントに情報を提供します。|  
|**その他**|その他のカテゴリに含まれていないすべてのメッセージ。|  
|**パーサー**|送信元スキーマを解析します。|  
|**シンクロナイザー**|ソースにデータベース オブジェクトの読み込み[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。|  
|**TreeConverter**|ソースのメタデータ内のオブジェクトに変換します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]メタデータ。|  
  
各オプションの下の**メッセージ レベル**SSMA の次のログ記録レベルのいずれかを構成します。  
  
|||  
|-|-|  
|**致命的なエラー**|致命的なエラー メッセージのみをログに書き込みます。|  
|**Error**|エラーと致命的なエラー メッセージをログに書き込みます。|  
|**警告**|警告、エラー、および致命的なエラー メッセージをログに書き込みます。|  
|**情報**|情報、警告、エラー、および致命的なエラー メッセージをログに書き込みます。|  
|**デバッグ**|デバッグのログへのメッセージを含む、すべてのメッセージを記述します。|  
  
**ログ ファイルのパス**  
ファイルのパスと SSMA ログ ファイルの名前。 別の名前を指定する、現在のパス をクリックし、クリックし、参照ボタン (**.**) ボタンをクリックします。  
  
**ログ ファイルのサイズ**  
サポート技術情報のログ ファイルの最大サイズ。 最小サイズは、10 KB です。 既定のサイズは 10240 KB です。  
  
**ログ ファイルの合計数**  
1 つのログがいっぱいになる、SSMA は、ログ ファイルの名前を変更し、新しいを開始します。 この設定を使用すると、保持するログ ファイルの最大数を指定します。 最小値は 2 です。  
  
