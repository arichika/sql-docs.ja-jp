---
title: "概要: テーブルからデータをインポートする (マスター データ サービス) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ステージング処理 [Master Data Services]、ステージング処理について"
  - "データのインポート [Master Data Services]"
  - "ステージング処理 [Master Data Services]"
ms.assetid: 181d1e22-379c-45d1-b03c-e1e22ff14164
caps.latest.revision: 21
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 21
---
# 概要: テーブルからデータをインポートする (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]内のデータのモデルを作成すると、データの追加と変更ができるようになります。   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ステージング テーブル、ストアド プロシージャ、マスター データ マネージャーを使います。  
  
 データを追加および変更する方法の手順については、「[テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/import-data-from-tables-master-data-services.md)」を参照してください。  
  
> [!NOTE]  
>  また、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] を使って、Excel から MDS リポジトリ ([!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース) にデータを追加することもできます。 詳細については、「[概要: Excel からのデータのインポート (Excel 用 MDS アドイン)](../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)」を参照してください。  
  
 データを追加、変更する場合は、次の操作を行うことができます。  
  
-   メンバーの読み込みと更新、属性値の更新  
  
-   メンバーの非アクティブ化と削除  
  
-   明示的階層メンバーの移動  
  
 データの追加と更新には、次の主要なタスクが含まれます。  
  
1.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのステージング テーブルにデータを読み込みます。  
  
2.  ステージング テーブルから適切な [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] テーブルにデータを読み込みます。  
  
     ステージング ストアド プロシージャや [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] を使って、データを読み込みます。  
  
> [!NOTE]  
>  [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] では、[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] ステージング プロセスのサポートは推奨されなくなりました。  
  
## メンバーの非アクティブ化と削除 (MDS)  
 非アクティブにしたメンバーは、再びアクティブにできます。 メンバーを再びアクティブにすると、階層およびコレクションにおける属性とメンバーシップが復元されます。 以前のトランザクションはすべてそのままです。 マスター データ マネージャーの **[バージョン管理]** 機能領域の管理者は、非アクティブになっているトランザクションを表示できます。  
  
 削除したメンバーは、システムから完全に削除されます。 そのメンバーのすべてのトランザクション、すべてのリレーションシップ、およびすべての属性が完全に削除されます。  
  
> [!NOTE]  
>  ステージングを使用してメンバーを再アクティブ化することはできません。 マスター データ マネージャーで手動で行う必要があります。 詳細については、「[メンバーまたはコレクションを再アクティブ化する (マスター データ サービス)](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)」を参照してください。  
>   
>  ステージングを使用してコレクションを削除または非アクティブ化することはできません。 手動でのコレクションの非アクティブ化の詳細については、「[メンバーまたはコレクションを削除する (マスター データ サービス)](../master-data-services/delete-a-member-or-collection-master-data-services.md)」を参照してください。  
  
## 明示的階層メンバーの移動 (MDS)  
 明示的階層に含まれるメンバーの位置を一括で移動するときは、次を指定できます。  
  
-   統合メンバーの親として統合メンバー。  
  
-   リーフ メンバーの親として統合メンバー。  
  
-   リーフ メンバーまたは統合メンバーの兄弟としてリーフ メンバー。  
  
-   リーフ メンバーまたは統合メンバーの兄弟として統合メンバー。  
  
## ステージング テーブルとストアド プロシージャ (MDS)  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースには、データを設定できる、次の種類のステージング テーブルが含まれています。  
  
-   [リーフ メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/leaf-member-staging-table-master-data-services.md)  
  
-   [統合メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/consolidated-member-staging-table-master-data-services.md)  
  
-   [リレーションシップ ステージング テーブル (マスター データ サービス)](../master-data-services/relationship-staging-table-master-data-services.md)  
  
 モデル内の各エンティティには、ステージング テーブルがあります。 テーブル名は、対応するエンティティと、リーフ メンバーなどのエンティティ型を示します。 次の画像は、通貨、顧客、製品のエンティティのステージング テーブルを示しています。  
  
 ![Staging Tables in MDS database](../master-data-services/media/mds-staging-tables.png "Staging Tables in MDS database")  
  
 テーブルの名前はエンティティの作成時に指定され、変更できません。 ステージング テーブルの名前に _1 またはその他の数値が含まれる場合は、エンティティの作成時にその名前のテーブルが既に存在していたことを示します。  
  
 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] には、次の種類のステージング ストアド プロシージャが含まれています。  
  
-   stg.udp_\<名前>_Leaf  
  
-   stg.udp_\<名前>_Consolidated  
  
-   stg.udp_\<名前>_Relationship  
  
 モデル内の各エンティティには、リーフ メンバー、統合メンバー、リレーションシップ ステージング テーブルに対応する 3 つのストアド プロシージャがあります。  次の画像は、通貨、顧客、製品のエンティティのステージング ストアド テーブルを示しています。  
  
 ![Staging stored procedures in the MDS database](../master-data-services/media/mds-staging-storedprocedures.png "Staging stored procedures in the MDS database")  
  
 ストアド プロシージャの詳細については、「[ステージング ストアド プロシージャ (マスター データ サービス)](../master-data-services/staging-stored-procedure-master-data-services.md)」を参照してください。  
  
## トランザクションのログ記録 (MDS)  
 データまたはリレーションシップのインポート時または更新時に発生するトランザクションは、すべてログに記録することができます。 ストアド プロシージャのオプションによって、このログ記録が可能になります。 ステージング処理を [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]から開始する場合、ログ記録は行われません。  
  
 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]では、 **[すべてのステージング トランザクションをログに記録]** 設定がステージング データのこのメソッドに適用されません。  
  
## 関連コンテンツ  
  
-   [検証 (マスター データ サービス)](../master-data-services/validation-master-data-services.md)  
  
-   [ビジネス ルール (マスター データ サービス)](../master-data-services/business-rules-master-data-services.md)  
  
  