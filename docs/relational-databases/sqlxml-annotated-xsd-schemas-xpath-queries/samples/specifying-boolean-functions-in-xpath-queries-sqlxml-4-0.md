---
title: XPath クエリ (SQLXML 4.0) に論理関数を指定する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 9366a70d31e286ec69610f3551642ec24b1e2cad
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a>XPath クエリ内での論理関数の指定 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  以下の例では、XPath クエリに論理関数を指定する方法を示します。 これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。 このサンプル スキーマについては、次を参照してください。[サンプル注釈付き XSD スキーマを XPath の例 & #40 です。SQLXML 4.0 & #41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>使用例  
  
## <a name="a-specify-the-not-boolean-function"></a>A. not() 論理関数を指定する  
 このクエリでは、すべてを返します、 **\<顧客 >** コンテキスト ノードの子要素がない**\<順序 >** 子要素。  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 **子**軸は、既定値です。 そのため、クエリは、として指定できます。  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  コピー、[サンプル スキーマ コード](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)し、テキスト ファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
2.  次のテンプレート (BooleanFunctionsA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 テンプレートを実行して得られる結果セットの一部を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a>B. true() 論理関数と false() 論理関数を指定する  
 このクエリでは、すべてを返します**\<顧客 >** がない、コンテキスト ノードの要素の子**\<順序 >** 子要素です。 具体的には、このクエリでは、発注していないすべての顧客が返されます。  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 **子**軸は、既定値です。 そのため、クエリは、として指定できます。  
  
```  
/Customer[Order=false()]  
```  
  
 このクエリは、次のと同じです。  
  
```  
/Customer[not(Order)]  
```  
  
 次のクエリでは、少なくとも 1 回発注したすべての顧客が返されます。  
  
```  
/Customer[Order=true()]  
```  
  
 このクエリは、次の指定と同じです。  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  コピー、[サンプル スキーマ コード](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)し、テキスト ファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
2.  次のテンプレート (BooleanFunctionsB.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 テンプレートを実行して得られる結果セットの一部を次に示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  
