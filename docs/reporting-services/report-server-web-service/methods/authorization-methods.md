---
title: Authorization メソッド | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: report-server-web-service
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- security [Reporting Services], reports
- authorization [Reporting Services]
- reports [Reporting Services], security
- tasks [Reporting Services]
- roles [Reporting Services], methods
ms.assetid: 45e9cf2c-facf-4801-9482-c855403f42a8
caps.latest.revision: 42
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 479c1814a6ce52f3deec42d5ce84f40bc00278a1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="authorization-methods"></a>Authorization メソッド
  以下のメソッドを使用して、レポート サーバーでタスク、ロール、およびポリシーを管理できます。  
  
|方法|操作|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.CreateRole%2A>|新しいロールをレポート サーバー データベースに追加します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.DeleteRole%2A>|レポート サーバー データベースからロールを削除します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.GetPermissions%2A>|レポート サーバー データベースまたは SharePoint ライブラリの特定のアイテムに関連付けられたユーザー アクセス許可を返します。|  
|<xref:ReportService2010.ReportingService2010.GetPolicies%2A>|レポート サーバー データベースまたは SharePoint ライブラリの特定のアイテムに関連付けられたポリシーを返します。|  
|<xref:ReportService2010.ReportingService2010.GetRoleProperties%2A>|ロールのメタデータ プロパティと関連付けられたタスクのコレクションを返します。|  
|<xref:ReportService2010.ReportingService2010.GetSystemPermissions%2A>|ユーザーのシステム権限を返します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.GetSystemPolicies%2A>|システム ポリシーに関連付けられるグループとロールを含むシステム ポリシーを返します。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.InheritParentSecurity%2A>|レポート サーバー データベースの特定のアイテムに関連付けられたポリシーを削除し、アイテムのセキュリティ ポリシーをアイテムの親のセキュリティ ポリシーに設定します。|  
|<xref:ReportService2010.ReportingService2010.IsSSLRequired%2A>|<xref:ReportService2010> エンドポイントを使用するために SSL (Secure Sockets Layer) プロトコルが必要かどうかを示すブール値を返します。|  
|<xref:ReportService2010.ReportingService2010.ListRoles%2A>|レポート サーバーによって管理されるロールの名前と説明を返します。|  
|<xref:ReportExecution2005.ReportExecutionService.ListSecureMethods%2A>|呼び出し時にセキュリティで保護された接続が必要な、<xref:ReportExecution2005> エンドポイントの Simple Object Access Protocol (SOAP) メソッドの一覧を返します。 レポート サーバーの **SecureConnectionLevel** 設定を使用して、どのメソッドを返すかを判断します。|  
|<xref:ReportService2010.ReportingService2010.ListTasks%2A>|レポート サーバーが管理するタスクを返します。|  
|<xref:ReportService2010.ReportingService2010.SetPolicies%2A>|指定したアイテムに関連付けられたポリシーを設定します。|  
|<xref:ReportService2010.ReportingService2010.SetRoleProperties%2A>|ロールのメタデータ プロパティを設定し、一連のタスクをロールに関連付けます。 このメソッドはネイティブ モードにのみ適用されます。|  
|<xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A>|グループと、それらに関連付けられたロールを定義するシステム ポリシーを設定します。 このメソッドはネイティブ モードにのみ適用されます。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [レポート サーバー Web サービス メソッド](../../../reporting-services/report-server-web-service/methods/report-server-web-service-methods.md)   
 [テクニカル リファレンス (SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
