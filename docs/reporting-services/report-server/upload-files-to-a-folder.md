---
title: フォルダーへのファイルのアップロード | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-server
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
- files [Reporting Services]
- folders [Reporting Services], uploading files to
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: dc7ec7802dc229fe3272f6204d3aede698ede150
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="upload-files-to-a-folder"></a>フォルダーへのファイルのアップロード
  ファイル システムからファイルをアップロードし、それらを管理対象アイテムとしてレポート サーバー データベースに格納できます。 ファイルのアップロード時に行われる処理は、ファイルの種類によって異なります。  
  
-   .rdl ファイルのアップロードは、レポートのパブリッシュと同等です。  
  
-   その他のファイルをアップロードすると、アップロードしたファイルが単一のバイナリ オブジェクトとしてレポート サーバー データベースに追加されます。 これらのファイルは、リソースとしてレポート サーバーにパブリッシュされます。 リソースのファイルの種類には指定がありません。 ファイルの拡張子が既知の MIME の種類に一致する場合、リソースの種類を識別するために、その MIME の種類のアイコンが使用されます。 ファイルの拡張子が未登録の場合、リソースは汎用ファイル アイコンで示されます。  
  
> [!NOTE]  
>  レポート データ ソース (.rds) ファイルをアップロードして共有データ ソースを作成することはできません。 .rds ファイルは、レポート デザイナーでのみ使用されます。 レポート マネージャーで定義および管理する共有データ ソース アイテムのコンテンツを、このファイルから提供することはできません。 アップロードする代わりに、.rds ファイルを基に共有データ ソースを作成するスクリプトを記述することができます。  
  
 アップロードするアイテムの最大ファイル サイズは [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]によって決まります。 既定の最大サイズは 4 MB です。  
  
 視覚的には、レポート サーバー データベースにアップロードしたファイルは、以下のアイコンでフォルダー階層に表示されます。  
  
 ![レポート アイコン](../../reporting-services/report-server/media/hlp-16doc.gif "レポート アイコン")  
レポート アイコン  
  
 ![モデル アイコン](../../reporting-services/report-server/media/model-icon.gif "モデル アイコン")  
レポート モデル アイコン  
  
 ![汎用リソース アイコン](../../reporting-services/report-server/media/hlp-16file.gif "汎用リソース アイコン")  
汎用リソース アイコン  
  
 ファイルをアップロードすると、ファイルは常に、現在選択しているフォルダーに格納されます。 最初に、アイテムを含めるフォルダーに移動できます。また、ファイルをアップロードしてから最終的な場所にファイルを移動することもできます。  
  
 ファイルをアップロードするには、レポート マネージャーを使用します。 レポート サーバーにファイルをアップロードできるかどうかは、ロールの割り当てを構成するタスクによって異なります。 既定のセキュリティを使用している場合は、ローカル管理者によってレポート サーバーにアイテムを追加できます。 個人用レポートが有効である場合は、個人用レポート フォルダーを持っているすべてのユーザーに、そのフォルダーへアイテムをアップロードする権限が与えられます。 カスタム ロールの割り当てを使用している場合は、フォルダー管理をサポートするタスクがロールの割り当てに含まれている必要があります。  
  
|目的|含まれるタスク|  
|----------------|-------------------------|  
|.rdl ファイルをフォルダーにアップロード|レポートの管理|  
|任意のファイルをバイナリ オブジェクトとしてアップロード|リソースの管理|  
|フォルダーのコンテンツの表示|リソースの表示、レポートの表示|  
  
## <a name="see-also"></a>参照  
 [レポート マネージャー (SSRS ネイティブ モード)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)   
 [ネイティブ モードのレポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [タスクと権限](../../reporting-services/security/tasks-and-permissions.md)   
 [ファイルまたはレポートをアップロードする &#40;レポート マネージャー&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)  
  
  
