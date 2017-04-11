---
title: "[Web アプリケーションの作成] ダイアログ ボックス (Master Data Services 構成マネージャー) | Microsoft Docs"
ms.custom: ""
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.mds.configmanager.createapp.f1"
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 9
---
# [Web アプリケーションの作成] ダイアログ ボックス (Master Data Services 構成マネージャー)
  **[Web アプリケーションの作成]** ダイアログ ボックスを使用して、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを作成します。 この Web アプリケーションは、**[Web の構成]** ページで選択したサイトに作成されます。  
  
## Web アプリケーション  
 Web サーバーでは、ファイル システム内の [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] の **WebApplication** フォルダーから、この Web アプリケーションのコンテンツを提供します。 この場所は、セットアップ中に指定されます。既定のパスは、*drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication です。  
  
|コントロール名|Description|  
|------------------|-----------------|  
|[仮想パス]|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを作成する仮想パスを選択します。 仮想パスは、Web アプリケーションへのアクセスに使用される URL の一部です。<br /><br /> この一覧は、[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを作成できる、アプリケーションの仮想パスのみが表示されるようにフィルター選択されています。 別の [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションに [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを作成することはできません。|  
|別名|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションの名前を入力するか、既定の名前を使用します。 この名前は、Web ブラウザーから Web アプリケーションにアクセスするための URL で使用されます。|  
  
## アプリケーション プール  
  
|コントロール名|Description|  
|------------------|-----------------|  
|**名前**|新しいアプリケーション プールの一意な表示名を入力するか、既定の名前を使用します。 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションは、このアプリケーション ツールに追加されます。<br /><br /> アプリケーション プールには、あるアプリケーション プール内のアプリケーションが別のアプリケーション プール内のアプリケーションに影響しないように境界が設けられています。|  
|**ユーザー名**|Active Directory のドメインおよびユーザー名を入力します。 このアカウントは、Web アプリケーションを実行するアプリケーション プールの ID です。 このアカウントは、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの作成時にサービス アカウントとして指定したアカウントと同じにします。<br /><br /> このアカウントは、データベースにアクセスするために [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの mds_exec データベース ロールに追加されます。 詳細については、「[データベース ログイン、ユーザー、およびロール &#40;マスター データ サービス&#41;](../master-data-services/database-logins-users-and-roles-master-data-services.md)」を参照してください。 また、このアカウントは、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Windows グループ **MDS_ServiceAccounts** にも追加されます。このグループには、ファイル システムの一時コンパイル ディレクトリ **MDSTempDir** に対する権限が与えられています。 詳細については、「[フォルダーとファイルの権限 &#40;マスター データ サービス&#41;](../master-data-services/folder-and-file-permissions-master-data-services.md)」を参照してください。|  
|**Password**|指定したユーザー アカウントのパスワードを入力します。|  
|**[パスワードの確認入力]**|指定したユーザー アカウントのパスワードを再入力します。 **[パスワード]** フィールドと **[パスワードの確認入力]** フィールドには、同じパスワードを入力する必要があります。|  
  
## 参照  
 [[Web の構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../Topic/Web%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)   
 [マスター データ サービスの概要 (SQL Server 2016)](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [Web アプリケーションの要件 &#40;マスター データ サービス&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md)   
 [マスター データ マネージャー Web アプリケーションの作成 &#40;マスター データ サービス&#41;](../master-data-services/install-windows/create-a-master-data-manager-web-application-master-data-services.md)  
  
  