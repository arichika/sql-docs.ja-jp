---
title: "DQS セキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2012"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 921927f5-1b1e-452a-a79e-c691829fd826
caps.latest.revision: 11
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# DQS セキュリティ
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) のセキュリティ インフラストラクチャは、SQL Server のセキュリティ インフラストラクチャに基づいています。 データベース管理者は、ユーザーに DQS ロールを関連付けることによって、ユーザーに一連の権限を付与します。 これにより、ユーザーがアクセスできる DQS リソースや、ユーザーが実行できる機能アクティビティを定義します。  
  
## DQS ロール  
 DQS には 4 つのロールがあります。 1 つはデータベース管理者 (DBA) で、主に製品のインストール、データベースのメンテナンス、およびユーザー管理を行います。 このロールは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションよりも SQL Server Management Studio を主に使用します。 このサーバー ロールは sysadmin です。  
  
 その他の 3 つのロールは、 [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] アプリケーションを使用して製品を直接使用するインフォメーション ワーカー、データ スチュワード用です。 これらのロールには、次が含まれます。  
  
-    **DQS 管理者** (dqs_administrator ロール) は、製品のスコープ内のすべてを行うことができます。 管理者は、プロジェクトの編集と実行、ナレッジ ベースの作成と編集、アクティビティの終了、アクティビティ内のプロセスの停止、および構成と参照データ サービス設定の変更を行うことができます。 ただし、DQS 管理者は、サーバーのインストールや新しいユーザーの追加はできません。 これらはデータベース管理者が行う必要があります。  
  
-    **DQS KB エディター** (dqs_kb_editor ロール) は、すべての管理以外の DQS アクティビティを実行できます。 KB エディターは、プロジェクトの編集と実行、およびナレッジ ベースの作成と編集を行うことができます。 アクティビティ監視データを参照することはできますが、アクティビティの終了や停止、または管理業務の実行はできません。  
  
-    **DQS KB オペレーター** (dqs_kb_operator ロール) を編集したり、プロジェクトを実行します。 どのようなナレッジ マネージメントも実行できず、ナレッジ ベースの作成や変更もできません。 アクティビティ監視データを参照することはできますが、アクティビティの終了または管理業務の実行はできません。  
  
## ユーザー管理  
 データベース管理者 (DBA) は DQS ユーザーを作成し、SQL Server Management Studio の DQS ロールに関連付けます。 DBA は、DQS_MAIN データベースのユーザーとして SQL ログインを追加し、各ユーザーを DQS ロールの 1 つと関連付けることによってユーザーの権限を管理します。 各ロールには、DQS_MAIN データベースの一連のストアド プロシージャに対する権限が付与されています。 DQS_PROJECTS および DQS_STAGING_DATA データベースについては、3 つの DQS ロールは使用できません。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|SQL Server Management Studio を使用してユーザーを作成し、DQS ロールを付与する方法について説明します。|[SSMS による DQS ユーザーの管理](../Topic/Manage%20DQS%20Users%20in%20SSMS.md)|  
  
  