---
title: ADO MD から ADOMD.NET への移行 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e6d0e3acb77657bcac754b9e6b9392dc2971ce9c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="migrating-from-ado-md-to-adomdnet"></a>ADO MD から ADOMD.NET への移行
  ADOMD.NET ライブラリは、ActiveX Data Objects (ADO) ライブラリを機能拡張した ActiveX Data Objects Multidimensional (ADO MD) ライブラリに似ています。このライブラリは、COM (Component Object Model) ベースのクライアント アプリケーションで多次元データへアクセスするときに使用されます。 ADO MD を使用すると、C++ や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などのアンマネージ言語から多次元データへ簡単にアクセスできます。 ADOMD.NET では、[!INCLUDE[msCoName](../../includes/msconame-md.md)] C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic .NET などのマネージ言語から、分析データ (多次元データとデータ マイニングの両方) へ簡単にアクセスできます。 また、ADOMD.NET は、高度な機能を備えたメタデータ オブジェクト モデルでもあります。  
  
 既存のクライアント アプリケーションを ADO MD から ADOMD.NET へ移行するのは容易ですが、移行時には、次の重要な相違点に注意してください。  
  
 **クライアント アプリケーションへの接続とデータのアクセスを提供するには**  
 |ADO MD (ADO MD)|ADOMD.NET|  
|------------|---------------|  
|Adodb.dll と Adomd.dll を両方とも参照する必要があります。|Microsoft.AnalysisServices.AdomdClient.dll への参照のみが必要です。|  
  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> クラスは、メタデータへのアクセスだけでなく、接続のサポートも提供します。  
  
 **多次元オブジェクトのメタデータを取得するには**  
 |ADO MD (ADO MD)|ADOMD.NET|  
|------------|---------------|  
|カタログのクラスを使用します。|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.Cubes%2A> の <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> プロパティを使用します。|  
  
 **クエリを実行し、セルセット オブジェクトの取得**  
 |ADO MD (ADO MD)|ADOMD.NET|  
|------------|---------------|  
|セルセット クラスを使用します。|<xref:Microsoft.AnalysisServices.AdomdClient.AdomdCommand> クラスを使用します。|  
  
 **セルセットの表示に使用されるメタデータにアクセスするには**  
 |ADO MD (ADO MD)|ADOMD.NET|  
|------------|---------------|  
|位置クラスを使用します。|<xref:Microsoft.AnalysisServices.AdomdClient.Set> オブジェクトおよび <xref:Microsoft.AnalysisServices.AdomdClient.Tuple> オブジェクトを使用します。|  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.AdomdClient.Position> クラスは、旧バージョンとの互換性を維持するためにサポートされています。  
  
 **マイニング モデルのメタデータを取得するには**  
 ADO MD でクラスがない使用できます。 ADOMD.NET では、データ マイニング コレクションの 1 つを使用します。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> には、データ ソース内のマイニング モデルの一覧が含まれています。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> は、使用可能なマイニング アルゴリズムに関する情報を提供します。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> は、サーバーのマイニング構造に関する情報を示します。  
  
 これらの違いをわかりやすく示すため、次の移行例では、既存の ADO MD アプリケーションと同等の ADOMD.NET アプリケーションを比較します。  
  
## <a name="looking-at-a-migration-example"></a>移行例  
 この例に示す既存の ADO MD と同等の ADOMD.NET コードは、どちらも同じ一連の操作 (接続の作成、多次元式 (MDX) ステートメントの実行、メタデータとデータの取得) を実行します。 ただし、これらの 2 つのコードは、これらのタスクの実行に異なるオブジェクトを使用します。  
  
### <a name="existing-ado-md-code"></a>既存の ADO MD コード  
 ADO MD 2.8 ドキュメントから抽出された、次のコード例で記述された[!INCLUDE[msCoName](../../includes/msconame-md.md)]に接続し、クエリを実行する方法を示すには、Visual Basic® 6.0 および ADO MD を使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ソース。 この ADO MD の例では、次のオブジェクトを使用します。  
  
-   接続を作成、**カタログ**オブジェクト。  
  
-   多次元式 (MDX) ステートメントを使用して、実行、**セルセット**オブジェクト。  
  
-   メタデータとデータを取得、**位置**から取得したオブジェクト、**セルセット**オブジェクト。  
  
