---
title: ユーザー階層 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 40b3ebfd8a92bb1c577c9fbd8ee4c9ed0068a700
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="user-hierarchies"></a>ユーザー階層
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ユーザー定義階層で使用される属性のユーザー定義階層は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]をディメンションのメンバーを階層構造に整理し、キューブ内のナビゲーション パスを提供します。 たとえば、次のテーブルでは、時間ディメンションにディメンション テーブルを定義します。 ディメンション テーブルは、年、四半期、月という 3 つの属性をサポートしています。  
  
|年|Quarter|Month|  
|----------|-------------|-----------|  
|1999|第 1 四半期|1 月|  
|1999|第 1 四半期|2 月|  
|1999|第 1 四半期|3 月|  
|1999|第 2 四半期|4 月|  
|1999|第 2 四半期|5 月|  
|1999|第 2 四半期|6 月|  
|1999|第 3 四半期|7 月|  
|1999|第 3 四半期|8 月|  
|1999|第 3 四半期|9 月|  
|1999|第 4 四半期|Oct|  
|1999|第 4 四半期|11 月|  
|1999|第 4 四半期|Dec|  
  
 年、四半期、月の各属性は、時間ディメンションに Calendar というユーザー定義階層を作成するために使用されます。 次の図は、Calendar ディメンション (標準のディメンション) のレベルとメンバーの関係を示しています。  
  
 ![時間ディメンションのレベルとメンバーの階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/media/as-levelconcepts.gif "時間ディメンションのレベルとメンバーの階層")  
  
> [!NOTE]  
>  2 つのレベルで構成される既定の属性階層以外の階層はすべて、ユーザー定義階層と呼ばれます。 属性階層の詳細については、次を参照してください。[属性と属性階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)です。  
  
## <a name="member-structures"></a>メンバー構造  
 親子階層の例外を除いて、階層内のメンバーの位置は、階層定義の属性の順序に制御されます。 階層定義内の各属性によって階層のレベルが作成されます。 レベル内のメンバーの位置は、レベルの作成に使用された属性の順序によって決まります。 ユーザー定義階層のメンバー構造は、メンバー間の関係によって、4 つの基本形式のいずれかになります。  
  
### <a name="balanced-hierarchies"></a>均衡階層  
 均衡階層では、階層のすべての分岐は同じレベルに至り、各メンバーの論理上の親はそのメンバーのすぐ上のレベルです。 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースが示す Product ディメンションの Product Categories 階層は、均衡階層の好例です。 Product Name レベルの各メンバーは Subcategory レベルに親メンバーがあり、Subcategory レベルは Category レベルに親メンバーがあります。 また、階層内の各分岐には Product Name レベルのリーフ メンバーがあります。  
  
### <a name="unbalanced-hierarchies"></a>不均衡階層  
 不均衡階層では、階層の分岐はさまざまなレベルに至ります。 親子階層は不均衡階層です。 たとえば、[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] サンプルの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの Organization ディメンションには、各従業員のメンバーが含まれています。 CEO は階層の最上位メンバーで、部長と役員秘書は CEO の直下にあります。 部長は従属メンバーですが、役員秘書は直属です。  
  
 エンド ユーザーは、不均衡階層と不規則階層を区別できません。 ただし、管理者は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でさまざまなテクニックとプロパティを使用してこれらの 2 種類の階層をサポートできます。 詳細については、次を参照してください。[不規則階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md)、および[、親子階層内の属性](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)です。  
  
### <a name="ragged-hierarchies"></a>不規則階層  
 不規則階層では、少なくとも 1 つのメンバーの論理上の親メンバーが、そのメンバーのすぐ上のレベルにありません。 このため、不規則階層の分岐はさまざまなレベルに至ります。 たとえば、Continent、CountryRegion、City の各レベルで順に定義されている地域ディメンションでは、メンバー Europe は階層の最上位レベルに表示され、メンバー France は中間レベル、メンバー Paris は最下位レベルに表示されます。 France は Europe より限定的で、Paris は France より限定的です。 この標準階層は、次のように変更されます。  
  
