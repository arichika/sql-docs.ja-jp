---
title: "SQLServer のエディション別の計算容量制限 | Microsoft Docs"
ms.custom: ""
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サポートするプロセッサ [SQL Server]"
  - "サポートするプロセッサ数"
  - "サポートする最大プロセッサ数"
ms.assetid: cd308bc9-9468-40cc-ad6e-1a8a69aca6c8
caps.latest.revision: 60
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 60
---
# SQLServer のエディション別の計算容量制限
  このトピックでは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の各エディションの計算容量の制限と、ハイパースレッド プロセッサを持つ物理環境と仮想化環境での違いについて説明します。  
  
 ![容量制限計算のためのマッピング](../sql-server/media/compute-capacity-limits.gif "容量制限計算のためのマッピング")  
  
 次の表では、上の図で使用されている表記について説明します。  
  
|値|説明|  
|-----------|-----------------|  
|0..1|0 個または 1 個|  
|1|1 個|  
|1..*|1 個以上|  
|0..*|0 個以上|  
|1..2|1 個または 2 個|  
  
> [!IMPORTANT]  
>  さらに詳しく説明します。  
>   
>  1.  仮想マシンには、1 個以上の仮想プロセッサが割り当てられます。  
> 2.  1 個の仮想マシンには、1 個以上の仮想プロセッサが割り当てられます。  
> 3.  0 個または 1 個の仮想プロセッサは、0 個以上の論理プロセッサにマップされます。 次に、仮想プロセッサと論理プロセッサのマッピングとその意味を示します。  
>   
>      -   1 対 0 の場合は、ゲスト オペレーティング システムで使用されないアンバウンド論理プロセッサを表します。  
>     -   1 対多の場合は、オーバーコミットを表します。  
>     -   0 対多の場合は、ホスト システム上に仮想マシンがなく、VM が論理プロセッサを使用しないことを表します。  
> 4.  ソケットは、0 個以上のコアにマップされます。 次に、ソケットとコアのマッピングとその意味を示します。  
>   
>      -   1 対 0 の場合は、空の (チップが取り付けられていない) ソケットを表します。  
>     -   1 対 1 の場合は、ソケットに取り付けられているシングルコア チップ (最近では非常にまれ) を表します。  
>     -   1 対多の場合は、ソケットに取り付けられているマルチコア チップ (通常は 2、4、8) を表します。  
> 5.  コアは、1 個または 2 個の論理プロセッサにマップされます。 次に、コアと論理プロセッサのマッピングとその意味を示します。  
>   
>      -   1 対 1 の場合は、ハイパースレッディングが無効です。  
>     -   1 対 2 の場合は、ハイパースレッディングが有効です。  
  
 次の定義は、このトピック全体で使用される用語に適用されます。  
  
-   スレッドまたは論理プロセッサは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、オペレーティング システム、アプリケーション、ドライバーでは 1 個の論理コンピューティング エンジンとして見なされます。  
  
-   コアは、1 個以上の論理プロセッサで構成されるプロセッサ ユニットです。  
  
-   物理プロセッサは、1 個以上のコアで構成されます。 物理プロセッサは、プロセッサ パッケージまたはソケットと同じです。  
  
 1 個以上の物理プロセッサを搭載したシステムや、複数のコアまたはハイパースレッドを持つ物理プロセッサを搭載したシステムでは、オペレーティング システムで複数のタスクを同時に実行できます。 各実行スレッドは論理プロセッサとして表示されます。 たとえば、ハイパースレッディングが有効になっているクアッド コア プロセッサがコンピューターに 2 個搭載されていて、それぞれのコアにスレッドが 2 個ある場合、プロセッサ数が 2、プロセッサごとのコア数が 4、コアごとのスレッド数が 2 であるため、論理プロセッサの数は 16 個 (2 x 4 x 2) になります。 次の点に注意してください。  
  