```  
Private Sub cmdCellSettoDebugWindow_Click()  
Dim cat As New ADOMD.Catalog  
Dim cst As New ADOMD.Cellset  
Dim i As Integer  
Dim j As Integer  
Dim k As Integer  
Dim strServer As String  
Dim strSource As String  
Dim strColumnHeader As String  
Dim strRowText As String  
  
On Error GoTo Error_cmdCellSettoDebugWindow_Click  
Screen.MousePointer = vbHourglass  
'*-----------------------------------------------------------------------  
'* Set server to local host.  
'*-----------------------------------------------------------------------  
    strServer = "LOCALHOST"  
  
'*-----------------------------------------------------------------------  
'* Set MDX query string source.  
'*-----------------------------------------------------------------------  
    strSource = strSource & "SELECT "  
    strSource = strSource & "{[Measures].members} ON COLUMNS,"  
    strSource = strSource & _  
        "NON EMPTY [Store].[Store City].members ON ROWS"  
    strSource = strSource & " FROM Sales"  
  
'*-----------------------------------------------------------------------  
'* Set active connection.  
'*-----------------------------------------------------------------------  
        cat.ActiveConnection = "Data Source=" & strServer & _  
            ";Provider=msolap;"  
  
'*-----------------------------------------------------------------------  
'* Set cellset source to MDX query string.  
'*-----------------------------------------------------------------------  
        cst.Source = strSource  
  
'*-----------------------------------------------------------------------  
'* Set cellset active connection to current connection  
'*-----------------------------------------------------------------------  
    Set cst.ActiveConnection = cat.ActiveConnection  
  
'*-----------------------------------------------------------------------  
'* Open cellset.  
'*-----------------------------------------------------------------------  
    cst.Open  
  
'*-----------------------------------------------------------------------  
'* Allow space for row header text.  
'*-----------------------------------------------------------------------  
strColumnHeader = vbTab & vbTab & vbTab & vbTab & vbTab & vbTab  
  
'*-----------------------------------------------------------------------  
'* Loop through column headers.  
'*-----------------------------------------------------------------------  
       For i = 0 To cst.Axes(0).Positions.Count - 1  
            strColumnHeader = strColumnHeader & _  
                cst.Axes(0).Positions(i).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
       Next  
       Debug.Print vbTab & strColumnHeader & vbCrLf  
  
'*-----------------------------------------------------------------------  
'* Loop through row headers and provide data for each row.  
'*-----------------------------------------------------------------------  
        strRowText = ""  
        For j = 0 To cst.Axes(1).Positions.Count - 1  
            strRowText = strRowText & _  
                cst.Axes(1).Positions(j).Members(0).Caption & vbTab & _  
                    vbTab & vbTab & vbTab  
            For k = 0 To cst.Axes(0).Positions.Count - 1  
                strRowText = strRowText & cst(k, j).FormattedValue & _  
                    vbTab & vbTab & vbTab & vbTab  
            Next  
            Debug.Print strRowText & vbCrLf  
            strRowText = ""  
        Next  
  
    Screen.MousePointer = vbDefault  
Exit Sub  
  
Error_cmdCellSettoDebugWindow_Click:  
   Beep  
   Screen.MousePointer = vbDefault  
   MsgBox "The following error has occurred:" & vbCrLf & _  
      Err.Description, vbCritical, " Error!"  
   Exit Sub  
End Sub  
```  
  
### <a name="equivalent-adomdnet-code"></a>同等の ADOMD.NET コード  
 Visual Basic.NET で記述され、ADOMD.NET を使用している次の例は、上記の Visual Basic 6.0 の例と同じ操作の実行方法を示しています。 この例と前述の ADO MD の例との大きな違いは、操作のアクションの実行に使用するオブジェクトです。 ADOMD.NET の例では、次のオブジェクトを使用します。  
  
-   接続を作成、 **AdomdConnection**オブジェクト。  
  
-   MDX ステートメントを使用して、実行、 **AdomdCommand**オブジェクト。  
  
-   メタデータとデータを取得、**設定**から取得したオブジェクト、**セルセット**オブジェクト。  
  
```  
Private Sub DisplayCellSetInOutputWindow()  
    Dim conn As AdomdConnection  
    Dim cmd As AdomdCommand  
    Dim cst As CellSet  
    Dim i As Integer  
    Dim j As Integer  
    Dim k As Integer  
    Dim strServer As String = "LOCALHOST"  
    Dim strSource As String = "SELECT [Measures].members ON COLUMNS, " & _  
        "NON EMPTY [Store].[Store City].members ON ROWS FROM SALES"  
    Dim strOutput As New System.IO.StringWriter  
  
    '*-----------------------------------------------------------------------  
    '* Open connection.  
    '*-----------------------------------------------------------------------  
    Try  
        ' Create a new AdomdConnection object, providing the connection  
        ' string.  
        conn = New AdomdConnection("Data Source=" & strServer & _  
        ";Provider=msolap;")  
        ' Open the connection.  
        conn.Open()  
    Catch ex As Exception  
        Throw New ApplicationException( _  
            "An error occurred while connecting.")  
    End Try  
  
    Try  
    '*-----------------------------------------------------------------------  
    '* Open cellset.  
    '*-----------------------------------------------------------------------  
        ' Create a new AdomdCommand object, providing the MDX query string.  
        cmd = New AdomdCommand(strSource, conn)  
        ' Run the command and return a CellSet object.  
        cst = cmd.ExecuteCellSet()  
  
    '*-----------------------------------------------------------------------  
    '* Concatenate output.  
    '*-----------------------------------------------------------------------  
  
    ' Include spacing to account for row headers.  
    strOutput.Write(vbTab, 6)  
  
    ' Iterate through the first axis of the CellSet object and  
    ' retrieve column headers.  
    For i = 0 To cst.Axes(0).Set.Tuples.Count - 1  
        strOutput.Write(cst.Axes(0).Set.Tuples(i).Members(0).Caption)  
        strOutput.Write(vbTab, 4)  
    Next  
    strOutput.WriteLine()  
  
    ' Iterate through the second axis of the CellSet object and  
    ' retrieve row headers and cell data.  
    For j = 0 To cst.Axes(1).Set.Tuples.Count - 1  
        ' Append the row header.  
        strOutput.Write(cst.Axes(1).Set.Tuples(j).Members(0).Caption)  
        strOutput.Write(vbTab, 4)  
  
        ' Append the cell data for that row.  
        For k = 0 To cst.Axes(0).Set.Tuples.Count - 1  
            strOutput.Write(cst.Cells(k, j).FormattedValue)  
            strOutput.Write(vbTab, 4)  
        Next  
        strOutput.WriteLine()  
    Next  
  
    ' Display the output.  
    Debug.WriteLine(strOutput.ToString)  
  
    '*-----------------------------------------------------------------------  
    '* Release resources.  
    '*-----------------------------------------------------------------------  
        conn.Close()  
    Catch ex As Exception  
        ' Ignore or handle errors.  
    Finally  
        cst = Nothing  
        cmd = Nothing  
        conn = Nothing  
    End Try  
End Sub  
```  
  
  
