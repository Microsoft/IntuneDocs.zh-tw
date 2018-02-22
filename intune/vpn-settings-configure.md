---
title: "如何設定 Intune VPN 設定"
titleSuffix: Azure portal
description: "了解如何使用 Intune 在您管理的裝置上設定 VPN 連線。"
keywords: 
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 1/25/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 772b7f025adc7ae80d0f14c5c630209c4c7529b2
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-configure-vpn-settings-in-microsoft-intune"></a>如何在 Microsoft Intune 中設定 VPN 設定

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

虛擬私人網路 (VPN) 為您的使用者提供安全的公司網路遠端存取。 裝置使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 在 Microsoft Intune 中使用「VPN 設定檔」，將 VPN 設定指派給組織中的使用者和裝置，讓他們可以輕鬆且安全地連線到網路。

例如，假設您想要使用連線到公司網路上檔案共用所需的設定來佈建所有 iOS 裝置。 建立包含連線到公司網路所需設定的 VPN 設定檔，然後將此設定檔部署給所有使用 iOS 裝置的使用者。 使用者會在可用的網路清單中看到此 VPN 連線，而且很輕鬆就能完成連線。

## <a name="vpn-connection-types"></a>VPN 連線類型

您可使用下列連線類型，建立 VPN 設定檔︰

|連線類型|Android<br>Android for Work|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|Pulse Secure|是|是|是|是|是|是|
|Cisco (IPSec)|否|是|否|否|否|否|
|Citrix|是|是|否|否|否|是|
|F5 Edge Client|是|是|是|是|是|是|
|Dell SonicWALL Mobile Connect|是|是|是|是|是|是|
|Check Point Capsule VPN|是|是|是|是|是|是|
|Cisco AnyConnect|是|是|是|否|否|否|
|自動|否|否|否|否|否|是|
|IKEv2|否|否|否|否|否|是|
|L2TP|否|否|否|否|否|是|
|PPTP|否|否|否|否|否|是|
|自訂|否|是|是|否|否|否|


> [!IMPORTANT]
> 您必須先針對設定檔安裝適用的 VPN 應用程式，才能使用指派至裝置的 VPN 設定檔。 您可以使用[什麼是 Microsoft Intune 應用程式管理？](app-management.md)主題中的資訊，協助您使用 Intune 指派應用程式。  

了解如何使用[建立自訂 VPN 設定檔](custom-vpn-profiles-create.md)中的 URI 設定，建立自訂 VPN 設定檔。     

## <a name="create-a-device-profile-containing-vpn-settings"></a>建立內含 VPN 設定的裝置設定檔

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置設定]。
2. 在 [裝置設定] 刀鋒視窗中，選擇 [管理]  >  [設定檔]。
3. 在設定檔刀鋒視窗中，選擇 [建立設定檔]。
4. 在 [建立設定檔] 刀鋒視窗中，為 VPN 設定檔輸入 [名稱] 及 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用 VPN 設定的裝置平台。 您目前可為 VPN 裝置設定，選擇下列平台之一︰
    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 及更新版本**
    - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [VPN]。
7. 您可設定的設定值隨您選擇的平台而有所不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
    - [Android 和 Android for Work 設定](vpn-settings-android.md)
    - [iOS 設定](vpn-settings-ios.md)
    - [macOS 設定](vpn-settings-macos.md)
    - [Windows Phone 8.1 設定](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1 設定](vpn-settings-windows-8-1.md)
    - [Windows 10 設定](vpn-settings-windows-10.md) (包括 Windows Holographic for Business)
8. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。

設定檔隨即建立，並出現在 [設定檔清單] 刀鋒視窗上。
若想繼續，並將此設定檔指派給群組，請參閱[如何指派裝置設定檔](device-profile-assign.md)。


## <a name="methods-of-securing-vpn-profiles"></a>保護 VPN 設定檔的方法

VPN 設定檔可以使用來自不同製造商的多種連線類型及通訊協定。 這些連線通常透過以下兩種方法之一進行保護。

### <a name="certificates"></a>憑證

當您建立 VPN 設定檔時，請選擇先前在 Intune 中建立的 SCEP 或 PKCS 憑證設定檔。 這稱為識別憑證。 其用來針對您建立且允許使用者裝置連線的受信任憑證設定檔 (或「根憑證」) 進行驗證。 受信任的憑證會指派到可驗證 VPN 連線的電腦 (一般是 VPN 伺服器)。

如需如何在 Intune 中建立及使用憑證設定檔的詳細資訊，請參閱[如何利用 Microsoft Intune 設定憑證](certificates-configure.md)。

### <a name="user-name-and-password"></a>使用者名稱和密碼

使用者藉由提供使用者名稱和密碼向 VPN 伺服器進行驗證。
