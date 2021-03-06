---
title: AMO データ マイニング クラス |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 803e6738fc526f68b8937efaa2b65be1b7d30dc4
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="amo-data-mining-classes"></a>AMO データ マイニング クラス
  データ マイニング クラスは、データ マイニング オブジェクトの作成、変更、削除、および処理を行うのに役立ちます。 データ マイニング オブジェクトでの作業には、データ マイニング構造の作成、データ マイニング モデルの作成、およびモデルの処理が含まれます。  
  
 詳細方法については、環境を設定して約<xref:Microsoft.AnalysisServices.Server>、 <xref:Microsoft.AnalysisServices.Database>、 <xref:Microsoft.AnalysisServices.DataSource>、および<xref:Microsoft.AnalysisServices.DataSourceView>、オブジェクトを参照してください[AMO 基礎クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)です。  
  
 分析管理オブジェクト (AMO) でオブジェクトを定義するには、各オブジェクトで多くのプロパティを設定し、正しいコンテキストを設定する必要があります。 OLAP やデータ マイニング オブジェクトなどの複雑なオブジェクトには、長くて詳細なコーディングが必要となります。  
  
 このトピックには、次のセクションが含まれます。  
  
-   [MiningStructure オブジェクト](#MiningStructure)  
  
-   [MiningModel オブジェクト](#MiningModel)  
  
 次の図は、このトピックで説明するクラスの関係を示しています。  
  
 ![AMO データ マイニング クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-dataminingclasses.gif "AMO データ マイニング クラス")  
  
##  <a name="MiningStructure"></a> MiningStructure オブジェクト  
 マイニング構造はマイニング モデルのコンテナーです。 この構造では、マイニング モデルが使用する可能性のあるすべての列を定義します。 各マイニング モデルでは、構造で定義された列のセットから独自の列を定義します。  
  
 簡単な <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトは、基本情報、データ ソース ビュー、1 つ以上の <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>、0 個以上の <xref:Microsoft.AnalysisServices.TableMiningStructureColumn>、および <xref:Microsoft.AnalysisServices.MiningModelCollection> で構成されます。  
  
 基本情報には、<xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトの名前および ID (内部識別子) が含まれます。  
  
 <xref:Microsoft.AnalysisServices.DataSourceView> オブジェクトは、マイニング構造の基になるデータ モデルを保持します。  
  
 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> は、それぞれが単一の値を持つ列または属性です。  
  
 <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> は、それぞれの場合について複数の値を持つ列または属性です。  
  
 <xref:Microsoft.AnalysisServices.MiningModelCollection> には、同じデータ上に作成されたすべてのマイニング モデルが含まれます。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを作成するには、データベースの <xref:Microsoft.AnalysisServices.MiningStructureCollection> に新しいオブジェクトを追加した後、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを更新します。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを削除するには、<xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトの Drop メソッドを使用します。 コレクションから <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを削除してもサーバーには影響を与えません。  
  
 <xref:Microsoft.AnalysisServices.MiningStructure> は、独自の処理メソッドを使用して処理するか、親オブジェクトがそれ自体を独自の処理メソッドで処理する際に処理することができます。  
  
### <a name="columns"></a>列  
 列は、モデルのデータを保持し、その用途により、異なる種類、つまり Key、Input、Predictable、または InputPredictable となることができます。 Predictable 列はマイニング モデルを構築する対象です。  
  
 単一の値の列は、AMO では <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> と呼ばれます。 複数の値の列は、<xref:Microsoft.AnalysisServices.TableMiningStructureColumn> と呼ばれます。  
  
#### <a name="scalarminingstructurecolumn"></a>ScalarMiningStructureColumn  
 簡単な <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> オブジェクトは、基本情報、型、コンテンツ、およびデータ バインドで構成されます。  
  
 基本情報には、<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> の名前および ID (内部識別子) が含まれます。  
  
 型は、値のデータ型で、LONG、BOOLEAN、TEXT、DOUBLE、DATE があります。  
  
 コンテンツは、列をどのようにモデル化できるかをエンジンに指示します。 値として、Discrete、Continuous、Discretized、Ordered、Cyclical、Probability、Variance、StdDev、ProbabilityVariance、ProbabilityStdDev、Support、Key を取ることができます。  
  
 データ バインドは、データ ソース ビュー要素を使用して、データ マイニング列を基になるデータ モデルにリンクします。  
  
 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> を作成するには、親 <xref:Microsoft.AnalysisServices.MiningStructureCollection> に新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上で親 <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを更新します。  
  
 削除する、 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>、親のコレクションから削除する必要があります<xref:Microsoft.AnalysisServices.MiningStructure>、および親<xref:Microsoft.AnalysisServices.MiningStructure>オブジェクトは、Update メソッドを使用して、サーバーに更新する必要があります。  
  
#### <a name="tableminingstructurecolumn"></a>TableMiningStructureColumn  
 簡単な <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> オブジェクトは、基本情報とスカラー列で構成されます。  
  
 基本情報には、<xref:Microsoft.AnalysisServices.TableMiningStructureColumn> の名前および ID (内部識別子) が含まれます。  
  
 スカラー列は <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> です。  
  
 <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> を作成するには、親 <xref:Microsoft.AnalysisServices.MiningStructure> コレクションに新しいオブジェクトを追加した後、Update メソッドを使用して、サーバー上で親 <xref:Microsoft.AnalysisServices.TableMiningStructureColumn> オブジェクトを更新します。  
  
 <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> を削除するには、親 <xref:Microsoft.AnalysisServices.MiningStructure> のコレクションからこれを削除し、Update メソッドを使用して、サーバー上で親 <xref:Microsoft.AnalysisServices.MiningStructure> オブジェクトを更新する必要があります。  
  
##  <a name="MiningModel"></a> MiningModel オブジェクト  
 <xref:Microsoft.AnalysisServices.MiningModel> は、使用する構造の列、使用するアルゴリズム、およびモデルをチューニングする特定のオプション パラメーターを選択できるオブジェクトです。 たとえば、同じアルゴリズムを使用する同じマイニング構造で、いくつかのマイニング モデルを定義したいが、1 つのモデルのマイニング構造のいくつかの列を無視し、これらを別のモデルで入力として使用し、第 3 のモデルでこれらを入力および予測として使用したいという場合があります。 このオブジェクトは、1 つのマイニング モデルで列を連続的なものとして扱い、別のモデルでこの列を分離されているものとして扱う場合に便利です。  
  
 簡単な <xref:Microsoft.AnalysisServices.MiningModel> オブジェクトは、基本情報、アルゴリズム定義、および、いくつかの列で構成されます。  
  
 基本情報には、マイニング モデルの名前および ID (内部識別子) が含まれます。  
  
 アルゴリズム定義は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] で指定された標準アルゴリズムのいずれか 1 つ、または、サーバーで有効な任意のカスタム アルゴリズムを参照します。  
  
 いくつかの列とは、アルゴリズムおよび使用方法の定義によって使用される列のコレクションです。  
  
 <xref:Microsoft.AnalysisServices.MiningModel> を作成するには、データベースの <xref:Microsoft.AnalysisServices.MiningModelCollection> に新しいオブジェクトを追加した後、Update メソッドを使用してサーバー上で <xref:Microsoft.AnalysisServices.MiningModel> オブジェクトを更新します。  
  
 <xref:Microsoft.AnalysisServices.MiningModel> を削除するには、<xref:Microsoft.AnalysisServices.MiningModel> の Drop メソッドを使用します。 コレクションから <xref:Microsoft.AnalysisServices.MiningModel> を削除してもサーバーには影響を与えません。  
  
 <xref:Microsoft.AnalysisServices.MiningModel> は、作成後、独自の処理メソッドを使用して処理するか、親オブジェクトがそれ自体を独自の処理メソッドで処理する際に処理することができます。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices>   
 [AMO 基礎クラス](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-fundamental-classes.md)   
 [AMO データ マイニング オブジェクトのプログラミング](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-data-mining-objects.md)   
 [AMO クラスの概要](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [論理アーキテクチャと #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)   
 [データベース オブジェクト & #40 です。Analysis Services - 多次元データ & #41;](../../../analysis-services/multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md)  
  
  
