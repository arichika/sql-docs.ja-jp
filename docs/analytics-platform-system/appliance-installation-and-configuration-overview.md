---
title: アプライアンスのインストールし、構成の分析プラットフォーム システム |Microsoft ドキュメント
description: Analytics Platform System (APS) アプライアンス管理者を設定し、新しいアプライアンスの使用を開始する初期手順について説明します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5b6aa75cdab85fce9ef308d3e853ddb0107c28ee
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Analytics Platform System のアプライアンスのインストールと構成
Analytics Platform System (APS) アプライアンス管理者を設定し、新しいアプライアンスの使用を開始する初期手順について説明します。  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1.ハードウェアをインストールします。  
新しいアプライアンスは、データ センターでドッキング ステーションにパレットに配信されます。  
  
> [!IMPORTANT]  
> IHV がアンパックされる場合によってには、ラック、データ センター内のアプライアンスを接続します。 かどうか、これらの手順が不要になりにスキップできます、 [3 です。アプライアンスを構成する](#ConfigureAppliance)以下のセクションです。  
  
IHV がハードウェアのインストールが実行されていない場合は、ハードウェアをインストールする次の手順を使用します。  
  
|||  
|-|-|  
|**タスク**|**Description**|  
|ドキュメントを確認します。|独立系ハードウェア ベンダー (IHV) からすべての必要なドキュメントや情報を入手したことを確認します。 参照してください[、IHV から取得する情報&#40;Analytics Platform System&#41;](information-to-obtain-from-your-ihv.md)です。|  
|ハードウェアをインストールします。|データ センターがアプライアンスに対応できることを確認します。 アプライアンス コンポーネントをデータ センターに移動します。 ネットワーク スイッチ、Pdu をラックに取り付けて配線です。 参照してください[ハードウェアの設置&#40;Analytics Platform System&#41;](hardware-installation.md)です。|  
  
## <a name="PowerOnAppliance"></a>2.アプライアンス上の電源  
  
|||  
|-|-|  
|**タスク**|**Description**|  
|アプライアンス上の電源|エラーが発生しなかったことを確認する必要に応じて、待機している、必要な順序で各アプライアンス コンポーネント ノードの電源を入れます。|  
  
## <a name="ConfigureAppliance"></a>3.アプライアンスを構成します。  
  
|||  
|-|-|  
|**タスク**|**Description**|  
|||  
|SQL Server PDW を使用してアプライアンスを構成する**構成マネージャー**|Configuration Manager を使用すると、アプライアンス上アプライアンス パスワード、タイム ゾーン、ネットワークとファイアウォールの設定、セキュリティ証明書、およびパフォーマンスおよびその他の設定を設定できます。 参照してください[アプライアンス構成&#40;Analytics Platform System&#41;](appliance-configuration.md)です。|  
  
> [!WARNING]  
> 構成の変更のみに使用する SQL Server PDW**Configuration Manager**です。 によって公開されていない変更**Configuration Manager**はサポートされていません。 たとえば、SQL Server PDW アプライアンスは、英語 (米国) 言語の設定のみをサポートします。  
  
## <a name="SoftwareServicing"></a>4.ソフトウェアのサービスの設定します。  
  
|||  
|-|-|  
|**タスク**|**Description**|  
|SQL Server PDW の更新プログラムを適用します。|(省略可能)最新バージョンに、SQL Server PDW ソフトウェアを更新する 1 つまたは複数の SQL Server PDW の更新を適用する必要があります。 参照してください[分析プラットフォーム システムの修正プログラム適用&#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)です。|  
|Windows Server Update Services を構成します。|ソフトウェアをサポートするための Windows Server Update Services からの更新プログラムを受信するアプライアンスを構成します。 参照してください[ダウンロードして Microsoft 更新プログラムを適用して&#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)です。|  
  
## <a name="NextSteps"></a>次の手順  
前の手順をすべて完了したら、後に、アプライアンスが使用できる状態にします。 ユーザーや、場所にその他の担当者は、次のタスクを開始できます。  
  
|||  
|-|-|  
|**タスク**|**Description**|  
|SQL Server PDW のドライバーをインストールし、接続を構成|SQL Server Data Tools、sqlcmd、ビジネス インテリジェンスのソフトウェア、またはその他のツールを使用して SQL Server PDW に接続するローカル コンピューターを構成します。 <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|ログオンとサーバーの役割を作成し、アクセス許可を割り当てる|計画し、適切なアクセス許可を持つ SQL Server PDW にログオンするユーザーがログオンとサーバーの役割を作成します。 <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Azure Data Management Gateway を構成します。|ゲートウェイには、AP データをセキュリティで保護された OData フィードとして公開することにより、内部設置型 APS データにアクセスする Azure のユーザーができます。 ゲートウェイについては、既に管理 ノードでインストールされます。 構成には、Microsoft を問い合わせてください。|  
|モニターのクエリとアプライアンス ユーザー|管理コンソールとその他のリソースを使用すると、クエリとアプライアンスのユーザーを監視できます。 参照してください[アプライアンスを管理コンソールを使用して監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->です。|  
|SQL Server PDW にデータを読み込む|アプライアンスにデータを読み込みます。 <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|災害復旧計画を作成します。|ハードウェアの障害からデータを保護する方法を計画、またはデータが上書きされます。 定期的なバックアップを使用して計画を作成し、データの破損または消失が発生した場合の計画を復元します。 <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|アプライアンスを監視します。|システム ビュー、ログ、および管理コンソールを使用して、アプライアンスの状態、ヘルス、およびパフォーマンスを監視します。 解決または問題を報告します。 参照してください[モニター アプライアンスの正常性状態&#40;Analytics Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md)です。|  
