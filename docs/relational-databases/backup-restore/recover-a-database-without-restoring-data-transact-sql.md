---
title: "データを復元しないデータベースの復旧 (Transact-SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "復元 [SQL Server], 復旧のみ"
  - "復旧のみのシナリオ [SQL Server]"
  - "データベースの復元 [SQL Server], 復旧のみ"
  - "復旧 [SQL Server], 復旧のみ"
  - "データベース復旧 [SQL Server]"
  - "データベースの復元 [SQL Server], 復旧のみ"
  - "復旧 [SQL Server], データを復元しない"
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# データを復元しないデータベースの復旧 (Transact-SQL)
  通常、データベースを復旧する前に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのすべてのデータを復元します。 ただし、実際にバックアップを復元しなくても、復元操作でデータベースを復旧することは可能です。たとえば、データベースと一貫性のある読み取り専用ファイルを復旧する場合などです。 これは、*復旧のみの復元*と呼ばれます。 オフライン データが既にデータベースと一貫性があり、データを使用可能にするだけでよい場合、復旧のみの復元を実行することで、データベースの復旧が完了し、データがオンラインになります。  
  
 復旧のみの復元は、データベース全体、1 つまたは複数のファイル、およびファイル グループに対して行うことができます。  
  
## 復旧のみのデータベース復元  
 復旧のみのデータベース復元は、次の場合に役に立ちます。  
  
-   復元シーケンスで前回のバックアップを復元したときはデータベースを復旧しなかったが、現在そのデータベースを復旧してオンラインにする必要がある場合。  
  
-   データベースがスタンバイ モードであり、別のログ バックアップを適用せずにそのデータベースを更新可能にする場合。  
  
 復旧のみのデータベース復元の [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) 構文は次のとおりです。  
  
 RESTORE DATABASE *database_name* WITH RECOVERY  
  
> [!NOTE]  
>  復旧のみの復元にはバックアップは必要ないので、FROM **=** \<*backup_device>* 句は使用しません。  
  
 **例**  
  
 次の例では、データを復元しない復元操作で [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースを復旧します。  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## 復旧のみのファイル復元  
 復旧のみのファイル復元は、次の場合に役に立ちます。  
  
 データベースを段階的に部分復元する場合。 プライマリ ファイル グループの復元が完了した後、復元されていないのに、新しいデータベースの状態と一貫性があるファイルが 1 つ以上ある場合。これはおそらく、しばらくの間読み取り専用であったことが原因です。 このようなファイルに対して必要な作業は、復旧のみです。データをコピーする必要はありません。  
  
 復旧のみの復元操作では、オフラインのファイル グループ内のデータをオンラインにします。データのコピー フェーズ、再実行フェーズ、および元に戻すフェーズはありません。 復元の各フェーズに関する詳細については、「[復元と復旧の概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)」を参照してください。  
  
 復旧のみのファイル復元の [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) 構文は次のとおりです。  
  
 RESTORE DATABASE *database_name* { FILE **=***logical_file_name* | FILEGROUP **=***logical_filegroup_name* }[ **,**...*n* ] WITH RECOVERY  
  
 **例**  
  
 次の例は、`SalesGroup2` データベースのセカンダリ ファイル グループ `Sales` に含まれているファイルの復旧のみのファイル復元を示しています。 プライマリ ファイル グループは段階的な部分復元の最初の手順で既に復元されており、`SalesGroup2` は復元されたプライマリ ファイル グループと一貫性があります。 このファイル グループを復旧してオンラインにするために必要なのは、次に示す 1 つのステートメントだけです。  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## 復旧のみの復元を使用した段階的な部分復元シナリオの完了の例  
 **単純復旧モデル**  
  
-   [例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 **完全復旧モデル**  
  
-   [例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## 参照  
 [Online Restore &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [段階的な部分復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [ファイル復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [ファイル復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  