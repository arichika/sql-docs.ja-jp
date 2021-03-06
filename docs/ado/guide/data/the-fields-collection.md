---
title: Fields コレクション |Microsoft ドキュメント
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
- Field object [ADO], fields collection
- Fields collection [ADO]
ms.assetid: 574cf36e-e5f5-403b-983c-749ef93c108f
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 35be5189e20c9f028c5d73a68aab90ac502b4dfc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="the-fields-collection"></a>Fields コレクション
**フィールド**コレクションは、ADO の組み込みコレクションの 1 つです。 コレクションは、単位としてに参照できる項目の順序付けされたセットです。 ADO コレクションの詳細については、次を参照してください。 [ADO オブジェクト モデル](../../../ado/guide/data/ado-objects-and-collections.md)です。  
  
 **フィールド**コレクションが含まれています、**フィールド**内のすべてのフィールド (列) のオブジェクト、 **Recordset**です。 ADO のすべてのコレクションと同様に**カウント**と**項目**プロパティだけでなく**Append**と**更新**メソッドです。 さらに、**ただし**、**削除**、**再同期**、および**更新**メソッドで、他の ADO コレクションにご利用いただけません。  
  
## <a name="examining-the-fields-collection"></a>フィールド コレクションを確認します。  
 検討してください、**フィールド**サンプルのコレクション**Recordset**ここで紹介します。 サンプル**Recordset** SQL ステートメントから派生しました  
  
```  
SELECT ProductID, ProductName, UnitPrice FROM Products WHERE CategoryID = 7  
```  
  
 したがって、する必要がありますと考えることが、**レコード セット フィールド**コレクションには、3 つのフィールドが含まれています。  
  
```  
'BeginWalkFields  
    Dim objFields As ADODB.Fields  
    Dim intLoop As Integer  
  
    objRs.Open strSQL, strConnStr, adOpenForwardOnly, adLockReadOnly, adCmdText  
  
    Set objFields = objRs.Fields  
  
    For intLoop = 0 To (objFields.Count - 1)  
        Debug.Print objFields.Item(intLoop).Name  
    Next  
'EndWalkFields  
```  
  
 このコードの数を指定するだけ**フィールド**内のオブジェクト、**フィールド**コレクションを使用して、**カウント**プロパティしの値を返す、コレクションをループ**名前**それぞれのプロパティ**フィールド**オブジェクト。 さらに多くを使用する**フィールド**プロパティ、フィールドに関する情報を取得します。 クエリの詳細については、**フィールド**を参照してください[フィールド Object](../../../ado/guide/data/the-field-object.md)です。  
  
## <a name="counting-columns"></a>列のカウント  
 ご想像、**カウント**の実際の数を返します**フィールド**内のオブジェクト、**フィールド**コレクション。 コレクションのメンバーの番号付けは 0 から始まるため、する必要がありますループ常に 0 から始まるの値で終わる、**カウント**から 1 を引いたプロパティです。 Microsoft Visual Basic を使用しているし、確認せずにコレクションのメンバーをループ処理する場合、**カウント**プロパティを使用して、**ごとにしています.[次へ]** コマンド。  
  
 場合、**カウント**プロパティが 0 で、コレクションにオブジェクトがありません。  
  
## <a name="getting-to-the-field"></a>フィールドを取得します。  
 ADO コレクションと同様、**項目**プロパティは、コレクションの既定のプロパティです。 個人が返されます**フィールド**名前で指定されたオブジェクトまたはインデックスに渡されます。 したがって、次のステートメントは、サンプルのと同じ**Recordset**:  
  
```  
objField = objRecordset.Fields.Item("ProductID")  
objField = objRecordset.Fields("ProductID")  
objField = objRecordset.Fields.Item(0)  
objField = objRecordset.Fields(0)  
```  
  
 これらのメソッドと同じ場合は、最適なしますか。 事によりけりです。 取得するインデックスを使用して、**フィールド**コレクションからは、高速にアクセスするため、**フィールド**文字列参照を実行する必要なく、直接です。 その一方の順序**フィールド**、コレクション内で認識される必要があります、し、順序を変更への参照、**フィールドの**インデックスが常に変更する必要があります。 名前を使用して少し遅くなりますが、**フィールド**の順序に依存しないためにより柔軟性が、**フィールド**コレクション内で。  
  
## <a name="using-the-refresh-method"></a>更新メソッドを使用します。  
 その他の ADO コレクションによって、使用するとは異なり、**更新**メソッドを**フィールド**コレクションが表示される影響を与えません。 基になるデータベース構造から変更を取得する、いずれかを使用する必要があります、 **Requery**メソッド、または、**レコード セット**オブジェクトは、ブックマークをサポートしていません、 **MoveFirst**メソッドで、プロバイダーに対してもう一度実行するコマンドが発生します。  
  
## <a name="adding-fields-to-a-recordset"></a>レコード セットにフィールドを追加します。  
 **Append**メソッドを使用して、フィールドを追加、 **Recordset**です。  
  
 使用することができます、**追加**を生成するメソッド、 **Recordset**データ ソースへの接続を開かずにプログラムでします。 実行時エラーが発生、 **Append**メソッドが、**フィールド**の開いているコレクション**レコード セット**または、**レコード セット**ここで、 **ActiveConnection**プロパティが設定されています。 のみフィールドを追加できる、 **Recordset**が開かれていないと、データ ソースに接続されていません。 ただし、新たに追加の値を指定する**フィールド**、 **Recordset**を開いておく必要があります。  
  
 開発者には、一時的に一部のデータを格納または一部のデータが機能するように、ユーザー インターフェイスのデータ バインドに参加できるように、サーバーから送信する場所が必要があります。 ADO (と組み合わせて、 [OLE DB 用の Microsoft カーソル サービス](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md)) により、開発者は、空のビルド**Recordset**列情報を指定して呼び出すことでオブジェクト**を開く**. 次の例では、次の 3 つの新しいフィールドは、新しいに追加されます**Recordset**オブジェクト。 **レコード セット**を開くと、2 つの新しいレコードを追加、および**レコード セット**ファイルに保存されます。 (の詳細については**Recordset**永続化ストアを参照してください[更新およびデータの永続化](../../../ado/guide/data/updating-and-persisting-data.md))。  
  
```  
'BeginFabricate  
    Dim objRs As ADODB.Recordset  
    Set objRs = New ADODB.Recordset  
  
    With objRs.Fields  
        .Append "StudentID", adChar, 11, adFldUpdatable  
        .Append "FullName", adVarChar, 50, adFldUpdatable  
        .Append "PhoneNmbr", adVarChar, 20, adFldUpdatable  
    End With  
  
    With objRs  
        .Open  
  
        .AddNew  
        .Fields(0) = "123-45-6789"  
        .Fields(1) = "John Doe"  
        .Fields(2) = "(425) 555-5555"  
        .Update  
  
        .AddNew  
        .Fields(0) = "123-45-6780"  
        .Fields(1) = "Jane Doe"  
        .Fields(2) = "(615) 555-1212"  
        .Update  
    End With  
  
    objRs.Save App.Path & "FabriTest.adtg", adPersistADTG  
  
    objRs.Close  
'EndFabricate  
```  
  
 使用法、**フィールドの追加**メソッドがの間で異なれば、**レコード セット**オブジェクトおよび**レコード**オブジェクト。 詳細については、**レコード**オブジェクトを参照してください[レコードとストリーム](../../../ado/guide/data/records-and-streams.md)です。  
  
## <a name="see-also"></a>参照  
 [階層レコードセットの作成](../../../ado/guide/data/fabricating-hierarchical-recordsets.md)
