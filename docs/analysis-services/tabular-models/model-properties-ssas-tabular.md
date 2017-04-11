---
title: "モデルのプロパティ (SSAS テーブル) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.wspacedbconfig.f1"
  - "sql13.asvs.bidtoolset.fileprop.f1"
ms.assetid: 8ab04656-75a5-485c-9687-7b1ca49f7f80
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 30
---
# モデルのプロパティ (SSAS テーブル)
  このトピックでは、テーブル モデル プロパティについて説明します。 各テーブル モデル プロジェクトには、SQL Server 開発ツールで作成中のモデルの構築とバックアップの方法やワークスペース データベースの保存方法に影響するモデルのプロパティが含まれています。 ここで説明するモデルのプロパティは、既に配置されているモデルには適用されません。  
  
 このトピックのセクション:  
  
-   [モデルのプロパティ](#bkmk_model_properties)  
  
-   [モデル プロパティの設定の構成](#bkmk_conf_model_prop)  
  
##  <a name="bkmk_model_properties"></a> モデルのプロパティ  
 **詳細設定**  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**ビルド アクション**|コンパイル|このプロパティは、ビルドおよび配置プロセスとファイルとの関係を指定します。 このプロパティの設定には、以下のオプションがあります。<br /><br /> **コンパイル** – 通常のビルド アクションが行われます。 モデル オブジェクトの定義は、.asdatabase ファイルに書き込まれます。<br /><br /> **なし** – .asdatabase ファイルへの出力は空になります。|  
|**出力ディレクトリにコピー**|コピーしない|このプロパティは、ソース ファイルを出力ディレクトリにコピーするかどうかを指定します。 このプロパティの設定には、以下のオプションがあります。<br /><br /> **コピーしない** – コピーは出力ディレクトリに作成されません。<br /><br /> **常にコピーする** – コピーは出力ディレクトリに常に作成されます。<br /><br /> **新しい場合はコピーする** - model.bim ファイルが変更されている場合にのみ、コピーが出力ディレクトリに作成されます。|  
  
 **その他**  
  
> [!NOTE]  
>  モデルの作成時に自動的に設定され、変更できないプロパティもあります。  
  
> [!NOTE]  
>  ワークスペース サーバー、ワークスペースの保有期間、およびデータ バックアップの各プロパティには、新しいモデル プロジェクトを作成するときに既定の設定が適用されます。 [ツール] メニューから開く [オプション] ダイアログ ボックスで、[分析サーバー] 設定の [データ モデリング] ページを使用して、新しいモデルの既定の設定を変更できます。 他のプロパティと同様に、これらのプロパティは [プロパティ] ウィンドウでモデルごとに設定することもできます。 詳細については、「[既定のデータ モデルと配置プロパティの構成 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)」を参照してください。  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**照合順序**|Visual Studio がインストールされているコンピューターの既定の照合順序。|モデルの照合順序指定子。|  
|**互換性レベル**|既定またはプロジェクト作成時に選択した他のレベル|SQL Server 2012 Analysis Services SP1 以降に適用されます。 このモデルで利用できる機能と設定を指定します。 詳細については、「[Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。|  
|**データ バックアップ**|ディスクにバックアップしない|モデル データのバックアップをバックアップ ファイルに保存するかどうかを指定します。 このプロパティの設定には、以下のオプションがあります。<br /><br /> **ディスクにバックアップする** - モデル データのバックアップをディスク上に保持するように指定します。 モデルを保存すると、バックアップ (ABF) ファイルにもデータが保存されます。 このオプションを選択すると、モデルの保存と読み込みが低速化する可能性があります。<br /><br /> **ディスクにバックアップしない** - モデル データのバックアップをディスク上に保持しないように指定します。 保存時間とモデルの読み込み時間が最小限で済みます。<br /><br /> <br /><br /> このプロパティの既定の設定は、[ツール] メニューから開く [オプション] ダイアログ ボックスで、[分析サーバー] 設定の [データ モデリング] ページを使用して変更できます。|  
|**DirectQuery モード**|Off|このモデルを DirectQuery モードで動作させるかどうかを指定します。 詳細については、「[DirectQuery モード &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)」を参照してください。|  
|**[ファイル名]**|Model.bim|.bim ファイルの名前を指定します。 このファイル名は変更しないでください。|  
|**完全なパス**|プロジェクトを作成したときに指定したパス。|model.bim ファイルの場所。 このプロパティを [プロパティ] ウィンドウで設定することはできません。|  
|**言語**|英語|モデルの既定の言語。 既定の言語は Visual Studio の言語によって決まります。 このプロパティを [プロパティ] ウィンドウで設定することはできません。|  
|**ワークスペース データベース**|プロジェクト名の後にアンダースコア、GUID が続きます。|選択した model.bim ファイルに対するインメモリ モデルを格納および編集する際に使用されるワークスペース データベースの名前です。 このデータベースは、ワークスペース サーバー プロパティで指定された Analysis Services インスタンスに表示されます。 このプロパティを [プロパティ] ウィンドウで設定することはできません。 詳細については、「[ワークスペース データベース &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/workspace-database-ssas-tabular.md)」を参照してください。|  
|**ワークスペースの保有期間**|メモリからアンロード|モデルが閉じられた後でワークスペース データベースを保持する方法を指定します。 ワークスペース データベースには、モデル メタデータ、モデルにインポートされたデータ、および権限借用の資格情報 (暗号化) が含まれます。 場合によっては、ワークスペース データベースは非常に大きくなり、大量のメモリを消費することがあります。 既定では、ワークスペース データベースはメモリからアンロードされます。 この設定を変更するときには、使用可能なメモリ リソースと、モデルに対する作業を行う頻度を考慮することが重要です。 このプロパティの設定には、以下のオプションがあります。<br /><br /> **メモリに保持** - モデルを閉じた後もワークスペース データベースをメモリ内に保持するように指定します。 このオプションはより多くのメモリを消費しますが、モデルを開くときのリソース消費が少なくて済み、ワークスペース データベースの読み込みも高速になります。<br /><br /> **メモリからアンロード** - モデルを閉じた後、ワークスペース データベースをディスク上に保持し、メモリには残さないように指定します。 このオプションはメモリの消費量は比較的少なくて済みますが、モデルを開くときのリソース消費が増え、ワークスペース データベースをメモリ内に保持した場合と比べて、モデルの読み込みにも時間がかかるようになります。 メモリ内のリソースが制限されている場合、またはリモートのワークスペース データベースで作業する場合に、このオプションを使用します。<br /><br /> **ワークスペースの削除** - モデルを閉じた後、メモリからワークスペース データベースを削除し、ディスク上にもワークスペース データベースを保持しないように指定します。 このオプションはメモリとストレージ領域の消費量が比較的少なくて済みますが、モデルを開くときのリソース消費が増え、ワークスペース データベースをメモリ内やディスク上に保持した場合と比べて、モデルの読み込みにも時間がかかるようになります。 このオプションは、モデルに対する作業の頻度が低い場合に使用してください。<br /><br /> <br /><br /> このプロパティの既定の設定は、[ツール] メニューから開く [オプション] ダイアログ ボックスで、[分析サーバー] 設定の [データ モデリング] ページを使用して変更できます。|  
|**ワークスペース サーバー**|localhost|このプロパティは、モデルが作成されるときにワークスペース データベースをホストするのに使用される既定のサーバーを指定します。 ローカル コンピューターで実行されている Analysis Services の使用可能なすべてのインスタンスが、このボックスの一覧に表示されます。<br /><br /> このプロパティの既定の設定は、[ツール] メニューから開く [オプション] ダイアログ ボックスで、[分析サーバー] 設定の [データ モデリング] ページを使用して変更できます。<br /><br /> <br /><br /> 注: 常にローカル Analysis Services サーバーをワークスペース サーバーとして指定することをお勧めします。 リモート サーバー上のワークスペース データベースでは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] からのインポートはサポートされておらず、データはローカルにバックアップされず、クエリ中にユーザー インターフェイスで遅延が発生する場合があります。|  
  
##  <a name="bkmk_conf_model_prop"></a> モデル プロパティの設定の構成  
  
1.  SSDT の **ソリューション エクスプローラー**で、 **Model.bim** ファイルをクリックします。  
  
2.  **[プロパティ]** ウィンドウでプロパティをクリックし、値を入力するか、下矢印をクリックして、設定オプションを選択します。  
  
## 参照  
 [既定のデータ モデルと配置プロパティの構成 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [プロジェクトのプロパティ &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  