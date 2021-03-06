---
title: アドレス帳のサンプル アプリケーションを実行している |Microsoft ドキュメント
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
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: 3a2644e9-d634-4ae6-a5b7-13fb7b317ec7
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ae87cba1c56924f841e00ba8fcdd1e66eff5d01
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="running-the-address-book-sample-application"></a>アドレス帳のサンプル アプリケーションの実行
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
 アドレス帳アプリケーションを実行するには、この手順を実行します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
### <a name="to-run-this-application"></a>このアプリケーションを実行するには  
  
1.  Microsoft SQL Server が実行されていることを確認します。 をクリックして**開始**、 をポイント**プログラム**、 をポイント**Microsoft SQL Server 7.0**、順にクリック**Service Manager**です。 白い円に緑色の矢印がある場合は SQL Server を実行します。 ない場合は (が表示されますが赤い四角形の白い丸)、をクリックして**開始/再開**です。  
  
2.  Microsoft Internet Explorer 4.0 以降では、次のアドレスを入力します。  
  
     **http://** *webserver* **/RDS/AddressBook/AddrBook.asp**  
  
     ここで*webserver* RDS サーバー コンポーネントがインストールされている Web サーバーの名前を指定します。  
  
3.  アドレス帳のサンプル アプリケーションでさまざまなシナリオは、「プログラム マネージャー」というタイトルのすべてのユーザーを一覧表示するか、自分の電子メール名に基づく人を検索または編集の既存のレコードなどを試してことができます。 をクリックして**検索**に利用可能なすべての名前とデータ グリッドに表示します。  
  
## <a name="see-also"></a>参照  
 [アドレス帳のデータ バインディング オブジェクト](../../../ado/guide/remote-data-service/address-book-data-binding-object.md)




