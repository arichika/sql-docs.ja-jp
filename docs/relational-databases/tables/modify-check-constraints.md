---
title: CHECK 制約の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CHECK constraints, modifying
- modifying constraints
- constraints [SQL Server], check
- constraints [SQL Server], modifying
ms.assetid: f22daef8-e350-40ef-8ff0-b5f87d1d9e56
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4578301eabb2dc76f2a02dd9d556c29c8087a1e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="modify-check-constraints"></a>CHECK 制約の変更
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、制約式を変更するとき、または特定の条件の制約を有効または無効にするオプションを変更するときは、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)] を使用して CHECK 制約を変更できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **CHECK 制約を変更するための方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-a-check-constraint"></a>CHECK 制約を変更するには  
  
1.  **オブジェクト エクスプローラー**で、CHECK 制約を含むテーブルを右クリックし、 **[デザイン]** をクリックします。  
  
2.  **[テーブル デザイナー]** メニューの **[CHECK 制約]** をクリックします。  
  
3.  **[CHECK 制約]** ダイアログ ボックスの **[選択された制約のチェック]** で、編集する制約を選択します。  
  
4.  次の表の操作を完了します。  
  
    |変換先|手順|  
    |--------|------------------------|  
    |制約式を編集する。|**[式]** フィールドに新しい式を入力します。|  
    |制約名を変更する。|**[名前]** フィールドに新しい名前を入力します。|  
    |既存のデータに制約を適用する。|**[作成時または再度有効化するときに既存データを確認]** チェック ボックスをオンにします。|  
    |テーブルに新しいデータを追加する場合、またはテーブル内の既存のデータを更新する場合に、制約を無効にする。|**[INSERTs および UPDATEs に適用]** チェック ボックスをオフにします。|  
    |レプリケーション エージェントによってテーブルにデータが挿入された場合やデータが更新された場合に制約を無効にする。|**[レプリケーションに対して適用]** チェック ボックスをオフにします。|  
  
    > [!NOTE]  
    >  CHECK 制約に対して異なる機能を持つデータベースもあります。  
  
5.  **[閉じる]** をクリックします。  
  
6.  **[ファイル]** メニューの *[<テーブル名> を保存]* をクリックします。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 **CHECK 制約を変更するには**  
  
 `CHECK` を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)]制約を変更するには、最初に既存の `CHECK` 制約を削除してから、新しい定義を使用して再作成する必要があります。 詳細については、「 [CHECK 制約の削除](../../relational-databases/tables/delete-check-constraints.md) 」および「 [CHECK 制約の作成](../../relational-databases/tables/create-check-constraints.md)」を参照してください。  
  
###  <a name="TsqlExample"></a>  
