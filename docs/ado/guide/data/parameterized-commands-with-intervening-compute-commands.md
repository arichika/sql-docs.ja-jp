---
title: 介在するコンピューティング コマンドを使用するコマンドをパラメーター化された |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
- APPEND clause [ADO]
- COMPUTE command [ADO]
ms.assetid: 732f624f-8900-4608-9815-194302d22e8b
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2affa34fd504397b045e100ec8f07232d6dfec7e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="parameterized-commands-with-intervening-compute-commands"></a>パラメーター化コマンドの介在するコンピューティング コマンド
通常、パラメーター化された shape APPEND コマンドは親によって作成される句**レコード セット**クエリ コマンドと、子を作成する別の句**レコード セット**パラメーター化されたクエリ コマンドを使って —パラメーターのプレース ホルダーを含むコマンドは、(疑問符 ()、"?") です。 シェイプ**Recordset**親が上位のレベルを占有する、2 つのレベルがあり、子は、下位のレベルを占有します。  
  
 子が作成される句**Recordset**できるようになりました任意の数の入れ子になった図形コンピューティング コマンドでは、最も深く入れ子になったコマンドにパラメーター化クエリが含まれています。 シェイプ**レコード セット**親が最上位のレベルを占有する複数のレベルには、子占有低位側のレベル、および任意の数の**Recordset**s によって生成された、図形のコンピューティングのコマンドは、介在するレベルを占有します。  
  
 介在するを作成するためのコマンドこの機能は、集計関数および shapeCOMPUTE のグループ化機能を呼び出すための典型的な使用**Recordset**子に関する分析情報を持つオブジェクト**レコード セット**. さらに、これは、パラメーター化された shape コマンドであるため、毎回、親のチャプター列は、新しい子**Recordset**取得することがあります。 派生するため、介在するレベルは、子から、それらも再計算されます。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)
