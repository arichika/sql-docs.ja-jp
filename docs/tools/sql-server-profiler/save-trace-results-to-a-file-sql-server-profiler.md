---
title: トレース結果のファイルへの保存 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: sql-server-profiler
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- saving traces
- traces [SQL Server], saving
ms.assetid: ac528747-0c19-4f3d-96f5-44c762a4abed
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ca51815b413f23cd006e1e08b359630e11259a18
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="save-trace-results-to-a-file-sql-server-profiler"></a>トレース結果のファイルへの保存 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース結果をファイルに保存する方法について説明します。  
  
### <a name="to-save-trace-results-to-a-file"></a>トレース結果をファイルに保存するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **[ファイルに保存する]** チェック ボックスをオンにします。  
  
     **[名前を付けて保存]** ダイアログ ボックスが表示されます。  
  
4.  **[名前を付けて保存]** ダイアログ ボックスでパスとファイル名を指定します。 **[保存]** をクリックします。  
  
    > [!NOTE]  
    >  SQL Server サービスに、指定したディレクトリのファイルに対して書き込めるアクセス許可があることを確認します。  
  
5.  **[トレースのプロパティ]** ダイアログ ボックスの **[最大ファイル サイズの設定 (MB)]** ボックスに、ファイルの最大サイズを入力します。 既定値は 5 MB です。  
  
6.  必要に応じて、次のオプションを指定します。  
  
    -   **[ファイル ロールオーバーを有効にする]** チェック ボックスをオンにすると、最大ファイル サイズに達したとき、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] によりトレース データ用の新しいファイルが作成されます。 既定では、このオプションはオンになっています。  
  
    -   **[サーバーがトレース データを処理する]** チェック ボックスをオンにすると、サーバーにより、すべてのトレース イベントが記録されます。  
  
        > [!NOTE]  
        >  **[サーバーがトレース データを処理する]** チェック ボックスをオフにすると、イベントを記録することが原因でパフォーマンスが大幅に低下する場合、イベントは記録されなくなります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
