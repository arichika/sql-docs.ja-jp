---
title: "CPU 使用率の監視 | Microsoft Docs"
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
  - "パフォーマンスの監視 [SQL Server], CPU 使用率"
  - "データベースのチューニング [SQL Server], CPU 使用率"
  - "プロセッサ [SQL Server], 使用率の監視"
  - "データベース パフォーマンス [SQL Server], CPU 使用率"
  - "CPU 使用率の監視 [SQL Server]"
  - "サーバー パフォーマンス [SQL Server], CPU 使用率"
  - "データベース監視 [SQL Server], CPU 使用率"
  - "監視 [SQL Server], CPU 使用率"
  - "プロセッサ [SQL Server]"
  - "CPU [SQL Server], 監視"
  - "サーバー パフォーマンスの監視 [SQL Server], CPU 使用率"
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# CPU 使用率の監視
  CPU 使用率が通常の範囲内にあるかどうかを確認するため、Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを定期的に監視する必要があります。 CPU 使用率が常に高い場合は、CPU のアップグレードまたは多重プロセッサの追加を検討する必要があります。 また、CPU 使用率が高い場合、アプリケーションのチューニングや設計に問題がある可能性もあります。 この場合は、アプリケーションを最適化することで CPU 使用率を下げることができます。  
  
 CPU 使用率を効率よく確認するには、システム モニターの **Processor:% Processor Time** カウンターを使用します。 このカウンターは、アイドル状態でないスレッドを実行するために CPU が費やす時間を監視します。 使用率が常に 80 ～ 90% である場合は、CPU のアップグレードまたはプロセッサの追加が必要です。 多重プロセッサ システムでは、各プロセッサについて、このカウンターを個別に監視します。 この値は、特定のプロセッサの処理時間の合計を表します。 すべてのプロセッサの平均値を調べるには、代わりに **System: %Total Processor Time** カウンターを使用します。  
  
 必要に応じて、次のカウンターでプロセッサ使用率を監視することもできます。  
  
-   **Processor: % Privileged Time**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の I/O 要求など、Microsoft Windows のカーネル コマンドの実行にプロセッサが費やす時間の比率を示します。 **Physical Disk** カウンターの値が高いときに、このカウンターの値が常に高い場合は、より高速で効率的なディスク サブシステムのインストールを検討してください。  
  
    > [!NOTE]  
    >  カーネルの処理時間をどの程度使用するかは、ディスク コントローラーやドライバーによって異なります。 効率のよいコントローラーやドライバーは処理時間をそれほど必要としないため、ユーザー アプリケーションの利用可能な処理時間が多くなり、全体的な処理能力が向上します。  
  
-   **Processor: %User Time**  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] などのユーザー プロセスの実行にプロセッサが費やす時間比率を示します。  
  
-   **System: Processor Queue Length**  
  
     プロセッサ時間を待っているスレッドの数を示します。 プロセスのスレッドが、使用できるよりも多くのプロセッサ サイクルを必要とする場合は、プロセッサのボトルネックが生じます。 複数のプロセスがプロセッサ時間を利用する場合、状況によっては、より高速なプロセッサのインストールが必要になります。 多重プロセッサ システムを使用している場合は、プロセッサの追加も可能です。  
  
 プロセッサ使用率を調べる場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスで実行されている作業の種類を考慮してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が集計に関するクエリや、ディスク I/O を必要としないメモリ バインド クエリなどの多数の計算を実行している場合は、100% のプロセッサ時間が使用されることがあります。 これによって他のアプリケーションのパフォーマンスが低下する場合は、ワークロードを変更してみてください。 たとえば、そのコンピューターを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの実行専用にします。  
  
 多数のクライアント要求が処理されている場合に、使用率が 100% 前後の値を示しているとき、プロセスが待ち行列内でプロセッサ時間を待っているために、ボトルネックが生じていることが考えられます。 この問題を解決するには、より高速なプロセッサを追加します。  
  
  