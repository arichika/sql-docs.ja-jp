---
title: ポリシー管理者にポリシー エラーを通知する警告の構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, configure alerts
ms.assetid: e8e60159-d5b0-49d5-91f3-af8e9cb994c1
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d74d77229e88e04c2d661da827b4d6183ab2d2c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-alerts-to-notify-policy-administrators-of-policy-failures"></a>ポリシー管理者にポリシー エラーを通知する警告の構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ポリシー ベースの管理ポリシーが 3 つの自動評価モードのいずれかで実行された場合にポリシー違反が発生すると、メッセージがイベント ログに書き込まれます。 このメッセージがイベント ログに書き込まれたときに通知を受けるには、メッセージを検出してアクションを実行する警告を作成します。 警告は、次の表に示すようにメッセージを検出します。  
  
|実行モード|メッセージ番号|  
|--------------------|--------------------|  
|変更中 - 禁止<br /><br /> (自動の場合)|34050|  
|変更中 - 禁止<br /><br /> (要求時に実行する場合)|34051|  
|スケジュールで実行|34052|  
|変更中|34053|  
  
 ポリシー ベースの管理のエラー メッセージに対処するように警告を設定するには、次のトピックを参照してください。  
  
-   [オペレーターの作成](http://msdn.microsoft.com/library/1359d790-5905-4927-a208-e7155e7768a2)  
  
-   [エラー番号を使用して警告を作成する](http://msdn.microsoft.com/library/03dd7fac-5073-4f86-babd-37e45a86023c)  
  
-   [オペレーターへの警告の割り当て](http://msdn.microsoft.com/library/aa818155-6fa2-4565-a09f-5c7e31c89754)  
  
## <a name="permissions"></a>アクセス許可  
 要求時に評価されるポリシーは、ユーザーのセキュリティ コンテキストで実行されます。 エラー ログに書き込むには、ALTER TRACE 権限を持っているか、固定サーバー ロール sysadmin のメンバーである必要があります。 権限が不十分なユーザーがポリシーを評価した場合、イベント ログへの書き込みは行われず、警告は発生しません。  
  
 自動実行モードは、sysadmin ロールのメンバーとして実行されます。 これにより、エラー ログへの書き込みと警告の生成が可能になります。  
  
## <a name="additional-considerations-about-alerts"></a>警告に関するその他の注意点  
 警告に関するその他の注意点を次に示します。  
  
-   警告は、有効になっているポリシーに対してのみ発生します。 **[要求時]** ポリシーは有効にできないので、要求時に実行されるポリシーに対して警告は発生しません。  
  
-   実行するアクションに電子メール メッセージの送信が含まれる場合は、メール アカウントを構成する必要があります。 データベース メールを使用することをお勧めします。 データベース メールをセットアップする方法の詳細については、「 [データベース メール アカウントの作成](../../relational-databases/database-mail/create-a-database-mail-account.md)」を参照してください。  
  
  
