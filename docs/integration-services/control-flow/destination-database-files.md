---
title: "[転送先データベース ファイル] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.transferdatabasetask.destdbfiles.f1"
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# [転送先データベース ファイル]
  **[転送先データベース ファイル]** ダイアログ ボックスを使用すると、転送先サーバーのデータベース ファイルの名前と場所を表示または変更したり、データベース転送タスクのネットワーク ファイルの場所を指定したりできます。 このタスクの詳細については、「[データベース転送タスク](../../integration-services/control-flow/transfer-database-task.md)」を参照してください。  
  
 このダイアログ ボックスで転送元サーバーのデータベース ファイルの名前と場所を自動的に入力するには、最初に **[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページで、**[SourceConnection]**、**[SourceDatabaseName]**、および **[SourceDatabaseFiles]** を指定します。  
  
## オプション  
 **[転送先ファイル]**  
 転送先サーバーの転送されたデータベース ファイルの名前です。  
  
 ファイル名を入力するか、ファイル名をクリックして編集します。  
  
 **[同期先フォルダー]**  
 データベース ファイルの転送先となる転送先サーバーのフォルダーです。  
  
 フォルダー パスを入力するか、フォルダー パスをクリックして編集するか、参照ボタンをクリックしてデータベース ファイルを転送する転送先サーバーのフォルダーを指定します。  
  
 **[ネットワーク ファイル共有]**  
 データベース ファイルの転送先となる転送先サーバーのネットワーク共有フォルダーです。 **[ネットワーク ファイル共有]** は、データベースをオフライン モードで転送する場合に使用します。**[データベース転送タスク エディター]** ダイアログ ボックスの **[データベース]** ページの **[Method]** に、**[DatabaseOffline]** を指定します。  
  
 ネットワーク ファイル共有の場所を入力するか、参照ボタンをクリックしてネットワーク ファイル共有の場所を見つけます。  
  
 オフライン モードでデータベースを転送すると、データベース ファイルは **[転送先フォルダー]** で指定した場所に転送される前に、**[ネットワーク ファイル共有]** で指定した場所にコピーされます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[データベース転送タスク エディター] &#40;[全般] ページ&#41;](../Topic/Transfer%20Database%20Task%20Editor%20\(General%20Page\).md)   
 [[データベース転送タスク エディター] &#40;[データベース] ページ&#41;](../Topic/Transfer%20Database%20Task%20Editor%20\(Databases%20Page\).md)  
  
  