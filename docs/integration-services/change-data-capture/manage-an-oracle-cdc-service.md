---
title: Oracle CDC Service の管理 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: change-data-capture
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- createSrv
ms.assetid: 5972cee3-b1a9-4c56-aed6-bdddf84af283
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 64c1702e49bf68edd9e5b3abf316ea9289d9a6ce
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="manage-an-oracle-cdc-service"></a>Manage an Oracle CDC Service
  CDC Service 構成コンソールを使用すると、特定の CDC Service を管理できます。  
  
 **操作する CDC サービスを選択するには**  
  
1.  CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** を展開します。  
  
2.  操作する CDC サービスを選択します。  
  
     操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。 「 [CDC Service で可能な操作](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)」を参照してください。  
  
 **OR**  
  
1.  CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** をクリックします。  
  
2.  CDC Service 構成コンソールの中央のセクションで、操作するサービスを選択します。  
  
     操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。 「 [CDC Service で可能な操作](../../integration-services/change-data-capture/manage-an-oracle-cdc-service.md#BKMK_WhatcandowithCDCService)」を参照してください。  
  
##  <a name="BKMK_WhatcandowithCDCService"></a> CDC Service で可能な操作  
 CDC サービスの操作時には、以下のアクションを実行できます。  
  
### <a name="delete-the-service"></a>サービスの削除  
 サービスを削除するには、CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[削除]** をクリックします。  
  
 または、削除する CDC サービスを右クリックして **[削除]** を選択します。  
  
 **注**: 実行中のサービスを削除した場合、サービスは停止されてから削除されます。  
  
 Oracle CDC Windows Service の定義を削除するには、プログラムに、関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の MSXDBCDC データベースに対する更新アクセスが必要です。 [OK] をクリックしてサービスを削除すると、MSXDBCDC データベース内にある Oracle CDC Service 登録の削除が試みられます。 プログラムが適切な権限を持っていないため Oracle CDC Service 登録を削除できない場合、ユーザーは、MSXDBCDC データベースに対する更新権限を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力するよう求められます。  
  
 [SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Connection to SQL Server for Delete](../../integration-services/change-data-capture/connection-to-sql-server-for-delete.md)」を参照してください。  
  
### <a name="edit-the-cdc-service-properties"></a>CDC Service のプロパティの編集  
 CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[プロパティ]** をクリックします。  
  
 または、プロパティを編集する CDC サービスを右クリックして **[プロパティ]** を選択します。  
  
## <a name="see-also"></a>参照  
 [ローカルの CDC Service を管理する方法](../../integration-services/change-data-capture/how-to-manage-a-local-cdc-service.md)  
  
  