-   ハイパースレッド コアの単一スレッドの論理プロセッサの計算容量は、ハイパースレッディングが無効になっている同じコアの論理プロセッサの計算容量よりも小さくなります。  
  
-   ただし、ハイパースレッド コアの 2 個の論理プロセッサの計算容量は、ハイパースレッディングが無効になっている同じコアの計算容量よりも大きくなります。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の各エディションには、次の 2 つの計算容量制限があります。  
  
1.  ソケットの最大数 (物理プロセッサまたはソケットまたはプロセッサ パッケージと同じ)。  
  
2.  オペレーティング システムによって報告されたコアの最大数。  
  
 これらの制限は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つのインスタンスに適用され、 1 つのインスタンスが使用する最大計算容量を表します。 これらの制限には、インスタンスが配置される可能性があるサーバーは含まれません。 実際、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の複数のインスタンスを同じ物理サーバーに配置することは、以下に示す容量制限よりも多くのソケットまたはコアを搭載した物理サーバーの計算容量を使用するための効果的な方法です。  
  
 次の表に、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の各エディションの 1 つのインスタンスに適用される計算容量制限を示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [エディション]|1 つのインスタンスで使用される最大計算容量 ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)])|1 つのインスタンスで使用される最大計算容量 (AS、RS)|  
|---------------------------------------|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------|  
|Enterprise Edition: コアベース ライセンス*|オペレーティング システムの最大容量|オペレーティング システムの最大容量|  
|開発者|オペレーティング システムの最大容量|オペレーティング システムの最大容量|  
|Standard|4 ソケットまたは 24 コアのいずれか小さいほうに制限|4 ソケットまたは 24 コアのいずれか小さいほうに制限|  
|Express|1 ソケットまたは 4 コアのいずれか小さいほうに制限|1 ソケットまたは 4 コアのいずれか小さいほうに制限|  
 *Enterprise Edition with Server および Client Access License (CAL) に基づくライセンス (新しい使用許諾契約では利用できません) は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスあたり最大 20 コアに制限されています。 コアベースのサーバー ライセンス モデルでは、制限はありません。  
  
 仮想化された環境では、計算容量の制限はコアではなく論理プロセッサの数に基づいて決まります。これは、ゲスト アプリケーションがプロセッサのアーキテクチャを認識できないためです。  たとえば、クアッド コア プロセッサが搭載された 4 個のソケットと、コアごとに 2 個のハイパースレッドを有効にする機能を備えたサーバーには、ハイパースレッディングが有効になっている論理プロセッサが 32 個ありますが、ハイパースレッディングが無効になっている論理プロセッサは 16 個しかありません。 これらの論理プロセッサはサーバー上の仮想マシンにマップすることができます。これを行うと、マップした論理プロセッサに対する仮想マシンの計算負荷がホスト サーバーの物理プロセッサの実行スレッドにマップされます。  
  
 仮想プロセッサあたりのパフォーマンスが重要な場合は、ハイパースレッディングを無効にすることができます。 ハイパースレッディングの有効化または無効化は、BIOS のセットアップ中にプロセッサの BIOS 設定で行うことができます。ただし、サーバー上で実行されているすべてのワークロードに影響するのは、通常はサーバー スコープの操作です。 したがって、仮想化された環境で実行されるワークロードを、物理オペレーティング システム環境でハイパースレッディングによるパフォーマンス向上の恩恵を受けるワークロードから切り離すと良い結果が得られる場合があります。  
  
## 参照  
 [SQL Server 2016 のエディションとコンポーネント](../sql-server/editions-and-components-of-sql-server-2016.md)   
 [SQL Server 2016 の各エディションでサポートされる機能](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [SQL Server の最大容量仕様](../sql-server/maximum-capacity-specifications-for-sql-server.md)   
 [SQL Server 2016 のクイックスタート インストール](../Topic/Quick-Start%20Installation%20of%20SQL%20Server%202016.md)  
  
  