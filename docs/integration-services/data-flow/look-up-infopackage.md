---
title: "[インフォパッケージの参照] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c0cb7a4-cd07-44cc-85cb-eb1ad91f85fd
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# [インフォパッケージの参照]
  SAP Netweaver BW システムで定義されたインフォパッケージを参照する場合、 **[インフォパッケージの参照]** ダイアログ ボックスを使用します。 インフォパッケージの一覧が表示されたら、目的のインフォパッケージを選択します。変換先の関連するオプションに必要な値が設定されます。  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW の SAP BW 変換先は、 **[プロセス チェーンの参照]** ダイアログ ボックスを使用します。 SAP BW 変換先の詳細については、「 [SAP BW Destination](../../integration-services/data-flow/sap-bw-destination.md)」を参照してください。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW に関するドキュメントでは、SAP Netweaver BW 環境について理解していることを前提としています。 SAP Netweaver BW の詳細または SAP Netweaver BW オブジェクトやプロセスを構成する方法については、SAP のマニュアルを参照してください。  
  
 **[インフォパッケージの参照] ダイアログ ボックスを開くには**  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、SAP BW 変換先が含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを開きます。  
  
2.  **[データ フロー]** タブで、SAP BW 変換先をダブルクリックします。  
  
3.  **[SAP BW 変換先エディター]**で、 **[接続マネージャー]** をクリックして **[接続マネージャー]** ページを開きます。  
  
4.  **[接続マネージャー]** ページの **[インフォパッケージ/インフォソース]** で、**[参照]** をクリックして **[インフォパッケージの参照]** ダイアログ ボックスを表示します。  
  
## [参照] のオプション  
 参照フィールドで、アスタリスクのワイルドカード文字 (*) を使用して、または部分的な文字列をアスタリスクのワイルドカード文字と組み合わせて使用して、結果をフィルター処理できます。 ただし、参照フィールドを空にした場合、参照操作は、フィールドの空の文字列のみを検索します。  
  
 **インフォパッケージ**  
 参照するインフォパッケージの名前、または部分的な名前をアスタリスクのワイルドカード文字 (*) と入力します。 すべてのインフォパッケージを含めるには、アスタリスクのワイルドカード文字を単独で使用します。  
  
 **インフォソース**  
 インフォソースの名前、または部分的な名前をアスタリスクのワイルドカード文字 (*) と入力します。 インフォソースにかからわずすべてのインフォパッケージを含めるには、アスタリスクのワイルドカード文字を単独で使用します。  
  
 **転送元システム**  
 ソース システムの名前、または部分的な名前をアスタリスクのワイルドカード文字 (*) と入力します。 ソース システムにかからわずすべてのインフォパッケージを含めるには、アスタリスクのワイルドカード文字を単独で使用します。  
  
 **参照**  
 SAP Netweaver BW システムで定義されている一致するインフォパッケージを参照します。  
  
## 参照結果  
 [参照] ボタンをクリックすると、SAP Netweaver BW システムのインフォパッケージの一覧が、次の列見出しのテーブルに表示されます。  
  
 **インフォパッケージ**  
 SAP Netweaver BW システムで定義された InfoPackage の名前を表示します。  
  
 **型**  
 インフォパッケージの種類を表示します。 次の表に、種類として使用できる値の一覧を示します。  
  
|値|Description|  
|-----------|-----------------|  
|Trans.|トランザクション データ。|  
|Attr.|属性データ。|  
|テキスト|テキスト。|  
  
 **Description**  
 インフォパッケージの説明を表示します。  
  
 **インフォソース**  
 インフォパッケージに関連付けられているインフォソースの名前を表示します (ある場合)。  
  
 **転送元システム**  
 ソース システムの名前を表示します。  
  
 インフォパッケージの一覧が表示されたら、目的のインフォパッケージを選択します。変換先の関連するオプションに必要な値が設定されます。  
  
## 参照  
 [SAP BW 変換先エディター ([接続マネージャー] ページ)](../Topic/SAP%20BW%20Destination%20Editor%20\(Connection%20Manager%20Page\).md)   
 [Microsoft Connector for SAP BW の F1 ヘルプ](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  