---
title: CONNECTIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 51685541435f4ab0192792341d2a29210dc9f504
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

サーバーに送信される要求に対して、この関数は、その要求をサポートする固有の接続の接続プロパティに関する情報を返します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>引数  
*property*  
接続のプロパティです。 *property* には、これらの値のいずれかを指定することができます。
  
|ReplTest1|データ型|Description|  
|---|---|---|
|net_transport|**nvarchar(40)**|この接続で使用される物理的な転送プロトコルを返します。 この値は NULL 許容ではありません。 有効な戻り値:<br /><br /> **HTTP**<br /> **名前付きパイプ**<br /> **Session**<br /> **共有メモリ**<br /> **SSL**<br /> **TCP**<br /><br /> および<br /><br /> **VIA**<br /><br /> 注: 接続で複数のアクティブな結果セット (MARS) の両方が有効になっているときに、接続プールが有効になっている場合は、常に**セッション**を返します。|  
|protocol_type|**nvarchar(40)**|ペイロードのプロトコルの種類を返します。 現在、TDS (TSQL) と SOAP が区別されます。 NULL 値が許可されます。|  
|auth_scheme|**nvarchar(40)**|接続の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証スキームを返します。 認証方法は、Windows 認証 (NTLM、KERBEROS、DIGEST、BASIC、NEGOTIATE) または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のいずれかです。 NULL 値は許可されません。|  
|local_net_address|**varchar(48)**|この特定の接続の対象となったサーバーの IP アドレスを返します。 TCP トランスポート プロバイダーを使用する接続の場合にのみ該当します。 NULL 値が許可されます。|  
|local_tcp_port|**int**|接続が TCP トランスポートを使用する接続であった場合に、この接続の対象となったサーバー TCP ポートを返します。 NULL 値が許可されます。|  
|client_net_address|**varchar(48)**|このサーバーに接続を試行しているクライアントのアドレスを要求します。 NULL 値が許可されます。|  
|physical_net_transport|**nvarchar(40)**|この接続で使用される物理的な転送プロトコルを返します。 接続で複数のアクティブな結果セット (MARS) が有効になっている場合、正確です。|  
|\<その他の文字列>||無効な入力の場合は NULL を返します。|  
  
## <a name="remarks"></a>Remarks  
**local_net_address** と **local_tcp_port** で NULL を返す [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。
  
戻り値は、[sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) 動的管理ビューの対応する列に表示されるオプションと同じです。 例 :
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>参照
[sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests (&) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
