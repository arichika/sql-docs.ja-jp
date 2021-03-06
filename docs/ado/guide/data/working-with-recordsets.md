---
title: レコード セットの操作 |Microsoft ドキュメント
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
- Recordset object [ADO]
ms.assetid: bdf9a56a-de4a-44de-9111-2f11ab7b16ea
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b83fb8d5ad4e2e063ca840b7e8fb31bbf15fde14
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-recordsets"></a>レコード セットの操作
**Recordset**オブジェクトが組み込みの機能を指定する条件に基づいて特定のレコードを検索して、インデックスを使用してこれらの検索操作を最適化するためにも、結果セット内のデータの順序を変更することができます。 これらの機能を使用できるかどうかは、プロバイダーによって異なります: などの[インデックス](../../../ado/reference/ado-api/index-property.md)プロパティ — データ ソース自体の構造。  
  
## <a name="arranging-data"></a>データの整列  
 多くの場合、最も効率的にデータを並べ替えるため、 **Recordset**に結果を返すために使用する SQL コマンドに ORDER BY 句を指定することによって、します。 ただし、データの順序を変更する必要があります、 **Recordset**を既に作成されています。 使用することができます、**並べ替え**プロパティの行の順序を確立するために、**レコード セット**スキャンされます。 さらに、**フィルター**プロパティを指定する行の行を走査する場合にアクセスできます。  
  
 **並べ替え**プロパティを設定または取得、**文字列**内のフィールドを示す値名、 **Recordset**並べ替えを行う。 それぞれの名前をコンマで区切ってし、スペースと、キーワードに続けて**ASC** (フィールドを昇順に並べ替え) または**DESC** (降順にフィールドの並べ替え) します。 既定では、キーワードが指定されていない場合、フィールドが昇順で並べ替えられます。  
  
 並べ替え操作は、データが物理的に並べ替えられることはできませんが、インデックスによって指定された順序でアクセスするために効率的です。  
  
 **並べ替え**プロパティが必要です、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)設定するプロパティを**adUseClient**です。 指定された各フィールドに一時インデックスが作成されます、**並べ替え**プロパティ、インデックスが既に存在しない場合。  
  
 設定、**並べ替え**プロパティを空の文字列には行は元の順序にリセットされ、一時的なインデックスを削除します。 既存のインデックスは削除されません。  
  
 たとえば、**レコード セット**という 3 つのフィールドが含まれています*firstName*、 *[middleinitial]* と*lastName*です。 設定、**並べ替え**プロパティを文字列に"`lastName DESC, firstName ASC`"、順序は、 **Recordset**姓の順序を降順で、最初名順で昇順に並べ替えます。 ミドル ネームのイニシャルは無視されます。  
  
 フィールドの並べ替え条件の文字列で参照されている名前を指定できますなし"ASC"または"DESC"キーワードとそれらの名前が競合するため**ASC**と**DESC**です。 名前を持つ、競合するエイリアスを使用してフィールドを付ける、 **AS**を返すクエリ内のキーワード、 **Recordset**です。  
  
 詳細については**Recordset**フィルター処理すると、このトピックの「"結果をフィルター処理する"を参照してください。  
  
## <a name="finding-a-specific-record"></a>特定のレコードを検索します。  
 ADO の提供、[検索](../../../ado/reference/ado-api/find-method-ado.md)と[シーク](../../../ado/reference/ado-api/seek-method.md)の特定のレコードを検索するためのメソッド、**レコード セット**です。 **検索**メソッドはさまざまなプロバイダーがサポートされますが、1 つの検索条件に制限されます。 **シーク**メソッドは、複数の条件で検索をサポートしていますが、多くのプロバイダーでサポートされていません。  
  
 フィールドのインデックスのパフォーマンスが向上、**検索**メソッドおよび**並べ替え**と**フィルター**のプロパティ、 **Recordset**オブジェクト。 内部のインデックスを作成することができます、**フィールド**、動的に設定してオブジェクト[最適化](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)プロパティです。 この動的プロパティに追加、**プロパティ**のコレクション、**フィールド**オブジェクトを設定するとき、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティを**adUseClient**. ただし、このインデックスは ADO 内部 — へのアクセス権を獲得または他の目的に使用することはできません。 また、このインデックスとは異なります、[インデックス](../../../ado/reference/ado-api/index-property.md)のプロパティ、 **Recordset**オブジェクト。  
  
 **検索**メソッドは、の列 (フィールド) 内の値をすばやく検索、 **Recordset**です。 頻繁の速度を向上することができます、**検索**メソッドを使用して列を**最適化**プロパティをインデックスを作成します。  
  
 **検索**メソッドは、検索対象を 1 つのフィールドの内容を制限します。 **シーク**にインデックスであるし、その他の制限がありますもメソッドが必要です。 かどうか、インデックスのベースではない複数のフィールドを検索する必要がありますかを使用して、結果を制限するには、プロバイダーがインデックスをサポートしていない場合、**フィルター**のプロパティ、 **Recordset**オブジェクト。  
  
