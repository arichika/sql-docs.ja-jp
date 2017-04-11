---
title: "派生階層 (Master Data Services) | Microsoft Docs"
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
helpviewer_keywords: 
  - "派生階層"
  - "階層 [マスター データ サービス], 派生階層"
  - "派生階層, 派生階層について"
ms.assetid: a0fbd519-a10e-4cbd-92e6-5de9b8d3e3f0
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# 派生階層 (Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の派生階層は、モデル内のエンティティ間に既に存在するドメインベースの属性のリレーションシップから派生します。  
  
 派生階層を作成することで、モデル内の既存のドメイン ベースの属性リレーションシップを強調表示できます。  
  
## 他のリーフ メンバーをグループ化するリーフメンバー  
 派生階層では、1 つのエンティティのリーフ メンバーを使用して別のエンティティのリーフ メンバーをグループ化します。 派生階層は、これらのエンティティの間のリレーションシップに基づいています。 これに対し、明示的階層は単一エンティティのメンバーに基づき、指定した任意の方法で構造化されます。  
  
 派生階層の構造は、基になるデータに影響を与えることなく変更できます。 モデル内にリレーションシップが存在している限り、派生階層を削除してもマスター データには影響しません。  
  
## 明示的階層と派生階層  
 次の表は、明示的階層と派生階層の相違点の一部を示しています。  
  
> [!NOTE]  
>  明示的階層は、今回のリリースで廃止されました。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]します。  
  
|明示的階層|派生階層|  
|--------------------------|-------------------------|  
|構造はユーザーによって定義される|構造はドメイン ベースの属性間のリレーションシップから派生する|  
|単一のエンティティからのメンバーを含む|複数のエンティティからのメンバーを含む|  
|他のメンバーをグループ化する統合メンバーを使用する|1 つのエンティティのリーフ メンバーを使用して、別のエンティティのリーフ メンバーをグループ化する|  
  
## 変数の深さ階層の作成  
 変数の深さ階層の作成方法として、次の 2 種類の方法をお勧めします。  
  
-   すべてのレベルの属性を同じにする場合は、単一のエンティティを作成してから、エンティティに基づくドメイン ベースの属性を使用してそのエンティティの再帰型階層を作成します。  
  
-   リーフ メンバーに 1 セットの属性が必要で、上位レベルにはもう 1 セット属性が必要な場合は、派生階層に 2 つのエンティティを作成します。 リーフ エンティティに対しては、親エンティティに基づくドメイン ベースの属性を使用します。 親エンティティに対しては、親エンティティ自体に基づくドメイン ベースの属性を使用します。  
  
## 派生階層の例  
 次の例では、Product エンティティのリーフ メンバーは Subcategory エンティティのリーフ メンバーによってグループ化されています。Subcategory エンティティは、Category エンティティのリーフ メンバーによってグループ化されています。 Product エンティティには Subcategory というドメイン ベースの属性があり、Subcategory エンティティには Category というドメイン ベースの属性があるので、この階層は有効です。  
  
 階層構造は、メンバーがグループ化されている方法を示します。 ほとんどのメンバーを持つエンティティは一番下に位置します。  
  
 ![モデル構造から派生した階層](../master-data-services/media/mds-conc-derived-hierarchy-structure.gif "モデル構造から派生した階層")  
  
 派生階層では、Product と Subcategory 間のリレーションシップを強調表示してから、Subcategory と Category 間のリレーションシップを強調表示できます。 この階層内にメンバーを表示すると、ツリー内の各レベルに同じエンティティのメンバーが含まれています。  
  
 ![マウンテン バイク派生階層の例](../master-data-services/media/mds-conc-derived-hierarchy-example.gif "マウンテン バイク派生階層の例")  
  
 この種類の階層では、無効なレベルにメンバーを移動できません。 たとえば、自転車 Road-650 は、Road Bikes というサブカテゴリから Mountain Bikes という別のサブカテゴリに移動することはできますが、 1 {Bikes} などのカテゴリの直下に移動することはできません。 階層ツリー内でメンバーを移動するたびに、メンバーのドメイン ベースの属性値は、移動を反映して変更されます。  
  
## 注  
 派生階層ツリー内のすべてのメンバーは、コードによって並べ替えられます。 並べ替え順序は変更できません。  
  
 メンバーのドメイン ベースの属性が空で、その属性が派生階層で使用される場合、そのメンバーは階層内に表示されません。 属性への値の設定を要求するビジネス ルールを作成してください。 詳細については、次を参照してください。 [属性の値を必要とする (&) #40 です。マスター データ サービスと #41;](../master-data-services/require-attribute-values-master-data-services.md)します。  
  
## 関連タスク  
  
|タスクの説明|トピック|  
|----------------------|-----------|  
|新しい派生階層を作成する。|[派生階層 (& r) #40 です。マスター データ サービスと #41 です。](../master-data-services/create-a-derived-hierarchy-master-data-services.md)|  
|既存の派生階層のレベルを非表示にするか、または削除する。|[非表示または派生階層と #40; 内のレベルを削除マスター データ サービスと #41 です。](../master-data-services/hide-or-delete-levels-in-a-derived-hierarchy-master-data-services.md)|  
|既存の派生階層の名前を変更する。|[派生階層名と #40; を変更します。マスター データ サービスと #41 です。](../master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|  
|既存の派生階層を削除する。|[派生階層と #40; を削除します。マスター データ サービスと #41 です。](../master-data-services/delete-a-derived-hierarchy-master-data-services.md)|  
  
## 関連コンテンツ  
  
-   [ドメイン ベースの属性と #40 です。マスター データ サービスと #41 です。](../master-data-services/domain-based-attributes-master-data-services.md)  
  
-   [明示的階層と #40 です。マスター データ サービスと #41 です。](../master-data-services/explicit-hierarchies-master-data-services.md)  
  
-   [再帰型階層と #40 です。マスター データ サービスと #41 です。](../master-data-services/recursive-hierarchies-master-data-services.md)  
  
-   [#40; (&)、明示的なキャップを持つ派生階層マスター データ サービスと #41 です。](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)  
  
-   [派生階層と #40; で多対多のリレーションシップを表示します。マスター データ サービスと #41 です。](../master-data-services/show-many-to-many-relationships-in-derived-hierarchies-master-data-services.md)  
  
-   [コレクションと #40 です。マスター データ サービスと #41 です。](../master-data-services/collections-master-data-services.md)  
  
  