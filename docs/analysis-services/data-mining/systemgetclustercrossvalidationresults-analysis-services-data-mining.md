---
title: "SystemGetClusterCrossValidationResults (Analysis Services - データ マイニング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SystemGetClusterCrossValidationResults"
  - "データ マイニングであるストアド プロシージャ [Analysis Services]"
  - "相互検証 [データ マイニング]"
ms.assetid: 79de9b81-9f2e-4f20-ace9-e3b19d6a9759
caps.latest.revision: 21
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 21
---
# SystemGetClusterCrossValidationResults (Analysis Services - データ マイニング)
  指定した数の複数のセクションにマイニング構造をパーティション分割し、各パーティションに対してモデルをトレーニングして、各パーティションの精度の基準を返します。  
  
 **注** このストアド プロシージャは、少なくとも 1 つのクラスター モデルが含まれているマイニング構造でのみ使用できます。 非クラスター モデルをクロス検証するには、[SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md) を使用する必要があります。  
  
## 構文  
  
```  
  
SystemGetClusterCrossValidationResults(  
<structure name>,   
[,<mining model list>]  
,<fold count>}  
,<max cases>  
<test list>])  
```  
  
## 引数  
 *マイニング構造 (mining structure)*  
 現在のデータベースのマイニング構造の名前。  
  
 (必須)  
  
 *マイニング モデルの一覧 (mining model list)*  
 検証するマイニング モデルのコンマ区切りの一覧。  
  
 マイニング モデルの一覧を指定しないと、指定した構造に関連付けられたすべてのクラスター モデルに対してクロス検証が実行されます。  
  
> [!NOTE]  
>  クラスター モデルではないモデルをクロス検証するには、[SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md) という別のストアド プロシージャを使用する必要があります。  
  
 (省略可能)  
  
 *フォールド カウント (fold count)*  
 データセットを分割するパーティションの数を指定する整数。 最小値は、2 です。 フォールドの最大数は、 **maximum integer** とケース数のいずれか小さい方になります。  
  
 各パーティションには、*ケースの最大数*/*フォールド カウント*とほぼ同じ数のケースが含まれます。  
  
 既定値はありません。  
  
> [!NOTE]  
>  フォールドの数は、クロス検証の実行に必要な時間に大きく影響します。 選択する数が大きすぎると、クエリの実行時間が非常に長くなる可能性があります。また、場合によっては、サーバーが応答しなくなったり、タイムアウトする可能性があります。  
  
 (必須)  
  
 *ケースの最大数 (max cases)*  
 テストできるケースの最大数を指定する整数。  
  
 値に 0 を指定すると、データ ソース内のすべてのケースが使用されます。  
  
 データセット内の実際のケース数より大きい数字を指定すると、データ ソース内のすべてのケースが使用されます。  
  
 (必須)  
  
 *テスト リスト (test list)*  
 テスト オプションを指定する文字列。  
  
 **注** このパラメーターは将来使用するために予約されています。  
  
 (省略可能)  
  
## 戻り値の型  
 戻り値の型のテーブルには、個別のパーティションのスコアと、すべてのモデルの集計が含まれます。  
  
 次の表は、返される列を示しています。  
  
|列名|Description|  
|-----------------|-----------------|  
|ModelName|テストされたモデルの名前。|  
|AttributeName|予測可能列の名前。 クラスター モデルでは、常に **null**になります。|  
|AttributeState|予測可能列で指定した対象の値。 クラスター モデルでは、常に **null.**|  
|PartitionIndex|結果が適用されるパーティションを識別する、1 から始まるインデックス。|  
|PartitionSize|各パーティションに含まれていたケースの数を示す整数。|  
|テスト|実行されたテストの種類。|  
|[メジャー]|テストから返されたメジャーの名前。 各モデルのメジャーは、予測可能な値の型によって異なります。 各メジャーの定義については、「[相互検証 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/cross-validation-analysis-services-data-mining.md)」をご覧ください。<br /><br /> 予測可能な型ごとに返されるメジャーの一覧については、「[相互検証レポートのメジャー](../../analysis-services/data-mining/measures-in-the-cross-validation-report.md)」をご覧ください。|  
|値|指定したテスト メジャーの値。|  
  
## 解説  
 データ セット全体の精度の基準を返すには、[SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md) を使用します。  
  
 また、既にマイニング モデルをフォールドにパーティション分割している場合は、[SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md) を使用して、処理を省略し、クロス検証の結果のみを返すことができます。  
  
## 使用例  
 次の例では、マイニング構造を 3 つのフォールドにパーティション分割し、マイニング構造に関連付けられている 2 つのクラスター モデルをテストする方法を示します。  
  
 コードの 3 行目では、テストする特定のマイニング モデルの一覧を指定します。 一覧を指定しない場合、構造に関連付けられているすべてのクラスター モデルが使用されます。  
  
 コードの 4 行目ではフォールドの数を指定し、5 行目では使用するケースの最大数を指定しています。  
  
 これらはクラスター モデルであるため、予測可能な属性または値を指定する必要はありません。  
  
```  
CALL SystemGetClusterCrossValidationResults(  
[v Target Mail],  
[Cluster 1], [Cluster 2],  
3,  
10000  
)  
```  
  
 サンプルの結果 :  
  
|ModelName|AttributeName|AttributeState|PartitionIndex|PartitionSize|テスト|[メジャー]|値|  
|---------------|-------------------|--------------------|--------------------|-------------------|----------|-------------|-----------|  
|クラスター 1|||1|3025|クラスター|ケースの確率値|0.930524511864121|  
|クラスター 1|||2|3025|クラスター|ケースの確率値|0.919184178430778|  
|クラスター 1|||3|3024|クラスター|ケースの確率値|0.929651120490248|  
|Cluster 2|||1|1289|クラスター|ケースの確率値|0.922789726933607|  
|Cluster 2|||2|1288|クラスター|ケースの確率値|0.934865535691068|  
|Cluster 2|||3|1288|クラスター|ケースの確率値|0.924724595688798|  
  
## 必要条件  
 クロス検証は、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssEnterprise](../../includes/ssenterprise-md.md)] でのみ使用できます。  
  
## 参照  
 [SystemGetCrossValidationResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetcrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetaccuracyresults-analysis-services-data-mining.md)   
 [SystemGetClusterCrossValidationResults](../../analysis-services/data-mining/systemgetclustercrossvalidationresults-analysis-services-data-mining.md)   
 [SystemGetClusterAccuracyResults (Analysis Services - データ マイニング)](../../analysis-services/data-mining/systemgetclusteraccuracyresults-analysis-services-data-mining.md)  
  
  