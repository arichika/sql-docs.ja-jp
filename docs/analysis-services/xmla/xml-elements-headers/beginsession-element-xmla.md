---
title: "BeginSession 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- BeginSession Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b3ebacd7677aecf7c953d966e3001cbe8f8f7691
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="beginsession-element-xmla"></a>BeginSession 要素 (XMLA)
  インスタンスで新しいセッションを開始する SOAP 要求メッセージの SOAP ヘッダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <BeginSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **BeginSession**ヘッダー要素に送信される SOAP 要求の一部である、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、および明示的にインスタンスで新しいセッションを開始します。 SOAP 応答によって返される SOAP ヘッダーが含まれています、[セッション](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)新しいセッションを識別する要素。 この新しいセッション識別子は保存されを使用して後続の SOAP 要求で送信された、**セッション**ヘッダー要素。  
  
 場合、 **BeginSession**ヘッダー要素は送信されず、セッションが明示的に開始されていません。 セッションが明示的に開始されない場合、そのセッション上のトランザクションを管理することはできません。 つまり、Analysis (XMLA) コマンドを次の XML を使用することはできません: [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)です。 暗黙的に開始されたセッションで実行されるすべての XMLA メソッドおよびコマンドは、アトミックなトランザクションと見なされます。  
  
## <a name="see-also"></a>参照  
 [EndSession 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Session 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [管理接続およびセッション (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダーと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  