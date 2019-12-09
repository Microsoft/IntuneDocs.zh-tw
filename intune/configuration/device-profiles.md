---
title: Microsoft Intune 中的裝置功能和設定 - Azure | Microsoft Docs
description: 各種 Microsoft Intune 裝置設定檔的概觀。 取得包括功能、限制、電子郵件、Wi-Fi、VPN、教育、憑證、升級 Windows 10、BitLocker 與 Microsoft Defender、Windows 資訊保護、系統管理範本，以及 Azure 入口網站自訂裝置組態設定等項目的資訊。 使用這些設定檔來管理及保護公司的資料和裝置。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: b74cdf29999bccdefaa94c84673b9ea89c335537
ms.sourcegitcommit: 7001dc5a9cffeb2e161748f9e6dba126bf1cb06f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2019
ms.locfileid: "74694942"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>在 Microsoft Intune 中使用裝置設定檔將功能和設定套用至您的裝置

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune 包含可讓您在組織內不同裝置上啟用或停用的設定和功能。 這些設定和功能會新增至「組態設定檔」。 您可以為不同的裝置和平台 (包括 iOS、Android 和 Windows) 建立設定檔。 然後，使用 Intune 套用或「指派」設定檔至裝置。

作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些組態設定檔完成不同的工作。 一些設定檔範例包括：

- 在 Windows 10 裝置上，使用設定檔範本來封鎖 Internet Explorer 中的 ActiveX 控制項。
- 在 iOS 和 macOS 裝置上，允許使用者在您的組織中使用 AirPrint 印表機。
- 允許或防止對裝置上藍牙的存取。
- 建立 Wi-Fi 或 VPN 設定檔，讓不同裝置存取您的公司網路。
- 管理軟體更新，包括它們的安裝時間。
- 執行 Android 裝置作為專用 kiosk 裝置，該裝置可以執行一或多個應用程式。

本文提供您可以建立的各種類型設定檔的概觀。 使用這些設定檔以允許或防止裝置上的某些功能。

## <a name="administrative-templates"></a>系統管理範本

[系統管理範本](administrative-templates-windows.md)包含您可以為 Internet Explorer、OneDrive、遠端桌面、Word、Excel 和其他 Office 程式進行的數百項設定。

這些範本提供系統管理員一個簡化過的設定檢視，類似於群組原則，但為 100% 雲端架構。

這項功能支援：

- Windows 10 及更新版本

## <a name="certificates"></a>憑證

[憑證](../protect/certificates-configure.md)可設定指派給裝置的信任的憑證、SCEP 憑證及 PKCS 憑證。 而這些憑證可驗證 Wi-fi、VPN 和電子郵件設定檔。

這項功能支援： 

- Android
- Android 企業
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 及更新版本

## <a name="custom-profile"></a>自訂設定檔

[自訂設定](custom-settings-configure.md)可讓系統管理員指派非 Intune 中內建的裝置設定。 您可以在 Android 裝置上輸入 OMA-URI 值。 對於 iOS 裝置，您可以匯入您在 Apple Configurator 中建立的設定檔。

這項功能支援：

- Android
- Android 企業
- iOS/iPadOS
- macOS
- Windows Phone 8.1

## <a name="delivery-optimization"></a>傳遞最佳化

[傳遞最佳化](delivery-optimization-windows.md) 提供傳遞軟體更新的更棒體驗。 這些設定將取代 [軟體更新]   > [Windows 10 更新通道]  設定。

使用這些設定來控制軟體更新如何下載到您組織中的裝置。 例如，您可以讓使用者取得其自己的更新，或在裝置設定檔中使用傳遞最佳化雲端服務取得更新。

這項功能支援：

- Windows 10 及更新版本

## <a name="device-features"></a>裝置功能

[裝置功能](device-features-configure.md)控制 iOS 和 macOS 裝置上的功能，例如 AirPrint、通知和鎖定畫面訊息。

這項功能支援：

- iOS/iPadOS
- macOS

## <a name="device-firmware-configuration-interface"></a>裝置韌體設定介面

[裝置韌體設定介面](device-firmware-configuration-interface-windows.md) (DFCI) 可讓系統管理員使用 Intune 啟用或停用 UEFI (BIOS) 設定。 使用這些設定來強化韌體層級的安全性，此做法通常會對惡意攻擊更具復原性。

這項功能支援：

