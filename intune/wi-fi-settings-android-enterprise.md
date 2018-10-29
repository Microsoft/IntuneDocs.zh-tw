---
title: 設定 Android 企業和 kioisk 裝置的 Wi-Fi 設定 - Microsoft Intune - Azure | Microsoft Docs
titleSuffix: ''
description: 建立或新增適用於 Android 企業和 Android Kiosk 的 WiFi 裝置組態設定檔。 請查看不同的設定，包括在 Microsoft Intune 中新增憑證、選擇 EAP 類型，以及選取驗證方法。 針對 Kiosk 裝置，也請輸入您網路的預先共用金鑰。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c2983f2f7b7079f73c857bf7caafe4236373c5dc
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2018
ms.locfileid: "49431914"
---
# <a name="add-wi-fi-settings-for-devices-running-android-enterprise-and-android-kiosk-in-microsoft-intune"></a>在 Microsoft Intune 中新增適用於執行 Android 企業和 Android kiosk 之裝置的 Wi-Fi 設定

您可以建立含有特定 WiFi 設定的設定檔，然後將此設定檔部署到您的 Android 企業與 Android kiosk 裝置。 Microsoft Intune 提供許多功能，包括驗證您的網路、使用預先共用金鑰等等。

本文說明了這些設定。

## <a name="before-you-begin"></a>開始之前

[建立裝置設定檔](device-profile-create.md)。

## <a name="device-owner-only---kiosk"></a>僅限裝置擁有者 - kiosk

如果使用 Android 企業裝置作為 kiosk，請選取此選項。

- **網路名稱**：輸入此 Wi-Fi 連線的名稱。 此值是使用者瀏覽裝置上的可用連線清單時所見到的名稱。
- **SSID**：[服務組識別元] (service set identifier) 的縮寫。 此設定是裝置要連線之無線網路的實際名稱。 但當使用者選擇此連線時，只會看到您設定的 [網路名稱]。
- **自動連線**：選擇 [啟用] 可讓裝置在位於網路連線範圍內時自動連線到此網路。 選擇 [停用] 可防止裝置自動連線。
- **隱藏的網路**：選擇 [啟用] 可在裝置的可用網路清單中隱藏此網路。 不會廣播 SSID。 選擇 [停用] 可在裝置的可用網路清單中顯示此網路。
- **Wi-Fi 類型**：選取向 Wi-Fi 網路驗證時要使用的安全性通訊協定。 選項包括：

  - **開放 (無驗證)**：只有在網路不安全時才使用此選項。
  - **WEP 預先共用金鑰**：在 [預先共用金鑰] 中輸入密碼。 當您的組織建置或設定網路時，也會設定密碼或網路金鑰。 請輸入此密碼或網路金鑰作為 PSK 值。
  - **WEP 預先共用金鑰**：在 [預先共用金鑰] 中輸入密碼。 當您的組織建置或設定網路時，也會設定密碼或網路金鑰。 請輸入此密碼或網路金鑰作為 PSK 值。

按一下 [確定] 以儲存您的變更。

## <a name="work-profile-only"></a>僅限工作設定檔

### <a name="basic-settings"></a>基本設定

- **Wi-Fi 類型**：選擇 [基本]。
- **SSID**：[服務組識別元] (service set identifier) 的縮寫。 此設定是裝置要連線之無線網路的實際名稱。
- **自動連線**：選擇 [啟用] 可讓裝置在位於網路連線範圍內時自動連線到此網路。 選擇 [停用] 可防止裝置自動連線。
- **隱藏的網路**：選擇 [啟用] 可在裝置的可用網路清單中隱藏此網路。 不會廣播 SSID。 選擇 [停用] 可在裝置的可用網路清單中顯示此網路。

## <a name="enterprise-profile"></a>企業設定檔

