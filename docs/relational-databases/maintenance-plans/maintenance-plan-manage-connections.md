---
title: '[メンテナンス プラン] ([接続の管理]) | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: maintenance-plans
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 99250afb057830b8a6bc06eb5c2727e8d38bab88
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="maintenance-plan-manage-connections"></a>[メンテナンス プラン] ([接続の管理])
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[接続の管理]** ダイアログ ボックスを使用すると、メンテナンス プランで使用される接続のプロパティを指定できます。 メンテナンス プランを作成すると、プランを作成したサーバーへのローカル接続が作成されます。 この接続を使用して、このローカル接続で作業を実行するタスクを作成します。 必要に応じて、 **[接続の管理]** ダイアログ ボックスを使用して接続のプロパティを追加します。 追加の接続が構成されると、各タスクの接続ボックスに表示されます。  
  
## <a name="options"></a>および  
 **[サーバー]**  
 サーバー インスタンスです。  
  
 **[認証]**  
 接続が Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のどちらで作成されるかを指定します。  

> [!IMPORTANT]  
> パッケージは **msdb** データベースに格納され、**ProtectionLevel** は **ServerStorage** に設定されるため、*SQL Server 認証*を使うと、**msdb** 内のパスワードは暗号化されません。 **msdb** がセキュリティで保護されている場合は *SQL Server 認証*を使ってもかまいませんが、"*Windows 認証*" を使うことをお勧めします

## <a name="see-also"></a>参照  
 [のオブジェクト エクスプローラーの](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