- Windows 10 1809 和更新版本 (在支援的韌體上)

## <a name="device-restrictions"></a>裝置限制

[裝置限制](device-restrictions-configure.md)控制安全性、硬體、資料共用，以及裝置上的更多設定。 例如，建立裝置限制設定檔以禁止 iOS 裝置的使用者使用裝置相機 。 

這項功能支援：

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 10 及更新版本
- Windows 10 團隊版

## <a name="edition-upgrade"></a>版本升級

[Windows 10 版本升級](edition-upgrade-configure-windows-10.md)自動升級執行某些 Windows 10 版本的裝置至較新的版本。

這項功能支援：

- Windows 10 及更新版本

## <a name="education"></a>Education

[教育設定 - Windows 10](education-settings-configure.md) 設定 [Windows「進行測驗」應用程式](https://education.microsoft.com/gettrained/win10takeatest)的選項。 當您設定這些選項時，裝置將無法執行其他應用程式，直到測驗結束為止。

[教育設定 - iOS](../fundamentals/education-settings-configure-ios-shared.md) 使用 iOS Classroom 應用程式，可在課堂中引導學習並控制學生的裝置。 您可以設定 iPad 裝置，讓多個學生可以共用單一裝置。

## <a name="email"></a>電子郵件

[電子郵件設定](email-settings-configure.md)會建立、指派、監視裝置上的 Exchange ActiveSync 電子郵件設定。 電子郵件設定檔有助於達成一致性、減少支援來電，以及讓終端使用者無須任何設定，就能從其個人裝置存取公司的電子郵件。 

這項功能支援： 

- Android
- Android 企業
- iOS/iPadOS
- Windows Phone 8.1
- Windows 10 及更新版本

## <a name="endpoint-protection"></a>Endpoint Protection

[適用於 Windows 10 的 Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md)可設定適用於 Windows 10 裝置的 BitLocker 及 Windows Defender 設定。

若要使用 Microsoft Intune 來將 Microsoft Defender 進階威脅防護 (WDATP) 上線，請參閱[使用行動裝置管理 (MDM) 工具設定端點](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm) \(部分機器翻譯\)。

這項功能支援：

- Windows 10 及更新版本

## <a name="esim-cellular---public-preview"></a>eSIM 行動數據 - 公開預覽

[eSIM 行動數據設定檔](esim-device-configuration.md)可讓系統管理員在您的受控裝置上設定行動數據方案來進行網際網路與資料存取。 向您的電信業者取得啟用代碼之後，請使用 Intune 匯入這些啟用代碼，然後指派給支援 eSIM 的裝置。

這項功能支援：

- Windows 10 Fall Creators Update 和更新版本

## <a name="extensions"></a>延伸模組

[核心延伸模組](kernel-extensions-overview-macos.md)讓管理員能夠在 macOS 裝置的核心層級上新增功能或程式。 設定這些設定，以信任特定開發人員或合作夥伴的所有延伸模組，或允許特有的核心延伸模組。

這項功能支援：

- macOS

## <a name="identity-protection"></a>身分識別保護

[Identity Protection](../protect/identity-protection-configure.md) 控制 Windows 10 和 Windows 10 行動裝置版裝置上的 Windows Hello 企業版體驗。 設定這些設定，將 Windows Hello 企業版提供給使用者和裝置，並指定裝置 PIN 和筆勢的需求。  

這項功能支援：  

- Windows 10 及更新版本
- Windows Holographic for Business  

## <a name="kiosk"></a>Kiosk

[Kiosk 設定](kiosk-settings.md)設定檔可將裝置設定為執行一或多個應用程式。 您也可以在 Kiosk 上自訂其他功能，包括 [開始] 功能表和網頁瀏覽器。

這項功能支援：

- Windows 10 及更新版本

Kiosk 設定也透過 [Android](device-restrictions-android.md#kiosk)、[Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) 與 [ios](device-restrictions-ios.md#kiosk) 裝置限制的形式提供。

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md) 是一項標準，讓 OEM (原始設備製造商) 和 EMM (企業行動管理) 能夠以標準化方式，在 Android Enterprise 裝置上建置及支援 OEM 特有的功能。 使用 OEMConfig，OEM 會建立結構描述來定義 OEM 特有的管理功能，並將其內嵌於已上傳至 Google Play 的應用程式中。 Intune 會從應用程式中讀取結構描述，讓 Intune 服務管理員可以設定結構描述中的設定。

這項功能支援：

- Android Enterprise (OEMConfig)

## <a name="powershell-scripts"></a>PowerShell 指令碼

[Windows 10 裝置上的 PowerShell 指令碼](../apps/intune-management-extension.md)會使用 Intune 管理延伸模組，在 Intune 中上傳 PowerShell 指令碼，然後在裝置上執行這些指令碼。 另請參閱使用延伸模組所需的項目、如何將其新增至 Intune，以及其他重要資訊。


這項功能支援：

- Windows 10 及更新版本
- Windows Holographic for Business

## <a name="shared-multi-user-device"></a>共用的多重使用者裝置

[Windows 10](shared-user-device-settings-windows.md) 和 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md) 包含可與多位使用者共同管理裝置的設定，也稱為共用的裝置或共用的電腦。 當使用者登入裝置時，您可以選擇使用者能否變更睡眠選項，或將檔案儲存在裝置上。 在另一個範例中，您可以建立一個會從 Windows HoloLens 裝置刪除非使用中認證的設定檔，以節省空間。

