---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 969e7bc4804e1f66230c76d742bec2c67c2fa006
ms.sourcegitcommit: 99b74d7849fbfc8f5cf99cba33e858eeb9f537aa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68670930"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 8月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 此外：

- 若我們預期您將需要在變更前先行採取動作，我們會發佈輔助性的 Office 訊息中心貼文。
- 當功能在生產環境中啟動時，無論是作為預覽功能還是正式推出，功能描述都會從此頁面移除，並移到 [[新增功能]](whats-new.md) 頁面。
- 此頁面和 [[新增功能]](whats-new.md) 頁面會定期更新。 請回來查看其他更新。
- 請參閱 [M365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性的交付時間表。

> [!Note]
> 這些項目會反映 Microsoft 目前針對未來版本中 Intune 功能的預期。 日期和個別的功能可能會產生變更。 並非所有正在開發的項目在此頁面上都具有功能描述。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>應用程式管理

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>控制裝置取消註冊時的 iOS 應用程式卸載行為 <!-- 3504144 -->
系統管理員可以管理在使用者或裝置群組層級取消註冊裝置時, 應用程式是否已移除或保留在裝置上。 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>分類商務用 Microsoft 網上商店應用程式 <!-- 3926922 -->
您將能夠分類商務應用程式的 Microsoft Store。 若要這麼做, 請選擇 [ **Intune**  > **用戶端應用** > 程式] [**應用**程式] > 選取商務應用程式 >**應用程式資訊** > **類別**的 Microsoft Store。 在下拉式功能表中, 指派 [類別]。
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定組織帳戶的代理程式更新內容 <!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式保護原則 (應用程式) 可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援, 而且可能無法供所有啟用應用程式的應用程式使用。 如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式 <!-- 3041956  -->
針對安裝在 Android 工作設定檔裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>某些不受監督 iOS 裝置限制將會在 iOS 13.0 版本中僅受到監督 <!-- 4867809  -->
有些設定會套用到 iOS 13.0 版僅限受監督的裝置。 這些設定包括：

- App Store、文件檢視、遊戲
  - App Store
  - 明確 iTunes、音樂、播客或新聞內容
  - 新增 Game Center 朋友
  - 多人遊戲
- 內建應用程式
  - 相機
    - FaceTime
  - Safari
    - 自動填寫
- 雲端與儲存體
  - 備份至 iCloud
  - 封鎖 iCloud 檔同步
  - 防止同步 iCloud 鑰匙圈

如果在 iOS 13.0 版本之前設定這些設定並將其指派給不受監督裝置, 這些設定仍然會套用到那些不受監督裝置。 它們也會在裝置升級至 iOS 13.0 之後套用。 這些限制會在備份和還原的不受監督裝置上移除。 

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](device-restrictions-ios.md)。

適用於：  
- iOS 13.0 和更新版本

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>新設定和現有設定的變更, 以限制 iOS 和 macOS 裝置上的功能 <!-- 4867699 4867709  -->
您將能夠建立設定檔來限制執行 iOS 和 macOS 的裝置上的設定 (**裝置配置** > **檔** > 為平臺**建立設定檔** >  **iOS**或**macOS** )輸入 >**裝置限制**)。 將新增下列功能：

- 在 [ **macOS**  > **裝置限制** > ] [**雲端和儲存體**] 上, 使用新的 [**遞交**] 設定來封鎖使用者在一個 macOS 裝置上啟動工作, 並繼續使用另一個 macOS 或 iOS 裝置。
  若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](device-restrictions-macos.md)。
- 在**iOS**  > **裝置限制**上, 有幾個變更:
  - **內建應用程式** > **尋找我的 iPhone (僅限受監督)** : 在「尋找我的應用程式」功能中封鎖這項功能的新設定。 
  - **內建應用程式** > **尋找我的朋友 (僅限受監督)** : 在「尋找我的應用程式」功能中封鎖這項功能的新設定。 
  -   >  **Wi-fi 狀態的無線修改 (僅限受監督)** : 防止使用者在裝置上開啟或關閉 wi-fi 的新設定。
  - **鍵盤和字典** >  **QuickPath (僅限受監督)** : 封鎖 QuickPath 功能的新設定。
  - **雲端和儲存體**:**活動接續**已重新命名為 [**遞交**]。

  若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](device-restrictions-ios.md)。

適用於：  
- macOS 10.15 和更新版本
- iOS 13 和更新版本

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>控制使用者登入 macOS 裝置時開啟的應用程式、檔案、檔和資料夾 <!--3914202  -->
您將能夠在 macOS 裝置上啟用及設定功能 (**裝置** > 設定**設定檔** > **建立** > 適用于的平臺 >**裝置功能**的設定檔**macOS**配置檔案類型)。 

將會有新的登入專案設定, 可控制當使用者登入已註冊的裝置時, 會開啟哪些應用程式、檔案、檔及資料夾。 

若要查看目前的設定，請前往 [Intune 中的 macOS 裝置功能設定](macos-device-features-settings.md)。

