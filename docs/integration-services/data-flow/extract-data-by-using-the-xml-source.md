---
title: "XML ソースを使用してデータを抽出する | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "データの抽出 [Integration Services]"
  - "ソース [Integration Services], XML"
  - "XML ソース [Integration Services]"
ms.assetid: 5d5be54c-2b7e-4957-9193-c5ea5c5d6d15
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# XML ソースを使用してデータを抽出する
  XML ソースを追加して構成するには、パッケージに 1 つ以上のデータ フロー タスクがあらかじめ含まれている必要があります。  
  
### XML ソースを使用してデータを抽出するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[データ フロー]** タブをクリックし、次に **[ツールボックス]** で、XML ソースをデザイン画面にドラッグします。  
  
4.  XML ソースをダブルクリックします。  
  
5.  **[XML ソース エディター]** の **[接続マネージャー]** ページで、データ アクセス モードを次のうちから選択します。  
  
    -   **[XML ファイルの場所]** アクセス モードでは、**[参照]** をクリックし、XML ファイルが含まれるフォルダーを探します。  
  
    -   **[変数からの XML ファイル]** アクセス モードでは、XML ファイルのパスが含まれるユーザー定義変数を選択します。  
  
    -   **[変数からの XML データ]** アクセス モードでは、XML データが含まれるユーザー定義変数を選択します。  
  
    > [!NOTE]  
    >  変数は、XML ソースが含まれるデータ フロー タスクのスコープ内、またはパッケージのスコープ内で定義する必要があります。また、変数は文字列データ型である必要があります。  
  
6.  必要に応じて、**[インライン スキーマを使用する]** を選択し、スキーマ情報が含まれる XML ドキュメントを指定します。  
  
7.  XML ファイルに対して、外部の XML Schema Definition Language (XSD) スキーマを指定するには、次のいずれかの操作を行います。  
  
    -   **[参照]** をクリックして既存の XSD ファイルを探します。  
  
    -   **[XSD の生成]** をクリックして、XML ファイルから XSD を作成します。  
  
8.  出力列の名前を更新するには、**[列]** をクリックし、**[出力列]** 一覧の値を編集します。  
  
9. エラー出力を構成するには、 **[エラー出力]**をクリックします。 詳細については、「[データ フロー コンポーネントでエラー出力を構成する](../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)」を参照してください。  
  
10. **[OK]**をクリックします。  
  
11. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## 参照  
 [XML ソース](../../integration-services/data-flow/xml-source.md)   
 [Integration Services の変換](../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Integration Services のパス](../../integration-services/data-flow/integration-services-paths.md)   
 [[データ フロー タスク]](../../integration-services/control-flow/data-flow-task.md)  
  
  