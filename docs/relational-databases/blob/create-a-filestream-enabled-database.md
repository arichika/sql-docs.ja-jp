---
title: "FILESTREAM が有効なデータベースを作成する方法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FILESTREAM [SQL Server]、FILESTREAM が有効なデータベース"
ms.assetid: 0fc16356-76f7-44b8-a58b-f0b7c43694ec
caps.latest.revision: 16
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 16
---
# FILESTREAM が有効なデータベースを作成する方法
  このトピックでは、FILESTREAM をサポートするデータベースを作成する方法について説明します。 FILESTREAM は特殊なファイル グループを使用するので、データベースの作成時に少なくとも 1 つのファイル グループに対して CONTAINS FILESTREAM 句を指定する必要があります。  
  
 FILESTREAM ファイル グループに、2 つ以上のファイルを含められます。 複数のファイルを含む FILESTREAM ファイル グループの作成方法を示すコード例については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
  
### FILESTREAM が有効なデータベースを作成するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[新しいクエリ]** をクリックしてクエリ エディターを表示します。  
  
2.  次の例からクエリ エディターに [!INCLUDE[tsql](../../includes/tsql-md.md)] コードをコピーします。 この [!INCLUDE[tsql](../../includes/tsql-md.md)] コードによって、アーカイブと呼ばれる FILESTREAM が有効なデータベースが作成されます。  
  
    > [!NOTE]  
    >  このスクリプトでは、ディレクトリ C:\Data が存在している必要があります。  
  
3.  データベースを構築するには、 **[実行]**をクリックします。  
  
## 例  
 次のコード例では、`Archive` という名前のデータベースを作成します。 このデータベースは、 `PRIMARY`、 `Arch1`、 `FileStreamGroup1`という 3 つのファイル グループを含んでいます。 `PRIMARY` と `Arch1` は、FILESTREAM データを含むことのできない通常のファイル グループです。 `FileStreamGroup1` は、 `FILESTREAM` ファイル グループです。  
  
 [!code-sql[FILESTREAM#FS_CreateDB](../../relational-databases/blob/codesnippet/tsql/create-a-filestream-enab_1.sql)]  
  
 `FILESTREAM` ファイル グループに対しては、 `FILENAME` がパスを参照します。 最後のフォルダーまでのパスが存在する必要がありますが、最後のフォルダーは存在できません。 この例では、 `c:\data` が存在する必要があります。 ただし、`filestream1` ステートメントを実行するときに `CREATE DATABASE` サブフォルダーが存在してはいけません。 構文の詳細については、「[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)」を参照してください。  
  
 上の例を実行すると、c:\Data\filestream1 フォルダーに filestream.hdr ファイルと $FSLOG フォルダーが作成されます。 filestream.hdr ファイルは、FILESTREAM コンテナーのヘッダー ファイルです。  
  
> [!IMPORTANT]  
>  filestream.hdr ファイルは、重要なシステム ファイルです。 このファイルには、FILESTREAM ヘッダー情報が含まれています。 このファイルを削除したり変更したりしないでください。  
  
 既存のデータベースに対しては、 [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) ステートメントを使用して FILESTREAM ファイル グループを追加できます。  
  
## 参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
  