- **Wi-Fi 類型**：選擇 [企業]。
- **SSID**：[服務組識別元] (service set identifier) 的縮寫。 此設定是裝置要連線之無線網路的實際名稱。
- **自動連線**：選擇 [啟用] 可讓裝置在位於網路連線範圍內時自動連線到此網路。 選擇 [停用] 可防止裝置自動連線。
- **隱藏的網路**：選擇 [啟用] 可在裝置的可用網路清單中隱藏此網路。 不會廣播 SSID。 選擇 [停用] 可在裝置的可用網路清單中顯示此網路。
- **EAP 類型**：選擇用來驗證安全無線連線的可延伸驗證通訊協定 (EAP) 類型。 選項包括： 

  - **EAP-TLS**：另請輸入：

    - **伺服器信任** - **伺服器驗證的根憑證**：選擇現有受信任的根憑證設定檔。 當用戶端連線到網路時，會向伺服器提供此憑證，並用來驗證連線。

      按一下 [確定] 以儲存您的變更。

    - **用戶端驗證** - **用戶端驗證的用戶端憑證 (身分識別憑證)**：選擇 也會部署到裝置的 SCEP 或 PKCS 用戶端憑證設定檔。 此憑證是裝置提供給伺服器以驗證連線的身分識別。

      按一下 [確定] 以儲存您的變更。

  - **EAP-TTLS**：另請輸入：

    - **伺服器信任** - **伺服器驗證的根憑證**：選擇現有受信任的根憑證設定檔。 當用戶端連線到網路時，會向伺服器提供此憑證，並用來驗證連線。

      按一下 [確定] 以儲存您的變更。

    - **用戶端驗證** - 選擇 [驗證方法]。 選項包括：

      - **使用者名稱和密碼**：提示使用者輸入使用者名稱和密碼以驗證連線。 另請輸入：
        - **非 EAP 方法 (內部識別)**：選擇驗證連線的方式。 請務必選擇與您的 Wi-Fi 網路設定相同的通訊協定。

          選項包括：[未加密的密碼 (PAP)]、[Challenge Handshake 驗證通訊協定 (CHAP)]、[Microsoft CHAP (MS-CHAP)]，或 [Microsoft CHAP 第 2 版 (MS-CHAP v2)]

      - **憑證**：選擇也會部署到裝置的 SCEP 或 PKCS 用戶端憑證設定檔。 此憑證是裝置提供給伺服器以驗證連線的身分識別。

        按一下 [確定] 以儲存您的變更。

      - **識別隱私權 (外部識別)**：指定回應 EAP 識別要求時所要傳送的文字。 此文字可以是任何值，例如 `anonymous`。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。

  - **PEAP**：另請輸入：

    - **伺服器信任** - **伺服器驗證的根憑證**：選擇現有受信任的根憑證設定檔。 當用戶端連線到網路時，會向伺服器提供此憑證，並用來驗證連線。

      按一下 [確定] 以儲存您的變更。

    - **用戶端驗證** - 選擇 [驗證方法]。 選項包括：

      - **使用者名稱和密碼**：提示使用者輸入使用者名稱和密碼以驗證連線。 另請輸入：
        - **非 EAP 驗證方法 (內部識別)**：選擇驗證連線的方式。 請務必選擇與您的 Wi-Fi 網路設定相同的通訊協定。

          選項包括： [無] 或 [Microsoft CHAP 第 2 版 (MS-CHAP v2)]

      - **憑證**：選擇也會部署到裝置的 SCEP 或 PKCS 用戶端憑證設定檔。 此憑證是裝置提供給伺服器以驗證連線的身分識別。

        按一下 [確定] 以儲存您的變更。

      - **識別隱私權 (外部識別)**：指定回應 EAP 識別要求時所要傳送的文字。 此文字可以是任何值，例如 `anonymous`。 在驗證期間，一開始會先傳送此匿名識別，隨後以安全通道傳送真正的識別。

選取 [確定] > [建立] 儲存您的變更。 設定檔隨即建立，並顯示在設定檔清單中。

## <a name="next-steps"></a>接下來的步驟

設定檔已建立，但它不會執行任何動作。 接下來，請[指派此設定檔](device-profile-assign.md)。

## <a name="more-resources"></a>其他資源

- 請參閱[W執行 Android 之裝置的 Wi-Fi 設定](wi-fi-settings-android.md)，以了解可供 Android 裝置使用的設定。
- [Wi-Fi 設定概觀](wi-fi-settings-configure.md)，包括其他平台。