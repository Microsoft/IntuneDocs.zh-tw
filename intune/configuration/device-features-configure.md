---
title: 使用 Microsoft Intune 建立 iOS 或 macOS 裝置設定檔 - Azure | Micrososft Docs
description: 新增或建立 iOS 或 macOS 裝置設定檔，然後在 Microsoft Intune 中設定 AirPrint 的設定、主畫面配置、應用程式通知、共用裝置、單一登入，以及網路內容篩選器設定。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 83328652c366eea6e1a3cbb81ea4979d8844a96b
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71724187"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>在 Intune 中新增 iOS 或 macOS 裝置功能設定

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 包含許多可協助系統管理員控制 iOS 和 macOS 裝置的功能和設定。 例如，系統管理員可以：

- 允許使用者存取您網路中的 AirPrint 印表機
- 將應用程式與資料夾新增至主畫面，包括新增頁面
- 選擇是否要顯示應用程式通知及如何顯示
- 設定鎖定畫面以顯示一則訊息或資產標記，特別適用於共用裝置
- 為使用者提供在應用程式之間共用認證的安全單一登入體驗
- 篩選使用成人內容語言的網站，並允許或封鎖特定網站

Intune 會使用「組態設定檔」來依據貴組織的需求建立和自訂這些設定。 在設定檔中新增這些功能之後，接著將該設定檔推送或部署至組織中的 iOS 和 macOS 裝置。

本文描述您可以設定的各種功能，並示範如何建立裝置組態設定檔。 您也可以查看適用於 [iOS](ios-device-features-settings.md) 和 [macOS](macos-device-features-settings.md) 裝置的所有可用設定。

## <a name="airprint"></a>AirPrint

