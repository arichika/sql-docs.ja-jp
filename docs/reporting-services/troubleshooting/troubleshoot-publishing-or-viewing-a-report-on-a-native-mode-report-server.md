---
title: "ネイティブ モードのレポート サーバーでのレポートのパブリッシュまたは表示のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "02/28/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
  - "reporting-services-sharepoint"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df7720a1-d178-45bb-8d6f-63e208cae7fe
caps.latest.revision: 6
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 6
---
# ネイティブ モードのレポート サーバーでのレポートのパブリッシュまたは表示のトラブルシューティング
  
  
  
ネイティブ モードで構成されているレポート サーバーにレポートをパブリッシュまたはアップロードすると、レポート サーバーでレポートを表示する場合に固有の問題が発生することがあります。 このトピックでは、このような問題のトラブルシューティングについて説明します。   
  
## レポートをパブリッシュするときに資格情報が要求される  
レポートをレポート サーバーに配置するには、サーバーのアドレスを指定する必要があります。 [Reporting Services ログイン] ダイアログ ボックスが表示され、資格情報の入力を求められることがあります。   
  
レポート サーバー名の指定が正しくない  
  
  
ネイティブ モードのレポート サーバーにレポートを配置する場合の一般的なエラーは、レポート サーバーの名前ではなくレポート フォルダーの名前を指定してしまうことです。   
  
レポート サーバーの URL が、レポート マネージャー仮想ディレクトリのアドレス (たとえば `http://localhost/reports`) ではなく、レポート サーバーのアドレス (たとえば `http://localhost/reportserver`) になっていることを確認してください。 既定のポート番号 80 とは異なるポート番号をレポート サーバーに指定した場合は、レポート サーバーのアドレス形式でポート番号 (たとえば `http://localhost:81/reportserver`) を指定する必要があります。   
  
 ## パブリッシュしたレポートでアイテムを切り替えても何も起こらない  
  ローカル プレビューでレポートを表示する場合は、レポートでアイテムを切り替えて、アイテムを表示または非表示にすることができます。 同じレポートをレポート サーバーにパブリッシュした後で表示すると、切り替えアイテムが機能しなくなります。   
  
\<レポート サーバー名> にアンダースコア (_) が含まれている  
  
エラーが発生することなくレポートが実行されても切り替えアイテムが機能しない (たとえば、展開アイコン (+) をクリックしても何も起こらない) 場合、レポート サーバーをホストするコンピューターの名前を確認してください。 コンピューター名にアンダースコアが含まれていると、切り替えアイテムが機能しません。 これは既知の問題です。 回避策はありません。   
  
切り替えアイテムを使用するレポートを実行するには、名前にアンダースコア文字を含まないコンピューターを使用する必要があります。  
  
## Run As とブラウザーを使用してレポートを実行すると画像とグラフが読み込まれない  
レポート マネージャーを別のセキュリティ コンテキストで実行すると、レポート内のレポート アイテムの一部が表示されないことがあります。   
  
### インターネット一時ファイル フォルダーに対する権限の不足  
  
状況によっては、レポート マネージャーを使用してグラフや画像を含むパブリッシュ済みレポートを表示する場合、レポートを表示できないことがあります。 たとえば、Microsoft Windows の **Run As** コマンドを使用して、別のセキュリティ コンテキストでレポートを表示する場合、グラフや画像がレポート サーバーによって一時インターネット ファイルとしてキャッシュされるフォルダーに対する権限を持っていないことがあります。   
  
キャッシュ ファイルが格納されているフォルダーにアクセスする権限があることを確認してください。   
    
## 参照  
[Reporting Services と Power View のブラウザー サポート](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)  
[エラーとイベント (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
[Reporting Services レポートのデータ取得に関する問題のトラブルシューティング](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Reporting Services のサブスクリプションと配信に関するトラブルシューティング](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]