### <a name="find"></a>[検索]  
 **検索**メソッドを検索、**レコード セット**を指定した条件を満たす行にします。 必要に応じて、検索、開始行、および開始行からのオフセットの方向を指定することがあります。 見つかったレコードです。 現在の行位置を設定、条件が満たされた場合それ以外の場合、位置に設定されている (先頭または末尾) の**Recordset**検索の方向に応じて、します。  
  
 条件の単一列の名前のみを指定できます。 つまり、このメソッドは複数列の検索をサポートしていません。  
  
 条件の比較演算子を指定できます"**>**「(より大きい)、」**\<**"(より小さい)、「=」(等しい)、"> ="(より大きいまたは等しい)、"< ="(以下)、"<>"(等しくない)、または「のように」(パターン一致)。  
  
 基準値には、文字列、浮動小数点数、または日付を指定できます。 文字列の値が単一引用符または「#」(シャープ記号) 記号で区切られた (たとえば、"状態 = 'WA'"または"の状態 = WA #") です。 日付の値は「#」(シャープ記号) 記号で区切られます (たとえば、"start_date > #7 月 22 日/97 #") です。  
  
 比較演算子が"like"にある場合は、文字列値は、アスタリスク (*) を 1 つ以上の出現箇所を任意の文字または部分文字列の検索を含めることができます。 たとえば、"のような状態にして\*'"メイン州と Massachusetts に一致します。 また、値に含まれる部分文字列を検索するのに先頭および末尾のアスタリスクを使用することができます。 たとえば、"のような状態 '\*として\*'"アラスカ、アーカンソー、Massachusetts に一致します。  
  
 アスタリスクできる条件の文字列の末尾でのみまたは組み合わせて使用先頭と条件の文字列の末尾の両方で前に示したようです。 先頭のワイルドカードとしてアスタリスクを使用することはできません ('* str')、または埋め込みワイルドカード ('s\*r')。 これにより、エラーが発生します。  
  
### <a name="seek-and-index"></a>シークおよびインデックス  
 使用して、**シーク**メソッドと共に、**インデックス**基になるプロバイダーのインデックスをサポートする場合は、プロパティ、 **Recordset**オブジェクト。 使用して、[サポート](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** 基になるプロバイダーがサポートしているかどうかを判断するメソッド**シーク**、および**Supports(adIndex)** プロバイダーはインデックスをサポートするかどうかを判断するメソッドです。 (たとえば、 [OLE DB Provider for Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)をサポートしている**シーク**と**インデックス**)。  
  
 場合**シーク**は検索対象の行では、エラーはありませんが発生すると、およびその行がの末尾に配置されている、 **Recordset**です。 設定、**インデックス**にこのメソッドを実行する前に目的のインデックスのプロパティです。  
  
 このメソッドは、サーバー側のカーソルでのみサポートされます。 シークときはサポートされていません、 [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)のプロパティの値、 **Recordset**オブジェクトが**adUseClient**です。  
  
 このメソッドを使用する場合にのみ、**レコード セット**でオブジェクトが開かれた、 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)の値**adCmdTableDirect**です。  
  
