---
title: MSSQLSERVER_2519 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2519 (Database Engine error)
ms.assetid: 8dc6ad98-5db8-4c88-8dea-6d455e63b839
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a8998e454d58c1daa8f099f31d77529f54204631
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2519"></a>MSSQLSERVER_2519
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|2519|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC_NO_EXPRESSION_EVALUATOR|  
|メッセージ テキスト|内部の式エバリュエーターを初期化できなかったため、オブジェクト ID O_ID (オブジェクト "O_NAME") の計算列とユーザー定義型を確認できません。|  
  
## <a name="explanation"></a>説明  
この情報メッセージは、クエリ プロセッサが、計算列と CLR (common language runtime) ユーザー定義型を評価するための内部オブジェクトを DBCC に提供できなかったことを示しています。 つまり、計算列および CLR ユーザー定義型の正当性チェックが行われなかったり、DBCC でインデックスとベース テーブルの整合性をチェックする際に計算列が使用されないことを意味します。  
  
## <a name="user-action"></a>ユーザーの操作  
なし  
  
## <a name="see-also"></a>参照  
[MSSQLSERVER_2518](~/relational-databases/errors-events/mssqlserver-2518-database-engine-error.md)  
  
