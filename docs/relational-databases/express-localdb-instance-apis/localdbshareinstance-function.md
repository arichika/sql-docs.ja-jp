---
title: LocalDBShareInstance 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: localdb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- LocalDBShareInstance
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: 21eb3b9a-7d32-455b-89bb-f624198cd202
caps.latest.revision: 9
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e57ff8210a9676920805b655c7c2fa44c27f3c28
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="localdbshareinstance-function"></a>LocalDBShareInstance 関数
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  指定した共有名を使用して、指定した SQL Server Express LocalDB インスタンスをコンピューターの他のユーザーと共有します。  
  
 **ヘッダー ファイル:** sqlncli.h  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LocalDBShareInstance(  
           PSID pOwnerSID,  
           PCWSTR pInstancePrivateName,  
           PCWSTR pInstanceSharedName,   
           DWORD dwFlags   
);  
```  
  
## <a name="parameters"></a>パラメーター  
 *pOwnerSID*  
 [入力] インスタンスの所有者の SID。  
  
 *pInstancePrivateName*  
 [入力] 共有する LocalDB インスタンスのプライベート名。  
  
 *pInstanceSharedName*  
 [入力] 共有する LocalDB インスタンスの共有名。  
  
 *dwFlags*  
 [入力] 将来の使用のために予約されています。 現時点では、0 に設定する必要があります。  
  
## <a name="returns"></a>返します。  
 S_OK  
 関数が正常に実行されました。  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB は、コンピューターにインストールされていません。  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 指定した 1 つまたは複数の入力パラメーターが無効です。  
  
 [LOCALDB_ERROR_INVALID_INSTANCE_NAME](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-instance-name.md)  
 指定したインスタンス名は無効です。  
  
 [LOCALDB_ERROR_UNKNOWN_INSTANCE](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-instance.md)  
 指定したインスタンスは存在しません。  
  
 [LOCALDB_ERROR_ADMIN_RIGHTS_REQUIRED](../../relational-databases/express-localdb-error-messages/localdb-error-admin-rights-required.md)  
 この操作を実行するためには、管理者権限が必要です。  
  
 [LOCALDB_ERROR_SHARED_NAME_TAKEN](../../relational-databases/express-localdb-error-messages/localdb-error-shared-name-taken.md)  
 指定した共有名は既に使用されています。  
  
 [LOCALDB_ERROR_INSTANCE_ALREADY_SHARED](../../relational-databases/express-localdb-error-messages/localdb-error-instance-already-shared.md)  
 指定したインスタンスは既に共有されています。  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 予期しないエラーが発生しました。 詳細をイベント ログで確認してください。  
  
## <a name="remarks"></a>解説  
 LocalDB API を使用するコード サンプルは、次を参照してください。 [SQL Server Express LocalDB リファレンス](../../relational-databases/sql-server-express-localdb-reference.md)です。  
  
## <a name="see-also"></a>参照  
 [SQL Server Express LocalDB ヘッダーとバージョン情報](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
