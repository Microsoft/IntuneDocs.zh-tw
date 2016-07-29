---
title: "VPN 設定檔的自訂組態 | Microsoft Intune"
description: "在 Intune 中使用自訂組態來建立 VPN 設定檔。"
keywords: 
author: Nbigman
manager: angrobe
ms.date: 07/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9a124663a80bb477d0312faa0fb43e4457ba8246
ms.openlocfilehash: ae5ac5c697195f8b45f500cfa9d0de24953f8cb0


---

# VPN 設定檔的自訂組態

## 建立自訂組態
您可以在 Intune 中使用自訂組態來建立 VPN 設定檔。 若要建立自訂組態：

   1. 在 Intune 管理主控台中，**[原則]** -> **[新增原則]** -> *<Expand platform>* -> **[自訂設定]** -> **[建立原則]**。
   2. 提供原則的名稱。
   3. 針對每個 URI 設定，按一下 [新增] 並提供必要資訊。 範例如下：

   ![VPN 設定檔自訂組態對話方塊](./media/Intune_Add_VPN_URI.png)

   4.  輸入所有 URI 設定後，請按一下 [儲存原則] 再部署原則。

## 部署組態原則

1.  在 [原則]  工作區中，選取您要部署的原則，然後按一下 [管理部署] 。

2.  在 [管理部署]  對話方塊中：

    -   **部署原則** - 選取您要部署原則的一或多個群組，然後按一下 [新增] &gt; [確定]。

    -   **關閉對話方塊但不加以部署** - 按一下 [取消]。

當您選取某項已部署的原則時，您可以在原則清單下方檢視有關部署的進一步資訊。

##自訂的 VPN 設定檔組態的 URI 設定範例
以下是 URI 值項目範例，可為稱為 Contoso 的虛構公司中的 VPN 建立自訂組態。 如需詳細資訊，例如每個項目的資料類型，請參閱 [VPNv2 CSP](https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776.aspx)

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

若對這些設定的使用方式有任何疑問，或想更詳細了解它們的功用，客戶應參考 CSP 說明文件︰https://msdn.microsoft.com/en-us/library/windows/hardware/dn914776(v=vs.85).aspx

## 適用於 PulseSecure 上 Android 個別應用程式 VPN 的 URI 設定
### 封裝清單的自訂 URI
-  資料類型 = 字串
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/<Name>/PackageList
-  值 = 分隔符號分隔的封裝清單。
   - 分隔符號︰分號 (;)、冒號 (:)、逗號 (,)、直立線符號 (|)

範例：
- com.android.chrome
- com.android.chrome;com.android.browser

### 模式自訂 URI (選用)
- 資料類型 = 字串
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> 附註
> - 使用指派給自訂設定檔的相同*名稱*
> - 可能的值︰*GLOBAL*、*WHITELIST*、*BLACKLIST*
> - 若未提供 PackageList，則預設為 *GLOBAL* (與全系統設定檔回溯相容)
> - 若提供 PackageList，則預設為 *WHITELIST*


### 請參閱
(Microsoft Intune 中的 VPN 連線)[vpn-connections-in-microsoft-intune.md]



<!--HONumber=Jul16_HO4-->


