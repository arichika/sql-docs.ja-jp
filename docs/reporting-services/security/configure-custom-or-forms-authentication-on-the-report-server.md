---
title: "レポート サーバーでカスタム認証またはフォーム認証を構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "フォーム認証, 構成"
  - "カスタム認証 [Reporting Services]"
ms.assetid: e8601a8f-e66d-4649-8e4d-a46ca20ec7d0
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 16
---
# レポート サーバーでカスタム認証またはフォーム認証を構成する
  Reporting Services に用意されている拡張可能なアーキテクチャを使用すると、カスタム認証モジュールまたはフォームベースの認証モジュールを組み込むことができます。 配置の要件に Windows 統合セキュリティまたは基本認証が含まれていない場合は、カスタム認証拡張機能を実装することを検討してください。 カスタム認証を使用する最も一般的なシナリオは、インターネットまたはエクストラネットを介した Web アプリケーションへのアクセスをサポートすることです。 既定の Windows 認証拡張機能の代わりにカスタム認証拡張機能を使用することで、レポート サーバーへのアクセスを外部ユーザーに許可する方法をより細かく制御できます。  
  
 実際に、カスタム認証拡張機能を配置するには、アセンブリとアプリケーション ファイルのコピー、構成ファイルの変更、テストを含む、複数の手順を実行する必要があります。 ここでは、構成ファイルで指定する認証設定のみに焦点を当てて説明します。  
  
> [!NOTE]  
>  カスタム認証拡張機能を作成するには、カスタム コードと [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] セキュリティに関する専門知識が必要です。 カスタム認証拡張機能を作成しない場合は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory のグループとアカウントを使用できます。ただし、レポート サーバーの配置のスコープを大幅に縮小する必要があります。 カスタム認証について詳しくは、「[セキュリティ拡張機能の実装](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)」をご覧ください。  
  
 さらに、SharePoint 製品と統合された [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 環境でフォーム認証またはカスタム認証拡張機能を使用する場合は、選択した認証方法を使用するように SharePoint サイトを構成する必要があります。 SharePoint における認証の構成に関する詳細については、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Developer Network (MSDN) の「[認証の例](http://go.microsoft.com/fwlink/?LinkId=115575)」をご覧ください。  
  
### カスタム認証を使用するようにレポート サーバーを構成するには  
  
1.  テキスト エディターで RSReportServer.config を開きます。  
  
2.  \<**Authentication**> を検索します。  
  
3.  次の XML 構造をコピーします。  
  
    ```  
    <Authentication>  
          <AuthenticationTypes>  
                 <Custom />  
          </AuthenticationTypes>  
          <EnableAuthPersistence>true</EnableAuthPersistence>  
    </Authentication>  
    ```  
  
4.  これを \<**Authentication**> の既存のエントリ上に貼り付けます。  
  
     **Custom** は他の認証の種類と併用できないので注意してください。  
  
5.  ファイルを保存します。  
  
6.  レポート サーバーの Web.config ファイルを開きます。 既定では、このファイルは \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportServer にあります。  
  
7.  **authentication mode** を探して、それを **Forms** に設定します。  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
8.  **identity impersonate** を探して、それを **False** に設定します。  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
9. レポート マネージャーの Web.config ファイルを開きます。 既定では、このファイルは \Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\ReportManager にあります。  
  
10. **authentication mode** を探して、それを **Forms** に設定します。  
  
    ```  
    <authentication mode = "Forms" />  
    ```  
  
11. **identity impersonate** を探して、それを **False** に設定します。  
  
    ```  
    <identity impersonate = "false" />  
    ```  
  
12. 構成ファイルに **PassThroughCookies** 要素構造を追加します。 詳しくは、「[カスタム認証クッキーを送信するようにレポート マネージャーを構成する](../Topic/Configure%20Report%20Manager%20to%20Pass%20Custom%20Authentication%20Cookies.md)」をご覧ください。  
  
13. ファイルを保存します。  
  
14. スケールアウト配置を構成した場合は、配置内の他のレポート サーバーに対して上記の手順すべてを繰り返します。  
  
15. レポート サーバーを再起動して、現在開いているセッションを消去します。  
  
## 参照  
 [セキュリティ拡張機能の実装](../../reporting-services/extensions/security-extension/implementing-a-security-extension.md)   
 [レポート サーバーでの認証](../../reporting-services/security/authentication-with-the-report-server.md)   
 [RsReportServer.config 構成ファイル](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [レポート サーバーで基本認証を構成する](../../reporting-services/security/configure-basic-authentication-on-the-report-server.md)   
 [レポート サーバーで Windows 認証を構成する](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md)  
  
  