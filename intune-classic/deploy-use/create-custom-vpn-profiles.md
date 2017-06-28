---
title: "Microsoft Intune VPN 設定檔的自訂設定"
description: "在 Intune 中使用自訂組態來建立 VPN 設定檔。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 2ee20ce0b9f7794132c3a56046b1680f940b3424
ms.contentlocale: zh-tw
ms.lasthandoff: 06/08/2017


---

# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Microsoft Intune VPN 設定檔的自訂設定

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>建立自訂設定
您可以使用 Intune 自訂設定原則來建立下列各項的 VPN 設定檔：

* 執行 Android 4 和更新版本的裝置
* Android for Work 裝置
* 執行 Windows 8.1 和更新版本的已註冊裝置
* 執行 Windows Phone 8.1 和更新版本的裝置
* 執行 Windows 10 Desktop 的已註冊裝置
* 執行 Windows 10 行動裝置版的裝置

標準 Intune VPN 原則未包含您想要使用的設定時，此類型的原則十分有用。

## <a name="to-create-a-custom-configuration-policy"></a>建立自訂設定原則：

   1. 在 [Intune 管理主控台](https://manage.microsoft.com)中，選擇 [原則] > [新增原則] > [擴充平台] > [自訂設定] > [建立原則]。
   2. 輸入原則的名稱。
   3. 針對您想要指定的每個 URI 設定選擇 [新增]，並提供要求的資訊。 範例如下：

   ![VPN 設定檔自訂設定對話方塊](./media/Intune_Add_VPN_URI.png)

   4.  輸入所有 URI 設定後，請選擇 [儲存原則]，然後部署原則。

然後，一如以往[部署原則](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)。

## <a name="example-uri-settings"></a>範例 URI 設定

這些設定可以用來為稱為 Contoso 的虛構公司中的 VPN 建立自訂設定。
如需您可使用之所有設定的完整詳細資訊，請參閱 [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx)。

**原生 Contoso VPN (IKEv2)：**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
   <EapMethod>
      <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
      <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
      <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
      <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
   </EapMethod>
   <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
      <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
         <Type>13</Type>
         <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
            <CredentialsSource>
               <CertificateStore>
                  <SimpleCertSelection>true</SimpleCertSelection>
               </CertificateStore>
            </CredentialsSource>
            <ServerValidation>
               <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
               <ServerNames></ServerNames>
            </ServerValidation>
            <DifferentUsername>false</DifferentUsername>
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

若對這些設定的使用方式有任何疑問，或想更詳細了解這些設定的功能，客戶應參考閱[設定服務提供者 (CSP) 文件 (英文)](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx)。

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


### <a name="see-also"></a>另請參閱
[Microsoft Intune 中的 VPN 連線](vpn-connections-in-microsoft-intune.md)

