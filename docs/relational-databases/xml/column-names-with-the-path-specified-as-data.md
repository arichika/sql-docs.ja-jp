---
title: "パスを data() として指定した列の名前 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "名前 [SQL Server], 列"
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
caps.latest.revision: 10
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 10
---
# パスを data() として指定した列の名前
  列名として指定したパスが "data()" の場合、生成される XML では列の値がアトミック値として処理されます。 シリアル化時の後続アイテムもアトミック値である場合は、空白文字が XML に追加されます。 これはリスト状の要素値または属性値を作成する場合に有用です。 次のクエリでは、製品モデルの ID および名前と、そのモデルに含まれる製品のリストを取得します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 入れ子の内側の SELECT では、製品 ID のリストを取得しています。 製品 ID の列名が "data()" と指定されています。 PATH モードでは空文字列が行の要素名に指定されるので、ここでは行要素は生成されません。 代わりに、親の SELECT で指定した <`ProductModelData`> 行要素の ProductIDs 属性に設定された値が返されます。 結果を次に示します。  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## 参照  
 [FOR XML での PATH モードの使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  