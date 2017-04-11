---
title: "行サンプリング変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.rowsamplingtrans.f1"
helpviewer_keywords: 
  - "サンプリング シード [Integration Services]"
  - "ランダム シード"
  - "ランダム サンプリング"
  - "サンプル データセット [Integration Services]"
  - "行サンプリング変換"
  - "パッケージ [Integration Services], サンプル"
  - "データセット [Integration Services], サンプル"
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# 行サンプリング変換
  行サンプリング変換を使用すると、入力データセットからランダムに選択されたサブセットを取得できます。 出力サンプルの正確なサイズを指定したり、乱数ジェネレーターのシード値を指定できます。  
  
 ランダム サンプリング用のアプリケーションには、多くの種類があります。 たとえば、ある会社がくじ引きを行って、ランダムに選択された 50 人の社員を当選者とする場合、社員データベースに対して行サンプリング変換を行い、正確な数の当選者を生成できます。  
  
 また、行サンプリング変換は、パッケージの開発中にサイズは小さいが標本化されたデータセットを作成する際に便利です。 十分に標本化されたデータがあれば、パッケージの実行とデータ変換のテストを行うことができます。この場合、完全なデータセットではなくランダム サンプルを使用するため、より迅速にテストできます。 テスト パッケージで使用されるサンプル データセットは常に同じサイズであるため、サンプル サブセットを使用することで、パッケージのパフォーマンスの問題をより簡単に判別することもできます。  
  
 この変換は、比率サンプリング変換と同様です。ただし、比率サンプリング変換は、入力行数の比率を選択してサンプル データセットを作成します。 「[比率サンプリング変換](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)」をご覧ください。  
  
## 行サンプリング変換の構成  
 行サンプリング変換は、指定された数の変換入力行を選択してサンプル データセットを作成します。 変換入力からの行の選択はランダムに行われるため、結果サンプルは入力の標本となります。 乱数ジェネレーターで使用するシード値を指定すると、変換による行の選択方法を制御することもできます。  
  
 同じ変換入力で同じランダム シードを使用すると、常に同じサンプル出力が作成されます。 シードを指定しない場合、この変換はオペレーティング システムのティック数を使用して乱数を作成します。 したがって、パッケージの開発およびテスト中に変換結果を確認するためにテスト中は同じシード値を使用し、パッケージの実稼働時にランダム シードへ変更することができます。  
  
 行サンプリング変換には、**SamplingValue** カスタム プロパティがあります。 このプロパティは、パッケージの読み込み時にプロパティ式で更新できます。 詳細については、「[Integration Services &#40;SSIS&#41; の式](../../../integration-services/expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../../integration-services/expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)」をご覧ください。  
  
 この変換は、1 つの入力と 2 つの出力をとります。 エラー出力はありません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[行サンプリング変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「[行サンプリング変換エディター &#40;[サンプリング] ページ&#41;](../Topic/Row%20Sampling%20Transformation%20Editor%20\(Sampling%20Page\).md)」をご覧ください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、次のトピックを参照してください。  
  
## 関連タスク  
 [データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)  
  
  