---
title: 開始または SharePoint サーバーに対して Stop a Power Pivot |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4b53cc7730f962d790ebdb9a0373bf98e9bf32bf
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="start-or-stop-a-power-pivot-for-sharepoint-server"></a>PowerPivot for SharePoint サーバーの開始または停止
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスと [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスは、同じローカル アプリケーション サーバー上で同時に動作し、SharePoint ファーム内での連携要求とデータ処理をサポートします。  
  
 このトピックには、次のセクションが含まれます。  
  
 [サービスの依存関係](#dependencies)  
  
 [サービスの開始または停止](#startstop)  
  
 [Power Pivot サーバーの停止の影響](#effects)  
  
##  <a name="dependencies"></a> サービスの依存関係  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスには、同じ物理サーバーに一緒にインストールされているローカル Analysis Services サーバー インスタンスに対する依存関係があります。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを停止する場合は、ローカル Analysis Services サーバー インスタンスも手動で停止する必要があります。 一方のサービスのみが実行されている場合は、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データの処理で要求割り当てエラーが発生します。  
  
 Analysis Services サーバーを単独で実行するのは、問題の診断またはトラブルシューティングを行う場合だけにしてください。 それ以外の場合は、同じサーバーでローカルに実行される [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスが必要です。  
  
##  <a name="startstop"></a> サービスの開始または停止  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスまたは Analysis Services サーバー インスタンスを開始または停止するには、必ずサーバーの全体管理を使用します。 サーバーの全体管理を使用すると、同じページからサービスの開始または停止をまとめて実行できます。 また、サーバーの全体管理では、実行する必要があると思われるサービスを再起動するために、 **[1 つ以上のサービスが開始または停止されています]** というタイマー ジョブが使用されます。 SharePoint 以外のツールを使用して [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスまたは Analysis Services を停止した場合は、タイマー ジョブの実行時にサービスが再起動されます。  
  
 サービスの開始および停止は、物理サービス インスタンスに適用される操作です。 ファーム内に追加の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーがある場合、ファーム内の他のサーバーは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する要求の受け入れを続行します。  
  
 ファーム全体のすべての物理サービスを同時に開始または停止することはできません。 各サーバーを選択してから、特定のサービスを開始または停止する必要があります。  
  
 特定の Web アプリケーションに対する [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを開始、一時停止、または停止することはできませんが、サービスを既定の接続リストから削除して使用できない状態にすることができます。 詳しくは、「 [サーバーの全体管理での SharePoint Web アプリケーションへの PowerPivot サービス アプリケーションの接続](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)」をご覧ください。  
  
1.  サーバーの全体管理で、 **[システム設定]** の **[サーバーのサービスの管理]** をクリックします。  
  
2.  ページの上部にある [サーバー] の下矢印をクリックし、 **[サーバーの変更]** をクリックします。  
  
3.  開始または停止する [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスまたは [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] インスタンスがある SharePoint サーバーを選択します。  
  
4.  サービスを選択し、アクションをクリックします。 サービスはペアで開始または停止することを忘れないでください。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスを開始または停止する場合は、同じコンピューターで実行される Analysis Services サーバー インスタンスも開始または停止する必要があります。  
  
##  <a name="effects"></a> Power Pivot サーバーの停止の影響  
 次の表に、SharePoint サーバーでの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスおよび Analysis Services サービスの停止の影響を示します。  
  
|影響を受ける対象|Description|  
|---------------|-----------------|  
|既存のクエリ|Analysis Services サーバーで処理されているクエリは直ちに停止します。 ユーザーは、データまたはデータ ソース接続が見つからないことを示すエラーを受け取ります。|  
|現在処理中の既存のデータ更新ジョブ|現在の Analysis Services サーバーで処理されているジョブは直ちに停止します。 データ更新が失敗し、データ更新の履歴にエラーが記録されます。<br /><br /> SharePoint サーバーの全体管理の [ジョブの状態の確認] ページを使用することにより、サービスを停止する前に現在のジョブの状態を表示できます。<br /><br /> 現在処理中のジョブを確認することはできますが、キュー自体を表示して、他のジョブが開始されようとしているかどうかを確認することはできません。|  
|キュー内の既存のデータ更新要求|スケジュール設定されたデータ更新要求は、スケジュールのサイクル全体にわたって処理キューに残ります (つまり、次の開始時間までキューに残ります)。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスがそのときまでに再起動されなかった場合、データ更新要求は削除され、エラーがログに記録されます。|  
|新しいクエリ要求またはデータ更新要求|ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーのみを停止した場合、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する新しい要求は処理されません。データを要求すると、データが見つからないことを示すエラーが発生します。<br /><br /> ファーム内に追加の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint サーバーがある場合、要求は使用可能なサーバーのうちの 1 つに送信されます。|  
|使用状況データ|使用状況データは、サービスの停止中は収集されません。|  
  
## <a name="see-also"></a>参照  
 [Power Pivot サービス アカウントの構成](../../analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts.md)  
  
  
