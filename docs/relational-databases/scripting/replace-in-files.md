---
title: "[フォルダーを指定して置換] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findreplace.replaceinfiles"
  - "vs.replaceinfiles"
helpviewer_keywords: 
  - "[フォルダーを指定して置換] ダイアログ ボックス"
ms.assetid: 51191c0a-e022-41d6-8473-5cb3c6596862
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [フォルダーを指定して置換]
  **[検索と置換]** ウィンドウの [フォルダーを指定して置換] タブを使用すると、指定したファイル セットのコード内で文字列や正規表現を検索したり、検出された項目の一部またはすべてを置き換えたりできます。 検出された項目および実行するアクションは、**[結果オプション]** で選択された検索結果ウィンドウに表示されます。  
  
 ツール バー ボタンやショートカット キーを使用して **[検索と置換]** ダイアログ ボックスを開くこともできます。  
  
## [検索する文字列]  
 **[フォルダーを指定して置換]** タブの次のコントロールを使用して、検索する文字列または正規表現を指定します。  
  
 **[検索する文字列]**  
 検索するテキストを入力します。 ダイアログ ボックスを開く前にカーソルで選択されていたテキスト、近接するテキスト、または以前に検索したテキストが、検索テキストの候補として示されます。 ドロップダウン リストを使用して、直前の 20 回の検索文字列の中から 1 つを再選択することができます。  
  
 **ワイルドカード付き文字列**  
 アスタリスク (`*`) や疑問符 (`?`) などのワイルドカードを検索文字列内で使用する場合は、**[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、**[ワイルドカード]** をクリックします。  
  
 **正規表現**  
 検索エンジンが検索文字列を正規表現として解釈するようにするには、**[検索オプション]** の下にある **[条件]** チェック ボックスをオンにして、**[正規表現]** をクリックします。  
  
 **[式ビルダー]**  
 **[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、**[検索する文字列]** ボックスの横にある三角形のボタンを使用できます。 このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。 この一覧から項目を選択すると、**[検索する文字列]** ボックスに指定した文字列にその項目が追加されます。  
  
## [置換後の文字列]  
 次のコントロールを使用して、検索で一致した文字列や正規表現に置き換えて挿入する文字列を指定します。  
  
 **[置換後の文字列]**  
 **[検索する文字列]** で指定した文字列のインスタンスを別の文字列で置き換えるには、このフィールドに置換後の文字列を入力します。 **[検索する文字列]** で指定した文字列のインスタンスを削除するには、このボックスを空白にしておきます。 ドロップダウン リストを選択すると、直前の 20 回の入力項目が表示されます。 **[置換後の文字列]** ボックスで指定する文字列で正規表現を使用するには、**[条件]** チェック ボックスをオンにしてから **[正規表現]** オプションをクリックします。  
  
 **[式ビルダー]**  
 **[検索オプション]** で **[条件]** チェック ボックスがオンになっている場合、**[置換後の文字列]** ボックスの横にある三角形のボタンを使用できます。 このボタンをクリックすると、選択した **[条件]** オプションに応じて、ワイルドカードまたは正規表現の一覧が表示されます。 この一覧から項目を選択すると、**[置換後の文字列]** ボックスに指定されている文字列にその項目が追加されます。  
  
 **[置換]**  
 このボタンをクリックすると、**[検索する文字列]** に指定された文字列の現在のインスタンスが **[置換後の文字列]** ボックスで指定した文字列で置き換えられ、**[検索対象]** で指定された範囲内で次のインスタンスが検索されます。  
  
 **[すべて置換]**  
 このボタンをクリックすると、**[検索対象]** に指定されている範囲内のすべてのファイルにおいて、**[検索する文字列]** に指定された文字列のすべてのインスタンスが、**[置換後の文字列]** ボックスに指定された文字列で置き換えられます。  
  
> [!CAUTION]  
>  変更する対象のファイルだけが **[検索対象]** に含まれていることを確認してください。  
  
 **[変更したファイルを閉じない]** オプションを含む通知が表示されます。 **[元に戻す]** オプションを使用できるようにするには、このオプションを選択する必要があります。 **[元に戻す]** は、変更後も開いていて編集可能なファイルでのみ使用できます。  
  
 **[ファイルのスキップ]**  
 **[検索対象]** に指定した値によって複数のファイルが検索対象になる場合、このボタンを使用できます。 現在のファイルを検索したり変更したりしない場合に、このボタンをクリックします。 検索は、**[検索対象]** の一覧の次のファイルから続行されます。  
  
## [検索対象]  
 **[検索対象]** ドロップダウン リストから選択したオプションで、**[フォルダーを指定して置換]** の検索を現在アクティブなファイル内でだけ実行するか、特定のフォルダー内のすべてのファイルに対して実行するかが決まります。 一覧から検索範囲を選択するか、フォルダー パスを入力します。または、**[参照]** ボタンをクリックして **[検索フォルダーの選択]** ダイアログ ボックスを表示し、検索対象のフォルダーを選択します。  
  
> [!NOTE]  
>  選択した **[検索対象]** オプションの設定により、ソース コード管理からチェックアウトしたファイルに対して検索が行われる場合、ローカル コンピューターにダウンロードされているファイル バージョンだけが検索されます。  
  
 **[探す場所]**  
 あらかじめ定義されている検索範囲をこの一覧から選択するか、**[検索フォルダーの選択]** ダイアログ ボックスを使用して独自のディレクトリのセットを入力します。  
  
 **[現在のドキュメント]**  
 このオプションは、ドキュメントがエディターで開かれているときに使用できます。 アクティブ ドキュメントだけを対象に、**[検索する文字列]** に指定した文字列の検索が実行されます。  
  
 **[すべての開かれているドキュメント]**  
 編集のために現在開かれているすべてのファイルを検索します。  
  
 **[現在のプロジェクト]**  
 アクティブ プロジェクト内のすべてのファイルを検索します。  
  
 **[ソリューション全体]**  
 アクティブ ソリューション内のすべてのファイルを検索します。  
  
 **[サブフォルダーを含める]**  
 **[検索対象]** に指定したフォルダーのサブフォルダーも検索対象とすることを指定します。 [検索フォルダーの選択] を使用する必要があります。  
  
 **[...]**  
 このボタンをクリックすると、**[検索対象]** ボックスに入力するディレクトリの名前付きセットを作成、編集、保存、および選択するための **[検索フォルダーの選択]** ダイアログ ボックスが表示されます。  
  
## [検索オプション]  
 **[検索オプション]** セクションは、展開したり折りたたんだりできます。 次のオプションをオンまたはオフに設定できます。  
  
 **[大文字と小文字を区別する]**  
 このチェック ボックスをオンにすると、検索結果ウィンドウには、**[検索する文字列]** で指定した文字列に大文字と小文字の違いを含めて完全に一致するインスタンスのみが検索結果ウィンドウに表示されます。 たとえば、**[大文字と小文字を区別する]** チェック ボックスをオンにした状態で「**MyObject**」を検索すると、"myobject" や "MYOBJECT" ではなく "MyObject" のみが返されます。  
  
 **[単語単位]**  
 このチェック ボックスをオンにすると、**[検索する文字列]** で指定した文字列に単語単位で一致するインスタンスのみが検索結果ウィンドウに表示されます。 たとえば、「**MyObject**」を検索すると、"CMyObject" や "MyObjectC" ではなく "MyObject" のみが返されます。  
  
 **新しく使用する機能**  
 **[検索する文字列]** ボックスまたは **[置換後の文字列]** ボックスに入力された特殊文字を解釈する方法を指定します。 オプションは **[ワイルドカード]** と **[正規表現]** です。  
  
 **[正規表現]**  
 検索するテキストのパターンを定義する、特殊な表記です。 一覧については、「[正規表現によるテキストの検索](../../relational-databases/scripting/search-text-with-regular-expressions.md)」を参照してください。  
  
 **ワイルドカード**  
 アスタリスク (`*`) や疑問符 (`?`) などの特殊文字は、1 つまたは複数の文字を表します。 一覧については、「[ワイルドカードを使用したテキスト検索](../../relational-databases/scripting/search-text-with-wildcards.md)」を参照してください。  
  
 **[次のファイルの種類を参照]**  
 この一覧は、**[検索対象]** で指定したディレクトリ内で検索するファイルの種類を示します。 このボックスが空の場合、**[検索対象]** に指定されているディレクトリ内のすべてのファイルが検索の対象となります。  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 特定の種類のファイルを検索するには、ファイル名としてアスタリスク ワイルドカード (`*`) を入力し、ピリオド (`.`) およびファイル拡張子を順に入力します。 複数の種類のファイルを検索するには、複数の検索文字列をセミコロン (`;`) で区切って入力します。  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 一覧から項目を選択することによって、特定の種類のファイルを検索対象とする構成済みの検索文字列を入力できます。  
  
## [結果オプション]  
 **[結果オプション]** セクションは、展開したり折りたたんだりできます。 次のオプションをオンまたはオフに設定できます。  
  
 **[検索結果 1] ウィンドウ**  
 このチェック ボックスがオンの場合、現在の検索の結果は [検索結果 1] ウィンドウの内容に追加されます。 このウィンドウは、検索結果を表示するために自動的に開きます。 このウィンドウを手動で開くには、**[表示]** メニューの **[その他のウィンドウ]** をクリックし、**[検索結果 1]** をクリックします。  
  
 **[検索結果 2 ウィンドウ]**  
 このチェック ボックスがオンの場合、現在の検索の結果は [検索結果 2] ウィンドウの内容に追加されます。 このウィンドウは、検索結果を表示するために自動的に開きます。 このウィンドウを手動で開くには、**[表示]** メニューの **[その他のウィンドウ]** をクリックし、**[検索結果 2]** をクリックします。  
  
 **[ファイル名のみ表示する]**  
 一致項目ごとに 1 つのエントリではなく、一致項目を含むファイルごとに 1 つのエントリを、[検索結果 1] ウィンドウまたは [検索結果 2] ウィンドウに表示します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では、このオプションは使用できません。  
  
 **[置換後に、変更したファイルを閉じない]**  
 オンにすると、置換が実行されたすべてのファイルは開かれたままになります。これにより、変更内容を元に戻すか、保存するかを選択できます。 メモリの制約により、置換が実行された後に開いたままにできるファイル数が制限されることがあります。  
  
> [!CAUTION]  
>  **[元に戻す]** は、編集のために開かれているファイルにだけ使用できます。 このオプションをオフにすると、編集のために開かれていなかったファイルは閉じたままとなるので、それらのファイルに対して **[元に戻す]** オプションは利用できません。  
  
## [検索と置換] のビュー  
 [検索と置換] ウィンドウの上部にあるタブに、**ビュー**を切り替えるためのメニューがあります。 このメニューを使用して、アクティブなペインに表示する一連のフィールドを選択できます。 [検索と置換] ウィンドウを使いやすい場所にドッキングしておくと、タブを変えてビューを切り替えながら任意の検索操作や置換操作を実行できます。  
  
 **[[クイック検索] に切り替える]**  
 このツール バー タブを使用すると、ダイアログ ボックスが **[クイック検索]** ダイアログ ボックスに変わります。  
  
 **[[フォルダーを指定して検索] に切り替える]**  
 このツール バー タブを使用すると、ダイアログ ボックスが **[フォルダーを指定して検索]** ダイアログ ボックスに変わります。  
  
 **[[シンボルの検索] に切り替える]**  
 このツール バー タブを使用すると、ダイアログ ボックスが **[シンボルの検索]** ダイアログ ボックスに変わります。  
  
## 参照  
 [SQL Server Management Studio のキーボード ショートカット](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)  
  
  