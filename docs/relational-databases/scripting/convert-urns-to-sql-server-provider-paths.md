---
title: "URN から SQL Server プロバイダー パスへの変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c9b1b8f1-b117-4e87-9704-2170f62c5c8b
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# URN から SQL Server プロバイダー パスへの変換
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) モデルでは、オブジェクトに対して URN (Uniform Resource Name) が作成されます。 各 URN によって、SMO オブジェクトが一意に識別されます。また、**Convert-UrnToPath** コマンドレットを使用して、URN を SQL Server PowerShell プロバイダーのパスに変換できます。  
  
## パスへの URN の変換  
 各 URN に含まれる情報はオブジェクトへのパスと同じですが、形式が異なります。 たとえば、テーブルへのパスは次のようになります。  
  
 SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Person.Address  
  
 これと同じオブジェクトへの URN は次のようになります。  
  
 Server[@Name='MyComputer']\Database[@Name='AdventureWorks2012']\Table[@Name='Address' and @Schema='Person']  
  
 PowerShell スクリプトで SMO オブジェクトを作成した場合は、**Urn** プロパティを参照してそのオブジェクトの URN を取得し、**Convert-UrnToPath** コマンドレットを使用して SMO URN 文字列を Windows PowerShell パスに変換できます。 次に、プロバイダーを使用して、パス上の別の場所に移動できます。  
  
 Windows PowerShell パス名でサポートされない拡張文字がノード名に含まれている場合、**Convert-UrnToPath** はそれらの文字を 16 進数表記でエンコードします。 たとえば、"My:Table" は "My%3ATable" として返されます。  
  
 このコマンドレットの使用例については、Windows PowerShell で次を実行してください。  
  
```  
Get-Help Convert-UrnToPath -Examples  
```  
  
## 参照  
 [クエリ式と Uniform Resource Name](../../powershell/query-expressions-and-uniform-resource-names.md)   
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  