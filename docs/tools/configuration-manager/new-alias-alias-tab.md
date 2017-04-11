---
title: "[別名 - 新規] ダイアログ ボックス ([別名] タブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 785eb6fb-f67e-449d-b1c8-c38dfbb95ef6
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# [別名 - 新規] ダイアログ ボックス ([別名] タブ)
  別名は、接続のために使用できる代替名です。 別名は、接続文字列の必須要素をカプセル化したものであり、ユーザーが選択した名前でそれらの要素を公開できます。 **[別名 - 新規]** ダイアログ ボックスの **[別名]** ページでは、別名の接続文字列の各要素を指定できます。 既存の別名の接続文字列を変更する場合は、「[[&#60;Alias&#62; のプロパティ] ダイアログ ボックス ([別名] タブ)](../Topic/%3CAlias%3E%20Properties%20\(Alias%20Tab\).md)」を参照してください。  
  
 **[プロパティ]** グリッドのすべての値を設定する必要はありません。 有効な組み合わせは、選択したプロトコルによって異なります。 有効な組み合わせの例については、最後に示してあるトピックを参照してください。  
  
 **[別名]**  
 この接続を参照するために使用する名前 (別名) です。  
  
 **[パイプ名]** / **[ポート番号]**  
 接続文字列の追加要素です。 このボックスの名前は、選択したプロトコルによって異なります。  
  
 **[プロトコル]**  
 接続に使用するプロトコルです。  
  
 **[サーバー]**  
 接続先の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前です。  
  
## 別名を使用する状況  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は既定で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに接続するときには**共有メモリ** プロトコルを使用し、別のコンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続するときには **TCP/IP** または**名前付きパイプ**を使用します。 TCP/IP または名前付きパイプを使用するときにカスタム接続文字列を指定する場合や、接続のためにサーバー名以外の名前を使用する場合には、別名を作成してください。  
  
### 使用例  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定の TCP/IP ポート 1433 で受信を待機しない場合に、別のポート番号を設定した接続文字列を指定します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が既定の名前付きパイプで受信を待機しない場合に、別のパイプ名を設定した接続文字列を指定します。  
  
-   `ACCT`という名前のサーバー上のデータベースに接続するアプリケーションがありますが、そのデータベースは、 `ACCT` という名前のサーバー上の `CENTRAL`という名前のインスタンスとして統合されています。 そのアプリケーションは、簡単に変更できません。 この場合は、 `ACCT`という別名を作成し、接続文字列で `CENTRAL\ACCT`を参照します。  
  
## 有効な接続文字列の作成  
 別名のプロパティの有効な組み合わせに関する説明と例については、以下のトピックを参照してください。  
  
-   [共有メモリ プロトコルを使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
-   [TCP/IP を使用した有効な接続文字列の作成](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)  
  
-   [名前付きパイプを使用した有効な接続文字列の作成](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  