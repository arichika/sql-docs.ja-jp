---
title: "データベース ミラーリング モニターの起動 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データベース ミラーリングの監視 [SQL Server]"
  - "データベース ミラーリング モニター [SQL Server], 起動"
  - "データベース ミラーリング [SQL Server] の監視"
ms.assetid: 53165335-97ca-4f88-8e78-22f1839dee98
caps.latest.revision: 20
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 20
---
# データベース ミラーリング モニターの起動 (SQL Server Management Studio)
  データベース ミラーリング モニターは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] モニターの一部であり、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] から起動します。  
  
> [!NOTE]  
>  データベース ミラーリング モニターは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのエディションで使用できるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の各エディションでサポートされる機能の一覧については、「[SQL Server 2016 の各エディションがサポートする機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)」を参照してください。  
  
### データベース ミラーリング モニターを起動するには  
  
1.  プリンシパル サーバー インスタンスに接続した後、オブジェクト エクスプローラーでサーバー名をクリックして、サーバー ツリーを展開します。  
  
2.  **[データベース]** を展開し、監視するデータベースをクリックします。  
  
3.  データベースを右クリックして **[タスク]** を選択し、**[データベース ミラーリング モニターの起動]** をクリックします。  
  
4.  **[データベース ミラーリング モニター]** ダイアログ ボックスで、**[ミラー化されたデータベースの登録]** をクリックして 1 つまたは複数のミラー化されたデータベースを登録します。  
  
    > [!NOTE]  
    >  1 つのパートナーにデータベースを登録すると、そのデータベースは他のパートナーにも自動的に登録されます。 モニターに他のパートナー インスタンス用の接続資格情報が既にある場合は、その情報が接続時に使用されます。 そのような接続資格情報がない場合、モニターは Windows 認証を使用して接続を試行します。 いずれかのサーバー インスタンスへの接続に使用している資格情報を変更する場合は、**[[OK] をクリックしたときに [サーバー インスタンスの接続管理] ダイアログ ボックスを表示する]** をクリックします。  
  
 データベース ミラーリング モニターの詳細については、「[データベース ミラーリング モニターの概要](../../database-engine/database-mirroring/database-mirroring-monitor-overview.md)」を参照してください。  
  
## 参照  
 [データベース ミラーリング &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
  