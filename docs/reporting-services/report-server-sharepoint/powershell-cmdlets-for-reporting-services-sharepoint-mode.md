---
title: "Reporting Services SharePoint モードの PowerShell コマンドレット | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
caps.latest.revision: 32
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 31
---
# Reporting Services SharePoint モードの PowerShell コマンドレット
   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードをインストールすると、SharePoint モードのレポート サーバーをサポートするために PowerShell コマンドレットがインストールされます。 コマンドレットは 3 つのカテゴリの機能をサポートしています。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービスおよびプロキシのインストール。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションおよび関連付けられたプロキシのプロビジョニングと管理。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 機能 (拡張機能や暗号化キーなど) の管理。  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード|  
  
 **このトピックの内容は次のとおりです。**  
  
-   [コマンドレットの概要](#bkmk_cmdlet_sum)  
  
-   [共有サービスとプロキシ コマンドレット](#bkmk_sharedservice_cmdlets)  
  
-   [サービス アプリケーションとプロキシ コマンドレット](#bkmk_serviceapp_cmdlets)  
  
-   [Reporting Services カスタム機能コマンドレット](#bkmk_ssrsfeatures_cmdlets)  
  
-   [Reporting Services PowerShell の基本的なサンプル](#bkmk_basic_samples)  
  
-   [Reporting Services PowerShell の高度なサンプル](#bkmk_detailedsamples)  
  
    -   [Reporting Services サービス アプリケーションとプロキシの作成](#bkmk_example_create_service_application)  
  
    -   [Reporting Services 配信拡張機能の確認と更新](#bkmk_example_delivery_extension)  
  
    -   [Reporting Service アプリケーション データベースのプロパティの取得と設定](#bkmk_example_db_properties)  
  
    -   [Reporting Services データ拡張機能の一覧表示](#bkmk_example_list_data_extensions)  
  
    -   [Reporting Services サブスクリプション所有者の変更と一覧表示](#bkmk_change_subscription_owner)  
  
##  <a name="bkmk_cmdlet_sum"></a> コマンドレットの概要  
 コマンドレットを実行するには、SharePoint 管理シェルを開く必要があります。 Microsoft Windows に付属しているグラフィカル ユーザー インターフェイス エディター (**Windows PowerShell Integrated Scripting Environment (ISE)**) を使用することもできます。 詳細については、「[Windows Server での Windows PowerShell の開始](http://technet.microsoft.com/library/hh847814.aspx)」(http://technet.microsoft.com/library/hh847814.aspx) を参照してください。 次のコマンドレット概要では、サービス アプリケーション "データベース" への参照は、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションによって作成および使用されたすべてのデータベースを参照します。 これには、構成、警告、および一時データベースが含まれます。  
  
 PowerShell の例を入力すると、次のようなエラー メッセージが表示されます。  
  
-   Install-SPRSService : 用語 'Install-SPRSService' は、  
    コマンドレット、関数、スクリプト ファイル、または操作可能なプログラムの名前として認識されません。 名前が正しく記述されていることを確認し、パスが含まれている場合はそのパスが正しいことを確認してから、再試行してください。  
  
 次のいずれかの問題が発生しています。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードがインストールされていないため、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コマンドレットがインストールされていません。  
  
-   SharePoint 管理シェルでなく、Windows PowerShell または Windows PowerShell ISE で PowerShell コマンドを実行しました。 SharePoint 管理シェルを使用するか、次のコマンドで SharePoint スナップインを Windows PowerShell ウィンドウに追加します。  
  
    ```  
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 詳細については、「[Windows PowerShell を使用して SharePoint 2013 を管理する](http://technet.microsoft.com/library/ee806878.aspx)」 (http://technet.microsoft.com/library/ee806878.aspx) を参照してください。  
  
#### SharePoint 管理シェルを開いてコマンドレットを実行するには  
  
1.  **[スタート]** ボタンをクリックします。  
  
2.  **[Microsoft SharePoint 製品]** グループをクリックします。  
  
3.  **[SharePoint 管理シェル]**をクリックします。  
  
 コマンドレットのコマンド ライン ヘルプを表示するには、PowerShell のコマンド プロンプトで 'Get-Help' コマンドを使用します。 例:  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="bkmk_sharedservice_cmdlets"></a> 共有サービスとプロキシ コマンドレット  
 次の表に、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共有サービス用の PowerShell コマンドレットを示します。  
  
|コマンドレット|Description|  
|------------|-----------------|  
|Install-SPRSService|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスをインストールして登録するか、アンインストールします。 この操作は、SharePoint モードの SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされているコンピューター上でのみ行うことができます。 インストールの場合は、以下の 2 つの操作が行われます。<br /><br /> - [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスがファーム内にインストールされる。<br /><br /> - [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス インスタンスが現在のコンピューターにインストールされる。<br /><br /> アンインストールの場合は、以下の 2 つの操作が行われます。<br /><br /> - [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスが現在のコンピューターからアンインストールされる。<br /><br /> - [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスがファームからアンインストールされる。<br /><br /> <br /><br /> メモ: [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスがインストールされているファーム内に他のコンピューターが存在する場合や [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションがファーム内で引き続き実行されている場合は、警告メッセージが表示されます。|  
|Install-SPRSServiceProxy|SharePoint ファーム内で Reporting Services サービス プロキシをインストールして登録するか、アンインストールします。|  
|Get-SPRSProxyUrl|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスにアクセスするための URL を取得します。|  
|Get-SPRSServiceApplicationServers|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 共有サービスのインストールを含む、ローカル SharePoint ファーム内のすべてのサーバーを取得します。 このコマンドレットは、どのサーバーで共有サービスを実行していてアップグレードする必要があるかを調べる目的に適しており、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のアップグレードに役立ちます。|  
  
###  <a name="bkmk_serviceapp_cmdlets"></a> サービス アプリケーションとプロキシ コマンドレット  
 次の表には、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションとそれらに関連付けられたプロキシ用の PowerShell コマンドレットが含まれています。  
  
|コマンドレット|Description|  
|------------|-----------------|  
|Get-SPRSServiceApplication|1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション オブジェクトを取得します。|  
|New-SPRSServiceApplication|新しい Reporting Services サービス アプリケーションと、それに関連付けられたデータベースを作成します。<br /><br /> LogonType パラメーター: レポート サーバーが、レポート サーバー データベースへのアクセスに SSRS Application Pool アカウントと SQL Server ログインのどちらを使用するかを指定します。 以下の値が有効です。<br /><br /> 0 Windows 認証<br /><br /> 1 SQL Server<br /><br /> 2 アプリケーション プール アカウント (既定)|  
|Remove-SPRSServiceApplication|指定した Reporting Services サービス アプリケーションを削除します。 これを実行すると、関連付けられたデータベースも削除されます。|  
|Set-SPRSServiceApplication|既存の Reporting Services サービス アプリケーションのプロパティを編集します。|  
|New-SPRSServiceApplicationProxy|新しい Reporting Services サービス アプリケーション プロキシを作成します。|  
|Get-SPRSServiceApplicationProxy|1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション プロキシを取得します。|  
|Dismount-SPRSDatabase|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用のサービス アプリケーション データベースをマウント解除します。|  
|Remove-SPRSDatabase|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用のサービス アプリケーション データベースを削除します。|  
|Set-SPRSDatabase|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションに関連付けられたデータベースのプロパティを設定します。|  
|Mount-SPRSDatabase|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用のデータベースをマウントします。|  
|New-SPRSDatabase|指定した [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用の新しいサービス アプリケーション データベースを作成します。|  
|Get-SPRSDatabaseCreationScript|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用に、データベース作成スクリプトを画面に出力します。 その後、SQL Server Management Studio でスクリプトを実行できます。|  
|Get-SPRSDatabase|1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション データベースを取得します。 Set-SPRSDatabase コマンドレットを使用して `querytimeout` などのプロパティを変更できるように、コマンドを使用してサービス アプリケーション データベースの ID を取得します。 このトピックの例「[Reporting Service アプリケーション データベースのプロパティの取得と設定](#bkmk_example_db_properties)」を参照してください。|  
|Get-SPRSDatabaseRightsScript|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用に、データベース権限スクリプトを画面に出力します。 これを実行すると、対象のユーザーとデータベースの入力を求めるプロンプトが表示され、権限を変更するための Transact-SQL が返されます。 その後、SQL Server Management Studio でこのスクリプトを実行できます。|  
|Get-SPRSDatabaseUpgradeScript|データベース アップグレード スクリプトを画面に出力します。 このスクリプトは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション データベースを、現在の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールのデータベース バージョンにアップグレードします。|  
  
###  <a name="bkmk_ssrsfeatures_cmdlets"></a> Reporting Services カスタム機能コマンドレット  
  
|コマンドレット|Description|  
|------------|-----------------|  
|Update-SPRSEncryptionKey|指定した Reporting Services サービス アプリケーションの暗号化キーを更新し、そのデータを再暗号化します。|  
|Restore-SPRSEncryptionKey|以前にバックアップした、Reporting Services サービス アプリケーションの暗号化キーを復元します。|  
|Remove-SPRSEncryptedData|指定した Reporting Services サービス アプリケーションの暗号化されたデータを削除します。|  
|Backup-SPRSEncryptionKey|指定した Reporting Services サービス アプリケーションの暗号化キーをバックアップします。|  
|New-SPRSExtension|新しい拡張機能を Reporting Services サービス アプリケーションに登録します。|  
|Set-SPRSExtension|既存の Reporting Services 拡張機能のプロパティを設定します。|  
|Remove-SPRSExtension|Reporting Services サービス アプリケーションから拡張機能を削除します。|  
|Get-SPRSExtension|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーション用の、1 つ以上の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 拡張機能を取得します。<br /><br /> 以下の値が有効です。<br /><br /> <br /><br /> Delivery<br /><br /> DeliveryUI<br /><br /> Render<br /><br /> データ<br /><br /> Security<br /><br /> [認証]<br /><br /> EventProcessing<br /><br /> ReportItems<br /><br /> デザイナー<br /><br /> ReportItemDesigner<br /><br /> ReportItemConverter<br /><br /> ReportDefinitionCustomization|  
|Get-SPRSSite|"ReportingService" 機能が有効になっているかどうかに基づいて SharePoint サイトを取得します。 既定では、"ReportingService" 機能が有効になっているサイトが返されます。|  
  
##  <a name="bkmk_basic_samples"></a> Reporting Services PowerShell の基本的なサンプル  
 名前に 'SPRS' を含んでいるコマンドレットの一覧を返します。 これは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コマンドレットの完全な一覧になります。  
  
```  
Get-command –noun *SPRS*  
```  
  
 または、より詳細な情報を使用して、commandlist.txt という名前のテキスト ファイルにパイプします。  
  
```  
Get-command -noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint サービスおよびサービス プロキシをインストールします。  
  
```  
Install-SPRSService  
```  
  
```  
Install-SPRSServiceProxy  
```  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービスを開始します。  
  
```  
get-spserviceinstance -all |where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 SharePoint 管理シェルから次のコマンドを入力すると、フィルター処理された行のリストがログ ファイルから返されます。 このコマンドを実行すると、"ssrscustomactionerror" を含む行がフィルター処理されます。 この例では、rssharepoint.msi のインストール時に作成されたログ ファイルが検索対象となっています。  
  
```  
Get-content -path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | select-string "ssrscustomactionerror"  
```  
  
##  <a name="bkmk_detailedsamples"></a> Reporting Services PowerShell の高度なサンプル  
 次のサンプルに加えて、「[手順 1 ～ 4 に対応する Windows PowerShell スクリプト](../../reporting-services/install-windows/install-the-first-report-server-in-sharepoint-mode.md#bkmk_full_script)」の「Windows PowerShell スクリプト」を参照してください。  
  
###  <a name="bkmk_example_create_service_application"></a> Reporting Services サービス アプリケーションとプロキシの作成  
 このサンプル スクリプトは次のタスクを完了します。  
  
1.  Reporting Services サービス アプリケーションとプロキシを作成する。 このスクリプトは、"My App Pool" というアプリケーション プールが既に存在することを前提としています。  
  
2.  作成したプロキシを既定のプロキシ グループに追加する。  
  
3.  ポート 80 の Web アプリケーションのコンテンツ データベースに、サービス アプリケーション アクセス権を付与する。 このスクリプトは、サイト "http://sitename" が既に存在することを前提としています。  
  
```  
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool “My App Pool”  
$serviceApp = New-SPRSServiceApplication “My RS Service App” –ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy –Name “My RS Service App Proxy” –ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup –default | Add-SPServiceApplicationProxyGroupMember –Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application’s content database.  
$webApp = Get-SPWebApplication “http://sitename”  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)  
  
```  
  
###  <a name="bkmk_example_delivery_extension"></a> Reporting Services 配信拡張機能の確認と更新  
 次の PowerShell スクリプトの例では、`My RS Service App` という名前のサービス アプリケーションについて、レポート サーバーの電子メール配信拡張機能の構成を更新します。 SMTP サーバー (`<email server name>`) と差出人の電子メール別名 (`<your FROM email address>`) の値を更新します。  
  
```  
$app=get-sprsserviceapplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml   
$emailXml = [xml]$emailCfg   
$emailXml.SelectSingleNode("//SMTPServer").InnerText = “<email server name>”  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 上の例で、サービス アプリケーションの正確な名前がわからない場合は、最初のステートメントを書き換えて、サービス アプリケーションを部分名検索に基づいて取得することもできます。 例:  
  
```  
$app=get-sprsserviceapplication | where {$_.name -like " ssrs_testapp *"}  
```  
  
 次のスクリプトは、"Reporting Services Application" という名前のサービス アプリケーションについて、レポート サーバーの電子メール配信拡張機能の現在の構成値を返します。 最初のステップでは、"My RS Service App" という名前のサービス アプリケーションのオブジェクトに、変数 $app の値が設定されます。  
  
 2 番目のステートメントは、変数 $app 内のサービス アプリケーション オブジェクト用の "レポート サーバー電子メール" 配信拡張機能を取得し、configurationXML を選択します。  
  
```  
$app=get-sprsserviceapplication –Name "Reporting Services Application"  
Get-SPRSExtension -identity $app -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
 上の 2 つのステートメントを次のように書き直して 1 つのステートメントにすることもできます。  
  
```  
get-sprsserviceapplication –Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -name "Report Server Email" | select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="bkmk_example_db_properties"></a> Reporting Service アプリケーション データベースのプロパティの取得と設定  
 次の例では、set コマンドに指定するデータベースの GUID (ID) を確認できるように、最初にデータベースとプロパティの一覧を返します。 プロパティの一覧については、「 `Get-SPRSDatabase | format-list`」を参照してください。  
  
```  
get-SPRSDatabase | select id, querytimeout,connectiontimeout, status, server, ServiceInstance   
```  
  
 出力の例を次に示します。 変更するデータベースの ID を確認し、SET コマンドレットでその ID を使用します。  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```  
Set-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 値が設定されていることを確認するには、もう一度 GET コマンドレットを実行します。  
  
```  
Get-SPRSDatabase –identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="bkmk_example_list_data_extensions"></a> Reporting Services データ拡張機能の一覧表示  
 次の例では、各 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] サービス アプリケーションの間をループし、それぞれの現在のデータ拡張機能を一覧表示します。  
  
```  
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)   
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType “Data” | select name,extensiontype | Format-Table -AutoSize  
}  
```  
  
 **出力例:**  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="bkmk_change_subscription_owner"></a> Reporting Services サブスクリプション所有者の変更と一覧表示  
 「 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../reporting-services/subscriptions/manage subscription owners and run subscription - powershell.md)」を参照してください。  
  
## 参照  
 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../reporting-services/subscriptions/manage subscription owners and run subscription - powershell.md)   
 [チェック リスト: PowerShell を使用して PowerPivot for SharePoint を確認する](../../analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint.md)   
 [SQL Server PowerShell のヘルプの参照](../../relational-databases/scripting/get-help-sql-server-powershell.md)   
 [CodePlex SharePoint 管理 PowerShell スクリプト](http://sharepointpsscripts.codeplex.com/)   
 [PowerShell を使用して SSRS を管理する方法](https://curatedviews.cloudapp.net/13107/how-to-administer-ssrs-using-powershell)  
  
  