## <a name="filtering-the-results"></a>結果をフィルター選択  
 **検索**メソッドは、検索対象を 1 つのフィールドの内容を制限します。 **シーク**にインデックスであるし、その他の制限がありますもメソッドが必要です。 インデックスのベースではない複数のフィールドを検索する必要がありますかを使用して、結果を制限するには、プロバイダーがインデックスをサポートしていない場合、**フィルター**のプロパティ、 **Recordset**オブジェクト。  
  
 使用して、**フィルター**プロパティ内のレコードを選択して画面を**Recordset**オブジェクト。 フィルター選択された**Recordset**を記録することを意味を満たしていない、現在のカーソルになります、**フィルター**条件では使用できない、**レコード セット**まで、**フィルター**を削除します。 現在のカーソルに基づく値を返す他のプロパティは、影響を受けるよう**AbsolutePosition**、**と、AbsolutePage**、 **RecordCount**、および**PageCount**です。 これは、設定するため、**フィルター**プロパティを特定の値には、新しい値を満たす最初のレコードを現在のレコードを移動します。  
  
 **フィルター**プロパティは、バリアント型の引数を受け取ります。 この値は、3 つのメソッドを使用するための 1 つを表す、**フィルター**プロパティ: 条件の文字列、 **FilterGroupEnum**定数、またはブックマークの配列。 詳細については、このトピックの「フィルター条件の文字列で、フィルター処理を定数、およびブックマークによるフィルター処理を参照してください。  
  
> [!NOTE]
>  開くには通常より効率的です、データを選択することがわかっている場合に、 **Recordset**効果的ではなく、結果セットをフィルター処理する SQL ステートメントを使用して、**フィルター**プロパティです。  
  
 フィルターを削除する、 **Recordset**を使用して、 **adFilterNone**定数。 設定、**フィルター**プロパティを長さ 0 の文字列 ("") を使用する場合と同じ効果、 **adFilterNone**定数。  
  
### <a name="filtering-with-a-criteria-string"></a>条件の文字列によるフィルター処理  
 条件の文字列形式の句でから成る*FieldName 演算子の値*(たとえば、 `"LastName = 'Smith'"`)。 個々 の句を連結して複合句を作成することができます**AND** (たとえば、 `"LastName = 'Smith' AND FirstName = 'John'"`) および**または**(たとえば、 `"LastName = 'Smith' OR LastName = 'Jones'"`)。 条件の文字列の次のガイドラインを使用します。  
  
-   *FieldName*から有効なフィールド名にする必要があります、 **Recordset**です。 フィールド名にスペースが含まれている場合は、角かっこで囲んで、名前を囲む必要があります。  
  
-   *演算子*、次のいずれかを指定する必要があります: **\<**、 **>**、 **\< =**、 **>=**、 **<>**、 **=**、または**など**です。  
  
