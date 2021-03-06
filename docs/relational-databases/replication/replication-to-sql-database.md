---
title: SQL Database へのレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Database replication
- replication, SQL Database
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5e3099ebb18883a99b5815b3db3e40f178b22234
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="replication-to-sql-database"></a>SQL Database へのレプリケーション
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に対し、 [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]のレプリケーションを構成できます。  
 
 ### <a name="supported-configurations"></a>**サポートされている構成:**  
 -  オンプレミスで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス、またはクラウド上の Azure の仮想マシンで実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が可能です。 詳細については、「 [Azure Virtual Machines 上の SQL Server の概要](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)」を参照してください。  
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャーのプッシュ サブスクライバーである必要があります。  
 -  ディストリビューション データベースとレプリケーション エージェントは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]には配置できません。  
 - スナップショットおよび一方向トランザクション レプリケーションがサポートされています。 ピアツーピア トランザクション レプリケーションおよびマージ レプリケーションはサポートされていません。  
 
 ## <a name="versions"></a>バージョン  
 - パブリッシャーとディストリビューターは、次のいずれかのバージョンである必要があります。  
   
 -   [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)]  
 
 -   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
   
 -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1 CU3  
   
 -   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
   
 -   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP2 CU8  
   
 -   予定されている[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] SP3  
   
 - 以前のバージョンを使用してレプリケーションを構成しようとするとエラー番号 MSSQL_REPL20084 (プロセスでサブスクライバーに接続できませんでした) および MSSQL_REPL40532 (このログインで要求されたサーバー \<name> を開くことができません。 ログインに失敗しました。) が表示される場合があります。  
 
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のサブスクライバーは任意のリージョンに存在する V12 以上である必要があります。  
   
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のすべての機能を使用するには、最新バージョンの [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) と [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx) を使用する必要があります。  
   
 ## <a name="remarks"></a>Remarks  
 - レプリケーションは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、またはパブリッシャーで [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行して構成できます。 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] ポータルを使用してレプリケーションを構成することはできません。  
   
 - レプリケーションでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続に [!INCLUDE[ssSDS](../../includes/sssds-md.md)]認証ログインのみを使用できます。  
   
 - レプリケートしたテーブルには、主キーが必要です。  
   
 - 既存の Azure サブスクリプションと、既存の [!INCLUDE[ssSDS](../../includes/sssds-md.md)] V12 が必要です。  
   
 - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 上の単一のパブリケーションでは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (オンプレミスと Azure 仮想マシン上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ) の両方のサブスクライバーをサポートできます。  
   
 - レプリケーションの管理、監視、およびトラブルシューティングは、オンプレミスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]から実行する必要があります。  
   
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] へは、プッシュ サブスクリプションのみがサポートされています。  
   
 - SQL データベースの `@subscriber_type = 0` では、 **sp_addsubscription** のみがサポートされています。  
   
 - [!INCLUDE[ssSDS](../../includes/sssds-md.md)] では、双方向、即時、更新可能な、またはピア ツー ピアのレプリケーションはサポートされていません。      
   
 ## <a name="replication-architecture"></a>レプリケーションのアーキテクチャ  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
   
 ## <a name="scenarios"></a>シナリオ  
   
 ### <a name="typical-replication-scenario"></a>典型的なレプリケーションのシナリオ  
   
 1.  オンプレミスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに、トランザクション レプリケーションのパブリケーションを作成します。  
   
 2.  オンプレミスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で、 **へのプッシュ サブスクリプションを作成するために、** [サブスクリプションの新規作成ウィザード] [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用するか、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ステートメントを使用します。  
   
 3.  初期データセットは、通常、スナップショット エージェントにより作成され、ディストリビューション エージェントにより配信および適用されるスナップショットです。 初期データセットは、バックアップや、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]のレプリケーションを構成できます。  
   
 #### <a name="data-migration-scenario"></a>データの移行シナリオ  
   
 1.  トランザクション レプリケーションを使用して、データをオンプレミスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから [!INCLUDE[ssSDS](../../includes/sssds-md.md)]へレプリケートします。  
   
 2.  クライアントまたは中間層アプリケーションをリダイレクトし、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のコピーを更新します。  
   
 3.  テーブルの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンの更新を停止し、パブリケーションを削除します。  
   
 ## <a name="limitations"></a>制限事項  
  次のオプションは、 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] のサブスクリプションではサポートされていません。  
   
 -   ファイル グループの関連付けのコピー  
   
 -   テーブルのパーティション分割スキーマのコピー  
   
 -   インデックスのパーティション分割のスキーマのコピー  
   
 -   ユーザー定義の統計情報のコピー  
   
 -   既定のバインドのコピー  
   
 -   ルールのバインドのコピー  
   
 -   フルテキスト インデックスのコピー  
   
 -   XML XSD のコピー  
   
 -   XML インデックスのコピー  
   
 -   アクセス許可のコピー  
   
 -   空間インデックスのコピー  
   
 -   フィルター選択されたインデックスのコピー  
   
 -   データ圧縮属性のコピー  
   
 -   スパース列属性のコピー  
   
 -   filestream の MAX データ型への変換  
   
 -   hierarchyid の MAX データ型への変換  
   
 -   空間の MAX データ型への変換  
   
 -   拡張プロパティのコピー  
   
 -   アクセス許可のコピー  
   
### <a name="limitations-to-be-determined"></a>未定の制限 
 
 -   コピーの照合順序  
   
 -   [SP のシリアル化されたトランザクションでの実行]  
   
 ## <a name="examples"></a>使用例  
  パブリケーションおよびプッシュ サブスクリプションを作成します。 詳細については、以下をご覧ください。  
   
 -   [パブリケーションの作成](../../relational-databases/replication/publish/create-a-publication.md)  
   
 -   [プッシュ サブスクリプションの作成](../../relational-databases/replication/create-a-push-subscription.md)。サブスクライバーとして [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] の論理サーバー名 (**N'azuresqldbdns.database.windows.net'** など) を、転送先データベースとして [!INCLUDE[ssSDS](../../includes/sssds-md.md)] の名前 (**AdventureWorks** など) を使用します。  
   
 ## <a name="see-also"></a>参照  
 - [パブリケーションの作成](../../relational-databases/replication/publish/create-a-publication.md)   
 - [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 - [レプリケーションの種類](../../relational-databases/replication/types-of-replication.md)   
 - [監視 &#40;レプリケーション&#41;](../../relational-databases/replication/monitor/monitoring-replication.md)   
 - [サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)  
