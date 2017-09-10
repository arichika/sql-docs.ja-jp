---
title: "NumRings (geography データ型) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3a27cb4953f8ca0ca51ec6d3fdef80ae27dd976a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="numrings-geography-data-type"></a>NumRings (geography データ型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  内のリングの合計数を返します、**多角形**インスタンス。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Geography**タイプ、外部、内部リングは区別されません、としてすべてのリングは、外部リングに扱われることができます。  
  
## <a name="syntax"></a>構文  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>戻り値の型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]型を返す: **int**  
  
 CLR の戻り値の型: **SqlInt32**  
  
## <a name="remarks"></a>解説  
 このメソッドは NULL でない場合は、**多角形**インスタンスし、は、インスタンスが空の場合 0 を返します。 このメソッドは正確です。  
  
## <a name="examples"></a>使用例  
 2 つのリングを含む `Polygon` インスタンスを作成し、リングが 2 つあることを確認する例を次に示します。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>参照  
 [Geography インスタンスの拡張メソッド](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  