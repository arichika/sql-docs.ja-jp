---
title: CommandType プロパティ (ADO) |Microsoft ドキュメント
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
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2008231e7daba12fbbabf81ce5e0e6b79b41cd80
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="commandtype-property-ado"></a>CommandType プロパティ (ADO)
型を示す、[コマンド](../../../ado/reference/ado-api/command-object-ado.md)オブジェクト。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 1 つまたは複数を取得または設定[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)値。  
  
> [!NOTE]
>  使用しないでください、 **CommandTypeEnum**値**adCmdFile**または**adCmdTableDirect**で**CommandType**です。 これらの値は、オプションとしてのみ使用できます、[開く](../../../ado/reference/ado-api/open-method-ado-recordset.md)と[Requery](../../../ado/reference/ado-api/requery-method.md)のメソッド、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
## <a name="remarks"></a>解説  
 使用して、 **CommandType**プロパティの評価を最適化するために、 [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)プロパティです。  
  
 場合、 **CommandType**プロパティ値が既定値に設定**adCmdUnknown**、ADO かどうかをするプロバイダーを呼び出す必要があるためにパフォーマンスの低下が発生する可能性があります、 **CommandText**プロパティは、SQL ステートメント、ストアド プロシージャ、またはテーブル名。 コマンドの種類を使用している場合は、設定、 **CommandType**プロパティ ADO では、関連するコードに直接移動するように指示します。 場合、 **CommandType**プロパティは、コマンドの種類と一致しません、 **CommandText**プロパティを呼び出すときにエラーが発生した、 [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)メソッドです。  
  
## <a name="applies-to"></a>適用対象  
 [Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの使用例 (vc++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、CommandText、CommandTimeout、CommandType、サイズ、および方向プロパティの例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
