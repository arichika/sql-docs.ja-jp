---
title: MSSQLSERVER_833 | Microsoft Docs
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
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fd32f5eb35a0d938e60e3ea43aa8428a4b458930
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver833"></a>MSSQLSERVER_833
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|833|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|BUF_LONG_IO|  
|メッセージ テキスト|SQL Server は、データベース `[%ls] (%d)` のファイル [%ls] で、完了に %d 秒以上かかった I/O 要求を %d 個検出しました。  OS ファイル ハンドルは 0x%p です。  最新の実行時間の長い I/O のオフセットは %#016I64x です。|  
  
## <a name="explanation"></a>説明  
このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスクからの読み取り要求やディスクへの書き込み要求を発行してからその要求が完了するまでの時間が 15 秒を超えたことを示しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からこのエラーが報告された場合は、IO サブシステムに問題があります。  
  
### <a name="possible-causes"></a>考えられる原因  
この問題の原因としては、システム パフォーマンスの問題、ハードウェア エラー、ファームウェア エラー、デバイス ドライバーの問題、IO プロセスへのフィルター ドライバーの介入などが考えられます。  
  
## <a name="user-action"></a>ユーザーの操作  
このエラーのトラブルシューティングを行うには、システム イベント ログを参照し、ハードウェア関連のエラー メッセージが記録されているかどうかを調べます。 また、可能な場合はハードウェア固有のログも調べます。  
  
パフォーマンス モニターを使用して、次のカウンターを調べます。  
  
-   **Average Disk Sec/Transfer**  
  
-   **Average Disk Queue Length**  
  
-   **Current Disk Queue Length**  
  
たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの **Average Disk Sec/Transfer** の時間は、通常 15 ミリ秒未満です。 **Avg. Disk sec/Transfer** の値が増加している場合、I/O サブシステムが I/O 要求を最適な速度で処理できていません。  
  
> [!NOTE]  
> ディスク アクセス速度は、ウイルス対策プログラムによって低下する場合があります。 アクセスを高速化するには、エラー メッセージに示されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ファイルをアクティブ ウイルス スキャンの対象から除外します。  
  
I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?LinkId=69370)」と、[http://support.microsoft.com/kb/897284/en-us](http://support.microsoft.com/kb/897284/en-us) にあるサポート技術情報の資料を参照してください。  
  
