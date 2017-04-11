---
title: "データベースの状態 | Microsoft Docs"
ms.custom: ""
ms.date: "07/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SQL13.SWB.DATABASESTATES.F1"
helpviewer_keywords: 
  - "緊急のデータベース状態 [SQL Server]"
  - "データベース状態の確認"
  - "データベース状態の参照"
  - "データベースの状態の表示"
  - "データベースの状態 [SQL Server]"
  - "現在のデータベースの状態"
  - "オフラインのデータベース状態 [SQL Server]"
  - "問題があると考えられるデータベース状態"
  - "復旧保留のデータベース状態 [SQL Server]"
  - "状態 [SQL Server]、データベース"
  - "オンラインのデータベース状態"
  - "状態 [SQL Server]"
  - "データベース状態の復元 [SQL Server]"
ms.assetid: b7f1f111-ca73-4a89-b567-a98d64d6ecb3
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# データベースの状態
  データベースは、常に、ある特定の状態にあります。 たとえば、ONLINE、OFFLINE、SUSPECT などです。 データベースの現在の状態を確認するには、[sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューで **state_desc** 列を選択するか、[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md) 関数で **Status** プロパティを選択します。  
  
## データベースの状態の定義  
 次の表では、データベースの状態を定義します。  
  
|状態|定義|  
|-----------|----------------|  
|ONLINE|データベースにアクセスできます。 復旧時に行われる元に戻すフェーズが完了していなくても、プライマリ ファイル グループはオンラインです。|  
|OFFLINE|データベースは使用できません。 ユーザーの明示的な操作によってデータベースがオフラインになり、ユーザーが新たな操作を行うまでオフラインのままになります。 たとえば、ファイルを新しいディスクに移動するために、データベースをオフラインにできます。 移動の完了後に、データベースをオンラインに戻します。|  
|RESTORING|プライマリ ファイル グループの 1 つ以上のファイルが復元中か、1 つ以上のセカンダリ ファイルがオフラインで復元中です。 データベースは使用できません。|  
|RECOVERING|データベースが復旧中です。 復旧処理は一時的な状態です。復旧が成功すると、データベースは自動的に online 状態になります。 復旧が失敗すると、データベースは suspect 状態になります。 データベースは使用できません。|  
|RECOVERY PENDING|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、復旧中にリソースに関連するエラーが発生しました。 データベースは破損していませんが、ファイルが見つからないか、システム リソースの制限によりデータベースを起動できない可能性があります。 データベースは使用できません。 エラーを解決して復旧処理を完了するには、ユーザーによる新たな操作が必要です。|  
|SUSPECT|少なくともプライマリ ファイル グループが問題のある状態で、破損している可能性があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の起動中にはデータベースを復旧できません。 データベースは使用できません。 問題を解決するには、ユーザーによる新たな操作が必要です。|  
|EMERGENCY|ユーザーがデータベースを変更し、状態を EMERGENCY に設定しました。 データベースはシングル ユーザー モードになり、修復または復元できます。 データベースは READ_ONLY に設定され、ログ記録が無効になり、アクセスが **sysadmin** 固定サーバー ロールのメンバーに制限されます。 EMERGENCY は、主にトラブルシューティングの目的で使用されます。 たとえば、suspect に設定されたデータベースを、EMERGENCY 状態に設定できます。 これにより、システム管理者にデータベースへの読み取り専用のアクセスを許可できます。 **sysadmin** 固定サーバー ロールのメンバーのみが、データベースを EMERGENCY 状態に設定できます。|  
  
## 関連コンテンツ  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)  
  
 [ミラーリング状態 &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
 [ファイルの状態](../../relational-databases/databases/file-states.md)  
  
  