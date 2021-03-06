---
title: srv_alloc (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- srv_alloc
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_alloc
ms.assetid: 91505c59-a273-452f-b71d-5e8205c21863
caps.latest.revision: 32
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b95185ccec1d1c7c3be112340d4894df097f2617
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="srvalloc-extended-stored-procedure-api"></a>srv_alloc (拡張ストアド プロシージャ API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 メモリを動的に割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
  
void * srv_alloc ( DBINT  
size  
);  
```  
  
## <a name="arguments"></a>引数  
 *size*  
 割り当てるバイト数を指定します。  
  
## <a name="returns"></a>戻り値  
 新しく割り当てた領域を指すポインターを返します。 *size* で指定したバイト数を割り当てられない場合は、NULL ポインターを返します。  
  
## <a name="remarks"></a>Remarks  
 **srv_alloc** 関数は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows API の **GlobalAlloc** 関数に相当します。 拡張ストアド プロシージャ API アプリケーションでは、通常の Windows API C ランタイムのメモリ管理関数を使用できます。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)をご覧ください。  
  
  
