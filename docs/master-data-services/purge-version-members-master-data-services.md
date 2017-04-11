---
title: "バージョン メンバーのパージ (マスター データ サービス) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: adecce2d-46bb-49ff-8be9-0b31b8dd3cb6
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# バージョン メンバーのパージ (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、メンバーを削除してもメンバーは非アクティブ化 (論理削除) されるだけです。 データはデータベースに残ります。 このトピックでは、モデル バージョンで論理削除されたすべてのメンバーをパージ (永続的に削除) する方法について説明します。  
  
## 前提条件  
 この手順を実行するには  
  
-   [バージョン管理] 機能領域にアクセスする権限が必要です。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
## 論理削除されたメンバーをパージするには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]**をクリックします。  
  
2.  **[バージョンの管理]** ページで、パージするバージョンのあるモデルを選択します。 モデル バージョンの一覧が表示されます。  
  
3.  パージするバージョンの行を選択します。  
  
4.  **[Purge Members]**(メンバーのパージ) をクリックします。  
  
5.  確認プロンプトで [OK] をクリックします。  
  
## メンバーをパージするための追加メソッド  
 バージョン メンバーをパージすると、選択したバージョンに関連するすべてのエンティティの論理削除されたメンバーが永続的に削除されます。 より細分化された代替手段としては、エンティティ ベースのステージングを使用してエンティティの特定のメンバーのみを永続的に削除します。 また、エクスプローラーの機能権限を持つエンティティ管理者は、エンティティ エクスプローラー ページ内のエンティティ バージョンをパージできます。  
  
 詳細については、「[リーフ メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。  
  
  