-   *値*これには、フィールドの値を比較し、値は、(たとえば、 `'Smith'`、 `#8/24/95#`、 `12.345`、または`$50.00`)。 文字列に単一引用符 (') を使用し、シャープ記号 (`#`) 日付。 数値の場合は、小数点、ドル記号、および科学的表記法を使用できます。 場合*演算子*は**など**、*値*ワイルドカード文字を使用できます。 アスタリスクのみ (\*) とパーセント記号 (%) のワイルドカード文字は使用すると、および文字列の最後の文字であることが必要です。 *値*null にすることはできません。  
  
    > [!NOTE]
    >  フィルターに単一引用符 (') を含める*値*、1 つの 2 つの単一引用符を使用します。 フィルターする場合など、 *O'Malley*、条件の文字列にする必要があります`"col1 = 'O''Malley'"`です。 先頭と末尾のフィルター値の両方に単一引用符を含めるを文字列で囲むのシャープ記号 (#)。 フィルターする場合など、 *'1'*、条件の文字列にする必要があります`"col1 = #'1'#"`です。  
  
 間の優先順位がない**AND**と**または**です。 句は、かっこで囲まれてグループ化することができます。 ただし、によって結合句をグループ化することはできません、**または**し、次のように、グループを別の句は AND に参加します。  
  
```  
(LastName = 'Smith' OR LastName = 'Jones') AND FirstName = 'John'  
```  
  
 代わりに、次のようにこのフィルターを構築するとします。  
  
```  
(LastName = 'Smith' AND FirstName = 'John') OR (LastName = 'Jones' AND FirstName = 'John')  
```  
  
 **と同様に**句、先頭とパターンの末尾にワイルドカードを使用することができます (たとえば、 `LastName Like '*mit*'`) またはパターンの末尾でのみ (たとえば、 `LastName Like 'Smit*'`)。  
  
### <a name="filtering-with-a-constant"></a>定数でフィルター処理  
 次の定数はフィルター処理に使用できる**レコード セット**です。  
  
|定数|Description|  
|--------------|-----------------|  
|**adFilterAffectedRecords**|最後に影響を受けるレコードのみを表示するためのフィルター**削除**、**再同期**、 **UpdateBatch**、または**CancelBatch**呼び出します。|  
|**adFilterConflictingRecords**|最後のバッチ更新が失敗したレコードを表示するためのフィルター。|  
|**adFilterFetchedRecords**|現在のキャッシュ内のレコードを表示するためのフィルター-つまり、データベースからレコードを取得するには、最後の呼び出しの結果。|  
|**adFilterNone**|現在のフィルターを削除し、表示するためのすべてのレコードを復元します。|  
|**adFilterPendingRecords**|変更されましたが、サーバーにまだ送信されていないレコードだけを表示するためのフィルター。 バッチ更新モードにのみ適用できます。|  
  
 フィルター定数しやすく、最後の中に影響を受けたレコードを専用などを表示することにより、バッチ更新モード中に個々 のレコード競合を解決するのには**UpdateBatch**メソッドの呼び出しのように、次の例です。  
  
 `Attribute VB_Name = "modExaminingData"`  
  
### <a name="filtering-with-bookmarks"></a>ブックマークを使用したフィルター処理  
 最後へのブックマークの variant の配列を渡すことができます、**フィルター**プロパティです。 結果として得られるカーソルは、プロパティに渡されたブックマーク レコードのみが含まれます。 次のコード例では、内のレコードからブックマークの配列を作成、 **Recordset** "B"である、 *ProductName*フィールドです。 これは、後、先の配列を渡します、**フィルター**フィルターを適用した結果に関する情報のプロパティを表示します**Recordset**です。  
  
```  
'BeginFilterBkmk  
Dim vBkmkArray() As Variant  
Dim i As Integer  
  
'Recordset created using "SELECT * FROM Products" as command.  
'So, we will check to see if ProductName has a capital B, and  
'if so, add to the array.  
i = 0  
Do While Not objRs.EOF  
    If InStr(1, objRs("ProductName"), "B") Then  
        ReDim Preserve vBkmkArray(i)  
        vBkmkArray(i) = objRs.Bookmark  
        i = i + 1  
        Debug.Print objRs("ProductName")  
    End If  
    objRs.MoveNext  
Loop  
  
'Filter using the array of bookmarks.  
objRs.Filter = vBkmkArray  
  
objRs.MoveFirst  
Do While Not objRs.EOF  
    Debug.Print objRs("ProductName")  
    objRs.MoveNext  
Loop  
'EndFilterBkmk  
```  
  
## <a name="creating-a-clone-of-a-recordset"></a>レコード セットの複製を作成します。  
 使用して、**クローン**を複数作成するメソッドが重複して**Recordset**オブジェクトを指定したレコード セットの 1 つ以上の現在のレコードを維持する場合に特にです。 使用して、**クローン**メソッドが作成して、新しいよりも効率的**Recordset**元と同じ定義を持つオブジェクト。  
  
 最初のレコードには、新しく作成された複製の現在のレコードが設定されていた。 クローンでは、現在のレコード ポインター **Recordset**元またはその逆は同期されません。 内で移動できましていない個別に各**Recordset**です。  
  
 いずれかに加えた**Recordset**オブジェクトがすべてのカーソルの種類に関係なく複製で表示されます。 ただしを実行する前後[Requery](../../../ado/reference/ado-api/requery-method.md)元の**Recordset**クローンは、元に同期できなくします。  
  
 元の終了**レコード セット**は、そのコピーを閉じませんも閉じるコピーの終了では、元または他のコピーのいずれか。  
  
 複製することができます、 **Recordset**ブックマークをサポートするかどうかのオブジェクトのみです。 ブックマークの値は同義です。いずれかからのブックマーク参照は、 **Recordset**オブジェクトの複製のいずれかで同じレコードを参照します。
