---
title: "レッスン 2: SSIS での配置バンドルの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: ab17289d-c3d4-4a5e-b7f5-4fea8ae21707
caps.latest.revision: 18
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 18
---
# レッスン 2: SSIS での配置バンドルの作成
[「レッスン 1: 配置バンドルを作成する準備」](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)では、Deployment Tutorial という名前の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成し、パッケージとサポート ファイルをプロジェクトに追加して、パッケージに構成を実装しました。  
  
このレッスンでは、配置バンドルを作成します。配置バンドルとは、他のコンピューターにパッケージをインストールするために必要なアイテムが含まれているフォルダーです。 配置バンドルには、Deployment Tutorial プロジェクトの配置マニフェスト、パッケージのコピー、サポート ファイルのコピーを含めます。 配置マニフェストとは、配置バンドルに含まれているパッケージ、その他のファイル、および構成の一覧です。  
  
また、配置バンドルに含まれているファイルの一覧を確認し、マニフェストの内容を確認します。  
  
**このレッスンの推定所要時間:** 30 分  
  
## このレッスンの作業  
このレッスンの内容は次のとおりです。  
  
-   [手順 1: 配置ユーティリティの構築](../integration-services/step-1-building-the-deployment-utility.md)  
  
-   [手順 2: 配置バンドルの確認](../integration-services/step-2-verifying-the-deployment-bundle.md)  
  
## レッスンの開始  
[手順 1: 配置ユーティリティの構築](../integration-services/step-1-building-the-deployment-utility.md)  
  
  
  