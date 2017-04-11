---
title: "パッケージ実行タスク エディター | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.executepackagetask.package.f1"
  - "sql13.dts.designer.executepackagetask.parameter.F1"
  - "sql13.dts.designer.executepackagetask.general.f1"
ms.assetid: c2c96b4f-eb10-4d8b-be34-88edfd0785fb
caps.latest.revision: 7
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 7
---
# パッケージ実行タスク エディター
  パッケージ実行タスクを構成するには、パッケージ実行タスク エディターを使用します。 パッケージ実行タスクは、パッケージのワークフローの一部として他のパッケージを実行できるようにすることで、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のエンタープライズ用機能を拡張します。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [パッケージ実行タスク エディターを開く](#open)  
  
-   [[全般] ページのオプションを設定する](#general)  
  
-   [[パッケージ] ページのオプションを設定する](#package)  
  
-   [[パラメーター バインド] ページのオプションを設定する](#parameter)  
  
##  <a name="open"></a> パッケージ実行タスク エディターを開く  
  
1.  パッケージ実行タスクが含まれる [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] で開きます。  
  
2.  SSIS デザイナーでタスクを右クリックし、**[編集]** をクリックします。  
  
##  <a name="general"></a> [全般] ページのオプションを設定する  
 **名前**  
 パッケージ実行タスクの一意な名前を指定します。 この名前は、タスク アイコンのラベルとして使用されます。  
  
> [!NOTE]  
>  タスク名はパッケージ内で一意である必要があります。  
  
 **Description**  
 パッケージ実行タスクの説明を入力します。  
  
##  <a name="package"></a> [パッケージ] ページのオプションを設定する  
 **ReferenceType**  
 プロジェクト内の子パッケージの場合は **[プロジェクト参照]** をクリックします。 パッケージの外部にある子パッケージの場合は **[外部参照]** をクリックします。  
  
> [!NOTE]  
>  **[ReferenceType]** オプションは読み取り専用であり、対象パッケージを含むプロジェクトがプロジェクト配置モデルに変換されていない場合は **[外部参照]** に設定されます。 変換の詳細については、「[Integration Services サーバーへのプロジェクトの配置](../../integration-services/packages/deploy-projects-to-integration-services-server.md)」を参照してください。  
  
 **Password**  
 子パッケージがパスワードで保護されている場合は、子パッケージのパスワードを入力するか、参照ボタン ([...]) をクリックして子パッケージの新しいパスワードを作成します。  
  
 **ExecuteOutOfProcess**  
 子パッケージが親パッケージのプロセス内で実行するか、または別のプロセスで実行するかを指定します。 既定では、パッケージ実行タスクの ExecuteOutOfProcess プロパティは **False** に設定されるので、子パッケージは親パッケージと同じプロセス内で実行されます。 このプロパティを **true** に設定すると、子パッケージは別のプロセスで実行されます。 これにより、子パッケージの起動が遅くなる場合があります。 また、プロパティを **true** に設定した場合、ツールのみのインストールではパッケージをデバッグできません。[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 製品をインストールする必要があります。 詳細については、「[Integration Services のインストール](../../integration-services/install-windows/install-integration-services.md)」を参照してください。  
  
### [ReferenceType] の動的オプション  
  
#### ReferenceType = 外部参照  
 **場所**  
 子パッケージの場所を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**SQL Server**|場所を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに設定します。|  
|**ファイル システム**|場所をファイル システムに設定します。|  
  
 **接続**  
 子パッケージの格納場所の種類を選択します。  
  
 **PackageNameReadOnly**  
 パッケージ名が表示されます。  
  
#### ReferenceType = プロジェクト参照  
 **PackageNameFromProjectReference**  
 プロジェクトに含まれるパッケージで子パッケージにするものを選択します。  
  
### [Location] の動的オプション  
  
#### Location = SQL Server  
 **接続**  
 OLE DB 接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [OLE DB 接続マネージャー](../../integration-services/connection-manager/ole-db-connection-manager.md)、[OLE DB 接続マネージャーの構成](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **PackageName**  
 子パッケージの名前を入力するか、[...] をクリックし、パッケージを指定します。  
  
#### Location = ファイル システム  
 **接続**  
 ファイル接続マネージャーを一覧から選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
 **PackageNameReadOnly**  
 パッケージ名が表示されます。  
  
##  <a name="parameter"></a> [パラメーター バインド] ページのオプションを設定する  
 親パッケージまたはプロジェクトから子パッケージに値を渡すことができます。 プロジェクトはプロジェクト配置モデルを使用し、子パッケージが親パッケージと同じプロジェクトに含まれている必要があります。  
  
 プロジェクト配置モデルへのプロジェクトの変換に関する詳細については、「[Integration Services サーバーへのプロジェクトの配置](../../integration-services/packages/deploy-projects-to-integration-services-server.md)」を参照してください。  
  
 **子パッケージのパラメーター**  
 子パッケージのパラメーターの名前を入力または選択します。  
  
 **バインドするパラメーターまたは変数**  
 子パッケージに渡す値を含むパラメーターまたは変数を選択します。  
  
 **[追加]**  
 パラメーターまたは変数を子パッケージのパラメーターにマップする場合にクリックします。  
  
 **[削除]**  
 パラメーターまたは変数と子パッケージのパラメーターの間のマッピングを削除する場合にクリックします。  
  
  