---
title: 権限の付与キューブまたはモデル (Analysis Services) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f028885e91dd67869e15bab4d7b64cc97b64f9bb
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="grant-cube-or-model-permissions-analysis-services"></a>キューブ権限またはモデル権限の付与 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブまたは表形式モデルは、Analysis Services データ モデルの主要なクエリ オブジェクトです。 アドホック データ探索のために Excel から多次元データまたは表形式データに接続する場合、ユーザーは、通常、最初に、ピボット レポート オブジェクトの基礎となるデータ構造として、特定のキューブまたは表形式モデルを選択します。 このトピックでは、キューブまたは表形式データへのアクセスに必要な権限を付与する方法について説明します。  
  
 既定では、サーバー管理者とデータベース管理者を除いて、データベースのクエリ キューブに対する権限を持ちません。 管理者以外がキューブにアクセスするには、キューブが含まれているデータベースのために作成されたロールでのメンバーシップが必要です。 メンバーシップは、Active Directory またはローカル コンピューターに定義された、Windows ユーザー アカウントまたはグループ アカウントに対してサポートされています。 開始する前に、作成するロールではどのアカウントにメンバーシップが割り当てられるかを判別します。  
  
 キューブへの **Read** アクセス権には、そのキューブ内のディメンション、メジャー グループ、およびパースペクティブに対する権限も付属します。 ほとんどの管理者は、キューブ レベルで Read 権限を付与し、特定のオブジェクト、関連するデータ、またはユーザー ID に対する権限を制限します。  
  
 後続のソリューション配置でもロール定義を保持するには、モデルの不可欠な要素として [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] にロールを定義し、データベースがパブリッシュされた後、データベース管理者が [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] にロール メンバーシップを割り当てることがベスト プラクティスとなります。 ただし、どちらのツールも両方のタスクに使用できます。 手順を簡素化するため、ロール定義とメンバーシップの両方に [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用します。  
  
> [!NOTE]  
>  サーバー管理者、またはフル コントロール権限を持つデータベース管理者のみが、ソース ファイルからサーバーへのキューブの配置や、ロールの作成とメンバーへの割り当てを実行できます。 これらの権限レベルの詳細については、「[Analysis Services インスタンスにサーバー管理者権限を付与する](../../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)」および「[データベース権限の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)」をご覧ください。  
  
#### <a name="step-1-create-the-role"></a>手順 1: ロールの作成  
  
1.  SSMS で、Analysis Services に接続します。 この手順について不明な点がある場合は、「[クライアント アプリケーションからの接続 (Analysis Services)](../../analysis-services/instances/connect-from-client-applications-analysis-services.md)」をご覧ください。  
  
2.  オブジェクト エクスプローラーで **[データベース]** フォルダーを開き、データベースを選択します。  
  
3.  **[ロール]** を右クリックし、 **[新しいロール]** を選択します。 ロールがデータベース レベルで作成され、データベース内のオブジェクトに適用されることに注意してください。 データベース間でロールを共有することはできません。  
  
4.  **[全般]** ペインで、名前を入力し、必要に応じて説明を入力します。 また、このペインには、フル コントロール、データベースの処理、定義の読み取りなど、いくつかのデータベース権限も含まれています。 これらのいずれの権限も、キューブまたは表形式モデルに対するクエリの実行には必要ありません。 これらの権限の詳細については、「[データベース権限の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-database-permissions-analysis-services.md)」をご覧ください。  
  
5.  名前および必要に応じて説明を入力した後、次の手順に進みます。  
  
#### <a name="step-2-assign-membership"></a>手順 2: メンバーシップの割り当て  
  
1.  **[メンバーシップ]** ペインで、 **[追加]** をクリックして、このロールを使用してキューブにアクセスする Windows ユーザー アカウントまたはグループ アカウントを入力します。 Analysis Services では、Windows セキュリティ ID のみがサポートされています。 この手順ではデータベース ログインを作成しないことに注意してください。 Analysis Services では、ユーザーは Windows アカウントで接続します。  
  
2.  次の手順に進み、キューブ権限を設定します。  
  
     データ ソース ペインをスキップしていることに注意してください。 Analysis Services データの通常のコンシューマーのほとんどには、データ ソース オブジェクトに対する権限は必要ありません。 これらの権限レベルの詳細については、「 [データ ソース オブジェクトに対する権限の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md) 」をご覧ください。  
  
#### <a name="step-3-set-cube-permissions"></a>手順 3: キューブ権限の設定  
  
1.  **[キューブ]** ペインで、キューブを選択し、 **[読み取り]** アクセス権または **[読み取り/書き込み]** アクセス権をクリックします。  
  
     ほとんどの操作は **[読み取り]** アクセス権で十分です。 **[読み取り/書き込み]** は、処理ではなく書き戻しにのみ使用します。 この機能の詳細については、「 [パーティションの書き戻しの設定](../../analysis-services/multidimensional-models/set-partition-writeback.md) 」をご覧ください。  
  
     複数のキューブのほか、[ロールの作成] ダイアログ ボックスで使用可能なその他のオブジェクトも選択できることに注意してください。 キューブに対する権限を付与すると、そのキューブに関連付けられたディメンションおよびパースペクティブへのアクセスが承認されます。 キューブに既に表されているオブジェクトを手動で追加する必要はありません。  
  
     特定のメジャーを使用できないようにするなどの目的で、オブジェクトまたはユーザーによって承認方法を変化させる必要がある場合、特定のオブジェクトやセルに対するアクセスをアトミックに許可または拒否できます。 詳細については、「[ディメンション データへのカスタム アクセス権の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)」および「[セル データへのカスタム アクセス権の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)」をご覧ください。  
  
2.  この時点で **[OK]** をクリックすると、このロールのすべてのメンバーが、指定した権限レベルでキューブにアクセスできるようになります。  
  
     **[キューブ]** ペインでは、 **[ドリルスルーとローカル キューブ]** を使用してサーバー キューブからローカル キューブを作成するための権限をユーザーに付与したり、 **[ドリルスルー]** 権限を使用してドリルスルーのみを許可したりできることに注意してください。  
  
     さらに、このペインでは、キューブに対する **[データベースの処理]** 権限を付与して、このロールのすべてのメンバーがこのキューブのデータを処理できるようにすることができます。 処理は通常制限付きの操作であるため、そのタスクを管理者に委ねるか、または特にそのタスク用に別途ロールを定義することをお勧めします。 処理権限のベスト プラクティスの詳細については、「[処理権限の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-process-permissions-analysis-services.md)」をご覧ください。  
  
#### <a name="step-4-test"></a>手順 4: テスト  
  
1.  Excel を使用して、キューブのアクセス権をテストします。 また、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用すると、次に説明するのと同じ方法に従って、管理者以外のユーザーとしてアプリケーションを実行できます。  
  
    > [!NOTE]  
    >  Analysis Services 管理者の場合、管理者権限がより権限の小さいロールと結合されるため、個別にロール権限をテストするのが難しくなります。 テストを簡素化するため、テスト対象のロールに割り当てられたアカウントを使用して、SSMS の 2 番目のインスタンスを開くことをお勧めします。  
  
2.  Shift キーを押したまま **[Excel]** を右クリックして、 **[別のユーザーとして実行]** オプションにアクセスします。 このロールにメンバーシップがある Windows ユーザー アカウントまたはグループ アカウントの 1 つを入力します。  
  
3.  Excel が開いたら、[データ] タブを使用して Analysis Services に接続します。 別の Windows ユーザーとして Excel を実行しているため、ロールをテストする際には **[Windows 認証を使用する]** オプションが適切な資格情報の種類です。 この手順について不明な点がある場合は、「[クライアント アプリケーションからの接続 (Analysis Services)](../../analysis-services/instances/connect-from-client-applications-analysis-services.md)」をご覧ください。  
  
     接続に関するエラーが表示された場合は、Analysis Services のポート構成を確認し、サーバーがリモート接続に対応していることを確認します。 ポートの構成については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) 」をご覧ください。  
  
