---
title: セキュリティ保護可能なアイテム | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: security
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- securable items [Reporting Services]
- roles [Reporting Services], securable items
- security [Reporting Services], securable items listed
- role-based security [Reporting Services], securable items
ms.assetid: 27f58d4c-5c7b-4947-af5b-0f1fa60faf5f
caps.latest.revision: 45
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: c6b95923b8ca5dfef2f6b98345ce914eeb11991e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="securable-items"></a>セキュリティ保護可能なアイテム
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、レポート サーバーに保存されているアイテムへのアクセス制御に、ロールベースのセキュリティが使用されます。 レポート サーバーへのユーザー アクセスを許可する場合は、通常次の場所でロールの割り当てのペアを作成します。  
  
-   サイト レベル  
  
-   [ホーム] (レポート サーバーのフォルダー階層のルート ノード)  
  
 セキュリティは、レポート サーバーのフォルダー階層内で継承されます。 サイト レベルと [ホーム] フォルダーでロールの割り当てを作成すると、レポート サーバーのすべてのアイテムおよび操作に拡張される権限の継承が設定されます。  
  
 個別のアイテムにセキュリティを定義することで、権限の継承を無効にすることができます。 個別に保護できるのは、次のアイテムです。  
  
-   フォルダー  
  
-   [レポート]  
  
-   レポート モデル  
  
-   リソース  
  
-   共有データ ソース  
  
-   共有データセット  
  
 スケジュールやサブスクリプションなどのその他の構成要素は、明示的にセキュリティ保護されません。 スケジュールとサブスクリプションは、レポートのセキュリティの中で運用されます。  
  
## <a name="item-descriptions"></a>アイテムの説明  
 セキュリティ保護可能なアイテムの一覧と、その特性の説明を次の表に示します。  
  
|アイテム|特性|  
|----------|---------------------|  
|フォルダー|フォルダーのセキュリティは、フォルダー自体と内部のアイテムに適用されます。 [ホーム] フォルダーは、フォルダー階層のルート ノードです。 このフォルダーに対して設定したセキュリティは、そのフォルダー階層にあるすべての下位フォルダー、レポート、リソース、および共有データ ソースに対するセキュリティの初期設定になります。 詳細については、「 [フォルダーをセキュリティで保護する](../../reporting-services/security/secure-folders.md)」をご覧ください。<br /><br /> [個人用レポート] は特別な用途を持つフォルダーで、専用のロールに基づく黙示的なロールの割り当てによってセキュリティで保護されています。 詳細については、「 [個人用レポートをセキュリティで保護する](../../reporting-services/security/secure-my-reports.md)」を参照してください。|  
|[レポート]|レポートおよびリンク レポートをセキュリティで保護して、ユーザーが実行できるアクションの範囲 (指定したレポートのプロパティを変更するなど) を制御することができます。<br /><br /> レポート履歴は、履歴に含まれているレポートによりセキュリティで保護されます。 レポート履歴のスナップショットを個別にセキュリティで保護することはできません。<br /><br /> レポートのセキュリティの詳細については、「 [レポートとリソースの保護](../../reporting-services/security/secure-reports-and-resources.md)」を参照してください。|  
|レポート モデル|レポート モデル全体またはその一部に対してロールの割り当てを指定できます。 レポート モデルは非常に広範囲にわたることがあるため、そのような場合は、機密データに関連するモデル アイテムのみをセキュリティで保護できます。|  
|リソース|リソースをセキュリティで保護して、リソース自体とプロパティへのアクセスを制御することができます。<br /><br /> スタンドアロン リソースのみ、独立したアイテムとしてセキュリティで保護できます。 レポートに埋め込まれているリソースは、レポートと別にセキュリティで保護できません。<br /><br /> レポートのセキュリティの詳細については、「 [レポートとリソースの保護](../../reporting-services/security/secure-reports-and-resources.md)」を参照してください。|  
|共有データ ソース|共有データ ソースをセキュリティで保護して、共有データ ソース アイテムおよびそのプロパティ ページへのアクセスを制限することができます。 詳細については、「 [Secure Shared Data Source Items](../../reporting-services/security/secure-shared-data-source-items.md)」(共有データ ソース アイテムをセキュリティで保護する) を参照してください。|  
|共有データセット|共有データセットをセキュリティで保護し、ユーザーが実行できるアクションの範囲 (定義の表示や変更、特定の共有データセットのプロパティの変更など) を制御できます。<br /><br /> 詳細については、「 [共有データセット アイテムをセキュリティで保護する](../../reporting-services/security/secure-shared-dataset-items.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [ネイティブ モードのレポート サーバーに対する権限の許可](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [ロールを作成、削除、または変更する (Management Studio)](../../reporting-services/security/role-definitions-create-delete-or-modify.md)   
 [レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)](../../reporting-services/security/grant-user-access-to-a-report-server-report-manager.md)   
 [ロールの割り当てを変更または削除する (レポート マネージャー)](../../reporting-services/security/role-assignments-modify-or-delete.md)  
  
  
