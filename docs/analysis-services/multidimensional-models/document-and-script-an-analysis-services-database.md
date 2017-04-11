---
title: "Analysis Services データベースのドキュメントとスクリプトの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML for Analysis, スクリプト"
  - "XMLA, スクリプト"
  - "スクリプト [Analysis Services], データベース"
  - "データベースのドキュメントの作成"
  - "データベース [Analysis Services], ドキュメント"
  - "データベース [Analysis Services], スクリプト"
ms.assetid: 125044e2-8d36-4733-8743-8bb68ff9aa4e
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 35
---
# Analysis Services データベースのドキュメントとスクリプトの作成
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを配置した後、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、データベースのメタデータまたはデータベースに含まれているオブジェクトのメタデータを XML for Analysis (XMLA) スクリプトとして出力できます。 このスクリプトは、新しい **[XMLA クエリ エディター]** ウィンドウ、ファイル、またはクリップボードに出力できます。 XMLA の詳細については、「[Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)」を参照してください。  
  
 生成された XMLA スクリプトでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] スクリプト言語 (ASSL) の要素を使用して、スクリプトに含まれるオブジェクトを定義します。 CREATE スクリプトを生成した場合、結果として得られる XMLA スクリプトには、インスタンスで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース構造全体を作成するための XMLA **Create** コマンドおよび ASSL 要素が含まれます。 ALTER スクリプトを生成した場合、結果として得られる XMLA スクリプトには、既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの構造をスクリプト作成時点のデータベースの状態に復元するための XMLA **Alter** コマンドおよび ASSL 要素が含まれます。  
  
 生成された XMLA スクリプトは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースから以下のようなさまざまな用途に使用できます。  
  
-   すべてのデータベース オブジェクトおよび権限を再作成するためのバックアップ スクリプトを維持できます。  
  
-   データベース開発コードを作成または更新できます。  
  
-   既存のスキーマからテスト環境または開発環境を作成できます。  
  
## 参照  
 [Analysis Services データベースの変更または削除](../../analysis-services/multidimensional-models/modify-or-delete-an-analysis-services-database.md)   
 [Alter 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)   
 [Create 要素 (XMLA)](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)  
  
  