---
title: XPath クエリ (SQLXMLOLEDB プロバイダー) の実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- queries [SQLXML], SQLXMLOLEDB Provider
- Base Path property
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
ms.assetid: 19063222-dc9c-48ae-a55f-778103674a9e
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: a5cad9cb9284353aa856b45bad2fa6a14ad126d5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="executing-xpath-queries-sqlxmloledb-provider"></a>XPath クエリの実行 (SQLXMLOLEDB プロバイダー)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  この例では、次の SQLXMLOLEDB プロバイダー固有のプロパティの使用を示します。  
  
-   **ClientSideXML**  
  
-   **基本パス**  
  
-   **マッピング スキーマ**  
  
 このサンプル ADO アプリケーションでは、XPath クエリ (root) を XSD マッピング スキーマ (MySchema.xml) に対して指定します。 スキーマには、 **\<連絡先 >** を持つ要素**ContactID**、 **FirstName**、および**LastName**属性。 このスキーマでは、既定のマッピングにより、要素名は同じ名前のテーブルに、単純型の属性は同じ名前の列にマップされます。  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contacts'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name='Contacts' sql:relation='Person.Contact'>   
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
 マッピング スキーマ プロパティは、XPath クエリの実行対象となるマッピング スキーマを提供します。 このマッピング スキーマには XSD または XDR スキーマを指定できます。 Base Path プロパティは、マッピング スキーマへのファイル パスを提供します。  
  
 ClientSideXML プロパティが True に設定します。 つまり、XML ドキュメントはクライアントで生成されます。  
  
 このアプリケーションでは、XPath クエリを直接指定します。 したがって、XPath 言語 {ec2a4293-e898-11d2-b1b7-00c04f680c56} を含める必要があります。  
  
> [!NOTE]  
>  コードでは、接続文字列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス名を含める必要があります。 また、この例で指定の使用、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]追加ネットワーク クライアント ソフトウェアをインストールする必要がありますデータ プロバイダー用の Native Client (SQLNCLI11)。 詳細については、次を参照してください。 [SQL Server Native Client のシステム要件](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md)です。  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security= SSPI;"  
  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
  
oTestCommand.CommandText = "root"  
oTestStream.Open  
oTestCommand.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\XPathDirect\"  
oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
oTestCommand.Properties("Output Encoding") = "utf-8"  
oTestCommand.Execute , , adExecuteStream  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  
