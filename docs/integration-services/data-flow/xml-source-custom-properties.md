---
title: "XML 入力元のカスタム プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb29b28c-3159-41ec-b3d7-fce5b2f2be55
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# XML 入力元のカスタム プロパティ
  XML ソースには、カスタム プロパティと、すべてのデータ フロー コンポーネントとの共通プロパティの両方があります。  
  
 次の表は、XML ソースのカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer|XML データへのアクセスに使用するモード。|  
|UseInlineSchema|ブール値|XML ソース内のインライン スキーマ定義を使用するかどうかを示す値。 このプロパティの既定値は **False**です。|  
|XMLData|文字列|XML データを取得するファイルまたは変数。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
|XMLSchemaDefinition|文字列|スキーマ定義ファイル (.xsd) のパスおよびファイル名。<br /><br /> このプロパティの値は、プロパティ式を使用して指定することができます。|  
  
 次の表は、XML ソースの出力のカスタム プロパティを示しています。 すべてのプロパティは読み取り/書き込み可能です。  
  
|プロパティ名|データ型|Description|  
|-------------------|---------------|-----------------|  
|RowsetID|文字列|出力に関連付けられた行セットを識別する値。|  
  
 XML ソースの出力列には、カスタム プロパティがありません。  
  
 詳細については、「[XML ソース](../../integration-services/data-flow/xml-source.md)」を参照してください。  
  
## 参照  
 [共通プロパティ](../Topic/Common%20Properties.md)  
  
  