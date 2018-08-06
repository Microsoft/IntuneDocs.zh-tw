---
title: 在 Microsoft Intune 中設定 Android 裝置的 VPN 設定 | Microsoft Docs
description: 為 Android 和 Android for Work 裝置建立 VPN 組態設定檔時，請輸入連線名稱、VPN 伺服器的 IP 位址或 FQDN，選擇使用者向 VPN 伺服器進行驗證的方式，然後選擇 Citrix、SonicWall、Check Point Capsule、Pulse Secure 和 Edge 等連線類型。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f02a76def463c4ef1c3ee24b021df3185d263ecf
ms.sourcegitcommit: e4832ea81b9a707a6ad0699a18c8b3988413c283
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279316"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>在 Intune 中設定執行 Android 之裝置的 VPN 設定

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用於設定執行 Androi 之裝置上 VPN 連線的 Intune 設定。

您可以為下列平台進行 VPN 設定：

- [Android](#android-vpn-settings)
- [Android for work](#android-for-work-vpn-settings)

根據您選擇的設定，下列所有值並非全部都是可設定的。

## <a name="android-vpn-settings"></a>Android VPN 設定

- **連線名稱**：輸入此連線的名稱。 終端使用者瀏覽其裝置的可用 VPN 連線時，使用者會看到此名稱。
- **IP 位址或 FQDN**輸入裝置所連線 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。

  - **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 選項包括：

    - **憑證**：選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](certificates-configure.md)列出用來建立憑證設定檔的步驟。
    - **使用者名稱和密碼**：登入 VPN 伺服器時，系統會提示終端使用者輸入使用者名稱和密碼。

- **連線類型**︰選取 VPN 連線類型。 選項包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **指紋** (僅限 Check Point Capsule VPN)：輸入 **Contoso Fingerprint Code** 之類的字串，以確認 VPN 伺服器可受信任。 指紋可以傳送至用戶端，如此用戶端才知道連線時可以信任有相同指紋的任何伺服器。 如果裝置沒有指紋，則會提示使用者信任 VPN 伺服器，同時顯示指紋。 使用者可手動驗證指紋，然後選擇 [信任] 即可連線。
- **為 Citrix VPN 屬性輸入索引鍵/值組** (僅限 Citrix)：輸入 Citrix 提供的索引鍵/值組。 這些值會設定 VPN 連線的屬性。

## <a name="android-for-work-vpn-settings"></a>Android for Work VPN 設定

- **連線名稱**：輸入此連線的名稱。 終端使用者查看其裝置的可用 VPN 連線時，使用者會看到此名稱。
- **IP 位址或 FQDN**輸入裝置所連線 VPN 伺服器的 IP 位址或完整網域名稱 (FQDN)。 例如，輸入 **192.168.1.1** 或 **vpn.contoso.com**。

  - **驗證方法**：選擇裝置向 VPN 伺服器進行驗證的方式。 選項包括：
  
    - **憑證**：選取現有的 SCEP 或 PKCS 憑證設定檔來驗證連線。 [設定憑證](certificates-configure.md)列出用來建立憑證設定檔的步驟。
    - **使用者名稱和密碼**：登入 VPN 伺服器時，系統會提示終端使用者輸入使用者名稱和密碼。

- **連線類型**︰選取 VPN 連線類型。 選項包括：

  - **Check Point Capsule VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

## <a name="next-steps"></a>接下來的步驟
[Intune 的 VPN 設定檔](vpn-settings-configure.md)
