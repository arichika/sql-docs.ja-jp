---
title: "[復元オプション] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベース [Analysis Services], 復元"
  - "データベースの復元 [Analysis Services]"
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 23
---
# [復元オプション]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する方法は数多くありますが、どの方法でもサーバー コンピューターと [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの両方に対する管理者権限が必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元するには、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **[データベースの復元]** ダイアログ ボックスを開き、このダイアログ ボックスから適切なオプション構成を選択して、復元を実行します。 または、ファイルに既に指定されている設定を使用してスクリプトを作成できます。このスクリプトを保存して、必要に応じて実行できます。 この場合、次のセクションの説明に従って、XMLA を使用して復元を実行します。  
  
## XMLA を使用したデータベースの復元  
 XMLA の Restore コマンドを使用すると、.abf ファイルに基づいて復元を実行することによって復元プロセスを自動化できます。 Restore コマンドには数多くのプロパティがあり、セキュリティの定義、リモート パーティションの保存場所、リレーショナル OLAP (ROLAP) オブジェクトの再配置などを指定できます。 詳細については、「[Restore 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)」を参照してください。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
## 参照  
 [[データベースの復元] ダイアログ ボックス (Analysis Services - 多次元データ)](../Topic/Restore%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Restore 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [データベースのバックアップ、復元、および同期 (XMLA)](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  