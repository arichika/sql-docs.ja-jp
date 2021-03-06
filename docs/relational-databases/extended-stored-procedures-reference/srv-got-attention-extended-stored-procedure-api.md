---
title: srv_got_attention (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- srv_got_attention
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_got_attention
ms.assetid: 805e68e1-d17f-41bd-8b9f-a27283bb6fbe
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ccc83edc32893f01ff2a5bb2d3574d74bca78bde
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="srvgotattention-extended-stored-procedure-api"></a>srv_got_attention (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 現在の接続またはタスクを中断する必要があるかどうかをチェックし、接続が強制終了された場合、またはバッチが中断された場合に TRUE を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BOOL srv_got_attention (SRV_PROC *   
srvproc  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 *srvproc*  
 データベース接続を特定するポインターです。  
  
## <a name="return-value"></a>戻り値  
 接続が強制終了されたか、バッチが中断された場合に TRUE を返します。 接続またはバッチがアクティブであれば FALSE を返します。  
  
## <a name="remarks"></a>Remarks  
 実行時間の長い拡張ストアド プロシージャの場合は、**srv_got_attention** を定期的に呼び出してサーバーのアテンションをチェックすることにより、接続が強制終了されたかバッチが中断されたときに、そのプロシージャが自身を終了できるようにする必要があります。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
