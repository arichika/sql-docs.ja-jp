---
title: キューブ階層のプロパティの定義 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 65cd9ae51a89e32c85b46da0c8f14f0c9a593976
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="define-cube-hierarchy-properties"></a>キューブ階層のプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブ階層のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のユーザー定義階層に一意の設定を指定できます。 次の表では、キューブ階層のプロパティについて説明します。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**有効**|キューブ ディメンションの階層が有効かどうかを決定します。|  
|**HierarchyID**|階層の一意の識別子 (ID) を格納します。|  
|**OptimizedState**|階層に適用される最適化のレベルを決定します。 このプロパティは、以下の値をとります。<br /><br /> **FullyOptimized**:<br />                    インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> **NotOptimized**:<br />                    インスタンスは追加のインデックスを構築しません。|  
|**[表示]**|キューブ階層の表示を決定します。 既定値は **True**です。|  
  
## <a name="see-also"></a>参照  
 [ユーザー階層](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/user-hierarchies.md)  
  
  
