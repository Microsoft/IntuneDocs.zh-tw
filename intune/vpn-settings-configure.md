---
title: 在 Microsoft Intune 中建立 VPN 裝置設定檔 - Azure | Microsoft Docs
description: 針對 iOS 裝置，在 Microsoft Intune 中檢視虛擬私人網路 (VPN) 連線類型、在 Azure 入口網站中建立 VPN 裝置設定檔，以及查看以憑證或使用者名稱和密碼來保護 VPN 設定檔的選項。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cd605542a0711e27f87d68af51662fd318f3250e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184874"
---
# <a name="create-vpn-profiles-in-intune"></a>在 Intune 中建立 VPN 設定檔

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

虛擬私人網路 (VPN) 為您的使用者提供安全的公司網路遠端存取。 裝置使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 在 Microsoft Intune 中使用「VPN 設定檔」，將 VPN 設定指派給組織中的使用者和裝置，讓他們可以輕鬆且安全地連線到網路。

例如，假設您想要使用連線到公司網路上檔案共用所需的設定來佈建所有 iOS 裝置。 您需建立一個 VPN 設定檔，其中包含可連線到公司網路的設定。 接著，您需將此設定檔指派給所有具有 iOS 裝置的使用者。 這些使用者會在可用的網路清單中看到此 VPN 連線，而且很輕鬆就能建立連線。

您可以使用 Intune 自訂設定原則來建立下列平台的 VPN 設定檔：

* Android 4 及更新版本
* 執行 Windows 8.1 和更新版本的已註冊裝置
* Windows Phone 8.1 和更新版本
* 執行 Windows 10 Desktop 的已註冊裝置
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 連線類型

您可使用下列連線類型，建立 VPN 設定檔︰

|連線類型|Android<br>Android 工作設定檔|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|自動|否|否|否|否|否|是|
|Check Point Capsule VPN|是|是|是|是|是|是|
|Cisco AnyConnect|是|是|是|否|否|否|
|SonicWall Mobile Connect|是|是|是|是|是|是|
|F5 Edge Client|是|是|是|是|是|是|
|Palo Alto Networks GlobalProtect|否|是|否|否|否|是|
|Pulse Secure|是|是|是|是|是|是|
|Cisco (IPSec)|否|是|否|否|否|否|
|Citrix|是 (僅 Android)|是|否|否|否|是|
|IKEv2|否|否|否|否|否|是|
|L2TP|否|否|否|否|否|是|
|PPTP|否|否|否|否|否|是|
|Zscaler|否|是|否|否|否|否|
|自訂 VPN|否|是|是|否|否|否|

> [!IMPORTANT]
> 您必須先針對設定檔安裝適用的 VPN 應用程式，才能使用指派至裝置的 VPN 設定檔。 您可以使用[什麼是 Microsoft Intune 應用程式管理？](app-management.md)一中的資訊，協助您使用 Intune 指派應用程式。  

如需了解如何使用 URI 設定來建立自訂 VPN 設定檔，請參閱[使用自訂設定來建立設定檔](custom-settings-configure.md)。

## <a name="create-a-device-profile-containing-vpn-settings"></a>建立內含 VPN 設定的裝置設定檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [All services] (所有服務)，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置設定] > [設定檔] > [建立設定檔]。
4. 輸入 VPN 設定檔的 [名稱] 和 [描述]。
5. 從 [平台] 下拉式清單中，選取要套用 VPN 設定的裝置平台。 您目前可為 VPN 裝置設定，選擇下列平台之一︰
   - **Android**
   - **Android 企業**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 及更新版本**
   - **Windows 10 及更新版本**
6. 從 [設定檔類型] 下拉式清單中，選擇 [VPN]。
7. 您可設定的設定會視您選擇的平台而不同。 前往下列主題之一，即可取得每個平台的詳細設定︰
   - [Android 和 Android 工作設定檔設定](vpn-settings-android.md)
   - [iOS 設定](vpn-settings-ios.md)
   - [macOS 設定](vpn-settings-macos.md)
   - [Windows Phone 8.1 設定](vpn-settings-windows-phone-8-1.md)
   - [Windows 8.1 設定](vpn-settings-windows-8-1.md)
   - [Windows 10 設定](vpn-settings-windows-10.md) (包括 Windows Holographic for Business)
8. 完成時，[建立] 您的設定檔

設定檔隨即建立，並出現在設定檔清單上。 若要將此設定檔指派給群組，請參閱[指派裝置設定檔](device-profile-assign.md)。

## <a name="methods-of-securing-vpn-profiles"></a>保護 VPN 設定檔的方法

VPN 設定檔可以使用來自不同製造商的多種連線類型及通訊協定。 這些連線通常透過以下兩種方法之一進行保護。

### <a name="certificates"></a>憑證

當您建立 VPN 設定檔時，請選擇先前在 Intune 中建立的 SCEP 或 PKCS 憑證設定檔。 這個設定檔稱為識別憑證。 此憑證可用來針對您為允許使用者裝置進行連線而建立的受信任憑證設定檔 (或「根憑證」) 進行驗證。 受信任的憑證會指派到可驗證 VPN 連線的電腦 (一般是 VPN 伺服器)。

如需如何在 Intune 中建立及使用憑證設定檔的詳細資訊，請參閱[如何利用 Microsoft Intune 設定憑證](certificates-configure.md)。

### <a name="user-name-and-password"></a>使用者名稱和密碼

使用者藉由提供使用者名稱和密碼向 VPN 伺服器進行驗證。
