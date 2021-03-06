---
title: 配信拡張機能を実装する準備 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 1c74178a2f5ece00d7e9fb86943cd5029ee403ca
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="preparing-to-implement-a-delivery-extension"></a>配信拡張機能を実装する準備
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を実装する前に、実装するインターフェイスを定義しておく必要があります。 最初に配信拡張機能の使用方法、配信拡張機能に必要な設定、およびレポート通知を配信するために実装が必要な特定の機能を決定する必要があります。  
  
 各 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能は、次の機能を提供する必要があります。  
  
-   <xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイスの実装。拡張機能とローカライズされた拡張機能名を表します。  
  
-   <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> の実装。レポート通知をエンド ユーザーに配信するために使用できる配信拡張機能を作成します。  
  
-   サブスクリプション用の特定のユーザー データを処理する機能。  
  
 各配信拡張機能は、次の機能を含むように強化することができます。  
  
-   [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ユーザー コントロールの実装。エンド ユーザーがレポート マネージャーを使用して、配信拡張機能を使用するレポート サブスクリプションを作成できます。  
  
 次の表では、配信拡張機能で使用できるインターフェイスとクラスについて説明します。  
  
|インターフェイスまたはクラス|Description|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイス|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の拡張機能を表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイス|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] の配信拡張機能を表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> インターフェイス|配信拡張機能に必要なレポート サーバーに関する情報を含みます (使用可能な表示拡張機能の一覧など)。|  
|<xref:Microsoft.ReportingServices.Interfaces.Setting> クラス|拡張機能の設定を表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.Notification> クラス|配信拡張機能がレポートの配信に使用するサブスクリプション情報を含みます。|  
|<xref:Microsoft.ReportingServices.Interfaces.Report> クラス|配信拡張機能によるユーザーへのレポート配信を可能にする、レポート固有の情報とメソッドを表します。|  
|<xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> クラス|表示拡張機能からの出力を表します。 <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> オブジェクトには、表示拡張機能によって返されたストリームを処理するために、配信拡張機能に必要な関連付けられたファイルの名前と種類の情報を含みます。|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> インターフェイス|レポート マネージャーのユーザーから配信拡張機能固有のサブスクリプション情報を取得する方法を表すユーザー コントロール (電子メール アドレスやファイル共有ディレクトリへのパスなど)。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [配信拡張機能の実装](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
