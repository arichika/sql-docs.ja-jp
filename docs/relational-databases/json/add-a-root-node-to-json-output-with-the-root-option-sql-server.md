---
title: "ROOT オプションを使用して JSON 出力にルート ノードを追加する (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/02/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ROOT (FOR JSON)"
ms.assetid: b9afa74a-f59f-483e-a178-42be2e9882c9
caps.latest.revision: 16
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 15
---
# ROOT オプションを使用して JSON 出力にルート ノードを追加する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  **FOR JSON** 句の JSON 出力に最上位の単一要素を追加するには、**ROOT** オプションを指定します。  
  
 **ROOT** オプションを指定しないと、JSON 出力にルート要素が含まれません。  
  
## 使用例  
 次の表に、 **ROOT** オプションを指定した場合と指定しなかった場合の **FOR JSON** 句の出力例を示します。  
  
 次の表の例では、追加の *RootName* 引数が空であると想定しています。 ルート要素に名前を指定すると、例の **root** の値がこの値に置き換わります。  
  
 **ROOT** オプションを指定しなかった場合  
  
```json  
{  
   <<json properties>>  
}  
```  
  
```json  
[  
   <<json array elements>>  
]  
```  
  
 **ROOT** オプションを指定した場合  
  
```json  
{   
  "root": {  
   <<json properties>>  
 }  
}  
```  
  
```json  
{   
  "root": [  
   << json array elements >>  
  ]  
}  
```  
  
 次に、 **FOR JSON** 句で **ROOT** オプションを指定した別の例を示します。 この例では、追加の *RootName* 引数に値を指定します。  
  
 **クエリ**  
  
```tsql  
SELECT TOP 5   
      BusinessEntityID As Id,  
      FirstName, LastName,  
      Title As 'Info.Title',  
      MiddleName As 'Info.MiddleName'  
  FROM Person.Person  
  FOR JSON PATH, ROOT('info')  
```  
  
 **結果**  
  
```json  
{  
  "info": [  
    {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
    {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
    {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
    {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
    {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
  ]  
}  
  
```  
  
 **結果 (root 指定なし)**  
  
```json  
[  
  {"Id":1,"FirstName":"Ken","LastName":"Sánchez","Info":{"MiddleName":"J"}},  
  {"Id":2,"FirstName":"Terri","LastName":"Duffy","Info":{"MiddleName":"Lee"}},  
  {"Id":3,"FirstName":"Roberto","LastName":"Tamburello"},  
  {"Id":4,"FirstName":"Rob","LastName":"Walters"},  
  {"Id":5,"FirstName":"Gail","LastName":"Erickson","Info":{"Title":"Ms.","MiddleName":"A"}}  
]  
  
```  
  
## 参照  
 [FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)  
  
  