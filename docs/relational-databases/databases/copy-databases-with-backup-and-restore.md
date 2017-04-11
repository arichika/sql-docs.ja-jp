---
title: "バックアップと復元によるデータベースのコピー | Microsoft Docs"
ms.custom: ""
ms.date: "07/15/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フルテキスト検索 [SQL Server], バックアップして復元"
  - "データベースの復元 [SQL Server], 前の SQL Server バージョン"
  - "データベースの復元 [SQL Server], データベースのコピー"
  - "データベースの復元 [SQL Server], 別のサーバー インスタンスへ"
  - "復元 [SQL Server]、別のサーバー インスタンス"
  - "データベースのバックアップ [SQL Server], データベースのコピー"
  - "データベース バックアップ [SQL Server], データベースのコピー"
ms.assetid: b93e9701-72a0-408e-958c-dc196872c040
caps.latest.revision: 61
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 61
---
# バックアップと復元によるデータベースのコピー
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンを使用して作成したユーザー データベースのバックアップを復元して、新しいデータベースを作成できます。 ただし、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を使用して作成された **master**、**model**、および **msdb** のバックアップを [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で復元することはできません。 また、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のバックアップを以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で復元することもできません。  
  
>**重要: ** SQL Server 2016 では、以前のバージョンとは異なる既定パスが使用されます。 そのため、以前のバージョンの既定の場所で作成されたデータベースのバックアップを復元するには、MOVE オプションを使用する必要があります。 新しい既定パスの詳細については、「[SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)」を参照してください。 データベース ファイルの移動の詳細については、このトピックの「データベース ファイルの移動」を参照してください。  
  
## バックアップと復元を使用してデータベースをコピーする一般的な手順  
 バックアップと復元を使用して他の SQL Server インスタンスにデータベースをコピーするとき、SQL Server を実行するコピー元とコピー先のコンピューターのプラットフォームは問いません。  
  
 一般的な手順は次のとおりです。  
  
1.  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のインスタンスにあるコピー元データベースをバックアップします。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを実行しているコンピューターが**コピー元コンピューター**です。  
  
2.  データベースをコピーする先のコンピューター (**コピー先コンピューター**) で、データベースの復元先の SQL Server インスタンスに接続します。 必要に応じて、**コピー元**データベースのバックアップに使用したのと同じバックアップ デバイスを**コピー先**のサーバー インスタンスにも作成します。  
  
3.  **コピー元**データベースのバックアップを**コピー先**コンピューターに復元します。 データベースを復元すると、すべてのデータベース ファイルが自動的に作成されます。  
  
この処理に影響する可能性があるその他の考慮事項:
  
## データベース ファイルを復元する前に  
 データベースを復元すると、復元しているデータベースに必要なデータベース ファイルが自動的に作成されます。 既定では、復元操作時に SQL Server によって作成されるファイルの名前とパスは、コピー元コンピューター上の元のデータベースのバックアップ ファイルと同一です。  
  
 必要に応じて、データベースを復元するときに、復元するデータベースのデバイス マッピング、ファイル名、またはパスを指定できます。 
 
 これは、次のような状況で必要になる場合があります。  
  
-   コピー元のコンピューター上のデータベースで使用されているディレクトリ構造やドライブ マッピングが他のコンピューター上に存在しない。 たとえば、既定でドライブ E に復元されるファイルがバックアップに含まれているのに、コピー先コンピューターにドライブ E が存在しない場合です。  
  
-   コピー先の場所の容量が十分ではない。  
  
-   復元先に存在するデータベースの名前を再利用していて、そのファイルのいずれかがバックアップ セット内のデータベース ファイルと同じ名前である場合は、次のいずれかの結果になります。  
  
    -   既存のデータベース ファイルを上書きできる場合は、上書きされます (別のデータベース名に属しているファイルには影響しません)。  
  
    -   既存のファイルを上書きできない場合は、復元エラーが発生します。  
  
 エラーと好ましくない結果を回避するには、復元操作の前に、[backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md) 履歴テーブルを使用して、復元しようとしているバックアップ内のデータベースとログ ファイルを確認できます。  
  
## データベース ファイルの移動  
 データベース バックアップ内のファイルをコピー先コンピューターに復元できない場合は、復元のときにファイルを新しい場所に移動する必要があります。 例:  
  
-   以前のバージョンの既定の場所に作成されたバックアップからデータベースを復元する場合。  
  
-   容量の制限により、バックアップ内のデータベース ファイルを別のドライブに復元する必要がある場合。 ディスク ドライブの数やサイズ、またはソフトウェア構成が同じであるコンピューターが組織内に存在することはまれなので、このようなことが頻発します。  
  
-   既存のデータベースをテストするため、そのコピーを同じコンピューター上に作成する必要がある場合。 この場合、元のデータベースのデータベース ファイルが既に存在するので、復元操作でデータベースをコピーする場合は異なるファイル名を指定する必要があります。  
  
 詳細については、このトピックの「ファイルとファイル グループを新しい場所に復元するには」を参照してください。  
  
## データベース名の変更  
 データベースをコピー先コンピューターに復元するときにデータベースの名前を変更できます。データベースを先に復元してから名前を手動で変更する必要はありません。 たとえば、データベースがコピーであることを示すため、名前を **Sales** から **SalesCopy** に変更する必要がある場合があります。  
  
 データベースを復元するときに明示的に指定するデータベース名が、新しいデータベース名として自動的に使用されます。 そのデータベース名はまだ存在していないため、新しい名前のデータベースがバックアップ内のファイルを使用して作成されます。  
  
## 復元を使用してデータベースをアップグレードする場合  
 バックアップを以前のバージョンから復元する場合は、バックアップにある各フルテキスト カタログのパス (ドライブとディレクトリ) がコピー先コンピューターに存在するかどうかを事前に知っておくと便利です。 バックアップにある、カタログ ファイルを含めたすべてのファイルの論理名と物理名 (パスとファイル名) を一覧にするには、RESTORE FILELISTONLY FROM *<backup_device>* ステートメントを使用します。 詳細については、「[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)」を参照してください。  
  
 コピー先のコンピューターに同一のパスが存在しない場合、2 つの方法で対処できます。  
  
-   コピー先コンピューターにも同じドライブ/ディレクトリ マッピングを作成します。  
  
-   RESTORE DATABASE ステートメントで WITH MOVE 句を使用して、復元操作中にカタログ ファイルを新しい場所に移動します。 詳細については、「[RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)」を参照してください。  
  
 フルテキスト インデックスをアップグレードするための別のオプションの詳細については、「[フルテキスト検索のアップグレード](../../relational-databases/search/upgrade-full-text-search.md)」を参照してください。  
  
## データベースの所有権  
 データベースを別のコンピューターに復元すると、復元操作を開始した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン ユーザーまたは [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザーが自動的に新しいデータベースの所有者になります。 復元されたデータベースのシステム管理者または新しいデータベース所有者は、そのデータベースの所有権を変更できます。 認められていないデータベースの復元を防止するため、メディアまたはバックアップ セットのパスワードを使用してください。  
  
## 別のサーバー インスタンスに復元するときのメタデータの管理  
 データベースを別のサーバー インスタンスに復元するときは、ユーザーおよびアプリケーションに一貫した使用環境を提供するために、復元先のサーバー インスタンスで、ログインやジョブなどのデータベースのメタデータの一部またはすべてを作成し直す必要がある場合があります。 詳細については、「[データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../../relational-databases/databases/manage metadata when making a database available on another server.md)」を参照してください。  
  
 **バックアップ セットに含まれているデータ ファイルおよびログ ファイルの表示**  
  
-   [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)  
  
 **ファイルとファイル グループを新しい場所に復元する**  
  
-   [新しい場所へのファイルの復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
  
-   [SSMS を使用したデータベース バックアップの復元](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
 **既存のファイルにファイルとファイル グループを復元する**  
  
-   [既存のファイルにファイルとファイル グループを復元する &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-over-existing-files-sql-server.md)  
  
 **新しい名前でデータベースを復元する**  
  
-   [SSMS を使用したデータベース バックアップの復元](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
 **中断された復元操作の再開**  
  
-   [中断された復元操作の再開 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/restart-an-interrupted-restore-operation-transact-sql.md)  
  
 **データベース所有者の変更**  
  
-   [sp_changedbowner &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)  
  
 **SQL Server 管理オブジェクト (SMO) を使用してデータベースをコピーする**  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReadFileList%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.RelocateFiles%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.ReplaceDatabase%2A>  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore>  
  
## 参照  
 [他のサーバーへのデータベースのコピー](../../relational-databases/databases/copy-databases-to-other-servers.md)   
 [SQL Server の既定のインスタンスおよび名前付きインスタンスのファイルの場所](../../sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)   
 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](../Topic/RESTORE%20FILELISTONLY%20\(Transact-SQL\).md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  