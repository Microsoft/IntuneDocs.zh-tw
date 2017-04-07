---
title: "如何使用 Microsoft Intune 建立自訂 VPN 設定檔"
titleSuffix: Intune Azure preview
description: "在 Intune 中使用自訂組態來建立 VPN 設定檔。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: ca4f1adc5704ecd66d2af7823f95ca63ec20469e
ms.openlocfilehash: 990f3ff6528b537d1ea62c82440f1e46bcde8c95
ms.lasthandoff: 03/17/2017


---

# <a name="how-to-create-custom-vpn-profiles-in-microsoft-intune"></a>如何在 Microsoft Intune 中建立自訂 VPN 設定檔

## <a name="create-a-custom-configuration"></a>建立自訂組態
您可以使用 Intune 自訂設定原則來建立下列各項的 VPN 設定檔：

* 執行 Android 4 和更新版本的裝置
* 執行 Windows 8.1 和更新版本的已註冊裝置
* 執行 Windows Phone 8.1 和更新版本的裝置
* 執行 Windows 10 Desktop 的已註冊裝置 
* 執行 Windows 10 行動裝置版的裝置

標準 Intune VPN 原則未包含您想要使用的設定時，這類型的原則十分有用。

## <a name="to-create-a-custom-configuration-policy"></a>建立自訂設定原則：

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
4. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
5. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
6. 在 [建立設定檔] 刀鋒視窗中，為 VPN 設定檔輸入 [名稱] 及 [描述]。
7. 從 [平台] 下拉式清單中，選取要套用 VPN 設定的裝置平台。 您目前可以為自訂裝置設定選擇下列平台之一︰
    - **Android**
    - **iOS** (使用您從 Apple Configurator 匯出的檔案進行設定)。
    - **macOS** (使用您從 Apple Configurator 匯出的檔案進行設定)。
    - **Windows Phone 8.1**
    - **Windows 10 及更新版本**
6. 從 [設定檔] 類型下拉式清單中選擇 [自訂]。
7. 在 [自訂 OMA URI 設定] 刀鋒視窗中，為您要指定的每個 URI 設定選擇 [新增]，以提供所要求的資訊，然後選擇 [確定]。 範例如下：

   ![VPN 設定檔自訂組態對話方塊](./media/Intune_Add_VPN_URI.png)

4.  輸入所有必要的 URI 設定之後，請選擇 [確定]，然後在 [建立設定檔] 刀鋒視窗中選擇 [建立]。

隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](how-to-assign-device-profiles.md)。

## <a name="example-uri-settings"></a>範例 URI 設定

這些設定可以用來為稱為 Contoso 的虛構公司中的 VPN 建立自訂設定。
如需您可使用之所有設定的完整詳細資訊，請參閱 [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)。

原生 Contoso VPN (IKEv2)：./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

vpn.contoso.com ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

Ikev2 ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

SplitTunnel ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

Eap ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration &lt;EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;EapMethod&gt;&lt;Type xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;13&lt;/Type&gt;&lt;VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorId&gt;&lt;VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/VendorType&gt;&lt;AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon"&gt;0&lt;/AuthorId&gt;&lt;/EapMethod&gt;&lt;Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig"&gt;&lt;Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1"&gt;&lt;Type&gt;13&lt;/Type&gt;&lt;EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1"&gt;&lt;CredentialsSource&gt;&lt;CertificateStore&gt;&lt;SimpleCertSelection&gt;true&lt;/SimpleCertSelection&gt;&lt;/CertificateStore&gt;&lt;/CredentialsSource&gt;&lt;ServerValidation&gt;&lt;DisableUserPromptForServerValidation&gt;false&lt;/DisableUserPromptForServerValidation&gt;&lt;ServerNames&gt;&lt;/ServerNames&gt;&lt;/ServerValidation&gt;&lt;DifferentUsername&gt;false&lt;/DifferentUsername&gt;&lt;PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/PerformServerValidation&gt;&lt;AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2"&gt;false&lt;/AcceptServerName&gt;&lt;/EapType&gt;&lt;/Eap&gt;&lt;/Config&gt;&lt;/EapHostConfig&gt;

**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal** True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials** 1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection** Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address** 10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize** 8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn** true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id** %PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id** %PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id** Microsoft.MicrosoftEdge_8wekyb3d8bbwe

若對這些設定的使用方式有任何疑問，或想更詳細了解它們的功用，客戶應參考設定服務提供者 (CSP) 說明文件︰https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx。

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>適用於 PulseSecure 上 Android 個別應用程式 VPN 的 URI 設定
### <a name="custom-uri-for-package-list"></a>套件清單的自訂 URI
-  資料類型 = 字串
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  值 = 分隔符號分隔的套件清單。
   - 分隔符號︰分號 (;)、冒號 (:)、逗號 (,)、直立線符號 (|)

範例：
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>模式自訂 URI (選用)
- 資料類型 = 字串
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> 附註
> - 使用指派給自訂設定檔的相同*名稱*
> - 可能的值︰*GLOBAL*、*WHITELIST*、*BLACKLIST*
> - 若未提供 PackageList，則預設為 *GLOBAL* (與全系統設定檔回溯相容)
> - 若提供 PackageList，則預設為 *WHITELIST*




