---
title: "可用性データベースが中断されている | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.drp1notsuspended.issues.f1"
helpviewer_keywords: 
  - "可用性グループ [SQL Server]、ポリシー"
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# 可用性データベースが中断されている
    
## 概要  
  
|||  
|-|-|  
|**ポリシー名**|可用性データベースの中断状態|  
|**問題点**|可用性データベースが中断されています。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性データベース|  
  
## 説明  
 このポリシーは、セカンダリ データベース ("セカンダリ データベース レプリカ" とも呼ばれます) のデータの移動状態をチェックします。 データの移動が中断された場合、ポリシーは通常とは異なる状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のこのリリース向けに、TechNet Wiki の「[可用性データベースが中断されている](http://go.microsoft.com/fwlink/p/?LinkId=220860)」に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## 考えられる原因  
 この可用性データベースでのデータ同期が中断された原因として、次の原因が考えられます。  
  
-   エラーが原因でシステムによってデータの同期が中断された。  
  
-   メンテナンスのためにデータベース管理者によってデータの同期が中断された。  
  
## 考えられる解決方法  
 データの同期を再開します。 問題が解決しない場合は、イベント ログで可用性グループを調べ、データの移動が中断された原因を分析します。  
  
## 参照  
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  