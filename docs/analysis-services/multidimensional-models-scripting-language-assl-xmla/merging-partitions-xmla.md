---
title: パーティションのマージ (XMLA) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 32c212ee7ffdfe234c5a4dd7760c32b0504ac38b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="merging-partitions-xmla"></a>パーティションのマージ (XMLA)
  使用してパーティションをマージするには、同じ集計デザインと構造のパーティションがある場合、 [MergePartitions](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md) XML for Analysis (XMLA) コマンド。 パーティション管理において、パーティションのマージは重要な操作です。日付によってパーティション分割された履歴データを含むパーティションの場合は特に重要です。  
  
 たとえば、次の 2 つのパーティションを使用する財務キューブがあるとします。  
  
-   1 つのパーティションは現在の年の財務データを表し、パフォーマンスのためにリアルタイム リレーショナル OLAP (ROLAP) ストレージ設定を使用します。  
  
-   もう 1 つのパーティションは過去の年の財務データを格納し、ストレージのために多次元 OLAP (MOLAP) ストレージ設定を使用します。  
  
 2 つのパーティションは異なるストレージ設定を使用しますが、集計デザインは同じものを使用します。 年の最後に履歴データの年の間で、キューブの処理ではなく、代わりに使用できます、 **MergePartitions**を過去の年は現在の年のパーティションにパーティションをマージするコマンド。 こうすれば、多くの時間をかけてキューブを詳細に処理しなくても、集計データを保持できます。  
  
## <a name="specifying-partitions-to-merge"></a>マージするパーティションの指定  
 ときに、 **MergePartitions**コマンドの実行で指定されたソース パーティションに格納された集計データ、[ソース](../../analysis-services/xmla/xml-elements-properties/source-element-xmla.md)プロパティで指定された対象パーティションに追加、[ターゲット](../../analysis-services/xmla/xml-elements-properties/target-element-xmla.md)プロパティです。  
  
> [!NOTE]  
>  **ソース**プロパティは、1 つ以上のパーティション オブジェクト参照を含めることができます。 ただし、**ターゲット**プロパティことはできません。  
  
 正常にマージする、両方で指定されたパーティションを**ソース**と**ターゲット**同じメジャー グループに含まれる必要があります、同じ集計デザインを使用します。 そうでない場合、エラーが発生します。  
  
 指定されたパーティション、**ソース**後に削除されます、 **MergePartitions**コマンドが正常に完了しました。  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>Description  
 次の例では、すべてのパーティション、 **Customer Counts**のメジャー グループ、 **Adventure Works**でキューブ、 **Adventure Works DW**サンプル[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]にデータベース、 **Customers_2004**パーティション。  
  
### <a name="code"></a>コード  
  
```  
<MergePartitions xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Sources>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2001</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2002</PartitionID>  
    </Source>  
    <Source>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2003</PartitionID>  
    </Source>  
  </Sources>  
  <Target>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2004</PartitionID>  
  </Target>  
</MergePartitions>  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