這些共用的多重使用者裝置設定可讓系統管理員控制某些裝置功能，並使用 Intune 管理這些共用的裝置。

這項功能支援：

- Windows 10 及更新版本
- Windows Holographic for Business

## <a name="update-policies"></a>更新原則

[iOS 更新原則](../protect/software-updates-ios.md)示範如何建立及指派 iOS 原則，以將軟體更新安裝在 iOS 裝置上。 您也可以檢閱安裝狀態。

如需 Windows 裝置上的更新原則，請參閱[傳遞最佳化](delivery-optimization-windows.md)。 

這項功能支援：

- iOS/iPadOS

## <a name="vpn"></a>VPN

[VPN 設定](vpn-settings-configure.md)指派 VPN 設定檔給組織中的使用者與裝置，讓他們可以輕鬆又安全地連線到網路。 

虛擬私人網路 (VPN) 為使用者提供安全的公司網路遠端存取。 裝置使用 VPN 連線設定檔來啟動與 VPN 伺服器的連線。 

這項功能支援： 

- Android
- Android 企業
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 及更新版本

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 設定](wi-fi-settings-configure.md)指派給使用者和裝置的無線網路設定。 若您指派 Wi-Fi 設定檔，使用者不需要自行設定即可存取您公司的 Wi-Fi。 

這項功能支援： 

- Android
- Android 企業
- iOS/iPadOS
- macOS
- Windows 8.1 (僅匯入)
- Windows 10 及更新版本

## <a name="windows-information-protection-profile"></a>Windows 資訊保護設定檔

[Windows 資訊保護](../protect/windows-information-protection-configure.md)可協助防範資料流失，但不會干擾員工的操作。 其也能協助保護企業應用程式與資料，防止企業擁有的裝置和員工在工作中使用的個人裝置意外外洩資料。 使用 Windows 資訊保護不需要變更您的環境或其他應用程式。

這項功能支援：

- Windows 10 及更新版本

## <a name="zebra-mobility-extensions-mx"></a>Zebra 行動性延伸模組 (MX)

[Zebra 行動性延伸模組 (MX)](android-zebra-mx-overview.md) 可讓系統管理員使用及管理 Intune 中的 Zebra 裝置。 您可以建立包含設定的 StageNow 設定檔，然後使用 Intune 將這些設定檔指派及部署到您的 Zebra 裝置。 [StageNow 記錄及常見問題](android-zebra-mx-logs-troubleshoot.md)是針對設定檔進行疑難排解，以及在使用 StageNow 時查看一些潛在問題的絕佳資源。

這項功能支援：

- Android (行動性延伸模組)

## <a name="manage-and-troubleshoot"></a>管理及疑難排解

[管理您的設定檔](device-profile-monitor.md)來檢查裝置的狀態，以及指派的設定檔。 也可藉由查看導致衝突的設定，以及包含這些設定的設定檔，以協助解決衝突。 [常見問題和解決方式](device-profile-troubleshoot.md)可協助系統管理員使用設定檔。 它會描述刪除設定檔時會發生什麼情況，哪些狀況會導致傳送通知至裝置，以及更多事項。

## <a name="next-steps"></a>後續步驟

選擇您的平台，並開始使用。
