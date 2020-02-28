---
title: 在 Microsoft Intune 中使用 Android 裝置的 VPN 設定 - Azure | Microsoft Docs
description: 查看在 Microsoft Intune 中於 Android 裝置上建立 VPN 連線的所有設定。 輸入 VPN 伺服器的連線名稱、IP 位址或 FQDN，選擇使用者的驗證方式，然後選擇 [Citrix]、[SonicWall]、[Check Point Capsule] 與 [Pulse Secure] 連線類型。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f82cc74aa2e351ee63ffba2629e9ddddb57fc76
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512512"
---
# <a name="android-device-settings-to-configure-vpn-in-intune"></a>在 Intune 中設定 VPN 的 Android 裝置設定

此文章列出並描述您可以在 Android 裝置上控制的各種不同 VPN 連線設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來建立 VPN 連線、選擇 VPN 驗證方式、選取 VPN 伺服器類型等。

身為 Intune 管理員，您可以建立 VPN 設定，並將其指派給 Android 裝置。 

若要深入了解 Intune 中的 VPN 設定檔，請參閱 [VPN 設定檔](vpn-settings-configure.md)。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](vpn-settings-configure.md#create-a-device-profile)，並選擇 [Android]  。

## <a name="base-vpn"></a>基底 VPN

- **連線名稱**：輸入此連線的名稱。 終端使用者查看其裝置的可用 VPN 連線時，使用者會看到此名稱。 例如，輸入 `Contoso VPN`。
- **IP 位址或 FQDN**：輸入裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。

  - **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 選項包括：

    - **憑證**：選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](../protect/certificates-configure.md)列出用來建立憑證設定檔的步驟。
    - **使用者名稱和密碼**：登入 VPN 伺服器時，系統會提示使用者輸入其使用者名稱和密碼。

- **連線類型**：選取 VPN 連線類型。 選項包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Access**
  - **Pulse Secure**
  - **Citrix SSO**

- **指紋** (僅限 Check Point Capsule VPN)：輸入 **Contoso Fingerprint Code** 之類的字串，以確認 VPN 伺服器是可信任的。 指紋會傳送至用戶端，讓用戶端知道可以信任具有相同指紋的任何伺服器。 如果裝置沒有指紋，則會提示使用者信任 VPN 伺服器，同時顯示指紋。 使用者可手動驗證指紋，然後選擇信任以連線。
- **輸入適用於 Citrix VPN 屬性的金鑰和值組** (僅限 Citrix)：輸入 Citrix 所提供的金鑰和值組。 這些值會設定 VPN 連線的屬性。 

  您也可以使用機碼值組來 [匯入]  逗點分隔值檔案 (.csv)。 請務必檢閱 [我的資料有標頭]  與 [機碼]  屬性。

  新增機碼值組之後，請使用 [匯出]  將您的資料備份到 .csv 檔案。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以建立適用於 [Android Enterprise](vpn-settings-android-enterprise.md)、[iOS/iPadOS](vpn-settings-ios.md)、[macOS](vpn-settings-macos.md)、[Windows 10 與更新版本](vpn-settings-windows-10.md)、[Windows 8.1](vpn-settings-windows-8-1.md) 與 [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) 裝置的 VPN 設定檔。
