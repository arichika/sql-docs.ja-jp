---
title: "マージ レプリケーションの Web 同期 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ レプリケーションの同期 [SQL Server レプリケーション]"
  - "インターネット [SQL Server レプリケーション], 同期"
  - "同期 [SQL Server レプリケーション], Web 同期"
  - "Web 公開 [SQL Server レプリケーション], 同期"
  - "Web 同期, 概要"
  - "Web 同期 (Web synchronization)"
ms.assetid: 84785aba-b2c1-4821-9e9d-a363c73dcb37
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# マージ レプリケーションの Web 同期
  マージ レプリケーションの Web 同期を利用すると、HTTPS プロトコルを使用したデータのレプリケートが可能になり、以下のようなシナリオで役立ちます。  
  
-   モバイル ユーザーからのデータをインターネット上で同期します。  
  
-   データの同期 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 企業ファイアウォール経由でのデータベースです。  
  
 たとえば、移動中の営業担当者は Web 同期を使用することができます。 [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] の営業担当者は、担当地域内の多数の店舗や納入業者を回ります。 長い移動の際にはホテルに滞在するため、一日の終わりに販売データをアップロードしたり、製品の更新をダウンロードするための便利な方法が必要になります。  
  
 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] の IT 部門は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で各ポータブル コンピューターを構成し、マージ レプリケーションで Web 同期を使用できるようにしました。 各ポータブル コンピューターのマージ エージェントでは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) を実行しているコンピューターにインストールされたレプリケーション コンポーネントを指すインターネットの URL を保持しています。 これらのコンポーネントにより、パブリッシャーとサブスクライバーが同期されます。 これで各担当者は、リモート ダイアルアップ接続を行わなくても、任意のインターネット接続経由で必要なデータのアップロードやダウンロードが行えるようになります。 インターネット接続では SSL (Secure Sockets Layer) を使用するため、仮想プライベート ネットワーク (VPN) は必要ありません。  
  
 Web 同期に必要なコンポーネントを構成する方法については、次を参照してください。 [Web 同期の構成](../../relational-databases/replication/configure-web-synchronization.md), 、[Web 同期用に IIS 構成](../../relational-databases/replication/configure-iis-for-web-synchronization.md), 、および [Web 同期用の IIS 7 の構成](../../relational-databases/replication/configure-iis-7-for-web-synchronization.md)します。  
  
> [!NOTE]  
>  Web 同期は、ポータブル コンピューター、ハンドヘルド デバイスなどのクライアントでデータを同期することを目的に設計されています。 Web 同期は、サーバー間のアプリケーションでの大量のデータ同期には適していません。  
  
## Web 同期の動作の概要  
 Web 同期を使用すると、サブスクライバーでの更新はパッケージ化され、HTTPS プロトコルを使用して XML メッセージとして IIS を実行しているコンピューターに送信されます。 次に IIS を実行しているコンピューターは、バイナリ形式でパブリッシャーにコマンドを送信します (通常は TCP/IP を使用します)。 パブリッシャーでの更新は、IIS を実行しているコンピューターに送信され、XML メッセージとしてパッケージ化されてサブスクライバーに配信されます。  
  
 次の図は、マージ レプリケーションの Web 同期に関係するコンポーネントを示しています。  
  
 ![Web 同期コンポーネントとデータ フロー](../../relational-databases/replication/media/web-sync01.gif "Web 同期コンポーネントとデータ フロー")  
  
 Web 同期は、プル サブスクリプションだけのオプションなので、サブスクライバー上では必ずマージ エージェントが動作します。 標準のマージ エージェント、マージ エージェントの ActiveX コントロール、またはレプリケーション管理オブジェクト (RMO) によって同期機能を提供するアプリケーションのいずれかを使用できます。 IIS を実行しているコンピューターの場所を指定するには、使用、 **– InternetUrl** マージ エージェントのパラメーターです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナー (Replisapi.dll) は、IIS を実行しているコンピューター上で構成され、パブリッシャーとサブスクライバーからサーバーに送信されたメッセージを処理します。 トポロジの各ノードは、マージ レプリケーション競合回避モジュール (Replrec.dll) を使用して XML データ ストリームを処理します。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] またはそれ以降のバージョンの Web 同期に参加しているすべてのコンピューターに必要です。  
  
### 同期プロセス  
 同期中の手順は次のとおりです。  
  
1.  マージ エージェントがサブスクライバーで開始されます。 このエージェントでは、次のことを行います。  
  
    1.  サブスクリプション データベースに SQL 接続を行います。  
  
    2.  データベースからすべての変更を抽出します。  
  
    3.  IIS を実行しているコンピューターに HTTPS 要求を行います。  
  
    4.  データの変更を XML メッセージとしてアップロードします。  
  
2.  IIS を実行しているコンピューター上でホストされる、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーション リスナーおよびマージ レプリケーション競合回避モジュールでは、次のことを行います。  
  
    1.  HTTPS 要求に応答します。  
  
    2.  パブリケーション データベースに SQL 接続を行います。  
  
    3.  アップロードされた変更をパブリケーション データベースに適用します。  
  
    4.  サブスクライバー用にダウンロードされた変更を抽出します。  
  
    5.  HTTPS 応答をマージ エージェントに返送します。  
  
3.  その後、サブスクライバーのマージ エージェントは HTTPS 応答を受け取り、サブスクリプション データベースに変更のダウンロードを適用します。  
  
## 参照  
 [Web 同期の構成](../../relational-databases/replication/configure-web-synchronization.md)   
 [Web 同期トポロジ](../../relational-databases/replication/topologies-for-web-synchronization.md)  
  
  