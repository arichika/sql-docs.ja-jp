---
title: 親子ディメンション |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a9f9cda883822d093db624a4580a94093120ba41
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="parent-child-dimension"></a>親子ディメンション
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  親子階層は、親属性を含んでいる標準ディメンションにある階層です。 親属性は、ディメンション メイン テーブル内の *自己参照型リレーションシップ*または *自己結合*を記述します。 親子階層は 1 つの親属性から構築されます。 親子階層に存在するレベルは、親属性に関連付けられているメンバー間の親子リレーションシップに基づいているので、1 つの親子階層に割り当てられるレベルは 1 つのみです。 親子階層内でのメンバーの位置は、親属性の **KeyColumns** プロパティおよび **RootMemberIf** プロパティで決まります。一方、レベル内でのメンバーの位置は、親属性の **OrderBy** プロパティで決まります。 属性のプロパティの詳細については、「 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」を参照してください。  
  
 親子階層のレベル間に親子リレーションシップがあることにより、一部の非リーフ メンバーには、子メンバーから集計したデータだけでなく、基になるデータ ソースから派生したデータが含まれる場合もあります。  
  
## <a name="dimension-schema"></a>ディメンション スキーマ  
 親子階層のディメンション スキーマは、ディメンション メイン テーブルに存在する自己参照型リレーションシップに依存します。 たとえば、次の図は、 **サンプル データベースの** DimOrganization [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] ディメンション メイン テーブルを示しています。  
  
 ![DimOrganization テーブルの自己参照型の結合](../../analysis-services/multidimensional-models/media/dimorganization.gif "DimOrganization テーブルの自己参照型の結合")  
  
 このディメンション テーブルでは、 **ParentOrganizationKey** 列に **OrganizationKey** 主キー列との外部キー リレーションシップがあります。 つまり、このテーブル内の各レコードは、親子リレーションシップによりテーブル内の別のレコードと関連している可能性があります。 この種の自己結合は、通常、部署内の従業員の管理構造などの組織エンティティ データを表すために使用します。  
  
## <a name="hierarchies-and-levels"></a>階層とレベル  
 親子リレーションシップのないディメンションは、属性をグループ化したり順序付けたりすることにより、階層を構築します。 これらのディメンションは、階層のレベル名を属性名から取得します。  
  
 ただし、親子ディメンションは、ディメンション メイン テーブルに格納されているデータを調べ、テーブル内のレコード間の親子リレーションシップを評価することにより、親子階層を構築します。 親子階層の詳細については、「 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)」を参照してください。  
  
 親子階層内のレベルの名前は、階層の作成に使用された属性からは派生しません。 親子ディメンションでは、名前付けテンプレート (属性が属性階層を生成する方法を制御する、親属性のレベルで指定できる文字列式) の使用により、レベル名が自動的に作成されます。 親属性用の名前付けテンプレートの設定方法の詳細については、「 [属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)」を参照してください。  
  
## <a name="data-members"></a>データ メンバー  
 通常、ディメンションのリーフ メンバーには基になるデータ ソースから直接派生したデータが含まれ、非リーフ メンバーには子メンバーに対して実行した集計から派生したデータが含まれます。  
  
 ただし、親子階層では、一部の非リーフ メンバーに、子メンバーから集計されたデータだけでなく、基になるデータ ソースから派生したデータも含まれている場合があります。 親子階層の非リーフ メンバーの場合、基になるファクト テーブル データを含む特殊なシステム生成の子メンバーを作成できます。 *データ メンバー*と呼ばれるこれらの特殊な子メンバーには、非リーフ メンバーに直接関係付けられた、非リーフ メンバーの子孫から計算される集計値に依存しない値が含まれます。 データ メンバーの詳細については、「 [親子階層の属性](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [親子階層内の属性](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)   
 [データベース ディメンションのプロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/database-dimension-properties.md)  
  
  
