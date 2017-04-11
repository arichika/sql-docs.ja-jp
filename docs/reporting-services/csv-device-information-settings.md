---
title: "CSV デバイス情報設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CSV [Reporting Services]"
  - "デバイス情報の設定 [Reporting Services], CSV 表示"
ms.assetid: f96f83a6-50bc-48ce-9fcd-fd9e1952d40a
caps.latest.revision: 43
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 43
---
# CSV デバイス情報設定
  CSV 表示拡張機能のデバイス情報設定では、区切り記号と修飾子を変更し、改行処理を指定できます。 ファイルの拡張子、エンコード、および出力にヘッダー行を含めることも指定できます。 区切り記号は通常特殊文字であるため、設定が XML として記述されている場合、CDATA セクションでエンコードしてください。  
  
 次の表は、テキスト形式で表示するためのデバイス情報設定を示しています。  
  
|設定|値|  
|-------------|-----------|  
|**[エンコード]**|.NET Framework でサポートされている文字エンコードの Internet Assigned Numbers Authority (IANA) 名。 既定値は **UTF-8** です。 他の値には、ASCII、UTF-7、UTF-16 などがあります。|  
|**ExcelMode**|Excel 用のターゲット出力であることを指定します。 既定値は **true**です。|  
|**FieldDelimiter**|結果に付ける区切り記号。 既定値はコンマ (,) です。 このデバイス情報の値は URL で渡すとき、URL エンコードしてください。 たとえば、区切り記号としてのタブ文字は "%09" にします。<br /><br /> 既定のフィールド区切り記号を任意の文字 (タブなど) に変更するには、構成ファイル内のデバイス情報設定を変更します。 たとえば、タブを使用するには、FieldDelimiter の設定を \<FieldDelimiter xml:space="preserve">[TAB]</FieldDelimiter> に更新します。\><br /><br /> この例では、[TAB] は実際のタブ文字です。つまり、構成ファイルには空白が表示されます。 "xml:space" 属性は、空白を保持するようパーサーに指示します。|  
|**FileExtension**|結果に付けるファイル拡張子。 既定値は **.CSV** です。 **FileExtension** と **Extension** の両方が指定された場合は、**FileExtension** が優先されます。|  
|**NoHeader**|出力からヘッダー行を除外するかどうかを示します。 既定値は **false**です。|  
|**Qualifier**|フィールド区切り文字またはレコード区切り文字が入った結果を囲む修飾子文字列。 結果に修飾子が入っている場合、修飾子は繰り返されます。 **Qualifier** の設定は、**FieldDelimiter** および **RecordDelimiter** の設定とは異なっている必要があります。 既定値は引用符 (") です。|  
|**RecordDelimiter**|各レコードの末尾に付けるレコード区切り記号。 既定値は \<cr>\<lf> です。|  
|**SuppressLineBreaks**|出力に入れるデータから改行を削除するかどうかを示します。 既定値は **false**です。 値が **true** の場合、**FieldDelimiter**、**RecordDelimiter**、**Qualifier** の設定を空白文字にすることはできません。|  
|**UseFormattedValues**|書式設定された文字列を CSV 出力に流し込むかどうかを示します。 **ExcelMode** が **true** の場合、既定値は **true** になり、それ以外の場合は **false** になります。|  
  
## 参照  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [表示拡張機能にデバイス情報設定を渡す](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  