---
title: データ処理拡張機能コードのデバッグ | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- debugging data processing extensions [Reporting Services]
- troubleshooting [Reporting Services], data processing extensions
- data processing extensions [Reporting Services], debugging
ms.assetid: e963e205-9ae0-446d-97df-028a1d2727d9
caps.latest.revision: 40
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 2fb83b02372a5ecb7313185f18d841884ffab775
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="debugging-data-processing-extension-code"></a>データ処理拡張機能コードのデバッグ
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] には、データ処理拡張機能コードを分析してエラーを探すのに役立ついくつかのデバッグ ツールが用意されています。 最適なデバッグ ツールは、使用する目的によって異なります。 この例では [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)]を使用します。  
  
#### <a name="to-debug-your-data-processing-extension-code"></a>データ処理拡張機能コードをデバッグするには  
  
1.  [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] を起動し、データ処理拡張機能プロジェクトを開きます。  
  
2.  プロジェクトを構築し、データ処理拡張機能アセンブリと付随する .pdb ファイルをレポート デザイナーに配置します。 配置の詳細については、「[データ処理拡張機能をレポート デザイナーに配置する方法](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)」を参照してください。  
  
3.  データ処理拡張機能コードを [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] で開いたまま、別の [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ウィンドウで新しいレポート プロジェクトを開きます。  
  
4.  データ処理拡張機能プロジェクトを含む [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のウィンドウに移動し、コードにブレーク ポイントを設定します。  
  
5.  データ処理拡張機能プロジェクト ウィンドウを開いたまま、**[デバッグ]** メニューの **[プロセスにアタッチ]** をクリックします。  
  
     **[プロセスにアタッチ]** ダイアログが開きます。  
  
6.  プロセスの一覧から、レポート プロジェクトに対応する devenv.exe プロセスを選択して、**[アタッチ]** をクリックします。  
  
7.  レポート プロジェクトの **[レポート データ]** タブを使用して、レポート データ ソースを定義します。 通常、汎用クエリ デザイナーを使用してカスタム データ ソースへのクエリを実行します。 これにより、デバッガーが呼び出され、ブレーク ポイントに対応するコードが実行されます。  
  
8.  F11 キーを使用してコードを実行します。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用したデバッグの詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] のマニュアルを参照してください。  
  
## <a name="see-also"></a>参照  
 [データ処理拡張機能の配置](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension.md)   
 [Reporting Services の拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
