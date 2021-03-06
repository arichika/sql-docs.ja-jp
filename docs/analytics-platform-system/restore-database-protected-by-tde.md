---
title: TDE の Parallel Data Warehouse で保護されたデータベースを復元 |Microsoft ドキュメント
description: 分析プラットフォーム システム Parallel Data Warehouse での transparent data encryption を使用して暗号化されたデータベースを復元するのにには、次の手順を使用します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: a791d4110dc70c506025f8f11fb06b9ba2e5dcb3
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="restore-a-database-protected-by-tde-in-parallel-data-warehouse"></a>Parallel Data Warehouse での TDE で保護されたデータベースを復元します。
透過的なデータ暗号化を使用して暗号化されたデータベースを復元するのにには、次の手順を使用します。  
  
[Transparent Data Encryption を使用して](transparent-data-encryption.md#using-tde)例は、コードで TDE を有効にする、`AdventureWorksPDW2012`データベース。 次のコードは、元の Analytics Platform System (APS) アプライアンスに、データベースのバックアップを作成し、証明書と異なるアプライアンス上のデータベースの復元によってこの例を続行します。  
  
最初の手順では、ソース データベースのバックアップを作成します。  
  
```sql  
BACKUP DATABASE AdventureWorksPDW2012   
TO DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
TDE をマスター _ キーを作成し、暗号化を有効にすると、ネットワーク資格情報の作成、新しい SQL Server PDW を準備します。  
  
```sql  
USE master;  
GO  
  
-- Create a database master key in the master database  
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<UseStrongPasswordHere>';  
GO  
  
-- Enable encryption for PDW  
EXEC sp_pdw_database_encryption 1;  
GO  
  
EXEC sp_pdw_add_network_credentials 'SECURE_SERVER', '<domain>\<Windows_user>', '<password>';  
```  
  
最後の 2 つの手順では、元の SQL Server PDW からバックアップを使用して、証明書を再作成します。 証明書のバックアップを作成したときに使用したパスワードを使用します。  
  
```sql  
-- Create certificate in master  
CREATE CERTIFICATE MyServerCert  
    FROM FILE = '\\SECURE_SERVER\cert\MyServerCert.cer'   
    WITH PRIVATE KEY (FILE = '\\SECURE_SERVER\cert\MyServerCert.key',   
    DECRYPTION BY PASSWORD = '<password>');  
  
RESTORE DATABASE AdventureWorksPDW2012   
    FROM DISK = '\\SECURE_SERVER\Backups\AdventureWorksPDW2012';  
```  
  
## <a name="see-also"></a>参照  
[データベースのバックアップ](../t-sql/statements/backup-database-parallel-data-warehouse.md)  
[CREATE MASTER KEY](../t-sql/statements/create-master-key-transact-sql.md) 
[sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
[sp_pdw_database_encryption](../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
[証明書を作成します。](../t-sql/statements/create-certificate-transact-sql.md)  
[データベースを復元します。](../t-sql/statements/restore-database-parallel-data-warehouse.md)
  
