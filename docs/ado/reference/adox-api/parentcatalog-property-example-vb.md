---
title: ParentCatalog プロパティの例 (VB) |Microsoft ドキュメント
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
dev_langs:
- VB
helpviewer_keywords:
- ParentCatalog property [ADOX], Visual Basic example
ms.assetid: 448bc850-7584-4c5f-89f3-5f4fee88b259
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6d6c999e0df8036f64a949704309088bce4a145
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="parentcatalog-property-example-vb"></a>ParentCatalog プロパティの例 (VB)
次のコードを使用する方法を示しています、 [ParentCatalog](../../../ado/reference/adox-api/parentcatalog-property-adox.md)カタログにテーブルを追加する前に、プロバイダー固有のプロパティにアクセスするプロパティです。 このプロパティは**AutoIncrement**、Microsoft Jet データベースで自動増分 フィールドを作成します。  
  
```  
' BeginCreateAutoIncrColumnVB  
Sub Main()  
    On Error GoTo CreateAutoIncrColumnError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As New ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
  
    With tbl  
        .Name = "MyContacts"  
        Set .ParentCatalog = cat  
        ' Create fields and append them to the new Table object.  
        .Columns.Append "ContactId", adInteger  
        ' Make the ContactId column and auto incrementing column  
        .Columns("ContactId").Properties("AutoIncrement") = True  
        .Columns.Append "CustomerID", adVarWChar  
        .Columns.Append "FirstName", adVarWChar  
        .Columns.Append "LastName", adVarWChar  
        .Columns.Append "Phone", adVarWChar, 20  
        .Columns.Append "Notes", adLongVarWChar  
    End With  
  
    cat.Tables.Append tbl  
    Debug.Print "Table 'MyContacts' is added."  
  
    ' Delete the table as this is a demonstration.  
    cat.Tables.Delete tbl.Name  
    Debug.Print "Table 'MyContacts' is delete."  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set tbl = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CreateAutoIncrColumnError:  
  
    Set cat = Nothing  
    Set tbl = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
  
End Sub  
' EndCreateAutoIncrColumnVB  
```  
  
## <a name="see-also"></a>参照  
 [Append メソッド (ADOX 列)](../../../ado/reference/adox-api/append-method-adox-columns.md)   
 [Append メソッド (ADOX テーブル)](../../../ado/reference/adox-api/append-method-adox-tables.md)   
 [カタログ オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Column オブジェクト (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [Columns コレクション (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [Name プロパティ (ADOX)](../../../ado/reference/adox-api/name-property-adox.md)   
 [ParentCatalog プロパティ (ADOX)](../../../ado/reference/adox-api/parentcatalog-property-adox.md)   
 [Table オブジェクト (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Type プロパティ (列) (ADOX)](../../../ado/reference/adox-api/type-property-column-adox.md)
