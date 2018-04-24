---
title: Microsoft Intune - Azure 中的裝置設定檔 | Microsoft Docs
description: 不同 Microsoft Intune 裝置設定檔的概觀，包括功能、限制、電子郵件、Wi-Fi、VPN、教育、憑證、升級 Windows 10、BitLocker 與 Windows defender、Windows 資訊保護，以及 Azure 入口網站的自訂裝置設定。 使用這些設定檔來管理及保護資料和公司中的裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/22/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0b942f794136ce1a1d7851b0b04d6df70ea7174c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="what-are-microsoft-intune-device-profiles"></a>什麼是 Microsoft Intune 裝置設定檔？

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune 包含讓您可以在組織內不同的裝置上啟用或停用之設定及功能。 可使用設定檔來管理這些設定和功能。 一些設定檔範例包括： 

- 可讓不同裝置存取您的公司 WiFi 之 WiFi 設定檔
- 可讓不同裝置存取您公司網路內 VPN 伺服器的 VPN 設定檔

本主題提供可為您的裝置建立不同設定檔之概觀。 使用這些設定檔以允許或禁止裝置上的某些功能。

## <a name="before-you-begin"></a>開始之前
若要查看可用的功能，請開啟 [Azure 入口網站](https://portal.azure.com)，並開啟您的 Intune 資源。 

**裝置設定**包括下列各項：

- **概觀**：列出您的設定檔狀態，並在您指派給使用者和裝置的設定檔中提供其他詳細資料
- **管理**：建立裝置設定檔，並上傳自訂 [PowerShell 指令碼](intune-management-extension.md)以在設定檔中執行
- **監視**：檢查設定檔的狀態為成功或失敗，也檢視您設定檔中的記錄
- **安裝**：新增憑證授權單位 (SCEP 或 PFX) 或啟用電信費用管理 (Telecom Expense Management) 至設定檔

## <a name="create-the-profile"></a>建立設定檔

[建立裝置設定檔](device-profile-create.md)提供建立設定檔的逐步指示。 

## <a name="device-features-profile"></a>裝置功能設定檔

[裝置功能](device-features-configure.md)控制 iOS 和 macOS 裝置上的功能，例如 AirPrint、通知，以及共用的裝置設定。

這項功能支援：  
- iOS 
- macOS

## <a name="device-restrictions-profile"></a>裝置限制設定檔
[裝置限制](device-restrictions-configure.md)控制安全性、硬體、資料共用，以及裝置上的更多設定。 例如，建立裝置限制設定檔以禁止 iOS 裝置的使用者使用裝置相機 。 

這項功能支援： 

- Android
- iOS
- macOS
- Windows 10
- Windows 10 團隊版

## <a name="email-profile"></a>電子郵件設定檔
[電子郵件設定](email-settings-configure.md)設定檔建立、指派、監視裝置上的 Exchange ActiveSync 電子郵件設定。 電子郵件設定檔可協助確保一致性、減少支援來電，以及讓終端使用者無須任何設定，就能從其個人裝置存取公司的電子郵件。 

這項功能支援： 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="wi-fi-profile"></a>Wi-Fi 設定檔
[Wi-Fi 設定](wi-fi-settings-configure.md)指派給使用者和裝置的無線網路設定。 若您指派 Wi-Fi 設定檔，使用者不需要自行設定即可存取您公司的 Wi-Fi。 

這項功能支援： 

- Android
- iOS
- macOS
- Windows 8.1 (僅匯入)

## <a name="vpn-profile"></a>VPN 設定檔
[VPN 設定](vpn-settings-configure.md)指派 VPN 設定檔給組織中的使用者與裝置，讓他們可以輕鬆又安全地連線到網路。 

虛擬私人網路 (VPN) 為使用者提供安全的公司網路遠端存取。 裝置使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 

這項功能支援： 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="education-profile"></a>教育設定檔
[教育設定](education-settings-configure.md)設定 [Windows「進行測驗」應用程式](https://education.microsoft.com/gettrained/win10takeatest)的選項。 當您設定這些選項時，裝置將無法執行其他應用程式，直到測驗結束為止。

## <a name="certificates-profile"></a>憑證設定檔
[憑證](certificates-configure.md)設定信任的憑證、SCEP 憑證及 PKCS 憑證指派給裝置，以及用於驗證 Wi-Fi、VPN 及電子郵件設定檔。

這項功能支援： 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="edition-upgrade-profile"></a>版本升級設定檔
[Windows 10 版本升級](edition-upgrade-configure-windows-10.md)自動升級執行某些 Windows 10 版本的裝置至較新的版本。

此功能支援：僅限 Windows 10

## <a name="endpoint-protection-profile"></a>Endpoint Protection 設定檔
[適用於 Windows 10 的 Endpoint protection 設定](endpoint-protection-windows-10.md) 可設定適用於 Windows 10 裝置的 BitLocker 及 Windows Defender 設定。

若要使用 Microsoft Intune 上架 Windows Defender 進階威脅防護 (WDATP)，請參閱 [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (使用行動裝置管理 (MDM) 工具設定端點)。

這項功能支援：僅限 Windows 10

## <a name="windows-information-protection-profile"></a>Windows 資訊保護設定檔
[Windows 資訊保護](windows-information-protection-configure.md)可協助防範資料流失，但不會干擾員工的操作。 其也能協助保護企業應用程式與資料，防止企業擁有的裝置和員工在工作中使用的個人裝置意外外洩資料。 不需要變更您的環境或其他應用程式即可進行。

這項功能支援：僅限 Windows 10

## <a name="custom-profile"></a>自訂設定檔
[自訂設定](custom-settings-configure.md)包含指派不屬於 Intune 內建設定之裝置設定的能力。 例如，您可以在 Android 裝置上輸入 OMA-URI 值。 對於 iOS 裝置，您可以匯入您在 Apple Configurator 中建立的設定檔。 

這項功能支援：

- Android
- iOS
- macOS
- Windows Phone 8.1