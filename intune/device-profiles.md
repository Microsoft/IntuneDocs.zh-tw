---
title: Microsoft Intune - Azure 中的裝置設定檔 | Microsoft Docs
description: 不同 Microsoft Intune 裝置設定檔的概觀，包括功能、限制、電子郵件、Wi-Fi、VPN、教育、憑證、升級 Windows 10、BitLocker 與 Windows defender、Windows 資訊保護，以及 Azure 入口網站的自訂裝置設定。 使用這些設定檔來管理及保護資料和公司中的裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/19/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: c9a3146b1ad5f6f7c439d2e49cf534e14d154f76
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728696"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>什麼是 Microsoft Intune 裝置設定檔？

Microsoft Intune 包含讓您可以在組織內不同的裝置上啟用或停用之設定及功能。 可使用設定檔來管理這些設定和功能。 一些設定檔範例包括： 

- 可讓不同裝置存取您的公司 WiFi 之 WiFi 設定檔
- 可讓不同裝置存取您公司網路內 VPN 伺服器的 VPN 設定檔

此文章提供可為您的裝置建立不同設定檔的概觀。 使用這些設定檔以允許或禁止裝置上的某些功能。

## <a name="before-you-begin"></a>開始之前

若要查看可用的功能，請開啟 [Azure 入口網站](https://portal.azure.com)，並開啟您的 Intune 資源。 

**裝置設定**包括下列各項：

- **概觀**：列出您的設定檔狀態，並在您指派給使用者和裝置的設定檔中提供其他詳細資料
- **管理**：建立裝置設定檔，並上傳自訂 [PowerShell 指令碼](intune-management-extension.md)以在設定檔中執行
- **監視**：檢查設定檔的狀態為成功或失敗，也檢視您設定檔中的記錄
- **安裝**：新增憑證授權單位 (SCEP 或 PFX) 或啟用電信費用管理 (Telecom Expense Management) 至設定檔

## <a name="create-the-profile"></a>建立設定檔

[建立裝置設定檔](device-profile-create.md)提供建立設定檔的逐步指示。 

## <a name="device-features---ios-and-macos"></a>裝置功能 - iOS 和 macOS

[裝置功能](device-features-configure.md)控制 iOS 和 macOS 裝置上的功能，例如 AirPrint、通知，以及共用的裝置設定。

此功能支援：
- iOS 
- macOS

## <a name="device-restrictions"></a>裝置限制

[裝置限制](device-restrictions-configure.md)控制安全性、硬體、資料共用，以及裝置上的更多設定。 例如，建立裝置限制設定檔以禁止 iOS 裝置的使用者使用裝置相機 。 

此功能支援：

- Android
- Android Enterprise
- iOS
- macOS
- Windows 10
- Windows 10 團隊版

## <a name="delivery-optimization"></a>傳遞最佳化

[傳遞最佳化](delivery-optimization-windows.md) 提供傳遞軟體更新的更棒體驗。 這些設定將取代 [軟體更新] > [Windows 10 更新通道] 設定。

使用這些設定來控制軟體更新如何下載到您組織中的裝置。 例如，您可以讓使用者取得其自己的更新，或在裝置設定檔中使用傳遞最佳化雲端服務取得更新。

此功能支援：

- Windows 10 及更新版本

## <a name="endpoint-protection"></a>Endpoint Protection

[適用於 Windows 10 的 Endpoint protection 設定](endpoint-protection-windows-10.md) 可設定適用於 Windows 10 裝置的 BitLocker 及 Windows Defender 設定。

若要使用 Microsoft Intune 上架 Windows Defender 進階威脅防護 (WDATP)，請參閱 [Configure endpoints using Mobile Device Management (MDM) tools](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection) (使用行動裝置管理 (MDM) 工具設定端點)。

此功能支援：

- Windows 10 及更新版本

## <a name="identity-protection"></a>身分識別保護

[Identity Protection](identity-protection-configure.md) 控制 Windows 10 和 Windows 10 行動裝置版裝置上的 Windows Hello 企業版體驗。 設定這些設定，將 Windows Hello 企業版提供給使用者和裝置，並指定裝置 PIN 和筆勢的需求。  

此功能支援：  

- Windows 10 及更新版本
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

[Kiosk 設定](kiosk-settings.md)設定檔可將裝置設定為執行一或多個應用程式。 您也可以在 Kiosk 上自訂其他功能，包括 [開始] 功能表和網頁瀏覽器。

此功能支援：

- Windows 10 及更新版本

Kiosk 設定也透過 [Android](device-restrictions-android.md#kiosk)、[Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) 與 [ios](device-restrictions-ios.md#kiosk-supervised-only) 裝置限制的形式提供。

## <a name="email"></a>電子郵件

[電子郵件設定](email-settings-configure.md)會建立、指派、監視裝置上的 Exchange ActiveSync 電子郵件設定。 電子郵件設定檔有助於達成一致性、減少支援來電，以及讓終端使用者無須任何設定，就能從其個人裝置存取公司的電子郵件。 

此功能支援： 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN

[VPN 設定](vpn-settings-configure.md)指派 VPN 設定檔給組織中的使用者與裝置，讓他們可以輕鬆又安全地連線到網路。 

虛擬私人網路 (VPN) 為使用者提供安全的公司網路遠端存取。 裝置使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 

此功能支援： 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 設定](wi-fi-settings-configure.md)指派給使用者和裝置的無線網路設定。 若您指派 Wi-Fi 設定檔，使用者不需要自行設定即可存取您公司的 Wi-Fi。 

此功能支援： 

- Android
- iOS
- macOS
- Windows 8.1 (僅匯入)

## <a name="esim-cellular---public-preview"></a>eSIM 行動數據 - 公開預覽

[eSIM 行動數據設定檔](esim-device-configuration.md)可讓系統管理員在您的受控裝置上設定行動數據方案來進行網際網路與資料存取。 向您的電信業者取得啟用代碼之後，請使用 Intune 匯入這些啟用代碼，然後指派給支援 eSIM 的裝置。

此功能支援：
- Windows 10 Fall Creators Update 和更新版本

## <a name="education"></a>教育

[教育設定 - Windows 10](education-settings-configure.md) 設定 [Windows「進行測驗」應用程式](https://education.microsoft.com/gettrained/win10takeatest)的選項。 當您設定這些選項時，裝置將無法執行其他應用程式，直到測驗結束為止。

[教育設定 - iOS](education-settings-configure-ios-shared.md) 使用 iOS Classroom 應用程式，可在課堂中引導學習並控制學生的裝置。 您可以設定 iPad 裝置，讓多個學生可以共用單一裝置。

## <a name="edition-upgrade"></a>版本升級

[Windows 10 版本升級](edition-upgrade-configure-windows-10.md)自動升級執行某些 Windows 10 版本的裝置至較新的版本。

此功能支援： 
- Windows 10 及更新版本

## <a name="update-policies"></a>更新原則

[iOS 更新原則](software-updates-ios.md)示範如何建立及指派 iOS 原則，以將軟體更新安裝在 iOS 裝置上。 您也可以檢閱安裝狀態。

此功能支援：
- iOS

## <a name="certificates"></a>憑證

[憑證](certificates-configure.md)設定信任的憑證、SCEP 憑證及 PKCS 憑證指派給裝置，而且用於驗證 Wi-Fi、VPN 與電子郵件設定檔。

此功能支援： 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Windows 資訊保護設定檔

[Windows 資訊保護](windows-information-protection-configure.md)可協助防範資料流失，但不會干擾員工的操作。 其也能協助保護企業應用程式與資料，防止企業擁有的裝置和員工在工作中使用的個人裝置意外外洩資料。 使用 Windows 資訊保護不需要變更您的環境或其他應用程式。

此功能支援：
- Windows 10 及更新版本

## <a name="custom-profile"></a>自訂設定檔

[自訂設定](custom-settings-configure.md)可讓系統管理員指派不屬於 Intune 內建設定的裝置設定。 例如，您可以在 Android 裝置上輸入 OMA-URI 值。 對於 iOS 裝置，您可以匯入您在 Apple Configurator 中建立的設定檔。 

此功能支援：

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>管理及疑難排解

[管理您的設定檔](device-profile-monitor.md)來檢查裝置的狀態，以及指派的設定檔。 也可藉由查看導致衝突的設定，以及包含這些設定的設定檔，來協助解決衝突。 [常見問題和解決方法](device-profile-troubleshoot.md)提供問與答以協助處理設定檔，包括刪除設定檔時發生什麼情況、什麼情況導致通知傳送至裝置等等。
