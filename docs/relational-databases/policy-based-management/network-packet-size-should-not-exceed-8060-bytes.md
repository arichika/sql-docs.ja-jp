---
title: ネットワーク パケット サイズは 8060 バイトを超えることはできない | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3a79cd7cd9047b93e154bf63bad5b4968a62ff9b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>ネットワーク パケット サイズは 8060 バイトを超えることはできない
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  sp_configure の 'network packet size' に指定された値またはログイン ユーザーのネットワーク パケット サイズが 8060 バイトを超えている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、異なるメモリ割り当て操作が実行されます。 これにより、バッファー プールに予約されていない、プロセスの仮想アドレス空間が増加する可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 ネットワーク パケット サイズが 8060 バイトを超えないようにする必要があります。  
  
## <a name="for-more-information"></a>詳細情報  
 [サポート技術情報の資料 903002](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>参照  
 [ポリシー ベースの管理を使用したベスト プラクティスの監視と実行](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
