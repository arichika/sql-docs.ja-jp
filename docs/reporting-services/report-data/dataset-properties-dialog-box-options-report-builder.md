---
title: '[オプション] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-data
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- "10020"
- sql13.rtp.rptdesigner.datasetproperties.options.f1
- "10130"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
caps.latest.revision: 15
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 411fe1b3d55ec8ad34120fd69ee129910e75a6b0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dataset-properties-dialog-box-options-report-builder"></a>[オプション] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  **[データセットのプロパティ]** ダイアログ ボックスの **[オプション]** を選択すると、照合順序オプションや小計を詳細行として処理するオプションなど、クエリのデータ オプションを変更できます。 照合順序の詳細については、 [SQL Server オンライン ブック](../../relational-databases/collations/collation-and-unicode-support.md) の「 [照合順序と Unicode のサポート](http://go.microsoft.com/fwlink/?linkid=98335)」を参照してください。  
  
 レポート サーバー上の共有データセット定義の一部であるデータ オプションは、共有データセットを使用するすべてのレポートに影響を及ぼします。 共有データセットのオプションは、レポートに追加した後にオーバーライドできます。 これらの変更は、オプションが定義されているレポートのみに影響を及ぼします。  
  
 埋め込みデータセットのデータ オプションは、オプションが定義されているレポートのみに影響を及ぼします。  
  
 詳細については、「 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[照合順序]**  
 データの並べ替えに使用される照合順序を決めるロケールを選択します。 **[既定]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。 値を取得できない場合、既定値はコンピューターのロケール設定から取得されます。  
  
 **大文字と小文字の区別**  
 大文字と小文字の区別を決める値を選択します。 データが大文字と小文字を区別するかどうかを示します。 **[大文字と小文字の区別]** は、 **[True]**、 **[False]**、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーが大文字と小文字の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[アクセントの区別]**  
 アクセントの区別を決める値を選択します。 **[アクセントの区別]** は、データでアクセントを区別するかどうかを示します。 **[True]**、 **[False]**、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーがアクセントの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[かなの区別]**  
 かなの区別を決める値を選択します。 データでかなを区別するかどうかを示します。 **[True]**、 **[False]**、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーがかなの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[文字幅の区別]**  
 文字幅の区別を決める値を選択します。 データで文字幅を区別するかどうかを示します。 **[True]**、 **[False]**、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。 データ プロバイダーが文字幅の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。 値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。  
  
 **[小計を詳細行として解釈]**  
 集計行ではなく詳細行として小計行を解釈するかどうかを示す値を選択します。 既定値は **[自動]** で、レポートがデータセット内のフィールドへのアクセスに **Aggregate**() 関数を使用しない場合に、小計行を詳細行として処理する必要があることを示します。 小計行を集計行として解釈する必要がある場合は、 **[False]** を選択します。 小計行を詳細行として解釈する必要があり、小計行で **Aggregate**() 関数が使用されていないことがわかっている場合は、 **[True]** を選択します。  
  
## <a name="see-also"></a>参照  
 [レポート ビルダーのダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [集計関数 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-function.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [[クエリ] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)](../../reporting-services/report-data/dataset-properties-dialog-box-query-report-builder.md)  
  
  
