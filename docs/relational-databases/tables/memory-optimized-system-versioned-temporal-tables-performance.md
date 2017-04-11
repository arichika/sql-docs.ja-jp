---
title: "メモリ最適化およびシステム バージョン管理されたテンポラル テーブルのパフォーマンスに関する考慮事項 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e110984-7703-4806-a24b-b41e8c3018c6
caps.latest.revision: 14
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 12
---
# メモリ最適化およびシステム バージョン管理されたテンポラル テーブルのパフォーマンスに関する考慮事項
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、システム バージョン管理およびメモリ最適化されたテンポラル テーブルを使用する場合のパフォーマンスに関するいくつかの考慮事項について説明します。  
  
-   既存の非テンポラル テーブルにシステム バージョン管理を追加すると、履歴テーブルが自動的に更新されるため、更新操作および削除操作のパフォーマンスに影響が及ぶ可能性があります。  
  
-   更新操作および削除操作はすべて内部のメモリ最適化履歴テーブルに記録されるため、ワークロードでこれらの 2 つの操作が大量に使用される場合に予期しない量のメモリ消費が発生する可能性があります。 したがって、以下のことをお勧めします。  
  
    -   領域をクリーンアップして利用可能な RAM を増やすために、現在のテーブルに対する大量の削除操作を実行しない。 データの削除は、[sp_xtp_flush_temporal_history](../Topic/sp_xtp_flush_temporal_history.md) を手動で呼び出してデータ フラッシュを途中で実行しながら複数のバッチに分けて実行するか、または **SYSTEM_VERSIONING = OFF** のときに実行することを検討してください。  
  
    -   一度に大量のテーブルの更新を実行しない。そのような操作を実行すると、非テンポラル メモリ最適化テーブルの更新操作と比較して 2 倍の量のメモリが消費される場合があります。 メモリ消費量が 2 倍になる状態は一時的なものです。これは、定期的にデータ フラッシュ タスクが実行され、計画された境界内の内部ステージング テーブルのメモリ消費量が安定状態 (現在のテンポラル テーブルのメモリ使用量の約 10%) に保たれるためです。 大量の更新を実行するときは、複数のバッチに分けて実行するか、**SYSTEM_VERSIONING = OFF** のときに実行してください (更新を使用して、新しく追加された列の既定値を設定するなど)。  
  
-   データ フラッシュ タスクのアクティブ化の期間は構成できませんが、[sp_xtp_flush_temporal_history](../Topic/sp_xtp_flush_temporal_history.md) を呼び出すことによって、このプロセスを強制的に実行できます。  
  
-   履歴データに対して集計またはウィンドウ関数を使用する分析クエリを実行する場合は特に、クラスター化列ストアをディスクベースの履歴テーブルのストレージ オプションとして使用することを検討してください。 そのような場合の履歴テーブル用には、優れたデータ圧縮を提供し、履歴データの生成方法に合致して "挿入操作に対応" するクラスター化列ストアが最適です。  
  
## この記事は役に立ちましたか? フィードバックをお待ちしております。  
 どのような情報をお探しでしたか? お探しの情報は見つかりましたか? コンテンツ改善のため、フィードバックをお待ちしています。  [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Performance%20Considerations%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)にコメントをお寄せください。  
  
## 参照  
 [メモリ最適化テーブルでのシステム バージョン管理されたテンポラル テーブル](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [メモリ最適化のためのシステム バージョン管理されたテンポラル テーブルを作成する](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [メモリ最適化およびシステム バージョン管理されたテンポラル テーブルの使用](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [システムでバージョン管理されたメモリ最適化テンポラル テーブルの監視](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [テンポラル テーブル](../../relational-databases/tables/temporal-tables.md)   
 [テンポラル テーブルのシステム一貫性のチェック](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [テンポラル テーブル メタデータのビューおよび関数](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  