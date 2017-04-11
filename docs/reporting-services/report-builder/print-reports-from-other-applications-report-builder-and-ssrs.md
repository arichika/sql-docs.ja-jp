---
title: "他のアプリケーションからのレポートの印刷 (レポート ビルダーおよび SSRS) | Microsoft Docs"
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
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# 他のアプリケーションからのレポートの印刷 (レポート ビルダーおよび SSRS)
  レポート ビルダーには、他のアプリケーションでレポートを簡単に表示できるエクスポート オプションが用意されています。 **Export** コマンドは、レポートをブラウザーまたは Web ベース アプリケーションで開くときにレポートの上部に表示される [レポート] ツール バーで使用できます。 レポートをエクスポートすると、レポートは別のアプリケーションで表示されます。たとえば、レポートを Excel にエクスポートすると、[!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)] でレポートが開きます。 印刷を実行する場合は、必要な印刷機能がアプリケーションに備わっている場合にのみレポートのエクスポートをお勧めします。  
  
 レポートを別のアプリケーションにエクスポートするには、該当するアプリケーションがインストールされている必要があります。 たとえば、Acrobat (PDF) 形式でエクスポートするには、コンピューターにあらかじめ Adobe Acrobat Reader がインストールされている必要があります。 TIFF 形式でレポートをエクスポートする場合は、レポート サーバーにより、TIFF ファイル形式に関連付けられている表示アプリケーションでレポートが開かれます。 インストールされている [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のバージョンにより異なりますが、この表示アプリケーションには、通常 Windows 画像と FAX ビューアーが使用されます。 既定の解像度は、画面の解像度に合わせて、96 DPI になります。 Windows 画像と Fax ビューアーの解像度は、プリンターの機能に合わせて、300 DPI または 600 DPI に上げることができます。 解像度の調整方法の詳細については、Windows の製品マニュアルを参照してください。  
  
 Web アーカイブ (MHTML) を選択した場合、レポートは既定のブラウザーにエクスポートされます。 ブラウザーから印刷すると、レポートのパス情報がすべてのページの下部に追加される場合があります。 多くの場合、ブラウザーのオプションを設定して、印刷ページにパス情報が印刷されないように設定できます。 詳細については、使用しているブラウザーの製品マニュアルを参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## 参照  
 [レポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/print-a-report-report-builder-and-ssrs.md)   
 [印刷コントロールを使用したブラウザーからのレポートの印刷 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [レポートのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)   
 [別の種類のファイルとしてレポートをエクスポートする &#40;レポート ビルダーおよび SSRS&#41;](../Topic/Export%20a%20Report%20as%20Another%20File%20Type%20\(Report%20Builder%20and%20SSRS\).md)   
 [レポートの検索、表示、管理 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  