---
title: STGeomCollFromWKB (geography データ型) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|spatial-geography
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STGeomCollFromWKB (geography Data Type)
- STGeomCollFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMGeomCollFromWKB method
ms.assetid: bbed028c-9cd6-4236-b5e5-8e914a21f2e4
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7c9ed0d97c2bacd7891434dfeffe92a71cfc3709
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stgeomcollfromwkb-geography-data-type"></a>STGeomCollFromWKB (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Open Geospatial Consortium (OGC) の Well-Known Binary (WKB) 表現を基に **GeometryCollection** インスタンスを返します。
  
## <a name="syntax"></a>構文  
  
```  
  
STGeomCollFromWKB ( 'WKB_geometrycollection' , SRID )  
```  
  
## <a name="arguments"></a>引数  
 *WKB_geometrycollection*  
 返される **GeometryCollection** インスタンスの WKB 表現です。 *WKB_geometrycollection* は、**varbinary(max)** 式です。  
  
 *SRID*  
 返される **GeometryCollection** インスタンスの SRID (spatial reference ID) を表す **int** 式です。  
  
## <a name="return-types"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 戻り値の型: **geography**  
  
 CLR の戻り値の型: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 STGeomCollFromWKB() によって返される **geography** インスタンスの OGC 型は、対応する WKB 入力に基づき、**GeometryCollection**、**MultiPolygon**、**MultiLineString** または **MultiPoint** のいずれかに設定されます。  
  
 このメソッドでは、入力が適切な形式でない場合に、**FormatException** 例外がスローされます。  
  
## <a name="examples"></a>使用例  
 `STGeomCollFromWKB()` を使用して `geography` インスタンスを作成する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomCollFromWKB(0x01070000000200000001010000007593180456965EC017D9CEF753D34740010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>参照  
 [OGC の静的な地理メソッド](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
