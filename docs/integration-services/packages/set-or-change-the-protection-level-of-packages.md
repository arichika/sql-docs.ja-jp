---
title: "パッケージの保護レベルを設定または変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "パスワード [Integration Services]"
  - "パッケージ [Integration Services], セキュリティ"
  - "セキュリティ [Integration Services], 保護レベル"
  - "パッケージの保護レベル [Integration Services]"
ms.assetid: 904a5580-82ba-4a26-b0c5-d1c989975f61
caps.latest.revision: 10
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 10
---
# パッケージの保護レベルを設定または変更する
  パッケージの内容やパッケージに含まれているパスワードなどの機密データへのアクセスを制御するには、**ProtectionLevel** プロパティの値を設定します。 プロジェクトをビルドするには、プロジェクトに含まれるパッケージの保護レベルがプロジェクトと同じである必要があります。 **ProtectionLevel** プロパティ設定をプロジェクトで変更する場合は、パッケージのプロパティ設定を手動で更新する必要があります。  
  
 パッケージのライフ サイクルの各段階のパッケージに適した **ProtectionLevel** 設定を判断する方法については、「[パッケージ内の機微なデータへのアクセス制御](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)」を参照してください。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のセキュリティ機能の概要については、「[セキュリティの概要 #40; Integration Services &#41;](../../integration-services/security/security-overview-integration-services.md)」を参照してください。  
  
 このトピックの手順では、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] または dtutil コマンド プロンプト ユーティリティを使用して **ProtectionLevel** プロパティを変更する方法について説明します。  
  
> [!NOTE]  
>  このトピックの手順に加えて、通常、パッケージのインポートまたはエクスポート時にパッケージの **ProtectionLevel** プロパティを設定または変更できます。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インポートおよびエクスポート ウィザードを使用してパッケージを保存するときにも、パッケージの **ProtectionLevel** プロパティを変更できます。  
  
### SQL Server データ ツールでパッケージの保護レベルを設定または変更するには  
  
1.  「[パッケージの保護レベルの設定](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)」で **ProtectionLevel** プロパティに使用可能な値を確認し、パッケージに適した値を判断します。  
  
2.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で、パッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
3.  [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでパッケージを開きます。  
  
4.  [プロパティ] ウィンドウにパッケージのプロパティが表示されない場合は、デザイン画面をクリックします。  
  
5.  [プロパティ] ウィンドウの **[セキュリティ]** グループの **[ProtectionLevel]** プロパティで、適切な値を選択します。  
  
     パスワードを必要とする保護レベルを選択する場合は、**[PackagePassword]** プロパティの値としてパスワードを入力します。  
  
6.  **[ファイル]**メニューの **[選択されたファイルを上書き保存]** をクリックして、変更したパッケージを保存します。  
  
### コマンド プロンプトでパッケージの保護レベルを設定または変更するには  
  
1.  「[パッケージの保護レベルの設定](../../integration-services/packages/access-control-for-sensitive-data-in-packages.md)」で **ProtectionLevel** プロパティに使用可能な値を確認し、パッケージに適した値を判断します。  
  
2.  「[dtutil ユーティリティ](../../integration-services/dtutil-utility.md)」で **Encrypt** オプションのマッピングを確認し、選択した **ProtectionLevel** プロパティの値として使用するのに適した整数を判断します。  
  
3.  コマンド プロンプト ウィンドウを開きます。  
  
4.  コマンド プロンプトで、**ProtectionLevel** プロパティを設定するパッケージが格納されているフォルダーに移動します。  
  
     次の手順に示す構文の例では、このフォルダーは現在のフォルダーであると想定しています。  
  
5.  次のいずれかの例のようなコマンドを使用して、パッケージの保護レベルを設定または変更します。  
  
    -   次のコマンドでは、ファイル システム内の個々のパッケージの **ProtectionLevel** プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。  
  
         `dtutil.exe /file "C:\Package.dtsx" /encrypt file;"C:\Package.dtsx";2;strongpassword`  
  
    -   次のコマンドでは、ファイル システム内の特定のフォルダーに存在するすべてのパッケージの **ProtectionLevel** プロパティがレベル 2 の [機微なデータをパスワードで暗号化する] に設定され、パスワードが "strongpassword" に設定されます。  
  
         `for %f in (*.dtsx) do dtutil.exe /file %f /encrypt file;%f;2;strongpassword`  
  
         バッチ ファイルで同様のコマンドを使用する場合は、ファイルのプレースホルダー「%f」をバッチ ファイルでは「%%f」と入力します。  
  
## 参照  
 [dtutil ユーティリティ](../../integration-services/dtutil-utility.md)  
  
  