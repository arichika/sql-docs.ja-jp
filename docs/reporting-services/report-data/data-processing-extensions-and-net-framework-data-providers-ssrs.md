---
title: "データ処理拡張機能と .NET Framework データ プロバイダー (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "レポート [Reporting Services]、データ"
  - "データ処理拡張機能 [Reporting Services]"
  - "データ プロバイダー [Reporting Services]"
  - "データの取得 [Reporting Services]"
  - "Reporting Services、データ ソース"
  - "レポート データ [レポート ビルダー], アクセス"
ms.assetid: 42a5afb5-f4c8-4957-b1fd-77bf39afa5be
caps.latest.revision: 19
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 19
---
# データ処理拡張機能と .NET Framework データ プロバイダー (SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能は、特定の種類のデータ ソースからのデータ取得や、レポート デザインやレポート処理をサポートする追加機能を提供することを目的として、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と共にインストールされるコンポーネントです。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーは、特定の種類のデータ ソースからのデータの取得や変更を可能にする <xref:System.Data> インターフェイスをサポートするコンポーネントで、[!INCLUDE[msCoName](../../includes/msconame-md.md)] またはサード パーティ ソースから入手できます。  
  
## データ処理拡張機能について  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能では、<xref:System.Data> インターフェイスのサブセットがサポートされています。 データ処理拡張機能には、データ ソースへの読み取り専用アクセスのみが必要です。書き込みおよび更新用のインターフェイスは実装されていません。 それぞれのデータ処理拡張機能では、レポート処理をサポートするカスタム機能を設定できます。 たとえば、データ処理拡張機能がサポートしている機能の種類は次のとおりです。  
  
-   資格情報を接続文字列とは別に管理  
  
-   複数値パラメーターのサポート  
  
-   データ ソースで計算されたサーバー集計の取得  
  
-   データ ソースからのデータ プロパティおよびデータ値の取得  
  
## データ プロバイダーについて  
 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダー (ドライバーと呼ばれることもある) では、データ ソースのデータを読み込み、書き込み、更新するための <xref:System.Data> インターフェイスの標準セットがサポートされています。 データ プロバイダーは、特定の種類のデータ ソースに対して使用できるデータ処理拡張機能がない場合に使用できます。 サード パーティの標準 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーは多数あります。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には拡張可能なデータ プロバイダー アーキテクチャがあるので、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] データ処理拡張機能によって提供される追加機能を含めたカスタムのデータ処理拡張機能を構築することもできます。 詳細については、「 [Implementing a Data Processing Extension](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)」を参照してください。 サード パーティのデータ処理拡張機能の詳細については、サード パーティのデータ処理拡張機能に付属するドキュメントを参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーまたはカスタム データ処理拡張機能を使用してデータ ソースのデータにアクセスするには、インストールと登録が事前に完了している必要があります。 レポートを作成するためのレポート クライアントと、パブリッシュされたレポートを表示するためのレポート サーバーの両方で、データ処理拡張機能をインストールおよび登録する必要があります。 すべてのデータ プロバイダーがサーバー環境で機能するように設計されているわけではありません。 詳細については、「[標準 .NET Framework データ プロバイダーを登録する (SSRS)](../../reporting-services/report-data/register-a-standard-net-framework-data-provider-ssrs.md)」と「[データ処理拡張機能の配置](../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)」を参照してください。  
  
## 参照  
 [データ処理拡張機能の概要](../../reporting-services/extensions/data-processing/data-processing-extensions-overview.md)   
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
  
  