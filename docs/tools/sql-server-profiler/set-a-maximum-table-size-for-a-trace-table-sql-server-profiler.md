---
title: トレース テーブルの最大テーブル サイズの設定 (SQL Server Profiler) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.suite: sql
ms.technology: profiler
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- size [SQL Server], trace tables
- maximum table size for traces
ms.assetid: d0ae83e5-1c88-4a2e-be05-2c341280b978
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6778240b62eb801dfc9d183f02976e443f45ac67
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MTE
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="set-a-maximum-table-size-for-a-trace-table-sql-server-profiler"></a>トレース テーブルの最大テーブル サイズの設定 (SQL Server Profiler)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  このトピックでは、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]を使用して、トレース テーブルの最大テーブル サイズを設定する方法について説明します。  
  
### <a name="to-set-a-maximum-table-size-for-a-trace-table"></a>トレース テーブルの最大テーブル サイズを設定するには  
  
1.  **[ファイル]** メニューの **[新しいトレース]** をクリックし、SQL Server のインスタンスに接続します。  
  
     **[トレースのプロパティ]** ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  **[接続の確立直後にトレースを開始する]** チェック ボックスがオンになっている場合、 **[トレースのプロパティ]** ダイアログ ボックスは表示されず、すぐにトレースが開始されます。 この設定を無効にするには、 **[ツール]** メニューの **[オプション]** をクリックし、 **[接続の確立直後にトレースを開始する]** チェック ボックスをオフにします。  
  
2.  **[トレース名]** ボックスに、トレースの名前を入力します。  
  
3.  **[テンプレート名]** ボックスの一覧で、トレース テンプレートを選択します。  
  
4.  **[テーブルに保存]** チェック ボックスをオンにします。  
  
5.  トレースを格納するサーバーに接続します。  
  
     **[キャプチャ先テーブル]** ダイアログ ボックスが表示されます。  
  
6.  **[データベース]** ボックスの一覧から、トレースするデータベースを選択します。  
  
7.  **[テーブル]** ボックスで、テーブル名を入力するか、選択します。  
  
8.  **[最大行数の設定 (1000 行単位)]** チェック ボックスをオンにし、トレース テーブルの最大行数を指定します。  
  
    > [!NOTE]  
    >  テーブル内の行数が、指定した最大数を超えると、トレース イベントは記録されなくなります。 ただし、トレースは続行されます。  
  
## <a name="see-also"></a>参照  
 [[SQL Server Profiler]](../../tools/sql-server-profiler/sql-server-profiler.md)   
 [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  
