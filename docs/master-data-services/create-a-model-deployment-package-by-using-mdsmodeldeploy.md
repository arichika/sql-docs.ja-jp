---
title: "MDSModelDeploy を使用したモデルの配置パッケージの作成 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2687e39-dc20-494f-a707-2aa29f4c329e
caps.latest.revision: 13
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 13
---
# MDSModelDeploy を使用したモデルの配置パッケージの作成
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] では、MDSModelDeploy ツールを使用して、パッケージを作成します。 指定するコマンドに応じて、次のどちらかを含むパッケージを作成できます。  
  
-   モデル オブジェクトのみ。  
  
-   モデル オブジェクトとデータ。  
  
 モデル オブジェクトのみを含むパッケージを配置する必要がある場合は、代わりに、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションのモデル配置ウィザードを使用できます。 詳細については、「[ウィザードを使用したモデルの配置パッケージの作成](../master-data-services/create-a-model-deployment-package-by-using-the-wizard.md)」を参照してください。  
  
## 前提条件  
 この手順を実行するには  
  
1.  MDSModelDeploy ツールを実行するために必要な基本的な権限は、次のとおりです。  
  
    -   MDS 構成マネージャー (Windows の管理者) と同じ Windows 権限  
  
    -   MDS データベースに対する DBA 権限  
  
2.  MDSModelDeploy ツールを使用してパッケージを作成するために必要な権限は、次のとおりです。  
  
    -   データ モデルに対する MDS モデル管理者権限  
  
    -   MDS ImportExport 機能領域権限  
  
3.  MDSModelDeploy ツールを使用してモデルを配置するために必要な権限は、次のとおりです。  
  
    -   MDS エクスプローラー機能権限  
  
    -   MDS システム管理機能権限  
  
4.  MDSModelDeploy ツールを使用してモデルをリストするために必要な権限は、次のとおりです。  
  
    -   MDS エクスプローラー機能権限  
  
    -   リスト内のモデルを表示するための、データ モデルに対する MDS モデル管理権限  
  
 モデルのパッケージを作成するには、そのモデルが存在する必要があります。 詳細については、「[モデルを作成する (マスター データ サービス)](../master-data-services/create-a-model-master-data-services.md)」を参照してください。  
  
 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### MDSModelDeploy を使用してモデルの配置パッケージを作成するには  
  
1.  管理者のコマンド プロンプトを開きます。  
  
2.  MDSModelDeploy.exe がある場所に移動します。  
  
    -   MDS を既定の場所にインストールした場合、ファイルは \<*ドライブ*>:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration にあります。  
  
    -   MDS を既定の場所にインストールしなかった場合は、ローカル コンピューター内で MDSModelDeploy.exe を検索します。  
  
3.  省略可。 オプションおよびヘルプを表示します。  
  
    -   使用可能なすべてのオプションを表示するには、「`MDSModelDeploy`」と入力し、Enter キーを押します。  
  
    -   オプションのヘルプを表示するには、「`MDSModelDeploy help OptionName`」と入力します。*OptionName* はオプションの名前です。  
  
4.  省略可。 Web アプリケーションが複数ある場合、次のコマンドを入力し、Enter キーを押して、配置するサービスの名前を確認します。  
  
    ```  
    MDSModelDeploy listservices  
    ```  
  
     値の一覧が返されます (例: `MDS1, Default Web Site, MDS`)。 モデルを配置するには、この一覧の最初の値 (この例では、`MDS1`) が必要です。  
  
5.  モデル オブジェクトとデータを含むパッケージを作成するには、次のコマンドを入力します。*ModelName*、*VersionName*、*ServiceName*、および *PackageName* は、それぞれモデル、バージョン、サービス、および .pkg 出力ファイルの名前です。  
  
    ```  
    MDSModelDeploy createpackage -model ModelName -version VersionName -service ServiceName -package PackageName -includedata  
    ```  
  
     データを含める必要がない場合は、`-version` スイッチと `-includedata` スイッチを使用しないでください。  
  
6.  Enter キーを押します。 パッケージが正常に作成されると、「MDSModelDeploy 操作は正常に完了しました」というメッセージが表示されます。  
  
## 次の手順  
  
-   [MDSModelDeploy を使用したモデルの配置パッケージの配置](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)  
  
## 参照  
 [モデル配置オプション (マスター データ サービス)](../master-data-services/model-deployment-options-master-data-services.md)   
 [モデルの配置 (マスター データ サービス)](../master-data-services/deploying-models-master-data-services.md)  
  
  