---
title: 執行 Android 的裝置的 Microsoft Intune VPN 設定
titlesuffix: ''
description: 了解可用於設定執行 Android 之裝置上 VPN 連線的 Intune 設定
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6753e0232548d862b46a273f1be0105ad7f16d63
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>設定 Microsoft Intune 中執行 Android 之裝置的 VPN 設定 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

本文說明可用於設定執行 Androi 之裝置上 VPN 連線的 Intune 設定。


您可以為下列平台進行 VPN 設定：

- [Android](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

根據您選擇的設定，下列所有值並非全部都是可設定的。

## <a name="android-vpn-settings"></a>Android VPN 設定
**連線名稱** - 輸入此連線的名稱。 終端使用者瀏覽其裝置的可用 VPN 連線清單時，使用者會看到此名稱。
- **IP 位址或 FQDN** - 提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法** - 從下列方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 選取您先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資料，請參閱[如何設定憑證](certificates-configure.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **指紋** (僅限 Check Point Capsule) - 指定用以確認 VPN 伺服器可受信任的字串 (例如 "Contoso Fingerprint Code")。 指紋可以傳送至用戶端，如此用戶端才知道連線時可以信任有相同指紋的任何伺服器。 如果裝置還未設定指紋，則會在顯示指紋 (使用者手動驗證指紋，並選擇信任以進行連線) 時，提示使用者信任所要連線的 VPN 伺服器。
- **為 Citrix VPN 屬性輸入索引鍵/值組** (僅限 Citrix) - 輸入 Citrix 提供的索引鍵/值組，以設定 VPN 連線的內容。

## <a name="android-for-work-vpn-settings"></a>Android for Work VPN 設定

**連線名稱** - 輸入此連線的名稱。 終端使用者瀏覽其裝置的可用 VPN 連線清單時，使用者會看到此名稱。
- **IP 位址或 FQDN** - 提供裝置所連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法** - 從下列方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 選取您先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資料，請參閱[如何設定憑證](certificates-configure.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

