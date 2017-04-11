---
title: "メール送信タスク | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.sendmailtask.f1"
helpviewer_keywords: 
  - "メール [Integration Services]"
  - "メール送信タスク"
  - "電子メール [Integration Services]"
  - "メッセージ [Integration Services]"
  - "sending messages"
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
caps.latest.revision: 51
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 51
---
# メール送信タスク
  メール送信タスクは、電子メール メッセージを送信します。 メール送信タスクを使用すると、パッケージ ワークフロー内のタスクが成功または失敗した場合にパッケージからメッセージを送信したり、実行時にパッケージで発生するイベントに応答してメッセージを送信したりできます。 たとえば、データベースのバックアップ タスクが成功または失敗したことを、メール送信タスクからデータベース管理者に通知できます。  
  
 メール送信タスクは、次の方法で構成できます。  
  
-   電子メール メッセージで使用するメッセージ テキストを指定します。  
  
-   電子メール メッセージの件名行を指定します。  
  
-   メッセージの優先度レベルを設定します。 タスクでは、標準、低、高の 3 種類の優先度レベルがサポートされています。  
  
-   [宛先]、[CC]、[BCC] 行に受信者を指定します。 タスクで複数の受信者を指定する場合、セミコロンで区切られます。  
  
    > [!NOTE]  
    >  [宛先]、[CC]、[BCC] 行の文字数は、インターネット標準に従って 256 文字に制限されています。  
  
-   添付ファイルを含めます。 タスクで複数の添付ファイルを指定する場合、パイプ (|) 文字で区切られます。  
  
    > [!NOTE]  
    >  パッケージの実行時に添付ファイルが存在しない場合、エラーが発生します。  
  
-   使用する SMTP 接続マネージャーを指定します。  
  
    > [!IMPORTANT]  
    >  SMTP 接続マネージャーでは、匿名認証と Windows 認証のみがサポートされています。 基本認証はサポートされていません。  
  
 メッセージ テキストには、指定する文字列、テキストを含むファイルへの接続、またはテキストを含む変数名を使用できます。 タスクは、ファイル接続マネージャーを使用してファイルに接続します。 詳しくは、「[フラット ファイル接続マネージャー](../../integration-services/connection-manager/flat-file-connection-manager.md)」をご覧ください。  
  
 タスクは、SMTP 接続マネージャーを使用してメール サーバーに接続します。 詳しくは、「[SMTP 接続マネージャー](../../integration-services/connection-manager/smtp-connection-manager.md)」をご覧ください。  
  
## メール送信タスクで使用できるカスタム ログ メッセージ  
 次の表は、メール送信タスクのカスタム ログ エントリの一覧です。 詳しくは、「[Integration Services &#40;SSIS&#41; のログ記録](../../integration-services/performance/integration-services-ssis-logging.md)」と「[ログ記録用のカスタム メッセージ](../../integration-services/performance/custom-messages-for-logging.md)」をご覧ください。  
  
|ログ エントリ|Description|  
|---------------|-----------------|  
|**SendMailTaskBegin**|タスクが電子メール メッセージの送信を開始したことを示します。|  
|**SendMailTaskEnd**|タスクが電子メール メッセージの送信を終了したことを示します。|  
|**SendMailTaskInfo**|タスクに関する説明情報を提供します。|  
  
## メール送信タスクの構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [[メール送信タスク エディター] &#40;[全般] ページ&#41;](../Topic/Send%20Mail%20Task%20Editor%20\(General%20Page\).md)  
  
-   [[メール送信タスク エディター] &#40;[メール] ページ&#41;](../Topic/Send%20Mail%20Task%20Editor%20\(Mail%20Page\).md)  
  
-   [[式] ページ](../Topic/Expressions%20Page.md)  
  
 プログラムによってこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## 関連タスク  
 これらのプロパティを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「[タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)」をご覧ください。  
  
## 関連コンテンツ  
  
-   shareourideas.com の技術記事「[配信通知付きで電子メールを送信する方法 (C#)](http://go.microsoft.com/fwlink/?LinkId=237625)」  
  
## 参照  
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  