適用於：  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>適用于多應用程式模式的 Android Enterprise 專用裝置新功能 <!-- 3755304 3041943 3041946  -->
您將能夠在 Android Enterprise 專用裝置上, 以 kiosk 樣式的體驗來控制功能和設定。 若要這麼做, 請選擇 [**裝置配置** > **檔** > ] [**建立設定檔** > ] [**Android Enterprise** for platform > 裝置擁有者], 配置檔案類型的**裝置限制**。

將新增下列功能：
- **專用裝置** > **多應用程式**: 您可以在裝置上進行輕掃, 或在螢幕上浮動, 讓使用者可以移動**虛擬首頁按鈕**。
- **專用裝置** > **多應用程式**: 「中」的**存取權**可讓使用者使用「外顯」。 
- **專用裝置** > **多應用程式**:**媒體音量控制**可讓使用者使用滑杆控制裝置的媒體量。 
- **專用裝置** > **多應用程式**: 啟用螢幕保護裝置、上傳自訂映射, 以及控制螢幕保護裝置程式的顯示時機。

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md#dedicated-device-settings)。

適用於：  
- Android Enterprise 專用裝置

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>適用于 Android Enterprise 完全受控裝置的新應用程式和設定設定檔 <!-- 3574215  -->
使用設定檔, 您將能夠設定將 VPN、電子郵件和 Wi-fi 設定套用到 Android Enterprise 完全受控裝置的設定。 您將能夠:
- 使用應用程式佈建檔來部署 Outlook、Gmail 和九個工作電子郵件設定。
- 使用裝置設定檔來部署受信任的根憑證設定。
- 使用裝置設定檔來部署 VPN 和 Wi-fi 設定。

使用者會使用其使用者名稱和密碼進行驗證, 以取得 VPN、Wi-fi 和電子郵件設定檔。 目前無法使用以憑證為基礎的驗證。 

適用於：  
- Android Enterprise 完全受控

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支援 iOS 版的 IKEv2 VPN 設定檔 <!-- 1943438 -->
您可以使用 IKEv2 通訊協定建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [VPN]  (設定檔類型) > [設定]  中的新連線類型。

這些 VPN 設定檔會設定原生的 VPN 用戶端。 因此，不會有 VPN 用戶端應用程式安裝或推送到受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請前往[在 Microsoft Intune 中的 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md)。

適用於：iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>裝置註冊

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>在設定助理中略過更多畫面 <!--4877451 -->
您將能夠設定裝置註冊計劃設定檔, 略過下列設定助理畫面: 
- 螢幕使用時間
- Touch ID 設定

若要這麼做, 請移至 **裝置註冊** >  **Apple 註冊** >  **註冊計畫權杖** > 選擇 >**設定檔**的權杖 > 選擇設定檔 >**屬性** > **編輯**在 **設定助理自訂** 旁。
如需設定助理自訂的詳細資訊, 請參閱[建立 Apple 註冊設定檔](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)。

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Android 註冊裝置系統管理員支援 <!-- 4869749  -->
Android 裝置管理員註冊選項將會新增至 android 註冊頁面 (**Intune**  > **裝置註冊** >  **Android 註冊**)。 針對所有租使用者, 預設仍會啟用 Android 裝置系統管理員。  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>若是 iOS 裝置, 請自訂公司入口網站的 [註冊程式隱私權] 畫面 <!-- 4394993  -->
使用 markdown, 您將能夠自訂使用者在 iOS 註冊期間看到的公司入口網站隱私權畫面。 具體來說, 您可以自訂群組織無法在裝置上查看或執行的專案清單。

<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Android 裝置硬體頁面上包含的組建編號 <!-- 4461910  -->
每個 Android 裝置的 [硬體] 頁面上都會有一個新專案, 其中包含裝置的作業系統組建編號。

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>將自動裝置清除時間限制設定為30天 <!--4231059  -->
在最後一次登入之後, 您將能夠將自動裝置清除時間限制設定為30天 (而不是目前的限制為90天)。 若要這麼做, 請移至**Intune**  > **裝置** > **設定** > **裝置清除規則**。

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>以角色為基礎的存取控制

### <a name="default-scope-tag----3702875---"></a>預設範圍標記 <!-- 3702875 -->
新的內建預設範圍標籤將可供使用。 所有支援範圍標籤的未標記 Intune 物件, 都會自動指派給預設範圍標籤。 **預設**範圍標籤會新增至所有現有的角色指派, 以維持與目前系統管理員體驗的同位。 如果您不想讓系統管理員看到具有預設範圍標籤的 Intune 物件, 請從角色指派中移除預設範圍標籤。 這項功能與 System Center Configuration Manager 中的安全性範圍功能類似。

<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="import-and-export-security-baselines------3408610------------"></a>匯入和匯出安全性基準    <!--3408610          -->  
我們正新增匯出和匯入安全性基準的功能。 這項功能可讓您進行自訂, 並在 Intune 環境之間共用。

<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。




