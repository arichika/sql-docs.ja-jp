---
title: Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0df164b267043e4784260b30b039ecb58c2c4cc7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="switch-an-analysis-services-database-between-readonly-and-readwrite-modes"></a>Analysis Services データベースの ReadOnly モードと ReadWrite モードの切り替え
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のデータベース管理者は、クエリ専用の複数のサーバー間でクエリ ワークロードを分散する作業の一部として、テーブルまたは多次元のデータベースの読み取り/書き込みモードを変更できます。  
  
 データベース モードを切り替える方法は複数あります。 このドキュメントでは、次の一般的なシナリオについて説明します。  
  
-   の対話的な使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   AMO を使用したプログラム  
  
-   XMLA または TMSL を使用したスクリプト  
  
## <a name="switch-the-readwrite-mode-of-a-database-interactively-using-management-studio"></a>Management Studio を使用してデータベースの読み取り/書き込みモードを対話的に切り替える  
  
1.  オブジェクト エクスプローラーで、データベースを右クリックし、 **[プロパティ]** をクリックします。  
  
     場所を書き留めます。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
2.  データベースを右クリックし、 **[デタッチ]** をクリックします。  
  
3.  デタッチするデータベースにパスワードを割り当て、 **[OK]** をクリックしてデタッチ コマンドを実行します。  
  
4.  オブジェクト エクスプローラーで、 **[データベース]** フォルダーを右クリックし、 **[アタッチ]** をクリックします。  
  
5.  **[フォルダー]** ボックスに、データベース フォルダーの元の場所を入力します。 または、参照ボタン (**[…]**) を使用して、データベース フォルダーを探すこともできます。  
  
6.  データベースの読み取り/書き込みモードを選択します。  
  
7.  パスワードを入力し、 **[OK]** をクリックしてアタッチ コマンドを実行します。  
  
## <a name="switch-the-readwrite-mode-to-a-database-programmatically-using-amo"></a>プログラムで AMO を使用してデータベースの読み取り/書き込みモードを切り替える  
 C# アプリケーションで、必要なパラメーターを指定して `SwitchReadWrite()` を呼び出します。 コードをコンパイルして実行し、データベースを移動します。  
  
```  
private void SwitchReadWrite(Server server, string dbName, ReadWriteMode dbReadWriteMode)  
{  
    if (server.Databases.ContainsName(dbName))  
    {  
        Database db;  
        string databaseLocation;  
        db = server.Databases[dbName];  
        databaseLocation = db.DbStorageLocation;  
  
              if (databaseLocation == null)  
            {  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
                 string dataDir = server.ServerProperties["DataDir"].Value;  
  
    String[] possibleFolders = Directory.GetDirectories(dataDir, string.Concat(dbName,"*"), SearchOption.TopDirectoryOnly);  
  
   if (possibleFolders.Length > 1)  
         {  
         List<String> sortedFolders = new List<string>(possibleFolders.Length);  
         sortedFolders.AddRange(possibleFolders);  
         sortedFolders.Sort();  
         databaseLocation = sortedFolders[sortedFolders.Count - 1];  
         }  
         else  
         {  
         databaseLocation = possibleFolders[0];  
          }  
        }  
    db.Detach();  
    server.Attach(databaseLocation, dbReadWriteMode);  
    }  
}  
  
```  
  
## <a name="switch-the-readwrite-mode-to-a-database-by-script-using-xmla"></a>XMLA を使用したスクリプトでデータベースの読み取り/書き込みモードを切り替える  
 次の手順は、互換モードが 1050、1100、または 1103 の多次元データベースと表形式データベースに適用されます。  
  
1.  オブジェクト エクスプローラーで、データベースを右クリックし、 **[プロパティ]** をクリックします。  
  
     場所を書き留めます。 データベースのストレージの場所が空の場合は、データベース フォルダーがサーバー データ フォルダー内にあることを示しています。  
  
2.  データベースを右クリックし、 **[デタッチ]** をクリックします。  
  
3.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]で、新しい XMLA タブを開きます。  
  
4.  次の XMLA 用のスクリプト テンプレートをコピーします。  
  
    ```  
    <Detach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Object>  
          <DatabaseID>%dbName%</DatabaseID>  
          <Password>%password%</Password>  
       </Object>  
    </Detach>  
    ```  
  
5.  `%dbName%` をデータベースの名前に置き換え、 `%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
6.  XMLA コマンドを実行します。  
  
7.  新しい XMLA タブに、次の XMLA 用のスクリプト テンプレートをコピーします。  
  
    ```  
    <Attach xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
       <Folder>%dbFolder%</Folder>  
       <ReadWriteMode xmlns="http://schemas.microsoft.com/analysisservices/2008/engine/100">%ReadOnlyMode%</ReadWriteMode>  
    </Attach>  
    ```  
  
8.  `%dbFolder%` をデータベース フォルダーの完全な UNC パスに置き換え、 `%ReadOnlyMode%` を対応する値 **ReadOnly** または **ReadWrite**に置き換え、 `%password%` をパスワードに置き換えます。 テンプレートに含まれている文字 % は削除する必要があります。  
  
9. XMLA コマンドを実行します。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [高可用性とスケーラビリティの Analysis Services](../../analysis-services/instances/high-availability-and-scalability-in-analysis-services.md)   
 [アタッチし、Analysis Services データベースのデタッチ](../../analysis-services/multidimensional-models/attach-and-detach-analysis-services-databases.md)   
 [データベースの格納場所](../../analysis-services/multidimensional-models/database-storage-location.md)   
 [データベースの Readwritemode](../../analysis-services/multidimensional-models/database-readwritemodes.md)   
 [Attach 要素](../../analysis-services/xmla/xml-elements-commands/attach-element.md)   
 [Detach 要素](../../analysis-services/xmla/xml-elements-commands/detach-element.md)   
 [ReadWriteMode 要素](../../analysis-services/xmla/xml-elements-properties/readwritemode-element.md)   
 [DbStorageLocation 要素](../../analysis-services/xmla/xml-elements-properties/dbstoragelocation-element.md)  
  
  
