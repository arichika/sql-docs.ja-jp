---
title: Add-rolemember コマンドレット |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: powershell
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8144e76d8d3ba7e0ff588c9f22875af430b68a1b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="add-rolemember-cmdlet"></a>Add-RoleMember コマンドレット
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]

  Analysis Services のテーブル データベースまたは多次元データベースの特定のロールにメンバーを追加します。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
## <a name="syntax"></a>構文  
 `Add-RoleMember [-MemberName] <System.String> [-Database] <System.String> [-RoleName] <System.String> [<CommonParameters>]`  
  
 `Add-RoleMember [-MemberName] <System.String> [-DatabaseRole] <Microsoft.AnalysisServices.Role> [<CommonParameters>]`  
  
## <a name="description"></a>Description  
 Add-RoleMember コマンドレットは、既存のデータベース ロールに有効なメンバーを追加します。 データベース ロールのみが許可されます。 このコマンドレットを使用して、サーバー ロールにメンバーを追加することはできません。  
  
 一度に追加できるのは 1 つのメンバーのみで、ユーザー アカウントまたはグループ アカウントです。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-membername-string"></a>-Membername\<文字列 >  
 ロールに追加する Windows ユーザーまたはグループを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-database-string"></a>-Database \<string>  
 ロールが属するデータベースを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-rolename-string"></a>-RoleName\<文字列 >  
 メンバーの追加先となるロールを指定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-databaserole-string"></a>-Databaserole &\<文字列 >  
 メンバーの追加先となる Microsoft.AnalysisServices.Role オブジェクトを指定します。 データベース ロールをパイプラインを介して指定する場合に、–Database および –RoleName パラメーターの代わりにこのパラメーターを使用します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|可 (ByPropertyName)|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters>  
 このコマンドレットは、-Verbose、-Debug、-ErrorAction、-ErrorVariable、-OutBuffer、および –OutVariable の共通パラメーターをサポートしています。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|なし|  
  
## <a name="example-1"></a>例 1  
  
```  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername “adventure-works\bobh” –database “AdventureWorks” –rolename “Reader”  
```  
  
 このコマンドは、既定のローカル インスタンス上で動作する AdventureWorks データベースの Reader ロールに Windows ドメイン ユーザー アカウントを追加します。  
  
## <a name="example-2"></a>例 2  
  
```  
PS SQLSERVER:\sqlas\localhost\default> $roles= dir .\databases\AWTEST\Roles  
PS SQLSERVER:\sqlas\localhost\default> $roles  
PS SQLSERVER:\sqlas\localhost\default> add-rolemember –membername:“adventure-works\bobh” –databaserole:$roles[0]  
```  
  
 行 1 は、AWTEST データベースのすべてのデータベース ロールをパイプラインに追加します。 行 2 のプロンプトで入力した「$roles」は、ロールの配列を示しています。 行 3 は、配列内の最初のロールのメンバーとして、Windows ユーザー "adventure-works\bobh" を追加します。  
  
## <a name="example-3"></a>例 3  
  
```  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles=dir  
PS SQLSERVER:\sqlas\localhost\default\Databases\AWTEST\Roles> $roles[0] | Add-rolemember –membername “adventure-works\bobh”  
```  
  
 このコマンドは、Windows ドメイン ユーザー アカウントを配列内の最初のロールに追加します。この配列は、特定のデータベース (AWTEST) のコンテキストで Roles フォルダーの子の一覧を表示することによって作成されたものです。  
  

  
  
