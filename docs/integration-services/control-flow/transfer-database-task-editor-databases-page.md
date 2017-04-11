---
title: "[データベース転送タスク エディター] ([データベース] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferdatabasetask.database.f1"
helpviewer_keywords: 
  - "データベース転送タスク エディター"
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# [データベース転送タスク エディター] ([データベース] ページ)
  **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページを使用すると、データベース転送タスクに使用される転送元および転送先のデータベースのプロパティを指定できます。 データベース転送タスクは、2 つの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースをコピーまたは移動します。 このタスクを使用して、同じサーバー内でデータベースをコピーすることもできます。 このタスクの詳細については、「[データベース転送タスク](../../integration-services/control-flow/transfer-database-task.md)」を参照してください。  
  
## オプション  
 **SourceConnection**  
 SMO 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックしてコピー元のサーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックしてコピー先のサーバーへの新しい接続を作成します。  
  
 **[DestinationDatabaseName]**  
 転送先サーバーの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの名前を指定します。  
  
 このフィールドにソース データベースの名前を自動的に入力するには、**[SourceConnection]** と **[SourceDatabaseName]** を先に指定します。  
  
 転送先サーバー上のデータベースの名前を変更するには、このフィールドに新しい名前を入力します。  
  
 **[DestinationDatabaseFiles]**  
 転送先サーバーにおけるデータベース ファイルの名前と場所を指定します。  
  
 このフィールドにソース データベース ファイルの名前と場所を自動的に入力するには、**[SourceConnection]**、**[SourceDatabaseName]**、**[SourceDatabaseFiles]** を先に指定します。  
  
 データベース ファイルの名前を変更するか、転送先サーバー上の新しい場所を指定するには、このフィールドにソース データベースの情報を入力した後、参照ボタンをクリックします。 **[転送先データベース ファイル]** ダイアログ ボックスで、**[転送先ファイル]**、**[転送先フォルダー]**、または **[ネットワーク ファイル共有]** を編集します。  
  
> [!NOTE]  
>  参照ボタンを使用してデータベース ファイルを指定した場合、ファイルの場所はローカル ドライブの表記 (c:\\ など) を使用して入力されます。 これをコンピューター名と共有名を含むネットワーク共有の表記に変える必要があります。 既定の管理共有を使用する場合、$ 表記を使用し、その共有に対する管理アクセスを行える必要があります。  
  
 **[DestinationOverwrite]**  
 転送先サーバーのデータベースを上書きできるかどうかを指定します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|Description|  
|-----------|-----------------|  
|**True**|転送先サーバーのデータベースを上書きします。|  
|**False**|転送先サーバーのデータベースを上書きしません。|  
  
> [!CAUTION]  
>  **[DestinationOverwrite]** に **[True]** を指定した場合、転送先サーバーのデータベースのデータが上書きされます。これにより、データが失われる可能性があります。 データが失われないようにするには、データベース転送タスクを実行する前に、転送先サーバーのデータベースを別の場所にバックアップしておきます。  
  
 **操作**  
 タスクによってデータベースを転送先サーバーにコピー (**[Copy]**) するのか移動 (**[Move]**) するのかを指定します。  
  
 **方法**  
 転送元サーバーのデータベースがオンライン モードのときにタスクを実行するか、オフライン モードのときに実行するかを指定します。  
  
 オフライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが **sysadmin** 固定サーバー ロールのメンバーである必要があります。  
  
 オンライン モードを使用してデータベースを転送するには、パッケージを実行するユーザーが **sysadmin** 固定サーバー ロールのメンバーであるか、選択されたデータベースのデータベース所有者 (**dbo**) である必要があります。  
  
 **[SourceDatabaseName]**  
 コピーまたは移動されるデータベースの名前を選択します。  
  
 **[SourceDatabaseFiles]**  
 参照ボタンをクリックして、データベース ファイルを選択します。  
  
 **[ReattachSourceDatabase]**  
 失敗した場合に、ソース データベースの再アタッチを試行するかどうかを指定します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|Description|  
|-----------|-----------------|  
|**True**|ソース データベースを再アタッチします。|  
|**False**|ソース データベースを再アタッチしません。|  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [[データベース転送タスク エディター] &#40;[全般] ページ&#41;](../Topic/Transfer%20Database%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  