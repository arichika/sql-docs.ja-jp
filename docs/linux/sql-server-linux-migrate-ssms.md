---
title: エクスポートし、Linux 上のデータベースのインポート |Microsoft ドキュメント
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.technology: linux
ms.assetid: 2210cfc3-c23a-4025-a551-625890d6845f
ms.custom: sql-linux
ms.openlocfilehash: 7a7c1c73ca70e0d42104e74c868d6acd32cc01b1
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="export-and-import-a-database-on-linux-with-ssms-or-sqlpackageexe-on-windows"></a>エクスポートし、SSMS または SqlPackage.exe Windows 上の Linux 上のデータベースのインポート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事は、使用する方法を示します[SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)と[SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx)をエクスポートし、Linux 上の SQL Server 2017 上のデータベースをインポートします。 SSMS と SqlPackage.exe は Windows アプリケーション、Linux 上のリモート SQL Server インスタンスに接続できる Windows マシンがあるときにそのためこの手法を使用します。

常にインストールし、」の説明に従って、最新バージョンの SQL Server Management Studio (SSMS) を使用する必要があります[Linux に SQL Server への接続に Windows での SSMS の使用](sql-server-linux-manage-ssms.md)

> [!NOTE]
> 使用する、推奨事項は、別に、1 つの SQL Server インスタンスからデータベースを移行する場合[バックアップと復元](sql-server-linux-migrate-restore-database.md)です。

## <a name="export-a-database-with-ssms"></a>SSMS でデータベースをエクスポートします。

1. 入力して、SSMS を起動**Microsoft SQL Server Management Studio** Windows の検索ボックスで、およびデスクトップ アプリをクリックします。

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. オブジェクト エクスプ ローラーで、ソース データベースに接続します。 ソース データベースは、オンプレミスで実行して Microsoft SQL server または Linux、Windows または Docker と Azure SQL Database または Azure SQL Data Warehouse で、クラウド内に指定できます。

3. オブジェクト エクスプ ローラーで、ソース データベースを右クリックし、順にポイント**タスク**、 をクリック**データ層アプリケーションのエクスポートしています.**

4. エクスポート ウィザード をクリックして**次**、し、**設定** タブでいずれかのローカル ディスクの場所、または Azure blob には、BACPAC ファイルを保存するエクスポートを構成します。

5. 既定では、データベース内のすべてのオブジェクトがエクスポートされます。 クリックして、**詳細設定 タブ**エクスポートするデータベース オブジェクトを選択します。

6. **[次へ]** をクリックし、 **[完了]** をクリックします。

* です。BACPAC ファイルが選択した場所に正常に作成し、ターゲット データベースにインポートする準備ができたらです。

## <a name="import-a-database-with-ssms"></a>SSMS でデータベースをインポートします。

1. 入力して、SSMS を起動**Microsoft SQL Server Management Studio** Windows の検索ボックスで、およびデスクトップ アプリをクリックします。

    ![SQL Server Management Studio](./media/sql-server-linux-manage-ssms/ssms.png) 

2. オブジェクト エクスプ ローラーで、対象サーバーに接続します。 対象サーバーがオンプレミスで実行して Microsoft SQL Server をあるまたはクラウドでは、Linux、Windows または Docker と Azure SQL Database または Azure SQL Data Warehouse にします。

3. 右クリックし、**データベース**をクリックして、オブジェクト エクスプ ローラーでフォルダー**データ層アプリケーションのインポートしています.**

4. ターゲット サーバーでデータベースを作成するには、ローカル ディスクから BACPAC ファイルを指定または Azure ストレージ アカウントと、BACPAC ファイルをアップロードしたコンテナーを選択します。

5. データベースの新しいデータベース名を提供します。 Azure SQL データベースでデータベースをインポートする場合は、エディションの Microsoft Azure SQL Database (サービス層)、データベースの最大サイズ、およびサービス目標 (パフォーマンス レベル) を設定します。

6. をクリックして**次へ**  をクリックし、**完了**対象サーバーで新しいデータベースに BACPAC ファイルをインポートします。

* です。指定した対象サーバーで新しいデータベースを作成する BACPAC ファイルをインポートするとします。

## <a id="sqlpackage"></a> SqlPackage コマンド ライン オプション

SQL Server Data Tools (SSDT) のコマンド ライン ツールを使用することも[SqlPackage.exe](https://msdn.microsoft.com/library/hh550080.aspx)をエクスポートし、BACPAC ファイルをインポートします。

次のコマンド例では、BACPAC ファイルをエクスポートします。

```bash
SqlPackage.exe /a:Export /ssn:tcp:<your_server> /sdn:<your_database> /su:<username> /sp:<password> /tf:<path_to_bacpac>
```

データベース スキーマとユーザー データをインポートする次のコマンドを使用して、します。BACPAC ファイル:

```bash
SqlPackage.exe /a:Import /tsn:tcp:<your_server> /tdn:<your_database> /tu:<username> /tp:<password> /sf:<path_to_bacpac>

```

## <a name="see-also"></a>参照
SSMS を使用する方法の詳細については、次を参照してください。 [SQL Server Management Studio を使用して](https://msdn.microsoft.com/library/ms174173.aspx)です。 SqlPackage.exe の詳細については、次を参照してください。、 [SqlPackage リファレンス ドキュメント](https://msdn.microsoft.com/library/hh550080.aspx)です。
