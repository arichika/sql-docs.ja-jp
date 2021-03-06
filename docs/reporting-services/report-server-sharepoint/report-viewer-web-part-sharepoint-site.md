---
title: SharePoint サイトのレポート ビューアー Web パーツ - SSRS | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server-sharepoint
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c29118ab8807d8bd0d51ee593488c66c89bf2942
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="report-viewer-web-part-on-a-sharepoint-site---reporting-services"></a>SharePoint サイトのレポート ビューアー Web パーツ - Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

レポート ビューアー Web パーツはカスタム Web パーツです。 Web パーツを使うと、SharePoint サイト内のレポート サーバーにあるレポートの表示、ナビゲーション、印刷、エクスポートを行うことができます。 レポート ビューアー Web パーツは、Microsoft SQL Server Reporting Services レポート サーバーによって処理されるレポート定義 (.rdl) ファイルに関連付けられています。 

最新のレポート ビューアー Web パーツは、Power BI Report Server に展開されたページ分割されたレポートを処理することもできます。 Web パーツは、Power BI レポートでは機能しません。

## <a name="why-the-report-viewer-web-part-is-re-introduced"></a>レポート ビューアー Web パーツが再度導入された理由

レポート ビューアー Web パーツは、SharePoint 製品用の Reporting Services アドインの一部として利用できました。 Web パーツは、SharePoint 統合モードのレポート サーバーに固有のものでした。 SQL Server 2016 の後で、SharePoint 統合モードは非推奨となりました。

SQL Server 2017 以降では、Reporting Services のインストール モードは**ネイティブ モード**だけです。 ページ ビューアー Web パーツを使うすべてのレポートの種類は、*rs:Embed=true* URL パラメーターを使って埋め込むことができます。 SharePoint ページへのレポートの埋め込みはユーザーから要望のあった統合方法であり、更新されたレポート ビューアー Web パーツはページ分割されたレポートでこのシナリオを可能にします。

ページ分割されたレポートを SharePoint ページに埋め込むにはページ ビューアー Web パーツで十分ですが、更新されたレポート ビューアー Web パーツはそれ以外の機能も提供します。

* 特定のツール バー ボタンの表示/非表示
* レポートのパラメーター値の上書き
* レポート パラメーターへのフィルター Web パーツの接続

## <a name="download-the-report-viewer-web-part-solution-package"></a>レポート ビューアー Web パーツのソリューション パッケージのダウンロード

レポート ビューアー Web パーツは、Microsoft ダウンロード センターから入手できます。

[レポート ビューアー Web パーツのソリューション パッケージのダウンロード](https://www.microsoft.com/download/details.aspx?id=55949)

## <a name="considerations-and-limitations"></a>注意点と制限事項

以下の項目は、更新されたレポート ビューアー Web パーツに固有のものです。

* Web パーツは、"*クラシック*" SharePoint ページでのみ使うことができます。
* レポート ビューアー Web パーツでの埋め込みでサポートされているのは、ページ分割された (RDL) レポートだけです。 Power BI レポートまたはモバイル レポートを埋め込む場合は、*rs:Embed=true* URL パラメーターを使うことができます。

## <a name="next-steps"></a>次の手順

更新されたレポート ビューアー Web パーツを使い始めるには、「[Deploy the Report Viewer web part on a SharePoint site](deploy-report-viewer-web-part.md)」(SharePoint サイトにレポート ビューアー Web パーツを展開する) を参照してください。
