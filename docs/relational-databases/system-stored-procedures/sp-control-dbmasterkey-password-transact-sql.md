---
title: sp_control_dbmasterkey_password (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_control_dbmasterkey_password
- sp_control_dbmasterkey_password_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_control_dbmasterkey_password
ms.assetid: 63979a87-42a2-446e-8e43-30481faaf3ca
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: a9894a10965affbd65406276445f6c84f05ce76e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spcontroldbmasterkeypassword-transact-sql"></a>sp_control_dbmasterkey_password (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースのマスター キーを開くときに必要とされるパスワードを含む資格情報を追加または削除します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_control_dbmasterkey_password @db_name = 'database_name,  
     @password = 'master_key_password' , @action = { 'add' | 'drop' }  
```  
  
## <a name="arguments"></a>引数  
 @db_name=N'*database_name*'  
 資格情報に関連付けられているデータベースの名前を指定します。 システム データベースは指定できません。 *database_name*は**nvarchar**です。  
  
 @password= N'*パスワード*'  
 マスター キーのパスワードを指定します。 *パスワード*は**nvarchar**です。  
  
 @action= N'add'  
 指定したデータベースの資格情報を、資格情報ストアに追加します。 資格情報には、データベースのマスター キーのパスワードが格納されます。 渡された値@actionは**nvarchar**です。  
  
 @action=N'drop'  
 指定したデータベースの資格情報を、資格情報ストアから削除します。 渡された値@actionは**nvarchar**です。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、キーの暗号化解除や暗号化にデータベースのマスター キーが必要となる場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではインスタンスのサービス マスター キーを使用して、データベースのマスター キーの暗号化解除が試行されます。 復号化が失敗した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資格情報ストアをマスター _ キーを必要なデータベースと同じファミリ GUID のあるマスター _ キー資格情報を検索します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、次に、一致した資格情報を順に使用してデータベースのマスター キーの暗号化解除が試行されます。これは暗号化解除が成功するか、資格情報がなくなった時点で終了します。  
  
> [!CAUTION]  
>  sa やその他の高位の権限を持つサーバー プリンシパルに対してデータベースへのアクセスを禁止する場合は、データベースのマスター キー資格情報を作成しないでください。 データベースのキー階層をサービス マスター キーで暗号化解除できないようにデータベースを構成できます。 この機能は、sa または高位の権限を持つサーバー プリンシパルに対して、データベースに含まれる暗号化情報へのアクセスを禁止するための、多重の防御としてサポートされているものです。 このようなデータベースに対してマスター キー資格情報を作成すると、この多重の防御が無効になり、sa およびその他の高位の権限を持つサーバー プリンシパルがデータベースの暗号化を解除できるようになります。  
  
 Sp_control_dbmasterkey_password を使用して作成した資格情報では表示、 [sys.master_key_passwords](../../relational-databases/system-catalog-views/sys-master-key-passwords-transact-sql.md)カタログ ビューです。 次の形式であるデータベース マスター _ キー用に作成する資格情報の名前:`##DBMKEY_<database_family_guid>_<random_password_guid>##`です。 パスワードは、資格情報シークレットとして格納されています。 sys.credentials には、資格情報ストアに追加されたパスワードごとに 1 行のデータが格納されます。  
  
 sp_control_dbmasterkey_password を使用して、システム データベース master、model、msdb、または tempdb の資格情報を作成することはできません。  
  
 sp_control_dbmasterkey_password では、指定したデータベースのマスター キーをパスワードで開くことができるかどうかは検証されません。  
  
 指定したデータベースの資格情報に既に格納されているパスワードを指定した場合、sp_control_dbmasterkey_password は失敗します。  
  
> [!NOTE]  
>  異なるサーバー インスタンスの 2 つのデータベースで、同じファミリ GUID を共有することができます。 この場合、両方のデータベースの資格情報ストア内で同じマスター キー レコードが共有されます。  
  
 sp_control_dbmasterkey_password に渡されるパラメーターは、トレースには表示されません。  
  
> [!NOTE]  
>  sp_control_dbmasterkey_password を使用して追加された資格情報を使ってデータベース マスター キーを開く場合、そのデータベース マスター キーはサービス マスター キーによって再暗号化されます。 データベースが読み取り専用モードの場合、再暗号化操作は失敗し、データベース マスター キーは暗号化されません。 それ以降、データベース マスター キーにアクセスする場合は、OPEN MASTER KEY ステートメントおよびパスワードを使用する必要があります。 パスワードの使用を避けるには、データベースを読み取り専用モードに移行する前に、資格情報を作成するようにしてください。  
  
 **下位互換性問題の潜在的な:** 現時点では、ストアド プロシージャは確認されないかどうか、マスター _ キー。 これは下位互換性を確保するために許容されていますが、警告が表示されます。 ただし、この動作は廃止予定となっています。 マスター _ キーが存在する必要があります、将来のリリースと、ストアド プロシージャで使用されるパスワードで**sp_control_dbmasterkey_password**データベース マスター _ キーの暗号化に使用されるパスワードのいずれかと同じパスワードをする必要があります。  
  
## <a name="permissions"></a>権限  
 データベースに対する CONTROL 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-credential-for-the-adventureworks2012-master-key"></a>A. AdventureWorks2012 マスター キーの資格情報を作成する  
 次の例では、`AdventureWorks2012` データベースのマスター キーの資格情報を作成し、マスター キーのパスワードをシークレットとして資格情報に保存します。 に渡されるすべてのパラメーター`sp_control_dbmasterkey_password`データ型でなければなりません**nvarchar**、テキスト文字列は、キャスト演算子変換`N`です。  
  
```  
EXEC sp_control_dbmasterkey_password @db_name = N'AdventureWorks2012',   
    @password = N'sdfjlkj#mM00sdfdsf98093258jJlfdk4', @action = N'add';  
GO  
```  
  
### <a name="b-dropping-a-credential-for-a-database-master-key"></a>B. データベースのマスター キーの資格情報を削除する  
 次の例では、例 A で作成した資格情報を削除します。ここではパスワードを含め、すべてのパラメーターが必須です。  
  
```  
EXEC sp_control_dbmasterkey_password @db_name = N'AdventureWorks2012',   
    @password = N'sdfjlkj#mM00sdfdsf98093258jJlfdk4', @action = N'drop';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [暗号化されたミラー データベースの設定](../../database-engine/database-mirroring/set-up-an-encrypted-mirror-database.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [資格情報 &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)  
  
  
