---
title: "例 : 読み取り専用ファイルのオンライン復元 (単純復旧モデル) | Microsoft Docs"
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
  - "復元シーケンス [SQL Server], オンライン"
  - "オンライン復元 [SQL Server], 単純復旧モデル"
  - "単純復旧モデル [SQL Server], 復元の例"
ms.assetid: 0c691fc6-9865-46a7-b055-8097424492d6
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# 例 : 読み取り専用ファイルのオンライン復元 (単純復旧モデル)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックは、読み取り専用のファイル グループを含む、単純復旧モデルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに関連しています。 単純復旧モデルでは、ファイルが最後に読み取り専用になってから作成されたファイル バックアップが存在する場合、読み取り専用ファイルをオンラインに復元できます。  
  
 この例では、`adb` というデータベースに 3 つのファイル グループが含まれているとします。 ファイル グループ `A` は読み取り/書き込みが可能で、ファイル グループ `B` とファイル グループ `C` は読み取り専用です。 最初は、すべてのファイル グループがオンラインです。 ファイル グループ `B` の読み取り専用ファイル `b1` を復元する必要があります。 データベース管理者は、ファイルが読み取り専用になった後で作成されたバックアップを使用して、このファイルを復元できます。 復元の間、ファイル グループ `B` はオフラインになりますが、データベースの残りのファイル グループはオンライン状態で維持されます。  
  
## 復元シーケンス  
  
> [!NOTE]  
>  オンライン復元シーケンスでは、オフライン復元シーケンスと同じ構文を使用します。  
  
 ファイルを復元するには、データベース管理者が次の復元シーケンスを使用する必要があります。  
  
```  
RESTORE DATABASE adb FILE='b1' FROM filegroup_B_backup   
WITH RECOVERY  
```  
  
 ファイルがオンラインになります。  
  
## その他の例  
  
-   [例: データベースの段階的な部分復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [例: データベースの段階的な部分復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [例: 一部のファイル グループのみを復元する段階的な部分復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [例: 読み取り/書き込みファイルのオンライン復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-write-file-full-recovery-model.md)  
  
-   [例 : 読み取り専用ファイルのオンライン復元 &#40;完全復旧モデル&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## 参照  
 [Online Restore &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [段階的な部分復元 &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [ファイル復元 &#40;単純復旧モデル&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [復元と復旧の概要 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  