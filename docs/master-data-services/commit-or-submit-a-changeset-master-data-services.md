---
title: "変更セットのコミットまたは送信 (マスター データ サービス) | Microsoft Docs"
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
ms.assetid: d323bbac-c8d4-4d2f-a7d2-a597e8b53e2d
caps.latest.revision: 10
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 10
---
# 変更セットのコミットまたは送信 (マスター データ サービス)
  変更セットは、マスター データに対する保留中の変更のコレクションです。 エンティティの変更が管理者の承認を必要としない場合は、変更セットをコミットできます。 エンティティの変更が管理者の承認を必要とする場合は、承認を受けるために変更セットを送信できます。  
  
## 前提条件  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   エンティティの変更が管理者の承認を必要としない場合は、変更セットを自分が所有し、変更セットの状態がオープンである場合のみ、変更セットをコミットできます。  
  
-   エンティティの変更が管理者の承認を必要とする場合は、変更セットを自分が所有し、変更セットの状態がオープンまたは拒否である場合のみ、承認を受けるために変更セットを送信できます。  
  
## ローカルの変更セットをコミットするには  
 コミット オプションは、エンティティ管理者が承認の必要性を有効にしていないエンティティでローカルの変更セットにのみ使用できます。  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、モデルとバージョンを選択し、 **[エクスプローラー]**をクリックします。  
  
2.  **[エンティティ]** メニューでエンティティをクリックします。  
  
3.  右側のウィンドウで、**[変更セット]** を選択し、コミットする変更セットをダブルクリックします。  
  
4.  **[コミット]** をクリックします。  
  
## 変更セットを送信するには  
 送信オプションは、エンティティ管理者が承認の必要性を有効にしているエンティティの変更セットでのみ使用できます。  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、モデルとバージョンを選択し、 **[エクスプローラー]**をクリックします。  
  
2.  **[エンティティ]** メニューでエンティティをクリックします。  
  
3.  右側のウィンドウで、**[変更セット]** を選択し、送信する変更セットをダブルクリックします。  
  
4.  **[送信]** をクリックします。  
  
## 次の手順  
 [変更セットの承認または拒否 (マスター データ サービス)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
## 参照  
 [変更セットを作成する (マスター データ サービス)](../master-data-services/create-a-changeset-master-data-services.md)   
 [変更セットの適用および更新 (マスター データ サービス)](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [変更セットの承認または拒否 (マスター データ サービス)](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  