---
title: SetEmailConfiguration メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: wmi-provider-library-reference
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SetEmailConfiguration (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- SetEmailConfiguration method
ms.assetid: b40a2224-2c90-4d32-892f-1fe73a0591ca
caps.latest.revision: 19
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: bea00d4571559e43e1127ddad41fc194fcdead10
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configurationsetting-method---setemailconfiguration"></a>ConfigurationSetting メソッド - SetEmailConfiguration
  レポート サーバーが電子メール送信に使用する電子メール配信拡張機能を構成します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub SetEmailConfiguration(ByVal SendUsingSMTPServer As Boolean, _  
    ByVal SMTPServer As String, ByVal SenderEmailAddress As String, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void SetEmailConfiguration (Boolean SendUsingSMTPServer,   
   string SMTPServer, string SenderEmailAddress,   
   out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *SendUsingSMTPServer*  
 サーバーが電子メール送信に SMTP サーバーを使用するかどうかを示すブール値。 この値は、true にのみ設定できます。 既定値は false です。  
  
 *SMTPServer*  
 SMTP サーバーの名前または IP アドレスを含む文字列。  
  
 *SenderEmailAddress*  
 レポート サーバーから送信された電子メールの 'From:' フィールドで使用された電子メール アドレス。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
 *SendUsingSMTPServer* パラメーターが **true**の場合、レポート サーバー構成ファイルの **SendUsing** エントリは 1 に設定されます。 *SendUsingSMTPServer* が **false**の場合、 **SendUsing** エントリは構成されません。  
  
 このメソッドでは、レポート サーバー構成ファイルの **SendUsing** エントリを 1 以外の値に設定することはできません。 SMTP メール以外を使用するようにレポート サーバーを構成するには、構成ファイルを手動で編集する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
