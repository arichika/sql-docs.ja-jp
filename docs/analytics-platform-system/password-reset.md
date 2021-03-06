---
title: パスワード リセット - Analytics Platform System |Microsoft ドキュメント
description: パスワードのリセット ページでは、分析プラットフォーム システムで使用される管理者アカウントのパスワードを変更することができます。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 63fbb097bf1ca926223ce7c0114c8da5d10cd969
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
---
# <a name="password-reset---analytics-platform-system"></a>パスワード リセット - 分析プラットフォーム システム
**パスワード リセット** ページでは、分析プラットフォーム システムで使用される管理者アカウントのパスワードを変更することができます。  
  
> [!WARNING]  
> 常に使用する、 **Configuration Manager**アプライアンス ドメインの管理者パスワードを更新します。 その他のメソッドは、Analytics Platform System のすべてのコンポーネントを更新できなかった可能性がおよび、アプライアンスのアクセスに関する問題が発生する可能性があります。  
  
アプライアンスが配信されるときに、分析プラットフォーム システム パスワードが指定できます。 常に、アプライアンスを担当するときは、新しい値にパスワードを変更します。 3 つのパスワードを更新するにがあります。 パスワードを互いに同じである必要はありません。  
  
**F<*xxxx*>\Administrator**  
**管理者**のアプライアンス ドメイン。  
  
**.\Administrator**  
ローカル**管理者**仮想マシンをホストするコンピューター上のアカウントです。  
  
> [!IMPORTANT]  
> アプライアンスの update 1、 **Configuration Manager** PDW VM の全体でローカル管理者アカウントのパスワード正しくない変更しません。 これが必要な場合は、その他については CSS にお問い合わせください。  
  
**sa**  
**Sa** SQL Server にログインします。 **sa**のメンバーである、 **sysadmin**固定サーバー ロールと SQL Server の管理者です。 パスワード、 **sa**を使用してログインを変更することも、 **ALTER LOGIN**ステートメントです。  
  
## <a name="password-requirements"></a>パスワードの要件  
ドメイン管理者の資格情報と、システム管理者の資格情報の両方の資格情報の種類ごとにパスワードの強度ポリシーに準拠します。 ドメインに新しいパスワードを更新するドメイン管理者の資格情報を変更するときに SQL Server PDW 全体で必要な場所です。  
  
> [!IMPORTANT]  
> SQL Server PDW は、ドル記号をサポートしていません (**$**) では、ドメイン管理者またはローカル管理者パスワードです。 文字**^ % &**が、PowerShell のこれらの特殊文字として既定では、パスワードで許可されています。 これらの文字のいずれかが、システム管理者または SQL Server のパスワードに使用される場合**sa**アカウント (、 **AdminPassword**と**PdwSAPassword**時にパラメーターセットアップ)、セットアップなどのインストール、アップグレード、REPLACENODE、および、修正プログラムの適用は失敗します。 現在のパスワードには、サポートされていない文字が含まれている場合は、アップグレードの成功を確実には、アップグレードを実行する前にこのような文字がないように、これらのパスワードを変更します。 アップグレードの完了後は、元の値にこれらのパスワードを設定できます。 パスワードの要件の詳細については、次を参照してください。 [ALTER LOGIN](../t-sql/statements/alter-login-transact-sql.md)です。  
  
## <a name="to-reset-a-password"></a>パスワードをリセットするには  
  
1.  コントロールのノードと起動への接続、 **Configuration Manager** (**dwconfig.exe**)。 詳細については、次を参照してください。[構成マネージャーを起動&#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)です。  
  
2.  左側のウィンドウで、 **Configuration Manager**をクリックして**パスワード リセット**です。  
  
3.  管理者の種類を選択して、**アカウント**ドロップダウン メニューに新しいパスワードを入力し、**パスワード**と**パスワードの確認**ボックス。 をクリックして**適用**して変更を保存します。  
  
    これらのアカウントに対して行った変更は、現在アクティブなセッションには影響しませんが、各ユーザーの次回のログオンに使用されます。  
  
    ![SQL Server DWConfig パスワード](./media/password-reset/SQL_Server_PDW_DWConfig_TopPW.png "SQL_Server_PDW_DWConfig_TopPW")  
  
## <a name="see-also"></a>参照  
[ディレクトリ サービス復元モードでの AD ノードにログオンするための管理者パスワードの設定&#40;DSRM&#41; &#40;分析プラットフォーム システム&#41;](set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode.md)  
[構成マネージャーを起動&#40;分析プラットフォーム システム&#41;](launch-the-configuration-manager.md)  
  
