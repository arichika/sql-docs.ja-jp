---
title: sys.dm_server_registry (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_server_registry_TSQL
- sys.dm_server_registry
- dm_server_registry
- sys.dm_server_registry_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_registry dynamic management view
ms.assetid: 9b3e0c74-2e99-4996-a383-104d51831e97
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4207ee898acec0d0f5f2f00594835ffcef40e9d1
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="sysdmserverregistry-transact-sql"></a>sys.dm_server_registry (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスについて Windows レジストリに格納されている構成情報とインストール情報を返します。 レジストリ キーごとに 1 行を返します。 この動的管理ビューを使用して情報を返すように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ホスト マシンまたはネットワークの構成値のインスタンスで使用できるサービス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|registry_key|**nvarchar (256)**|レジストリ キーの名前。 NULL 値が許可されます。|  
|value_name|**nvarchar (256)**|キー値の名前。 これに表示される項目、**名前**レジストリ エディターの列です。 NULL 値が許可されます。|  
|value_data|**sql_variant**|キー データの値。 これに表示される値、**データ**レジストリ エディター、指定されたエントリの列です。 NULL 値が許可されます。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-display-the-sql-server-services"></a>A. SQL Server サービスを表示します。  
 次の例では、SQL Server の現在のインスタンスについて SQL Server および SQL Server エージェント サービスのレジストリ キーの値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%ControlSet%';  
```  
  
### <a name="b-display-the-sql-server-agent-registry-key-values"></a>B. SQL Server エージェントのレジストリ キーの値を表示します。  
 次の例では、SQL Server の現在のインスタンスについて SQL Server エージェントのレジストリ キーの値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SQLAgent%';  
```  
  
### <a name="c-display-the-current-version-of-the-instance-of-sql-server"></a>C. SQL Server のインスタンスの現在のバージョンを表示します。  
 次の例では、SQL Server の現在のインスタンスのバージョンを返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key = N'CurrentVersion';  
```  
  
### <a name="d-display-the-parameters-passed-to-the-instance-of-sql-server-during-startup"></a>D. スタートアップ中に SQL Server のインスタンスに渡されるパラメーターを表示します。  
 次の例では、スタートアップ中に SQL Server のインスタンスに渡されるパラメーターを返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%Parameters';  
```  
  
### <a name="e-return-network-configuration-information-for-the-instance-of-sql-server"></a>E. SQL Server のインスタンスに関するネットワーク構成情報を返します。  
 次の例では、SQL Server の現在のインスタンスに関するネットワーク構成の値を返します。  
  
```  
SELECT registry_key, value_name, value_data  
FROM sys.dm_server_registry  
WHERE registry_key LIKE N'%SuperSocketNetLib%';  
```  
  
## <a name="see-also"></a>参照  
 [sys.dm_server_services &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-services-transact-sql.md)  
  
  
