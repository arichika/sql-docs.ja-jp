---
title: SQL Server Analysis Services 表形式の 1200 モデルでサポートされるデータ ソース |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31ef1eb37f85e3e9ec7a7ea7d7eadee03b6c9c20
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="data-sources-supported-in-sql-server-analysis-services-tabular-1200-models"></a>SQL Server Analysis Services 表形式モデル 1200 にサポートされるデータ ソース
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  
この記事では、SQL Server Analysis Services 表形式モデル 1200 より低い互換性レベルで使用できるデータ ソースの種類について説明します。 

1400 の互換性レベル モデルでは、次を参照してください。 [SQL Server Analysis Services 表形式の 1400 モデルでサポートされるデータ ソース](data-sources-supported-ssas-tabular-1400.md)です。

Azure Analysis Services では、次を参照してください。 [Azure Analysis Services でサポートされるデータ ソース](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)です。
  
##  <a name="bkmk_supported_ds"></a> メモリ内のテーブル モデルに対してサポートされているデータ ソース  
[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]をインストールする際のセットアップで、各データ ソースに対して挙げられているプロバイダーはインストールされません。 その他のアプリケーションがコンピューター上で一部のプロバイダーをインストールする可能性があります。 それ以外の場合に、ダウンロードしてプロバイダーをインストールする必要があります。  
  
|||||  
|-|-|-|-|  
|ソース|バージョン|ファイルの種類|[プロバイダー]|  
|Access データベース|Microsoft Access 2010 以降。|.accdb または .mdb|ACE 14 OLE DB プロバイダー|  
|SQL Server リレーショナル データベース|SQL Server 2008 以降、SQL Server データ ウェアハウス 2008 およびそれ以降、Azure SQL Database、Azure SQL Data Warehouse、Analytics Platform System (APS)<br /><br /> <br /><br /> Analytics Platform System (APS) として SQL Server 並列データ ウェアハウス (PDW) 呼ばれていました。 当初、Analysis Services から PDW に接続するには、特別なデータ プロバイダーが必要でした。 このプロバイダーは、SQL Server 2012 で変更されました。 SQL Server 2012 以降、PDW/APS への接続には、SQL Server Native Client が使用されます。 |(該当なし)|OLE DB Provider for SQL Server<br /><br /> SQL Server Native Client OLE DB プロバイダー<br /><br /> SQL Server Native 10.0 Client OLE DB プロバイダー<br /><br /> .NET Framework Data Provider for SQL Client|  
|Oracle リレーショナル データベース|Oracle 9i 以降。|(該当なし)|Oracle OLE DB プロバイダー<br /><br /> .NET Framework Data Provider for Oracle Client<br /><br /> .NET Framework Data Provider for SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Teradata リレーショナル データベース|Teradata V2R6 以降|(該当なし)|TDOLEDB OLE DB プロバイダー<br /><br /> .Net Data Provider for Teradata|  
|Informix リレーショナル データベース||(該当なし)|Informix OLE DB プロバイダー|  
|IBM DB2 リレーショナル データベース|8.1|(該当なし)|DB2OLEDB|  
|Sybase Adaptive Server Enterprise (ASE) リレーショナル データベース|15.0.2|(該当なし)|Sybase OLE DB プロバイダー|  
|その他のリレーショナル データベース|(該当なし)|(該当なし)|OLE DB プロバイダーまたは ODBC ドライバー|  
|テキスト ファイル|(該当なし)|.txt、.tab、.csv|ACE 14 OLE DB Provider for Microsoft Access|  
|Microsoft Excel ファイル|Excel 2010 以降|.xlsx、.xlsm、.xlsb、.xltx、.xltm|ACE 14 OLE DB プロバイダー|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック|Microsoft SQL Server 2008 以降の Analysis Services|.xlsx、.xlsm、.xlsb、.xltx、.xltm|ASOLEDB 10.5<br /><br /> ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] がインストールされている SharePoint ファームにパブリッシュされた [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ブックでのみ使用)|  
|Analysis Services キューブ|Microsoft SQL Server 2008 以降の Analysis Services|(該当なし)|ASOLEDB 10|  
|データ フィード<br /><br /> (Reporting Services のレポート、Atom サービス ドキュメント、Microsoft Azure Marketplace DataMarket、および単一のデータ フィードからのデータのインポートに使用)|Atom 1.0 形式<br /><br /> Windows Communication Foundation (WCF) データ サービス (以前の ADO.NET Data Services) として公開されている任意のデータベースまたはドキュメント。|`.atomsvc` サービス ドキュメントの 1 つまたは複数のフィードを定義します。<br /><br /> .atom (Atom Web フィード ドキュメント用)|Microsoft Data Feed Provider for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> 用の .NET Framework データ フィード データ プロバイダー [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Office データ接続ファイル||.odc||  
  
  
##  <a name="bkmk_supported_ds_dq"></a> DirectQuery モデルのサポートされるデータ ソース  
 DirectQuery はインメモリ ストレージ モードの代わりに使用できます。このモデルでは、クエリがバックエンド データ システムにルーティングされ、結果が直接返されます。モデル (モデルが読み込まれている場合は RAM) 内にすべてのデータが格納されることはありません。 Analysis Services は、ネイティブ データベース クエリ構文でクエリがあるために、このモードでデータ ソースの小さなサブセットがサポートします。  
  
データ ソース   |バージョン  |[プロバイダー]
---------|---------|---------
Microsoft SQL Server    |  2008 以降      |       OLE DB Provider for SQL Server、SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client  
Azure SQL Database    |   すべて      |  OLE DB Provider for SQL Server、SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client            
Microsoft Azure SQL Data Warehouse     |   すべて     |  SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client       
Microsoft SQL Analytics Platform System (APS)     |   すべて      |  OLE DB Provider for SQL Server、SQL Server Native Client OLE DB Provider、.NET Framework Data Provider for SQL Client       
Oracle リレーショナル データベース     |  Oracle 9i 以降       |  Oracle OLE DB プロバイダー       
Teradata リレーショナル データベース    |  Teradata V2R6 以降     | .Net Data Provider for Teradata    

  
##  <a name="bkmk_tips"></a> データ ソースの選択に関するヒント  
  
リレーショナル データベースからテーブルをインポートする場合、インポート時には *外部キー* リレーションシップを使用して、モデル デザイナーのテーブル間にリレーションシップが作成されるので、手順を省略できます。  
  
複数のテーブルをまとめてインポートしてから不必要なテーブルを削除することで、手順を省略することもできます。 テーブルを 1 つずつインポートしても、テーブル間のリレーションシップを手動で作成する必要が生じる場合があります。  
  
複数のデータ ソースに、類似データが格納されている列があれば、モデル デザイナー内でリレーションシップを作成する理由になります。 異種のデータ ソースを使用する場合は、同一データまたは類似データが格納されている他のデータ ソースのテーブルにマップできる列のあるテーブルを選択します。  
  
OLE DB プロバイダーでは、大規模なデータに対して高いパフォーマンスを発揮します。 同じデータ ソースに対して数種類のプロバイダーの中から選択する場合は、最初に OLE DB プロバイダーを選択することをお勧めします。  

## <a name="see-also"></a>参照

[データ ソースが SQL Server Analysis Services で 1400 の表形式モデルをサポート](data-sources-supported-ssas-tabular-1400.md)

[Azure Analysis Services でサポートされるデータ ソース](https://docs.microsoft.com/azure/analysis-services/analysis-services-datasource)   