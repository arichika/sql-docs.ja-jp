---
title: "DAX のプロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aa928dc5-d00d-4f8a-80b9-7e6973d2196c
caps.latest.revision: 6
author: "HeidiSteen"
ms.author: "heidist"
manager: "erikre"
caps.handback.revision: 6
---
# DAX のプロパティ
   msmdsrv.ini の DAX セクションには、DAX クエリの結果セットで返される行数の上限など、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の特定のクエリの動作を制御する設定が含まれています。 
  
  巨大な行セットについては、DirectQuery モデルで返される行数など、既定の 100 万行では不十分である場合があります。 上限の調整が必要であるかどうかは、"The result set of a query to external data source has exceeded the maximum allowed size of '1000000' rows (外部データ ソースへのクエリの結果セットが許可されている最大サイズである '1000000' 行を超えています)" というエラーが発生することでわかります。
 
上限を増やすには、**MaxIntermediateRowSize** 構成設定を指定します。 構成ファイルの DAX セクションに全要素を手動で追加する必要があります。 追加するまで設定はファイル内に存在しません。
  
## 構成スニペット

```
<ConfigurationSettings>
. . .
<DAX>   
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . . 
```

## プロパティの説明

設定 |値 |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | DAX クエリで返される最大行数。 既定値が小さすぎる場合は、このエントリを手動で msmdsrv.ini ファイルに追加し、値を増やします。 
PredicateCheckSpoolCardinalityThreshold| 5000 | 高度なプロパティであるため、マイクロソフトのサポート下でのみ変更してください。

その他のサーバー プロパティとその設定方法の詳細については、「[Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。 