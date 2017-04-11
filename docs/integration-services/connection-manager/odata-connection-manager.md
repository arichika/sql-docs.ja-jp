---
title: "OData 接続マネージャー | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3caa4372-aff3-4c0f-9ecd-97870948b8d0
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# OData 接続マネージャー
  OData ソースに接続するには、OData 接続マネージャーを使用します。 OData ソース コンポーネントは OData 接続マネージャーを使用して OData ソースに接続し、サービスから取得したデータを使用します。 詳細については、「 [OData Source](../../integration-services/data-flow/odata-source.md)」を参照してください。  
  
## <a name="adding-an-odata-connection-manager-to-an-ssis-package"></a>SSIS パッケージへの OData 接続マネージャーの追加  
 次の 3 とおりの方法で、SSIS パッケージに新しい OData 接続マネージャーを追加できます。  
  
-    **[OData ソース エディター]** の **[新規]**  
  
-   **ソリューション エクスプローラー** で **[接続マネージャー]**を右クリックし、 **[新しい接続マネージャー]**をクリックします。 **[接続マネージャーの種類]** の **[ODATA]**をクリックします。  
  
-   パッケージ デザイナーの下部にある **[接続マネージャー]** ペインを右クリックし、 **[新しい接続]**をクリックします。 **[接続マネージャーの種類]** の **[ODATA]**をクリックします。  
  
## <a name="connection-manager-authentication"></a>接続マネージャーの認証  
 OData 接続マネージャーでは、5 つの認証モードがサポートされています。  
  
-   [Windows 認証]  
  
-   基本認証 (ユーザー名とパスワードを使用)  

-   Microsoft Dynamics AX Online (ユーザー名とパスワードを使用)
  
-   Microsoft Dynamics CRM Online (ユーザー名とパスワードを使用)
  
-   Microsoft Online Services (ユーザー名とパスワードを使用)  
  
 匿名アクセスを使用するには、[Windows 認証] オプションを選択します。  
  
### <a name="specifying-and-securing-credentials"></a>資格情報の指定とセキュリティ保護  
 OData サービスで基本認証が必要とされる場合は、 [OData Connection Manager Editor](../../integration-services/connection-manager/odata-connection-manager-editor.md)でユーザー名とパスワードを指定できます。 エディターに入力した値は、パッケージ内に保存されます。 パスワードの値は、パッケージの保護レベルに応じて暗号化されます。  
  
 ユーザー名とパスワードの値をパラメーター化またはパッケージ外に保存する方法はいくつかあります。 たとえば、パラメーターを使用するか、SQL Server Management Studio を使用してパッケージを実行するときに接続マネージャーのプロパティを直接設定します。  
  
## <a name="odata-connection-manager-properties"></a>OData 接続マネージャーのプロパティ  
 次の一覧で、OData 接続マネージャーのプロパティについて説明します。  
  
|||  
|-|-|  
|プロパティ|Description|  
|URL|サービス ドキュメントに対応する URL。|  
|UserName|基本認証で使用するユーザー名。|  
|Password|基本認証で使用するパスワード。|  
|ConnectionString|接続マネージャーの他のプロパティを反映します。|  
  
## <a name="see-also"></a>参照  
 [OData 接続マネージャー エディター](../../integration-services/connection-manager/odata-connection-manager-editor.md)  
  
  