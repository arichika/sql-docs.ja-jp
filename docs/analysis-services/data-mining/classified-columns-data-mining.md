---
title: "分類済みの列 (データ マイニング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コンテンツの種類 [データ マイニング]"
  - "STDEV 列"
  - "VARIANCE 列"
  - "PROBABLILITY 列"
  - "PROBABILITY_STDEV 列"
  - "列 [データ マイニング], 分類済み"
  - "分類済みの列 [データ マイニング]"
  - "PROBABILITY_VARIANCE 列"
  - "SUPPORT 列"
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 26
---
# 分類済みの列 (データ マイニング)
  分類済みの列を定義する場合は、マイニング構造内の現在の列と別の列の間でリレーションシップを作成します。 マイニング構造内で分類済みの列として指定した列のデータには、その構造内の別の列の値について説明した分類情報が含まれています。  
  
 たとえば、数値データを含んだ 2 つの列があるとします。一方の列 [Yearly Purchases] には、特定の暦年における顧客ごとの年間合計購入金額が格納され、もう一方の [Standard Deviations] 列には、これらの値の標準偏差が格納されます。 この場合、[Yearly Purchases] 列を分類済みの列に指定すると、モデルはこのリレーションシップを分析で使用できるようになります。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されているアルゴリズムでは、分類済みの列の使用がサポートされていません。この機能はカスタム アルゴリズムの作成用に提供されています。  
  
## 分類済みの列の定義  
 分類済みの列のデータ型は、**Long** または **Double** にする必要があります。  
  
 次の一覧では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で分類済みの列に対してサポートされているコンテンツの種類について説明します。  
  
 **PROBABILITY**  
 この列の値は、関連付けられている値の確率であり、0 から 1 までの数値です。  
  
 **VARIANCE**  
 この列の値は、関連付けられている値の分散です。  
  
 **[STDEV]**  
 この列の値は、関連付けられている値の標準偏差です。  
  
 **PROBABILITY_VARIANCE**  
 この列の値は、関連付けられている値の確率の分散です。  
  
 **PROBABILITY_STDEV**  
 この列の値は、関連付けられている値の確率の標準偏差です。  
  
 **SUPPORT**  
 この列の値は、関連付けられている値の重み (ケース レプリケーション係数) です。  
  
## 参照  
 [コンテンツの種類 (データ マイニング)](../../analysis-services/data-mining/content-types-data-mining.md)   
 [マイニング構造 (Analysis Services - データ マイニング)](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [データ型 (データ マイニング)](../../analysis-services/data-mining/data-types-data-mining.md)  
  
  