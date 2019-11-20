---
title: 在 Microsoft Intune 中將 VPN 設定新增至裝置 - Azure | Microsoft Docs
description: 針對 Android、Android Enterprise、iOS、macOS 與 Windows 裝置，請使用內建設定來建立 Microsoft Intune 中的虛擬私人網路 (VPN) 連線。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59a1b5679b81a8de90e39d6ec13bbe87dac90947
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984177"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>在 Intune 中建立 VPN 設定檔以連線到 VPN 伺服器

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

虛擬私人網路 (VPN) 為您的使用者提供安全的組織網路遠端存取。 裝置會使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 Microsoft Intune 中的 **VPN 設定檔**會將 VPN 設定指派給組織中的使用者與裝置，讓他們可以輕鬆且安全地連線到組織網路。

例如，您想要使用連線到組織網路上檔案共用所需的設定，來設定所有 iOS 裝置。 您會建立包含這些設定的 VPN 設定檔。 接著，您需將此設定檔指派給所有擁有 iOS 裝置的使用者。 這些使用者會在可用的網路清單中看到此 VPN 連線，而且很輕鬆就能建立連線。

> [!NOTE]
> 您可以使用 [Intune 自訂設定原則](custom-settings-configure.md)來建立下列平台的 VPN 設定檔：
>
> * Android 4 及更新版本
> * 執行 Windows 8.1 和更新版本的已註冊裝置
> * Windows Phone 8.1 和更新版本
> * 執行 Windows 10 Desktop 的已註冊裝置
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 連線類型

您可使用下列連線類型，建立 VPN 設定檔︰

|連線類型|平台|
|-|-|
|自動|Windows 10|
|Check Point Capsule VPN|- Android<br/>- Android Enterprise 工作設定檔<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Android Enterprise 工作設定檔<br/>- Android Enterprise 裝置擁有者 (完全受控)<br/>- iOS<br/>- macOS|
|Cisco (IPSec)|iOS|
|Citrix SSO|- Android<br/>- Android Enterprise 工作設定檔：使用[應用程式設定原則](../apps/app-configuration-policies-use-android.md)<br/>- Android Enterprise 裝置擁有者 (完全受控)：使用[應用程式設定原則](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|自訂 VPN|- iOS<br/>- macOS|
|F5 Access|- Android<br/>- Android Enterprise 工作設定檔<br/>- Android Enterprise 裝置擁有者 (完全受控)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Android Enterprise 工作設定檔：使用[應用程式設定原則](../apps/app-configuration-policies-use-android.md)<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Android Enterprise 工作設定檔<br/>- Android Enterprise 裝置擁有者 (完全受控)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Android Enterprise 工作設定檔<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Android Enterprise 工作設定檔：使用[應用程式設定原則](../apps/app-configuration-policies-use-android.md)<br/>- iOS|

> [!IMPORTANT]
> 您必須先針對設定檔安裝適用的 VPN 應用程式，才能使用指派至裝置的 VPN 設定檔。 您可以使用[什麼是 Microsoft Intune 應用程式管理？](../apps/app-management.md)一中的資訊，協助您使用 Intune 指派應用程式。  

如需了解如何使用 URI 設定來建立自訂 VPN 設定檔，請參閱[使用自訂設定來建立設定檔](custom-settings-configure.md)。

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 登入 [Microsoft Endpoint Manager 系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [裝置]   > [組態設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：為設定檔輸入描述性名稱。 命名您的設定檔，以方便之後能輕鬆識別。 例如，良好的設定檔名稱為**適用於整家公司的 VPN 設定檔**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選擇您的裝置平台。 選項包括：

      - **Android**
      - **Android Enterprise** > **僅限裝置擁有者**
      - **Android Enterprise** > **僅限工作設定檔**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 及更新版本**
      - **Windows 10 及更新版本**

    - **設定檔類型**：選取 [VPN]  。

4. 您可設定的設定會視您選擇的平台而不同。 如需每個平台的詳細設定，請參閱下列文章：

    - [Android 設定](vpn-settings-android.md)
    - [Android 企業設定](vpn-settings-android-enterprise.md)
    - [iOS/iPadOS 設定](vpn-settings-ios.md)
    - [macOS 設定](vpn-settings-macos.md)
    - [Windows Phone 8.1 設定](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1 設定](vpn-settings-windows-8-1.md)
    - [Windows 10 設定](vpn-settings-windows-10.md) (包括 Windows Holographic for Business)

5. 當您完成時，請選取 [確定]   > [建立]  儲存變更。

設定檔隨即建立，並出現在設定檔清單上。 若要將此設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。

## <a name="secure-your-vpn-profiles"></a>保護您的 VPN 設定檔

VPN 設定檔可以使用來自不同製造商的多種連線類型及通訊協定。 這些連線通常會透過以下方法來保護。

### <a name="certificates"></a>憑證

當您建立 VPN 設定檔時，請選擇先前在 Intune 中建立的 SCEP 或 PKCS 憑證設定檔。 這個設定檔稱為識別憑證。 此憑證可用來針對您為允許使用者裝置進行連線而建立的受信任憑證設定檔 (或「根憑證」  ) 進行驗證。 受信任的憑證會指派到可驗證 VPN 連線的電腦 (一般是 VPN 伺服器)。

如需如何在 Intune 中建立及使用憑證設定檔的詳細資訊，請參閱[如何利用 Microsoft Intune 設定憑證](../protect/certificates-configure.md)。

### <a name="user-name-and-password"></a>使用者名稱和密碼

使用者藉由提供使用者名稱和密碼向 VPN 伺服器進行驗證。

## <a name="next-steps"></a>後續步驟

一旦設定檔建立完成，它還不會執行任何動作。 接下來，[指派設定檔](device-profile-assign.md)給一些裝置。

您也可以在 [Android](android-pulse-secure-per-app-vpn.md) 與 [iOS](vpn-setting-configure-per-app.md) 裝置上，建立及使用個別應用程式 VPN。
