---
title: ファイルの最大アップロード サイズ (Power Pivot for SharePoint) の構成 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 15ce366acc4244db16f0b58bbdc8226e9327416c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="configure-maximum-file-upload-size-power-pivot-for-sharepoint"></a>アップロードするファイルの最大サイズの構成 (Power Pivot for SharePoint)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックには大量のデータが含まれる場合が多く、SharePoint のアップロードで許容されるファイルの最大サイズを超過することがあります。 最大サイズを超過したファイルをアップロードしようとすると、SharePoint で次のエラーが発生します。  
  
-   "指定されたファイルは、サポートされる最大ファイル サイズを超えています。"  
  
 ファイル サイズを増やすには、まず、Excel Services の [ブックの最大サイズ] を 50 MB に調整します。 これにより、Excel に対するファイルの最大サイズの上限が SharePoint Web アプリケーションに対するファイル サイズの上限 (SharePoint 2010 では既定で 50 MB、SharePoint 2013 では既定で 200 MB) と同じになります。 ファイルのサイズが 50 MB を超える場合は、Excel Services と Web アプリケーションの両方についてファイル サイズの上限を増やします。  
  
 ファイルの最大アップロード サイズを変更するには、SharePoint 管理者である必要があります。  
  
### <a name="configure-maximum-file-size-for-excel-services"></a>Excel Services に対するファイルの最大サイズの構成  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[サービス アプリケーションの管理]** をクリックします。  
  
2.  Excel Services アプリケーションの名前をクリックします。  
  
3.  **[信頼できるファイル保存場所]** をクリックします。  
  
4.  プロパティを編集する場所をクリックします。 既定では、既定の Web アプリケーションは信頼できるサイトと見なされます。 既定の Web アプリケーションを使用している場合は、 **http://** をクリックして、この場所の構成ページを開きます。  
  
5.  **[ブックのプロパティ]** までスクロールします。  
  
6.  [ブックの最大サイズ] で、ファイル サイズを 10 (既定値) から 50、または使用するファイルに対応できるさらに大きい値に増やします。  
  
     既定では、50 MB が SharePoint Web アプリケーションのファイルの最大アップロード サイズです。 [ブックの最大サイズ] を 50 MB よりも大きい値に設定した場合は、次の手順に従って、SharePoint Web アプリケーションの [アップロードの最大サイズ] を同じ値に増やしてください。  
  
     指定できる最大値は 2 GB (またはサーバーの全体管理で指定された 2047 MB) です。  
  
7.  **[OK]** をクリックします。  
  
### <a name="configure-maximum-file-size-for-a-sharepoint-web-application"></a>SharePoint Web アプリケーションに対するファイルの最大サイズの構成  
  
1.  サーバーの全体管理で、[アプリケーション構成の管理] の **[Web アプリケーションの管理]** をクリックします。  
  
    > [!NOTE]  
    >  以下の手順は、Excel Services の [ブックの最大サイズ] を大きい値に設定した場合にのみ実行してください。  
  
2.  アプリケーションを選択します ( **SharePoint -80**など)。  
  
3.  [Web アプリケーション] リボンで、[全般設定] ボタンの下矢印をクリックします。  
  
4.  **[全般設定]** をクリックします。  
  
5.  **[アップロードの最大サイズ]** までスクロールします。  
  
6.  Excel Services の [ブックの最大サイズ] 以上の値にプロパティを設定します。  
  
7.  **[OK]** をクリックします。  
  
  
