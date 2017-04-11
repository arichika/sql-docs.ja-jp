---
title: "Issue 要素 (ssbdiagnose) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "issue 要素"
  - "XML 出力ファイルの形式 [ssbdiagnose], issue 要素"
  - "ssbdiagnose"
ms.assetid: 2246a886-686b-44ca-9771-b155cedad8be
caps.latest.revision: 17
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 17
---
# Issue 要素 (ssbdiagnose)
  **ssbdiagnose** ユーティリティによって検出された問題を報告します。 **ssbdiagnose** の XML 出力ファイルには、報告される問題につき 1 つの Issue 要素が含まれています。  
  
## 構文  
  
```  
  
<Issue  
    type="..."   
    code="..."   
    server="..."   
    database="..."   
    object="...">   
    ...   
</Issue>  
```  
  
## 要素の属性  
  
|属性|説明|  
|---------------|-----------------|  
|**型**|Issue 要素で報告する問題のカテゴリを次に示します。<br /><br /> **"Diagnosis"** では、[!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成の分析時に検出された構成の問題を報告します。<br /><br /> **"Problem"** では、**ssbdiagnose** で分析を完了できない場合の原因となった問題を報告します。 問題を修正して、**ssbdiagnose** を再実行します。<br /><br /> **"Event"** では、**-RUNTIME** チェックの実行時に検出された [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] イベントを報告します。 イベントが報告されるのは、**-SHOWEVENTS** が指定されている場合のみです。|  
|**コード**|メッセージのエラー番号を示します。|  
|**サーバー (server)**|問題が検出された[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスを示します。 既定のインスタンスに問題があった場合、サーバー属性には、コンピューター名のみが含まれます。 既定のインスタンスに問題があった場合、サーバー属性は "ComputerName\ InstanceName" という形式になります。|  
|**データベース (database)**|問題が検出されたデータベースの名前を示します。|  
|**オブジェクト (object)**|問題が検出されたオブジェクトの名前を示します。 問題がインスタンス レベルまたはデータベース レベルの問題である場合、オブジェクト属性はインスタンス名またはデータベース名を繰り返します。|  
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|**string**、長さは無制限です。|  
|**値**|エラー メッセージのテキストを返します。|  
|**個数**|報告されたエラーにつき 1 個。|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DiagnosticInformation 要素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)|  
|**子要素**|なし|  
  
## 例  
 この要素は、マスター キーを持たないデータベースの 1102 エラーを報告します。このエラーは、[!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成の分析時に検出されました。  
  
```  
<Issue type="Diagnosis" code="1102" server="TestComputer" database="TargetDB" object="TargetDB">The master key was not found</diagnostic>  
```  
  
## 参照  
 [ssbdiagnose ユーティリティ &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  