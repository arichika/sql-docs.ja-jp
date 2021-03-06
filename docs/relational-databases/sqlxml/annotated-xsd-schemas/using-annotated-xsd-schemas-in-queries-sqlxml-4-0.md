---
title: クエリ (SQLXML 4.0) での XSD スキーマを使用して注釈が付けられた |Microsoft ドキュメント
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
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cc4d6f7c2d77f2c375765bd745bee8e35e70f622
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>クエリでの注釈付き XSD スキーマの使用 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  注釈付きスキーマに対してクエリを指定し、XSD スキーマに対してテンプレートで XPath クエリを指定して、データベースからデータを取得することができます。  
  
 **\<Sql:xpath-クエリ >** 要素では、注釈付きスキーマで定義されている XML ビューに対して XPath クエリを指定することができます。 使用して実行するのには、XPath クエリ対象となる注釈付きスキーマを識別、**マッピング スキーマ**の属性、  **\<sql:xpath-クエリ >** 要素。  
  
 テンプレートは、1 つ以上のクエリを含む有効な XML ドキュメントです。 FOR XML クエリと XPath クエリでは、ドキュメント フラグメントが返されますが、 テンプレートは、ドキュメント フラグメントのコンテナーとして機能します。テンプレートは、そのため、単一の最上位の要素を指定する方法を提供します。  
  
 このトピックの例では、テンプレートを使用して注釈付きスキーマに対する XPath クエリを指定し、データベースからデータを取得します。  
  
 たとえば、次の注釈付きスキーマを考えてみます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 わかりやすくするため、この XSD スキーマは Schema2.xml というファイルに格納されているものとします。 ここで、次のテンプレート ファイル (Schema2T.xml) で指定されている注釈付きスキーマに対し、XPath クエリを指定できます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 SQLXML 4.0 のテスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用すると、テンプレート ファイルの一部としてクエリを実行できます。 詳細については、次を参照してください。[注釈付き XDR スキーマ&#40;SQLXML 4.0 では廃止&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)です。  
  
## <a name="using-inline-mapping-schemas"></a>インライン マッピング スキーマの使用  
 注釈付きスキーマはテンプレートに直接含めることができます。このテンプレートで、インライン スキーマに対する XPath クエリを指定できます。 テンプレートはアップデートグラムとしても使用できます。  
  
 テンプレートには複数のインライン スキーマを含めることができます。 テンプレートに含まれているインライン スキーマを使用して、指定、 **id**属性の一意の値に、  **\<xsd:schema >** 要素、およびしを使用して **#idvalue**インライン スキーマを参照します。 **Id**属性と同じ働きを**sql:id** ({urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-sql} id) XDR スキーマで使用します。  
  
 たとえば、次のテンプレートでは、2 つのインライン注釈付きスキーマを指定しています。  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 このテンプレートでは 2 つの XPath クエリも指定しています。 各、  **\<xpath クエリ >** 要素を指定することにより、マッピング スキーマを一意に識別、**マッピング スキーマ**属性。  
  
 テンプレートでインライン スキーマを指定すると、 **sql: はマッピング スキーマ**注釈にも指定する必要があります、  **\<xsd:schema >** 要素。 **Sql: はマッピング スキーマ**ブール値を受け取る (0 = false、1 = true)。 インライン スキーマ**sql: はマッピング スキーマ =「1」**はインライン注釈付きスキーマとして扱われ、XML ドキュメントでは返されません。  
  
 **Sql: はマッピング スキーマ**注釈がテンプレートの名前空間に属する**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql}-sql**です。  
  
 この例をテストするには、テンプレート (InlineSchemaTemplate.xml) をローカルのディレクトリに保存した後、SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。 詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 指定するだけでなく、**マッピング スキーマ**属性を **\<sql:xpath-クエリ >** 要素 (XPath クエリがある) 場合のテンプレート、または   **\<updg:sync >** 要素アップデート グラムでは、次を実行することができます。  
  
-   指定して、**マッピング スキーマ**属性を**\<ルート >** テンプレート内の要素 (グローバル宣言)。 このマッピング スキーマは、明示的ないる、すべての XPath およびアップデート グラム ノードで使用される既定のスキーマになります**マッピング スキーマ**注釈。  
  
-   指定して、**マッピング スキーマ**、ADO を使用して属性**コマンド**オブジェクト。  
  
 **マッピング スキーマ**属性で指定されている、  **\<xpath クエリ >** または **\<updg:sync >** 要素が一番多い優先順位です。ADO**コマンド**オブジェクトには最低の優先順位。  
  
 テンプレートの XPath クエリを指定し、XPath クエリの実行対象となるマッピング スキーマを指定しない場合、XPath クエリとして扱われます、 **dbobject**型クエリ。 たとえば、次のテンプレートを考えてみます。  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 このテンプレートでは、XPath クエリが指定されていますが、マッピング スキーマが指定されていません。 したがって、このクエリとして扱う、 **dbobject** Production.ProductPhoto のテーブル名の種類のクエリと@ProductPhotoID= '100' は ID 値 100 は製品の写真を検索する述語です。 @LargePhoto 値を取得する対象の列です。  
  
  
