---
title: フィルター式の例 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filtering data [Reporting Services], filter equation examples
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
caps.latest.revision: 18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8a0a69e9c22d287b8cf1db86e7d62f19a3df7b90
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="filter-equation-examples-report-builder-and-ssrs"></a>フィルター式の例 (レポート ビルダーおよび SSRS)
  フィルターを作成するには、1 つ以上のフィルター式を指定する必要があります。 フィルター式には、式、データ型、演算子、および値が含まれます。 ここでは、一般的に使用されるフィルターの例を示します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>フィルターの例  
 次の表は、さまざまなデータ型と演算子を使用するフィルター式の例を示します。 比較のスコープは、フィルターが定義されたレポート アイテムによって決まります。 たとえば、データセットに定義されたフィルターの場合、 **[上位 10%]** はデータセットの値の上位 10% になります。グループに定義されたフィルターの場合、 **[上位 10%]** はグループの値の上位 10% になります。  
  
|単純式|データ型|演算子|ReplTest1|Description|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|**Integer**|**>**|`7`|7 より大きいデータ値が含まれます。|  
|`[SUM(Quantity)]`|**Integer**|**TOP N**|`10`|上位 10 データ値が含まれます。|  
|`[SUM(Quantity)]`|**Integer**|**TOP %**|`20`|上位 20% のデータ値が含まれます。|  
|`[Sales]`|**テキスト**|**>**|`=CDec(100)`|$100 より大きい System.Decimal 型 (SQL "money" データ型) のすべての値が含まれます。|  
|`[OrderDate]`|**DateTime**|**>**|`2008-01-01`|2008 年 1 月 1 日から現在の日付までのすべての日付が含まれます。|  
|`[OrderDate]`|**DateTime**|**BETWEEN**|`2008-01-01`<br /><br /> `2008-02-01`|2008 年 1 月 1 日から 2008 年 2 月 1 日までの日付が含まれます。|  
|`[Territory]`|**テキスト**|**LIKE**|`*east`|最後に "east" が付くすべての販売区域名。|  
|`[Territory]`|**テキスト**|**LIKE**|`%o%th*`|名前の先頭に North と South が含まれるすべての販売区域名。|  
|`=LEFT(Fields!Subcat.Value,1)`|**テキスト**|**IN**|`B, C, T`|B、C、T のいずれかの文字で始まるすべてのサブカテゴリ値。|  
  
## <a name="see-also"></a>参照  
 [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [データセット フィルター、データ領域フィルター、およびグループ フィルターの追加 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)   
 [式で使用されるデータ型 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [レポートでの式の使用 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [式の例 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)  
  
  
