---
title: "Android 裝置的 Intune VPN 設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解您可用於設定 Android 裝置之 VPN 連線的 Intune 設定。"
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 16c056ca-320e-4107-ad03-a0cf96c28885
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 8c8690b191c7358c8fd60c241177aca1372a8f54
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="vpn-settings-for-android-devices-in-microsoft-intune"></a>Microsoft Intune 中 Android 裝置的 VPN 設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

下列清單中所列的值並非全部都能設定，須取決於您選擇的設定。

**連線名稱** - 輸入此連線的名稱。 當使用者瀏覽其裝置尋找可用 VPN 連線的清單時，使用者會看到此名稱。
- **IP 位或 FQDN** - 提供裝置要連線之 VPN 伺服器的 IP 位址或完整網域名稱。 範例：**192.168.1.1**、**vpn.contoso.com**。
- **驗證方法** - 從下列各方式中選擇裝置對 VPN 伺服器的驗證方式︰
    - **憑證** - 選取您先前建立用於驗證連線的 SCEP 或 PKCS 憑證設定檔。 如需憑證設定檔的詳細資訊，請參閱[如何設定憑證](certificates-configure.md)。
    - **使用者名稱與密碼** - 使用者必須提供使用者名稱及密碼才能登入 VPN 伺服器。
- **連線類型** - 從下列廠商清單中選取 VPN 連線類型︰
    - **Check Point Capsule VPN**
    - **Cisco AnyConnect**
    - **Dell SonicWALL Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **指紋** (僅限 Check Point Capsule) - 指定用以確認 VPN 伺服器可茲信任的字串 (例如 "Contoso Fingerprint Code")。 指紋可以傳送至用戶端，如此用戶端才知道連線時可以信任有相同指紋的任何伺服器。 若裝置還未設定指紋，會在顯示指紋 (使用者手動驗證指紋，並選擇 [信任] 進行連線) 時，提示使用者信任所要連線的 VPN 伺服器。
- **為 Citrix VPN 屬性輸入索引鍵/值組** (僅限 Citrix) - 輸入 Citrix 提供的索引鍵/值組，以設定 VPN 連線的內容。

