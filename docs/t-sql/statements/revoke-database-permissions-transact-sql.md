---
title: "取り消すデータベース権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], databases
- database permissions [SQL Server], revoking
- REVOKE statement, databases
ms.assetid: 442acfc6-af97-40a3-b546-91cd485ee2be
caps.latest.revision: 42
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa0e2b41ff61d3ff8ab7069e4d94e7399053bf43
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-database-permissions-transact-sql"></a>REVOKE (データベースの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースに対して許可および拒否された権限を取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE [ GRANT OPTION FOR ] <permission> [ ,...n ]    
    { TO | FROM } <database_principal> [ ,...n ]   
        [ CASCADE ]  
    [ AS <database_principal> ]  
  
<permission> ::=    
permission | ALL [ PRIVILEGES ]  
  
<database_principal> ::=   
      Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login    
```  
  
## <a name="arguments"></a>引数  
 *アクセス許可*  
 データベースで取り消すことができる権限を指定します。 権限の一覧については、後の「解説」を参照してください。  
  
 ALL  
 このオプションでは、可能な権限がすべて取り消されるわけではありません。 ALL を指定した場合は、BACKUP DATABASE、BACKUP LOG、CREATE DATABASE、CREATE DEFAULT、CREATE FUNCTION、CREATE PROCEDURE、CREATE RULE、CREATE TABLE、および CREATE VIEW 権限を取り消すことになります。  
  
 PRIVILEGES  
 ISO 準拠のために用意されています。 ALL の動作は変更されません。  
  
 GRANT OPTION  
 指定した権限を他のプリンシパルに許可するための権利が、取り消されます。 その権限自体は失効しません。  
  
> [!IMPORTANT]  
>  指定した権限が GRANT オプションなしでプリンシパルに許可されている場合は、その権限自体が取り消されます。  
  
 CASCADE  
 このプリンシパルによって権限が許可または拒否されている他のプリンシパルからも、同じ権限が取り消されることを示します。  
  
> [!CAUTION]  
>  WITH GRANT OPTION で許可されている権限を CASCADE で取り消すと、その権限の GRANT および DENY の両方が取り消されます。  
  
 AS \<database_principal > このクエリを実行するプリンシパルの権限を取り消す権利の派生元のプリンシパルを指定します。  
  
 *Database_user*  
 データベース ユーザーを指定します。  
  
 *Database_role*  
 データベース ロールを指定します。  
  
 *Application_role*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
 アプリケーション ロールを指定します。  
  
 *Database_user_mapped_to_Windows_User*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Windows ユーザーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_Windows_Group*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Windows グループにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_certificate*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 証明書にマップされているデータベース ユーザーを指定します。  
  
 *Database_user_mapped_to_asymmetric_key*  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 非対称キーにマップされているデータベース ユーザーを指定します。  
  
 *Database_user_with_no_login*  
 対応するサーバー レベルのプリンシパルがないデータベース ユーザーを指定します。  
  
## <a name="remarks"></a>解説  
 権限が許可された GRANT オプションを指定するプリンシパルに権限を取り消すときに CASCADE を指定しないと、ステートメントは失敗します。  
  
 データベースは、セキュリティ保護可能なリソースで、権限の階層で親となっているサーバーに含まれています。 次の表に、データベースで取り消すことができる権限のうち最も限定的なものを、それらを暗黙的に含む一般的な権限と共に示します。  
  
|データベース権限|権限が含まれるデータベース権限|権限が含まれるサーバー権限|  
|-------------------------|------------------------------------|----------------------------------|  
|ADMINISTER DATABASE BULK OPERATIONS<br/>**適用対象:** [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]」を参照してください。|CONTROL|CONTROL SERVER|
|ALTER|CONTROL|ALTER ANY DATABASE|  
|ALTER ANY APPLICATION ROLE|ALTER|CONTROL SERVER|  
|ALTER ANY ASSEMBLY|ALTER|CONTROL SERVER|  
|ALTER ANY ASYMMETRIC KEY|ALTER|CONTROL SERVER|  
|ALTER ANY CERTIFICATE|ALTER|CONTROL SERVER|  
|任意の列の暗号化キーを変更します。|ALTER|CONTROL SERVER|  
|すべての列のマスター_キーの定義を変更します。|ALTER|CONTROL SERVER|  
|ALTER ANY CONTRACT|ALTER|CONTROL SERVER|  
|ALTER ANY DATABASE AUDIT|ALTER|ALTER ANY SERVER AUDIT|  
|ALTER ANY DATABASE DDL TRIGGER|ALTER|CONTROL SERVER|  
|ALTER ANY DATABASE EVENT NOTIFICATION|ALTER|ALTER ANY EVENT NOTIFICATION|  
|ALTER ANY DATABASE EVENT SESSION<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|ALTER|ALTER ANY EVENT SESSION|  
|ALTER ANY DATABASE SCOPED CONFIGURATION<br /> **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。|CONTROL|CONTROL SERVER|  
|ALTER ANY DATASPACE|ALTER|CONTROL SERVER|  
|すべての外部データ ソースを変更します。|ALTER|CONTROL SERVER|  
|任意の外部のファイル形式を変更します。|ALTER|CONTROL SERVER|  
|任意の外部ライブラリを変更します。 <br /> **適用対象**: [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)]|CONTROL|CONTROL SERVER |    
|ALTER ANY FULLTEXT CATALOG|ALTER|CONTROL SERVER|
|任意のマスクを変更します。|CONTROL|CONTROL SERVER|  
|ALTER ANY MESSAGE TYPE|ALTER|CONTROL SERVER|  
|ALTER ANY REMOTE SERVICE BINDING|ALTER|CONTROL SERVER|  
|ALTER ANY ROLE|ALTER|CONTROL SERVER|  
|ALTER ANY ROUTE|ALTER|CONTROL SERVER|  
|ALTER ANY SCHEMA|ALTER|CONTROL SERVER|  
|すべてのセキュリティ ポリシーを変更します。<br />**適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|CONTROL|CONTROL SERVER|  
|ALTER ANY SERVICE|ALTER|CONTROL SERVER|  
|ALTER ANY SYMMETRIC KEY|ALTER|CONTROL SERVER|  
|ALTER ANY USER|ALTER|CONTROL SERVER|  
|AUTHENTICATE|CONTROL|AUTHENTICATE SERVER|  
|BACKUP DATABASE|CONTROL|CONTROL SERVER|  
|BACKUP LOG|CONTROL|CONTROL SERVER|  
|CHECKPOINT|CONTROL|CONTROL SERVER|  
|CONNECT|CONNECT REPLICATION|CONTROL SERVER|  
|CONNECT REPLICATION|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|CREATE AGGREGATE|ALTER|CONTROL SERVER|  
|CREATE ASSEMBLY|ALTER ANY ASSEMBLY|CONTROL SERVER|  
|CREATE ASYMMETRIC KEY|ALTER ANY ASYMMETRIC KEY|CONTROL SERVER|  
|CREATE CERTIFICATE|ALTER ANY CERTIFICATE|CONTROL SERVER|  
|CREATE CONTRACT|ALTER ANY CONTRACT|CONTROL SERVER|  
|CREATE DATABASE|CONTROL|CREATE ANY DATABASE|  
|CREATE DATABASE DDL EVENT NOTIFICATION|ALTER ANY DATABASE EVENT NOTIFICATION|CREATE DDL EVENT NOTIFICATION|  
|CREATE DEFAULT|ALTER|CONTROL SERVER|  
|CREATE FULLTEXT CATALOG|ALTER ANY FULLTEXT CATALOG|CONTROL SERVER|  
|CREATE FUNCTION|ALTER|CONTROL SERVER|  
|CREATE MESSAGE TYPE|ALTER ANY MESSAGE TYPE|CONTROL SERVER|  
|CREATE PROCEDURE|ALTER|CONTROL SERVER|  
|CREATE QUEUE|ALTER|CONTROL SERVER|  
|CREATE REMOTE SERVICE BINDING|ALTER ANY REMOTE SERVICE BINDING|CONTROL SERVER|  
|CREATE ROLE|ALTER ANY ROLE|CONTROL SERVER|  
|CREATE ROUTE|ALTER ANY ROUTE|CONTROL SERVER|  
|CREATE RULE|ALTER|CONTROL SERVER|  
|CREATE SCHEMA|ALTER ANY SCHEMA|CONTROL SERVER|  
|CREATE SERVICE|ALTER ANY SERVICE|CONTROL SERVER|  
|CREATE SYMMETRIC KEY|ALTER ANY SYMMETRIC KEY|CONTROL SERVER|  
|CREATE SYNONYM|ALTER|CONTROL SERVER|  
|CREATE TABLE|ALTER|CONTROL SERVER|  
|CREATE TYPE|ALTER|CONTROL SERVER|  
|CREATE VIEW|ALTER|CONTROL SERVER|  
|CREATE XML SCHEMA COLLECTION|ALTER|CONTROL SERVER|  
|DELETE|CONTROL|CONTROL SERVER|  
|CREATE ステートメントを実行する前に、|CONTROL|CONTROL SERVER|  
|EXECUTE ANY EXTERNAL SCRIPT <br /> **適用対象**: [!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]|CONTROL|CONTROL SERVER|   
|INSERT|CONTROL|CONTROL SERVER|  
|KILL DATABASE CONNECTION<br /> **適用対象**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]|CONTROL|ALTER ANY CONNECTION|  
|REFERENCES|CONTROL|CONTROL SERVER|  
|SELECT|CONTROL|CONTROL SERVER|  
|SHOWPLAN|CONTROL|ALTER TRACE|  
|SUBSCRIBE QUERY NOTIFICATIONS|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|マスク解除します。|CONTROL|CONTROL SERVER|  
|UPDATE|CONTROL|CONTROL SERVER|  
|列の暗号化キーの定義を表示します。|CONTROL|VIEW ANY DEFINITION|  
|任意の列のマスター_キーの定義の表示|CONTROL|VIEW ANY DEFINITION|  
|VIEW DATABASE STATE|CONTROL|VIEW SERVER STATE|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 このステートメントを実行するプリンシパル (または AS オプションで指定したプリンシパル) には、データベースに対する CONTROL 権限、またはデータベースに対する CONTROL 権限を暗黙的に許可する上位レベルの権限が与えられている必要があります。  
  
 AS オプションを使用する場合、指定するプリンシパルはデータベースを所有している必要があります。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-revoking-permission-to-create-certificates"></a>A. 証明書を作成する権限を取り消す  
 次の例では失効`CREATE CERTIFICATE`に対する権限、`AdventureWorks2012`ユーザーからのデータベース`MelanieK`です。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
USE AdventureWorks2012;  
REVOKE CREATE CERTIFICATE FROM MelanieK;  
GO  
```  
  
### <a name="b-revoking-references-permission-from-an-application-role"></a>B. REFERENCES 権限をアプリケーション ロールから取り消す  
 次の例では失効`REFERENCES`に対する権限、`AdventureWorks2012`アプリケーション ロールからデータベース`AuditMonitor`です。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]
  
```  
USE AdventureWorks2012;  
REVOKE REFERENCES FROM AuditMonitor;  
GO  
```  
  
### <a name="c-revoking-view-definition-with-cascade"></a>C. CASCADE を指定して VIEW DEFINITION を取り消す  
 次の例では失効`VIEW DEFINITION`に対する権限、`AdventureWorks2012`ユーザーからのデータベース`CarmineEs`とすべてのプリンシパルから`CarmineEs`与え`VIEW DEFINITION`権限です。  
  
```  
USE AdventureWorks2012;  
REVOKE VIEW DEFINITION FROM CarmineEs CASCADE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [データベース権限の許可 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-database-permissions-transact-sql.md)   
 [データベースのアクセス許可 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-database-permissions-transact-sql.md)   
 [アクセス許可 &#40;データベース エンジン&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  

