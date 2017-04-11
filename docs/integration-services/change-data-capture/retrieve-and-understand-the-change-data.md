---
title: "変更データを取得および理解する | Microsoft Docs"
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
  - "増分読み込み [Integration Services], データの取得"
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# 変更データを取得および理解する
  変更データの増分読み込みを実行する [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージのデータ フローにおいて、最初のタスクは、変更データを取得するクエリを実行することです。 このクエリは、データ フロー タスクの変換元コンポーネント内で実行します。 その後、下流にある変換や変換先を使用して、変更データを変換先に適用できます。  
  
> [!NOTE]  
>  テーブル値関数を含むクエリの作成は、変更データの増分読み込みを実行するパッケージを作成するプロセスにおける 3 番目の手順です。 このクエリの詳細については、「[変更データを取得する関数を作成する](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md)」を参照してください。 変更データの増分読み込みを実行するパッケージを作成するプロセス全体の説明については、「[変更データ キャプチャ &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)」を参照してください。  
  
## データ フロー タスクの追加  
 パッケージのデータ フローでは、変更データを取得し、行われた変更の種類に基づいて行を分割し、変更を変換先に適用します。  
  
#### データ フロー タスクをパッケージに追加するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[制御フロー]** タブで、データ フロー タスクを追加します。  
  
2.  クエリ文字列を準備した先行タスクをデータ フロー タスクに連結します。  
  
## 変更をクエリで取得するための変換元コンポーネントの構成  
 変換元コンポーネントは、変数に格納されている準備済みのクエリ文字列を使用して、変更データを取得するテーブル値関数を呼び出します。  
  
> [!NOTE]  
>  変数に格納されている準備済みのクエリ文字列の詳細については、「[変更データのクエリを準備する](../../integration-services/change-data-capture/prepare-to-query-for-the-change-data.md)」を参照してください。 変更データを取得するテーブル値関数の詳細については、「[変更データを取得する関数を作成する](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md)」を参照してください。  
  
#### 変更データを取得するように OLE DB ソースを構成するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の **[データ フロー]** タブで、OLE DB ソースを追加します。  
  
2.  **[OLE DB ソース エディター]** の **[接続マネージャー]** ページで、次のオプションを選択します。  
  
    1.  ソース データベースへの有効な接続を構成します。  
  
    2.  **[データ アクセス モード]** で **[変数からの SQL コマンド]** を選択します。  
  
    3.  **[変数名]** で **[User::SqlDataQuery]** を選択します。  
  
3.  **[OLE DB ソース エディター]** の **[列]** ページで、必要なすべての列が出力列にマップされていることを確認します。  
  
## 次の手順  
 変更データを取得するように OLE DB ソースを構成したら、次の手順で、パッケージのデータ フローのデザインを開始します。  
  
 **次のトピック:** [挿入、更新、および削除を処理する](../../integration-services/change-data-capture/process-inserts-updates-and-deletes.md)  
  
  