-   Vatican City メンバーが CountryRegion レベルに追加されます。  
  
-   City レベルにメンバーが追加され、CountryRegion レベルの Vatican City メンバーに関連付けられます。  
  
-   Province というレベルが CountryRegion レベルと City レベルの間に追加されます。  
  
 Province レベルに、CountryRegion レベルの他のメンバーに関連付けられているメンバーが生成され、City レベルのメンバーが Province レベルの対応するメンバーに関連付けられます。 ただし、CountryRegion レベルの Vatican City メンバーは Province レベルのメンバーに関連付けられていないため、メンバーは City レベルから CountryRegion レベルの Vatican City メンバーに直接関連付ける必要があります。 この変更により、このディメンションの階層は不規則になります。 市 Vatican City の親は国/地域である Vatican City で、これは City レベルの Vatican City メンバーの真上にはありません。 詳細については、「 [不規則階層](../../analysis-services/multidimensional-models/user-defined-hierarchies-ragged-hierarchies.md)」を参照してください。  
  
### <a name="parent-child-hierarchies"></a>親子階層  
 ディメンションの親子階層は、親子属性という特殊な属性を使用して定義され、これによってメンバー間の相互関係が決まります。 親属性は、ディメンション メイン テーブル内の *自己参照型リレーションシップ*または *自己結合*を記述します。 親子階層は 1 つの親属性から構築されます。 親子階層に存在するレベルは、親属性に関連付けられているメンバー間の親子リレーションシップに基づいているので、1 つの親子階層に割り当てられるレベルは 1 つのみです。 親子階層のディメンション スキーマは、ディメンション メイン テーブルに存在する自己参照型リレーションシップに依存します。 たとえば、次の図は、 **DimOrganization**ディメンション メイン テーブルを[!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]サンプル データベース。  
  
 ![DimOrganization テーブルの自己参照型の結合](../../analysis-services/multidimensional-models/media/dimorganization.gif "DimOrganization テーブルの自己参照型の結合")  
  
 このディメンション テーブルでは、 **ParentOrganizationKey** 列に **OrganizationKey** 主キー列との外部キー リレーションシップがあります。 つまり、このテーブル内の各レコードは、親子リレーションシップによりテーブル内の別のレコードと関連している可能性があります。 この種の自己結合は、通常、部署内の従業員の管理構造などの組織エンティティ データを表すために使用します。  
  
 親子階層を作成する場合、両方の属性で表す列は同じデータ型でなければなりません。 また、どちらの属性も同じテーブルに属する必要があります。 既定では、親キーがそのメンバー キーと同じ値、NULL、0 を持つメンバー、またはメンバー キーの列にない値を持つメンバーは、(All) を除くトップレベルのメンバーと見なされます。  
  
 親子階層の深さは、その階層の分岐によって異なります。 つまり、親子階層は不均衡階層と見なされます。  
  
 エンド ユーザーに表示されるレベル数が階層内のレベル数によって決まるユーザー定義階層とは異なり、親子階層は、単一レベルの属性階層で定義され、この単一レベルの値によりユーザーに表示される複数レベルが生成されます。 表示レベルの数は、メンバー キーと親キーが格納されるディメンション テーブルの列の内容によって異なります。 レベルの数は、ディメンション テーブルのデータが変わると変化します。 詳細については、次を参照してください。[親子ディメンション](../../analysis-services/multidimensional-models/parent-child-dimension.md)、および[、親子階層内の属性](../../analysis-services/multidimensional-models/parent-child-dimension-attributes.md)です。  
  
## <a name="see-also"></a>参照  
 [ユーザー定義階層を作成します。](../../analysis-services/multidimensional-models/user-defined-hierarchies-create.md)   
 [ユーザー階層プロパティ](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)   
 [ディメンションの属性のプロパティの参照](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