#### <a name="step-5-script-role-definition-and-assignments"></a>手順 5: スクリプト ロールの定義と割り当て  
  
1.  最後の手順として、作成したロール定義をキャプチャするスクリプトを生成します。  
  
     [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] からプロジェクトを再配置すると、プロジェクト内に定義されていないロールまたはロール メンバーシップが上書きされます。 再配置後にロールおよびロール メンバーシップを最も速く再構築する方法は、スクリプトを使用することです。  
  
2.  SSMS で、 **[ロール]** フォルダーに移動し、既存のロールを右クリックします。  
  
3.  **[ロールをスクリプト化]** | **[CREATE TO]** | **[ファイル]** の順に選択します。  
  
4.  拡張子を .xmla にしてファイルを保存します。 スクリプトをテストするには、現在のロールを削除し、SSMS でファイルを開き、F5 キーを押してスクリプトを実行します。  
  
## <a name="next-step"></a>次の手順  
 セルまたはディメンション データへのアクセスを制限するようにキューブ権限を調整できます。 詳細については、「[ディメンション データへのカスタム アクセス権の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)」および「[セル データへのカスタム アクセス権の付与 (Analysis Services)](../../analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services でサポートされる認証方法](../../analysis-services/instances/authentication-methodologies-supported-by-analysis-services.md)   
 [データ マイニング構造およびモデルに対する権限を与える&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [データ ソース オブジェクト & #40; に対する権限を付与します。Analysis Services & #41;](../../analysis-services/multidimensional-models/grant-permissions-on-a-data-source-object-analysis-services.md)  
  
  
