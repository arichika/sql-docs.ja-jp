---
title: MSSQLSERVER_3619 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3619 (Database Engine error)
ms.assetid: 7d94f8d9-65ca-4fde-9c17-7b83e94a3779
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f487685e727f9f5ccf3862ac62cf0f1e21fb78ea
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver3619"></a>MSSQLSERVER_3619
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3619|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SYS_NOLOG|  
|メッセージ テキスト|ログに空き領域がないので、データベース ID %d にチェックポイント レコードを書き込めませんでした。 データベース管理者に問い合わせて、ログを切り捨てるか、データベース ログ ファイルに追加領域を割り当ててください。|  
  
## <a name="explanation"></a>説明  
トランザクション ログ用のディスク容量が不足しています。  
  
## <a name="user-action"></a>ユーザーの操作  
ログの切り捨てを行って容量を解放するか、ログ ファイルに追加領域を割り当てます。 詳細については、SQL Server オンライン ブックの「満杯になったトランザクション ログのトラブルシューティング (エラー 9002)」を参照してください。  
  
