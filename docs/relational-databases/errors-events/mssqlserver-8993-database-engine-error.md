---
title: MSSQLSERVER_8993 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8993 (Database Engine error)
ms.assetid: 06aac110-a41c-4853-bc8e-a83e8535b8be
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cbe279437fdc5839a635128ab24b53a898c661af
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver8993"></a>MSSQLSERVER_8993
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|8993|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBCC3_MISSING_FORWARDED_ROW|  
|メッセージ テキスト|オブジェクト ID O_ID、転送元の行のページ P_ID1、スロット S_ID1 は、ページ P_ID2、スロット S_ID2 を指しています。 転送先の行が見つかりません。 アロケーション エラーが発生した可能性があります。|  
  
## <a name="explanation"></a>説明  
ヒープ内の転送元の行が、存在しない転送先の行を指しています。  
  
## <a name="user-action"></a>ユーザーの操作  
  
### <a name="look-for-hardware-failure"></a>ハードウェア障害を調査する  
ハードウェアの診断を実行し、問題があれば修正します。 また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを調査し、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。 ログに記録されているハードウェアに関する問題があれば、それを修正します。  
  
データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。 システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。 書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。  
  
それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。 導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。  
  
### <a name="restore-from-backup"></a>バックアップから復元する  
問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。  
  
### <a name="run-dbcc-checkdb"></a>DBCC CHECKDB の実行  
クリーン バックアップがない場合には、REPAIR 句を付けずに DBCC CHECKDB を実行して破損の程度を調べます。 DBCC CHECKDB によって使用が推奨される REPAIR 句が表示されたら、 適切な REPAIR 句を付けて DBCC CHECKDB を実行し、破損を修復します。  
  
> [!CAUTION]  
> REPAIR 句を付けて DBCC CHECKDB を実行した場合にデータにどのような影響があるか確信がない場合は、ステートメントを実行する前に購入元にお問い合わせください。  
  
いずれかの REPAIR 句を付けて DBCC CHECKDB を実行しても問題が解決しない場合は、購入元にお問い合わせください。  
  
#### <a name="results-of-running-repair-options"></a>REPAIR オプションの実行結果  
転送元の行は削除され、非クラスター化インデックスはすべて再構築されます。  
  