AirPrint 是可讓裝置透過無線網路列印到檔案的 Apple 功能。 在 Intune 中，您可以將 AirPrint 資訊新增至裝置。

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的 AirPrint](ios-device-features-settings.md#airprint) 和 [macOS 上的 AirPrint](macos-device-features-settings.md#airprint)。

如需 AirPrint 的詳細資訊，請參閱 Apple 網站上的[關於 AirPrint](https://support.apple.com/HT201311)。

適用於：

- iOS 7.0 和更新版本
- iPadOS 13.0 和更新版本
- macOS 10.10 和更新版本

## <a name="app-notifications"></a>應用程式通知

選擇 iOS 和 iPad 裝置上的應用程式接收通知的方式。 例如，從 Intune 傳送應用程式通知，以使其顯示於通知中心、顯示於鎖定畫面上或播放音效。

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的應用程式通知](ios-device-features-settings.md#app-notifications)。

如需此功能的詳細資訊，請參閱 Apple 網站上的[通知](https://developer.apple.com/notifications/) \(英文\)。

適用於：

- iOS 9.3 與更新版本
- iPadOS 13.0 和更新版本

## <a name="associated-domains"></a>相關網域

相關網域可讓您在網域 (例如 `contoso.com`) 和您的應用程式之間建立關聯性。 此功能可讓您：

- 在組織中的應用程式與網站之間共用資料和登入認證。
- 使用以您的網站為基礎的應用程式功能，例如，單一登入應用程式擴充功能、通用連結，以及自動填滿密碼。

  例如，建立相關網域以允許自動填滿密碼為與您應用程式相關聯的網站建議認證 (例如密碼)。

如需可在 Intune 中設定的設定清單，請參閱 [macOS 上的相關網域](macos-device-features-settings.md#associated-domains)。

如需此功能的詳細資訊，請參閱 Apple 網站上的[設定應用程式的相關網域](https://developer.apple.com/documentation/security/password_autofill/setting_up_an_app_s_associated_domains) \(英文\)。

適用於：

- macOS 10.15 與更新版本

## <a name="home-screen-layout"></a>主畫面配置

這些設定會在 iOS 和 iPadOS 裝置的 Dock 和主畫面上設定應用程式配置和資料夾。 您可以：

- 使用 **Dock** 設定來將應用程式或資料夾新增至畫面。 例如，在裝置 Dock 上顯示 [Safari] 和 [郵件] 應用程式。
- 新增您想要顯示於主畫面上的**頁面**，以及要顯示於每個頁面上的應用程式。 例如，新增 [Contoso]  頁面，然後在此頁面上新增 [設定] 應用程式。

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的主畫面配置](ios-device-features-settings.md#home-screen-layout)。

適用於：

- iOS 9.3 與更新版本
- iPadOS 13.0 和更新版本

## <a name="lock-screen-message"></a>鎖定畫面訊息

使用這些設定以在登入視窗和鎖定畫面上顯示自訂訊息或文字。 例如，您可以輸入「若遺失，請送回...」訊息，並顯示資產標籤資訊。

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的鎖定畫面訊息設定](ios-device-features-settings.md#lock-screen-message)。

如需鎖定畫面訊息的詳細資訊，請參閱 Apple 網站上的 [LockScreenMessage](https://developer.apple.com/documentation/devicemanagement/lockscreenmessage) \(英文\)。

適用於：

- iOS 9.3 與更新版本
- iPadOS 13.0 和更新版本

## <a name="login-items"></a>登入項目

使用此功能，來選擇使用者登入裝置時所開啟的應用程式、自訂應用程式、檔案和資料夾。 

如需可在 Intune 中設定的設定清單，請參閱 [macOS 上的登入項目](macos-device-features-settings.md#login-items)。

適用於：

- macOS 10.13 與更新版本

## <a name="login-window"></a>登入視窗

控制登入畫面的外觀，以及使用者在登入之前可使用的功能。 例如，新增具有自訂訊息的橫幅，選擇是否要顯示 [睡眠] 按鈕，以及其他功能。

如需可在 Intune 中設定的設定清單，請參閱 [macOS 上的登入視窗](macos-device-features-settings.md#login-window)。

適用於：

- macOS 10.7 和更新版本

## <a name="single-sign-on"></a>單一登入

大部分的企業營運 (LOB) 應用程式需要某種程度的使用者驗證才會支援安全性。 在許多情況下，驗證都會要求使用者重複輸入相同認證。 為了改善使用者體驗，開發人員可以建立使用單一登入 (SSO) 的應用程式。 使用單一登入可減少使用者必須輸入認證的次數。

若要使用單一登入，請確定您已具備：

- 已將程式碼撰寫成會在裝置上的單一登入中尋找使用者認證存放區的應用程式。
- 設定進行 iOS 裝置單一登入的 Intune。

![單一登入窗格](./media/device-features-configure/sso-blade.png)

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的單一登入](ios-device-features-settings.md#single-sign-on)。

適用於：

- iOS 7.0 和更新版本
- iPadOS 13.0 和更新版本

## <a name="single-sign-on-app-extension"></a>單一登入應用程式擴充功能

這些設定會設定應用程式擴充功能，以便為您的 iOS、iPadOS 和 macOS 裝置啟用單一登入 (SSO)。 大部分的企業營運 (LOB) 應用程式和組織網站都需要某種程度的安全使用者驗證。 在許多情況下，驗證都會要求使用者重複輸入相同認證。 SSO 讓使用者在輸入其認證一次之後，就能存取應用程式和網站。 當使用者登入之後，即可自動存取應用程式和網站，或使用 Face ID、Touch ID 或 Apple 密碼來獲得存取權。

在 Intune 中，使用這些設定來設定 Apple 的內建 Kerberos 擴充功能，或設定組織所建立的 SSO 應用程式擴充功能。 SSO 應用程式擴充功能會為您的使用者處理驗證。 這些設定會設定認證類型的 SSO 應用程式擴充功能，這些擴充功能是針對挑戰和回應驗證流程所設計的。 您可以在 Apple 所提供的 Kerberos 特定認證擴充功能和一般認證擴充功能之間進行選擇。

如需可在 Intune 中設定的設定清單，請參閱 [iOS SSO 應用程式擴充功能](ios-device-features-settings.md#single-sign-on-app-extension)和 [macOS SSO 應用程式擴充功能](macos-device-features-settings.md#single-sign-on-app-extension)。

如需開發 SSO 應用程式擴充功能的詳細資訊，請觀賞 Apple 網站上的[可擴充的企業 SSO](https://developer.apple.com/videos/play/tech-talks/301) \(英文\)。

> [!NOTE]
> **單一登入應用程式擴充功能**與**單一登入**功能不同：
>
> - **單一登入應用程式擴充功能**設定適用於 iPadOS 13.0 (和更新版本) 及 iOS 13.0 (和更新版本)。 **單一登入**設定適用於 iPadOS 13.0 (和更新版本) 及 iOS 7.0 和更新版本。
> - **單一登入應用程式擴充功能**會處理作業系統的驗證。 在**單一登入**中，特定的應用程式會處理驗證。
> - 使用**單一登入應用程式擴充功能**時，使用者會以無訊息模式登入應用程式和網站，或是使用 Face ID、Touch ID，或是 Apple 的 PIN 碼或密碼來登入。 使用**單一登入**時，使用者會使用其他應用程式來登入應用程式和網站。
>
>    **單一登入應用程式擴充功能**會使用 Apple 作業系統進行驗證。 因此，它可能會提供更好的使用者體驗。
>
> - 從開發觀點來看，**單一登入應用程式擴充功能**可以使用任何類型的認證 SSO 驗證。 使用**單一登入**，您只能使用 Kerberos SSO 驗證。  

適用於：

- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本
- macOS 10.15 與更新版本

## <a name="wallpaper"></a>桌布

將自訂的 .png、.jpg 或 .jpeg 影像新增至您的受監督 iOS 裝置。 例如，使用 Intune 來將公司標誌新增至裝置上的鎖定畫面。

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的背景圖案](ios-device-features-settings.md#wallpaper)。

適用於：

- iOS
- iPadOS 13.0 和更新版本

## <a name="web-content-filter"></a>Web 內容篩選

這些設定可以使用 Apple 的內建自動篩選演算法來評估網頁，並封鎖成人內容和成人語言。 您也可以建立已允許的網頁連結及受限制之網頁連結的清單。 例如，您可以允許僅開啟 `contoso` 網站。

如需可在 Intune 中設定的設定清單，請參閱 [iOS 上的內容篩選](ios-device-features-settings.md#web-content-filter)。

適用於：

- iOS 7.0 和更新版本
- iPadOS 13.0 和更新版本

## <a name="create-a-device-profile"></a>建立裝置設定檔

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [裝置設定]   > [設定檔]   > [建立設定檔]  。
3. 輸入下列內容：

    - **名稱**：輸入政策的描述性名稱。 為您的設定檔命名，以方便之後能夠輕鬆識別。 例如，良好的原則名稱是 **macOS：設定登入畫面**。
    - **描述**：輸入設定檔的描述。 這是選擇性設定，但建議執行。
    - **平台**：選擇您的裝置平台。 選項包括：  
        - **iOS/iPadOS**
        - **macOS**
    - **設定檔類型**：選取 [裝置功能]  。

4. 您可設定的設定會視您選擇的平台而不同。 選擇您平台來進行詳細設定：

    - [iOS/iPadOS](ios-device-features-settings.md)
    - [macOS](macos-device-features-settings.md)

5. 當您完成時，請選取 [確定]   > [建立]  儲存變更。

設定檔隨即建立，並顯示在設定檔清單中。 請確認會[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

## <a name="next-steps"></a>後續步驟

建立設定檔之後，就可以指派它。 接下來，[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

檢視適用於 [iOS](ios-device-features-settings.md) 和 [macOS](macos-device-features-settings.md) 裝置的所有裝置功能設定。
