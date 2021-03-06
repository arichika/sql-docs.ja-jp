---
title: Linux および macOS - 高可用性と災害復旧の ODBC ドライバー |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fa656c5b-a935-40bf-bc20-e517ca5cd0ba
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d416abb8076e4728724ff971845a9efd970cccc2
ms.sourcegitcommit: feff98b3094a42f345a0dc8a31598b578c312b38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
---
# <a name="odbc-driver-on-linux-and-macos-support-for-high-availability-and-disaster-recovery"></a>Linux および macOS 高可用性と災害復旧のサポート上の ODBC ドライバー
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Linux および macOS サポート用の ODBC ドライバー[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]です。 詳細については[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]を参照してください。  
  
-   [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー (SQL Server)](http://msdn.microsoft.com/library/hh213417.aspx)  
  
-   [可用性グループ (SQL Server) の作成と構成](http://msdn.microsoft.com/library/ff878265.aspx)  
  
-   [フェールオーバー クラスタ リングと AlwaysOn 可用性グループ (SQL Server)](http://msdn.microsoft.com/library/ff929171.aspx)  
  
-   [アクティブなセカンダリ: 読み取り可能なセカンダリ レプリカ (AlwaysOn 可用性グループ)](http://msdn.microsoft.com/library/ff878253.aspx)  
  
接続文字列で、特定の可用性グループの可用性グループ リスナーを指定できます。 Linux または macOS 上の ODBC アプリケーションがフェールオーバーする可用性グループ内のデータベースに接続されている場合は、元の接続が切断され、アプリケーションは、フェールオーバー後の作業を続行する新しい接続を開く必要があります。

Linux および macOS 上の ODBC ドライバーは、可用性グループ リスナーに接続していないと、複数の IP アドレスがホスト名に関連付けられた場合は、DNS ホスト名に関連付けられているすべての IP アドレスを順番に反復処理します。

DNS サーバーの最初の返された IP アドレスが接続可能でない場合、これらのイテレーションは時間を削減できます。 可用性グループ リスナーに接続する、ドライバーは並列ですべての IP アドレスへの接続を確立しようとします。 接続試行が成功すると、ドライバーは保留状態の接続試行をすべて破棄します。

> [!NOTE]  
> 接続が可用性グループのフェールオーバーのため失敗する可能性、接続再試行ロジックを実装します。再接続されるまでは、失敗した接続を再試行してください。 接続タイムアウトを長くして、接続再試行ロジックを実装すると、可用性グループに接続できる可能性が高くなります。

## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続

常に指定**MultiSubnetFailover = [はい]** に接続するとき、[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]可用性グループ リスナーまたは[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]フェールオーバー クラスター インスタンス。 **MultiSubnetFailover**すべての可用性グループおよびフェールオーバー クラスター インスタンスに対して高速フェールオーバーを有効に[!INCLUDE[ssSQL11](../../../includes/sssql11_md.md)]です。 **MultiSubnetFailover**単一サブネットおよびマルチ サブネットの AlwaysOn トポロジにおけるフェールオーバー時間が大幅に軽減します。 マルチサブネット フェールオーバーの場合、クライアントは複数の接続を並列で試行します。 サブネットのフェールオーバー中に、ドライバーは、TCP 接続を積極的に再試行します。

**MultiSubnetFailover** 接続プロパティは、可用性グループまたはフェールオーバー クラスター インスタンスにアプリケーションが配置されていることを示します。 ドライバーが、プライマリ データベースに接続しようとしています。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]すべての ip アドレスに接続しようとしてのインスタンスに対応します。 接続するときに**MultiSubnetFailover = [はい]** クライアントは、オペレーティング システムの既定の TCP 再転送間隔よりも高速接続試行を再試行します。 **MultiSubnetFailover=Yes** を指定すると、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後に、短時間で再接続できます。 **MultiSubnetFailover = Yes**単一およびマルチ サブネットの可用性グループとフェールオーバー クラスター インスタンスの両方に適用されます。  

可用性グループ リスナーまたはフェールオーバー クラスター インスタンスに接続する場合は、 **MultiSubnetFailover=Yes** を使用します。 それ以外の場合、アプリケーションのパフォーマンスが低下します。

可用性グループまたはフェールオーバー クラスター インスタンス内のサーバーに接続するときは、次に注意してください。
  
-   指定**MultiSubnetFailover = Yes**単一サブネットまたはマルチ サブネットの可用性グループに接続するときにパフォーマンスを向上させるためにします。

-   接続文字列でサーバーとして可用性グループの可用性グループ リスナーを指定します。
  
-   接続することはできません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 64 を超える IP アドレスで構成されているインスタンス。

-   両方[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]で認証または Kerberos 認証を使用できます**MultiSubnetFailover = Yes**アプリケーションの動作に影響を与えずにです。

-   **loginTimeout** の値を増やすことで、フェールオーバー時間に対応し、アプリケーションの接続試行回数を減らすことができます。

-   分散トランザクションはサポートされていません。  
  
読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
2.  アプリケーションに **ApplicationIntent=ReadWrite** が使用されているが、セカンダリ レプリカの場所が読み取り専用アクセスとして構成されている。  
  
プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly**が含まれていると、接続は失敗します。  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="odbc-syntax"></a>ODBC 構文

2 つの ODBC 接続文字列キーワードをサポートして[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]:  
  
-   **ApplicationIntent**  
  
-   **MultiSubnetFailover**  
  
ODBC 接続文字列キーワードの詳細については、「 [SQL Server Native Client での接続文字列キーワードの使用](http://msdn.microsoft.com/library/ms130822.aspx)」を参照してください。  
  
同等の接続属性は次のとおりです。
  
-   **SQL_COPT_SS_APPLICATION_INTENT**  
  
-   **SQL_COPT_SS_MULTISUBNET_FAILOVER**  
  
ODBC 接続属性の詳細については、次を参照してください。 [SQLSetConnectAttr](http://msdn.microsoft.com/library/ms131709.aspx)です。  
  
使用する ODBC アプリケーション[!INCLUDE[ssHADR](../../../includes/sshadr_md.md)]接続を確立する 2 つの関数のいずれかを使用できます。  
  
|関数|Description|  
|------------|---------------|  
|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|**SQLConnect**の両方をサポート**ApplicationIntent**と**MultiSubnetFailover**データ ソース名 (DSN) または接続属性を使用しています。|  
|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|**SQLDriverConnect**サポート**ApplicationIntent**と**MultiSubnetFailover** DSN、接続文字列キーワード、または接続属性を使用しています。|
  
## <a name="see-also"></a>参照  

[接続文字列のキーワードとデータ ソース名 (DSN)](../../../connect/odbc/linux-mac/connection-string-keywords-and-data-source-names-dsns.md)

[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)

[リリース ノート](../../../connect/odbc/linux-mac/release-notes.md)  
