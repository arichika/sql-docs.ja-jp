---
title: "エラー ログの監視 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ [SQL Server]"
  - "データベース パフォーマンス [SQL Server]、エラー"
  - "Windows アプリケーション ログ [SQL Server]"
  - "パフォーマンスの監視 [SQL Server]、エラー"
  - "サーバー パフォーマンス [SQL Server]、エラー"
  - "エラー ログとアプリケーション ログの出力の比較"
  - "エラー [SQL Server]、ログ"
  - "データベースのチューニング [SQL Server]、エラー"
  - "データベース監視 [SQL Server]、エラー"
  - "SQL Server エラー ログ"
  - "ログ [SQL Server], SQL Server エラー ログ"
  - "エラー ログ [SQL Server]"
  - "ログ [SQL Server]、Windows アプリケーション ログ"
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# エラー ログの監視
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、特定のシステム イベントとユーザー定義イベントを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログに記録します。 両方のログで、記録されるすべてのイベントのタイムスタンプが自動的に記録されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログの情報を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に関連する問題のトラブルシューティングを行うことができます。  
  
 Windows アプリケーション ログでは、Windows オペレーティング システムで発生したイベントと、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] や [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントでのイベントの全体像が示されます。 Windows イベント ビューアーを使用すると、Windows アプリケーション ログを表示して情報をフィルター処理できます。 たとえば、情報、警告、エラー、および成功または失敗の監査などのイベントをフィルター処理できます。  
  
## エラー ログ出力とアプリケーション ログ出力の比較  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログと Windows アプリケーション ログの両方を使用して、問題の原因を特定できます。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログの監視中、原因に関する情報が含まれていないエラー メッセージが表示される場合があります。 これらのログの間でイベントの日付と時刻を比較することにより、可能性のある原因の範囲を絞り込むことができます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ログ ファイル ビューアーにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、および Windows ログが 1 つの一覧に統合され、関連するサーバー イベントや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントの把握が容易になります。 詳細については、SQL Server オンライン ブックの「[ログ ファイルの表示]」を参照してください。  
  
## このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[SQL Server エラー ログの表示](../../tools/configuration-manager/viewing-the-sql-server-error-log.md)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログとその表示方法について説明します。|  
|[Windows アプリケーション ログの表示](../../tools/configuration-manager/viewing-the-windows-application-log.md)|Windows アプリケーション ログとその表示方法について説明します。|  
  
  