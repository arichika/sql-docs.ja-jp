---
title: ListSSLCertificateBindings メソッド (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
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
helpviewer_keywords:
- ListSSLCertificateBindings method
ms.assetid: d12d280c-9b6f-47a8-bcd9-34cde31c8886
caps.latest.revision: 12
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d7b75526aafe7bc9a7379a3d73d526c64e1c583a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configurationsetting-method---listsslcertificatebindings"></a>ConfigurationSetting メソッド - ListSSLCertificateBindings
  コンピューターにインストールされている SSL 証明書の一覧を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Sub ListSSLCertificateBindings(ByVal LCID As Int32, ByRef Application() As String, _  
    ByRef CertificateHash() As String, ByRef IPAddresses() As String, ByRef Port() As Int32, _  
    ByRef Errors() As String, ByRef Length As Int32, _  
    ByRef HRESULT As Int32)  
```  
  
```csharp  
public void ListSSLCertificateBindings(Int32 Lcid, out string[] Application,   
    out string[] CertificateHash,out string[] IPAddress,   
    out Int32[] Port, out string Errors,   
    out Int32 length, out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>パラメーター  
 *LCID (LCID)*  
 返されるエラー メッセージに使用するロケール。  
  
 *Application[]*  
 [out] 証明書のバインドを含むアプリケーション。  
  
 *CertificateHash[]*  
 [out] 証明書のハッシュ。  
  
 *IPAddress[]*  
 [out] アプリケーションの IP アドレス。  
  
 *Port[]*  
 [out] rsreportserver.config のバインドに格納されているポート番号。  
  
 *Errors[]*  
 [out] 発生したエラーの説明。  
  
 *[データ型]*  
 [out] メソッドによって返される配列の長さ。  
  
 *HRESULT*  
 [out] 呼び出しの成功または失敗を示す値。  
  
## <a name="return-value"></a>戻り値  
 メソッド呼び出しの成功または失敗を示す *HRESULT* を返します。 値 0 は、メソッド呼び出しが成功したことを示します。 0 以外の値は、エラーが発生したことを示します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_ConfigurationSetting メンバー](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  
