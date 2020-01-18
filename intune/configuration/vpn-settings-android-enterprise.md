---
title: 在 Microsoft Intune 中使用 Android Enterprise 的 VPN 設定 - Azure | Microsoft Docs
description: 在 Microsoft Intune 中，查看在 Android Enterprise 裝置上建立 VPN 連線的所有設定。 輸入 VPN 伺服器的 [連線名稱]、[IP 位址] 或 [FQDN]，選擇使用者的驗證方式，然後選擇 [Citrix]、[SonicWall]、[檢查點膠囊] 和 [脈衝安全連線類型]。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a0c11be374e36ec32feb9540f6cfd4f1bc794e9c
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206307"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>在 Intune 中設定 VPN 的 Android 企業裝置設定



此文章列出並描述您可以在 Android Enterprise 裝置上控制的各種不同 VPN 連線設定。 作為行動裝置管理（MDM）解決方案的一部分，請使用這些設定來建立 VPN 連線、選擇 VPN 的驗證方式、選取 VPN 伺服器類型等等。

Intune 管理員可以建立 VPN 設定，並將其指派給 Android Enterprise 裝置。 

若要深入瞭解 Intune 中的 VPN 設定檔，請參閱[vpn 設定檔](vpn-settings-configure.md)。

> [!NOTE]
> 若要設定「永遠開啟」 VPN，您需要建立 VPN 設定檔，並使用已設定的「永遠開啟」 VPN 設定來建立[裝置限制](device-restrictions-android-for-work.md#connectivity)設定檔。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](vpn-settings-configure.md#create-a-device-profile)，並選擇 [Android Enterprise]  。

## <a name="device-owner-only"></a>僅限裝置擁有者

- **連線名稱**：輸入此連線的名稱。 終端使用者查看其裝置的可用 VPN 連線時，使用者會看到此名稱。 例如，輸入 `Contoso VPN`。
- **IP 位址或 FQDN**：輸入裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。

  - **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 選項包括：
  
    - **憑證**：選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](../protect/certificates-configure.md)列出用來建立憑證設定檔的步驟。
    - **使用者名稱和密碼**：登入 VPN 伺服器時，系統會提示使用者輸入其使用者名稱和密碼。

- **連線類型**：選取 VPN 連線類型。 選項包括：

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>僅限工作設定檔

- **連線名稱**：輸入此連線的名稱。 終端使用者查看其裝置的可用 VPN 連線時，使用者會看到此名稱。 例如，輸入 `Contoso VPN`。
- **IP 位址或 FQDN**：輸入裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。

  - **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 選項包括：
  
    - **憑證**：選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](../protect/certificates-configure.md)列出用來建立憑證設定檔的步驟。
    - **使用者名稱和密碼**：登入 VPN 伺服器時，系統會提示使用者輸入其使用者名稱和密碼。

- **連線類型**：選取 VPN 連線類型。 選項包括：

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **Check Point Capsule VPN**

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以建立適用于[Android](vpn-settings-android.md)、 [iOS](vpn-settings-ios.md)、 [macOS](vpn-settings-macos.md)、 [Windows 10 和更新版本](vpn-settings-windows-10.md)、 [Windows 8.1](vpn-settings-windows-8-1.md)和[Windows Phone 8.1](vpn-settings-windows-phone-8-1.md)裝置的 VPN 設定檔。
