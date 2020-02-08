---
title: 前幾個月的 Microsoft Intune 新功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 檢閱 Intune 新功能頁面中較舊的公告
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 1/28/2020
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 313d9f470e9467cc80bae9c2400d4cc64aacc7ea
ms.sourcegitcommit: 5ad0ce27a30ee3ef3beefc46d2ee49db6ec0cbe3
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886773"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune 的新功能 - 前幾個月

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


<!-- ########################## -->
## <a name="october-2019"></a>2019 年 10 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>改善了 Android 版公司入口網站應用程式中的檢查清單設計<!-- 5550857 -->  
Android 版公司入口網站應用程式中的設定檢查清單已更新為採用輕量設計與新圖示。 這些變更與針對 iOS 版公司入口網站應用程式所做的最新更新一致。 如需變更項目的並列比較，請參閱[應用程式 UI 中的新功能](whats-new-app-ui.md)。 針對已更新的註冊步驟，請參閱[使用 Android 工作設定檔註冊](/intune-user-help/enroll-device-android-work-profile)與[註冊您的 Android 裝置](/intune-user-help/enroll-device-android-company-portal)。  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Windows 10 S 模式裝置上的 Win32 應用程式<!-- 3747604 --> 
您可以在 Windows 10 S 模式受控裝置上安裝並執行 Win32 應用程式。 若要這樣做，您可以使用 Windows Defender 應用程式控制 (WDAC) PowerShell 工具，為 S 模式建立一或多個補充原則。 使用「Device Guard 簽署入口網站」簽署補充原則，然後透過 Intune 上傳及散發原則。 在 Intune 中，只要選取 [用戶端應用程式]   > [Windows 10 S 補充原則]  就可以找到此功能。 如需詳細資訊，請參閱[在 S 模式裝置上啟用 Win32 應用程式](~/apps/apps-win32-s-mode.md)。

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>以日期和時間為基礎來設定 Win32 應用程式可用性<!-- 3510685 -->
身為系統管理員，您可以設定必要 Win32 應用程式的開始時間和期限時間。 Intune 管理延伸模組將會在開始時間開始下載並快取應用程式內容。 系統會在期限時間安裝應用程式。 針對可用的應用程式，開始時間會決定應用程式何時會顯示在公司入口網站。 如需詳細資訊，請參閱 [Intune Win32 應用程式管理](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications)。

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>依據安裝 Win32 應用程式之後的寬限期要求重新啟動裝置<!-- 3136567 -->
您可以要求裝置必須在 Win32 應用程式成功安裝後重新啟動。 如需詳細資訊，請參閱 [Win32 應用程式管理](~/apps/apps-win32-app-management.md)。

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>iOS 公司入口網站的深色模式<!-- 4911422 -->
iOS 公司入口網站可以使用深色模式。 使用者可以下載公司應用程式、管理其裝置，以及取得根據所選裝置設定色彩配置的 IT 支援。 iOS 公司入口網站會自動符合使用者的裝置設定，以深色或淺色模式顯示。 如需詳細資訊，請參閱[推出 iOS 版 Microsoft Intune 公司入口網站應用程式的深色模式](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453) \(英文\)。 如需 iOS 公司入口網站的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](~/apps/company-portal-app.md)。

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android 公司入口網站強制要求最低應用程式版本<!-- 2378776 -->
透過使用應用程式防護原則 [最低公司入口網站版本]  ，您可以指定在使用者裝置上強制要求公司入口網站的特定最低定義版本。 此條件式啟動設定可讓您將 [封鎖存取]  、[抹除資料]  或 [警告]  作為未符合值時的可能動作。 此值的可能格式遵循模式 [主要].[次要]  、[主要].[次要].[組建]  或 [主要].[次要].[組建].[修訂]  。

若已設定 [最低公司入口網站版本]  設定，將會影響公司入口網站 5.0.4560.0 版及未來任何版本的任何使用者。 此設定不會影響使用的公司入口網站版本是早於推出此功能版本的使用者。 在裝置上使用應用程式自動更新的使用者，可能會因為使用最新的公司入口網站版本，而不會看到此功能的任何對話。 此設定僅適用於 Android 已註冊與尚未註冊之裝置的應用程式防護。 如需詳細資訊，請參閱 [Android 應用程式防護原則設定 - 條件式啟動](~/apps/app-protection-policy-settings-android.md#conditional-launch)。

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>將 Mobile Threat Defense 應用程式新增至尚未註冊的裝置<!-- 3005337 -->
您可以建立會根據裝置健康情況，而封鎖或選擇性地抹除使用者公司資料的 Intune 應用程式防護原則。 裝置的健康情況是使用您選擇的 Mobile Threat Defense (MTD) 解決方案來判斷的。 此功能目前使用 Intune 已註冊的裝置作為裝置合規性設定。 透過此新功能，我們將來自 Mobile Threat Defense 廠商的威脅偵測，延伸到在尚未註冊的裝置上運作。 在 Android 上，此功能需要裝置上有最新版公司入口網站。 在 iOS 上，當應用程式整合最新的 Intune SDK (v 12.0.15+) 時，就可以使用此功能。 當第一個應用程式採用最新的 Intune SDK 時，我們會更新「新功能」主題。 其餘應用程式將會輪流推出。 如需詳細資訊，請參閱[使用 Intune 建立 Mobile Threat Defense 應用程式防護原則](~/protect/mtd-app-protection-policy.md)。

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式<!-- 3041956   -->
針對安裝在 Android Enterprise 工作設定檔、專用且完全受控的裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](~/apps/app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](~/enrollment/android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](~/apps/apps-add-android-for-work.md#managed-google-play-app-types)。

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>適用於 Windows 10 和 macOS (公開預覽) 的 Microsoft Edge 77 版和更新版本<!-- 3872025, 4678761  -->
Microsoft Edge 77 版與更新版本將可部署至執行 Windows 10 與 macOS 的電腦。 

公開預覽針對 Windows 10 提供 **Dev** 和 **Beta** 通道，以及針對 macOS 提供 **Beta** 通道。 部署僅限英文 (EN)，不過，終端使用者可以在瀏覽器中的 [設定]   > [語言]  下變更顯示語言。 Microsoft Edge 是一個 Win32 應用程式，安裝在系統內容和類似的架構 (x86 OS 上的 x86 應用程式，以及 x64 OS 上的 x64 應用程式) 上。 此外，瀏覽器的自動更新預設會 [開啟]  ，而且無法解除安裝 Microsoft Edge。 如需詳細資訊，請參閱[將適用於 Windows 10 的 Microsoft Edge 新增至 Microsoft Intune](~/apps/apps-windows-edge.md) 和 [Microsoft Edge 文件](https://go.microsoft.com/fwlink/?linkid=2103823) \(英文\)。

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>應用程式保護 UI 和 iOS 應用程式佈建 UI 的更新<!-- 4102027, 4102029   -->
在 Intune 中用來建立和編輯應用程式保護原則和 iOS 應用程式佈建設定檔的 UI 已更新。 UI 變更包括：
- 使用壓縮成單一刀鋒視窗的精靈樣式格式簡化體驗。 
- 針對建立流程的更新，以包含指派。
- 檢視屬性 (建立新的原則之前) 或編輯屬性時所設定之所有內容的摘要頁面。 此外，當編輯屬性時，摘要只會顯示正在編輯的屬性類別中的項目清單。

如需詳細資訊，請參閱[如何建立及指派應用程式保護原則](~/apps/app-protection-policies.md)與[使用 iOS 應用程式佈建設定檔](~/apps/app-provisioning-profile-ios.md)。

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Intune 引導式案例<!-- 4850318, 4831296, 3610611  -->
Intune 現在提供引導式案例，協助您在 Intune 中完成一項特定工作或一組工作。 引導式案例是以一個端對端使用案例為中心的一系列自訂步驟 (工作流程)。 常見案例是根據組織中系統管理員、使用者或裝置所扮演的角色來定義。 這些工作流程通常需要一組仔細協調的設定檔、設定、應用程式和安全性控制項，以提供最佳的使用者體驗和安全性。 新的引導式案例包括：
- [部署適用於行動裝置的 Microsoft Edge](~/fundamentals/guided-scenarios-edge.md)
- [保護 Microsoft Office 行動應用程式](~/fundamentals/guided-scenarios-office-mobile.md) 
- [雲端管理的新式桌面](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

如需詳細資訊，請參閱 [Intune 引導式案例概觀](guided-scenarios-overview.md)。

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>其他可用的應用程式設定變數<!-- 4969237   -->
建立應用程式設定原則時，您可以將 `AAD Device ID` 設定變數包含在您的組態設定中。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式設定原則]   > [新增]  。 輸入設定原則詳細資料，然後選取 [組態設定]  以檢視 [組態設定]  刀鋒視窗。 如需詳細資訊，請參閱[適用於受控 Android Enterprise 裝置的應用程式設定原則 - 使用設定設計工具](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer)。

#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>建立稱為原則集合的管理物件群組<!-- 3762880  -->
原則集合可讓您建立現有管理實體的參考組合；這些實體必須以單一概念單元進行識別、設為目標及監視。 原則集合不會取代現有的概念或物件。 您可以繼續在 Intune 中指派個別物件，而且可以參考個別物件作為原則集合的一部分。 因此，對那些個別物件所做的任何變更都會反映在原則集合中。  在 Intune 中，您將選取 [原則集合]   > [建立]  建立新的原則集合。 


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>適用於 Windows 10 和更新版本裝置的新裝置韌體設定介面設定檔 (公開預覽)<!-- 2266073  -->
在 Windows 10 和更新版本上，您可以建立裝置組態設定檔來控制設定和功能 (**裝置組態** > **設定檔** > **建立設定檔** > **Windows10 和更新版本** (針對平台))。 在此更新中，有新的裝置韌體設定介面設定檔類型，可讓 Intune 管理 UEFI (BIOS) 設定。

如需這項功能的詳細資訊，請參閱[在 Microsoft Intune 中的 Windows 裝置上使用 DFCI 設定檔](../configuration/device-firmware-configuration-interface-windows.md)。

適用於：

- 支援韌體上的 Windows 10 RS5 (1809) 和更新版本

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>建立和編輯 Windows 10 更新通道的 UI 更新<!-- 4099089         -->
我們已針對 Intune 更新[建立和編輯 Windows 10 更新通道的 UI 體驗](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings)。 UI 的變更包括：  
- 壓縮成單一刀鋒視窗的精靈樣式格式，與先前在設定更新通道時看到的刀鋒視窗蔓延不一樣。   
- 在完成通道的初始設定之前，修改後的工作流程包含 [指派]。
- [摘要] 頁面可用來檢查您所做的所有設定，然後再儲存和部署新的更新通道。 編輯更新通道時，摘要僅顯示在您所編輯的屬性類別內設定的項目清單。

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>用於建立和編輯 iOS 軟體更新原則的 UI 更新<!-- 4099090       --> 
我們已針對 Intune 更新[建立](../protect/software-updates-ios.md#configure-the-policy)和[編輯](../protect/software-updates-ios.md#edit-a-policy) iOS 軟體更新原則的 UI 體驗。  UI 的變更包括：  
- 壓縮成單一刀鋒視窗的精靈樣式格式，與先前在設定更新原則時看到的刀鋒視窗蔓延不一樣。   
- 在完成原則的初始設定之前，修改後的工作流程包含 [指派]。
- 在儲存和部署新原則之前，您可以用來檢閱所有設定的 [摘要] 頁面。 編輯原則時，摘要僅顯示在您所編輯的屬性類別內設定的項目清單。

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404--------"></a>Windows Update 通道的 [預約重新啟動] 設定已移除<!--  4464404      -->
如先前所宣佈的那樣，Intune 的 Windows 10 更新通道現在[支援期限設定](../protect/windows-update-settings.md)，並且不再支援 [預約重新啟動]  。 當您在 Intune 中設定或管理更新通道時，將無法再使用 [預約重新啟動]  設定。  

這種變更會與最近的 [Windows 服務變更](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing)一致，並且在執行 Windows 10 1903 或更高版本的裝置上，[期限]  取代了 [預約重新啟動]  設定。

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>防止在 Android Enterprise 工作設定檔裝置上安裝來自不明來源的應用程式<!-- 4760025   -->
在 Android Enterprise 工作設定檔裝置上，使用者無法從不明來源安裝應用程式。 在此更新中，有一個新的設定 - **禁止在個人設定檔中從不明來源安裝應用程式**。 根據預設，此設定可防止使用者從不明來源側載應用程式到裝置上的個人設定檔。

若要查看您可以設定的設定，請前往[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：

- Android Enterprise 工作設定檔

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>在 Android Enterprise 裝置擁有者裝置上建立全域 HTTP Proxy<!-- 4816339   -->
在 Android Enterprise 裝置上，您可以設定全域 HTTP Proxy 以符合組織的網頁瀏覽標準 ([裝置組態]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  (針對平台) > [裝置擁有者] > [裝置限制]  (針對設定檔類型) > [連線]  )。 一旦設定之後，所有 HTTP 流量都會使用此 Proxy。

若要設定此功能，並查看您設定的所有設定，請前往[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：

- Android Enterprise 裝置擁有者

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Android 裝置系統管理員和 Android Enterprise 的 Wi-Fi 設定檔中已移除 [自動連線] 設定<!-- 5021055   -->
在 Android 裝置系統管理員和 Android Enterprise 裝置上，您可以建立 Wi-Fi 設定檔來設定不同的設定 ([裝置組態]   > [設定檔]   > [建立設定檔]   > [Android 裝置系統管理員]  或 [Android Enterprise]  (針對平台) > [Wi-Fi]  (針對設定檔類型))。 在此更新中，會移除 [自動連線]  設定，因為它[不受 Android 支援](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29) \(英文\)。 

如果您在 Wi-Fi 設定檔中使用此設定，您可能已注意到 [自動連線]  無法使用。 您不需要採取任何動作，但請注意，Intune 使用者介面中已移除這項設定。

若要查看目前的設定，請前往 [Android Wi-Fi 設定](../configuration/wi-fi-settings-android.md)或 [Android Enterprise Wi-Fi 設定](../configuration/wi-fi-settings-android-enterprise.md)。

適用於：

- Android 裝置管理員 
- Android 企業


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>受監督 iOS 和 iPadOS 裝置的新裝置組態設定<!-- 5199328   -->
在 iOS 和 iPadOS 裝置上，您可以建立設定檔以限制裝置上的功能和設定 ([裝置組態]   > [設定檔]   > [建立設定檔]   > [iOS/iPadOS]  (針對平台) > [裝置限制]  (針對設定檔類型))。 在此更新中，有您可以控制的新設定： 
- 存取檔案應用程式中的網路磁碟機  
- 存取檔案應用程式中的 USB 磁碟機 
- Wi-Fi 一律開啟 

若要查看這些設定，請前往[使用 Intune 來允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：

- iOS 13.0 與更新版本
- iPadOS 13.0 和更新版本

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>切換以在使用全新體驗 (OOBE) 佈建的裝置上僅顯示 [註冊狀態頁面]<!--3959566-->
您現在可以選擇在 Autopilot OOBE 所佈建的裝置上只顯示 [註冊狀態頁面]。

若要查看新的切換開關，請選擇 [Intune]   > [裝置註冊]   > [Windows 註冊]   > [註冊狀態頁面]   > [建立設定檔]   > [設定]   > [僅顯示由全新體驗 (OOBE) 佈建的裝置頁面]  。

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>指定使用工作設定檔註冊或裝置系統管理員註冊進行註冊的 Android 裝置作業系統版本<!-- 4350697   -->
使用 Intune 裝置類型限制時，您可以使用裝置的 OS 版本來指定哪些使用者裝置將使用 Android Enterprise 工作設定檔註冊或 Android 裝置系統管理員註冊。  如需詳細資訊，請參閱[設定註冊限制](../enrollment/enrollment-restrictions-set.md)。



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune 支援 iOS 11 與更新版本<!-- 4665324  -->
Intune 註冊與公司入口網站現在支援 iOS 11 版與更新版本。 不支援舊版。

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>重新命名 Windows 裝置的新限制<!-- 3478938  -->
重新命名 Windows 裝置時，您必須遵循新規則：
- 15 個字元或更少 (必須小於或等於 63 個位元組，不包括尾端的 Null 字元)
- 非 Null 或空字串
- 允許的 ASCII：字母 (a-z, A-Z)、數字 (0-9) 和連字號
- 允許的 Unicode：字元 >= 0x80，必須是有效的 UTF8，必須是 IDN 可映射 (也就是繼 RtlIdnToNameprepUnicode 之後；請參閱 RFC 3492)
- 名稱不能僅包含數字
- 名稱中不能有空格
- 不允許的字元：{ | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 如需詳細資訊，請參閱[在 Intune 中重新命名裝置](../remote-actions/device-rename.md)。

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>[裝置概觀] 頁面上的新 Android 報告<!-- 4924364 -->
[裝置概觀] 頁面的新報告會顯示每個裝置管理解決方案中已註冊的 Android 裝置數目。 此圖表顯示工作設定檔、完全受控、專用和裝置系統管理員註冊的裝置計數。 若要查看報告，請選擇 [Intune]   > [裝置]   > [概觀]  。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge 基準 (預覽)<!--  3787164  -->
我們已新增 [Microsoft Edge 設定](../protect/security-baseline-settings-edge.md)的安全性基準預覽。 

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>適用於 macOS 的 PKCS 憑證<!-- 1333650       -->
您現在可以[搭配 macOS 使用 PKCS 憑證](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)。 您可以選取 [PKCS 憑證] 作為 macOS 的設定檔類型，並部署具有[自訂主體和主體別名欄位](../protect/certficates-pfx-configure.md#subject-name-format)的使用者和裝置憑證。  

macOS 的 PKCS 憑證也支援新的設定 [允許所有應用程式存取]  。 使用這項設定，您可以啟用所有相關聯的應用程式存取憑證的私密金鑰。  如需此設定的詳細資訊，請參閱位於 https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 的 Apple 文件。

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>使用憑證佈建 iOS 行動裝置的衍生認證<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune 支援使用[衍生認證](../protect/derived-credentials.md)作為驗證方法，以及適用於 iOS 裝置的 S/MIME 簽署和加密。 衍生認證是*國家標準暨技術研究院 (NIST) 800-157* 標準的實作，用於將憑證部署至裝置。  

衍生認證仰賴個人識別驗證 (PIV) 或一般存取卡 (CAC)，如智慧卡。 若要取得其行動裝置的衍生認證，使用者必須從公司入口網站應用程式中啟動，並遵循您所使用之提供者獨有的註冊工作流程。  對於所有提供者來說，共同的要求是在電腦上使用智慧卡向衍生認證提供者進行驗證。 該提供者接著會將憑證發行至衍生自使用者智慧卡的裝置。  

Intune 支援下列衍生認證提供者：
- DISA Purebred
- Entrust Datacard
- Intercede

您可以使用衍生認證作為 VPN、Wi-Fi 和電子郵件的裝置組態設定檔的驗證方法。 您也可以使用它們進行應用程式驗證和 S/MIME 簽署和加密。  

如需有關標準的詳細資訊，請參閱位於 www.nccoe.nist.gov 的 [PIV 衍生認證](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) \(英文\)。

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>使用圖形 API 指定內部部署使用者主體名稱作為 SCEP 憑證的變數<!--  5437939        -->  
當您使用 [Intune 圖形 API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) 時，您可以將 onPremisesUserPrincipalName 指定為 SCEP 憑證的主體別名 (SAN) 的變數。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 裝置管理

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>已改善 Microsoft 365 裝置管理中的管理體驗<!-- 5551239 -->
現已在 Microsoft 365 裝置管理專家工作區 ([https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com)) 中推出重新整理且簡化的管理體驗，包括：

- **已更新的導覽**：您會發現第一層導覽已簡化，並以邏輯方式將功能分組。
- **新的平台篩選器**：您可以在 [裝置及應用程式] 頁面上選取單一平台，只顯示所選平台的原則與應用程式。
- **新的首頁**：在新的首頁上快速查看服務健康情況、租用戶狀態、新聞等等。

如需這些改進的詳細資訊，請參閱 Microsoft 技術社群網站上的 [Enterprise Mobility + Security 部落格文章](https://go.microsoft.com/fwlink/?linkid=2109094) \(英文\)。

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>推出 Microsoft 365 裝置管理中的端點安全性節點<!-- 5630102 -->

**端點安全性**節點現已在 Microsoft 365 裝置管理專家工作區 (https://devicemanagement.microsoft.com ) 中公開推出，它將各功能分組在一起，以保護端點，例如：

- 安全性基準：預先設定的設定群組，可協助您套用 Microsoft 所建議的已知設定群組與預設值。
- 安全性工作：利用 Microsoft Defender ATP 威脅與弱點管理 (TVM)，並使用 Intune 來修復端點弱點。
- Microsoft Defender ATP：整合 Microsoft Defender 進階威脅防護 (ATP) 來協助防止安全性缺口。

從其他適用的節點 (例如裝置) 仍然可以存取這些設定，不論您從哪裡存取與是否啟用這些功能，目前設定的狀態都會相同。

如需這些改進的詳細資訊，請參閱 Microsoft 技術社群網站上的 [Intune 客戶成功部落格文章](https://aka.ms/Endpoint_security_node) \(英文\)。

<!-- ########################## -->
## <a name="september-2019"></a>2019 年 9 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>受控的 Google Play 私人 LOB 應用程式<!-- 1464182  -->
Intune 現在讓 IT 管理員能夠透過內嵌於 Intune 主控台中的 iframe，將私人 Android LOB 應用程式發佈至受控的 Google Play。  以前，IT 管理員需要將 LOB 應用程式直接發佈至 Google 的 Play 發佈主控台，而這需要數個步驟且相當耗時。 這項新功能可讓您使用一組最少的步驟來輕鬆發佈 LOB 應用程式，而不需離開 Intune 主控台。  管理員將不再需要以 Google 的開發人員身分手動註冊，也不再需要向 Google 支付 25 美元的註冊費用。  任何使用受控 Google Play 的 Android Enterprise 管理案例都可利用這項功能 (工作設定檔、專用、完全受控及未註冊的裝置)。 從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 接著，從 [應用程式類型]  清單中，選取 [受控的 Google Play]  。 如需受控 Google Play 應用程式的詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)。

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows 公司入口網站體驗<!-- 1473353, 3598357 -->
Windows 公司入口網站正在更新。 您將能夠在 Windows 公司入口網站中的 [應用程式] 頁面上使用多個篩選。 [裝置詳細資料] 頁面也會使用已改進的使用者體驗進行更新。 我們正在將這些更新推出給所有客戶，預計會在下周末完成。

#### <a name="macos-support-for-web-apps---3174427---"></a>Web 應用程式的 macOS 支援<!-- 3174427 -->
Web 應用程式 (可讓您新增 Web URL 的捷徑) 可以使用 macOS 公司入口網站安裝到 Dock。 終端使用者可以在 macOS 公司入口網站中，從 Web 應用程式的 [應用程式詳細資料] 頁面存取 [安裝]  動作。 如需 **Web 連結**應用程式類型的詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](../apps/apps-add.md)，以及[將 Web 應用程式新增至 Microsoft Intune](../apps/web-app.md)。

#### <a name="macos-support-for-vpp-apps---3173501----"></a>VPP 應用程式的 macOS 支援<!-- 3173501  -->
使用 Apple Business Manager 購買的 macOS 應用程式，會在 Intune 中的 Apple VPP 權杖同步處理時顯示在主控台中。 您可以使用 Intune 主控台為群組指派、撤銷和重新指派裝置和使用者型授權。 Microsoft Intune 可協助您管理已購買供公司使用的 VPP 應用程式，方法是：

- 從應用程式市集報告授權資訊。
- 追蹤您已經使用多少個授權。
- 協助您避免安裝超過所擁有數目的應用程式複本。

如需有關 Intune 與 VPP 的詳細資訊，請參閱[使用 Microsoft Intune 管理大量採購的應用程式與書籍](../apps/vpp-apps.md)。

#### <a name="managed-google-play-iframe-support---2871756----"></a>受控的 Google Play iframe 支援<!-- 2871756  -->
Intune 現在支援透過受控的 Google Play iframe，直接在 Intune 主控台中新增和管理網頁連結。  這讓 IT 管理員能夠提交 URL 和圖示圖形，然後將那些連結部署到裝置，就像一般的 Android 應用程式一樣。 任何使用受控 Google Play 的 Android Enterprise 管理案例都可利用這項功能 (工作設定檔、專用、完全受控及未註冊的裝置)。 從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 接著，從 [應用程式類型]  清單中，選取 [受控的 Google Play]  。 如需受控 Google Play 應用程式的詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)。

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>在 Zebra 裝置上以無訊息方式安裝 Android LOB 應用程式<!-- 4252734  -->
在 [Zebra 裝置](../configuration/android-zebra-mx-overview.md)上安裝 Android 企業營運 (LOB) 應用程式時，不會提示您下載並安裝 LOB 應用程式，您將能夠以無訊息方式安裝該應用程式。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [選取應用程式類型]  窗格中，選取 [企業營運應用程式]  。 如需詳細資訊，請參閱[將 Android 企業營運應用程式新增至 Microsoft Intune](../apps/lob-apps-android.md)。

目前，在下載 LOB 應用程式之後，使用者的裝置上將出現**下載成功**通知。 只有點選通知陰影中的 [全部清除]  ，才能關閉通知。 即將發行的版本中將會修正此通知問題，而且安裝將以完全無訊息方式執行，且不會顯示任何視覺指標。

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Intune 應用程式的讀取和寫入圖形 API 作業<!-- 5031704  -->
應用程式可以使用應用程式身分識別，搭配讀取和寫入作業來呼叫 Intune 圖形 API，而無需使用者認證。 如需有關存取「適用於 Intune 的 Microsoft Graph API」的詳細資訊，請參閱[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) \(英文\)。

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>針對適用於 iOS 的 Intune App SDK 共用和加密受保護資料<!-- 3586942  -->
適用於 iOS 的 Intune App SDK 將會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 所有應用程式都將需要有 SDK 8.1.1 版，才能共用受保護資料。

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Microsoft Intune 應用程式的更新<!-- 4997846 -->
適用於 Android 的 Microsoft Intune 應用程式已更新，並具有下列改善：
- 已更新並改善版面配置以納入最重要動作的下方導覽。
- 已新增顯示使用者設定檔的額外頁面。
- 已在應用程式中為使用者新增可採取動作的通知顯示，例如需要更新其裝置設定。
- 已新增自訂推播通知的顯示，並將應用程式與適用於 iOS 和 Android 之公司入口網站應用程式中最近新增的支援一致。 如需詳細資訊，請參閱[在 Intune 中傳送自訂通知](../remote-actions/custom-notifications.md)。

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>針對 iOS 裝置，請自訂公司入口網站的 [註冊程序隱私權] 畫面<!-- 4394993 -->
使用 Markdown，您可以自訂使用者在 iOS 註冊期間看到的公司入口網站隱私權畫面。 具體來說，您可以自訂組織無法在裝置上查看或執行的操作清單。 如需詳細資訊，請參閱[如何設定 Intune 公司入口網站應用程式](../apps/company-portal-app.md#privacy-statement-customization)。



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>支援 iOS 版的 IKEv2 VPN 設定檔<!-- 1943438   -->
在此更新中，您可以使用 IKEv2 通訊協定，來建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [VPN]  作為設定檔類型 > [連線類型]  中的新連線類型。

這些 VPN 設定檔會設定原生 VPN 用戶端，因此，不會安裝任何 VPN 用戶端應用程式，或將其推送至受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請移至[在 iOS 裝置上設定 VPN 設定](../configuration/vpn-settings-ios.md)。

適用於：

- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>適用於 iOS 和 macOS 設定的裝置功能、裝置限制及擴充功能設定檔會依註冊類型顯示<!-- 4886161   -->

在 Intune 中，您會為 iOS 和 macOS 裝置建立設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  作為平台 > [裝置功能]  、[裝置限制]  或 [擴充功能]  作為設定檔類型)。 

在此更新中，Intune 入口網站中的可用設定會依其適用的註冊類型分類：

- iOS
  - 使用者註冊
  - 裝置註冊
  - 自動裝置註冊 (受監督)
  - 所有註冊類型

- macOS
  - 使用者已核准
  - 裝置註冊
  - 自動裝置註冊
  - 所有註冊類型

適用於：

- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>以 kiosk 模式執行之受監督 iOS 裝置的新語音控制設定<!-- 4892835   -->
在 Intune 中，您可以建立原則來執行受監督的 iOS 裝置作為 kiosk 或專用裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [裝置限制]  作為設定檔類型 > [Kiosk]  )。

在此更新中，有您可以控制的新設定：
- **語音控制**：在 kiosk 模式中，啟用裝置上的語音控制。
- **修改語音控制**：允許使用者在 Kiosk 模式中變更裝置上的語音控制設定。

若要查看目前的設定，請移至 [iOS Kiosk 設定](../configuration/device-restrictions-ios.md#kiosk)。

適用於：

- iOS 13.0 與更新版本

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>在 iOS 和 macOS 裝置上針對應用程式和網站使用單一登入<!-- 4893175   -->
在此更新中，有一些適用於 iOS 和 macOS 裝置的新單一登入設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  作為平台 > [裝置功能]  作為設定檔類型)。

使用這些設定來設定單一登入體驗，特別是針對使用 Kerberos 驗證的應用程式和網站。 您可以在一般認證單一登入應用程式擴充功能，以及 Apple 的內建 Kerberos 擴充功能之間進行選擇。

若要查看您目前可以設定的裝置功能，請參閱 [iOS 裝置功能](../configuration/ios-device-features-settings.md)和 [macOS 裝置功能](../configuration/macos-device-features-settings.md)。

適用於：

- iOS 13.0 與更新版本
- macOS 10.15 與更新版本

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>將網域關聯至 macOS 10.15 及以上版本裝置上的應用程式<!-- 4898079   -->
在 macOS 裝置上，您可以設定不同功能，並使用原則來將這些功能推送至裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  作為平台 > [裝置功能]  作為設定檔類型)。 在此更新中，您可以將網域關聯至應用程式。 這項功能可協助與您應用程式相關的網站共用認證，並可搭配 Apple 的單一登入擴充功能、通用連結及密碼自動填入使用。 

若要查看目前您可以設定的功能，請參閱 [Intune 中的 macOS 裝置功能設定](../configuration/macos-device-features-settings.md)。

適用於：

- macOS 10.15 與更新版本

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>顯示或隱藏 iOS 受監督裝置上的應用程式時，在 iTunes App Store URL 中使用 "iTunes" 與 "apps"<!-- 4928474   --> 
在 Intune 中，您可以建立原則來顯示或隱藏受監督 iOS 裝置上的應用程式 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [裝置限制]  作為設定檔類型 > [顯示或隱藏應用程式]  )。 

您可以輸入 iTunes App Store URL，例如 `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`。 在此更新中，`apps` 和 `itunes` 都可在 URL 中使用，例如：
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

如需這些設定的詳細資訊，請參閱[顯示或隱藏應用程式](../configuration/device-restrictions-ios.md#show-or-hide-apps)。

適用於：
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Windows 10 合規性政策密碼類型值更清楚且符合 CSP<!-- 5138985 -->
在 Windows 10 裝置上，您可以建立需要特定密碼功能的合規性政策 ([裝置合規性]   > [原則]   > [建立原則]   > [Windows 10 及更新版本]  作為平台 > [系統安全性]  )。 在此更新中：
- [密碼類型]  值更清楚，且已更新以符合 [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired) \(部分機器翻譯\)。
- [密碼到期 (天數)]  設定已更新以允許 1-730 天的值。 

如需 Windows 10 合規性設定的詳細資訊，請參閱[透過 Windows 10 及更新版本的設定將裝置標示為符合規範或不符合規範](../protect/compliance-policy-create-windows.md)。 

適用於：
- Windows 10 及更新版本

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>已更新用來設定 Microsoft Exchange 內部部署存取的 UI<!-- 4092920 -->  
我們已更新主控台，讓您可在其中[設定存取 Microsoft Exchange 內部部署存取](../protect/conditional-access-exchange-create.md)。 適用於 Exchange 內部部署存取的所有設定現在可在您「啟用 Exchange 內部部署存取控制」  的相同主控台窗格中取得。  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>允許或限制將應用程式 Widget 新增至 Android Enterprise 工作設定檔裝置上的主畫面<!-- 1109650  --> 
在 Android Enterprise 裝置上，您可以在工作設定檔中設定功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  作為平台 > [僅限工作設定檔] > [裝置限制]  作為設定檔類型)。 在此更新中，您可以讓使用者將工作設定檔應用程式所公開的 Widget 新增至裝置主畫面。

若要查看您可以設定的設定，請參閱[使用 Intune 來允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：
- Android Enterprise 工作設定檔

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>新的租用戶預設將離開 Android 裝置管理員管理<!-- 4869790   -->
Android 的裝置系統管理員功能已被 Android Enterprise 取代。 因此，建議您改用 Android Enterprise 來進行新的註冊。 在未來的更新中，新的租用戶將需要在 Android 註冊中完成下列先決條件步驟，才能使用裝置系統管理員管理：移至 [Intune]   > [裝置註冊]   > [Android 註冊]   > [具有裝置系統管理權限之個人及屬公司擁有的裝置]   > [使用裝置系統管理員來管理裝置]  。

現有的租用戶將在其環境中保持不變。

如需 Intune 中 Android 裝置系統管理員的詳細資訊，請參閱 [Android 裝置系統管理員註冊](https://docs.microsoft.com/intune/android-enroll-device-administrator)。

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045----"></a>與設定檔相關聯的 DEP 裝置清單<!-- 5012045  -->
您現在可以看到與設定檔相關聯的 Apple 自動裝置註冊計劃 (DEP) 裝置的分頁清單。 您可以從清單中的任何頁面搜尋此清單。 若要查看清單，請移至 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [指派的裝置]  (位於 [監視]  下方)。

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>預覽中的 iOS 使用者註冊<!-- 4817900 -->
Apple 的 iOS 13.1 版本包括使用者註冊，這是適用於 iOS 裝置的新形式輕量型管理。 它可用來代替個人擁有之裝置的裝置註冊或自動裝置註冊 (先前為「裝置註冊計劃」)。 Intune 的預覽藉由讓您能夠執行下列動作來支援此功能集：

- 將使用者註冊的目標設定為使用者群組。
- 讓終端使用者在註冊其裝置時，能夠在較輕量的使用者註冊或更強大的裝置註冊之間選取。

從 2019 年 9 月 24 日開始，隨著 iOS 13.1 的發行，我們正在將這些更新推出給所有客戶，預計會在下週末完成。

適用於：

- iOS 13.1 與更新版本

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>更多 Android 完全受控支援<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
我們新增了下列適用於 Android 完全受控裝置的支援：

- 適用於完全受控 Android 的 SCEP 憑證，可用來在以裝置擁有者身分管理的裝置上進行憑證驗證。 公司設定檔裝置上已經支援 SCEP 憑證。  使用適用於裝置擁有者的 SCEP 憑證，您將能夠： <!-- 5227935 -->
    - 在 Android Enterprise 的 DO 區段下方建立 SCEP 設定檔
    - 將 SCEP 憑證連結至 DO Wi-Fi 設定檔以進行驗證
    - 將 SCEP 憑證連結至 DO VPN 設定檔以進行驗證
    - 將 SCEP 憑證連結至 DO Email 設定檔以進行驗證 (透過 AppConfig)
- Android Enterprise 裝置上支援系統應用程式。 在 Intune 中，藉由選取 [用戶端應用程式]   > [應用程式]   > [新增]  ，來新增 Android Enterprise 系統應用程式。 在 [應用程式類型]  清單中，選取 [Android Enterprise 系統應用程式]  。 如需詳細資訊，請參閱[將 Android Enterprise 系統應用程式新增至 Microsoft Intune](../apps/apps-ae-system.md)。 <!-- 4062195 -->
- 在 [裝置合規性]   > [Android Enterprise]   > [裝置擁有者]  中，您可以建立合規性政策來設定 Google SafetyNet 證明層級。   <!-- 4631425 -->
- 在 Android Enterprise 完全受控裝置上，支援 Mobile Threat Defense 提供者。 在 [裝置合規性]   > [Android Enterprise]   > [裝置擁有者]  中，您可以選擇可接受的威脅等級。 <!-- 4631440 --> [使用 Intune，透過 Android Enterprise 設定將裝置標示為符合規範或不符合規範](../protect/compliance-policy-create-android-for-work.md#device-owner)列出目前的設定。
- 在 Android Enterprise 完全受控裝置上，現在可以透過應用程式設定原則來設定 Microsoft Launcher 應用程式，以便在完全受控的裝置上允許標準化的終端使用者體驗。 您可以使用 Microsoft Launcher 應用程式來將 Android 裝置個人化。 將應用程式搭配 Microsoft 帳戶或公司/學校帳戶一起使用，即可存取您個人化摘要中的行事曆、文件及最近活動。 <!-- 5334044 -->

透過此更新，我們很高興宣佈現已正式推出適用於 Android Enterprise 完全受控的 Intune 支援。

適用於：

- 完全受控的 Android Enterprise 裝置

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>將自訂通知傳送至單一裝置<!-- 4928910 -->
您現在可以選取單一裝置，然後使用遠端裝置動作，[只傳送自訂通知給該裝置](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device)。

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>利用使用者註冊來註冊的 iOS 裝置無法使用「抹除」和「密碼重設」動作<!-- 4950491 -->
使用者註冊是新類型的 Apple 裝置註冊。 當您利用使用者註冊來註冊裝置時，這類裝置將無法使用「抹除」和「密碼重設」遠端動作。

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>適用於 iOS 13 和 macOS Catalina 裝置的 Intune 支援<!-- 4665317 -->
Intune 現在支援同時管理 iOS 13 和 macOS Catalina 裝置。
如需詳細資訊，請參閱[適用於 iOS 13 和 iPadOS 的 Microsoft Intune 支援部落格文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998) \(英文\)。

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>適用於 iPadOS 與 iOS 13.1 裝置的 Intune 支援<!--5439574-->
Intune 現在支援同時管理 iPadOS 與 iOS 13.1 裝置。 如需詳細資訊，請參閱[這篇部落格文章](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094)。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>適用於用戶端驅動的復原密碼輪替的 BitLocker 支援<!--  3444125 -->
使用 Intune Endpoint Protection 設定，在執行 Windows 1909 版或更新版本的裝置上設定適用於 BitLocker 的[用戶端驅動的復原密碼輪替](../protect/endpoint-protection-windows-10.md#windows-encryption)。

此設定會在 OS 磁碟機復原 (藉由使用 bootmgr 或 WinRE) 之後起始用戶端驅動的復原密碼重新整理，並在固定資料磁碟機上解除鎖定復原密碼。 此設定會重新整理所使用的特定復原密碼，而磁碟區上其他未使用的密碼則會保持不變。 如需詳細資訊，請參閱適用於 [ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) \(部分機器翻譯\) 的 BitLocker CSP 文件。

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>適用於 Windows Defender 防毒軟體的防篡改保護<!-- 4705448        -->
使用 Intune 來管理適用於 Windows Defender 防毒軟體的「防篡改保護」  。 當您使用 Windows 10 Endpoint Protection 的裝置組態設定檔時，將可在 Microsoft Defender 資訊安全中心群組內找到[適用於防篡改保護的設定](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center)。 您可以將 [防篡改保護] 設定為 [已啟用]  以開啟 [防篡改保護] 限制、設定 [已停用]  以關閉它們，或設定 [未設定]  以讓裝置保留目前設定。  

如需防篡改保護的詳細資訊，請參閱 Windows 文件中的[使用防篡改保護來防止安全性設定變更](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) \(部分機器翻譯\)。

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>現已正式推出適用於 Windows Defender 防火牆的進階設定<!--  5317392       -->  
[適用於 Endpoint Protection 的 Windows Defender 自訂防火牆規則](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices) (您設定為裝置組態設定檔的一部分) 已超出公開預覽狀態且已正式推出 (GA)。  您可以使用這些規則，來指定應用程式、網路位址和連接埠的輸入及輸出行為。 這些規則已於七月發行為公開預覽。 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune 使用者介面更新 - [租用戶狀態] 儀表板<!-- 5273210  -->
已更新 [租用戶狀態] 儀表板的使用者介面以與 Azure 使用者介面樣式一致。 如需詳細資訊，請參閱[租用戶狀態](../tenant-status.md)。


### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863----"></a>範圍標籤現在支援使用規定原則<!-- 2358863  -->
您現在可以將[範圍標籤](scope-tags.md)指派給使用規定原則。 若要這麼做，請移至 [Intune]   > [裝置註冊]   > [條款及條件]  > 選擇清單中的項目 > [屬性]   > [範圍標籤]  > 選擇範圍標籤。

<!-- ########################## -->
## <a name="august-2019"></a>2019 年 8 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>控制當裝置取消註冊時的 iOS 應用程式解除安裝行為<!-- 3504144   -->
系統管理員可以管理當裝置在使用者或裝置群組層級取消註冊時，應用程式要從裝置上移除或保留。 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>分類商務用 Microsoft 網上商店應用程式<!-- 3926922 -->
您可以將商務用 Microsoft Store 應用程式分類。 若要這樣做，請選擇 [Intune]   > [用戶端應用程式]   > [應用程式]  > 選取商務用 Microsoft Store 應用程式 > [應用程式資訊]   > [類別]  。 在下拉式功能表中，指派類別。

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Microsoft Intune 應用程式使用者的自訂通知<!-- 4843354  -->
適用於 Android 的 Microsoft Intune 應用程式現在支援顯示自訂推播通知，使它與最近在適用於 iOS 與 Android 的公司入口網站應用程式中新增的支援有相同功能。 如需詳細資訊，請參閱[在 Intune 中傳送自訂通知](../remote-actions/custom-notifications.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>使用 Windows 10 和更新版本的系統管理範本，進行 Microsoft Edge 設定<!-- 5228061 -->
在 Windows 10 和更新版本的裝置中 ，您可以建立系統管理範本以進行 Intune 中的群組原則設定。 在此更新中，您可以進行設定，並套用至 Microsoft Edge 77 版和更新版本。

若要深入了解系統管理範本，請參閱[在 Intune 中使用 Windows 10 範本設定群組原則設定](../configuration/administrative-templates-windows.md)。

適用於：

- Windows 10 與更新版本 (Windows RS4+)

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>多個應用程式模式 Android Enterprise 專用裝置的新功能<!-- 3755304 3041943 3041946   -->

在 Intune 中，您可以控制 Android Enterprise 專用裝置上 Kiosk 式體驗的功能與設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [僅限裝置擁有者]、[裝置限制]  設定檔類型)。

在此更新中，已新增下列功能：

- [專用裝置]   > [多個應用程式]  ：[虛擬首頁按鈕]  可以透過在裝置上向上撥動來顯示，或是浮動顯示在畫面上，以便使用者可以移動它。
- [專用裝置]   > [多個應用程式]  ：[手電筒存取權]  可讓使用者使用手電筒。 
- [專用裝置]   > [多個應用程式]  ：[媒體音量控制]  可讓使用者使用滑桿來控制裝置的媒體音量。 
- [專用裝置]   > [多個應用程式]  ：**啟用螢幕保護裝置**、上傳自訂影像，並控制何時顯示螢幕保護裝置程式。

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)。

適用於：

- Android Enterprise 專用裝置

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>適用於 Android Enterprise 完全受控裝置的新應用程式設定檔<!-- 3574215 3574238 3574235 3574232   -->
您可以使用設定檔來設定將 VPN、電子郵件與 Wi-Fi 設定套用到 Android Enterprise 裝置擁有者 (完全受控) 裝置的設定。 在此更新中，您可以：

- 使用[應用程式設定原則](../apps/app-configuration-policies-use-android.md)來部署 Outlook、Gmail 與 Nine Work 電子郵件設定。
- 使用裝置組態設定檔來部署[受信任的根憑證設定](../protect/certificates-configure.md)。
- 使用裝置組態設定檔來部署 [VPN](../configuration/vpn-settings-android-enterprise.md) 與 [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) 設定。

> [!IMPORTANT]
> 使用者可以使用此功能來驗證其 VPN、Wi-Fi 與電子郵件設定檔的使用者名稱與密碼。 目前無法使用憑證式驗證。

適用於：  
- Android Enterprise 裝置擁有者 (完全受控)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>控制當使用者登入 macOS 裝置時會開啟的應用程式、檔案、文件與資料夾<!--3914202   -->
您可以啟用及設定 macOS 裝置上的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [macOS]  平台 > [裝置功能]  設定檔類型)。 

在此更新中，有一個新的 [登入項目] 設定，可控制當使用者登入已註冊的裝置時，會開啟哪些應用程式、檔案、文件與資料夾。 

若要查看目前的設定，請前往 [Intune 中的 macOS 裝置功能設定](../configuration/macos-device-features-settings.md)。

適用於：  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>Windows Update 通道的「預約重新啟動」已由「期限」取代<!-- 4464404        -->
為了具有與 [Windows 維護變更](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)相同的功能，Intune 的 Windows 10 Update 通道現在[支援期限設定](../protect/windows-update-settings.md)。 「期限」  決定裝置何時安裝功能與安全性更新。  在執行 Windows 10 1903 或更新版本的裝置上，「期限」  會取代「預約重新啟動」  的設定。  未來「期限」  也會取代舊版 Windows 10 上的「預約重新啟動」  。  

當您未設定 [期限]  時，裝置會繼續使用其 [預約重新啟動]  設定，不過在未來的更新中，Intune 將會淘汰對預約重新啟動設定的支援。  

規劃在您的所有 Windows 10 裝置上使用「期限」  。 當「期限」  的設定就緒之後，您可以將您 Intune 的「預約重新啟動」  設定變更為 [尚未設定]。 當設定為 [尚未設定] 時，Intune 會停止管理裝置上的這些設定，但不會從裝置中移除設定的最後一個組態。 因此，為「預約重新啟動」  設定的最後一個設定會在裝置上維持作用中設定，直到透過 Intune 以外的方法修改這些設定為止。 之後，當裝置的 Windows 版本變更時，或當 Intune 對「期限」  的支援擴充到裝置 Windows 版本時，裝置就會開始使用已準備好的新設定。

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>支援多個 Microsoft Intune 憑證連接器<!--   4704642      -->
Intune 現在支援安裝並使用多個[適用於 PKCS 作業的 Microsoft Intune 憑證連接器](../protect/certficates-pfx-configure.md)。 此變更支援連接器的負載平衡與高可用性。 每個連接器執行個體都能處理來自 Intune 的憑證要求。  如果某個連接器無法使用，其他連接器會繼續處理要求。

若要使用多個連接器，您不需要升級到連接器軟體的最新版本。  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>新設定，以及可限制 iOS 與 macOS 裝置上功能的現有設定變更<!-- 4867699 4867709   -->
您可以建立設定檔來限制執行 iOS 與 macOS 之裝置上的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  平台類型 > [裝置限制]  )。 此更新包含下列功能：

- 在 [macOS]   > [裝置限制]   > [雲端與儲存體]  中，使用新的 [Handoff]  設定可防止使用者在一部 macOS 裝置上工作，然後在另一部 macOS 或 iOS 裝置上繼續工作。

  若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](../configuration/device-restrictions-macos.md)。

- 在 [iOS]   > [裝置限制]  上，有幾個變更：

  - [內建應用程式]   > [尋找我的 iPhone (僅限受監督)]  ：封鎖 [尋找] 應用程式功能中此功能的新設定。 
  - [內建應用程式]   > [尋找我的朋友 (僅限受監督)]  ：封鎖 [尋找我的] 應用程式功能中此功能的新設定。 
  - [無線]   > [修改 Wi-Fi 狀態 (僅限受監督)]  ：防止使用者開啟或關閉裝置上 Wi-Fi 功能的新設定。
  - [鍵盤與字典]   > [QuickPath (僅限受監督)]  ：封鎖 QuickPath 功能的新設定。
  - **雲端與儲存體**：[活動接續]  已重新命名為 [接力]  。

  若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：  
- macOS 10.15 與更新版本
- iOS 13 與更新版本

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>某些不受監督的 iOS 裝置限制將會只在 iOS 13.0 版本中受到監督<!-- 4867809   -->
在此更新中，某些設定適用於執行 iOS 13.0 版的僅限受監督裝置。 如果在執行早於 iOS 13.0 版之版本的未受監督裝置上設定並指派這些設定，這些設定仍然會套用到那些未受監督裝置。 裝置升級到 iOS 13.0 之後仍然會套用它們。 在已備份和已還原的未受監督裝置上，系統會移除這些限制。

這些設定包括：

- App Store、文件檢視、遊戲
  - App Store
  - 清晰的 iTunes 音樂、播客或新聞內容
  - 新增 Game Center 朋友
  - 多人遊戲
- 內建應用程式
  - 相機
    - FaceTime
  - Safari
    - 自動填寫
- 雲端與儲存體
  - 備份至 iCloud
  - 禁止 iCloud Document 同步
  - 防止同步 iCloud 鑰匙圈

若要查看目前的設定，請前往[使用 Intune 允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md)。

適用於：  
- iOS 13.0 與更新版本

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>已改善 macOS FileVault 加密的裝置狀態<!-- 4944983         -->
我們已針對 macOS 裝置的 FileVault 加密更新數個[裝置狀態訊息](../protect/encryption-monitor.md#device-encryption-status)。

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>報告中的某些 Windows Defender 防毒軟體掃描設定顯示 [失敗] 狀態<!-- 5119229 -->
在 Intune 中，您可以建立原則來使用 Windows Defender Antivirus 掃描您的 Windows 10 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [裝置限制]  設定檔類型 > [Windows Defender 防毒軟體]  )。 [執行每日快速掃描的時間]  與 [要執行的系統掃描類型]  報告顯示 [失敗] 狀態，但它實際上是成功狀態。 

在此更新中，已修正此行為。 因此，[執行每日快速掃描的時間]  和 [要執行的系統掃描類型]  設定會在掃描成功完成時顯示成功狀態，並在無法套用設定時顯示失敗狀態。

如需 Windows Defender 防毒軟體設定的詳細資訊，請參閱[使用 Intune 來允許或限制功能的 Windows 10 (和更新版本) 裝置設定](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)。

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies 是 Android Enterprise 裝置上支援的 OEMConfig OEM<!-- 4843713 -->
在 Intune 中，您可以建立裝置組態設定檔，並使用 OEMConfig 將設定套用至 Android Enterprise 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [OEMConfig]  設定檔類型)。

在此更新中，Zebra Technologies 是受支援的 OEMConfig 原始設備製造商 (OEM)。 如需 OEMConfig 的詳細資訊，請參閱[運用 OEMConfig 來使用及管理 Android Enterprise 裝置](../configuration/android-oem-configuration-overview.md)。

適用於：  
- Android Enterprise


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="default-scope-tags---3702875----"></a>預設範圍標籤<!-- 3702875  -->
現已可使用新內建功能「預設範圍標籤」。 所有支援範圍標籤的未標記 Intune 物件都會自動指派至預設範圍標籤。 [預設]  範圍標籤會新增至所有現有的角色指派，以維持與目前系統管理員相同的體驗。 如果您不想讓系統管理員看到 Intune 物件有預設範圍標籤，請從角色指派中移除預設範圍標籤。 此功能與 Configuration Manager 中的安全性範圍功能類似。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](scope-tags.md)。

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android 註冊裝置系統管理員支援<!-- 4869749   -->
Android 裝置系統管理員註冊選項已新增至 Android 註冊頁面 ([Intune]   > [裝置註冊]   > [Android 註冊]  )。 針對所有租用戶，預設仍會啟用 Android 裝置系統管理員。  如需詳細資訊，請參閱 [Android 裝置系統管理員註冊](../enrollment/android-enroll-device-administrator.md)。

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>在設定輔助程式中略過更多畫面 <!--4877451  -->
您可以設定 [裝置註冊計劃] 設定檔，以略過下列 [設定輔助程式] 畫面：
- 適用於 iOS
    - 外觀
    - 快速語言
    - 慣用語言
    - 裝置到裝置的移轉
- 適用於 macOS
    - 螢幕使用時間
    - Touch ID 設定

如需 [設定輔助程式] 的詳細資訊，請參閱[建立適用於 iOS 的 Apple 註冊設定檔](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)與[建立適用於 macOS 的 Apple 註冊設定檔](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)。

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>將使用者欄新增至 Autopilot 裝置 CSV 上傳程序<!-- 3823054 -->
您現在可以將使用者欄新增至 Autopilot 裝置的 CSV 上傳。 這可讓您在匯入 CSV 時大量指派使用者。 如需詳細資訊，請參閱[使用 Windows Autopilot 在 Intune 中註冊 Windows 裝置](../enrollment/enrollment-autopilot.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>將自動裝置清除時間限制設定為最低 30 天<!--4231059  -->
您可以將自動裝置清除時間限制設定為最短在最後一次登入之後的 30 天 (而不是先前的限制 90 天)。 若要這樣做，請移至 [Intune]   > [裝置]   > [設定]   > [裝置清除規則]  。

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Android 裝置 [硬體] 頁面上包括的組建編號<!-- 4461910   -->
每個 Android 裝置的 [硬體] 頁面上都有一個新項目，它包括裝置的作業系統組建編號。 如需詳細資訊，請參閱[在 Intune 中檢視裝置詳細資料](../remote-actions/device-inventory.md)。

<!-- ########################## -->
## <a name="july-2019"></a>2019 年 7 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>使用者和群組的自訂通知<!-- 16766574          -->
將來自「公司入口網站」應用程式的自訂推播通知傳送給您以 Intune 管理的 iOS 和 Android 裝置上的使用者。 您可以使用任意文字來大幅自訂這些行動推播通知，並可用於任何用途。 您可以將它們的目標設定成您組織中各種不同的使用者群組。 如需詳細資訊，請參閱[自訂通知](../remote-actions/custom-notifications.md)。

#### <a name="googles-device-policy-controller-app---3041950----"></a>Google 的 Device Policy Controller 應用程式<!-- 3041950  -->
Managed Home Screen 應用程式現在可讓您存取 Google 的 Android Device Policy 應用程式。 Managed Home Screen 應用程式是用於裝置的自訂啟動器，這些裝置已在 Intune 中註冊為使用多應用程式 kiosk 模式的 Android Enterprise (AE) 專用裝置。 您可以存取 Android Device Policy 應用程式，或引導使用者存取 Android Device Policy 應用程式，以用以支援和偵錯。 當裝置在 Managed Home Screen 中註冊和鎖定時，即可使用這項啟動功能。 不需要其他安裝即可使用這項功能。

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>iOS 和 Android 裝置的 Outlook 保護設定<!-- 3212619 -->
您現在可以在不註冊裝置的情況下，使用簡單的 Intune 系統管理控制項，為 iOS 與 Android 版 Outlook 設定一般應用程式和資料保護組態設定。 一般應用程式組態設定所提供的設定，相當於系統管理員在管理已註冊裝置上 iOS 與 Android 版 Outlook 時所能啟用的設定。 如需有關 Outlook 設定的詳細資訊，請參閱[部署 iOS 與 Android 版 Outlook 應用程式組態設定](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune) \(部分機器翻譯\)。


#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Managed Home Screen 和受管理設定圖示<!-- 4918107 -->
Managed Home Screen 應用程式圖示和 [受管理設定]  圖示已更新。 Managed Home Screen 應用程式僅供在 Intune 中註冊為 Android Enterprise (AE) 專用裝置並以多應用程式 kiosk 模式執行的裝置使用。 如需有關 Managed Home Screen 應用程式的詳細資訊，請參閱[設定適用於 Android Enterprise 的 Microsoft Managed Home Screen 應用程式](../apps/app-configuration-managed-home-screen-app.md)。

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android Enterprise 專用裝置上的 Android Device Policy<!-- 4918136 -->
您可以從 Managed Home Screen 應用程式的偵錯畫面存取 Android Device Policy 應用程式。 Managed Home Screen 應用程式僅供在 Intune 中註冊為 Android Enterprise (AE) 專用裝置並以多應用程式 kiosk 模式執行的裝置使用。 如需詳細資訊，請參閱[設定適用於 Android Enterprise 的 Microsoft Managed Home Screen 應用程式](../apps/app-configuration-managed-home-screen-app.md)。

#### <a name="ios-company-portal-updates---3902931---"></a>iOS 公司入口網站更新<!-- 3902931 -->
iOS 應用程式管理提示上的貴公司名稱將取代目前的 "i.manage.microsoft.com" 文字。 例如，當使用者嘗試從「公司入口網站」安裝 iOS 應用程式，或當使用者允許管理應用程式時，使用者會看到其公司名稱而不是 "i.manage.microsoft.com"。 在接下來幾天將會向所有客戶推出這項功能。

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>Android Enterprise 裝置上的 AAD 和 APP<!-- 3574267 -->
讓完全受控的 Android Enterprise 裝置上線時，使用者現在會在初次設定其新的或恢復出廠預設值的裝置期間，向 Azure Active Directory (AAD) 註冊。 先前，針對完全受控的裝置，在完成設定之後，使用者必須手動啟動 Microsoft Intune 應用程式，才能啟動 AAD 註冊。 現在，當使用者在初次設定後抵達裝置首頁時，裝置便已註冊和登錄。

除了 AAD 更新之外，在完全受控的 Android Enterprise 裝置上現在也支援 Intune 應用程式防護原則 (APP)。 此功能將在我們推出它後變成可用功能。如需詳細資訊，請參閱[使用 Intune 將受控 Google Play 應用程式新增至 Android Enterprise 裝置](../apps/apps-add-android-for-work.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready------"></a>在建立 Windows 10 裝置組態設定檔時使用「適用性規則」 <!-- 2549910 eeready    -->

您可以建立 Windows 10 裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10]  平台 > [適用性規則]  )。 在這項更新中，您可以建立**適用性規則**，讓設定檔只套用到特定版本。 例如，您可以建立設定檔來啟用某些 BitLocker 設定。 一旦您新增設定檔後，您便可以使用適用性規則，將設定檔設為只套用到執行 Windows 10 企業版的裝置。

若要新增適用性規則，請參閱[適用性規則](../configuration/device-profile-create.md#applicability-rules)。

適用於：Windows 10 及更新版本

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>使用權杖在 iOS 與 macOS 裝置的自訂設定檔中新增裝置特定資訊<!-- 3330008  -->
您可以使用 iOS 與 macOS 裝置的自訂設定檔來設定 Intune 未內建的設定和功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  或 [macOS]  平台 > [自訂]  設定檔類型)。 在這項更新中，您可以將權杖新增至您的 `.mobileconfig` 檔案來新增裝置特定資訊。 例如，您可以將 `Serial Number: {{serialnumber}}` 新增至您的組態檔以顯示裝置的序號。

若要建立自訂設定檔，請參閱 [iOS 自訂設定](../configuration/custom-settings-ios.md) 或 [macOS 自訂設定](../configuration/custom-settings-macos.md)。

適用於：
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>為 Android Enterprise 建立 OEMConfig 設定檔時的新設定設計工具<!-- 3712769   -->
在 Intune 中，您可以建立使用 OEMConfig 應用程式的裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [Android 企業] 平台 > [OEMConfig] 設定檔類型)。 當您這麼做時，JSON 編輯器會開啟，其中含有可供您變更的範本和值。 

這項更新包含具有更佳使用者體驗的「設定設計工具」，可顯示內嵌在應用程式中的詳細資料，包括標題、描述等。 JSON 工具仍然可供使用，並且會顯示您在「設定設計工具中」所做的任何變更。

若要查看目前的設定，請前往[運用 OEMConfig 來使用及管理 Android Enterprise 裝置](../configuration/android-oem-configuration-overview.md)。

適用於：Android 企業

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>已更新用於設定 Windows Hello 的 UI<!-- 4089576            -->
我們已更新您[設定 Intune 以使用 Windows Hello 企業版](../protect/windows-hello.md)的主控台。 在您啟用 Windows Hello 支援的相同主控台窗格上現已提供所有組態設定。

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
透過 Microsoft Graph 提供 Intune API 支援的 Intune PowerShell SDK 已更新成 6.1907.1.0 版。 SDK 現在支援下列各項：
- 與「Azure 自動化」搭配運作。
- 支援僅限應用程式的驗證讀取作業。 
- 支援使用易記的縮寫名稱作為別名。
- 符合 PowerShell 命名慣例。 具體而言，`PSCredential` 參數 (在 `Connect-MSGraph` Cmdlet 上) 已重新命名為 `Credential`。
- 使用 `Invoke-MSGraphRequest` Cmdlet 時，支援手動指定 `Content-Type` 標頭。

如需詳細資訊，請參閱[適用於 Microsoft Intune Graph API 的 PowerShell SDK](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)。

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>管理 macOS 的 FileVault<!--  3858502 + 4557986 + 1210104  -->
您可以使用 Intune 來[管理 macOS 裝置的 FileVault 金鑰加密](../protect/encrypt-devices.md)。 若要加密裝置，您需使用端點保護裝置組態設定檔。

我們對 FileVault 的支援包括將未加密的裝置加密、委付裝置個人修復金鑰、自動或手動輪替個人加密金鑰，以及擷取您公司裝置的金鑰。 終端使用者也可以使用「公司入口網站」網站來取得其已加密裝置的個人修復金鑰。

我們也已將加密報告擴充成除了 BitLocker 資訊之外，還包含 [FileVault 相關資訊](../protect/encryption-monitor.md)，讓您可以在一個位置檢視所有裝置加密詳細資料。

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 系統管理範本中的新 Office、Windows 及 OneDrive 設定 <!-- 3510695 -->

您可以在 Intune 中建立模擬內部部署群組原則管理的系統管理範本 ([裝置管理]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [系統管理範本]  設定檔類型)。

這項更新包含更多可供您新增至範本的 Office、Windows 及 OneDrive 設定。 透過這些新的設定，您現在便可設定超過 2500 個 100% 雲端型的設定。

若要深入了解這項功能，請參閱[在 Intune 中使用 Windows 10 範本設定群組原則設定](../configuration/administrative-templates-windows.md)。

適用於：Windows 10 及更新版本

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>更新註冊限制<!-- 2871968 -->
新租用戶的「註冊限制」已更新成預設允許 Android Enterprise 公司設定檔。 現有租用戶將保持不變。 若要使用 Android Enterprise 公司設定檔，您仍然必須[將 Intune 帳戶連線至受控的 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Apple 註冊和註冊限制的 UI 更新<!--4089575, 4089579  -->
下列兩個程序皆使用精靈樣式的使用者介面：
- Apple 裝置註冊。 如需詳細資訊，請參閱[使用 Apple 的裝置註冊計劃來自動註冊 iOS 裝置](../enrollment/device-enrollment-program-enroll-ios.md)。
- 註冊限制建立。 如需詳細資訊，請參閱[設定註冊限制](../enrollment/enrollment-restrictions-set.md)。

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509-----"></a>處理 Android Q 裝置的公司裝置識別碼預先設定<!-- 4711509   -->
在 Android Q (v10) 中，Google 會讓舊版受控 (裝置系統管理員) Android 裝置上的 MDM 代理程式無法收集裝置識別碼資訊。  Intune 有一項功能，可讓 IT 系統管理員[預先設定一份裝置序號或 IMEI 的清單](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number)，以便自動將這些裝置標記為公司擁有的裝置。 此功能不適用於受裝置管理員管理的 Android Q 裝置。  不論是否上傳裝置的序號或 IMEI，在進行 Intune 註冊時，都會將其視為個人裝置。  您可以在註冊後手動將擁有權切換至公司。  這只會影響新的註冊項目，不會影響現有的已註冊裝置。  以公司設定檔管理的 Android 裝置不受這項變更影響，將會繼續依照目前的方式運作。  此外，以裝置管理員身分註冊的 Android Q 裝置將不再能夠於 Intune 主控台中將序號或 IMEI 回報成裝置屬性。

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Android Enterprise 註冊 (公司設定檔、專用裝置及完全受控裝置) 的圖示已變更<!-- 4977730 -->
Android Enterprise 註冊設定檔的圖示已變更。 若要查看新圖示，請前往 [Intune]   > [註冊]   > [Android 註冊]  > 在 [註冊設定檔]  底下尋找。

#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Windows 診斷資料收集變更<!-- 4113859 -->
執行 Windows 10 1903 版和更新版本之裝置的診斷資料收集預設值已變更。 從 Windows 10 1903 開始，預設會開啟診斷資料收集。 Windows 診斷資料是來自 Windows 裝置的重要技術資料，是與裝置及 Windows 和相關軟體執行情況有關的資料。 如需詳細資訊，請參閱[在組織中設定 Windows 診斷資料](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)。 除非在 Autopilot 設定檔中另以 [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry) 進行設定，否則 Autopilot 裝置也會選擇加入「完整」遙測。

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows Autopilot 重設會移除裝置的主要使用者<!-- 4156123 -->
在裝置上使用 Autopilot 重設時，將會移除裝置的主要使用者。 在重設後登入的下一個使用者將被設定為主要使用者。 在接下來幾天將會向所有客戶推出這項功能。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="improve-device-location---3855417----"></a>改善裝置位置<!-- 3855417  -->
您可以使用 [尋找裝置]  動作來移向裝置的確切座標。 如需有關尋找遺失之 iOS 裝置的詳細資訊，請參閱[尋找遺失的 iOS 裝置](../remote-actions/device-locate.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>適用於 Windows Defender 防火牆的進階設定 (公開預覽版)<!--  1311949     -->  
使用 Intune [將自訂防火牆規則納入裝置組態設定檔中](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)來管理，以執行 Windows 10 上的端點保護。 規則可指定應用程式、網路位址和連接埠的輸入及輸出行為。 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>已更新用於管理安全性基準的 UI<!-- 4091125     -->
我們已更新 Intune 主控台中安全性基準的[建立和編輯體驗](../protect/security-baselines.md#create-the-profile)。 這些變更包括：

已壓縮成更簡單精靈樣式的單一刀鋒視窗格式。 在一個刀鋒視窗內操作即可。 這個新設計廢除了需要 IT 專業人員向下切入至數個個別窗格的刀鋒視窗擴展。  
您現在可以在建立和編輯體驗中一併建立「指派」，而不需稍後返回來指派基準。 我們已新增設定摘要，可供您在建立新基準之前及在編輯現有基準時檢視。 編輯時，摘要只會顯示在目前編輯的一個屬性類別內設定的項目清單。

<!-- ########################## -->
## <a name="june-2019"></a>2019 年 6 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>設定允許連結至組織資料的瀏覽器<!-- 3145939 -->
Android 和 iOS 裝置上的 Intune 應用程式防護原則 (APP) 現在可讓您將組織網頁連結傳輸至 Intune Managed Browser 或 Microsoft Edge 以外的特定瀏覽器。  如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](../apps/app-protection-policy.md)

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>所有應用程式頁面皆可識別線上/離線商務用 Microsoft Store 應用程式<!--4089647 -->
[所有應用程式]  頁面現在包含可識別「商務用 Microsoft Store」(MSFB) 應用程式為線上或離線應用程式的標籤。 每個 MSFB 應用程式現在都包含「線上」  或「離線」  的尾碼。 應用程式詳細資料頁面也包含「授權類型」  和「支援裝置內容安裝」  (僅限離線授權應用程式) 資訊。

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Windows 共用裝置上的公司入口網站應用程式<!--4393553 -->
使用者現在可以存取 Windows 共用裝置上的「公司入口網站」應用程式。 終端使用者會在裝置圖標上看到「共用」  標籤。 這適用於「Windows 公司入口網站」應用程式 10.3.45609.0 版和更新版本。

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>從新的「公司入口網站」網頁檢視已安裝的應用程式<!-- 4224326 -->
「公司入口網站」的新 [已安裝的應用程式]  頁面會出安裝在使用者裝置上 (必要及可用的) 所有受控應用程式。 除了指派類型之外，使用者也可以看到應用程式的發行者、發行日期，以及目前的安裝狀態。 若您沒有針對使用者將任何應用程式設為必要或可用，他們將會看見一個訊息，說明沒有安裝任何公司應用程式。 若要在 Web 上查看新頁面，請前往[公司入口網站](https://portal.manage.microsoft.com)，然後按一下 [已安裝的應用程式]  。  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>新的檢視可讓應用程式使用者查看裝置上安裝的所有受控應用程式<!-- 2352913 -->  
適用於 Windows 的「公司入口網站」應用程式現在會列出使用者裝置上已安裝的所有受控應用程式 (必要及可用的)。 使用者也可以看到已嘗試與擱置中的應用程式安裝，以及其目前狀態。 若您沒有針對使用者將應用程式設為必要或可用，他們將會看見一個訊息，說明沒有安裝任何公司應用程式。 若要查看新檢視，請前往「公司入口網站」瀏覽窗格，然後選取 [應用程式]   > [已安裝的應用程式]  。

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 應用程式中的新功能
我們已在適用於 Android 的 Microsoft Intune 應用程式 (預覽) 中新增功能。 完全受控 Android 裝置上的使用者現在可以：  

* 透過 Intune 公司入口網站或 Microsoft Intune 應用程式，檢視及管理已註冊的裝置。
* 與其組織連絡以尋求支援。
* 將其意見反應傳送給 Microsoft。
* 若其組織已設定條款及條件，即可加以檢視。

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>可在 GitHub 上取得新的範例應用程式 (其會顯示 Intune SDK 整合)<!-- 2653471 -->
Msintuneappsdk GitHub 帳戶已新增適用於 iOS (Swift)、Android、Xamarin.iOS、Xamarin Forms 和 Xamarin.Android 的新範例應用程式。 這些應用程式旨在補充我們現有的文件，並提供如何將 Intune APP SDK 整合到您自己的行動裝置應用程式的示範。 如果您是需要其他 Intune SDK 指引的應用程式開發人員，請參閱以下連結的範例：
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) \(英文\) - 原生的 iOS (Swift) 即時通訊應用程式，其會使用 Azure Active Directory 驗證程式庫 (ADAL) 來進行代理驗證。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) \(英文\) -原生的 Android 待辦事項清單應用程式，其會使用 ADAL 來進行代理驗證。
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) \(英文\) - Xamarin.Android 待辦事項清單應用程式，其會使用 ADAL 來進行代理驗證，此存放庫也有 Xamarin.Forms 應用程式。
- [Xamarin.iOS 範例應用程式](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 重點式的 Xamarin.iOS 範例應用程式。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>在 macOS 裝置上設定核心延伸模組的設定<!-- 2043024 -->
在 macOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [macOS]  )。 這項更新包含一組新的設定，可讓您在裝置上設定及使用核心延伸模組。 您可以新增特定的延伸模組，或是允許來自特定合作夥伴或開發者的所有延伸模組。

若要深入了解此功能，請參閱[核心延伸模組概觀](../configuration/kernel-extensions-overview-macos.md)和[核心延伸模組設定](../configuration/kernel-extensions-settings-macos.md)。

適用於：macOS 10.13.2 和更新版本

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Windows 10 裝置的 [Apps from the store only] \(僅限來自 Store 的應用程式\) 設定包含更多設定選項<!-- 2697002 -->
當您建立 Windows 裝置的裝置限制設定檔時，您可以使用 [Apps from the store only] \(僅限來自 Store 的應用程式\)  設定，讓使用者只安裝來自 Windows App Store 的應用程式 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  (平台) > [裝置限制]  (設定檔類型))。 在這項更新中，此設定會擴展成支援更多選項。

若要查看新的設定，請前往[用以允許或限制功能的 Windows 10 (及更新版本) 裝置設定](../configuration/device-restrictions-windows-10.md#app-store)。

適用於：Windows 10 及更新版本

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>將多個 Zebra 行動延伸模組的裝置設定檔部署至裝置、相同的使用者群組或裝置群組<!-- 4089955 -->
在 Intune 中，您可以在裝置組態設定檔中使用 Zebra 行動延伸模組 (MX)，來自訂 Intune 未內建的 Zebra 裝置設定。 目前，一部裝置只能部署一個設定檔。 在這項更新中，您可以將多個設定檔部署至：
- 相同的使用者群組
- 相同的裝置群組
- 單一裝置

[在 Microsoft Intune 中透過 Zebra 行動延伸模組使用及管理 Zebra 裝置示範](../configuration/android-zebra-mx-overview.md)，了解如何在 Intune 中使用 MX。

適用於：Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>iOS 裝置上的某些 kiosk 設定是設定為使用 [封鎖] 來取代 [允許]<!-- 4404075  -->
當您在 iOS 裝置上建立裝置限制設定檔時 ([裝置設定]   >  [設定檔]   >  [建立設定檔]   >  [iOS] (平台)  [裝置限制]  (設定檔類型) > [Kiosk]  )，您可以設定 [自動鎖定]  、[響鈴開關]  、[旋轉螢幕]  、[螢幕睡眠按鈕]  以及 [音量按鈕]  。

在這項更新中，這些值會是 [封鎖]  (封鎖功能) 和 [未設定]  (允許功能)。 若要查看設定，請前往[用以允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md#kiosk)。

適用於：iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>在 iOS 裝置上使用 Face ID 進行密碼驗證<!-- 4490704 -->
當您建立 iOS 裝置的裝置限制設定檔時，您可以使用指紋作為密碼。 在這項更新中，指紋密碼設定也會允許臉部辨識 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型 > [密碼]  )。 因此，下列設定已變更：

- [指紋解除鎖定]  現為 [Touch ID 和 Face ID 解鎖]  。
- [指紋修改 (僅限監督對象)]  現為 [Touch ID 和 Face ID 修改 (僅限受監督)]  。

iOS 11.0 和更新版本可使用 Face ID。 若要查看這些設定，請前往[使用 Intune 來允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md#password)。

適用於：iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>iOS 裝置上的限制遊戲和 App Store 功能現在與分級區域相依<!-- 4593948 -->
您可以在 iOS 裝置上允許或限制與遊戲、App Store 及檢視文件相關的功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [裝置限制]  (設定檔類型) > [App Store、文件檢視、遊戲]  )。 您也可以選擇分級區域，例如美國。

在這項更新中，「應用程式」  功能會移動成為「分級區域」  的子系，並相依於「分級區域」  。 若要查看這些設定，請前往[使用 Intune 來允許或限制功能的 iOS 裝置設定](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

適用於：iOS

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>混合式 Azure AD Join 的 Windows Autopilot 支援<!-- 4809146-->
現有裝置的 Windows Autopilot 除了現有的 Azure AD Join 支援之外，現在也支援「混合式 Azure AD Join」。 適用於 Windows 10 1809 版和更新版本的裝置。 如需詳細資訊，請參閱[現有裝置的 Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices) \(部分機器翻譯)\。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>請參閱 Android 裝置的安全性修補程式等級<!-- 4461911 -->
您現在可以查看 Android 裝置的安全性修補程式等級。 若要這樣做，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [硬體]  。
修補程式等級會列在 [作業系統]  區段中。

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>將範圍標籤指派給安全性群組中的所有受控裝置<!-- 3173810 -->
您現在可以將範圍標籤指派給安全性群組，而安全性群組中的所有裝置也都會與這些範圍標籤建立關聯。 這些群組中的所有裝置也都會獲指派範圍標籤。 使用此功能設定之範圍標籤會覆寫以目前裝置範圍標記流程設定的範圍標籤。 如需詳細資訊，請參閱[針對分散式 IT 使用 RBAC 和範圍標籤](scope-tags.md) \(部分機器翻譯\)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>裝置安全性

#### <a name="use-keyword-search-with-security-baselines------"></a>搭配安全性基準使用關鍵字搜尋<!--  -->
建立或編輯[安全性基準設定檔](../protect/security-baselines.md#create-the-profile)時，您可以在新的「搜尋」  列中指定關鍵字，以將可用的設定群組篩選成包含您搜尋條件的設定。

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>安全性基準現已正式運作<!-- 3785395 -->
「安全性基準」  功能已結束預覽狀態，現已正式運作 (GA)。  這意謂著此功能已準備好在生產環境中使用。 不過，個別基準範本可以維持預覽狀態，並依據自己的排程進行評估及發行成 GA。

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>MDM 安全性基準範本現已正式運作<!-- 3794072, 4217151,  3534649 -->
MDM 安全性基準範本現已結束預覽狀態，現已正式運作 (GA)。 GA 範本會識別為「2019 年 5 月的 MDM 安全性基準」  。  這是一個新範本，不是預覽版的升級。  作為新範本，您將必須檢閱[它包含的設定](../protect/security-baseline-settings-mdm.md)，然後建立新設定檔以將範本部署至您的裝置。 其他安全性基準範本可以繼續保持預覽狀態。 如需可用基準的清單，請參閱[可用的安全性基準](../protect/security-baselines.md#available-security-baselines)。  

除了成為新範本之外，「2019 年 5 月的 MDM 安全性基準」  範本還包含我們最近在「開發中」文章中宣佈的兩個設定：  
- 鎖定畫面上：在鎖定畫面上啟動語音啟動應用程式  
- DeviceGuard：在下次裝置重新開機時使用虛擬化型安全性 (VBS)。  

「2019 年 5 月的 MDM 安全性基準」  也包括新增數個新設定、移除其他設定，以及修訂一個設定的預設值。 如需從預覽版到 GA 的變更詳細清單，請參閱＜新範本的變更內容＞  。

#### <a name="security-baseline-versioning---3194322---"></a>安全性基準版本設定<!-- 3194322 -->
Intune 的安全性基準支援版本設定。 有了這項支援，在每個安全性基準的新版本發行時，您便可以更新現有的安全性基準設定檔以使用較新的基準版本，而不需從頭開始重新建立及部署新的基準。 此外，在 Intune 主控台中，您還可以檢視每個基準的相關資訊，例如您所擁有之使用基準的個別設定檔數目、您的設定檔使用多少個不同的基準版本，以及特定安全性基準的最新版本是何時發行的。  如需詳細資訊，請參閱**安全性基準**。

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>[使用安全性金鑰登入] 設定已移動<!-- 4501151 -->
在 [設定 Windows Hello 企業版]  的子設定中，已經找不到名為 [使用安全性金鑰登入]  的身分識別保護裝置組態設定。 它現在已是即使您未啟用「Windows Hello 企業版」，也一律可用的最上層設定。 如需詳細資訊，請參閱[身分識別保護](../protect/identity-protection-windows-settings.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>所指派群組管理員的新權限<!-- 4504437   -->
Intune 內建的「學校管理員」角色現在具有「受管理的應用程式」的建立、讀取、更新及刪除 (CRUD) 權限。 這項更新意謂著如果您在「Intune 教育版」中被指派為群組管理員，您現在便可以建立、檢視、更新及刪除 iOS MDM Push Certificate、iOS MDM 伺服器權杖和 iOS VPP 權杖，以及[您具備的所有現有權限](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)。 若要進行這其中任何一個動作，請前往 [租用戶設定]   > [iOS 裝置管理]  。  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>應用程式可以使用圖形 API 來呼叫讀取作業而無需使用者認證<!-- 4655885 -->
應用程式可以使用應用程式身分識別來呼叫「Intune 圖形 API」讀取作業，而無需使用者認證。 如需有關存取「適用於 Intune 的 Microsoft Graph API」的詳細資訊，請參閱[在 Microsoft Graph 中使用 Intune](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0) \(英文\)。

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>將範圍標籤套用至商務用 Microsoft Store 應用程式<!-- 4392555 -->
您現在可以將範圍標籤套用至商務用 Microsoft Store 應用程式。 如需有關範圍標籤的詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](scope-tags.md)。

<!-- ########################## -->
## <a name="may-2019"></a>2019 年 5 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>針對 Android 裝置上具潛在危害之應用程式的報告<!-- 4223162 -->
Intune 現在能針對 Android 裝置上具潛在危害的應用程式提供額外的報告資訊。 

#### <a name="windows-company-portal-app---3316993---"></a>Windows 公司入口網站應用程式<!-- 3316993 -->
Windows 公司入口網站應用程式將新增標籤為 [裝置]  的頁面。 [裝置]  頁面會向終端使用者顯示其所有已註冊裝置。 使用者會在使用 10.3.4291.0 版或更新版本時，於公司入口網站看到這項變更。 如需設定公司入口網站的相關資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Intune 原則會更新驗證方法與公司入口網站應用程式安裝<!-- 1927359  -->
在已透過 [設定助理] 註冊的裝置上 (透過 Apple 的公司裝置註冊方法之一)，Intune 將不再支援公司入口網站 (當使用者從 App Store 手動安裝時)。 只有當您在註冊期間使用 Apple 設定助理進行驗證時，此變更才有意義。 此變更也只會影響透過下列各項註冊的 iOS 裝置：  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple 裝置註冊方案 (DEP)

如果使用者從 App Store 安裝公司入口網站應用程式，接著嘗試透過它註冊這些裝置，則它們將會收到錯誤。 這些裝置應該只有已在註冊期間透過 Intune 自動推送時，才會使用公司入口網站。 位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 如果您想讓 DEP 裝置使用者擁有公司入口網站，將必須在註冊設定檔中指定喜好設定。 

此外，會在 iOS 公司入口網站應用程式中移除 [識別您的裝置]  畫面。 因此，想要啟用條件式存取或部署公司應用程式的管理員必須更新 DEP 註冊設定檔。 此需求只有在 DEP 註冊是透過安裝小幫手驗證時才適用。 在該情況下，您必須將公司入口網站推送到裝置。 若要這樣做，請選擇 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [屬性]  > 將 [安裝公司入口網站]  設定為 [是]  。

若要在已經註冊的 DEP 裝置上安裝公司入口網站，您將必須移至 [Intune] > [用戶端應用程式]，然後使用應用程式設定原則來將它推送為受控應用程式。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>設定終端使用者如何使用應用程式保護原則來更新企業營運 (LOB) 應用程式<!-- 3568384 -->
您現在可以設定終端使用者可從何處取得企業營運 (LOB) 應用程式的更新版本。 終端使用者將可在 [應用程式最小版本]  條件式啟動對話方塊中看見此功能，其將提示終端使用者更新為 LOB 應用程式的最小版本。 您必須提供這些更新詳細資料作為 LOB 應用程式保護原則 (APP) 一部分。 此功能適用於 iOS 和 Android。 在 iOS 上，此功能需要整合 (或使用包裝工具包裝) 應用程式與 Intune SDK for iOS 10.0.7 版或更新版本。 在 Android 上，此功能需要最新版的公司入口網站。 若要設定終端使用者更新 LOB 應用程式的方式，應用程式需要透過金鑰 `com.microsoft.intune.myappstore` 傳送給它的受控應用程式設定原則。 傳送的值將定義終端使用者要從哪個存放區下載應用程式。 如果透過公司入口網站部署應用程式，則值必須為 `CompanyPortal`。 針對任何其他存放區，您必須輸入完整的 URL。

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune 管理延伸模組 PowerShell 指令碼<!-- 3734186  -->
您可以設定 PowerShell 指令碼，以在裝置上使用使用者的管理員權限來執行。 如需詳細資訊，請參閱[在 Windows 10 裝置上的 Intune 中使用 PowerShell 指令碼](../apps/intune-management-extension.md)和 [Win32 應用程式管理](../apps/app-management.md)。

#### <a name="android-enterprise-app-management---4459905---"></a>Android 企業應用程式管理<!-- 4459905 -->
為讓 IT 系統管理員輕鬆地設定及使用 Android 企業管理，Intune 會自動新增四個通用 Android 企業相關應用程式到 Intune 系統管理主控台。 這四個 Android Enterprise 應用程式為下列應用程式：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** - 協助您登入您的帳戶 (若您使用雙重要素驗證)。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- [受控主螢幕](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用於 Android 企業專用/資訊站案例。

之前，IT 系統管理員需要在安裝期間於[受控 Google Play 商店](https://play.google.com/store/apps)中手動尋找及核准這些應用程式。 此變更移除了先前那些手動步驟，讓客戶可以更輕鬆、更快速地使用 Android 企業管理。

系統管理員在第一次連線到其 Intune 租用戶的受控 Google Play 商店時，將會看到這四個應用程式自動新增到其 Intune 應用程式清單。 如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](../enrollment/connect-intune-android-enterprise.md)。 針對已連結其租用戶或已使用 Android 企業的租用戶，系統管理員不需要採取任何動作。 這四個應用程式會在 2019 年 5 月服務推出完成後的 7 天內自動顯示。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>已更新適用於 Microsoft Intune 的 PFX 憑證連接器<!-- 1533038 -->
我們已經發行 [Microsoft Intune 的 PFX 憑證連接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)的更新，解決現有 PFX 憑證繼續重新處理的問題，此問題造成連接器停止處理新要求。

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Defender ATP 的 Intune 安全性工作 (公開預覽)<!-- 3208597 -->
在公開預覽中，您可以使用 Intune 來管理 [Microsoft Defender 進階威脅防護 (ATP) 的安全性工作](../protect/atp-manage-vulnerabilities.md)。 這會與 ATP 整合，並新增一個以風險為基礎的方法來探索、設定優先順序及補救端點弱點和錯誤設定，同時減少從探索到風險降低之間的時間。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671-----"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組<!-- 3617671   -->
許多 Windows 10 及更新版本的裝置都具有信賴平台模組 (TPM) 晶片組。 這個更新引進新的合規性設定，此設定會檢查裝置上的 TPM 晶片版本。

[Windows 10 與更新版本的合規性原則設定](../protect/compliance-policy-create-windows.md#device-security)說明此設定。

適用於：Windows 10 及更新版本

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>在 iOS 裝置上，防止終端使用者修改其個人熱點，並停用 Siri 伺服器記錄<!-- 4097904   -->  
您會在 iOS 裝置上建立裝置限制設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 選取 [iOS] 作為平台  > 選取 [裝置限制]  作為設定檔類型)。 此更新包括您可以設定的新設定：

- **內建應用程式**：在伺服器端記錄 Siri 命令
- **無線**：使用者修改個人熱點 (僅限受監督)

若要查看這些設定，請移至[適用於 iOS 的內建應用程式設定](../configuration/device-restrictions-ios.md#built-in-apps)和[適用於 iOS 的無線設定](../configuration/device-restrictions-ios.md#wireless)。

適用於：iOS 12.2 與更新版本

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>適用於 macOS 裝置的新教室應用程式裝置限制設定<!-- 4097905   --> 
您可以為 macOS 裝置建立裝置設定設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 選取 [macOS]  作為平台 > 選取 [裝置限制]  作為設定檔類型)。 這項更新包括新的教室應用程式設定、封鎖螢幕擷取畫面的選項，以及停用「iCloud 照片圖庫」的選項。

若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](../configuration/device-restrictions-macos.md)。

適用於：macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>將用來存取 App Store 設定的 iOS 密碼重新命名<!-- 4557891  -->
將 [存取 App Store 的密碼]  設定重新命名為 [所有購買都需要 iTunes 密碼]  ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (針對平台) > [裝置限制]  (針對設定檔類型) > [App Store、文件檢視、遊戲]  )。

若要查看可用的設定，請移至 [App Store、文件檢視、遊戲的 iOS 設定](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

適用於：iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender 進階威脅防護基準 (預覽)<!--  3754134 -->
我們已新增 [Microsoft Defender 進階威脅防護](../protect/security-baseline-settings-defender-atp.md)設定的安全性基準預覽。 當您的環境符合使用 [Microsoft Defender 進階威脅防護](../protect/advanced-threat-protection.md#prerequisites)的必要條件時，即可使用此基準。

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>適用於 iOS 和 Android 裝置的 Outlook 簽章和生物特徵辨識設定<!-- 4050557 -->
您現在可以指定是否要在 iOS 和 Android 裝置上的 Outlook 中啟用預設簽章。 此外，您可以選擇允許使用者在 iOS 上的 Outlook 中變更生物特徵辨識設定。

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>iOS 裝置 F5 Access 的網路存取控制 (NAC) 支援<!-- 4500808 -->
F5 發行了 BIG-IP 13 的更新，可在 Intune 中於 iOS 上的 F5 Access 提供 NAC 功能。 若要使用此功能：

- 將 BIG-IP 更新為 13.1.1.5 版。 不支援 BIG-IP 14。
- 針對 NAC 整合 BIG-IP 與 Intune。 步驟位於 [Overview:Configuring APM for device posture checks with endpoint management systems](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html) (概觀：設定 APM 以向端點管理系統確認裝置狀態)。
- 在 Intune 中，確認 VPN 設定檔中的 [啟用網路存取控制 (NAC)]  設定。

若要查看可用的設定，請前往[在 iOS 裝置上進行 VPN 設定](../configuration/vpn-settings-ios.md)。

適用於：iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>已更新適用於 Microsoft Intune 的 PFX 憑證連接器<!-- doc-vso 1521237  -->  
我們發行了[適用於 Microsoft Intune 的 PFX 認證連接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)更新，可將輪詢間隔從 5 分鐘縮短為 30 秒。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 裝置 OrderID 屬性名稱變更為群組標籤 <!-- 4659453 -->

為了更容易查看，Autopilot 裝置上的 **OrderID** 屬性名稱已變更為**群組標籤**。 當您使用 CSV 上傳 Autopilot 裝置資訊時，必須使用群組標籤作為資料行標題，而非 OrderID。  

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows 註冊狀態頁面 (ESP) 現已全面上市<!-- 3605348 -->
註冊狀態頁面現已結束預覽。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。

#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune 使用者介面更新 - 建立 Autopilot 註冊設定檔<!-- 4593669 -->
建立 Autopilot 註冊設定檔的使用者介面已更新，以符合 Azure 使用者介面樣式。 如需詳細資訊，請參閱[建立 Autopilot 註冊設定檔](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)。 接下來，將其他 Intune 案例更新為這個新的 UI 樣式。

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>針對所有 Windows 裝置啟用 Autopilot 重設<!-- 4225665 -->
Autopilot 重設目前適用於所有 Windows 裝置，即使未設定為使用註冊狀態頁面的裝置也適用。 如果未在初始裝置註冊期間針對裝置設定註冊狀態頁面，則裝置將在登入之後直接前往桌面。 在 Intune 中最多可能需要 8 小時來進行同步處理並顯示符合規範。 如需詳細資訊，請參閱[使用遠端 Windows Autopilot 重設來重設裝置](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote) \(部分機器翻譯\)。

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>搜尋所有裝置時不需要精確的 IMEI 格式<!--30407680 -->
您不需要在搜尋**所有裝置**時，於 IMEI 編號中包含空格。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>在 Apple 入口網站刪除裝置將反映在 Intune 入口網站中<!--2489996 -->
若從 Apple 的裝置註冊計劃或 Apple 商務管理員入口網站刪除裝置，在下次同步時，會自動將該裝置從 Intune 刪除。

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>註冊狀態頁面現在會追蹤 Win32 應用程式<!-- 2714451 -->
這只適用於執行 Windows 10 1903 版及更新版本的裝置。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>使用圖形 API 大量重設及抹除裝置<!-- 3295288 -->
您現在可以使用圖形 API 大量重設及抹除最多 100 部裝置。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>加密報表已結束公開預覽<!-- 4587546      -->
現已正式推出[適用於 BitLocker 和裝置加密的報表](../protect/encryption-monitor.md)，其不再是公開預覽的一部分。


<!-- ########################## -->
## <a name="april-2019"></a>2019 年 4 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理
#### <a name="user-experience-update-for-the-company-portal-app-for-ios---2536024---"></a>iOS 版公司入口網站應用程式的使用者體驗更新<!-- 2536024 -->
適用於 iOS 裝置的公司入口網站應用程式首頁已經過重新設計。 透過這項變更，首頁將會改善採用 iOS UI 模式的能力，也會改善探索應用程式和電子書的能力。

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users--3448635---"></a>適用於 iOS 12 裝置使用者的公司入口網站註冊變更<!--3448635 -->
iOS 版公司入口網站註冊畫面和步驟，為了配合 Apple iOS 12.2 中發行的 MDM 註冊變更已有所更新。 更新的工作流程會提示使用者：  

* 允許 Safari 先開啟公司入口網站並下載管理設定檔，再返回公司入口網站應用程式。  
* 開啟設定應用程式以在其裝置上安裝管理設定檔。
* 返回公司入口網站應用程式以完成註冊。  

如需更新的註冊步驟和畫面，請參閱 [Enroll iOS device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) (在 Intune 中註冊 iOS 裝置)。

#### <a name="openssl-encryption-for-android-app-protection-policies---3747362---"></a>Android 應用程式防護原則的 OpenSSL 加密<!-- 3747362 -->
Android 裝置上 Intune 應用程式防護原則 (APP) 現在使用符合 FIPS 140-2 規範的 OpenSSL 加密程式庫。 如需詳細資訊，請參閱 [Microsoft Intune 的 Android 應用程式防護原則設定](../apps/app-protection-policy-settings-android.md)的[加密](../apps/app-protection-policy-settings-android.md#encryption)一節。

#### <a name="enable-win32-app-dependencies---2617348----"></a>啟用 Win32 應用程式相依性<!-- 2617348  -->
身為管理員，您可以要求將其他應用程式安裝為相依性，再安裝您的 Win32 應用程式。 具體來說，裝置必須安裝相依的應用程式，才能安裝 Win32 應用程式。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  以顯示 [新增應用程式]  刀鋒視窗。 選取 [Windows 應用程式 (Win32)]  作為 [應用程式類型]  。 新增應用程式之後，您可以選取 [相依性]  以新增必須先安裝才能安裝 Win32 應用程式的相依應用程式。 如需詳細資訊，請參閱 [Intune 獨立版 - Win32 應用程式管理](./../apps/app-management.md)。 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps---3537391-----"></a>商務用 Microsoft Store 應用程式的應用程式版本安裝資訊<!-- 3537391   -->
應用程式安裝報表包含商務用 Microsoft Store 應用程式的應用程式版本資訊。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]  。 選取 [商務用 Microsoft Store 應用程式]  ，然後在 [監視]  區段下選取 [裝置安裝狀態]  。

#### <a name="additions-to-win32-apps-requirement-rules---3676883-----"></a>新增 Win32 應用程式需求規則<!-- 3676883   -->
您可以建立以 PowerShell 指令碼、登錄值和檔案系統資訊為基礎的需求規則。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 然後在 [新增應用程式]  刀鋒視窗中，選取 [Windows 應用程式 (Win32)]  作為 [應用程式類型]  。  選取 [需求]   > [新增]  以設定其他需求規則。 然後，選取 [檔案類型]  、[登錄]  或 [指令碼]  作為 [需求類型]  。 如需詳細資訊，請參閱 [Win32 應用程式管理](./../apps/app-management.md)。

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices---3695227----"></a>設定在已註冊 Intune 並加入 Azure AD 之裝置上安裝您的 Win32 應用程式<!-- 3695227  -->
您可以指派在已註冊 Intune 並加入 Azure AD 的裝置上安裝 Win32 應用程式。 如需 Intune 中 Win32 應用程式的詳細資訊，請參閱 [Win32 應用程式管理](./../apps/app-management.md)。

#### <a name="device-overview-shows-primary-user--3794259----"></a>裝置概觀會顯示主要使用者<!--3794259  -->
裝置概觀頁面會顯示主要使用者，也稱為使用者裝置親和性使用者 (UDA)。 若要查看裝置的主要使用者，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置。 主要使用者會出現在 [概觀]  頁面頂端附近。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices---4105925----"></a>Android Enterprise 工作設定檔裝置的其他受控 Google Play 應用程式報告<!-- 4105925  -->
針對部署到 Android Enterprise 工作設定檔裝置的受控 Google Play 應用程式，您可以檢視裝置上所安裝應用程式的特定版本號碼。 這只適用於必要的應用程式。  

#### <a name="ios-third-party-keyboards---4111843-----"></a>iOS 協力廠商鍵盤<!-- 4111843   -->
iOS **協力廠商鍵盤**設定的 Intune 應用程式防護原則 (APP) 支援將因 iOS 平台的變更結束。 您將無法在 Intune 管理主控台中設定此設定，且無法在 Intune 應用程式 SDK 中於用戶端上實行此設定。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="updated-certificate-connectors---icm-113304612---"></a>更新憑證連接器<!-- ICM 113304612 -->
[Intune 憑證連接器和是用於 Microsoft Intune 的 PFX 憑證連接器](../protect/certficates-pfx-configure.md#whats-new-for-connectors)均已發行更新。 新的版本會修正幾個已知問題。

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices---1210083----"></a>在 macOS 裝置上設定登入設定及控制重新啟動選項<!-- 1210083  -->
在 iOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 選擇 [macOS]  平台 > [裝置功能]  設定檔類型)。 此更新包含新的登入視窗設定，例如顯示自訂橫幅、選擇使用者登入的方式、顯示或隱藏電源設定等。

若要查看這些設定，請前往 [macOS 裝置功能設定](../configuration/macos-device-features-settings.md)。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode--3041940----"></a>在以多應用程式 kiosk 模式執行的 Android Enterprise 裝置擁有者專用裝置上設定 WiFi<!--3041940  -->
當以多應用程式 kiosk 模式的專用裝置執行時，可啟用 Android Enterprise 裝置擁有者的設定。 在此更新中，使用者可以設定並連線到 WiFi 網路 ([Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [僅限裝置擁有者]、[裝置限制]  設定檔類型 > [專用裝置]   > [Kiosk 模式：   多應用程式] > [WiFi 設定]  )。

若要查看您可以設定的所有設定，請前往[允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：以多應用程式 kiosk 模式執行的 Android Enterprise 專用裝置

#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041941----"></a>在以多應用程式 kiosk 模式執行的 Android Enterprise 裝置擁有者專用裝置上設定藍牙和配對<!-- 3041941  -->
當以多應用程式 kiosk 模式的專用裝置執行時，可啟用 Android Enterprise 裝置擁有者的設定。 在此更新中，終端使用者可以啟用藍牙，並透過藍牙配對裝置 ([Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [僅限裝置擁有者]、[裝置限制]  設定檔類型 > [專用裝置]   > [Kiosk 模式  ：  多應用程式] > [藍牙設定]  )。

若要查看您可以設定的所有設定，請前往[允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：以多應用程式 kiosk 模式執行的 Android Enterprise 專用裝置

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune---3305883----"></a>在 Intune 中建立和使用 OEMConfig 裝置組態設定檔<!-- 3305883  -->
在此更新中，Intune 支援透過 OEMConfig 設定 Android Enterprise 裝置。 具體來說，您可以建立裝置組態設定檔，並使用 OEMConfig 將設定套用到 Android Enterprise 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台)。

對 OEM 的支援目前是依個別 OEM 來提供。 如果您想要的 OEMConfig 應用程式不在 OEMConfig 應用程式清單中，請連絡 `IntuneOEMConfig@microsoft.com`。

若要深入了解此功能，請前往[在 Microsoft Intune 中透過 OEMConfig 使用和管理 Android Enterprise 裝置](../configuration/android-oem-configuration-overview.md)。

適用於：Android Enterprise

#### <a name="windows-update-notifications---3316758-3316782----"></a>Windows 更新通知<!-- 3316758, 3316782  -->
Windows 更新通道設定中新增了兩項「使用者體驗設定」  ，可從 Intune 主控台進行管理。 您現在可以：
- 封鎖或允許使用者[掃描 Windows 更新](../protect/windows-update-settings.md)。
- 管理使用者所看到的 [Windows 更新通知層級](../protect/windows-update-settings.md)。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner---3574254----"></a>新增 Android Enterprise 裝置擁有者的裝置限制設定<!-- 3574254  -->
在 Android Enterprise 裝置上，您可以建立裝置限制設定檔來允許或限制功能、設定密碼規則等 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 選擇 [Android Enterprise]  平台 > [僅限裝置擁有者] > [裝置限制]  設定檔類型)。 

此更新包含新的密碼設定、允許完全受控的裝置對 Google Play 商店中應用程式進行完整存取等。 若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。 

適用於：完全受控的 Android Enterprise 裝置

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組<!-- 3617671 -->

此功能已延遲，計劃稍後發布。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices---3775833-----"></a>更新 Windows 10 及更新版本裝置上 Microsoft Edge 瀏覽器的 UI 變更<!-- 3775833   -->
當您建立裝置組態設定檔時，您可以允許或限制 Windows 10 及更新版本裝置上的 Microsoft Edge 功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [裝置限制]  設定檔類型 > [Microsoft Edge 瀏覽器]  )。 在此更新中，Microsoft Edge 設定會有更詳細的說明，因此更容易了解。

若要查看這些功能，請前往 [Microsoft Edge 瀏覽器裝置限制設定](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)。

適用於：Windows 10 及更新版本

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-----3903241-3903244-3903246-----"></a>擴充完全受控的 Android Enterprise 裝置支援 (預覽)<!--   3903241, 3903244, 3903246   -->
仍在公開預覽階段，我們已擴充完全受控的 Android Enterprise 裝置支援 (2019 年 1 月首次宣告)，包括：

- 在完全受控的專用裝置上，您可以建立[合規性政策](../protect/compliance-policy-create-android-for-work.md)來包含密碼規則和作業系統需求 ([裝置合規性]   > [原則]   > [建立原則]   > [Android Enterprise]  平台 > [裝置擁有者]  設定檔類型)。

  在專用裝置上，裝置可能會顯示為 [不符合規範]  。 專用裝置上無法使用條件式存取。 請務必完成任何工作或動作，以確保專用裝置符合您所指派原則的規範。

- [條件式存取](../protect/conditional-access.md) - 適用於 Android 的條件式存取原則也適用於完全受控的 Android Enterprise 裝置。 使用者現在可以使用 **Microsoft Intune 應用程式**，在 Azure Active Directory 中註冊其完全受控的裝置。 然後，查看並解決任何合規性問題以存取組織資源。

- 新的終端使用者應用程式 (Microsoft Intune 應用程式)：有一個適用於 Android 完全受控裝置的新終端使用者應用程式，稱為 **Microsoft Intune**。 這是輕量型且現代化的全新應用程式，提供與公司入口網站應用程式類似的功能，但適用於完全受控的裝置。 如需詳細資訊，請參閱 [Google Play 上的 Microsoft Intune 應用程式](https://play.google.com/store/apps/details?id=com.microsoft.intune)。

若要設定完全受控的 Android 裝置，請前往 [裝置註冊]   > [Android 註冊]   > [公司擁有、完全受控的使用者裝置]  。 完全受控的 Android 裝置支援仍在預覽階段，某些 Intune 功能可能無法完全正常運作。  

若要深入了解此預覽，請參閱我們的部落格 [Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged) (Microsoft Intune - 完全受控的 Android Enterprise 裝置 Preview 2)。

#### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>使用合規性管理員來建立 Microsoft Intune 的評定<!-- 4404750 -->

[合規性管理員](https://servicetrust.microsoft.com/ComplianceManager) (這會開啟另一個 Microsoft 網站) 是 Microsoft 服務信任入口網站中以工作流程為基礎的風險評定工具。 它可讓您追蹤、指派及驗證您組織中與 Microsoft 服務相關的合規性活動。 您可以使用 Office 365、Azure、Dynamics、專業服務和 Intune 來建立您自己的合規性評定。 Intune 提供兩個評定 - FFIEC 和 GDPR。

合規性管理員藉由將控制項細分為由 Microsoft 管理的控制項及由您組織管理的控制項，來協助您專注於工作。 您可以完成評定，然後匯出和列印評定。

[美國聯邦金融檢查委員會 (Federal Financial Institutions Examination Council，FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (這會開啟另一個 Microsoft 網站) 合規性是由 FFIEC 發行的一組線上銀行標準。 使用 Intune 的金融機構最常有此評定要求。 其闡釋 Intune 如何協助符合與公用網路工作負載相關的 FFIEC 網路安全性指導方針。 Intune 的 FFIEC 評定是合規性管理員中的第二項 FFIEC 評定。

您可在下列範例中看到 FFIEC 控制項的細分。 Microsoft 涵蓋 64 個控制項。 您會負責其餘 12 個控制項。

![查看 FFIEC 的範例 Intune 評定，其中包含客戶動作和 Microsoft 動作](./media/whats-new/intune-ffiec-assessment-status.png)

[一般資料保護規定 (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (這會開啟另一個 Microsoft 網站) 是協助保護個人及其資料權利的歐盟 (EU) 法律。 GDPR 是協助遵守隱私權法規最常有的評定要求。 

您可在下列範例中看到 GDPR 控制項的細分。 Microsoft 涵蓋 49 個控制項。 您會負責其餘 66 個控制項。

![查看 GDPR 的範例 Intune 評定，其中包含客戶動作和 Microsoft 動作](./media/whats-new/intune-assessment-status.png)


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant---2276470----"></a>設定設定檔，以在設定助理期間略過一些畫面<!-- 2276470  -->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- 外觀
- 顯示色調
- iCloudStorage，如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。  使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。
如需詳細資訊，請參閱[使用裝置註冊計劃或 Apple School Manager 自動註冊 macOS 裝置](../enrollment/device-enrollment-program-enroll-macos.md)。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>註冊公司 iOS 裝置時的大量裝置命名<!--3566569  -->
使用 Apple 的其中一個公司註冊方法 (DEP/ABM/ASM) 時，您可以將裝置名稱格式設定為自動命名連入的 iOS 裝置。 您可以指定格式來包含範本中的裝置類型和序號。 若要執行這項操作，請選擇 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]   > [選取權杖]   >[建立設定檔]   > [裝置命名格式]  。 您可以編輯現有的設定檔，但只有新同步的裝置會套用名稱。

#### <a name="updated-default-timeout-message-on-enrollment-status-page---3959331---"></a>更新註冊狀態頁面上的預設逾時訊息<!-- 3959331 -->
我們已更新當註冊狀態頁面 (ESP) 超過 ESP 設定檔中指定的逾時值時，使用者所看到的預設逾時訊息。 此新的預設訊息會向使用者顯示，並協助他們了解要對其 ESP 部署採取的下一個動作。  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="retire-noncompliant-devices---1827291-----"></a>淘汰不符合規範的裝置<!-- 1827291   -->
此功能已被延後，並規劃於未來版本中推出。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta---4403765---"></a>Intune 資料倉儲 V1.0 變更反映回到搶鮮版 (Beta)<!-- 4403765 -->
當 V1.0 首次在 V1.0 1808 中引進時，它與搶鮮版 (Beta) API 明顯不同。 在 1903 中，這些變更將會反映回到搶鮮版 (Beta) API 版本。 如果您有使用搶鮮版 (Beta) API 版本的重要報表，強烈建議將這些報表切換到 V1.0 以避免中斷性變更。 如需詳細資訊，請參閱 [Intune 資料倉儲 API 的變更記錄檔](../developer/reports-changelog.md#1903-part-2)。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>監視安全性基準狀態 (公開預覽) <!-- 3082047 --> 
安全性基準監視中已新增[每個類別的檢視](../protect/security-baselines-monitor.md#per-category-view) (安全性基準仍在預覽階段)。 每個類別的檢視會顯示基準中每個類別，以及落入該類別中每個狀態群組的裝置百分比。 您現在可以查看不符合每個類別、設定錯誤或不適用的裝置數目。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="scope-tags-for-apple-vpp-tokens--2371886----"></a>Apple VPP 權杖的範圍標籤<!--2371886  -->
您現在可以將範圍標籤新增至 Apple VPP 權杖。 只有獲派相同範圍標籤的使用者，才能存取具有該標籤的 Apple VPP 權杖。 使用該權杖購買的 VPP 應用程式和電子書會繼承其範圍標籤。 如需範圍標籤的詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。

<!-- ########################## -->
## <a name="march-2019"></a>2019 年 3 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理
#### <a name="deploy-microsoft-visio-and-microsoft-project---3725386----"></a>部署 Microsoft Visio 和 Microsoft Project<!-- 3725386  -->
如果您擁有 Microsoft Visio Pro for Office 365 和 Microsoft Project Online Desktop Client 的授權，您現在可以使用 Microsoft Intune 將這些應用程式當作獨立應用程式部署到 Windows 10 裝置。 從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  以顯示 [新增應用程式]  刀鋒視窗。 在 [新增應用程式]  刀鋒視窗中，選取 [Windows 10]  作為 [應用程式類型]  。 然後，選取 [設定應用程式套件]  以選取要安裝的應用程式。 如需適用於 Windows 10 裝置的 Office 365 應用程式詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](../apps/apps-add-office365.md)。

#### <a name="microsoft-visio-pro-for-office-365-product-name-change---3593653----"></a>Microsoft Visio Pro for Office 365 產品名稱變更<!-- 3593653  -->
**Microsoft Visio Pro for Office 365** 現在稱為 **Microsoft Visio Online 方案 2**。  如需 Microsoft Visio 的詳細資訊，請參閱 [Visio Online 方案 2](https://products.office.com/visio/visio-online-plan-2)。 如需適用於 Windows 10 裝置的 Office 365 應用程式詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](../apps/apps-add-office365.md)。

#### <a name="intune-app-protection-policy-app-character-limit-setting---3291302----"></a>Intune 應用程式防護原則 (APP) 字元限制設定<!-- 3291302  -->
Intune 管理員可以指定 Intune 應用程式 [限制使用其他應用程式剪下、複製及貼上]  原則設定的例外狀況。  身為管理員，您可以指定能從受控應用程式剪下或複製的字元數。 此設定可允許共用指定的字元數給任何應用程式，而不管 [限制使用其他應用程式剪下、複製及貼上] 設定。 請注意，Android 版 Intune 公司入口網站應用程式版本必須是 5.0.4364.0 版或更新版本。 如需詳細資訊，請參閱 [iOS 資料保護](../apps/app-protection-policy-settings-ios.md#data-protection)、[Android 資料保護](../apps/app-protection-policy-settings-android.md#data-protection)和[檢閱用戶端應用程式防護記錄](../apps/app-protection-policy-settings-log.md#app-protection-policy-settings)。

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment---3192477-----"></a>適用於 Office 專業增強版部署的 Office 部署工具 (ODT) XML<!-- 3192477   -->
在 Intune 管理主控台中建立 Office 專業增強版的執行個體時，您將能夠提供 Office 部署工具 (ODT) XML。 如果現有 Intune UI 選項不符合您的需求，這可提高自訂能力。 如需詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](../apps/apps-add-office365.md)和 [Office 部署工具的設定選項](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background---1429026----"></a>現在將顯示帶有自動生成背景的應用程式圖標<!-- 1429026  -->
在 Windows 公司入口網站應用程式中，現在會根據應用程式圖示主要色彩 (如果可偵測) 以自動產生的背景來顯示圖示。 適用時，此背景會取代先前在應用程式磚上顯示的灰色框線。 使用者會在公司入口網站 10.3.3451.0 以後版本中看到這項變更。

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment---2751523-----"></a>在 Windows 大量註冊之後使用公司入口網站應用程式安裝可用的應用程式<!-- 2751523   -->
使用 [Windows 大量註冊](../enrollment/windows-bulk-enroll.md) (佈建套件) 註冊到 Intune 中的 Windows 裝置，將能夠使用公司入口網站應用程式來安裝可用的應用程式。 如需公司入口網站應用程式的詳細資訊，請參閱[手動新增 Windows 10 公司入口網站](../apps/store-apps-company-portal-app.md)和[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite---3828932----"></a>Microsoft Teams 應用程式可作為 Office 應用程式套件的一部分選取<!-- 3828932  -->
Microsoft Teams 應用程式可加入作為 Office 專業增強版應用程式套件安裝的一部分或從中排除。 這項功能適用於 Office 專業增強版組建編號 16.0.11328.20116+。 使用者必須登出裝置後再重新登入，才能完成安裝。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 選取其中一個 [Office 365 套件]  應用程式類型，然後選取 [設定應用程式套件]  。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices---2351390---"></a>在 Windows 10 及更新版本裝置上以 kiosk 模式執行多個應用程式時自動啟動應用程式<!-- 2351390 -->

在 Windows 10 及更新版本裝置上，您可在 kiosk 模式下執行裝置，並執行多個應用程式。 在此更新中，有一項 [自動啟動]  設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [Kiosk]  設定檔類型 > [多應用程式 Kiosk]  )。 使用此設定在使用者登入裝置時自動啟動應用程式。

若要查看所有 kiosk 設定的清單和描述，請參閱[在 Intune 中讓 Windows 10 及更新版本裝置設定以 kiosk 形式執行](../configuration/kiosk-settings-windows.md)。

適用於：Windows 10 及更新版本

#### <a name="operational-logs-also-show-details-on-non-compliant-devices---4063755----"></a>作業記錄也會顯示不符合規範裝置的相關詳細資料<!-- 4063755  -->
將 Intune 記錄路由傳送到 Azure 監視器功能時，您也可以路由傳送作業記錄。 在此更新中，作業記錄也會提供不符合規範裝置的相關資訊。

如需此功能的詳細資訊，請參閱[在 Intune 中將記錄資料傳送至儲存體、事件中樞或記錄分析](../review-logs-using-azure-monitor.md)。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads---3804627---"></a>將記錄路由傳送到 Azure 監視器的更多 Intune 工作負載<!-- 3804627 -->
在 Intune 中，您可以將稽核與作業記錄路由傳送到 Azure 監視器的事件中樞、儲存體和記錄分析 ([Intune]   > [監視]   > [診斷設定]  )。 在此更新中，您可以將這些記錄路由傳送到更多 Intune 工作負載，包括合規性、設定、用戶端應用程式等。

若要深入了解如何將記錄路由傳送到 Azure 監視器，請參閱[將記錄資料傳送至儲存體、事件中樞或記錄分析](../review-logs-using-azure-monitor.md)。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune---3305880-----"></a>在 Intune 中建立和使用適用於 Android Zebra 裝置的行動延伸模組<!-- 3305880   -->
在此更新中，Intune 支援設定 Android Zebra 裝置。 具體來說，您可以建立裝置組態設定檔，並使用 StageNow 產生的行動延伸模組 (MX) 設定檔將設定套用到 Android Zebra 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android]  平台 > [MX 設定檔 (僅限 Zebra)]  設定檔類型)。

如需此功能的詳細資訊，請參閱[在 Intune 中透過行動延伸模組使用和管理 Zebra 裝置](../configuration/android-zebra-mx-overview.md)。

適用於：Android

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理
#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 裝置的加密報表 (公開預覽)<!-- 2351538 -->
使用新[加密報表 (預覽)](../protect/encryption-monitor.md) 來檢視 Windows 10 裝置加密狀態的相關詳細資料。 可用的詳細資料包含裝置 TPM 版本、加密整備和狀態、錯誤報告等。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview---2351547-----"></a>從 Intune 入口網站存取 BitLocker 修復金鑰 (公開預覽)<!-- 2351547   -->
您現在可以使用 Intune 來檢視 Azure Active Directory 中 BitLocker 金鑰識別碼和 BitLocker 修復金鑰的相關[詳細資料](../protect/encryption-monitor.md)。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>對 iOS 和 Android 裝置上 Intune 案例的 Microsoft Edge 支援<!-- 3411007 -->
Microsoft Edge 將支援與 Intune Managed Browser 相同的所有管理案例，另外還改善終端使用者體驗。 Microsoft Edge 企業功能是由 Intune 原則啟用，其中包含雙重身分識別、應用程式防護原則整合、Azure 應用程式 Proxy 整合，以及受控的我的最愛和首頁捷徑。 如需詳細資訊，請參閱 [Microsoft Edge 支援](../apps/app-configuration-managed-browser.md#microsoft-edge-support)。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices--3105122----"></a>Exchange Online/Intune 連接器淘汰僅限 EAS 裝置的支援<!--3105122  -->
Intune 主控台不再支援檢視和管理使用 Intune 連接器連線到 Exchange Online 的僅限 EAS 裝置。 相反地，您有下列選項：
- 在行動裝置管理 (MDM) 中註冊裝置
- 使用 Intune 應用程式防護原則來管理裝置
- 如 [Clients and mobile in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) (Exchange Online 中的用戶端和行動裝置) 中所述使用 Exchange 控制項

#### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name--4254930---"></a>使用 [名稱] 搜尋確切裝置的所有裝置頁面<!--4254930 -->
您現在可以搜尋確切裝置名稱。 移至 [Intune]   > [裝置]   > [所有裝置]  > 在搜尋方塊中，以 {} 括住裝置名稱來搜尋入完全相符的項目。 例如， **{Device12345}** 。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="support-for-additional-connectors-on-the-tenant-status-page---3617202----"></a>租用戶狀態頁面上的其他連接器支援<!-- 3617202  -->
[[租用戶狀態] 頁面](../tenant-status.md) 現在會顯示其他連接器的狀態資訊，包括 *Windows Defender 進階威脅防護* (ATP) 及其他 Mobile Threat Defense 連接器。

#### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune---4260871---"></a>Microsoft Intune 中的 [資料倉儲] 刀鋒視窗提供對 Power BI 合規性應用程式的支援<!-- 4260871 -->
之前，[Intune 資料倉儲]  刀鋒視窗中的 [下載 Power BI 檔案]  連結會下載 Intune 資料倉儲報表 (.pbix 檔案)。 此報表已取代為 Power BI 合規性應用程式。 Power BI 合規性應用程式不需要特殊載入或設定。 它會直接在 Power BI Online 入口網站中開啟，並根據您的認證顯示 Intune 租用戶特定資料。 在 Intune 中，選取 [Intune] 刀鋒視窗右側的 [設定 Intune 資料倉儲]  連結。 然後，按一下 [取得 Power BI 應用程式]  。 如需詳細資訊，請參閱[使用 Power BI 連線至資料倉儲](../developer/reports-proc-get-a-link-powerbi.md)。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles---3637917----"></a>Intune 唯讀存取權將授與某些 Azure Active Directory 角色<!-- 3637917  -->
Intune 唯讀存取權已授與下列 Azure Active Directory 角色。 透過 Azure AD 角色授與的權限會取代透過 Intune 角色型存取控制 (RBAC) 授與的權限。

對 Intune 稽核資料的唯讀存取權：

- 合規性管理員
- 相容性資料管理員

對所有 Intune 資料的唯讀存取權：

- 安全性系統管理員
- 安全性操作員
- 安全性讀取者

如需詳細資訊，請參閱[角色型存取控制](role-based-access-control.md)。

#### <a name="scope-tags-for-ios-app-provisioning-profiles--2934430-----"></a>iOS 應用程式佈建設定檔的範圍標籤<!--2934430   -->
您可以將範圍標籤新增至 iOS 應用程式佈建設定檔，僅限具有角色並同時獲派該範圍標籤的人員才能存取 iOS 應用程式佈建設定檔。 如需詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。

#### <a name="scope-tags-for-app-configuration-policies--2371891-----"></a>應用程式設定原則的範圍標籤<!--2371891   -->
您可以將範圍標籤新增至應用程式設定原則，僅限具有角色並同時獲派該範圍標籤的人員才能存取應用程式設定原則。 應用程式設定原則只能指定給或關聯到獲派相同範圍標籤的應用程式。 如需詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices---3411007---"></a>對 iOS 和 Android 裝置上 Intune 案例的 Microsoft Edge 支援<!-- 3411007 -->
Microsoft Edge 將支援與 Intune Managed Browser 相同的所有管理案例，並將在終端使用者體驗中新增增強功能。 Microsoft Edge 企業功能是由 Intune 原則啟用，其中包含雙重身分識別、應用程式防護原則整合、Azure 應用程式 Proxy 整合，以及受控的我的最愛和首頁捷徑。 如需詳細資訊，請參閱 [Microsoft Edge 支援](../apps/app-configuration-managed-browser.md#microsoft-edge-support)。




<!-- ########################## -->
## <a name="february-2019"></a>2019 年 2 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理
#### <a name="intune-macos-company-portal-dark-mode---3300524----"></a>Intune macOS 公司入口網站深色模式<!-- 3300524  -->
Intune macOS 公司入口網站現在支援 macOS 的深色模式。 當您在 macOS 10.14+ 裝置上啟用 [深色模式] 時，公司入口網站會將其外觀調整為反映該模式的色彩。

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices---2577355-----"></a>Intune 會在 Android 裝置上利用 Google Play Protect API<!-- 2577355   -->
某些 IT 系統管理員面臨到在 BYOD 的情況下，終端使用者的行動電話最後可能會遭到 Root 或 JB 破解。 這項行為雖然有時並非惡意，但還是會導致為了保護組織在終端使用者裝置上之資料所設定的許多 Intune 原則遭到略過。 因此，Intune 會針對已註冊和取消註冊的裝置提供 Root 和 JB 破解偵測。 在此版本中，Intune 現在會利用 Google Play Protect API，在我們現有的 Root 破解偵測檢查中新增對已取消註冊裝置的檢查。 雖然 Google 不會共用所發生 Root 破解偵測檢查的全部內容，但我們預期這些 API 會偵測到其裝置基於任何原因而遭到 Root 破解的使用者，這些原因從裝置自訂到能夠在舊版裝置上取得新版 OS 更新。 接著可防止這些使用者存取公司資料，或從其啟用原則的應用程式抹除其公司帳戶。 為了提高價值，IT 系統管理員現在於 [Intune 應用程式防護] 刀鋒視窗中有數項報告更新：「標有旗標的使用者」報告將會顯示透過 Google Play Protect 的 SafetyNet API 掃描偵測到哪些使用者，而「潛在有害的應用程式」報告將會顯示透過 Google 的 Verify Apps API 掃描偵測到哪些應用程式。 這項功能適用於 Android。

#### <a name="win32-app-information-available-in-troubleshooting-blade---2617342-----"></a>[疑難排解] 刀鋒視窗提供 Win32 應用程式資訊<!-- 2617342   -->
您現在可以從 Intune 應用程式 [疑難排解]  刀鋒視窗收集 Win32 應用程式安裝的失敗記錄檔。 如需應用程式安裝疑難排解的詳細資訊，請參閱[針對應用程式安裝問題進行疑難排解](./../apps/troubleshoot-app-install.md)和[針對 Win32 應用程式問題進行疑難排解](./../apps/troubleshoot-app-install.md#win32-app-installation-troubleshooting)。

#### <a name="app-status-details-for-ios-apps---3761235-----"></a>iOS 應用程式的應用程式狀態詳細資料<!-- 3761235   -->
新增下列應用程式安裝錯誤訊息：
- 在共用的 iPad 上安裝 VPP 應用程式時失敗
- 停用 App Store 時失敗
- 找不到應用程式的 VPP 授權
- 無法使用 MDM 提供者來安裝系統應用程式
- 裝置處於遺失模式或 kiosk 模式時，無法安裝應用程式
- 使用者未登入 App Store 時，無法安裝應用程式

在 Intune 中，選取 [用戶端應用程式]   > [應用程式]  >「應用程式名稱」> [裝置安裝狀態]  。 [狀態詳細資料]  欄將會提供新的錯誤訊息。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>在 Windows 10 版公司入口網站應用程式中新增 [應用程式類別] 畫面<!-- 3834780  -->
新增了稱為 [應用程式類別]  的畫面，以改善 Windows 10 版公司入口網站中的應用程式瀏覽和選取體驗。 使用者現在會看到其應用程式依類別排序，例如 [精選]  、[教育]  和 [生產力]  。 這項變更會出現在公司入口網站 10.3.3451.0 版和更新版本。 若要檢視新的畫面，請參閱[應用程式 UI 中的新功能](whats-new-app-ui.md)。 如需公司入口網站中應用程式的詳細資訊，請參閱[在裝置上安裝和共用應用程式](https://docs.microsoft.com/intune-user-help/install-apps-cpapp-windows)。  

#### <a name="power-bi-compliance-app---1455231-doc-work-item---"></a>Power BI 合規性應用程式<!-- 1455231 doc-work-item -->
在 Power BI Online 中使用 [Intune 合規性 (資料倉儲)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 應用程式，來存取您的 Intune 資料倉儲。 透過此 Power BI 應用程式中，您現在不需要任何設定也不需要離開網頁瀏覽器即可存取和共用預先建立的報表。 如需其他資訊，請參閱[變更記錄檔 - Power BI 合規性應用程式](../developer/reports-changelog.md#power-bi-compliance-app)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices---1862675-----"></a>PowerShell 指令碼可在 64 位元裝置上以 64 位元主機執行<!-- 1862675   -->
當您將 PowerShell 指令碼新增至裝置組態設定檔時，指令碼一律會以 32 位元執行，即使在 64 位元作業系統上也一樣。 在此更新中，系統管理員可以在 64 位元裝置上以 64 位元 PowerShell 主機執行指令碼 ([裝置設定]   > [PowerShell 指令碼]   > [新增]   > [設定]   > [Run script in 64 bit PowerShell Host] \(以 64 位元 PowerShell 主機執行指令碼\)  )。

如需使用 PowerShell 的詳細資料，請參閱 [Intune 中的 PowerShell 指令碼](../apps/intune-management-extension.md)。

適用於：Windows 10 及更新版本

#### <a name="macos-users-are-prompted-to-update-their-password---1873216---"></a>macOS 使用者會收到更新其密碼的提示<!-- 1873216 -->
Intune 將在 macOS 裝置上強制執行 **ChangeAtNextAuth** 設定。 此設定會影響具有合規性密碼原則或裝置限制密碼設定檔的終端使用者和裝置。 終端使用者會收到一次更新其密碼的提示。 每當使用者第一次執行需要驗證的工作時 (例如登入裝置)就會發生此提示。 當使用者執行任何需要系統管理權限的工作時 (例如要求 keychain 存取權)，也會收到更新其密碼的提示。

系統管理員所做的任何新的或現有密碼原則變更，都會再次提示終端使用者更新其密碼。

適用於：  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device---2340521------"></a>將 SCEP 憑證指派給無使用者的 macOS 裝置<!-- 2340521    -->
您可以使用裝置屬性將簡單憑證註冊通訊協定 (SCEP) 憑證指派給 macOS 裝置 (包括不具使用者親和性的裝置)，並建立憑證設定檔與 Wi-Fi 或 VPN 設定檔的關聯。 這會擴充我們已有的支援，以便[將 SCEP 憑證指派給具有和不具使用者親和性的裝置](../protect/certificates-profile-scep.md) (執行 Windows、iOS 和 Android)。  此更新會新增選項，可在您設定 macOS 的 SCEP 憑證設定檔時，選取 [裝置]  憑證類型。

適用於：
- macOS

#### <a name="intune-conditional-access-ui-update---2432313-----"></a>Intune 條件式存取 UI 更新<!-- 2432313   -->
我們已改善 Intune 主控台中的條件式存取 UI。 它們包括：
- 以 Azure Active Directory 中的刀鋒視窗取代 Intune [條件式存取]  刀鋒視窗。 這確保您可以從 Intune 主控台存取[條件式存取](../protect/conditional-access.md) (仍是 Azure AD 技術) 的完整設定和組態。 
- 我們已將 [內部部署存取]  刀鋒視窗重新命名為 [Exchange 存取]  ，並將 [Exchange 服務連接器]  設定重新放置到此重新命名的刀鋒視窗。  這項變更會整合您[設定和監視 Exchange Online 和內部部署相關詳細資料](../protect/exchange-connector-install.md)的位置。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode---2935135-----"></a>Kiosk 瀏覽器和 Microsoft Edge 瀏覽器應用程式可在 Windows 10 裝置上以 kiosk 模式執行<!-- 2935135   -->
您可以使用 kiosk 模式的 Windows 10 裝置來執行一或多個應用程式。 此更新包含在 kiosk 模式中使用瀏覽器應用程式的數項變更，包括：

- 新增 Microsoft Edge 瀏覽器或 Kiosk 瀏覽器以作為 kiosk 裝置上的應用程式執行 ([裝置設定]   > [設定檔]   > [新增設定檔]   > [Windows 10 及更新版本]  平台 > [Kiosk]  設定檔類型)。
- 可允許或限制的新功能和設定 ([裝置設定]   > [設定檔]   > [新增設定檔]   > [Windows 10 及更新版本]  平台 > [裝置限制]  設定檔類型)，包括：

- Microsoft Edge 瀏覽器：
  - 使用 Microsoft Edge kiosk 模式
  - 在閒置時間後重新整理瀏覽器

- 我的最愛和搜尋：
  - 允許變更搜尋引擎

如需這些設定的清單，請參閱：

- [讓 Windows 10 和更新版本的裝置設定以 kiosk 形式執行](../configuration/kiosk-settings-windows.md)
- [Microsoft Edge 瀏覽器裝置限制](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)
- [我的最愛和搜尋裝置限制](../configuration/device-restrictions-windows-10.md##favorites-and-search)

適用於：Windows 10 及更新版本

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices---3448774-----"></a>iOS 和 macOS 裝置的新裝置限制設定<!-- 3448774   -->
您可以在執行 iOS 和 macOS 的裝置上限制一些設定和功能 ([裝置設定]   > [設定檔]   > [新增設定檔]   > [iOS]  或 [macOS]  平台 > [裝置限制]  設定檔類型)。 此更新會新增您可以控制的更多功能和設定，包括在 macOS 裝置上設定螢幕使用時間，變更 eSIM 設定和行動數據方案等。 此外，您也可在 macOS 裝置上對使用者延遲顯示軟體更新，以及封鎖內容快取。

若要查看您可以限制的功能和設定，請參閱：

- [iOS 裝置限制設定](../configuration/device-restrictions-ios.md)
- [macOS 裝置限制設定](../configuration/device-restrictions-macos.md)

適用於：

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices---3598402-----"></a>"Kiosk" 裝置現在稱為 Android Enterprise 裝置的「專用裝置」<!-- 3598402   -->
為了配合 Android 術語，**kiosk** 已變更為 Android Enterprise 裝置的**專用裝置** ([裝置設定]   > [設定檔]   > [建立設定檔]  > [Android Enterprise] 平台 > [僅限裝置擁有者]   > [裝置限制]   > [專用裝置]  )。

若要查看可用的設定，請前往[允許或限制功能的裝置設定](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)。

適用於：  
Android 企業

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui---3640850-3803313-----"></a>Safari 及對使用者延遲顯示軟體更新等 iOS 設定將會移至 Intune UI<!-- 3640850, 3803313   -->
針對 iOS 裝置，您可以進行 Safari 設定及設定軟體更新。 在此更新中，這些設定將會移至 Intune UI 的不同部分：

- Safari 設定已從 [Safari]  ([裝置設定]   > [設定檔]   > [新增設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型) 移至 [[內建應用程式]](../configuration/device-restrictions-ios.md#built-in-apps)  。
- [Delaying user software update visibility for supervised iOS devices] \(對使用者延遲顯示受監督 iOS 裝置的軟體更新\)  設定 ([軟體更新]   > [更新 iOS 的原則]  ) 將會移至 [裝置限制]   > [[一般]](../configuration/device-restrictions-ios.md#general)  。  如需現有原則影響的詳細資訊，請參閱 [iOS 軟體更新](../protect/software-updates-ios.md#configure-the-policy)。

如需這些設定的清單，請參閱：

- [iOS 裝置限制](../configuration/device-restrictions-ios.md) 
- [iOS 軟體更新](../protect/software-updates-ios.md)

本功能適用於：

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices---3699164-----"></a>在 iOS 裝置上，[啟用裝置設定的限制] 已重新命名為 [螢幕使用時間]<!-- 3699164   -->
您可以在受監督的 iOS 裝置上設定 [啟用裝置設定的限制]  ([裝置設定]   > [設定檔]   > [新增設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型 > [一般]  )。 在此更新中，此設定已重新命名為 [螢幕使用時間 (僅限受監督)]  。

其行為完全一樣。 明確說來：

- iOS 11.4.1 和更早版本：[封鎖]  可防止終端使用者在裝置設定中設定自己的限制。 
- iOS 12.0 和更新版本：[封鎖]  可防止終端使用者在裝置設定中設定自己的 [螢幕使用時間]  ，包括內容與隱私權限制。 升級為 iOS 12.0 的裝置不會再於裝置設定中看到 [限制] 索引標籤。 這些設定位於 [螢幕使用時間]  中。 

如需這些設定的清單，請參閱 [iOS 裝置限制](../configuration/device-restrictions-ios.md#general)。

適用於：
- iOS


#### <a name="intune-powershell-module---951068----"></a>Intune PowerShell 模組<!-- 951068  -->
Intune PowerShell 模組透過 Microsoft Graph 支援 Intune API，現在於 [Microsoft PowerShell 資源庫](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)中提供使用。

- [如何使用此模組的相關詳細資料](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [使用此模組的案例範例](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization--3183757----"></a>改善傳遞最佳化的支援<!--3183757  -->
我們已在 Intune 中擴充設定傳遞最佳化的支援。 您現在可以直接從 Intune 主控台設定[傳遞最佳化設定](../configuration/delivery-optimization-settings.md)的擴充清單，並將它指定給您的裝置。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理

#### <a name="rename-an-enrolled-windows-device---1911112----"></a>重新命名已註冊的 Windows 裝置<!-- 1911112  -->
您現在可以重新命名已註冊的 Windows 10 裝置 (RS4 或更新版本)。 若要這樣做，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [重新命名裝置]  。 此功能目前不支援重新命名混合式 Azure AD Windows 裝置。

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope---3173823----"></a>自動將範圍標籤指派給管理員所建立並具有該範圍的資源<!-- 3173823  -->
當系統管理員建立資源時，任何指派給系統管理員的範圍標籤都會自動指派給這些新資源。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade---3560202----"></a>失敗的註冊報表會移至 [裝置註冊] 刀鋒視窗<!-- 3560202  -->
**註冊失敗**報表已移至 [裝置註冊]  刀鋒視窗的 [監視]  區段。 已新增兩欄 ([註冊方法] 和 [OS 版本])。

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments--3815076-eemiss---"></a>公司入口網站放棄報表已重新命名為 [未完成的使用者註冊]<!--3815076 eemiss -->
**公司入口網站放棄**報表已重新命名為 [未完成的使用者註冊]  。






<!-- ########################## -->
## <a name="january-2019"></a>2019 年 1 月

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>應用程式管理

#### <a name="intune-app-pin---2298397---"></a>Intune 應用程式 PIN<!-- 2298397 -->
身為 IT 系統管理員，您現在能設定終端使用者可在其 Intune 應用程式 PIN 必須變更之前等候的天數。 這項新設定稱為 [PIN reset after number of days] \(在數天後重設 PIN\)  ，並可在 Azure 入口網站中，藉由選取 [Intune]   > [用戶端應用程式]   > [應用程式防護原則]   > [建立原則]   > [設定]   > [存取需求]  來使用。 這項功能適用於 [iOS](../apps/app-protection-policy-settings-ios.md) 和 [Android](../apps/app-protection-policy-settings-android.md) 裝置，並支援正整數值。

#### <a name="intune-device-reporting-fields---2748738---"></a>Intune 裝置報告欄位<!-- 2748738 -->
Intune 提供其他裝置報告欄位，包括應用程式註冊識別碼、Android 製造商、型號和安全性修補程式版本，以及 iOS 型號。 在 Intune 中，您可以藉由選取 [用戶端應用程式]   > [應用程式防護狀態]  ，然後選擇 [應用程式防護報表：iOS、Android]  來使用這些欄位。 此外，這些參數將協助您設定適用於裝置製造商 (Android) 的 [允許]  清單、適用於裝置型號 (Android 和 iOS) 的 [允許]  清單，以及最低的 Android 安全性修補程式版本設定。

#### <a name="toast-notifications-for-win32-apps---3136566-----"></a>Win32 應用程式的快顯通知<!-- 3136566   -->
您可以隱藏而不顯示每個應用程式指派的終端使用者快顯通知。 從 Intune 選取 [用戶端應用程式]   > [應用程式]  > 選取應用程式 > [指派]   > [包含群組]  。

#### <a name="intune-app-protection-policies-ui-update---3251427----"></a>Intune 應用程式防護原則 UI 更新<!-- 3251427  -->
我們已變更 Intune 應用程式保護的設定和按鈕標籤，以使它們更容易理解。 部分變更包括：  
- 控制項從 [是]   / [否]  的控制項，變更成主要為 [封鎖]   / [允許]  ，以及 [停用]   / [啟用]  的控制項。 標籤也一併更新。  
- 設定已重新格式化，因此設定和其標籤會在控制項中並排顯示，提供更好的瀏覽。

預設設定和設定數量會保持相同，但這項變更可讓使用者更輕鬆了解、瀏覽和利用這些設定，以套用所選的應用程式保護原則。 如需詳細資訊，請參閱 [iOS 設定](../apps/app-protection-policy-settings-ios.md)和 [Android 設定](../apps/app-protection-policy-settings-android.md)。

#### <a name="additional-settings-for-outlook---3301182----"></a>Outlook 的其他設定<!-- 3301182  -->
您現在可以使用 Intune 來設定 iOS 和 Android 版 Outlook 的下列其他設定：

- 只允許在 iOS 和 Android 版 Outlook 中使用公司或學校帳戶
- 為 Office 365 和混合式新式驗證內部部署帳戶部署新式驗證
- 選取基本驗證時，針對電子郵件設定檔中的使用者名稱欄位使用 `SAMAccountName`
- 允許儲存連絡人
- 設定外部收件者郵件提示
- 設定 [焦點收件匣] 
- 需要生物識別技術才能存取 iOS 版 Outlook
- 封鎖外部影像

> [!NOTE]
> 如果您使用 Intune 應用程式防護原則來管理公司身分識別的存取權，您應該考慮不啟用 [require biometrics] \(需要生物識別技術\)  。 如需詳細資訊，請參閱 [iOS 存取設定](../apps/app-protection-policy-settings-ios.md#access-requirements)和 [Android 存取設定](../apps/app-protection-policy-settings-android.md#access-requirements)中的＜需要公司認證才能存取＞  。

如需詳細資訊，請參閱 [Microsoft Outlook 組態設定](../apps/app-configuration-policies-outlook.md)。

#### <a name="delete-android-enterprise-apps---1352553---"></a>刪除 Android Enterprise 應用程式<!-- 1352553 -->
您可以從 Microsoft Intune 刪除受控的 Google Play 應用程式。 若要刪除受控的 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [用戶端應用程式]   > [應用程式]  。 從應用程式清單，選取受控的 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]  。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

#### <a name="managed-google-play-app-type---1352580---"></a>受控的 Google Play 應用程式類型<!-- 1352580 -->
[受控的 Google Play]  應用程式類型可讓您將[受控的 Google Play 應用程式](https://play.google.com/work/search?q=microsoft&c=apps)特別新增至 Intune。 身為 Intune 系統管理員，您現在可以在 Intune 中瀏覽、搜尋、核准、同步及指派已核准之受控的 Google Play 應用程式。  您不再需要另外通過 Google Play 主控台瀏覽受控應用程式，而且您不再需要重新驗證。  在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [應用程式類型]  清單中，選取 [受控的 Google Play]  作為應用程式類型。

#### <a name="default-android-pin-keyboard---3802457---"></a>預設 Android PIN 鍵盤<!-- 3802457 -->
若終端使用者已在其 Android 裝置上設定 Intune 應用程式防護原則 (APP) PIN 且 PIN 類型為 [數值]，則現在會看到預設 Android 鍵盤，而不是先前所設計的固定 Android 鍵盤 UI。 這是為了在 Android 和 iOS 上使用預設鍵盤時能夠保持一致所做的變更，適用於 PIN 類型為 [數值] 及/或 [密碼]。 如需 Android 上終端使用者存取設定的詳細資訊，請參閱 [Android 存取需求](../apps/app-protection-policy-settings-android.md#access-requirements)。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>裝置設定

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>系統管理範本目前處於公開預覽狀態且已移至它們自己的組態設定檔 <!-- 3322847 -->

Intune 中的系統管理範本 ([裝置設定]   > [系統管理範本]  ) 目前為公開預覽狀態。 使用此更新：

- 系統管理範本包含約 300 個可在 Intune 中管理的設定。 這些設定先前只存在於群組原則編輯器中。
- 系統管理範本會在公開預覽版中提供。
- 系統管理範本正從 [裝置設定]   > [系統管理範本]  移至 [裝置設定]   > [設定檔]   > [建立設定檔]  > 在 [平台]  中選擇 [Windows 10 及更新版本]  > 在 [設定檔類型]  中選擇 [系統管理範本]  。
- 報告功能已啟用

若要深入了解這項功能，請前往[設定群組原則設定的 Windows 10 範本](../configuration/administrative-templates-windows.md)。

適用於：Windows 10 及更新版本

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user---1333642---"></a>使用 S/MIME 加密和簽署使用者的多部裝置<!-- 1333642 -->
此更新包括使用新匯入之憑證設定檔的 S/MIME 電子郵件加密 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 選取平台 > [PKCS imported certificate] \(PKCS 匯入的憑證\)  設定檔類型)。 在 Intune 中，您可以匯入 PFX 格式的憑證。 Intune 接著可以將這些相同的憑證提供給單一使用者所註冊的多個裝置。 這也包括：
- 原生 iOS 電子郵件設定檔支援啟用 PFX 格式之已匯入憑證的 S/MIME 加密。
- Windows Phone 10 裝置上的原生郵件應用程式會自動使用 S/MIME 憑證。
- 私人憑證可以跨多個平台提供。 但並非所有電子郵件應用程式都支援 S/MIME。
- 在其他平台上，您可能需要手動設定郵件應用程式來啟用 S/MIME。  
- 支援 S/MIME 加密的電子郵件應用程式可能會以 MDM 無法支援的方式來處理 S/MIME 電子郵件加密的憑證擷取 (例如從其發行者的憑證存放區中讀取)。
如需這項功能的詳細資訊，請參閱 [S/MIME 電子郵件簽署和加密概觀](../protect/certificates-s-mime-encryption-sign.md)。
支援於：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices---1333665-2999078---"></a>在 Windows 10 及更新版裝置上使用 DNS 設定時自動連線且持續規則的新選項<!-- 1333665, 2999078 -->
在 Windows 10 及更新版本裝置上，您可以建立 VPN 組態設定檔，其中包含可用以解析網域 (例如 contoso.com) 的 DNS 伺服器清單。 此更新包含可用於名稱解析的新設定 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [Windows 10 及更新版本]  > 針對設定檔類型選擇 [VPN]  > [DNS 設定]   >[新增]  )： 
- **自動連線**：若**已啟用**，裝置就會在連絡您輸入的網域 (例如 contoso.com) 時，自動連線至 VPN。
- **永續性**：根據預設，只要裝置會使用此 VPN 設定檔進行連線，所有的名稱解析原則表格 (NRPT) 規則都會處於作用中狀態。 已在 NRPT 規則上**啟用**此設定時，此規則就會在裝置上維持作用中狀態，即使在 VPN 中斷連線時也一樣。 規則將一直保留，直到移除 VPN 設定檔，或以手動方式移除規則，這可以透過使用 PowerShell 完成。
[Windows 10 VPN 設定](../configuration/vpn-settings-windows-10.md)將描述這些設定。

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices---1500165---"></a>針對 Windows 10 裝置上的 VPN 設定檔使用受信任的網路偵測<!-- 1500165 -->
使用受信任的網路偵測時，若使用者已經位於受信任的網路上，您可以防止 VPN 設定檔自動建立 VPN 連線。 在此更新中，您可以新增 DNS 尾碼，在執行 Windows 10 及更新版本之裝置上啟用受信任的網路偵測 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選擇 [Windows 10 及更新版本]  > 針對設定檔類型選擇 [VPN]  )。
[Windows 10 VPN 設定](../configuration/vpn-settings-windows-10.md)會列出目前的 VPN 設定。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users---1907917-1063203---"></a>管理多位使用者所使用的 Windows Holographic for Business 裝置<!-- 1907917, 1063203 -->
您目前可以使用自訂的 OMA-URI 設定，在 Windows 10 和 Windows Holographic for Business 裝置上設定共用的電腦設定。 在此更新中，會新增設定檔來設定共用的裝置設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]   > [共用的多重使用者裝置]  )。
若要深入了解這項功能，請前往[管理共用裝置的 Intune 設定](../configuration/shared-user-device-settings.md)。
適用於：Windows 10 及更新版本、Windows Holographic for Business

#### <a name="new-windows-10-update-settings--2626030--2512994----"></a>新的 Windows 10 更新設定<!--2626030  2512994  -->
針對 [Windows 10 更新通道](../protect/windows-update-for-business-configure.md)，您可以設定：
- **自動更新行為** - 使用新選項 [重設為預設]  ，在執行「2018 年 10 月更新」  的 Windows 10 電腦上還原原始的自動更新設定
- **防止使用者暫停 Windows 更新** - 設定新的軟體更新設定，可讓您封鎖或允許使用者從其電腦的 [設定]  暫停更新安裝。

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption---2662949---"></a>iOS 電子郵件設定檔可以使用 S/MIME 簽署和加密<!-- 2662949 -->
您可以建立包含不同設定的電子郵件設定檔。 此更新包含可在 iOS 裝置上用來簽署與加密電子郵件通訊的 S/MIME 設定 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [iOS]  > 針對設定檔類型選擇 [電子郵件]  )。
[iOS 電子郵件組態設定](../configuration/email-settings-ios.md)會列出這些設定。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>部分 BitLocker 設定支援 Windows 10 專業版<!-- 2727036 -->
您可以建立組態設定檔，在 Windows 10 裝置上設定 Endpoint Protection 設定，包括 BitLocker。 此更新會針對部分 BitLocker 設定新增對 Windows 10 專業版的支援。
若要查看這些保護設定，請前往[適用於 Windows 10 的 Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>共用裝置設定已在 Azure 入口網站中針對 iOS 裝置重新命名為鎖定畫面訊息<!-- 2809362 -->
當您建立適用於 iOS 裝置的組態設定檔時，您可以新增 [共用裝置設定]  設定，以便在鎖定畫面上顯示特定的文字。 此更新包含下列變更： 
- Azure 入口網站中的 [共用裝置設定]  已重新命名為「鎖定畫面訊息 (僅限受監督)」([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [iOS]  > 針對設定檔類型選擇 [裝置功能]  > [鎖定畫面訊息]  )。
- 新增鎖定畫面訊息時，您可以在 [資產標籤資訊]  和 [鎖定畫面註腳]  中插入序號、裝置名稱或另一個裝置特定的值以作為變數。 例如，您可以使用大括號來輸入 `Device name: {{devicename}}` 或 `Serial number is {{serialnumber}}`。 [iOS 權杖](../apps/app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)會列出可使用的可用權杖。
[在鎖定畫面上顯示訊息的設定](../configuration/ios-device-features-settings.md#lock-screen-message)會列出這些設定。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices---2827760--"></a>新增至 iOS 裝置的新 App Store、文件檢視、遊戲裝置限制設定<!-- 2827760-->
在 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型 > [App Store、文件檢視、遊戲]  中，新增下列設定：[允許受控應用程式將連絡人寫入非受控連絡人帳戶]、[允許非受控應用程式從受控連絡人帳戶讀取]。若要查看這些設定，請前往 [iOS 裝置限制](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices---3201839-3201843---"></a>將通知、提示和 Keyguard 設定新增至 Android Enterprise 裝置擁有者裝置<!-- 3201839 3201843 -->
以裝置擁有者身分執行時，此更新會包括 Android 企業裝置上的多個新功能。 若要使用這些功能，請前往 [裝置設定]   > [設定檔]   > [建立設定檔]  > 在 [平台]  中選擇 [Android 企業]  > 在 [設定檔類型]  中選擇 [僅限裝置擁有者]   > [裝置限制]  。

新功能包括：

- 停用系統通知的顯示，包括來電、系統警示、系統錯誤及更多功能。
- 針對第一次開啟的應用程式建議略過開始教學課程和提示。
- 停用進階的 Keyguard 設定，例如相機、通知、指紋解除鎖定及更多功能。

若要查看這些設定，請前往 [Android Enterprise 裝置限制設定](../configuration/device-restrictions-android-for-work.md)。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections---3202194---"></a>Android Enterprise 裝置擁有者裝置可以使用 Always On VPN 連線<!-- 3202194 -->
在此更新中，您可以在 Android 企業裝置擁有者裝置上使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選擇 [Android 企業]  > 針對 [僅限裝置擁有者] 選擇 [裝置限制]  > [連線能力]  設定中啟用 Always-On VPN。 若要查看這些設定，請前往 [Android Enterprise 裝置限制設定](../configuration/device-restrictions-android-for-work.md)。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices---3285177---"></a>Windows 10 裝置上工作管理員中用來結束處理序的新設定<!-- 3285177 --> 
此更新包含使用 Windows 10 裝置上的工作管理員來結束處理序的新設定。 您可以使用裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 在 [平台]  中選擇 [Windows 10]  > 在 [設定檔類型]  中選擇 [裝置限制]   > [一般]  設定)，來選擇允許或阻止此設定。
若要查看這些設定，請前往 [Windows 10 裝置限制設定](../configuration/device-restrictions-windows-10.md)。
適用於：Windows 10 及更新版本

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview---2055484-----"></a>使用針對安全性基準的 Microsoft 建議設定 (公開預覽)<!-- 2055484   -->

Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員可以直接從這些基準建立安全性政策，並將它們部署到其使用者。 您也可以自訂最佳做法建議項目，以符合您組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

這項功能處於公開預覽狀態，因此現在建立之任何設定檔都不會移至正式運作 (GA) 的安全性基準範本。 您不應該在生產環境中規劃使用這些預覽範本。

若要深入了解安全性基準，請參閱[在 Intune 中建立 Windows 10 安全性基準](../protect/security-baselines-monitor.md)。

本功能適用於：Windows 10 及更新版本

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>非系統管理員可在已加入 Azure AD 的 Windows 10 裝置上啟用 BitLocker<!-- 2147379   -->
當您在 Windows 10 裝置上啟用 BitLocker 設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選擇 [Windows 10 及更新版本]  > 針對設定檔類型選擇 [Endpoint Protection]  > [Windows 加密]  ) 時，您會新增 BitLocker 設定。

此更新包含新的 BitLocker 設定，可允許標準使用者 (非系統管理員) 啟用加密。

若要查看設定，請前往[適用於 Windows 10 的 Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="check-for-configuration-manager-compliance---2192052--eepublished----"></a>檢查 Configuration Manager 合規性<!-- 2192052  eepublished  -->
此更新會包括新的 Configuration Manager 合規性設定 ([裝置合規性]   > [原則]   > [建立原則]   > [Windows 10 及更新版本]   > [Configuration Manager 合規性]  )。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用此設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中就不會符合規範。

[Configuration Manager 合規性](../protect/compliance-policy-create-windows.md#configuration-manager-compliance)描述了這項設定。

適用於：Windows 10 及更新版本

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile---2809324-----"></a>使用裝置組態設定檔自訂受監督 iOS 裝置上的背景圖案<!-- 2809324   -->
當您建立 iOS 裝置的裝置組態設定檔時，您可以自訂某些功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [裝置功能]  設定檔類型)。 此更新包括新的**桌布**設定，可讓系統管理員在主畫面或鎖定畫面上使用 .png、.jpg 或 .jpeg 影像。 這些桌布設定只會套用至受監督的裝置。 

如需這些設定的清單，請參閱 [iOS 裝置功能設定](../configuration/ios-device-features-settings.md)。

#### <a name="windows-10-kiosk-is-generally-available---3594661----"></a>Windows 10 kiosk 已正式運作<!-- 3594661  -->
在此更新中，在 Windows 10 和更新版本的裝置上的 [Kiosk] 功能是正式推出 (GA)。 若要查看您可以新增和設定的所有設定，請參閱[適用於 Windows 10 (和更新版本) 的 Kiosk 設定](../configuration/kiosk-settings.md)。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise---3598396-----"></a>[透過藍牙分享連絡人] 已從 Android Enterprise 的 [裝置限制] > [裝置擁有者] 中移除<!-- 3598396   -->
當您建立 Android Enterprise 裝置的裝置限制設定檔時，有一項 [透過藍牙分享連絡人]  設定。 在此更新中，[透過藍牙分享連絡人]  設定會被移除 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android 企業]  平台 > [裝置限制] > [裝置擁有者]  設定檔類型 > [一般]  )。

Android Enterprise 裝置擁有者管理不支援 [透過藍牙分享連絡人]  設定。 因此，移除此設定之後，並不會影響任何裝置或租用戶，即使您已在環境中啟用和設定此設定亦然。

若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](../configuration/device-restrictions-android-for-work.md)。

適用於：Android Enterprise 裝置擁有者


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>裝置註冊

#### <a name="more-detailed-enrollment-restriction-failure-messaging---3111564---"></a>更詳細的註冊限制失敗訊息<!-- 3111564 -->
不符合註冊限制時，會提供更詳細的錯誤訊息。 若要查看這些訊息，請前往 [Intune]   > [疑難排解]  > 然後檢查 [註冊失敗] 表格。 如需詳細資訊，請參閱[註冊失敗清單](help-desk-operators.md#enrollment-failure-reference)。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>裝置管理
#### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices---1574342----"></a>公司擁有且完全受控的 Android 裝置支援預覽<!-- 1574342  -->
Intune 現在支援完全受控的 Android 裝置，此為公司擁有的「裝置擁有者」案例，其中的裝置會受到 IT 嚴格管理並隸屬於個別使用者。 這讓系統管理員能夠管理整個裝置、強制設定無法用於工作設定檔之原則控制項的延伸範圍，並限制使用者只能從受控的 Google Play 安裝應用程式。 如需詳細資訊，請參閱[設定 Android 完全受控裝置的 Intune 註冊](../enrollment/android-fully-managed-enroll.md)與[註冊您的專用裝置或完全受控裝置](../enrollment/android-dedicated-devices-fully-managed-enroll.md)。  請注意，此功能處於預覽狀態。 完全受控的 Android 使用者裝置目前不提供某些 Intune 功能，例如憑證、合規性和條件式存取。

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices---1434452---"></a>WIP (不含註冊) 裝置的選擇性抹除支援<!-- 1434452 -->
Windows 資訊保護 (不含註冊) (WIP-WE) 允許客戶保護其 Windows 10 裝置上的公司資料，而不需要完整的 MDM 註冊。 一旦文件受 WIP-WE 原則保護，受保護的資料就可以由 Intune 系統管理員選擇性抹除。 透過選取使用者與裝置並傳送抹除要求，透過 WIP-WE 原則保護的所有資料都會變成無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式]   > [應用程式選擇性抹除]  。


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="tenant-status-dashboard---1124854---"></a>租用戶狀態儀表板<!-- 1124854 -->
新的[租用戶狀態頁面](tenant-status.md)提供可讓您檢視租用戶狀態和相關詳細資料的單一位置。  此儀表板分成四個區域：
- **租用戶詳細資料** - 顯示資訊，包括您的租用戶名稱和位置、您的 MDM 授權單位、您租用戶中的總註冊裝置數，以及您的授權計數。 此區段也會列出您租用戶目前的服務版本。
- **連接器狀態** - 顯示您已設定的可用連接器相關資訊，也可能會列出尚未啟用的連接器。  
   每個連接器會根據其目前狀態，標記為 [狀況良好]、[警告] 或 [狀況不良]。 選取一個連接器以鑽研並檢視詳細資料，或為它設定其他資訊。
- **Intune 服務健全狀況** - 顯示您租用戶的作用中事件或中斷相關詳細資料。 此區段中的資訊是直接從 Office 訊息中心所擷取。
- **Intune 新聞** - 顯示您租用戶的作用中訊息。 包括您的租用戶收到最新 Intune 功能時的通知等訊息。  此區段中的資訊是直接從 Office 訊息中心所擷取。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10---1488939--"></a>Windows 10 公司入口網站中的新說明及支援體驗<!-- 1488939-->
新的公司入口網站 [說明及支援] 頁面協助使用者為應用程式和存取問題進行疑難排解，並要求協助。 他們可以從此新頁面，傳送有關錯誤和診斷記錄詳細資料的電子郵件，並找到其組織的技術服務人員詳細資料。 他們也將找到 [常見問題集] 區段，其中含有相關 Intune 文件的連結。

#### <a name="new-help-and-support-experience-for-intune---3307080---"></a>Intune 的新說明及支援體驗<!-- #3307080 -->
我們將於未來幾天為所有租用戶推出新的 [說明及支援] 體驗。 此新體驗適用於 Intune，並可在使用 [Azure 入口網站](https://portal.azure.com/)中的 Intune 刀鋒視窗時存取。
新體驗可讓您用自己的文字描述問題，並收到疑難排解深入解析和網站型修復內容。 這些解決方案透過規則型的機器學習演算法提供，由使用者查詢所驅動。 除了特定問題的指導之外，您也可以使用新的案例建立工作流程，透過電子郵件或電話來開啟支援案例。 此新體驗會取代一組靜態預先選取選項的舊版 [說明及支援] 體驗，這些選項是以您開啟 [說明及支援] 時所在控制台的區域為依據。
如需詳細資訊，請參閱[如何取得 Microsoft Intune 支援](get-support.md)。

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services---3762211----"></a>新的作業記錄，以及將記錄傳送至 Azure 監視器服務的能力<!-- 3762211  -->
Intune 具有內建稽核記錄，可在進行變更時追蹤事件。 此更新包含新的記錄功能，包括： 
- 作業記錄 (預覽)，顯示已註冊的使用者和裝置的詳細資料，包括成功和失敗的嘗試。
- 稽核記錄和作業記錄也可傳送到 Azure 監視器，包括儲存體帳戶、事件中樞和 Log Analytics。 這些服務可讓您儲存、使用 Splunk 和 QRadar 等分析，並取得記錄資料的視覺效果。

[將記錄資料傳送至 Intune 中的儲存體、事件中樞或記錄分析](../review-logs-using-azure-monitor.md)提供這項功能的詳細資訊。

#### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device---2687509----"></a>在 iOS DEP 裝置上略過更多設定助理畫面<!-- 2687509  -->
除了您目前可以略過的畫面之外，當使用者註冊裝置時，您還可以將 iOS DEP 裝置設定為略過 [設定助理] 中的下列畫面：顯示色調、隱私權、Android 移轉、首頁按鈕、iMessage 和 FaceTime、上架、Watch 移轉、外觀、螢幕使用時間、軟體更新、SIM 卡設定。
若要選擇要略過的畫面，請前往 [裝置註冊]   > [Apple 註冊]   > [註冊方案權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [屬性]   > [設定助理自訂]  > 針對任何您想要略過的畫面選擇 [隱藏]  > [確定]  。
如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。 使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。

#### <a name="android-enterprise-app-we-app-deployment---1171203---"></a>Android Enterprise APP-WE 應用程式部署<!-- 1171203 -->
針對未註冊之無註冊應用程式防護原則 (APP-WE) 部署案例中的 Android 裝置，您現在可以使用受控的 Google Play，將市集應用程式和 LOB 應用程式部署給使用者。 具體來說，您可以為終端使用者提供應用程式目錄和安裝體驗，藉由允許從不明來源進行安裝，就不再需要終端使用者放寬其裝置的安全性狀態。 此外，此部署案例將提供已改善的使用者體驗。

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="scope-tags-for-apps---1081941---"></a>應用程式的範圍標籤<!-- 1081941 -->
您可以建立範圍標籤，限制對角色和應用程式的存取。 您可以將範圍標籤新增至應用程式，僅限具有角色並同時獲派該範圍標籤的人員才能存取應用程式。 目前無法將範圍標籤指派給從受控 Google Play 加入至 Intune 的應用程式，或是使用 Apple 大量採購方案 (VPP) 購買的應用程式 (已規劃於未來提供支援)。 如需詳細資訊，請參閱[使用範圍標籤篩選原則](scope-tags.md)。




<!-- ########################## -->
## <a name="december-2018"></a>2018 年 12 月

### <a name="app-management"></a>應用程式管理

#### <a name="updates-for-application-transport-security---748318---"></a>更新 Application Transport Security<!-- 748318 -->

Microsoft Intune 支援傳輸層安全性 (TLS) 1.2+ 來提供業界領先的加密功能，以確保 Intune 預設更安全，並可搭配 Microsoft Office 365 等其他 Microsoft 服務使用。 為了符合此需求，iOS 和 macOS 公司入口網站將會強制執行 Apple 的更新 Application Transport Security (ATS) 需求，這些需求也要求使用 TLS 1.2+。 ATS 可用來對透過 HTTPS 通訊的所有應用程式強制執行更嚴格的安全性。 此變更會影響使用 iOS 和 macOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請參閱 [Intune 支援小組部落格](https://aka.ms/compportalats) \(英文\)。

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys---1832174---"></a>Intune App SDK 將支援 256 位元的加密金鑰<!-- 1832174 -->
適用於 Android 的 Intune App SDK 現在會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 SDK 將繼續提供 128 位元金鑰的支援，以取得與使用較舊 SDK 版本之內容和應用程式的相容性。

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices---3503442---"></a>macOS 裝置需要 Microsoft 自動更新版本 4.50<!-- 3503442 -->
若要繼續接收公司入口網站和其他 Office 應用程式的更新，Intune 所管理的 macOS 裝置必須先升級到 Microsoft 自動更新 4.5.0。 使用者可能已經擁有此版本的 Office 應用程式。

### <a name="device-management"></a>裝置管理

#### <a name="intune-requires-macos-1012-or-later---2827778---"></a>Intune 需要 macOS 10.12 或更新版本<!-- 2827778 -->
Intune 現在需要 macOS 版本 10.12 或更新版本。 使用先前的 macOS 版本的裝置無法使用公司入口網站來註冊 Intune。 為了收到支援協助和新功能，使用者必須將其裝置升級至 macOS 10.12 或更新版本，並將公司入口網站升級至最新版本。

<!-- ########################## -->
## <a name="november-2018"></a>2018 年 11 月

### <a name="app-management"></a>應用程式管理

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices---1281677---"></a>在公司擁有的受監督 iOS 裝置上解除安裝應用程式<!-- 1281677 -->
您可以移除公司所擁有之受監督 iOS 裝置上的任何應用程式。 您可以透過針對具有**解除安裝**指派類型的使用者或裝置群組，來移除任何應用程式。 針對個人或不受監督的 iOS 裝置，您仍可以僅移除使用 Intune 安裝的應用程式。

#### <a name="downloading-intune-win32-app-content---2617320---"></a>下載 Intune Win32 應用程式內容<!-- 2617320 -->
Windows 10 RS3 和更新版本的用戶端，將會使用 Windows 10 用戶端上的「傳遞最佳化」元件來下載 Intune Win32 應用程式內容。 傳遞最佳化能提供預設開啟的點對點功能。 目前傳遞最佳化可以由群組原則進行設定。 如需詳細資訊，請參閱[適用於 Windows 10 的傳遞最佳化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) \(部分機器翻譯\)。

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>終端使用者裝置和應用程式內容功能表<!-- 2771453 -->
終端使用者現在可以在裝置和應用程式上使用操作功能表，以觸發重新命名裝置或檢查合規性等常見動作。

#### <a name="set-custom-background-in-managed-home-screen-app----3041945---"></a>在受控主畫面應用程式中設定自訂背景 <!-- 3041945 -->
我們將新增一項設定，可讓您在 Android Enterprise、多應用程式、kiosk 模式裝置上自訂受控主畫面應用程式的背景外觀。  若要設定**自訂 URL 背景**，請前往 Azure 入口網站 > [裝置設定] 中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](../configuration/device-restrictions-android-for-work.md)。

#### <a name="app-protection-policy-assignment-save-and-apply---3104570---"></a>會儲存並套用應用程式防護原則指派<!-- 3104570 -->
您將可以更有效控制[應用程式保護原則指派](../apps/app-protection-policies.md)。 當您選取 [指派]  以設定或編輯某個原則的指派時，您必須先 [儲存]  設定，系統才會套用變更。 使用 [捨棄]  來清除您所做的所有變更，而不將任何變更儲存到包含或排除清單。  透過要求使用者進行 [儲存] 或 [捨棄]，將能確保系統只會將應用程式保護原則指派給您想要的使用者。

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later---3174639---"></a>適用於 Windows 10 及更新版本的新 Microsoft Edge 瀏覽器設定<!-- 3174639 -->
此更新將會包含新的設定，以協助您控制和管理裝置上的 Microsoft Edge 瀏覽器。 如需這些設定的清單，請參閱[適用於 Windows 10 (及更新版本) 的裝置限制](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)。

#### <a name="new-apps-support-with-app-protection-policies---3330037---"></a>搭配應用程式防護原則的新應用程式支援<!-- 3330037 -->
您現在可以搭配 [Intune 應用程式保護原則](../apps/app-protection-policies.md)管理下列應用程式：
- Stream (iOS)
- To DO (Android、iOS)
- PowerApps (Android、iOS)
- Flow (Android、iOS)

使用應用程式保護原則來保護公司資料，並以和其他 Intune 原則受管理的應用程式相同的方式控制這些應用程式的資料傳輸。 附註：如果 Flow 在主控台中尚不可見，您可在建立或編輯應用程式保護原則時新增 Flow。 若要這麼做，請使用 [+ 更多應用程式]  選項，然後在輸入欄位中指定 Flow 的 [應用程式識別碼]  。 針對 Android，請使用 *com.microsoft.flow*，而針對 iOS 則請使用 *com.microsoft.procsimo*。


### <a name="device-configuration"></a>裝置設定

#### <a name="support-for-ios-12-oauth-in-ios-email-profiles--2155106---"></a>在 iOS 電子郵件設定檔中支援 iOS 12 OAuth<!--2155106 -->
Intune 的 iOS 電子郵件設定檔支援 iOS 12 Open Authorization (OAuth)。 若要查看此功能，請建立新的設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [電子郵件]  作為設定檔類型)，或更新現有的 iOS 電子郵件設定檔。 如果您在已部署給使用者的設定檔中啟用 OAuth，則會提示使用者重新驗證，並再次下載其電子郵件。

[iOS 電子郵件設定檔](../configuration/email-settings-ios.md)會包含有關在電子郵件設定檔中使用 OAuth 的詳細資訊。

#### <a name="network-access-control-nac-support-for-citrix-sso-for-ios---3259404---"></a>網路存取控制 (NAC) 針對 iOS 支援 Citrix SSO<!-- 3259404 -->
Citrix 已發行 Citrix Gateway 更新以允許 Intune 中 iOS 的 Citrix SSO 的網路存取控制 (NAC)。 您可以在 Intune 中選擇在 VPN 設定檔中包括裝置識別碼，然後將此設定檔推送到您的 iOS 裝置。 您將必須安裝最新的更新到 Citrix Gateway，才能使用此功能。

[在 iOS 裝置上設定 VPN 設定](../configuration/vpn-settings-ios.md#base-vpn-settings)提供有關使用 NAC 的詳細資訊，包括一些額外需求。 

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown---1892471---"></a>顯示 iOS 和 macOS 版本號碼和組建編號<!-- 1892471 -->
在 [裝置合規性]   > [裝置合規性]  中，會顯示 iOS 和 macOS 作業系統版本，並可用於合規性政策。 此更新包含可同時針對兩個平台設定的組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 藉由在合規性政策中使用組建編號，即可輕鬆地檢查是否已安裝弱點更新。
若要使用此功能，請參閱 [iOS](../protect/compliance-policy-create-ios.md#device-health) 和 [macOS](../protect/compliance-policy-create-mac-os.md#device-properties) 合規性原則。

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later---2753807---"></a>針對 Windows 10 及更新版本，更新通道將由傳遞最佳化設定取代<!-- 2753807 -->
傳遞最佳化是適用於 Windows 10 和更新版本的新組態設定檔。 此功能可提供更加流暢的使用體驗，以將軟體更新傳遞到您組織中的裝置。 此更新也能協助您使用組態設定檔，在新的與現有的更新通道中傳遞設定。
若要設定傳遞最佳化組態設定檔，請參閱 [Windows 10 (和更新版本) 的傳遞最佳化設定](../configuration/delivery-optimization-windows.md)。

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices---2827760---"></a>新增至 iOS 和 macOS 裝置的新裝置限制設定<!-- 2827760 -->
此更新包含適用於 iOS 和 macOS 裝置，與 iOS 12 所發行的新設定：

**iOS 設定**： 
- 一般：封鎖應用程式移除 (僅限受監督)
- 一般：封鎖 USB 限制模式 (僅限受監督)
- 一般：強制自動日期和時間 (僅限受監督)
- 密碼：封鎖密碼自動填入 (僅限受監督)
- 密碼：封鎖密碼鄰近性要求 (僅限受監督)
- 密碼：封鎖密碼共用 (僅限受監督)

**macOS 設定**： 
- 密碼：防止自動填滿密碼
- 密碼：封鎖密碼鄰近性要求
- 密碼：防止共用密碼

若要深入了解這些設定，請參閱 [iOS](../configuration/device-restrictions-ios.md) 和 [macOS](../configuration/device-restrictions-macos.md) 裝置限制設定。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview---1048100--"></a>已加入混合式 Azure Active Directory 裝置的 Autopilot 支援 (預覽)<!-- 1048100-->
您現在可以透過使用 Autopilot，來設定混合式 Azure Active Directory 聯結裝置。 裝置必須聯結到您組織的網路，才能使用混合式 Autopilot 功能。 如需詳細資訊，請參閱[使用 Intune 和 Windows Autopilot 部署混合式 Azure AD 聯結裝置](../enrollment/windows-autopilot-hybrid.md)。
此功能將在未來幾天內在整個使用者群中推出。 因此，在推出至您的帳戶之前，您可能無法執行這些步驟。

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>選取註冊狀態頁面上追蹤的應用程式<!-- 2531007 -->
您可以選擇要在註冊狀態頁面上追蹤哪些應用程式。 在安裝這些應用程式之前，使用者將無法使用該裝置。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。

#### <a name="search-for-autopilot-device-by-serial-number--2595788---"></a>依序號搜尋 Autopilot 裝置<!--2595788 -->
您現在可以依序號搜尋 Autopilot 裝置。 若要這麼做，請選擇 [裝置註冊]   > [Windows 註冊]   > [裝置]  > 在 [依序號搜尋]  方塊中輸入序號 > 按 Enter。

#### <a name="track-installation-of-office-proplus--2620217---"></a>追蹤 Office 專業增強版的安裝<!--2620217 -->
使用者可以使用[註冊狀態頁面](../enrollment/windows-enrollment-status.md)來追蹤 [Office 專業增強版](../apps/apps-add-office365.md)的安裝進度。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low---2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

#### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts--3006133---"></a>Apple School Manager 帳戶的 macOS 裝置註冊計劃<!--3006133 -->
Intune 現已支援在適用於 Apple School Manager 帳戶的 macOS 裝置上使用裝置註冊計劃。  如需詳細資訊，請參閱[使用 Apple School Manager 或裝置註冊計劃來自動註冊 macOS 裝置](../enrollment/device-enrollment-program-enroll-macos.md)。

#### <a name="new-intune-device-subscription-sku--3312071--"></a>新的 Intune 裝置訂閱 SKU<!--3312071-->
為了協助降低企業中的裝置管理裝置成本，現在提供新的裝置型訂閱 SKU。 此 Intune 裝置 SKU 是依每月每部裝置來授權。 價格會因授權方案而有所不同。 它可直接透過 Microsoft 365 系統管理中心，以及透過 [Enterprise 合約](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA)、[Microsoft 產品和服務合約](https://www.microsoft.com/licensing/mpsa/default) (MPSA)、[Microsoft Open Agreement](https://partner.microsoft.com/licensing/licensing-agreements) 和[雲端解決方案提供者](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) 提供使用。

### <a name="device-management"></a>裝置管理

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes---3041935---"></a>暫停 Android 裝置上的 kiosk 模式以進行變更<!-- 3041935 -->
在多應用程式 kiosk 模式下使用 Android 裝置時，IT 系統管理員可能需要對裝置進行變更。 此更新包含新的多應用程式 kiosk 設定，允許 IT 系統管理員使用 PIN 暫時暫停 kiosk 模式，並存取整個裝置。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](../configuration/device-restrictions-android-for-work.md)。

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices----3042021---"></a>啟用 Android Enterprise kiosk 裝置上的虛擬首頁按鈕 <!-- 3042021 -->
新設定可讓使用者點選其裝置上的螢幕按鍵按鈕，以在其多應用程式 kiok 裝置上的受控主畫面應用程式和其他已指派應用程式之間切換。 在使用者的 kiosk 應用程式未對「返回」按鈕做出適當回應情況下，此設定特別有用。 您將能夠為公司擁有的一次性 Android 裝置設定此設定。 若要啟用或停用**虛擬首頁按鈕**，請前往 Azure 入口網站 > 裝置設定中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](../configuration/device-restrictions-android-for-work.md)。




<!-- ########################## -->
## <a name="october-2018"></a>2018 年 10 月

### <a name="app-management"></a>應用程式管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app---772203---"></a>使用公司入口網站應用程式存取重要設定檔屬性<!-- 772203 -->
終端使用者現在可以從公司入口網站應用程式，存取重要帳戶屬性和動作，例如密碼重設。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios---1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤<!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices---1248496---"></a>受控 Android 和 iOS 裝置上的 Intune 應用程式使用者帳戶存取<!-- 1248496 -->
身為 Microsoft Intune 系統管理員，您可以控制在受控裝置上要新增至 Microsoft Office 應用程式的使用者帳戶。 您可以僅允許組織使用者帳戶進行存取，並封鎖已註冊裝置上的個人帳戶。 

#### <a name="outlook-ios-and-android-app-configuration-policy--1828527---"></a>Outlook iOS 和 Android 應用程式設定原則<!--1828527 -->
您現在可以為透過 ActiveSync 通訊協定利用基本驗證的內部部署使用者，建立適用於 iOS 和 Android 的 Outlook iOS 及 Android 應用程式設定原則。 其他組態設定會隨著我們針對 iOS 和 Android 版 Outlook 啟用它們之後新增。

#### <a name="office-365-pro-plus-language-packs---1833450---"></a>Office 365 Pro Plus 語言套件<!-- 1833450 -->
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune]   > [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [新增應用程式]  刀鋒視窗的 [應用程式類型]  清單中，選取 [Office 365 套件]  下的 [Windows 10]  。 選取 [應用程式套件設定]  刀鋒視窗中的 [語言]  。

#### <a name="windows-line-of-business-lob-apps-file-extensions---1884873---"></a>Windows 企業營運 (LOB) 應用程式副檔名<!-- 1884873 -->
Windows LOB 應用程式的副檔名現在包含 *.msi*、 *.appx*、 *.appxbundle*、 *.msix* 和 *.msixbundle*。 您可以依序選取 [用戶端應用程式]   > [應用程式]   > [新增]  ，在 Microsoft Intune 中新增應用程式。 隨即顯示 [新增應用程式]  窗格，讓您可以選取 [應用程式類型]  。 針對 Windows LOB 應用程式，選取 [企業營運]  應用程式作為應用程式類型，並選取 [應用程式套件檔案]  ，然後輸入具有適當副檔名的安裝檔。

#### <a name="windows-10-app-deployment-using-intune---2309001---"></a>使用 Intune 進行 Windows 10 應用程式部署<!-- 2309001 -->
以企業營運 (LOB) 應用程式和商務用 Microsoft Store 應用程式的現有支援為基礎，系統管理員可以使用 Intune 將其組織的大部分現有應用程式部署到 Windows 10 裝置上的終端使用者。 系統管理員可以使用各種格式 (例如 MSI、Setup.exe 或 MSP)，為 Windows 10 的使用者新增、安裝及解除安裝應用程式。 Intune 會在下載和安裝之前評估需求規則，並使用 Windows 10 控制中心通知終端使用者狀態或重新開機需求。 這項功能會有效率地解除封鎖想要將此工作負載轉移到 Intune 和雲端的組織。 這項功能目前處於公開預覽狀態，我們預期在接下來的幾個月內在該功能中新增重要的新功能。 

#### <a name="app-protection-policy-app-settings-for-web-data---2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定<!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。 

#### <a name="end-user-device-and-app-content-menu---2771453---"></a>終端使用者裝置和應用程式內容功能表<!-- 2771453 -->
終端使用者現在可以使用裝置和應用程式上的操作功能表來觸發常見動作，例如重新命名裝置或檢查合規性。 

#### <a name="windows-company-portal-keyboard-shortcuts---2771518---"></a>Windows 公司入口網站鍵盤快速鍵<!-- 2771518 -->
終端使用者現在能夠於 Windows 公司入口網站中使用鍵盤快速鍵觸發程序應用程式和裝置動作。

#### <a name="require-non-biometric-pin-after-a-specified-timeout---1506985---"></a>在指定的逾時之後要求非生物特徵辨識 PIN<!-- 1506985 -->
透過在系統管理員指定的逾時之後要求非生物特徵辨識 PIN，Intune 可藉由限制使用生物特徵辨識身分識別來存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法，來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置，可能會向不正確使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]  。 選取 [用戶端應用程式]   > [應用程式保護原則]   > [新增原則]   > [設定]  。 找出特定設定的 [存取]  區段。 如需存取設定的資訊，請參閱 [iOS 設定](../apps/app-protection-policy-settings-ios.md#access-requirements)和 [Android 設定](../apps/app-protection-policy-settings-android.md#access-requirements)。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices---2244713---"></a>iOS MDM 註冊裝置上的 Intune 應用程式資料轉送設定<!-- 2244713 -->
您可以將已註冊 iOS MDM 裝置上 Intune 應用程式資料轉送設定的控制，與指定已註冊使用者的身分識別 (也稱為使用者主體名稱 (UPN)) 區分開來。 不使用 IntuneMAMUPN 的系統管理員將不會發現行為變更。 當此功能可用時，使用 IntuneMAMUPN 來控制已註冊裝置上資料轉送行為的系統管理員，應檢閱新的設定並視需要更新其應用程式設定。

#### <a name="windows-10-win32-apps---2617325---"></a>Windows 10 Win32 應用程式<!-- 2617325 -->
您可以設定 Win32 應用程式在個別 使用者的使用者內容中安裝，而不是為裝置的所有使用者安裝應用程式。

#### <a name="windows-win32-apps-and-powershell-scripts---2617330---"></a>Windows Win32 應用程式和 PowerShell 指令碼<!-- 2617330 -->
終端使用者已不再需要登入裝置來安裝 Win32 應用程式或執行 PowerShell 指令碼。 

#### <a name="troubleshooting-client-app-installation---1363711---"></a>針對用戶端應用程式安裝進行疑難排解<!-- 1363711 -->
您可以藉由檢閱 [疑難排解]  刀鋒視窗中標示為 [應用程式安裝]  的資料行，來為用戶端應用程式的安裝成功問題進行疑難排解。 若要檢視 [疑難排解]  刀鋒視窗，請在 Intune 入口網站中的 [說明及支援]  下選取 [疑難排解]  。

### <a name="device-configuration"></a>裝置設定

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>在執行 Windows 10 的裝置上於 VPN 組態設定檔中建立 DNS 尾碼<!-- 1333668 -->
當您建立 VPN 裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [VPN]  設定檔類型) 時，您需要輸入一些 DNS 設定。 透過此更新，您也可以在 Intune 中輸入多個 **DNS 尾碼**。 使用 DNS 尾碼時，您可以使用其簡短名稱來搜尋網路資源，而不需使用完整網域名稱 (FQDN)。 此更新也可讓您在 Intune 中變更 DNS 尾碼的順序。
[Windows 10 VPN 設定](../configuration/vpn-settings-windows-10.md#dns-settings)列出目前的 DNS 設定。
適用於：Windows 10 裝置

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles---1333705---"></a>適用於 Android 企業工作設定檔的 Always-On VPN 支援<!-- 1333705 -->
在此更新中，您將可以在 Android 企業裝置上搭配受控的工作設定檔來使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定]   > [設定檔]   > [建立設定檔]   > [Android 企業]  平台 > [裝置限制]   > [連線能力]  設定中啟用 Always-On VPN。

#### <a name="issue-scep-certificates-to-user-less-devices---1744554---"></a>將 SCEP 憑證發給無使用者的裝置<!-- 1744554 -->
目前憑證只能發給使用者。 透過此更新，您能夠將 SCEP 憑證發給裝置，包括 kiosk 等無使用者的裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [SCEP 憑證]  設定檔)。 其他更新包括：
- SCEP 設定檔中的 [主體]  屬性現已是自訂的文字方塊，且可以包含新的變數。 
- SCEP設定檔中的 [主體別名 (SAN)]  屬性現已是表格格式，且可以包含新的變數。 系統管理員可以在表格中新增屬性，並在自訂的文字方塊中填入值。 SAN 將支援下列屬性： 
  - DNS
  - 電子郵件地址
  - UPN

  您將能夠在自訂值文字方塊中以靜態文字新增這些新屬性。 例如，DNS 屬性可以新增為 `DNS = {{AzureADDeviceId}}.domain.com`。

  > [!NOTE]
  > 大括弧、分號和直立線符號「{ } ; |」在 SAN 的靜態文字中沒有作用。 大括弧只能括住其中一個新的裝置憑證變數，`Subject` 或 `Subject alternative name` 才會接受它。 

新的裝置憑證變數：  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
> - `{{FullyQualifiedDomainName}}` 只適用於 Windows 和已加入網域的裝置。 
> - 在裝置憑證的主體或 SAN 中指定 IMEI、序號和完整網域名稱等裝置屬性時，請留意這些屬性可能會被能夠存取該裝置的人員竄改。 

[建立 SCEP 憑證設定檔](../protect/certificates-profile-scep.md#create-a-scep-certificate-profile)列出目前在建立 SCEP 組態設定檔時的變數。 

適用於：Windows 10 及更新版本和 iOS (支援 Wi-Fi)

#### <a name="remotely-lock-uncompliant-devices---2064495---"></a>從遠端鎖定不符合規範的裝置<!-- 2064495 -->
當裝置不符合規範時，您可以在合規性原則上建立從遠端鎖定該裝置的動作。 在 Intune > [裝置合規性]  中建立新原則或選取現有的原則 > [屬性]  。 選取 [因不符合規範而採取的動作]   > [新增]  ，然後選擇以從遠端鎖定裝置。
支援於： 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 和更新版本 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal---2748224---"></a>Azure 入口網站中針對 Windows 10 及更新版本 Kiosk 設定檔的改善<!-- 2748224 -->
此更新包含下列對 Windows 10 Kiosk 裝置設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [Kiosk 預覽]  設定檔類型) 的改善： 
- 目前，您可以在相同的裝置上建立多個 Kiosk 設定檔。 透過此更新，Intune 針對每部裝置都只會支援單一 Kiosk 設定檔。 如果您仍需要在單一裝置上有多個 Kiosk 設定檔，則可以使用自訂 URI。
- 在 [多應用程式 kiosk]  設定檔中，您可以針對應用程式格線中的 [[開始] 功能表配置]  選取應用程式磚大小和順序。 如果您想要取得更多自訂項目，您可以繼續上傳 XML 檔案。
- [Kiosk 瀏覽器] 設定會移至 [Kiosk]  設定中。 目前，[Kiosk 網頁瀏覽器]  設定在 Azure 入口網站中具有自己的類別。
適用於：Windows 10 及更新版本

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device----2637704----"></a>當您變更 iOS 裝置上的指紋或 Face ID 時會收到輸入 PIN 的提示 <!-- 2637704  -->
現在，當使用者在其 iOS 裝置上進行生物特徵辨識變更之後，會收到輸入 PIN 的提示。 這包括變更已註冊的指紋或 Face ID。 提示時間取決於 [重新檢查存取需求前的剩餘時間 (分鐘)]  逾時的設定方式。  若未設定任何 PIN，則系統會提示使用者設定一個。 
 
此功能僅適用於 iOS，並需要整合 Intune APP SDK for iOS 9.0.1 版或更新版本的應用程式參與。 您必須整合此 SDK，才能針對目標應用程式強制執行該行為。 這項整合會輪流發生並取決於特定的應用程式小組。 參與的一些應用程式包括 WXP、Outlook、Managed Browser 和 Yammer。

#### <a name="network-access-control-support-on-ios-vpn-clients---1333693---"></a>iOS VPN 用戶端上的網路存取控制支援<!-- 1333693 -->
透過此更新，您可以在為 Cisco AnyConnect、F5 Access 和 Citrix SSO for iOS 建立 VPN 設定檔時啟用網路存取控制 (NAC)。 此設定可讓裝置的 NAC 識別碼包含在 VPN 設定檔中。 目前尚沒有任何支援此新 NAC 識別碼的 VPN 用戶端或 NAC 合作夥伴解決方案；當提供支援時，我們將透過[支援部落格文章](ttps://aka.ms/iOS12_and_vpn)通知您。

若要使用 NAC，您將需要：
1. 選擇允許 Intune 在 VPN 設定檔中包含裝置識別碼
2. 更新您的 NAC 提供者軟體/韌體，直接從您的 NAC 提供者使用指導方針

如需 iOS VPN 設定檔中此設定的相關資訊，請參閱[在 Microsoft Intune 中的 iOS 裝置上新增 VPN 設定](../configuration/vpn-settings-ios.md)。 如需網路存取控制的詳細資訊，請參閱[搭配 Intune 的網路存取控制 (NAC) 整合](../protect/network-access-control-integrate.md)。 

適用於：iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile---1818139---"></a>從裝置移除電子郵件設定檔，即使只有一個電子郵件設定檔也一樣<!-- 1818139 -->
之前，「如果」  這是唯一的電子郵件設定檔，則無法從裝置移除電子郵件設定檔。 在此更新中，此行為會有所變更。 現在，您可以移除電子郵件設定檔，即使裝置上只有一個電子郵件設定檔也一樣。 如需詳細資訊，請參閱[使用 Intune 將電子郵件設定新增至裝置](../configuration/email-settings-configure.md)。

#### <a name="powershell-scripts-and-aad---2309469---"></a>PowerShell 指令碼和 AAD<!-- 2309469 -->
Intune 中的 PowerShell 指令碼可以鎖定至 AAD 裝置安全性群組。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>適用於 Android、Android Enterprise 的新「必要密碼類型」預設設定<!-- 2649963 -->
當您建立新的合規性原則 (針對 [平台] > [系統安全性]，選擇 [Intune]   > [裝置合規性]   > [原則]   > [建立原則]   > [Android]  或 [Android Enterprise]  ) 時，[必要密碼類型]  的預設值會變更：

從：裝置預設為：至少包含數字

適用於：Android、Android Enterprise

若要查看這些設定，請瀏覽 [Android](../protect/compliance-policy-create-android.md) 和 [Android Enterprise](../protect/compliance-policy-create-android-for-work.md)。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile---2662938---"></a>在 Windows 10 Wi-Fi 設定檔中使用預先共用金鑰<!-- 2662938 -->
透過此更新，您可以搭配 WPA/WPA2-Personal 安全性通訊協定使用預先共用金鑰 (PSK)，來驗證適用於 Windows 10 的 Wi-Fi 組態設定檔。 您也可以在Windows 10 2018 年 10 月更新中，為裝置指定計量付費網路的成本設定。

目前您必須匯入 Wi-Fi 設定檔或是建立自訂的設定檔，才能使用預先共用金鑰。 [適用於 Windows 10 的 Wi-Fi 設定](../configuration/wi-fi-settings-windows.md)列出目前的設定。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices---3218390---"></a>從您的裝置移除 PKCS 和 SCEP 憑證<!-- 3218390 -->
在某些案例中，PKCS 和 SCEP 憑證會保留在裝置上，即使從群組中移除原則、刪除設定或合規性部署，或是系統管理員更新現有的 SCEP 或 PKCS 設定檔也一樣。 此更新會變更該行為。 在某些案例中，PKCS 和 SCEP 憑證會從裝置移除；在某些案例中，這些憑證會保留在裝置上。 請參閱[在 Microsoft Intune 中移除 SCEP 和 PKCS 憑證](../protect/remove-certificates.md)以了解這些案例。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance---2504381---"></a>在 macOS 裝置上使用閘道管理員以符合規範<!-- 2504381 -->
此更新包括 macOS 閘道管理員，用於評估裝置合規性。 若要設定閘道管理員屬性，請[為 macOS 裝置新增裝置合規性政策](../protect/compliance-policy-create-mac-os.md)。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot---1558983---"></a>將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置<!-- 1558983 -->
您可以將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置。 在 Autopilot 設定檔中，選擇 [將所有目標裝置轉換為 Autopilot]  選項，以將所有非 Autopilot 的裝置自動註冊至 Autopilot 部署服務。 等候 48 小時讓註冊處理完畢。 當裝置取消註冊並重設時，Autopilot 將會自動佈建它。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups---2526564---"></a>建立並指派多個註冊狀態頁面設定檔至 Azure AD 群組<!-- 2526564 -->
您現在可以[建立並指派](../enrollment/windows-enrollment-status.md)多個註冊狀態頁面設定檔至 Azure AD 群組。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune--2748613--"></a>從裝置註冊計劃移轉到 Intune 中的 Apple Business Manager<!--2748613-->
Apple Business Manager (ABM) 能在 Intune 中運作，您可以將您的帳戶從裝置註冊計劃 (DEP) 升級到 ABM。 Intune 中的程序都相同。 若要將您的 Apple 帳戶從 DEP 升級到 ABM，請前往 [https://support.apple.com/HT208817]( https://support.apple.com/HT208817)。

#### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page--2748656--"></a>[裝置註冊概觀] 頁面上的 [警示] 和 [註冊狀態] 索引標籤<!--2748656-->
警示和註冊失敗現在會出現在 [裝置註冊概觀] 頁面的個別索引標籤上。

#### <a name="enrollment-abandonment-report---1382924---"></a>註冊放棄報表<!-- 1382924 -->
您可以在 [裝置註冊]   > [監視]  下取得新報表，提供已放棄註冊的詳細資料。 如需詳細資訊，請參閱[公司入口網站放棄報表](../enrollment/enrollment-report-company-portal-abandon.md)。

#### <a name="new-azure-active-directory-terms-of-use-feature---2870393---"></a>新的 Azure Active Directory 使用條款功能<!-- 2870393 -->
Azure Active Directory 具備您可以改使用的條款功能，而無須使用現有 Intune 條款及條件。 Azure AD 使用條款功能可提供更多彈性，讓您決定要顯示哪些條款以及顯示的時機、具備更佳的當地語系化支援、對轉譯條款的方式擁有更大控制能力，以及改善回報。 Azure AD 使用條款需要 Azure Active Directory Premium P1，該項目也是 Enterprise Mobility + Security E3 套件的一部分。 若要深入了解，請參閱[管理公司的使用者存取條款及條件](../enrollment/terms-and-conditions-create.md)一文。

#### <a name="android-device-owner-mode-support--3188762--"></a>Android 裝置擁有者模式支援<!--3188762-->
針對 Samsung Knox 行動裝置註冊，Intune 現在支援將裝置註冊於 Android 裝置擁有者管理模式。 使用 WiFi 或行動電話通訊網路的使用者第一次開啟其裝置時，只需輕點幾下即可註冊。 如需詳細資訊，請參閱[使用 Samsung Knox Mobile Enrollment 自動註冊 Android 裝置](../enrollment/android-samsung-knox-mobile-enroll.md)。

### <a name="device-management"></a>裝置管理
#### <a name="new-settings-for-software-updates-----1907869---"></a>軟體更新的新設定  <!-- 1907869 -->  
- 您現在可以設定某些通知，以警告終端使用者完成最新軟體更新安裝所需的重新啟動。   
- 您現在可以為非工作時間發生的重新啟動設定重新啟動警告提示，可支援 BYOD 案例。

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id---2075110---"></a>透過交互識別碼群組 Windows Autopilot 註冊裝置<!-- 2075110 -->
Intune 現在支援在透過 Configuration Manager 使用[適用於現有裝置的 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)註冊時，使用交互識別碼來為 Windows 裝置分組。 交互識別碼是 Autopilot 設定檔的參數。 Intune 會自動將 [Azure AD 裝置屬性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices) 設為相等的 "OfflineAutopilotprofile-<correlator ID>"。 這會允許透過離線 Autopilot 註冊的 enrollmentprofileName 屬性，根據交互識別碼建立任意 Azure AD 動態群組。 如需詳細資訊，請參閱[適用於現有裝置的 Windows Autopilot](../enrollment/enrollment-autopilot.md#windows-autopilot-for-existing-devices)。

#### <a name="intune-app-protection-policies---2984657---"></a>Intune 應用程式防護原則<!-- 2984657 -->
Intune 應用程式保護原則可讓您為 Intune 保護的應用程式 (如 Microsoft Outlook 和 Microsoft Word) 設定各種資料保護設定。 我們已變更這些設定的外觀與風格 ([iOS](../apps/app-protection-policy-settings-ios.md) 和 [Android](../apps/app-protection-policy-settings-android.md))，以便輕鬆找到個別設定。 原則設定有三個類別：
- **資料重新配置** - 此群組包含資料外洩防護 (DLP) 控制項，例如剪下、複製、貼上以及另存新檔的限制。 這些設定會決定使用者如何與應用程式中的資料互動。
- **存取需求** - 此群組包含每個應用程式的 PIN 選項，用於決定終端使用者如何在工作環境中存取應用程式。  
- **條件式啟動** - 此群組包含最低作業系統設定、越獄和 Root 裝置偵測以及離線寬限期等設定。  
  
設定的功能不會變更，但可讓您在處理原則編寫流程時更容易找到。

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices---2451462----"></a>限制應用程式，並封鎖存取 Android 裝置上的公司資源<!-- 2451462  -->  
在 [裝置合規性]   > [原則]   > [建立原則]   > [Android]   > [系統安全性]  中，[裝置安全性]  區段下方有一個名為 [受限應用程式]  的新設定。 若在裝置上安裝特定應用程式，則 [受限應用程式]  設定會使用合規性原則來封鎖對公司資源的存取。 除非從裝置中移除受限制應用程式，否則會將裝置視為不符合規範。
適用於： 
- Android

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps---1727158---"></a>針對 LOB 應用程式，Intune 將支援最大 8 GB 套件大小<!-- 1727158 -->
Intune 會將企業營運 (LOB) 應用程式的最大套件大小增加為 8 GB。 如需詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](../apps/apps-add.md)。

#### <a name="add-custom-brand-image-for-company-portal-app---1916266---"></a>新增公司入口網站應用程式的自訂品牌形象<!-- 1916266 -->
作為 Microsoft Intune 系統管理員，您可以上傳自訂品牌影像，該影像會在 iOS 公司入口網站應用程式的使用者設定檔頁面上，作為背景影像顯示。 如需設定公司入口網站應用程式的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](../apps/company-portal-app.md)。

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines---2971030---"></a>Intune 會在更新終端使用者電腦上的 Office 時保留 Office 當地語系化語言<!-- 2971030 -->
當 Intune 在您終端使用者的電腦上安裝 Office 時，終端使用者會自動取得與其先前 .MSI Office 安裝相同的語言套件。 如需詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](../apps/apps-add-office365.md)。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal---3076965---"></a>Microsoft 365 裝置管理入口網站中的新 Intune 支援體驗<!-- 3076965 -->
我們正於 [Microsoft 365 裝置管理入口網站]( https://devicemanagement.microsoft.com)中，為 Intune 推出新的說明及支援體驗。 新體驗可讓您用自己的文字描述問題，並收到疑難排解深入解析和網站型修復內容。 這些解決方案透過規則型的機器學習演算法提供，由使用者查詢所驅動。  

除了特定問題的指導之外，您也可以使用新的案例建立工作流程，透過電子郵件或電話來開啟支援案例。  

針對參與推出的客戶，此新體驗會取代一組靜態預先選取選項的目前說明和支援體驗，這些選項會基於您開啟說明及支援時所在控制台的區域。  

*這個新的說明及支援體驗正在推出至部分 (並非全部) 租用戶，並且可在 [裝置管理] 入口網站中找到。從可用的 Intune 租用戶中隨機選取這個新體驗的參與者。在我們擴展推出時，將會新增新租用戶。*  

如需詳細資訊，請參閱＜如何取得 Microsoft Intune 支援＞中的[說明及支援體驗](get-support.md#help-and-support-experience)。  

#### <a name="powershell-module-for-intune--preview-available---951068---"></a>適用於 Intune 的 PowerShell 模組 - 現供預覽<!-- 951068 -->
新的 PowerShell 模組透過 Microsoft Graph 支援 Intune API，現在於 [GitHub](https://aka.ms/intunepowershell) 上提供預覽。 如需如何使用此模組的詳細資料，請參閱該位置的讀我檔案。

<!-- ########################## -->
## <a name="september-2018"></a>2018 年 9 月

### <a name="app-management"></a>應用程式管理

#### <a name="remove-duplication-of-app-protection-status-tiles---3083391---"></a>移除重複的應用程式保護狀態磚<!-- 3083391 -->
[用戶端應用程式 - 概觀]  頁面以及 [用戶端應用程式 - 應用程式保護狀態]  頁面都會顯示 [iOS 使用者狀態]  和 [Android 使用者狀態]  磚。 這些狀態磚已從 [用戶端應用程式 - 概觀]  頁面中移除，以避免重複。 

### <a name="device-configuration"></a>裝置設定

#### <a name="support-for-more-third-party-certification-authorities-ca---3093107---"></a>支援更多的協力廠商憑證授權單位 (CA)<!-- 3093107 -->
透過使用簡單憑證註冊通訊協定 (SCEP)，您現在可以在使用 Windows、iOS、Android 和 macOS 的行動裝置上發行新憑證及更新憑證。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="intune-moves-to-support-ios-10-and-later---2454656---"></a>Intune 轉為支援 iOS 10 和更新版本<!-- 2454656 -->  
Intune 註冊、公司入口網站及受控瀏覽器現在只支援執行 iOS 10 和更新版本的 iOS 裝置。 若要檢查組織中受影響的使用者或裝置，請移至 Azure 入口網站中的 Intune > [裝置]   > [所有裝置]  。 依 OS進行篩選，然後按一下 [資料行]  以呈現 OS 版本詳細資料。 要求這些使用者將其裝置升級至支援的 OS 版本。  

如果您有下面列出的任何裝置，或想要註冊下面列出的任何裝置，請注意，它們只支援 iOS 9 和更早版本。  若要繼續存取 Intune 公司入口網站，您必須將這些裝置升級為支援 iOS 10 或更新版本的裝置：  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (第 3 代) 
* iPad Mini (第 1 代)  

### <a name="device-management"></a>裝置管理

#### <a name="microsoft-365-device-management-administration-center---3078424---"></a>Microsoft 365 裝置管理的系統管理中心<!-- 3078424 -->
Microsoft 365 的承諾之一是簡化管理，多年來我們已整合後端的 Microsoft 365 服務來提供端對端案例，例如 Intune 和 Azure AD 條件式存取。 新的 [Microsoft 365 系統管理中心](https://devicemanagement.microsoft.com)可用來合併、簡化及整合管理體驗。 [裝置管理] 的專家工作區可讓您輕鬆地存取所有裝置和應用程式管理資訊，以及您組織需要的工作。 我們預期這會成為企業終端使用者運算小組的主要雲端工作區。


<!-- ########################## -->
## <a name="august-2018"></a>2018 年 8 月

### <a name="app-management"></a>應用程式管理

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types---1520957---"></a>自訂和 Pulse Secure 連線類型之 iOS 個別應用程式 VPN 設定檔的封包通道支援<!-- 1520957 -->
使用 iOS 個別應用程式 VPN 設定檔時，您可以選擇使用應用程式層通道 (app-proxy) 或封包層通道 (packet-tunnel)。 下列連線類型可以使用這些選項：
- 自訂 VPN
- Pulse Secure：如果您不確定要使用的值，請參閱您 VPN 提供者的文件。

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device---1949583---"></a>在裝置上顯示 iOS 軟體更新時延遲<!-- 1949583 -->
在 [Intune] > [軟體更新]   > [Update policies for iOS] \(更新 iOS 的原則\)  中，您可以設定不想要裝置安裝任何更新的日期和時間。 在未來的更新中，您可以在裝置上以可見的方式顯示軟體更新時延遲 (從 1-90 天)。 
[在 Microsoft Intune 中設定 iOS 更新原則](../protect/software-updates-ios.md)會列出目前設定。

#### <a name="office-365-proplus-version---2213968---"></a>Office 365 ProPlus 版本<!-- 2213968 -->
使用 Intune 將 Office 365 ProPlus 應用程式指派給 Windows 10 裝置時，您將能選取 Office 版本。 在 Azure 入口網站中，選取 [Microsoft Intune]   > [應用程式]   > [新增應用程式]  。 然後，從 [類型]  下拉式清單中選取 [Office 365 ProPlus Suite (Windows 10)]  。 選取 [App Suite 設定]  以顯示相關聯的刀鋒視窗。 將 [更新通道]  設定為值 (例如 [每月]  )。 選擇性地選取 [是]  ，以從終端使用者裝置移除其他 Office (msi) 版本。 選取 [特定]  ，以在終端使用者裝置上安裝所選取通道的特定 Office 版本。 目前，您可以選取要使用之 Office 的 [特定版本]  。 可用的版本將會隨著時間變更。 因此，建立新的部署時，可用的版本可能較新，因此沒有特定較舊版本可用。 目前部署將會繼續部署較舊的版本，但每個通道都會持續更新版本清單。 如需詳細資訊，請參閱 [Office 365 ProPlus 更新通道的概觀](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

#### <a name="support-for-register-dns-setting-for-windows-10-vpn---2282852---"></a>支援 Windows 10 VPN 的註冊 DNS 設定<!-- 2282852 -->
透過此更新，您可以設定 Windows 10 VPN 設定檔，動態註冊指派給具有內部 DNS 之 VPN 介面的 IP 位址，而不需要使用自訂設定檔。
如需目前可用之 VPN 設定檔設定的資訊，請參閱 [Windows 10 VPN 設定](../configuration/vpn-settings-windows-10.md)。

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name--2652728--"></a>macOS 公司入口網站安裝程式現在會在安裝程式檔案名稱中包含版本號碼<!--2652728-->

#### <a name="ios-automatic-app-updates---2729759---"></a>iOS 自動應用程式更新<!-- 2729759 -->
自動應用程式更新適用於 iOS 11.0 版和更新版本的裝置和使用者授權應用程式。

### <a name="device-configuration"></a>裝置設定

#### <a name="windows-hello-will-target-users-and-devices---1106609---"></a>Windows Hello 是以使用者和裝置為目標<!-- 1106609 -->
當您建立 [Windows Hello 企業版](../protect/windows-hello.md)原則時，該原則會套用至組織 (整個租用戶) 內的所有使用者。 使用此更新，也可以使用裝置設定原則將該原則套用至特定使用者或特定裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Identity Protection]   > [Windows Hello 企業版]  )。
在 Azure 入口網站的 Intune 中，Windows Hello 設定現在會存在於 [裝置註冊]  和 [裝置設定]  中。 [裝置註冊]  以整個組織 (整個租用戶) 為目標，並支援 Windows AutoPilot (OOBE)。 [裝置設定]  以使用在簽入期間所套用原則的裝置和使用者為目標。
本功能適用於：  
- Windows 10 及更新版本
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios---1769858---"></a>Zscaler 是 iOS 上 VPN 設定檔的可用連線<!-- 1769858 -->
當您建立 iOS VPN 裝置設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [VPN]  設定檔類型) 時，有數種連線類型 (包括 Cisco、Citrix 等等)。 此更新會將 Zscaler 新增為連線類型。 
[執行 iOS 之裝置的 VPN 設定](../configuration/vpn-settings-ios.md)列出可用的連線類型。

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10---1879077---"></a>適用於 Windows 10 企業 Wi-Fi 設定檔的 FIPS 模式<!-- 1879077 -->
您現在可以在 Intune Azure 入口網站中，啟用適用於 Windows 10 之企業 Wi-Fi 設定檔的美國聯邦資訊處理標準 (FIPS) 模式。 如果您在 Wi-Fi 設定檔中啟用 FIPS 模式，也請務必在您的 Wi-Fi 基礎結構中啟用。
[Intune 中適用於 Windows 10 和更新版本之裝置的 Wi-Fi 設定](../configuration/wi-fi-settings-windows.md)說明如何建立 Wi-Fi 設定檔。

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview---1958649---"></a>控制 Windows 10 和更新版本裝置上的 S 模式 - 公開預覽<!-- 1958649 -->
透過此功能更新，您可以建立裝置組態設定檔以將 Windows 10 裝置切換出 S 模式，或防止使用者將裝置切換出 S 模式。 此功能位於 Intune > [裝置設定]   > [設定檔]   >  [Windows 10 and later] \(Windows 10 及更新版本\)   > [Edition upgrade and mode switch] \(版本升級和模式切換\)  中。
[引進 Windows 10 S 模式](https://www.microsoft.com/windows/s-mode)提供 S 模式的詳細資訊。
適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile---2144658---"></a>Windows Defender ATP 設定套件會自動新增至組態設定檔<!-- 2144658 -->
在 Intune 中使用[進階威脅防護和上線](../protect/advanced-threat-protection.md#onboard-devices-by-using-a-configuration-profile)裝置時，您必須先下載設定套件，並將之新增至組態設定檔。 透過此更新，Intune 會從 Windows Defender 資訊安全中心自動取得套件，並將之新增至設定檔。
適用於 Windows 10 及更新版本。

#### <a name="require-users-to-connect-during-device-setup--2311457--"></a>要求使用者在裝置設定期間連線<!--2311457-->
您現在可以設定裝置設定檔，要求裝置連線到網路，再繼續進行 Windows 10 安裝期間的 [網路] 頁面。 此功能尚在預覽階段，需要 Windows 測試人員組建 1809 或更新版本才能使用這項設定。
適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices---2451462---"></a>限制應用程式，並封鎖存取 iOS 和 Android Enterprise 裝置上的公司資源<!-- 2451462 -->
在 [裝置合規性]   > [原則]   > [建立原則]   > [iOS]   > [系統安全性]  中，會有新的 [Restricted applications] \(受限制的應用程式\)  設定。 如果在裝置上安裝特定應用程式，則這個新的設定會使用合規性原則來封鎖對公司資源的存取。 除非從裝置中移除受限制應用程式，否則會將裝置視為不符合規範。
適用於：iOS

#### <a name="modern-vpn-support-updates-for-ios---2459928-1819876-and-2650856---"></a>iOS 的新式 VPN 支援更新<!-- 2459928, 1819876, and 2650856 -->
此更新會支援下列 iOS VPN 用戶端：
- F5 Access (3.0.1 版和更高版本)
- Citrix SSO
- Palo Alto Networks GlobalProtect 5.0 版和更高版本另外在此更新中：
- 現有的 **F5 Access** 連線類型會重新命名為 **F5 Access Legacy** for iOS。
- 現有的 **Palo Alto Networks GlobalProtect** 連線類型會重新命名為 **Palo Alto Networks GlobalProtect (legacy)** for iOS。
具有這些連線類型的現有設定檔會持續使用其各自的舊版 VPN 用戶端。 如果您搭配 iOS 使用 Cisco Legacy AnyConnect、F5 Access Legacy、Citrix VPN 或 Palo Alto Networks GlobalProtect 4.1 版及更舊版本，您應移至新的應用程式。 請盡快這麼做，確保 iOS 裝置在更新為 iOS 12 時可以提供 VPN 存取。
如需 iOS 12 和 VPN 設定檔的詳細資訊，請參閱 [Microsoft Intune 支援小組部落格](https://go.microsoft.com/fwlink/?linkid=2013806)。

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal---2469637---"></a>匯出 Azure 傳統入口網站合規性政策，在 Intune Azure 入口網站中重新建立這些原則<!-- 2469637 -->
將會取代在 Azure 傳統入口網站中建立的合規性原則。 您可檢閱及刪除任何現有的合規性政策，但無法加以更新。 若需要將任一合規性政策移轉至目前的 Intune Azure 入口網站，可以用逗號分隔的檔案 ( *.csv* 檔案) 匯出政策。 然後，使用檔案中的詳細資料，在 Intune Azure 入口網站中，重新建立這些政策。

> [!IMPORTANT]
> Azure 傳統入口網站淘汰之後，您將無法再存取或檢視合規性政策。 因此，請務必在淘汰 Azure 傳統入口網站之前，先匯出您的政策，然後於 Azure 入口網站中重新建立。

#### <a name="better-mobile---new-mobile-threat-defense-partner---22662717---"></a>Better Mobile - 新的 Mobile Threat Defense 夥伴<!-- 22662717 -->
您可以根據由 Better Mobile (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in--1067692---"></a>除非使用者登入，否則會以單一應用程式模式鎖定公司入口網站<!--1067692 --> 
如果您在 DEP 註冊期間透過公司入口網站 (而非設定助理) 驗證使用者，您現在可以選擇以單一應用程式模式執行公司入口網站。 此選項會在設定助理完成之後立即鎖定裝置，讓使用者必須登入才能存取裝置。 此程序可確保裝置完成上架，而且在處於沒有任何使用者繫結的狀態下未遭到遺棄。

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device--1346521---"></a>將使用者和易記名稱指派給 AutoPilot 裝置<!--1346521 -->
您現在可以[將使用者指派給單一 Autopilot 裝置](../enrollment/enrollment-autopilot.md)。 系統管理員也可以提供易記名稱，以在使用 Autopilot 設定其裝置時歡迎使用者。
適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment---1608345---"></a>在 DEP 註冊期間，使用 VPP 裝置授權預先佈建公司入口網站<!-- 1608345 -->
您現在可以於裝置註冊計劃 (DEP) 註冊期間，使用大量採購方案 (VPP) 裝置授權預先佈建公司入口網站。 若要這麼做，當您[建立或編輯註冊設定檔時](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)，請指定您要用來安裝公司入口網站的 VPP 權杖。 請確定您的權杖未過期，而且您有足夠的公司入口網站應用程式權限。 如果權杖過期或授權不足，則 Intune會改為推送 App Store 公司入口網站 (這會提示您輸入 Apple 識別碼)。

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning---2237634---"></a>需要確認刪除將用於預先佈建公司入口網站的 VPP 權杖<!-- 2237634 -->
如果在 DEP 註冊期間將使用大量採購方案 (VPP) 權杖來預先佈建公司入口網站，則需要確認刪除該權杖。

#### <a name="block-windows-personal-device-enrollments---1849498---"></a>封鎖 Windows 個人裝置註冊<!-- 1849498 -->
您可以在 Intune 中[封鎖 Windows 個人裝置](../enrollment/enrollment-restrictions-set.md)註冊[行動裝置管理](../enrollment/windows-enroll.md)。 使用此功能無法封鎖使用 [Intune PC 代理程式](../manage-windows-pcs-with-microsoft-intune.md)所註冊的裝置。 此功能會在未來幾週推出，因此您在使用者介面中可能不會立即看到它。

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile--1849855--"></a>在 AutoPIlot 設定檔中指定電腦名稱模式<!--1849855-->
您可以[指定電腦名稱範本](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)，以在 AutoPilot 註冊期間產生並設定[電腦名稱](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)。 適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page--1901669---"></a>針對 Windows AutoPilot 設定檔，隱藏公司登入頁面和網域錯誤頁面上的變更帳戶選項<!--1901669 -->
[新增 Windows AutoPilot 設定檔選項](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)，讓管理員隱藏公司登入和網域錯誤頁面上的變更帳戶選項。 隱藏這些選項需要在 Azure Active Directory 中設定公司商標。 適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。

### <a name="macos-support-for-apple-device-enrollment-program---747651---"></a>macOS 支援 Apple 裝置註冊計畫<!-- 747651 -->
Intune 現在支援將 macOS 裝置註冊到 Apple 裝置註冊計劃 (DEP) 中。 如需詳細資訊，請參閱[使用 Apple 的裝置註冊計劃來自動註冊 macOS 裝置](../enrollment/device-enrollment-program-enroll-macos.md)。

### <a name="device-management"></a>裝置管理

#### <a name="delete-jamf-devices---2653306--"></a>刪除 Jamf 裝置<!-- 2653306-->
您可以刪除受控於 JAMF 的裝置，方法是移至 [裝置]  > 選擇 Jamf 裝置 > [刪除]  。

#### <a name="change-terminology-to-retire-and-wipe---2175759---"></a>將術語變更為「淘汰」和「抹除」<!-- 2175759 -->
為了與圖形 API 保持一致，Intune 使用者介面和文件已變更下列詞彙：
- 「移除公司資料」  將變更為「淘汰」
- 「原廠重設」  將變更為「抹除」 

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate---297909500--"></a>系統管理員嘗試刪除 MDM Push Certificate 時的確認對話方塊<!-- 297909500-->
如果任何人嘗試刪除 Apple MDM Push Certificate，確認對話方塊會出現，顯示相關 iOS 和 macOS 裝置的數目。 如果刪除憑證，則必須重新註冊這些裝置。

#### <a name="additional-security-settings-for-windows-installer---2282430---"></a>Windows Installer 的其他安全性設定<!-- 2282430 -->
您可以允許使用者控制應用程式安裝。 如啟用，則可讓以安全性違規方式停止的安裝繼續執行。 您可以指示 Windows Installer 在系統上安裝任何程式時使用提升的權限。 此外，您可以將 Windows 資訊保護 (WIP) 項目編入索引，並將跟其有關的中繼資料儲存在未加密的位置。 停用此原則時，不會編製 WIP 保護項目的索引，且不會出現在 Cortana 或檔案總管的結果中。 預設會停用這些選項的功能。 

#### <a name="new-user-experience-update-for-the-company-portal-website--2000968---"></a>對於公司入口網站的新使用者體驗更新<!--2000968 -->
我們已依據客戶的意見反應，新增功能至公司入口網站。 您將能於裝置上體驗現有功能和可用性等方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 已獲得全新的現代化回應式設計。 此外還包括：

- 已簡化所有裝置平台上的工作流程
- 已改進裝置識別和註冊流程
- 更多實用的錯誤訊息
- 讓語言更容易使用，讓技術專業術語更少
- 能夠共用應用程式的直接連結
- 已改進大型應用程式目錄的效能
- 已增加適用於所有使用者的協助工具  

已更新 [Intune 公司入口網站文件](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)，以反映這些變更。 若要檢視應用程式增強功能的範例，請參閱 [Intune 終端使用者應用程式的 UI 更新](../whats-new-app-ui.md)。  

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>相容性報告中增強的越獄偵測<!-- 2198738 -->
增強的破解偵測設定狀態現在會顯示在管理主控台的所有合規性報告中。

### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="scope-tags-for-policies--1081974---"></a>原則的範圍標籤<!--1081974 -->
您可以[建立範圍標籤](scope-tags.md)，限制對 Intune 資源的存取。 將範圍標籤新增至角色指派，然後將範圍標籤新增至設定檔。 此角色只能存取設定檔具有相符範圍標籤 (或無範圍標籤) 的資源。





<!-- ########################## -->
## <a name="july-2018"></a>2018 年 7 月

### <a name="app-management"></a>應用程式管理

#### <a name="line-of-business-lob-app-support-for-macos---1895847---"></a>macOS 的企業營運 (LOB) 應用程式支援<!-- 1895847 -->
Microsoft Intune 可讓 macOS LOB 應用程式部署為**必要**或**註冊可用**。 終端使用者可以使用適用於 macOS 的公司入口網站或[公司入口網站](https://portal.manage.microsoft.com)，來取得部署為**可用**的應用程式。

#### <a name="ios-built-in-app-support-for-kiosk-mode---2051098---"></a>Kiosk 模式的 iOS 內建應用程式支援<!-- 2051098 -->
除了市集應用程式和受控應用程式，您現在可以選取在 iOS 裝置上以 kiosk 模式執行的內建應用程式 (例如 Safari)。

#### <a name="edit-your-office-365-pro-plus-app-deployments---2150145---"></a>編輯 Office 365 Pro Plus 應用程式部署<!-- 2150145 -->
身為 Microsoft Intune 系統管理員，您可以更有效率地編輯 Office 365 Pro Plus 應用程式部署。 此外，您不再需要刪除部署，就能變更套件的任何內容。 在 Azure 入口網站中，選取 [Microsoft Intune]   > [用戶端應用程式]   > [應用程式]  。 從應用程式的清單中，選取您的 Office 365 Pro Plus 套件。  

#### <a name="updated-intune-app-sdk-for-android-is-now-available---2744271--"></a>目前提供已更新且適用於 Android 的 Intune App SDK<!-- 2744271-->
已提供適用於 Android 的 Intune App SDK 的更新版本，以支援 Android P 版本。 如果您是應用程式開發人員，並使用適用於 Android 的 Intune SDK，則必須安裝 Intune App SDK 的更新版本，以確保 Android 應用程式中的 Intune 功能在 Android P 裝置上可以繼續如預期般運作。 這個版本的 Intune App SDK 提供了一個執行 SDK 更新的內建外掛程式。 您不需要重寫任何已整合的現有程式碼。 如需詳細資訊，請參閱[適用於 Android 的 Intune SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) \(英文\)。 如果您使用 Intune 舊的徽章樣式，建議您使用 [公事包] 圖示。 如需商標詳細資料，請參閱[此 GitHub 存放庫](https://github.com/msintuneappsdk/intune-app-partner-badge) \(英文\)。

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>有更多機會可以在 Windows 公司入口網站應用程式中執行同步處理  
Windows 版公司入口網站應用程式現在可讓您直接從 Windows 工作列和 [開始] 功能表起始同步。 如果同步裝置並取得公司資源存取權是您唯一的工作，這項功能特別有用。 若要存取這項新功能，請以滑鼠右鍵按一下已釘選到工作列或 [開始] 功能表的公司入口網站圖示。 在功能表選項 (也稱為捷徑清單) 中，選取 [同步此裝置]  。 公司入口網站會開啟至 **[設定]** 頁面並起始您的同步。若要查看新功能，請參閱 [UI 的新功能](../whats-new-app-ui.md)。   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>新的 Windows 公司入口網站應用程式瀏覽體驗  
現在，在 Windows 版公司入口網站應用程式中瀏覽或搜尋應用程式時，您可以切換現有的 [磚]  檢視和新增的 [詳細資料]  檢視。 新的檢視會列出應用程式詳細資料，例如名稱、發佈者、發佈日期，以及安裝狀態。  

[應用程式]  頁面的 [已安裝]  檢視可讓您查看已完成和進行中的應用程式安裝詳細資料。 若要查看新檢視的外觀，請參閱 [UI 的新功能](../whats-new-app-ui.md)。  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>已改善裝置註冊管理員的公司入口網站應用程式體驗  
當裝置註冊管理員 (DEM) 登入 Windows 版公司入口網站應用程式時，應用程式現在只會列出 DEM 目前執行中的裝置。 這項改善會減少之前應用程式在嘗試顯示所有 DEM 註冊裝置時所發生的逾時。  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models----1425689----"></a>依據未經核准的裝置廠商和型號來封鎖應用程式存取 <!-- 1425689 ! -->
Intune IT 系統管理員可以透過 Intune 應用程式防護原則，強制執行 Android 製造商和/或 iOS 型號的指定清單。 IT 系統管理員可以提供以分號分隔的製造商清單 (適用於 Android 原則) 及裝置型號清單 (適用於 iOS 原則)。 Intune 應用程式防護原則僅適用於 Android 和 iOS。 針對此指定清單，將可以執行兩個個別的動作：
- 針對未指定的裝置，封鎖其存取應用程式的能力。
- 或是針對未指定的裝置，選擇性地抹除該裝置上的公司資料。 

若沒有符合原則需求，使用者將無法存取目標應用程式。 根據設定的不同，系統可能會封鎖該使用者，或選擇性地抹除其位於應用程式內的公司資料。 在 iOS 裝置上，此功能需要應用程式 (亦即，WXP、Outlook、Managed Browser、Yammer) 的參與來就地整合 Intune App SDK，以在目標應用程式中強制執行此功能。 這項整合會輪流發生並取決於特定的應用程式小組。 在 Android 上，此功能需要有最新版的公司入口網站。 

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則 Intune 刀鋒視窗中所指定字串來進行簡單比對，藉以採取動作。 這會完全取決於裝置報告的值。 因此，我們會建議 IT 系統管理員確定預期的行為是正確無誤的。 這可透過針對小型的使用者群組，在各種不同的裝置製造商和型號上測試此設定來達成。 在 Microsoft Intune 中，選取 [用戶端應用程式]   > [應用程式保護原則]  來檢視及新增應用程式保護原則。 如需有關應用程式保護原則的詳細資訊，請參閱[什麼是應用程式保護原則](../apps/app-protection-policy.md)與[在 Intune 中使用應用程式防護原則的存取動作選擇性地抹除資料](../apps/app-protection-policies-access-actions.md)。

#### <a name="access-to-macos-company-portal-pre-release-build---1734766---"></a>存取 macOS 公司入口網站發行前版本組建<!-- 1734766 -->
使用 Microsoft AutoUpdate 註冊，您可以透過加入測試人員計畫提早收到組建。 註冊可讓您在使用者可使用已更新的公司入口網站之前先行使用。 如需詳細資訊，請參閱 [Microsoft Intune 部落格](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)。

### <a name="device-configuration"></a>裝置設定

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices---1497640---"></a>在 macOS 裝置上使用防火牆設定來建立裝置相容性原則<!-- 1497640 -->
當您建立新的 macOS 合規性原則 ([裝置合規性]   > [原則]   > [建立原則]   >  [平台：macOS]   > [系統安全性]  ) 時，會有一些可用的新 [防火牆]  設定： 

- **防火牆**：設定您環境中處理連入連線的方式。
- **連入連線**：除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，[封鎖]  所有連入連線。 這項設定也會封鎖所有的共用服務。
- **隱形模式**：[啟用]  隱形模式以防止電腦回應探查要求。 電腦會繼續回應已授權應用程式的連入要求。

適用對象：macOS 10.12 和更新版本

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later---1879077---"></a>Windows 10 和更新版本的新 Wi-Fi 裝置組態設定檔<!-- 1879077 -->
您目前可以使用 XML 檔案來匯入和匯出 Wi-Fi 設定檔。 透過此更新，您可以直接在 Intune 中建立 Wi-Fi 裝置組態設定檔，如同一些其他平台。

若要建立設定檔，請開啟 [裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 和更新版本]   > [Wi-Fi]  。 

適用於 Windows 10 及更新版本。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed---2149998---"></a>Kiosk - 已淘汰會變成灰色且無法變更<!-- 2149998 -->
Kiosk (預覽) 功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 和更新版本]   > [裝置限制]  ) 會淘汰，並取代為 [Windows 10 和更新版本的 Kiosk 設定](../configuration/kiosk-settings.md)。 透過此更新，[Kiosk - 已淘汰]  功能會變成灰色，而且無法變更或更新使用者介面。 

若要啟用 Kiosk 模式，請參閱[適用於 Windows 10 和更新版本的 Kiosk 設定](../configuration/kiosk-settings.md)。

適用於 Windows 10 和更新版本、Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities---2184013---"></a>使用協力廠商憑證授權單位的 API<!-- 2184013 -->
在此更新中，有 Java API 可讓協力廠商憑證授權單位與 Intune 和 SCEP 整合。 然後，使用者可將 SCEP 憑證新增至設定檔，並將它套用至使用 MDM 的裝置。

Intune 目前支援[使用 Active Directory 憑證服務的 SCEP 要求](../protect/certificates-scep-configure.md)。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser---2455253---"></a>切換在 Kiosk 瀏覽器上顯示或不顯示 [結束工作階段] 按鈕<!-- 2455253 -->
您現在可以設定 Kiosk 瀏覽器是否顯示 [結束工作階段] 按鈕。 您可以在 [裝置設定]   > [Kiosk (預覽)]   > [Kiosk Web Browser] \(Kiosk 網頁瀏覽器\)  看到控制項。 如果開啟，則使用者按一下此按鈕時，應用程式會提示您確認結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料，並巡覽回預設 URL。

#### <a name="create-an-esim-cellular-configuration-profile---2564077---"></a>建立 eSIM 行動數據組態設定檔<!-- 2564077 -->
在 [裝置設定]  中，您可以建立 eSIM 行動數據設定檔。 您可以匯入檔案，其中包含您的行動電信業者所提供的行動數據啟用碼。 您接著可以將這些設定檔部署至啟用 eSIM LTE 的 Windows 10 裝置，例如 Surface Pro LTE 和其他具有 eSIM 功能的裝置。

確認您的[裝置支援 eSIM 設定檔](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)與否。

適用於 Windows 10 及更新版本。

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings---1058963-eenotready---"></a>使用 [存取公司或學校資源] 設定來選取裝置類別<!-- 1058963 eenotready --> 
如果您已啟用[裝置群組對應](../enrollment/device-group-mapping.md)，現在將在 Windows 10 上的使用者透過 [設定]   > [帳戶]   > [存取公司或學校資源]  中的 [連線]  按鈕註冊之後，提示他們選取裝置類別。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles---1500307---"></a>使用 sAMAccountName 作為電子郵件設定檔的帳戶使用者名稱<!-- 1500307 -->
您可以使用內部部署 **sAMAccountName**，作為 Android、iOS 和 Windows 10 電子郵件設定檔的帳戶使用者名稱。 也可以從Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 屬性取得網域。 或者，輸入自訂靜態網域。

若要使用這項功能，您必須將來自內部部署 Active Directory 環境的 `sAMAccountName` 屬性同步至 Azure AD。

適用於 [Android](../configuration/email-settings-android.md)、[iOS](../configuration/email-settings-ios.md)、[Windows 10 和更新版本](../configuration/email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict---1556983---"></a>查看衝突的裝置組態設定檔<!-- 1556983 -->
在 [裝置設定]  中，會顯示現有設定檔的清單。 使用此更新即會新增資料行，以提供衝突之設定檔的詳細資料。 您可以選取衝突的資料列，以查看設定以及發生衝突的設定檔。 

移至[管理組態設定檔](../configuration/device-profile-monitor.md#view-conflicts)以取得更多資訊。

#### <a name="new-status-for-devices-in-device-compliance---2308882---"></a>裝置相容性中裝置的新狀態<!-- 2308882 -->
在 [裝置相容性]   > [原則]  > 選取原則 > [概觀]  中，已新增下列新狀態：
- 成功
- 錯誤
- 衝突
- 暫止
- 不適用。同時顯示了顯示不同平台裝置計數的影像。 例如，如果您要查看 iOS 設定檔，新的磚會顯示同時指派給此設定檔的非 iOS 裝置計數。 請參閱[裝置合規性原則](../protect/compliance-policy-monitor.md#view-status-of-device-policies)。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions---2325484---"></a>裝置相容性支援協力廠商防毒解決方案<!-- 2325484 -->
當您建立裝置合規性政策時 ([裝置合規性]   > [原則]   > [建立原則]   > [平台:  Windows 10 和更新版本] > [設定]   > [系統安全性]  )，有新的 [[裝置安全性](../protect/compliance-policy-create-windows.md)]  選項： 
- **防毒**：當設定為 [必要]  時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 
- **反間諜功能**：當設定為 [必要]  時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 

適用於：Windows 10 及更新版本 

### <a name="device-enrollment"></a>裝置註冊

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate---2404851---"></a>將使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置自動標示為「公司」。<!-- 2404851 -->
根據預設，使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置現在會在 [Device Ownership] \(裝置擁有權\)  下標示為 [公司]  。 在使用 Knox Mobile Enrollment 註冊之前，您不需要手動找出使用 IMEI 或序號的公司裝置。

#### <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens---1853904---"></a>註冊計畫權杖清單中沒有設定檔資料行的裝置<!-- 1853904 -->
在註冊程式權杖清單中，有一個新資料行會顯示未指派設定檔的裝置數目。 這有助於系統管理員在將設定檔交給使用者之前將其指派給這些裝置。 若要查看新資料行，請前往 [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]  。

### <a name="device-management"></a>裝置管理

#### <a name="bulk-delete-devices-on-devices-blade---1793693---"></a>裝置刀鋒視窗上的大量刪除裝置<!-- 1793693 -->
您現在可以在 [裝置] 刀鋒視窗上同時刪除多部裝置。 選擇 [裝置]   > [所有裝置]  > 選取您要刪除的裝置 > [刪除]  。 針對無法刪除的裝置，將會顯示警示。

#### <a name="google-name-changes-for-android-for-work-and-play-for-work--842873---"></a>Android for Work 和 Play for Work 的 Google 名稱變更<!--842873 -->
Intune 已更新 "Android for Work" 術語以反映 Google 的商標變更。 "Android for Work" 和 "Play for Work" 這些詞彙已不再使用。 視內容而定，會使用不同的術語：
- 「Android 企業」指的是整體的現代 Android 管理堆疊。
- 「工作設定檔」或「設定檔擁有者」指的是使用工作設定檔管理的 BYOD 裝置。
- 「受控 Google Play」則是指 Google 應用程式存放區。

#### <a name="rules-for-removing-devices---1609459---"></a>用於移除裝置的規則<!-- 1609459 -->
新規則已可用，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune]  窗格，然後依序選取 [裝置]  和 [裝置清除規則]  。

#### <a name="corporate-owned-single-use-support-for-android-devices---1630973---"></a>公司所擁有且適用於 Android 裝置的單次使用支援<!-- 1630973 -->

Intune 現在支援高度受控、鎖定、Kiosk 樣式的 Android 裝置。 這可讓系統管理員將裝置的用途進一步鎖定為單一應用程式或一小組的應用程式，並可防止使用者在裝置上啟用其他應用程式或執行其他動作。 若要設定 Android Kiosk，請移至 [Intune] > [裝置註冊]   > [Android 註冊]   > [Kiosk 及工作裝置註冊]  。 如需詳細資訊，請參閱[設定 Android 企業 Kiosk 裝置註冊](../enrollment/android-kiosk-enroll.md)。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded---2203794--"></a>已上傳之重複公司裝置識別碼的每一資料列檢閱<!-- 2203794-->
上傳公司識別碼時，Intune 現在會提供任何重複項目的清單，並可讓您選擇取代或保留現有資訊。 選擇 [裝置註冊]   > [公司裝置識別碼]   > [新增識別碼]  之後，如果有重複項目，則會出現報表。 

#### <a name="manually-add-corporate-device-identifiers---2203803---"></a>手動新增公司裝置識別碼<!-- 2203803 -->
您現在可以手動新增公司裝置識別碼。 請選擇 [裝置註冊]   > [公司裝置識別碼]   > [新增]  。 


<!-- ########################## -->
## <a name="june-2018"></a>2018 年 6 月

### <a name="app-management"></a>應用程式管理

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies---1817882---"></a>Intune 應用程式防護原則的 Microsoft Edge 行動支援<!-- 1817882 -->
行動裝置的 Microsoft Edge 瀏覽器現在支援 Intune 中所定義的應用程式防護原則。

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode---1560077----"></a>在 Kiosk 模式中擷取商務用 Microsoft Store 應用程式的相關聯應用程式使用者模型識別碼 (AUMID)<!-- 1560077 ! -->
Intune 現在可以擷取商務用 Microsoft Store (WSfB) 應用程式的應用程式使用者模型識別碼 (AUMID)，以提供改善的 Kiosk 設定檔設定。

如需商務用 Microsoft Store 應用程式的詳細資訊，請參閱[管理來自商務用 Microsoft Store 的應用程式](../apps/windows-store-for-business.md)。

#### <a name="new-company-portal-branding-page---1916370---"></a>新的公司入口網站商標頁面<!-- 1916370 -->
公司入口網站商標頁面有新的版面配置、訊息和工具提示。


### <a name="device-configuration"></a>裝置設定

#### <a name="pradeo---new-mobile-threat-defense-partner---1169249---"></a>Pradeo - 新的 Mobile Threat Defense 夥伴<!-- 1169249 -->
您可以根據由 Pradeo (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="use-fips-mode-with-the-ndes-certificate-connector---1333688---"></a>使用 FIPS 模式搭配 NDES 憑證連接器<!-- 1333688 -->
當您在啟用聯邦資訊處理標準 (FIPS) 模式的電腦上安裝 NDES 憑證連接器時，發行和撤銷憑證無法如預期運作。 在此更新中，NDES 憑證連接器隨附 FIPS 支援。 

此更新還包括：

- NDES 憑證連接器需要 .NET 4.5 Framework，這會自動隨附於 Windows Server 2016 和 Windows Server 2012 R2。 之前，.NET 3.5 Framework 是最低必要版本。
- NDES 憑證連接器隨附 TLS 1.2 支援。 因此，如果安裝 NDES 憑證連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

如需詳細資訊，請參閱[設定並使用 SCEP 憑證](../protect/certificates-scep-configure.md)和[設定並使用 PKCS 憑證](../protect/certficates-pfx-configure.md)。

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles---1333680----"></a>Palo Alto Networks GLOBalProtect VPN 設定檔的支援<!-- 1333680 ! -->
透過這項更新，您可以選擇 Palo Alto Networks GLOBalProtect 作為在 Intune 中 VPN 設定檔的 VPN 連線類型 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [設定檔類型]   > [VPN]  )。 在此版本中，支援下列平台： 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings---1403702---"></a>新增本機裝置安全性選項設定<!-- 1403702 -->
您現在能夠為 Windows 10 裝置設定額外的 [本機裝置安全性選項] 設定。 可使用額外設定的區域包括 Microsoft Network Client、Microsoft Network Server、[網路存取和安全性] 及 [互動式登入]。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

#### <a name="enable-kiosk-mode-on-windows-10-devices---1560072----"></a>在 Windows 10 裝置上啟用 Kiosk 模式<!-- 1560072 ! -->
在 Windows 10 裝置上，您可以建立組態設定檔並啟用 Kiosk 模式 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10]   > [裝置限制]   > [Kiosk]  )。 在此更新中，[Kiosk (預覽)]  設定已重新命名為 [Kiosk (已淘汰)]  。 我們不建議繼續使用 [Kiosk (已淘汰)]  ，但該功能在 7 月更新之前將會持續運作。 [Kiosk (已淘汰)]  已由新的 [Kiosk]  設定檔類型 ([建立設定檔]   > [Windows 10]   > [Kiosk (預覽)]  ) 取代，此設定檔類型將會包含在 Windows 10 RS4 及更新版本上設定 Kiosk 的設定。

適用於 Windows 10 及更新版本。

#### <a name="device-profile-graphical-user-chart-is-back---2160133---"></a>已重新推出裝置設定檔圖形化使用者圖表<!-- 2160133 -->
在改善裝置設定檔圖形化圖表 ([裝置設定]   > [設定檔]  > 選取現有的設定檔 > [概觀]  ) 上所顯示的數值計數之際，暫時移除了圖形化使用者圖表。

此更新已重新推出圖形化使用者圖表，如 Azure 入口網站中所示。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication---1165118---"></a>支援 Windows Autopilot 註冊而不需要使用者驗證<!-- 1165118 -->
Intune 現在支援 Windows Autopilot 註冊，而不需要使用者驗證。 這是 Windows Autopilot 部署設定檔中 [Autopilot 部署模式] 設為 [自我部署] 的新選項。  裝置必須執行 Windows 10 Insider Preview 組建 17672 或更新版本，並擁有 TPM 2.0 晶片才能成功完成此類型的註冊。 由於不需要任何使用者驗證，您只應將此選項指派給您擁有實體控制權的裝置。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot---1821766---"></a>針對 Autopilot 設定 OOBE 時的新語言/地區設定<!-- 1821766 -->
在全新體驗期間，將會有新的組態設定可供設定 Autopilot 設定檔的語言和地區。 若要查看新設定，請選擇 [裝置註冊]   > [Windows 註冊]   > [部署設定檔]   > [建立設定檔]   > [部署模式]   = [自我部署]   > [設定的預設值]  。

#### <a name="new-setting-for-configuring-device-keyboard---1821768---"></a>適用於設定裝置鍵盤的新設定<!-- 1821768 -->
在全新體驗期間，將會有新設定可供設定 Autopilot 設定檔的鍵盤。 若要查看新設定，請選擇 [裝置註冊]   > [Windows 註冊]   > [部署設定檔]   > [建立設定檔]   > [部署模式]   = [自我部署]   > [設定的預設值]  。

#### <a name="autopilot-profiles-moving-to-group-targeting---1877935---"></a>將 AutoPilot 設定檔移至群組目標設定<!-- 1877935 -->
AutoPilot 部署設定檔可以指派給包含 AutoPilot 裝置的 Azure AD 群組。

### <a name="device-management"></a>裝置管理

#### <a name="set-compliance-by-device-location---851881----"></a>依裝置位置設定相容性<!-- 851881 ! -->
在某些情況下，您可能會想要依網路連線將公司資源的存取限制於特定的位置。 您現在可以依據裝置的 IP 位址建立合規性原則 ([裝置合規性]   > [位置]  )。 如果裝置移出該 IP 範圍，則該裝置將會無法存取公司資源。

適用於：公司入口網站應用程式已更新的 Android 裝置 6.0 和更新版本

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>防止 Windows 10 企業版 RS4 AutoPilot 裝置上的消費者應用程式和體驗<!-- 1621980 -->
您將能夠防止在「Windows 10 企業版 RS4 AutoPilot」裝置上安裝消費者應用程式和體驗。 若要查看此功能，請移至 [Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]   > [平台]   = [Windows 10 或更新版本]   > [設定檔類型]   = [裝置限制]   > [設定]   > [Windows 焦點]   > [消費者功能]  。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates---1732948---"></a>解除安裝 Windows 10 軟體更新的最新版本<!-- 1732948 -->
如果您發現 Windows 10 電腦上發生重大問題，可以選擇解除安裝 (復原) 最新的功能更新或最新的品質更新。 解除安裝功能或品質更新只適用於裝置所在的維護通道。 解除安裝將會觸發原則，以在 Windows 10 電腦上還原先前的更新。 特別是對於功能更新，您可以將能夠套用解除安裝最新版本的時間限制為 2-60 天。 若要設定軟體更新解除安裝選項，請從 Azure 入口網站內的 [Microsoft Intune]  刀鋒視窗中選取 [軟體更新]  。 然後，從 [軟體更新]  刀鋒視窗中，選取 [Windows 10 更新通道]  。 接著可以選擇 [概觀]  區段中的 [解除安裝]  選項。

#### <a name="search-all-devices-for-imei-and-serial-number---1793685---"></a>搜尋所有裝置的 IMEI 和序號<!-- 1793685 -->
您目前能在所有裝置的刀鋒視窗上搜尋 IMEI 和序號 (電子郵件、UPN、裝置名稱和管理名稱仍然可用)。 在 Intune 中，選擇 [裝置]   > [所有裝置]  > 在搜尋方塊中輸入您的搜尋。

#### <a name="management-name-field-will-be-editable---1875989---"></a>管理名稱欄位將可以編輯<!-- 1875989 -->
您目前可在裝置的 [屬性]  刀鋒視窗上編輯管理名稱欄位。 如果要編輯此欄位，請選擇 [裝置]   > [所有裝置]  > 選擇裝置 > [屬性]  。 您可以使用管理名稱欄位來唯一識別裝置。

#### <a name="new-all-devices-filter-device-category---1878520---"></a>[新增全部] 裝置篩選條件：裝置類別<!-- 1878520 -->
您現在可以依裝置類別篩選 [所有裝置]  清單。 若要這樣做，請選擇 [裝置]   > [所有裝置]   > [篩選]   > [裝置類別]  。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices---1985547---"></a>使用 TeamViewer 來共用 iOS 和 MacOS 裝置的螢幕畫面<!-- 1985547 -->
系統管理員現在可以連線至 [TeamViewer](../remote-actions/teamviewer-support.md)，並與 iOS 和 macOS 裝置建立螢幕畫面共用工作階段。 iPhone、iPad 及 macOS 使用者都可以與任何其他電腦或行動裝置即時共用其螢幕畫面。 

#### <a name="multiple-exchange-connector-support---2070451---"></a>多重 Exchange Connector 支援<!-- 2070451 -->
您不會再受到每個租用戶只能有一個 Microsoft Intune Exchange Connector 的限制了。 Intune 現在支援多個 Exchange 連接器，使您可以用多個內部部署 Exchange 組織來設定 Intune 條件式存取。

透過 Intune 內部部署 Exchange 連接器，您可以根據裝置是否已在 Intune 註冊且符合 Intune 裝置合規性政策，來管理裝置對於您內部部署 Exchange 信箱的存取。 若要設定連接器，請從 Azure 入口網站下載 Intune 內部部署 Exchange 連接器，並安裝在您 Exchange 組織中的伺服器。 在 Microsoft Intune 儀表板中，選擇 [內部部署存取]  ，然後在 [安裝]  下選擇 [Exchange ActiveSync 連接器]  。 下載 Exchange 內部部署連接器，並將其安裝在您 Exchange 組織中的伺服器。 您現在已經沒有一個租用戶只能有一個 Exchange 連接器的限制，因此您如果有其他 Exchange 組織，亦可遵循此相同流程為每個 Exchange 組織下載並安裝連接器。

#### <a name="new-device-hardware-detail-ccid---2156657---"></a>新的裝置硬體詳細資料：CCID<!-- 2156657 -->
每個裝置現在都包含晶片卡介面裝置 (CCID) 資訊。 若要查看它，請選擇 [裝置]   > [所有裝置]  > 選擇裝置 > [硬體]  > 檢查 [網路詳細資料]  下的內容 >

#### <a name="assign-all-users-and-all-devices-as-scope-groups---2196803---"></a>將所有使用者和所有裝置指派為範圍群組<!-- 2196803 -->
您現在能以範圍群組的形式指派所有使用者、所有裝置，以及所有使用者和所有裝置。 若要這樣做，請選擇 [Intune 角色]   > [所有角色]   > [原則和設定檔管理員]   > [指派]  > 選擇指派 > [範圍 (群組)]  。

#### <a name="udid-information-now-included-for-ios-and-macos-devices---2219806---"></a>iOS 和 macOS 裝置現在包含 UDID 資訊<!-- 2219806 -->
若要查看 iOS 和 macOS 裝置的唯一裝置識別碼 (UDID)，請移至 [裝置]   > [所有裝置]  > 選擇裝置 > [硬體]  。 UDID 只適用於公司裝置 (如 [裝置]   > [所有裝置]  > 選擇裝置 > [屬性]   > [裝置擁有權]  下的設定)。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="improved-troubleshooting-for-app-installation---928990---"></a>已改善針對應用程式安裝進行疑難排解<!-- 928990 -->
在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 我們正在推出應用程式疑難排解功能的公開預覽。 您將會在每個個別裝置的底下看到名為 [受控應用程式]  的新節點。 這會列出透過 Intune MDM 傳遞的應用程式。 在該節點中，您將會看到應用程式安裝狀態的清單。 如果您選取個別的應用程式，將會看到針對該特定應用程式的疑難排解檢視。 在疑難排解檢視中，您將會看到應用程式的端對端生命週期，例如針對該應用程式進行建立、修改、設為目標，以及傳遞至裝置的時間。 此外，如果應用程式安裝沒有成功，系統將會針對導致該錯誤的原因為您顯示錯誤碼及協助訊息。 

#### <a name="intune-app-protection-policies-and-microsoft-edge---1818968---"></a>Intune 應用程式保護原則和 Microsoft Edge<!-- 1818968 -->
適用於行動裝置 (iOS 和 Android) 的 Microsoft Edge 瀏覽器現可支援 Microsoft Intune 應用程式保護原則。 使用其公司 Azure AD 帳戶登入 Microsoft Edge 應用程式的 iOS 和 Android 裝置使用者，將會受到 Intune 的保護。 在 iOS 裝置上，[要求受控瀏覽器的 Web 內容]  原則可讓使用者開啟受控 Microsoft Edge 中的連結。

<!-- ########################## -->
## <a name="may-2018"></a>2018 年 5 月

### <a name="app-management"></a>應用程式管理

#### <a name="configuring-your-app-protection-policies---2144597-part-2---"></a>設定應用程式保護原則<!-- 2144597 Part 2 -->

在 Azure 入口網站，不用移至 Intune 應用程式保護服務刀鋒視窗，您現在只需移至 Intune。 目前在 Intune 中只有一個應用程式保護原則的位置。 請注意，所有應用程式保護原則都在 Intune [應用程式保護原則]  底下的 [行動應用程式]  刀鋒視窗上。 這項整合有助於簡化雲端管理系統管理。 請記住，所有應用程式保護原則都已經在 Intune 中，而您可以修改任何先前已設定的原則。 Intune 應用程式原則保護 (APP) 和條件式存取 (CA) 原則現在在 [條件式存取]  下，這可以在 [Microsoft Intune]  刀鋒視窗的 [管理]  區段找到，或在 [Azure Active Directory]  刀鋒視窗的 [安全性]  區段找到。 如需有關修改條件式存取原則詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 如需詳細資訊，請參閱[什麼是應用程式保護原則？](../apps/app-protection-policy.md)

### <a name="device-configuration"></a>裝置設定

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles---1553555---"></a>要求安裝原則、應用程式、憑證及網路設定檔<!-- 1553555 -->
在佈建 AutoPilot 裝置期間，系統管理員能夠禁止終端使用者存取 Windows 10 RS4 桌面，直到 Intune 安裝原則、應用程式及憑證與網路設定檔為止。 如需詳細資訊，請參閱[設定註冊狀態頁面](../enrollment/windows-enrollment-status.md)。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="samsung-knox-mobile-enrollment-support--1112863--"></a>Samsung Knox Mobile Enrollment 支援<!--1112863-->
當 Intune 與 Samsung Knox Mobile Enrollment (KME) 搭配使用時，您可以註冊大量公司擁有的 Android 裝置。 使用 WiFi 或行動電話通訊網路的使用者第一次開啟其裝置時，只需輕點幾下即可註冊。 使用 Knox 部署應用程式時，可以使用藍牙或 NFC 註冊裝置。 如需詳細資訊，請參閱[使用 Samsung Knox Mobile Enrollment 自動註冊 Android 裝置](../enrollment/android-samsung-knox-mobile-enroll.md)。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解 

#### <a name="requesting-help-in-the-company-portal-for-windows-10---1874137---"></a>取得 Company Portal for Windows 10 說明<!-- 1874137 -->
當使用者啟動工作流程以取得有關問題的說明時，Windows 10 版公司入口網站現在會將應用程式記錄檔直接傳送給 Microsoft。 這樣可以更輕鬆地進行疑難排解並解決向 Microsoft 提出的問題。

<!-- ########################## -->
## <a name="april-2018"></a>2018 年 4 月

### <a name="app-management"></a>應用程式管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>在 Android 上針對 MAM PIN 提供密碼支援<!-- 1438086 -->

Intune 系統管理員可以將應用程式的啟動要求設定為使用密碼，而不是使用數字型的 MAM PIN 碼。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 Intune 支援密碼的方式與數字 PIN 類似，能夠透過管理主控台設定長度下限、允許重複的字元及順序。 若要使用此功能，Android 上必須要有最新版的公司入口網站。 此功能已經可供 iOS 使用。

#### <a name="line-of-business-lob-app-support-for-macos---1473977---"></a>macOS 的企業營運 (LOB) 應用程式支援<!-- 1473977 -->
Microsoft Intune 將可讓您從 Azure 入口網站安裝 macOS LOB 應用程式。 您將能夠在以 GitHub 中提供的工具對 macOS LOB 應用程式進行前處理之後，將其新增至 Intune。 在 Azure 入口網站中，從 [Intune]  刀鋒視窗選擇 [用戶端應用程式]  。 在 [用戶端應用程式]  刀鋒視窗上，選擇 [應用程式]   > [新增]  。 在 [新增應用程式]  刀鋒視窗上，選取 [企業營運應用程式]  。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment---1813073---"></a>適用於 Android Enterprise 工作設定檔應用程式指派的內建所有使用者和所有裝置群組<!-- 1813073 -->
您可以利用內建的 [所有使用者]  和 [所有裝置]  群組來進行 Android Enterprise 工作設定檔應用程式指派。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](../apps/apps-inc-exl-assignments.md)。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users---1947010---"></a>Intune 會重新安裝由使用者解除安裝的必要應用程式<!-- 1947010 -->
如果終端使用者解除安裝必要的應用程式，Intune 會在 24 小時內自動重新安裝應用程式，而不會等待 7 天的重新評估週期。

#### <a name="update-where-to-configure-your-app-protection-policies---2144597---"></a>更新應用程式保護原則的設定位置<!-- 2144597 -->

在 Microsoft Intune 服務的 Azure 入口網站中，我們將暫時將您從 [Intune 應用程式防護]  服務刀鋒視窗重新導向至 [行動應用程式]  刀鋒視窗。 請注意，您所有的應用程式防護原則都已經在 Intune 中應用程式組態底下的 [行動應用程式]  刀鋒視窗上。 若前往 Intune 應用程式防護，您就會直接前往 Intune。 在 2018 年 4 月，我們將停止重新導向，並完全移除 [Intune 應用程式防護]  服務刀鋒視窗，如此一來 Intune 中的應用程式防護原則只會有一個位置。 

**此變更會對我造成什麼影響？**
這項變更會影響 Intune 獨立部署客戶和混合部署 (Intune 搭配 Configuration Manager) 客戶。 此整合將有助於簡化您的雲端管理。

**我需要為這項變更做什麼準備？**
請將 [Intune]  標記為我的最愛，而不是 [Intune 應用程式防護]  服務刀鋒視窗，並確定您已熟悉 Intune 中 [行動應用程式]  刀鋒視窗中的應用程式防護原則工作流程。 我們會進行重新導向一段時間，然後便會移除 [應用程式防護]  刀鋒視窗。 請記住，所有應用程式保護原則都已經在 Intune 中，而您可以修改任何條件式存取原則。 如需有關修改條件式存取原則詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 如需詳細資訊，請參閱[什麼是應用程式保護原則？](../apps/app-protection-policy.md) 

### <a name="device-configuration"></a>裝置設定

#### <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group---1449153---"></a>裝置設定檔圖表和狀態清單顯示群組中的所有裝置<!-- 1449153 -->
當您設定裝置設定檔 ([裝置設定]   > [設定檔]  ) 時，可以選擇裝置設定檔，例如 iOS。 您會將這個設定檔指派給包含 iOS 裝置和非 iOS 裝置的群組。 圖形化圖表計數會顯示設定檔已套用至 iOS「和」  非 iOS 裝置 ([裝置設定]   > [設定檔]  > 選取現有的設定檔 > [概觀]  )。 當您在 [概觀]  索引標籤中選取圖形化圖表時，[裝置狀態]  會列出群組中的所有裝置，而不是只列出 iOS 裝置。 

在此更新中，圖形化圖表 ([裝置設定]   >  [設定檔]  > 選取現有的設定檔 > [概觀]  ) 只會顯示特定裝置設定檔的計數。 例如，如果設定裝置設定檔適用於 iOS 裝置，圖表只會列出 iOS 裝置的計數。 選取圖形化圖表和開啟 [裝置狀態]  只會列出 iOS 裝置。

進行此更新時，會暫時移除圖形化使用者圖表。 

#### <a name="always-on-vpn-for-windows-10--1333666---"></a>適用於 Windows 10 的 Always On VPN<!--1333666 -->

目前，可藉由使用以 OMA-URI 建立的自訂虛擬私人網路 (VPN) 設定檔，在 Windows 10 裝置上使用[一律開啟](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

在此更新中，系統管理員將能夠直接在 Azure 入口網站的 Intune 中，為 Windows 10 VPN 設定檔啟用 Always On。 「一律開啟」VPN 設定檔會在下列情況下自動連線：

- 使用者登入其裝置
- 裝置上的網路發生變更
- 裝置上的螢幕在關閉後恢復開啟

#### <a name="new-printer-settings-for-education-profiles---1308900---"></a>教育版設定檔的新印表機設定<!-- 1308900 -->

教育版設定檔的新設定位於 [印表機]  類別下：[印表機]  、[預設印表機]  、[新增印表機]  。

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile--1098984---"></a>在個人的設定檔中顯示呼叫者識別碼 - Android Enterprise 工作設定檔<!--1098984 -->
在裝置上使用個人設定檔時，終端使用者可能無法從工作連絡人看到呼叫者識別碼詳細資料。 

在此更新中，[Android Enterprise]   > [裝置限制]   > [工作設定檔設定]  中會有一個新的設定：
- 在個人設定檔中顯示工作連絡人呼叫者識別碼

啟用 (未設定) 時，工作連絡呼叫者詳細資料會顯示在個人設定檔中。 封鎖時，工作連絡呼叫者詳細資料不會顯示在個人設定檔中。 

適用於：Android OS 6.0 版和更新版本上的 Android 工作設定檔裝置

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings--1102252-----from-1802-and-1804--"></a>在 Endpoint Protection 設定中新增新的 Windows Defender Credential Guard 設定<!--1102252 --><!--from 1802 and 1804-->

在此更新中，[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) ([裝置設定]   >  [設定檔]   >  [端點保護]  ) 包含下列設定： 

- **Windows Defender Credential Guard**：開啟搭載虛擬化安全性的 Credential Guard。 若同時啟用了**安全開機的平台安全性層級**與**虛擬化安全性**，啟用此功能將有助於在下次重新開機時保護認證。 這些選項包括：
  - **已停用**：若先前開啟 Credential Guard 時也啟用了 [在不含鎖定情況下啟用]  選項，將會從遠端關閉 Credential Guard。

  - **在包含 UEFI 鎖定的情況下啟用**：確保無法使用登錄機碼或群組原則停用 Credential Guard。 若要在使用此設定後停用 Credential Guard，必須將群組原則設為 [已停用]。 接著移除每位真實存在之使用者每部電腦的安全性功能。 下列步驟會清除 UEFI 中保存的設定。 只要 UEFI 設定持續存在，就會啟用 Credential Guard。

  - **在不含鎖定情況下啟用**：允許使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置至少必須執行 Windows 10 (1511 版)。

設定 Credential Guard 時會自動啟用下列相關技術： 

- **啟用虛擬化安全性 (VBS)** ：在下次重新開機期間開啟虛擬化安全性 (VBS)。 虛擬化安全性使用 Windows Hypervisor 支援安全性服務，需要安全開機功能。
- **使用直接記憶體存取 (DMA) 進行安全開機**：透過安全開機和直接記憶體存取開啟 VBS。 DMA 保護需要硬體支援，而且只可在設定正確的裝置上啟用。 

#### <a name="use-a-custom-subject-name-on-scep-certificate---2064190---"></a>在 SCEP 憑證上使用自訂主體名稱<!-- 2064190 -->
您可以使用在 SCEP 憑證設定檔中，使用自訂主體常見的名稱 **OnPremisesSamAccountName**。 例如，您可以使用 `CN={OnPremisesSamAccountName})`。

#### <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles---1098977---"></a>在 Android Enterprise 工作設定檔上封鎖相機和螢幕擷取<!-- 1098977 -->
當您為 Android 裝置設定裝置限制時，有兩個新屬性可用於封鎖： 
- 相機：封鎖對裝置上所有相機的存取
- 螢幕擷取：封鎖螢幕擷取，同時也防止在沒有安全視訊輸出的顯示裝置上顯示內容

適用於 Android Enterprise 工作設定檔。

#### <a name="use-cisco-anyconnect-client-for-ios---1333708---"></a>使用適用於 iOS 的 Cisco AnyConnect 用戶端<!-- 1333708 -->

針對 iOS 建立新的 VPN 設定檔時，現在有兩個選項：**Cisco AnyConnect** 和 **Cisco Legacy AnyConnect**。 Cisco AnyConnect 設定檔支援 4.0.7x 和較新版本。 現有的 iOS Cisco AnyConnect VPN 設定檔會標記為 **Cisco Legacy AnyConnect**，但仍會繼續以目前的方式搭配 Cisco AnyConnect 4.0.5x 和較舊版本運作。

> [!NOTE]
> 這項變更只適用於 iOS。 Android、Android Enterprise 工作設定檔及 macOS 平台仍然只有一個 Cisco AnyConnect 選項。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132--1734567---"></a>具有 macOS High Sierra 10.13.2+ 之裝置上使用者所適用的新註冊步驟<!--1734567 -->
macOS High Sierra 10.13.2 引進了「使用者核准的」MDM 註冊概念。 核准的註冊讓 Intune 可以管理一些高度安全性的設定。 如需詳細資訊，請參閱以下的 Apple 支援文件： https://support.apple.com/HT208019 。

除非使用者開啟 [系統偏好設定] 手動提供核准，否則使用 macOS 公司入口網站註冊的裝置會被視為「未經使用者核准」。 為此，macOS 公司入口網站現在會在註冊程序結尾，將 macOS 10.13.2 和更新版本的使用者導向以供他們手動核准其註冊。 Intune 管理主控台將會針對已註冊裝置是否獲得使用者核准進行回報。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune---2370684---"></a>現在可以向 Intune 註冊 Jamf 註冊的 macOS 裝置<!-- 2370684 -->
版本 1.3 和 1.4 的 macOS 公司入口網站並未使用 Intune 成功註冊 Jamf 裝置。 版本 1.4.2 的 macOS 入口網站已修正此問題。

#### <a name="updated-help-experience-in-company-portal-app-for-android---1631531---"></a>更新 Android 版公司入口網站應用程式的說明體驗<!-- 1631531 -->
我們已更新 Android 公司入口應用程式的說明體驗，以符合 Android 平台的最佳做法。 現在，當使用者在應用程式中遇到問題時，可以點選 [功能表]   > [說明]  ，然後：
- 將診斷記錄上傳到 Microsoft。
- 傳送描述問題和事件識別碼的電子郵件給公司支援人員。  

若要了解已更新的說明體驗，請參閱[使用電子郵件來傳送記錄](/intune-user-help/send-logs-to-your-it-admin-by-email-android)和[將錯誤傳送給 Microsoft](/intune-user-help/send-logs-to-microsoft-android)。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table---1471783---"></a>新註冊失敗趨勢圖和失敗原因資料表<!-- 1471783 -->
在 [註冊概觀] 頁面上，您可以檢視註冊失敗趨勢和前五大失敗原因。 按一下圖表或資料表，即可向下鑽研至詳細資料來尋找疑難排解建議和補救建議。


### <a name="device-management"></a>裝置管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated---1629303---"></a>進階威脅防護 (ATP) 和 Intune 已完全整合<!-- 1629303 -->

[進階威脅防護 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 會顯示 Windows 10 裝置的風險層級。 在 Windows Defender 資訊安全中心 (ATP 入口網站)，您可以建立與 Microsoft Intune 的連線。 一旦建立之後，Intune 合規性原則會用來判斷可接受的威脅層級。 如果超過威脅層級時，那麼 Azure Active Directory (AD) 條件式存取原則可封鎖存取組織內的不同應用程式。

這項功能可讓 ATP 掃描檔案、偵測威脅，以及報告 Windows 10 裝置上的任何風險。

請參閱[在 Intune 中啟用具有條件存取的 ATP](../protect/advanced-threat-protection.md)。

#### <a name="support-for-user-less-devices---1637553---"></a>支援無使用者裝置<!-- 1637553 -->
Intune 可以評估不具使用者之裝置 (例如 Microsoft Surface Hub) 的合規性。 合規性原則可以針對特定裝置。 因此，可以針對沒有相關使用者的裝置判斷是否符合規範 (和不符合規範)。

#### <a name="delete-autopilot-devices---1713650---"></a>刪除 Autopilot 裝置<!-- 1713650 -->
Intune 系統管理員可以[刪除 Autopilot 裝置](../enrollment/enrollment-autopilot.md#delete-autopilot-devices)。

#### <a name="improved-device-deletion-experience--1832333---"></a>已改善的裝置刪除體驗<!--1832333 -->
您現在無須移除公司資料，或是將裝置重設為原廠預設值，就能[從 Intune 刪除裝置](../remote-actions/devices-wipe.md#delete-devices-from-the-intune-portal)。

若要查看新體驗，請登入 Intune，然後選取 [裝置]   > [所有裝置]  > 裝置的名稱 > [刪除]  。

如果您仍然想要確認抹除/淘汰，可以使用標準裝置生命週期途徑，方法是先發出 [移除公司資料]  和 [重設成出廠預設值]  ，再進行 [刪除]  。 

#### <a name="play-sounds-on-ios-when-in-lost-mode---1947769---"></a>在處於遺失模式時於 iOS 上播放音效<!-- 1947769 -->
當受監督的 iOS 裝置處於「行動裝置管理」(MDM) 的[遺失模式](../remote-actions/device-lost-mode.md)時，您可以[播放音效](../remote-actions/device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) ([裝置]   >  [所有裝置]  **> 選取 iOS 裝置 > [概觀]**  >  [更多]  )。 此音效會持續播放，直到裝置解除遺失模式，或使用者停用了裝置上的音效。 適用於 iOS 裝置 9.3 和更新版本。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device--1972804--"></a>禁止或允許在 Intune 裝置上執行的搜尋中出現 Web 結果<!--1972804-->

系統管理員現在可以禁止裝置上的搜尋出現 Web 結果。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure---2172331---"></a>已改善 Apple MDM Push Certificate 上傳失敗的錯誤訊息<!-- 2172331 -->

錯誤訊息將會說明更新現有的 MDM 憑證時，必須使用相同的 Apple ID。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines---2216679---"></a>在虛擬機器上測試適用於 macOS 的公司入口網站<!-- 2216679 -->

我們已發佈相關指引，可協助 IT 系統管理員在 Parallels Desktop 和 VMware Fusion 的虛擬機器上測試適用於 macOS 的公司入口網站應用程式。 深入了解如何[虛擬 macOS 機器進行測試](../enrollment/macos-enroll.md#enroll-virtual-macos-machines-for-testing)。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="user-experience-update-for-the-company-portal-app-for-ios--1412866---"></a>iOS 版公司入口網站應用程式的使用者體驗更新<!--1412866 -->
我們已經發行 iOS 版公司入口網站應用程式的主要使用者經驗更新。 此更新採用全新現代化外觀的視覺設計。 應用程式的功能不變，但強化了可用性與協助工具功能。  

此外還包括：
- iPhone X 的支援。
- 應用程式啟動速度與載入回應的速度變快，可以節省使用者寶貴的時間。
- 增加更多的進度列，方便使用者掌握最新旳狀態資訊。
- 改善使用者上傳記錄的方式，方便在發生問題時回報。  

若要查看更新後的外觀，請參閱[應用程式 UI 的新功能](../whats-new-app-ui.md)。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca---1056954---"></a>使用 Intune APP 和 CA 來保護內部部署 Exchange 資料<!-- 1056954 -->
您現在可以搭配 Outlook Mobile 使用 Intune「應用程式原則保護」(APP) 和「條件式存取」(CA) 來保護對內部部署 Exchange 資料的存取。 若要在 Azure 入口網站內新增或修改應用程式保護原則，請選取 [Microsoft Intune]   > [用戶端應用程式]   > [應用程式保護原則]  。 開始使用此功能之前，請確定您符合 [iOS 版和 Android 版 Outlook 的需求](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)。


### <a name="user-interface"></a>使用者介面

#### <a name="improved-device-tiles-in-the-windows-10-company-portal--2213364---"></a>已改良 Windows 10 公司入口網站中的裝置磚<!--2213364 -->

針對視力比較弱的使用者，我們已將磚更新為更容易存取，且螢幕閱讀工具的執行效果更好。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos---2216677---"></a>傳送適用於 macOS 的公司入口網站應用程式的診斷報表<!-- 2216677 -->
我們已更新適用於 macOS 的公司入口網站應用程式，以改善使用者報告 Intune 相關錯誤的方法。 您的員工可以透過公司入口網站應用程式，進行下列作業：

- 將診斷報告直接上傳給 Microsoft 開發人員小組。
- 透過電子郵件，將事件識別碼傳送給公司的 IT 支援小組。

如需詳細資訊，請參閱[傳送 macOS 的錯誤](/intune-user-help/send-errors-macos)。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10---1195010---"></a>Intune 採用 Company Portal for Windows 10 應用程式中的 Fluent Design System<!-- 1195010 -->
Intune Company Portal for Windows 10 應用程式已更新 [Fluent Design System 的瀏覽檢視](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)。 您會發現應用程式側邊多了一個垂直靜態清單，列有最上層的所有頁面。 按一下任何連結都能快速檢視及來回切換頁面。 我們仍持續努力為 Intune 建立適應性更好、更彈性、更直觀及更加容易上手的體驗，而這只是好幾個更新中的第一個。 若要查看更新後的外觀，請參閱[應用程式 UI 的新功能](../whats-new-app-ui.md)。

<!-- ########################## -->
## <a name="march-2018"></a>2018 年 3 月

### <a name="app-management"></a>應用程式管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune---748789---"></a>Microsoft Intune 即將到期的 iOS 企業營運 (LOB) 應用程式警示<!-- 748789 -->

在 Azure 入口網站中，Intune 會提醒您有即將到期的 iOS 企業營運應用程式。 上傳新版 iOS 企業營運應用程式之後，Intune 就會從應用程式清單中移除到期通知。 此到期通知只對新上傳的 iOS 企業營運應用程式有效。 在 iOS LOB 應用程式佈建設定檔到期前 30 天會出現警告。 到期時，警示就會變更為 [已到期]。

#### <a name="customize-your-company-portal-themes-with-hex-codes--1049561---"></a>以十六進位碼自訂您的公司入口網站佈景主題<!--1049561 -->

您可以使用十六進位碼自訂公司入口網站應用程式的佈景主題色彩。 當您輸入您的十六進位碼時，Intune 會判斷可在文字色彩與背景色彩之間提供最高程度對比的文字色彩。 您可以在 [用戶端應用程式]   >  **[公司入口網站]** 中預覽文字色彩，與公司標誌比對。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise---1813081---"></a>Android Enterprise 依據群組來包含和排除應用程式指派<!-- 1813081 -->

Android Enterprise (先前稱為 Android for Work) 支援包含及排除群組，但不支援預先建立的 [所有使用者]  和 [所有裝置]  內建群組。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](../apps/apps-inc-exl-assignments.md)。


### <a name="device-management"></a>裝置管理

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome---2258071---"></a>在 IE、Microsoft Edge 或 Chrome 中將所有裝置匯出成 CSV 檔案<!-- 2258071 -->
在 [裝置]   > [所有裝置]  中，您可以將裝置**匯出**成 CSV 格式的清單。 裝置超過 10,000 部的 Internet Explorer (IE) 使用者可以成功將其裝置匯出成多個檔案。 每個檔案最多可包含 10,000 部裝置。

具有超過 30,000 部以上裝置的 Microsoft Edge 和 Chrome 使用者可以成功將其裝置匯出成多個檔案。 每個檔案最多可包含 30,000 部裝置。

[管理裝置](../remote-actions/device-management.md)可以針對您可以對所管理裝置執行的操作，提供更多的詳細資料。

#### <a name="new-security-enhancements-in-the-intune-service----1637539---"></a>Intune 服務中的新安全性增強功能 <!-- 1637539 -->   

我們已在 Azure 上的 Intune 中導入一個切換，可供 Intune 獨立客戶用來將沒有任何已指派原則的裝置視為 [符合規範]  (關閉安全性功能)，或將這些裝置視為 [不符合規範]  (開啟安全性功能)。 這將可確保只有在評估裝置合規性之後，才能存取資源。

此功能影響您的方式會依您是否已經指派合規性原則而有所不同。

- 如果您是新的或現有的帳戶，而且未將任何合規性原則指派給裝置，則此切換自動設定為 [符合規範]  。 在主控台中，預設是將此功能設定為關閉。 這不會影響任何使用者。
- 如果您是現有的帳戶，而且有任何已獲指派合規性原則的裝置，則此切換會自動設定為 [不符合規範]  。 隨著三月更新的首度發行，預設就會將此功能設定為開啟。

如果您使用合規性原則搭配「條件式存取」(CA)，並且開啟此功能，CA 現在就會封鎖任何未至少已獲指派一個合規性原則的裝置。 除非您至少將一個合規性原則指派給所有裝置，否則與這些裝置關聯且先前已獲允許存取電子郵件的使用者將會失去其存取權。   

請注意，雖然預設切換狀態隨著 Intune 服務的三月更新而立即顯示在 UI 中，但系統並不會立即實施此切換狀態。 在我們讓您的帳戶擁有可運作的切換以進行正式發行前的小眾測試之前，您對此切換進行的任何變更將不會影響裝置合規性。 當我們完成您帳戶的正式發行前小眾測試之後，會透過「訊息中心」通知您。 在您的 Intune 服務進行三月更新之後，這可能會花費幾天的時間。

**其他資訊**：[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection---846515---"></a>增強的越獄偵測<!-- 846515 -->

加強的越獄偵測是一項新的合規性設定，可改進 Intune 評估已越獄裝置的方式。 此設定會使裝置更頻繁地簽入 Intune ，這會使用裝置的位置服務並影響電池使用量。

#### <a name="reset-passwords-for-android-o-devices---1238299---"></a>重設 Android O 裝置的密碼<!-- 1238299 -->
您將能夠使用工作設定檔重設已註冊 Android 8.0 裝置的密碼。 當您向 Android 8.0 裝置傳送「重設密碼」要求時，它會將新的裝置解除鎖定密碼或受控設定檔查問設定成目前的使用者。 這會傳送密碼或查問，並立即生效。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups--1307012---"></a>讓相容性原則以裝置群組中的裝置為目標<!--1307012 -->

您可以讓合規性原則以使用者群組中的使用者為目標。 在此更新中，您可以讓合規性原則以裝置群組中的裝置為目標。 隨著裝置群組一起作為目標的裝置不會收到任何合規性動作。

#### <a name="new-management-name-column---1333586---"></a>新的管理名稱資料行<!-- 1333586 -->
 [裝置] 刀鋒視窗中會提供名為 [管理名稱]  的新資料行。 此名稱會依照下列公式自動產生且不可編輯，並會指派給每一個裝置：
- 所有裝置的預設名稱：<username><em><devicetype></em><enrollmenttimestamp>
- 針對大量新增裝置：<PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

這是在 [裝置] 刀鋒視窗中的可選資料行。 預設並不會提供此資料行，您只能藉由使用資料行選取器來存取它。 裝置名稱不會受到這個新資料行影響。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes--1550837---"></a>每 15 分鐘都會提示 iOS 裝置輸入PIN<!--1550837 -->
將合規性或設定原則套用至 iOS 裝置之後，系統會每隔 15 分鐘提示使用者設定 PIN。 系統會持續提示使用者，直到設定 PIN 為止。

#### <a name="schedule-your-automatic-updates--1805514---"></a>排定自動更新<!--1805514 -->
Intune 可讓您使用 [Windows Update Ring 設定](../protect/windows-update-for-business-configure.md)來控制自動更新安裝。 在此更新中，您可以排定重複發生的更新，包括週、日及時間。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate--2221763---"></a>使用完整辨別名稱作為 SCEP 憑證的主體<!--2221763 -->
當您建立 SCEP 憑證設定檔時，會輸入主體名稱。 在此更新中，您可以使用完整辨別名稱作為主體。 針對 [主體名稱]  ，選取 [自訂]  ，然後輸入 `CN={{OnPrem_Distinguished_Name}}`。 若要使用 `{{OnPrem_Distinguished_Name}}` 變數，請務必將使用 [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onpremisesdistingishedname` 使用者屬性與 Azure AD 同步。

### <a name="device-configuration"></a>裝置設定

#### <a name="enable-bluetooth-contact-sharing---android-for-work--1098983---"></a>啟用藍牙連絡人共用 - Android for Work<!--1098983 -->
Android 預設會防止工作設定檔中的連絡人與藍牙裝置同步。 因此，工作設定檔連絡人不會顯示在藍牙裝置的呼叫者識別碼上。

在此更新中，[Android for Work]   > [裝置限制]   > [工作設定檔設定]  會有一個新的設定：
- 透過藍牙的連絡人共用

Intune 系統管理員可以設定這些設定，以啟用共用。 將裝置與汽車藍牙裝置配對時，這十分有用，而汽車藍牙裝置顯示免持式使用的呼叫者識別碼。 啟用時，會顯示工作設定檔連絡人。 未啟用時，不會顯示工作設定檔連絡人。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source---1690459---"></a>設定閘道管理員以控制 macOS 應用程式下載來源<!-- 1690459 -->

您可以藉由控制可下載應用程式的位置，以設定 Gatekeeper 來為您的裝置提供應用程式安全防護。 您可以設定下列下載來源：**Mac App Store**、**Mac App Store 和已識別的開發人員**或**任何位置**。 您可以藉由按住 Control 並同時按一下來覆寫這些 Gatekeeper 控制措施，以設定使用者是否可以安裝應用程式。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到這些設定。

#### <a name="configure-the-mac-application-firewall---1690461---"></a>設定 Mac 應用程式防火牆<!-- 1690461 -->

您可以設定 Mac 應用程式防火牆。 您可以利用此項目以每一應用程式為單位控制連線，而非以每一連接埠為單位。 這讓您能更輕鬆地取得防火牆保護的優點，也可協助防止不想要的應用程式控制為合法應用程式開啟之網路連接埠。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到此功能。

啟用防火牆設定後，您可以使用兩種策略來設定防火牆：

- 封鎖所有連入連線

   您可以為目標裝置封鎖所有連入連線。 如果您選擇這樣做，系統就會針對所有應用程式封鎖連入連線。

- 允許或封鎖特定應用程式

   您可以允許或封鎖特定的應用程式，使其無法接收連入連線。 您也可以啟用隱形模式，以避免回應探查要求。

#### <a name="detailed-error-codes-and-messages---1376342---"></a>詳細的錯誤碼和訊息<!-- 1376342 -->

在您的 [裝置設定] 中，可以檢視更詳細的錯誤碼和錯誤訊息。 這項改良的報告功能會顯示設定、這些設定的狀態，以及有關疑難排解的詳細資料。

##### <a name="more-information"></a>更多資訊

- 封鎖所有連入連線

   這會封鎖所有共用服務 (例如檔案共用和螢幕共用)，使其無法接收連入連線。 仍允許接收連入連線的系統服務是：
  - configd - 實作 DHCP 與其他網路設定服務
  - mDNSResponder - 實作 Bonjour
  - racoon - 實作 IPSec

    若要使用共用服務，請確認**連入連線**設定為**未設定** (而不是**封鎖**)。

- 隱形模式

   啟用此模式來防止電腦回應探查要求。 電腦仍然會回應已授權應用程式的連入要求。 ICMP (ping) 等未預期的要求都會予以忽略。

#### <a name="disable-checks-on-device-restart--1805490---"></a>停用裝置重新啟動的檢查<!--1805490 -->
Intune 可讓您控制[管理軟體更新](../protect/windows-update-for-business-configure.md)。 在此更新中，預設會提供並啟用 <strong>[重新啟動檢查]</strong> 屬性。 若要跳過重新啟動裝置時進行的典型檢查 (如作用中使用者、電池電量等等) 時，請選取 [跳過]。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings---1746293---"></a>可供部署通道使用的新 Windows 10 Insider Preview 通道<!-- 1746293 -->
現在，當您建立 Windows 10 部署通道時，可以選擇選取下列 Windows 10 Insider Preview 維護通道：
- Windows 測試人員組建 &#8208; 快
- Windows 測試人員組建 &#8208; 慢
- 發行 Windows 測試人員組建 

如需有關這些通道的詳細資訊，請參閱[管理 Insider Preview 組建](https://insider.windows.com/for-business-organization-admin/)。   
如需有關在 Intune 中建立部署通道的詳細資訊，請參閱[管理 Intune 中的軟體更新](../protect/windows-update-for-business-configure.md)。

### <a name="new-windows-defender-exploit-guard-settings---1631893---"></a>新的 Windows Defender 惡意探索防護設定<!-- 1631893 -->

有六項新的 [攻擊面縮減] 設定和擴充的 [受控資料夾存取權: 資料夾保護] 功能可用。 這些設定位於：Device configuration\Profiles\
建立 profile\Endpoint protection\Windows Defender 惡意探索防護。

#### <a name="attack-surface-reduction"></a>攻擊表面縮減

|設定名稱  |設定選項  |說明  |
|---------|---------|---------|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖可執行檔執行，除非它們符合普遍性、存留期或信任的清單準則。|

#### <a name="controlled-folder-access"></a>受控資料夾存取權

|              設定名稱               |                                                              設定選項                                                              | 說明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 資料夾防護 (已實作) | 未設定、啟用、僅稽核 (已實作)<br><br> <strong>新增</strong><br>封鎖磁碟修改、稽核磁碟修改 |             |

保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

### <a name="intune-apps"></a>Intune 應用程式

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview---710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入<!-- 710595 -->

使用 Azure Active Directory (Azure AD) 時，您現在可在行動裝置上限制只有 Intune Managed Browser 應用程式可以存取網站。 在 Managed Browser 中，網站資料會受到保護，而且會與使用者個人資料分開管理。 此外，Managed Browser 將針對受 Azure AD 保護的網站支援單一登入。 登入 Managed Browser，或是在裝置上具有由 Intune 所管理另一個應用程式時使用 Managed Browser 之際，將能讓使用者在無需輸入其認證的情況下，允許 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及其他如透過 Azure App Proxy 所存取內部網路資源的企業網站。 如需詳細資訊，請參閱[什麼是 Azure Active Directory 條件式存取中的存取控制？](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls) \(部分機器翻譯\)。

#### <a name="company-portal-app-for-android-visual-updates--976944---"></a>Android 版公司入口網站的視覺效果更新<!--976944 -->

我們已更新 Android 版公司入口網站應用程式，以遵循 Android 的 [Material Design](https://material.io/) 指導方針。 您可以在[應用程式 UI 最新內容](../whats-new-app-ui.md)一文中看到新圖示的影像。

#### <a name="company-portal-enrollment-improved---1874230-eeready--"></a>已改善的公司入口網站註冊<!-- 1874230 eeready-->
使用者如果是在 Windows 10 1703 組建或更新版本上使用公司入口網站來註冊裝置，現在將能夠在不離開應用程式的情況下，完成第一個註冊步驟。
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists--1725868---"></a>HoloLens 和 Surface Hub 現在會出現在裝置清單 中<!--1725868 -->
我們已新增支援，可向 Android 版公司入口網站應用程式顯示已在 Intune 註冊的 HoloLens 和 Surface Hub 裝置。

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks---1488911---"></a>為大量採購方案 (VPP) 電子書自訂書籍類別<!-- 1488911 -->
您可以建立自訂電子書類別，然後將 VPP 電子書指派給這些自訂電子書類別。 終端使用者便可以看見新建立的電子書類別，以及指派給這些類別的書籍。 如需詳細資訊，請參閱[使用 Microsoft Intune 管理大量採購的應用程式與書籍](../apps/vpp-apps.md)。  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option---2070166---"></a>針對 Windows 版公司入口網站應用程式傳送意見反應選項的支援已變更<!-- 2070166 -->
從 2018 年 4 月 30 日起，Windows 版公司入口網站應用程式中的 [傳送意見反應]  選項僅可在執行 Windows 10 年度更新 (1607) 及更新版本的裝置上執行。 搭配下列版本使用 Windows 版公司入口網站應用程式時，不再支援傳送意見反應的選項：  
- Windows 10，1507 版本  
- Windows 10，1511 版本  
- Windows Phone 8.1 

如果您的裝置執行的是 Windows 10 RS1 或更新版本，請從市集下載最新的 Windows 版公司入口網站應用程式。 如果您執行的是不支援的版本，請繼續透過下列通道傳送意見反應： 
- Windows 10 上的 [意見反應中樞] 應用程式
- 電子郵件 WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings---1631890---"></a>新的 Windows Defender 應用程式防護設定<!-- 1631890 -->

- **啟用圖形加速**：系統管理員能夠啟用 Windows Defender 應用程式防護的虛擬圖形處理器。 此設定可讓 CPU 將圖形轉譯卸載至 vGPU。 使用圖形運算密集的網站或觀賞容器內的影片時，這可以改善效能。

- **SaveFilestoHost**：系統管理員可以讓檔案從容器中執行的 Microsoft Edge 傳遞到主機檔案系統。 開啟這個功能可讓使用者從容器中的 Microsoft Edge 將檔案下載到主機檔案系統。

#### <a name="mam-protection-policies-targeted-based-on-management-state---1665993---"></a>根據管理狀態將 MAM 保護原則設為目標<!-- 1665993 -->
您可以根據裝置管理狀態將 MAM 原則設為目標：
- **Android 裝置** - 您可以將非受控裝置、受 Intune 管理的裝置及受 Intune 管理的 Android Enterprise 設定檔 (先前稱為 Android for Work) 設為目標。
- **iOS 裝置** - 您可以將非受控裝置 (僅限 MAM) 或受 Intune 管理的裝置設為目標。

    > [!NOTE]
    > - 此功能的 iOS 支援會在 2018 年的整個 4 月首度發行。

如需詳細資訊，請參閱[根據裝置管理狀態將應用程式保護原則設為目標](../apps/app-protection-policies.md)。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows---1683758---"></a>Windows 版公司入口網站應用程式中的語言改善<!-- 1683758 -->
我們已改進 Windows 10 版公司入口網站中的語言，不僅對使用者來說更簡單明瞭，也更專屬於您的公司。 若要查看我們所做改進的範例影像，請參閱[應用程式 UI 的新功能](../whats-new-app-ui.md)。

#### <a name="new-additions-to-our-docs-about-user-privacy---1440709---"></a>在我們的文件中新增有關使用者隱私權的部分<!-- 1440709 -->
我們努力讓使用者對其資料和隱私權有更多的控制，因此我們發佈了文件更新，說明如何檢視及移除公司入口網站應用程式儲存在本機的資料。 您可以在下列位置找到這些更新：

- **Android**：[如何從 Intune 移除 Android 裝置](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android (如果使用者已拒絕使用條款)** ：[如果您已拒絕「使用條款」，請移除您的裝置](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**：[從 Intune 移除 iOS 裝置](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**：[從 Intune 移除 Windows 裝置](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>2018 年 2 月

### <a name="device-enrollment"></a>裝置註冊

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶<!-- 747685 -->

Intune 現在支援註冊最多達 100 個來自不同 [Apple 裝置註冊計劃 (DEP)](../enrollment/device-enrollment-program-enroll-ios.md) 或 [Apple School Manager](../enrollment/apple-school-manager-set-up-ios.md) 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

#### <a name="see-enrollment-restrictions-per-user---1634444-eeready-wnready---"></a>查看每位使用者的註冊限制<!-- 1634444 eeready wnready -->
在 [疑難排解]  刀鋒視窗中，您現在可以從 [指派]  清單中選取 [註冊限制]  ，以查看對每位使用者有效的[註冊限制](../enrollment/enrollment-restrictions-set.md)。

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment---747625-eeready---"></a>適用於 Apple 大量註冊的使用者驗證新選項<!-- 747625 eeready -->

> [!NOTE]
> 新的租用戶會立即看到此項目。 現有租用戶的這項功能會在 4 月推出。 全部推出之後，您可能無法存取這些新功能。

Intune 現在可讓您將公司入口網站應用程式用於下列註冊方法，以對裝置進行驗證：

- Apple 裝置註冊方案
- Apple School Manager
- Apple Configurator 註冊

使用 [公司入口網站] 選項時，可以強制執行 Azure Active Directory 多重要素驗證，而不會封鎖這些註冊方法。

使用 [公司入口網站] 選項時，針對使用者親和性註冊，Intune 會跳過 iOS 設定輔助程式中的使用者驗證。 這表示該裝置一開始會註冊為無使用者的裝置，因此不會收到使用者群組的設定或原則。 它只會接收裝置群組的設定和原則。 不過，Intune 會自動在裝置上安裝公司入口網站應用程式。 第一位啟動並登入公司入口網站應用程式的使用者，將會在 Intune 中與該裝置產生關聯。 此時，使用者將會收到其使用者群組的設定和原則。 使用者關聯需要重新註冊才可以變更。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts---747685-eeready---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶<!-- 747685 eeready -->

Intune 現在支援註冊最多達 100 個來自不同 Apple 裝置註冊計劃 (DEP) 或 Apple School Manager 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

### <a name="remote-printing-over-a-secure-network---1709994----"></a>透過安全網路進行遠端列印<!-- 1709994  -->
PrinterOn 的無線行動列印方案，可讓使用者隨時隨地透過安全的網路來進行遠端列印。 PrinterOn 將與適用於 iOS 和 Android 的 Intune APP SDK 整合。 您將能透過管理主控台中的 [應用程式保護原則]  刀鋒視窗，讓應用程式保護原則以此應用程式為目標。 終端使用者將能夠透過 Play 商店或 iTunes 下載 'PrinterOn for Microsoft' 應用程式，以在其 Intune 生態系統內使用。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager---1352411---"></a>macOS 公司入口網站支援使用裝置註冊管理員註冊<!-- 1352411 -->

使用者現在於使用 macOS 公司入口網站進行註冊時，已可以使用裝置註冊管理員。

### <a name="device-management"></a>裝置管理

#### <a name="windows-defender-health-status-and-threat-status-reports--854704---"></a>Windows Defender 健全狀況狀態和威脅狀態報表<!--854704 -->

瞭解 Windows Defender 的健全狀況狀態是管理 Windows 電腦的關鍵。  使用此更新，Intune 會在 Windows Defender 代理程式的健全狀況狀態中新增報告和動作。 在[裝置合規性工作負載](../protect/compliance-policy-monitor.md)中使用狀態積存報表，即可看到需要下列任一項的裝置：
- 簽章更新
- 重新啟動
- 手動介入
- 完整掃描
- 需要介入的其他代理程式狀態

每個狀態類別的鑽研報表都會列出需要注意的個別電腦，或那些回報為**清除**的電腦。

#### <a name="new-privacy-settings-for-device-restrictions--1308926---"></a>裝置限制的新隱私權設定<!--1308926 -->
裝置現在有[兩項新的隱私權設定](../configuration/device-restrictions-windows-10.md#privacy)可用：
- **發佈使用者活動**：將此項設定為 [封鎖]  以防止共用體驗以及在工作切換器中探索最近使用的資源。
- **僅限本機活動**：將此項設定為 [封鎖]  以防止共用體驗，以及僅根據本機活動，在工作切換器中探索最近使用的資源。

#### <a name="new-settings-for-the-microsoft-edge-browser--1469166---"></a>Microsoft Edge 瀏覽器的新設定<!--1469166 -->
現在使用 Microsoft Edge 瀏覽器的裝置有[兩項新設定](../configuration/device-restrictions-windows-10.md#microsoft-edge-browser)可用：[我的最愛檔案路徑]  和 [我的最愛的變更]  。

### <a name="app-management"></a>應用程式管理

#### <a name="protocol-exceptions-for-applications--1035509---"></a>應用程式的通訊協定例外狀況<!--1035509 -->

您現在可以建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況，開啟特定的非受控應用程式。 這類應用程式必須為 IT 所信任。 當資料傳輸原則設為**僅限受管理應用程式** 時，除您建立的例外狀況，資料傳輸仍僅限於受 Intune 管理的應用程式。 您可以使用通訊協定 (iOS) 或套件 (Android) 來建立限制。

例如，您可以將 Webex 套件新增為 MAM 資料傳輸原則的例外狀況。 這樣可以直接在 Webex 應用程式中開啟受控 Outlook 電子郵件訊息中的 Webex 連結。 其他非受控應用程式中的資料傳輸仍會受到限制。 如需詳細資訊，請參閱[應用程式的資料傳輸原則例外狀況](../apps/app-protection-policies-exception.md)。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results---1469193---"></a>Windows 搜尋結果中的 Windows 資訊保護 (WIP) 加密資料<!-- 1469193 -->
Windows 資訊保護 (WIP) 原則中的設定現在可讓您控制 Windows 搜尋結果是否包含 WIP 加密資料。 在 Windows 資訊保護原則的 [進階設定]  中，選取 [允許 Windows 搜尋索引子搜尋加密項目]  來設定此應用程式保護原則選項。 應用程式保護原則必須設為 *Windows 10* 平台，且應用程式原則 [註冊狀態]  必須設為 [註冊]  。 如需詳細資訊，請參閱[允許 Windows 搜尋索引子搜尋加密項目](../apps/windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)。

#### <a name="configuring-a-self-updating-mobile-msi-app---1740840---"></a>設定自行更新的行動 MSI 應用程式<!-- 1740840 -->
您可以設定已知的自行更新行動 MSI 應用程式略過版本檢查程序。 這項功能對於不陷入競爭狀況很有用。 例如，當應用程式開發人員正在執行自動更新的應用程式，也正被 Intune 更新時，就可能發生這種競爭狀況。 雙方都可能嘗試在 Windows 用戶端上強制執行某個版本的應用程式，這可能造成衝突。 對於這些自動更新的 MSI 應用程式，您可以在 [應用程式資訊]  刀鋒視窗中設定 [略過應用程式版本]  設定。 當此設定切換為 [是]  時，Microsoft Intune 將會忽略 Windows 用戶端上安裝的應用程式版本。

#### <a name="related-sets-of-app-licenses-supported-in-intune---1864117---"></a>Intune 支援的相關應用程式授權集<!-- 1864117 -->
Azure 入口網站中的 Intune 現在支援相關的應用程式授權集，作為 UI 中單一應用程式項目。 此外，從商務用 Microsoft Store 同步處理的任何離線授權應用程式都會合併到單一應用程式項目，而個別套件的所有部署詳細資料都會移轉至單一項目。 若要在 Azure 入口網站中檢視相關的應用程式授權集，請選取 [用戶端應用程式]  刀鋒視窗中的 [應用程式授權]  。

### <a name="device-configuration"></a>裝置設定
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption---1463582---"></a>自動加密的 Windows 資訊保護 (WIP) 檔案副檔名<!-- 1463582 -->
Windows 資訊保護 (WIP) 原則中的設定現在可讓您指定，哪些檔案副檔名會在從公司界限內的伺服器訊息區塊 (SMB) 共用 (如 WIP 原則中所定義) 複製時自動加密。

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>設定 Surface Hub 的資源帳戶設定

您現在可以從遠端設定 Surface Hub 的資源帳戶設定。

Surface Hub 會使用資源帳戶驗證 Skype/Exchange 以加入會議。
您會想要建立唯一的資源帳戶，使 Surface Hub 在會議中顯示為會議室。
例如，像**會議室 B41/6233** 的資源帳戶。

> [!NOTE]
> - 如果欄位留白，您會覆寫先前在裝置上設定的屬性。
>
> - Surface Hub 的資源帳戶內容可以動態變更。 例如，開啟密碼輪換。 因此，Azure 主控台中的這些值很可能需要一些時間才能反映裝置的實際狀況。
>
>   若要了解 Surface Hub 目前的設定內容，資源帳戶資訊可以包含在硬體清查 (已有 7 天間隔) 中，或當成唯讀屬性。 為在採取遠端動作後強化精確度，您可以立即在執行動作後取得參數狀態，更新 Surface Hub 上的帳戶/參數。

##### <a name="attack-surface-reduction"></a>攻擊表面縮減

|設定名稱  |設定選項  |說明  |
|---------|---------|---------|
|執行電子郵件中受密碼保護的可執行檔內容|封鎖、稽核、未設定|避免執行透過電子郵件下載的受密碼保護可執行檔。|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖可執行檔執行，除非它們符合普遍性、存留期或信任的清單準則。|

##### <a name="controlled-folder-access"></a>受控資料夾存取權

|              設定名稱               |                                                              設定選項                                                              | 說明 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 資料夾防護 (已實作) | 未設定、啟用、僅稽核 (已實作)<br><br> <strong>新增</strong><br>封鎖磁碟修改、稽核磁碟修改 |             |

保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies--1704133--"></a>新增 Windows 10 和更新版本系統安全性設定的相容性原則<!--1704133-->

Windows 10 相容性設定的新增項目現在已可供使用，但需要防火牆及 Windows Defender 防毒軟體才能包含此內容。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business--1222672--"></a>支援來自商務用 Microsoft Store 的離線應用程式<!--1222672-->
您從商務用 Microsoft Store 購買的離線應用程式現在會同步處理至 Azure 入口網站。 您可以將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile---1728700---"></a>防止終端使用者在工作設定檔中手動新增或移除帳戶<!-- 1728700 -->

當您將 Gmail 應用程式部署到 Android for Work 設定檔時，現在可以使用 Android for Work 裝置限制設定檔中的 [Add and remove accounts] (新增與移除帳戶)  設定，防止終端使用者在工作設定檔中手動新增或移除帳戶。

<!-- ########################## -->
## <a name="january-2018"></a>2018 年 1 月

### <a name="device-enrollment"></a>裝置註冊

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire---1639263---"></a>過期的權杖與即將過期之權杖的警示<!-- 1639263 -->
概觀頁面現在會針對過期的權杖與即將過期的權杖顯示警示。 當您按一下單一權杖的警示時，將會移至權杖的詳細資料頁面。  當您按一下多個權杖的警示時，將會移至所有權杖的清單，其中包含權杖的狀態。 系統管理員應該在到期日之前更新其權杖。

### <a name="device-management"></a>裝置管理

#### <a name="remote-erase-command-support-for-macos-devices---1438084---"></a>macOS 裝置的遠端「清除」命令支援<!-- 1438084 -->

系統管理員可以針對 macOS 裝置遠端發出「清除」命令。

> [!IMPORTANT]
> 清除命令無法回復，應該謹慎使用。

清除命令會從裝置移除所有資料，包括作業系統。 這樣做也會從 Intune 管理移除裝置。 系統不會向使用者發出任何警告，且將在發出命令之際，立即開始清除。

您必須設定 6 位數的復原 PIN。 此 PIN 可用來將已清除的裝置解除鎖定，並開始重新安裝作業系統。 開始進行清除後，PIN 會出現在 Intune 中裝置 [概觀] 刀鋒視窗的狀態列上。 在清除進行期間，PIN 會持續顯示。 完成清除後，裝置會完全從 Intune 管理中消失。 請務必記錄復原 PIN，以供還原裝置的人員來使用。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token---820870---"></a>撤銷 iOS 大量採購方案權杖的授權<!-- 820870 -->
您可針對指定的 VPP 權杖，撤銷所有 iOS Volume Purchasing Program (VPP) 應用程式的授權。

### <a name="app-management"></a>應用程式管理

#### <a name="revoking-ios-volume-purchase-program-apps----820863---"></a>撤銷 iOS 大量採購方案應用程式 <!-- 820863 -->
對於具有一或多個 iOS Volume Purchasing Program (VPP) 應用程式的指定裝置，您可將裝置撤銷與其建立關聯的裝置應用程式授權。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]  。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](../apps/vpp-apps-ios.md)。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type---1332318---"></a>將 Office 365 行動應用程式指派給使用內建應用程式類型的 iOS 和 Android 裝置<!-- 1332318 -->
**內建**應用程式類型讓您可更輕鬆地建立 Office 365 應用程式，並將其指派給您管理的 iOS 及 Android 裝置。 這些應用程式包括 0365 應用程式，例如 Word、Excel、PowerPoint 和 OneDrive。 您可以將特定的應用程式指派給應用程式類型，並編輯應用程式資訊設定。

#### <a name="including-and-excluding-app-assignment-based-on-groups---1406920---"></a>依據群組來包含和排除應用程式指派<!-- 1406920 -->

在應用程式指派期間和選取指派類型後，您可選取要包含的群組及要排除的群組。

### <a name="device-configuration"></a>裝置設定

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments----1480316---"></a>您可包含和排除指派，將應用程式設定原則指派給群組 <!-- 1480316 -->

您可使用包含和排除指派的組合，將應用程式設定原則指派給一群使用者和裝置。 您可選擇自選群組或虛擬群組作為指派。 虛擬群組可以包括 [所有使用者]  、[所有裝置]  或 [所有使用者及所有裝置]  。

#### <a name="support-for-windows-10-edition-upgrade-policy-----903672archived-1119689---"></a>支援 Windows 10 版本升級原則  <!-- 903672(archived), 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級至 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資料，請參閱[如何設定 Windows 10 版本升級](../configuration/edition-upgrade-configure-windows-10.md)。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal----1737088-1634311---"></a>Intune 的條件式存取原則只能從 Azure 入口網站使用 <!-- 1737088 1634311 -->

從這個版本開始，您必須在 [Azure 入口網站](https://portal.azure.com)，從 [Azure Active Directory]   > [條件式存取]  設定及管理您的條件式存取原則。 為了方便起見，您也可以從 Azure 入口網站中的 Intune 存取此刀鋒視窗，位置是 [Intune]   > [條件式存取]  。

#### <a name="updates-to-compliance-emails--1637547---"></a>更新相容性電子郵件<!--1637547 -->

當傳送電子郵件以報告不符合規範的裝置時，會包含不符合規範之裝置的相關詳細資料。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="new-functionality-for-the-resolve-action-for-android-devices--1583480--"></a>Android 裝置的「解決」動作新功能<!--1583480-->

Android 公司入口網站應用程式將**更新裝置設定**的「解決」動作擴充為解決[裝置加密問題](/intune-user-help/encrypt-your-device-android)。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10--676506--"></a>Windows 10 版公司入口網站應用程式提供遠端鎖定<!--676506-->
使用者現在可以從 Windows 10 的公司入口網站應用程式遠端鎖定其裝置。 這不會顯示在他們正使用的本機裝置上。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10--676546--"></a>Windows 10 版公司入口網站應用程式更容易解決相容性問題<!--676546-->
使用 Windows 裝置的終端使用者將可在公司入口網站應用程式中點選不相容的原因。 在可能的情況下，這將會將他們帶到 [設定] 應用程式中的正確位置以修正該問題。

<!-- ########################## -->
## <a name="december-2017"></a>2017 年 12 月

### <a name="device-configuration"></a>裝置設定

#### <a name="new-automatic-redeployment-setting---1469168---"></a>新的自動重新部署設定<!-- 1469168 -->
**自動重新部署**設定允許具有系統管理權限的使用者，在裝置鎖定畫面上使用 **CTRL + Win + R** 來刪除所有使用者資料和設定。 裝置會自動重新設定並重新註冊以納入管理。 您可以在 [Windows 10] > [裝置限制] > [一般] > [自動重新部署] 下找到此設定。 如需詳細資料，請參閱 [Windows 10 的 Intune 裝置限制設定](../configuration/device-restrictions-windows-10.md#general)。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy----903672--1119689---"></a>支援 Windows 10 版本升級原則中的其他來源版本 <!-- 903672,  1119689 -->
您現在可以使用 Windows 10 版本升級原則，從其他 Windows 10 版本 (Windows 10 專業版、Windows 10 專業教育版、Windows 10 Cloud 等) 進行升級。 在此版本之前，支援的版本升級路徑十分有限。 如需詳細資訊，請參閱[如何設定 Windows 10 版本升級](../configuration/edition-upgrade-configure-windows-10.md)。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings---1335507---"></a>新的 Windows Defender 資訊安全中心 (WDSC) 裝置組態設定檔設定<!-- 1335507 -->

Intune 在 [端點保護] 下新增了新的裝置組態設定檔設定區段，名為 [Windows Defender 資訊安全中心]  。 IT 系統管理員可以設定終端使用者可存取的 Windows Defender 資訊安全中心應用程式方針。 如果 IT 系統管理員在 Windows Defender 資訊安全中心應用程式中隱藏某個方針，則與該隱藏方針相關聯的所有通知都不會顯示在使用者的裝置上。

以下是系統管理員可從 Windows Defender 資訊安全中心裝置組態設定檔設定中隱藏的方針：
- 病毒與威脅防護
- 裝置效能與健康情況
- 防火牆與網路保護
- 應用程式與瀏覽器控制
- 家長監護選項

IT 系統管理員也可以自訂使用者可接收的通知。 例如，您可以設定是否讓使用者接收由 WDSC 中可見方針所產生的所有通知，或僅接收重要通知。 非重大通知包括 Windows Defender 防毒軟體活動的定期摘要，以及掃描完成時的通知。 所有其他通知都被視為重大通知。 此外，您也可以自訂通知內容本身，例如，您可以在顯示於使用者裝置上的通知中內嵌 IT 連絡資訊。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling---1361755---"></a>針對 SCEP 和 PFX 憑證處理的多連接器支援<!-- 1361755 -->

使用內部部署 NDES 連接器將憑證傳遞至裝置的客戶，現在可在單一租用戶上設定多個連接器。

此新功能支援下列案例：

- **高可用性**

每個 NDES 連接器都會從 Intune 提取憑證要求。  如果有某個 NDES 連接器離線，其他連接器將可以繼續處理要求。

#### <a name="customer-subject-name-can-use-aad_device_id-variable----1468599---"></a>客戶主體名稱可以使用 AAD_DEVICE_ID 變數 <!-- 1468599 -->

當您在 Intune 中建立 SCEP 憑證設定檔時，現在可在建置自訂的主體名稱時使用 AAD_DEVICE_ID 變數。   當使用此 SCEP 設定檔要求憑證時，該變數會以要求憑證之裝置的 AAD 裝置識別碼來取代。


### <a name="device-management"></a>裝置管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747---"></a>使用 Intune 裝置相容性引擎管理 Jamf 註冊的 macOS 裝置<!-- 1592747 -->
您現在可以使用 Jamf 將 macOS 裝置狀態資訊傳送到 Intune，然後 Intune 會評估裝置是否符合 Intune 主控台中定義的合規性原則。 根據裝置合規性狀態以及其他條件 (例如位置、使用者風險等)，條件式存取將會針對存取雲端的 macOS 裝置和與 Azure AD 連線之內部部署應用程式 (包括 Office 365) 強制執行合規性檢查。 深入了解[設定 Jamf 整合](../protect/conditional-access-integrate-jamf.md)與[強制執行 Jamf 受控裝置的合規性](../protect/conditional-access-assign-jamf.md)。

#### <a name="new-ios-device-action-----1424701---"></a>新的 iOS 裝置動作  <!-- 1424701 -->

您現在可以關閉 iOS 10.3 受監督的裝置。 這個動作會立即關閉裝置，而不會警告使用者。 您可以在 [裝置]  工作負載中選取裝置時，於裝置屬性中找到 [關機 (僅限受監督)]  動作。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices---1468103---"></a>不允許 Samsung Knox 裝置的日期/時間變更<!-- 1468103 -->

我們已加入新的功能，可讓您封鎖 Samsung Knox 裝置上的日期與時間變更。 您可以在 [裝置組態設定檔]   > [裝置限制 (Android)]   > [一般]  中找到此功能。

#### <a name="surface-hub-resource-account-supported---1566442----"></a>支援 Surface Hub 資源帳戶<!-- 1566442  -->

已加入新的裝置動作，以便系統管理員對與 Surface Hub 相關聯的資源帳戶進行定義及更新。

Surface Hub 會使用資源帳戶向 Skype/Exchange 進行驗證以加入會議。 您可以建立唯一的資源帳戶，使 Surface Hub 在會議中顯示為會議室。 例如，資源帳戶可能會顯示為*會議室 B41/6233*。 Surface Hub 的資源帳戶 (也稱為裝置帳戶) 通常需要針對會議室位置，以及在其他資源帳戶參數需要被變更時進行設定。

當系統管理員想要更新裝置上的資源帳戶時，他們必須提供目前與裝置相關聯的 Active Directory/Azure Active Directory 認證。 如果裝置有開啟密碼輪換，則系統管理員必須移至 Azure Active Directory 以找出密碼。

> [!NOTE]
> 所有的欄位會以組合方式向下傳送，並覆寫先前設定的所有欄位。 空白欄位也會覆寫現有欄位。

以下是系統管理員可以設定的設定：

- **資源帳戶**
  - **Active Directory 使用者**

    Domainname\username 或使用者主體名稱 (UPN)：user@domainname.com

  - **密碼**

- **選擇性資源帳戶參數** (必須使用指定的資源帳戶進行設定)

  - **密碼輪換期間**

    確保帳戶密碼每週會由 Surface Hub 基於安全性考量進行自動更新。 若要在啟用此設定後設定任何參數，必須先將 Azure Active Directory 中的帳戶進行密碼重設。

  - **SIP (工作階段初始通訊協定) 位址**

    只有在自動探索失敗時才會使用。

  - **電子郵件**

    裝置/資源帳戶的電子郵件地址。

  - **Exchange 伺服器**

    只有自動探索失敗時才需要。

  - **行事曆同步處理**

    指定是否啟用行事曆同步處理和其他 Exchange 伺服器服務。 例如：會議同步處理。

#### <a name="install-office-apps-on-macos-devices---1494311---"></a>在 macOS 裝置上安裝 Office 應用程式<!-- 1494311 -->
您現在可在 macOS 裝置上安裝 Office 應用程式。 這個新的應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 及 OneNote。 這些應用程式也會隨附於 Microsoft AutoUpdate (MAU)，以協助保護您的應用程式並使它保持在最新狀態。

### <a name="app-management"></a>應用程式管理

#### <a name="delete-an-ios--volume-purchasing-program-token---820879---"></a>刪除 iOS 大量採購方案權杖<!-- 820879 -->
您可以使用主控台來刪除 iOS 大量採購方案 (VPP) 權杖。 當您擁有重複的 VPP 權杖執行個體時，這可能是必要的。

### <a name="intune-apps"></a>Intune 應用程式


### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data---1667026---"></a>名為 Current User 之新實體集合限於目前作用中的使用者資料<!-- 1667026 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](../developer/reports-ref-data-model.md)。

### <a name="updated-graph-apis---1736360---"></a>更新的 Graph API<!-- 1736360 -->

在此版本中，我們已更新一些 Intune 的搶鮮版 (Beta) Graph API。 如需詳細資訊，請查看每月 [Graph API 變更記錄](https://developer.microsoft.com/graph/docs/concepts/changelog) \(英文\)。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-supports-windows-information-protection-wip-denied-apps---1479103---"></a>Intune 支援 Windows 資訊保護 (WIP) 拒絕的應用程式<!-- 1479103 -->
您可以在 Intune 中指定拒絕的應用程式。 如果應用程式遭到拒絕，它會被封鎖而無法存取公司資訊，效果與允許的應用程式清單相反。 如需詳細資訊，請參閱 [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Windows 資訊保護的建議拒絕清單)。

<!-- ########################## -->
## <a name="november-2017"></a>2017 年 11 月

### <a name="troubleshoot-enrollment-issues----746324---"></a>針對註冊問題進行疑難排解 <!-- 746324 -->

[疑難排解]  工作區現在會顯示使用者註冊問題。 其中包含問題的詳細資料與建議的補救步驟，可協助系統管理員和技術服務人員針對相關問題進行疑難排解。 未擷取特定註冊問題，某些錯誤可能也沒有補救建議。

### <a name="group-assigned-enrollment-restrictions---747598---"></a>群組指派的註冊限制<!-- 747598 -->

身為 Intune 系統管理員，您現在可以[為使用者群組建立自訂的裝置類型和裝置限制註冊限制](../enrollment/enrollment-restrictions-set.md)。

Intune Azure 入口網站可讓您每種限制類型最多建立 25 個執行個體，以指派給使用者群組。 群組指派的限制會覆寫預設的限制。

限制類型的所有執行個體都使用嚴格排序的清單維護。 此順序會定義衝突解決方法的優先順序值。 受到多個限制執行個體影響的使用者，只受擁有最高優先順序值的執行個體限制。 您可以變更指定的執行個體優先順序，只要將它拖曳到清單中的不同位置即可。

當 Android for Work 設定從 [Android For Work 註冊] 功能表移轉到 [註冊限制] 功能表時，即發佈這項功能。 因為這項移轉可能需要花費數天，而您的帳戶可能要升級 11 月版本的其他組件後，您才會看到 [註冊限制] 的群組指派成為啟用狀態。

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors---1528104---"></a>支援多個網路裝置註冊服務 (NDES) 連接器<!-- 1528104 -->

NDES 可讓行動裝置依據簡單憑證註冊通訊協定 (SCEP) 在沒有網域認證的情況下取得憑證。
使用這項更新，可支援多個 NDES 連接器。

### <a name="manage-android-for-work-devices-independently-from-android-devices---1490731-eeready--"></a>從 Android 裝置獨立管理 Android for Work 裝置<!-- 1490731 EEready-->

Intune 支援從 Android 平台獨立管理 Android for Work 裝置的註冊。 這些設定在 [裝置註冊]   > [註冊限制]   > [裝置類型限制]  下管理。 (原位於 [裝置註冊]   > [Android for Work 註冊]   > [Android for Work 註冊設定]  下。)

根據預設，Android for Work 裝置設定與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。

如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

使用新設定時，請考慮下列各點：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>之前是否從未啟動 Android for Work 註冊

在預設的裝置類型限制中封鎖新的 Android for Work 平台。 啟動功能後，您可以允許裝置註冊 Android for Work。 若要這樣做，請變更預設值，或建立新的裝置類型限制來取代預設的裝置類型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>是否曾啟動 Android for Work 註冊

如果曾經啟動過，您的情況會隨您選擇的設定而異：

| 設定 | 預設裝置類型限制中的 Android for Work 狀態 | 備忘錄 |
| --- | --- | --- |
| **將所有裝置當成 Android 管理** | 封鎖 | 所有 Android 裝置都必須註冊，但不是 Android for Work。 |
| **將支援的裝置當成 Android for Work 管理** | 允許 | 所有支援 Android for Work 的裝置都必須註冊 Android for Work。 |
| **將這些群組中僅限使用者的受支援裝置當成 Android for Work 管理** | 封鎖 | 已建立不同的裝置類型限制原則，以覆寫預設值。 此原則會定義您先前選取的群組，以允許 Android for Work 註冊。 所選群組內的使用者仍可以繼續註冊他們的 Android for Work 裝置。 所有其他使用者則限制不能註冊 Android for Work。 |

無論什麼情況，都會保留您預期的法規。 您不需要執行任何動作，即能維持您環境中 Android for Work 的全域或各群組額度。

### <a name="google-play-protect-support-on-android---908720---"></a>Android 中的 Google Play Protect 支援<!-- 908720 -->

在 Android Oreo 版本中，Google 引進名為 Google Play Protect 的安全性功能套件，可讓使用者和組織執行安全的應用程式和保護 Android 映像。 Intune 現在支援 Google Play Protect 功能，包括 SafetyNet 遠端證明。 系統管理員可以設定合規性原則需求，藉此要求設定 Google Play Protect 且其狀況良好。
[SafetyNet 裝置證明]  設定可要求裝置連線至 Google 服務，以驗證裝置狀況良好且未遭入侵。 系統管理員也可以設定 Android for Work 的組態設定檔設定，以要求已安裝的應用程式必須經過 Google Play 服務驗證。 如果裝置不符合 Google Play 安全防護需求的規範，條件式存取可能會禁止使用者存取公司資源。

- 了解[如何建立可啟用「Google Play 安全防護」的裝置合規性原則](../protect/compliance-policy-create-android.md)。

### <a name="text-protocol-allowed-from-managed-apps---1414050----"></a>允許來自受控應用程式的文字通訊協定<!-- 1414050  -->

Intune App SDK 管理的應用程式可傳送 SMS 訊息。


### <a name="app-install-report-updated-to-include-install-pending-status---1249446---"></a>已更新應用程式安裝報表，以包含安裝擱置中狀態<!-- 1249446 -->  

透過 [用戶端應用程式]  工作負載中的 [應用程式]  清單，每個應用程式可存取的**應用程式安裝狀態**報告，現在包含使用者和裝置的**安裝擱置中**計數。

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection---1391759---"></a>適用於行動裝置威脅偵測的 iOS 11 應用程式清查 API<!-- 1391759 -->

Intune 會從個人和公司擁有的裝置收集應用程式清查資訊，並供 Lookout for Work 等行動裝置威脅偵測 (MTD) 提供者來擷取。 您可以收集 iOS 11+ 裝置使用者的應用程式清查。

**應用程式清查**  
個人擁有和公司擁有的 iOS 11+ 裝置清查都會傳送給您的 MTD 服務提供者。 應用程式清查中的資料包括：

- 應用程式識別碼
- 應用程式版本
- 應用程式簡短版本
- 應用程式名稱
- 應用程式套件組合大小
- 應用程式動態大小
- 應用程式是否已驗證
- 應用程式是否受管理

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone---1463747-wnready---"></a>將混合式 MDM 使用者和裝置移轉至 Intune 獨立版<!-- 1463747 wnready -->
Azure 入口網站中現在提供新的程序和工具，以將使用者和其裝置從混合式 MDM 移至 intune，讓您可以執行下列工作：
- 將原則與設定檔從 Configuration Manager 主控台複製到 Azure 入口網站的 Intune
- 將使用者子集移至 Azure 入口網站的 Intune，同時將其餘部分保留在混合式 MDM 中
- 將裝置移轉至 Azure 入口網站的 Intune 但不需要重新註冊

### <a name="on-premises-exchange-connector-high-availability-support----676614---"></a>內部部署 Exchange Connector 高可用性支援 <!-- 676614 -->
在 Exchange Connector 使用指定的 Client Access Server (CAS) 建立與 Exchange 的連線之後，連接器現在便能夠探索其他 CAS。 如果無法使用主要的 CAS，連接器將容錯移轉至另一個 CAS (如果有的話)，直到有可用的主要 CAS 為止。 如需詳細資訊，請參閱[內部部署 Exchange Connector 高可用性支援](../protect/exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support)。

### <a name="remotely-restart-ios-device-supervised-only---1424595---"></a>從遠端重新啟動 iOS 裝置 (僅限受監督)<!-- 1424595 -->

您現在可以使用裝置動作觸發受監督的 iOS 10.3+ 裝置，令它重新啟動。 如需使用裝置重新啟動動作的詳細資訊，請參閱[使用 Intune 從遠端重新啟動裝置](../remote-actions/device-restart.md)。

> [!Note]
> 此命令需要受監督的裝置和**裝置鎖定**存取權限。 裝置隨即重新啟動。 密碼鎖定的 iOS 裝置重新啟動後，不會重新加入 Wi-Fi 網路；重新啟動後，它們可能無法與伺服器通訊。

### <a name="single-sign-on-support-for-ios---1333645---"></a>iOS 的單一登入支援<!-- 1333645 -->  

您可以讓 iOS 使用者使用單一登入。 編碼成在單一登入裝載中尋找使用者認證的 iOS 應用程式，因為有此裝載設定更新，所以很實用。 您也可以使用 UPN 和 Intune 裝置識別碼來設定主體名稱和領域。 如需詳細資料，請參閱[設定 Intune 以進行 iOS 裝置單一登入](../configuration/ios-device-features-settings.md#single-sign-on)。

### <a name="add-find-my-iphone-for-personal-devices--1427287--"></a>新增個人裝置的「尋找我的 iPhone」<!--1427287-->
您現在可以檢視 iOS 裝置是否開啟 [啟用鎖定]。 這項功能以前位在 intune 傳統入口網站。

### <a name="remotely-lock-managed-macos-device-with-intune---1437691---"></a>使用 Intune 從遠端鎖定受控 macOS 裝置<!-- 1437691 -->

您可以鎖定遺失的 macOS 裝置，並設定 6 位數的復原 PIN。 鎖定時，[裝置概觀]  刀鋒視窗會顯示 PIN，直到傳送另一個裝置動作為止。

如需詳細資訊，請參閱[使用 Intune 從遠端鎖定受管理的裝置](../remote-actions/device-remote-lock.md)。

### <a name="new-scep-profile-details-supported---1559808---"></a>支援新的 SCEP 設定檔詳細資料<!-- 1559808 -->

現在於 Windows、iOS、macOS 和 Android 平台上建立 SCEP 設定檔時，系統管理員可以設定其他設定。  系統管理員可以設定 IMEI、序號或一般名稱，包括使用主體名稱格式的電子郵件。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset---1588489---"></a>重設為原廠設定時保留資料 <!--1588489 -->
將 Windows 10 1709 版和更新版本恢復出廠預設值時，有一項新的功能可以使用。 管理員可以指定是否透過恢復出廠預設值將裝置註冊及其他佈建資料保留在裝置上。

下列資料會透過原廠重設保留：
- 與裝置建立關聯的使用者帳戶
- 電腦狀態 (網域加入，已加入 Azure Active Directory)
- MDM 註冊
- OEM 安裝的應用程式 (市集和 Win32 應用程式)
- 使用者設定檔
- 使用者設定檔外的使用者資料
- 使用者自動登入

不保留下列資料：
- 使用者檔案
- 使用者安裝的應用程式 (市集和 Win32 應用程式)
- 非預設的裝置設定


### <a name="window-10-update-ring-assignments-are-displayed---1621837---"></a>顯示 Windows 10 更新通道指派<!-- 1621837 -->
當要針對您正在檢視的使用者進行**疑難排解**時，您會看到所有 Windows 10 更新通道指派。  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings----1455974----"></a>Windows Defender 進階威脅防護回報頻率設定 <!-- 1455974  -->
Windows Defender 進階威脅防護 (WDATP) 服務允許管理員管理受管理裝置的回報頻率。 使用新的 [加速遙測回報頻率]  選項，WDATP 可以更頻繁地收集資料及評估風險。 回報預設值最佳化速度及效能。 增加回報頻率對高風險裝置很重要。 此設定位在**裝置設定**的 **Windows Defender ATP** 設定檔中。

### <a name="audit-updates---1412961---"></a>稽核更新<!-- 1412961 -->  
Intune 稽核會提供與 Intune 相關的變更作業記錄。  擷取所有建立、更新、刪除和遠端工作作業，並保留一年。  Azure 入口網站提供每個工作負載過去 30 天的稽核資料檢視，且可篩選。  對應的圖形 API 可讓您擷取去年儲存的稽核資料。

[稽核] 位在**監視器**群組下。 每個工作負載都有 [稽核記錄檔]  功能表項目。

### <a name="company-portal-app-for-macos-is-available--1541700--"></a>macOS 版公司入口網站應用程式已推出<!--1541700-->
macOS 上的 Intune 公司入口網站的體驗已有更新，可針對使用者所有已註冊的裝置，以最佳方式清楚地顯示使用者所需的所有資訊與合規性通知。 此外，「Intune 公司入口網站」部署至裝置之後，適用於 macOS 的 Microsoft AutoUpdate 會提供其更新。 您可以從 macOS 裝置登入 Intune 公司入口網站，以下載適用於 macOS 的新 Intune 公司入口網站。

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps----1248473---"></a>Microsoft Planner 現在是已核准應用程式的行動裝置應用程式管理 (MAM) 清單的一部分 <!-- 1248473 -->
適用於 iOS 和 Android 的 Microsoft Planner 應用程式，現已是行動裝置應用程式管理 (MAM) 的核准應用程式之一。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，將應用程式設定至所有租用戶。
- 深入了解[已核准應用程式的 MAM 清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices-----1547061---"></a>iOS 裝置上個別應用程式 VPN 的需求更新頻率  <!-- 1547061 -->  
系統管理員現在可能會移除 iOS 裝置上應用程式的個別 App VPN 需求；受影響的裝置將在它們下一次 Intune 簽入後 (通常在 15 分鐘內發生)。  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector---885457---"></a>適用於 Exchange 連接器的 System Center Operations Manager 管理組件支援<!-- 885457 -->
適用於 Exchange 連接器的 System Center Operations Manager 管理組件現在可協助您剖析 Exchange 連接器記錄。 此功能可在您需要針對問題進行疑難排解時，為您提供不同方式來監視服務。

### <a name="co-management-for-windows-10-devices----1243445---"></a>Windows 10 裝置的共同管理 <!-- 1243445 -->
共同管理是一種可讓您從傳統管理過渡到現代化管理的解決方案，並提供您使用分段式方法的轉換過程。 本質上來說，共同管理解決方案可讓 Windows 10 裝置同時受 Configuration Manager 和 Microsoft Intune 管理，並聯結到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  如果您無法一次到位，此設定提供隨時間逐步實行現代化的轉換過程，讓您依據組織進展的步調來進行。  

### <a name="restrict-windows-enrollment-by-os-version---245498---"></a>依 OS 版本限制 Windows 註冊<!-- 245498 -->
您現在能夠以 Intune 系統管理員的身分指定裝置註冊的 Windows 10 最低與最高版本。 您現可在 [平台設定]  刀鋒視窗設定這些限制。

Intune 會繼續支援註冊 Windows 8.1 電腦與手機。 不過，只有 Windows 10 版本能夠設定最低與最高限制。 若要允許 8.1 裝置的註冊，請在最低限制留空。

### <a name="alerts-for-windows-autopilot-unassigned-devices----1631236---"></a>Windows Autopilot 未指派裝置的警示 <!-- 1631236 -->
在 [Microsoft Intune]   > [裝置註冊]   > [概觀]  頁面上，有新的警示可供 Windows AutoPilot 未指派的裝置使用。 此警示能夠顯示有多少 AutoPilot 方案的裝置未指派 AutoPilot 部署設定檔。 您可以使用警示中的資訊來建立設定檔，並加以指派至未指派的裝置。 當您按一下警示時，會看到 Windows AutoPilot 裝置的完整清單，以及這些裝置的詳細資訊。 如需詳細資訊，請參閱[使用 Windows AutoPilot 部署方案註冊 Windows 裝置](../enrollment/enrollment-autopilot.md)。


### <a name="refresh-button-for-devices-list------1333581---"></a>裝置清單的 [重新整理] 按鈕   <!-- 1333581 -->
因為裝置清單並不會自動重新整理，所以您可以使用新的 [重新整理] 按鈕來更新清單中顯示的裝置。

### <a name="support-for-symantec-cloud-certification-authority-ca----1333638---"></a>支援 Symantec 雲端憑證授權單位 (CA) <!-- 1333638 -->    
Intune 現在支援 Symantec 雲端 CA，因此 Intune 憑證連接器可以將來自 Symantec 雲端 CA 的 PKCS 憑證簽發給受 Intune 管理的裝置。 如果您已經使用 Intune 憑證連接器與 Microsoft 憑證授權單位 (CA)，則可以使用現有的 Intune 憑證連接器安裝程式來新增 Symantec CA 支援。

### <a name="new-items-added-to-device-inventory----1404455---"></a>新增至裝置清查的項目  <!--1404455 -->
下列新項目現在可用於[已註冊裝置執行的清查](../remote-actions/device-inventory.md)：

- Wi-Fi Mac 位址
- 儲存空間總計
- 可用空間總計
- MEID
- 用戶載波

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>依據裝置的 Android 安全性修補程式下限，來設定應用程式的存取權<!-- 1278463 -->   
系統管理員可以定義裝置必須安裝的 Android 安全性修補程式下限，才能以受管理帳戶來存取受管理的應用程式。

> [!Note]  
> 這項功能只能限制 Android 6.0+ 裝置上由 Google 發行的安全性修補程式。

### <a name="app-conditional-launch-support---1193313---"></a>支援條件式啟動應用程式<!-- 1193313 -->
現在，IT 系統管理員可以透過 Azure 管理入口網站，設定在應用程式啟動時強制執行密碼，而不是透過行動裝置應用程式管理 (MAM) 的數字 PIN。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 此版 Intune 將**僅在 iOS 上**啟用這項功能。 Intune 支援密碼的方式與數字 PIN 類似，它會設定長度下限，並允許重複的字元和順序。 此功能需要應用程式 (亦即，WXP、Outlook、Managed Browser、Yammer) 的參與來就地整合 Intune App SDK 與此功能的程式碼，以在目標應用程式中強制執行密碼設定。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report---1233999---"></a>裝置安裝狀態報告表的企業營運應用程式版本號碼<!-- 1233999 -->
在此版本中，裝置安裝狀態報告會顯示適用於 iOS 和 Android 的企業營運應用程式版本號碼。 您可以使用這些資訊來針對應用程式進行疑難排解，或找出執行過時應用程式版本的裝置。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile---951708---"></a>系統管理員現在可以使用裝置組態設定檔來設定裝置的防火牆設定<!-- 951708 -->   
系統管理員可以開啟裝置的防火牆，並針對網域、私用網路和公用網路設定各種通訊協定。  您可以在 "Endpoint Protection" 設定檔中找到這些防火牆設定。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization---958257---"></a>Windows Defender 應用程式防護可依據組織的定義，協助保護裝置避免不受信任網站的威脅<!-- 958257 -->   
系統管理員可以使用 Windows 資訊保護工作流程，或裝置設定下方的全新「網路界限」設定檔，將網站定義為「受信任」網站或「公司」網站。 如果使用 Microsoft Edge 進行檢視，則會開啟任何未列在 64 位元 Windows 10 裝置受信任網路界限上的網站，而不是在 Hyper-V 虛擬電腦的瀏覽器中開啟。

您可以在 "Endpoint Protection" 設定檔的裝置組態設定檔中，找到應用程式防護。 系統管理員可以從該處設定虛擬瀏覽器和主機電腦之間的互動、不受信任的網站和信任網站之間的互動，並儲存虛擬瀏覽器中產生的資料。 若要在裝置上使用應用程式防護，您必須先設定網路界限。 每部裝置都只能定義一個網路界限。  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps---1031096---"></a>Windows 10 Enterprise 的 Windows Defender 應用程式控制具有僅信任已獲授權應用程式的模式<!-- 1031096 -->    
每天有高達數千種的惡意檔案流竄出來，單純使用防毒特徵偵測來對抗惡意程式碼時，可能再也無法有效抵禦新的攻擊。 使用 Windows 10 Enterprise 的 Windows Defender 應用程式控制時，您可以將裝置設定的模式，從信任防毒軟體或其他安全性解決方案未封鎖的應用程式，變更為讓作業系統僅信任獲得企業授權的應用程式。 您可以將 Windows Defender 應用程式控制中的應用程式指派為信任。

使用 Intune 時，您可以在「僅限稽核」模式或「強制執行」模式中設定應用程式控制原則。 在「僅限稽核」模式中執行時，不會封鎖應用程式。 「僅限稽核」模式會在本機用戶端記錄檔中記錄所有事件。 您也可以設定是否只允許執行 Windows 元件和 Microsoft Store 應用程式，或允許依據智慧型安全性圖表的定義，執行評價良好的其他應用程式。

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10---1063615---"></a>Window Defender 惡意探索防護是一組 Windows 10 的全新入侵偵測功能<!-- 1063615 -->   
Window Defender 惡意探索防護包含自訂規則，可降低擅用應用程式的可能性、避免巨集和指令碼的威脅、自動封鎖評價不良的 IP 位址網路連線，並協助資料抵禦勒索軟體和未知的威脅。 Window Defender 惡意探索防護是由下列元件所組成：

- **受攻擊面縮小 (ASR)** 提供的規則可讓您避免巨集、指令碼和電子郵件的威脅。
- **控制存取資料夾**會自動封鎖對受保護資料夾內容的存取。
- **網路篩選**會封鎖任何應用程式與評價不良 IP/網域的輸出連線。
- **惡意探索保護**可提供記憶體限制、控制流程限制和原則限制，以用來保護應用程式不受惡意探索的威脅。

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices---790537---"></a>在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼<!-- 790537 -->

Intune 管理延伸模組可讓您在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 延伸模組可補充 Windows 10 的行動裝置管理 (MDM) 功能，讓您更輕鬆地轉移至新式管理。 如需詳細資料，請參閱[在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼](../apps/intune-management-extension.md)。

### <a name="new-device-restriction-settings-for-windows-10--------1308850---"></a>Windows 10 的新裝置限制設定     <!-- 1308850 -->
- 傳訊 (僅限行動裝置) - 停用測試或 MMS 訊息
- 密碼 - 可啟用 FIPS 和使用 Windows Hello 次要裝置以進行驗證的設定 
- 顯示 - 可開啟或關閉舊版應用程式 GDI 縮放比例的設定

### <a name="windows-10-kiosk-mode-device-restrictions---1308872---"></a>Windows 10 Kiosk 模式的裝置限制<!-- 1308872 -->   
您可以將 Windows 10 裝置使用者限制在 kiosk 模式中，使其僅可使用一組預先定義的應用程式。  若要這樣做，請建立 Windows 10 裝置限制設定檔，然後進行 Kiosk 設定。

Kiosk 模式支援兩種模式：**單一應用程式** (只允許使用者執行一個應用程式) 或**多重應用程式** (允許存取一組應用程式)。  您可定義使用者帳戶和裝置名稱，以決定支援的應用程式。  當使用者登入時，就只能使用定義的應用程式。  若要進一步了解，請參閱 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

Kiosk 模式具有下列要求：

- Intune 必須為 MDM 授權單位。
- 目標裝置上必須已安裝應用程式。
- 裝置必須[已正確佈建](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

### <a name="new-device-configuration-profile-for-creating-network-boundaries---1311967---"></a>可建立網路界限的新裝置組態設定檔<!-- 1311967 -->   
稱為**網路界限**的新裝置組態設定檔可以與其他裝置組態設定檔一起找到。 您可以使用這個設定檔，將線上資源定義為公司資源和受信任的資源。 您必須先定義裝置的網路界限  之後，裝置才可以使用 Windows Defender 應用程式防護和 Windows 資訊保護等功能。 每部裝置都只能定義一個網路界限。

您可以定義要信任的企業雲端資源、IP 位址範圍和內部 Proxy 伺服器。 定義好之後，Windows Defender 應用程式防護和 Windows 資訊保護等其他功能才可以使用網路界限。

### <a name="two-additional-settings-for-windows-defender-antivirus---1338409---"></a>Windows Defender 防毒軟體的兩個其他設定<!-- 1338409 -->  
**檔案封鎖層級**

| | |
|---|---|
| 尚未設定 | [尚未設定]  會使用預設的 Windows Defender 防毒軟體封鎖層級，並提供強式偵測，而不會增加偵測合法檔案的風險。 |
| 高 | [高]  適用於強力偵測層級。
| 高 +  | [高 +]  可提供 [高] 層級與額外的保護措施，但可能會影響用戶端效能。
| 零容錯  | [零容錯]  會封鎖所有未知的可執行檔。 |

雖然可能性很低，但設定為 [高]  有可能會導致部分合法檔案受到偵測。
建議您將檔案封鎖層級設為預設值 [尚未設定]  。

**延長掃描檔案的逾時 (依雲端)**  

| | |
|--|--|
| 秒數 (0-50) | 指定 Windows Defender 防毒軟體在封鎖檔案前應等候雲端結果的時間上限。 預設時間量為 10 秒：此處所指定的任何額外時間 (最多 50 秒) 均會加上預設的 10 秒。 在大部分情況下，掃描需要的時間遠比最大值少很多。 延長的時間可讓雲端徹底調查可疑的檔案。 建議您啟用此設定，並至少多指定 20 秒。 |

### <a name="citrix-vpn-added-for-windows-10-devices---1512457---"></a>為 Windows 10 裝置新增 Citrix VPN<!-- 1512457 -->  
您可為其所擁有的 Windows 10 裝置設定 Citrix VPN。 設定 Windows 10 和更新版本的 VPN 時，您可以在 [基本 VPN]  刀鋒視窗的 [選取連線類型]  清單中，選擇 Citrix VPN。

> [!Note]
> iOS 和 Android 中已有 Citrix 設定。

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios---1550823---"></a>iOS 上的 Wi-Fi 連線支援預先共用金鑰<!-- 1550823 -->
客戶可在 iOS 裝置上設定 Wi-Fi 設定檔，以使用預先共用金鑰 (PSK) 進行 WPA/WPA2 個人連線。 當裝置註冊到 Intune 時，會將這些設定檔推送到使用者的裝置。

將設定檔推送到裝置後，下一個步驟則取決於設定檔設定。  若設定為自動連線，就會在下次需要網路時這麼做。  若設定為手動連線，使用者就必須手動啟用連線。  

### <a name="access-to-managed-app-logs-for-ios---1469920---"></a>存取 iOS 的受控應用程式記錄檔<!-- 1469920 -->
安裝 Managed Browser 的終端使用者現在已可檢視所有 Microsoft 發行之應用程式的管理狀態，並傳送記錄檔來為受管理的 iOS 應用程式進行疑難排解。

深入了解如何在 iOS 裝置上的 Managed Browser 啟用疑難排解模式，請參閱 [How to access to managed app logs using the Managed Browser on iOS](../apps/app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios) (如何在 iOS 上使用 Managed Browser 存取受管理應用程式記錄檔)。

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290---1417174---"></a>iOS 版公司入口網站 2.9.0 版中裝置設定工作流程的改善<!-- 1417174 -->

已改善 iOS 版公司入口網站應用程式中的裝置設定工作流程。 語言對使用者來說更簡單明瞭，而且我們已盡量將可以合併的畫面合併。 透過在整個設定文字中使用您的公司名稱，讓語言更特定於您的公司。 您可以在  [[應用程式 UI 中的新增功能]](../whats-new-app-ui.md) 頁面中看到這個更新的工作流程。


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model---1544273---"></a>使用者實體包含資料倉儲資料模型中的最新使用者資料<!-- 1544273 -->
Intune 資料倉儲資料模型的第一個版本只包含最新的歷程 Intune 資料。 報表製作者無法擷取使用者的目前狀態。 在這項更新中，**使用者實體**會填入最新的使用者資料。

<!-- ########################## -->
## <a name="october-2017"></a>2017 年 10 月

### <a name="ios-and-android-line-of-business-app-version-number-is-visible---1380712---"></a>顯示 iOS 和 Android 的企業營運應用程式版本號碼<!-- 1380712 -->

Intune 的應用程式現在會顯示 iOS 和 Android 的企業營運應用程式版本號碼。 此號碼會顯示在 Azure 入口網站的應用程式清單及 [應用程式概觀] 刀鋒視窗中。 使用者可以在公司入口網站應用程式及入口網站中看到應用程式號碼。

__完整版本號碼__ 完整的版本號碼可識別特定的應用程式版本。 此號碼會顯示為_版本_(_組建_)。 例如，2.2(2.2.17560800)

完整的版本號碼有兩個部分：

- **版本**  
  版本號碼是人類可讀的應用程式版本號碼。 可供使用者識別不同的應用程式版本。

- **組建編號**  
  組建編號是內部編號，用於偵測應用程式與以程式設計方式管理應用程式。 組建編號是指參考程式碼變更的應用程式反覆項目。

深入了解版本號碼及開發企業營運應用程式，請參閱[開始使用 Microsoft Intune App SDK](../developer/app-sdk-get-started.md#line-of-business-app-version-numbers)。

### <a name="device-and-app-management-integration---677972---"></a>裝置與應用程式管理整合<!-- 677972 -->   
Intune 早已開始整合應用程式和裝置管理的 IT 系統管理員體驗；現在，Intune 的行動裝置管理 (MDM) 與行動應用程式管理 (MAM) 都可從 Azure 入口網站存取。 這些變更都是為了簡化您的裝置和應用程式管理體驗。

如需深入了解已宣布的 MDM 和 MAM 變更，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)。

### <a name="new-enrollment-alerts-for-apple-devices---1471790---"></a>Apple 裝置的新註冊警示<!-- 1471790 -->
註冊的 [概觀] 頁面會顯示對 IT 管理員極有幫助，有關 Apple 裝置管理的警示。 在下列情況中 [概觀] 頁面會顯示警示：Apple MDM Push Certificate 即將到期或已過期時、裝置註冊計劃權杖即將到期或已過期時、裝置註冊計劃中有未指派的裝置時。

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment---1080364---"></a>支援在不註冊裝置之情況下取代應用程式設定的權杖<!-- 1080364 -->

您可以在未註冊裝置的應用程式中，使用應用程式設定的動態值權杖。 如需詳細資訊，請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](../apps/app-configuration-policies-managed-app.md)。

### <a name="updates-to-the-company-portal-app-for-windows-10--1299474--"></a>Windows 10 版公司入口網站應用程式的更新<!--1299474-->
Windows 10 版「公司入口網站」應用程式中的 [設定] 頁面已更新，以使設定和預期的使用者動作在所有設定中更加一致。 它也已更新為符合其他 Windows 應用程式的配置。 您可以在 [應用程式 UI 中的新增功能](../whats-new-app-ui.md) 頁面中找到之前/之後影像。

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices--1337920--"></a>通知終端使用者可看到哪些 Windows 10 裝置資訊<!--1337920-->
我們已將 [擁有權類型]  新增至 Windows 10 版公司入口網站應用程式的 [裝置詳細資料] 畫面。 這樣可讓使用者直接從此頁面從 Intune 終端使用者文件尋找有關隱私權的詳細資訊。使用者也可以在 [關於]  畫面上找到此資訊。

### <a name="feedback-prompts-for-the-company-portal-app-for-android--1165249--"></a>Android 版公司入口網站應用程式的意見反應提示<!--1165249-->
Android 版公司入口網站應用程式現在會要求終端使用者提供意見反應。 此意見反應會直接傳給至 Microsoft，並讓使用者得以在公開的 Google Play 商店上評論應用程式。 意見反應並非必要，使用者可以輕易地將之關閉，以繼續使用應用程式。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android---1573324-1573150-1558616-1564878---"></a>協助您的使用者自助使用 Android 版公司入口網站應用程式<!-- 1573324, 1573150, 1558616, 1564878 -->

Android 版公司入口網站應用程式新增了終端使用者指示，能幫助他們了解，並盡可能自行解決新的使用案例。
- 如果使用者已達可新增裝置的數目上限，系統會引導他們前往 [Azure Active Directory 網站](https://account.activedirectory.windowsazure.com/r/#/profile)移除裝置。
- 有提供步驟協助終端使用者[修正 Samsung Knox 裝置的啟動錯誤](https://go.microsoft.com/fwlink/?linkid=859718)或[關閉省電模式](/intune-user-help/power-saving-mode-android)。 如果這些解決方案都無法解決他們的問題，我們會提供[向 Microsoft 提交記錄檔](/intune-user-help/send-logs-to-microsoft-android)的說明。

### <a name="new-resolve-action-available-for-android-devices---1583480---"></a>Android 裝置提供新的「解決」動作<!-- 1583480 -->

Android 版公司入口網站應用程式的 [更新裝置設定]  頁面上新增了「解決」動作。 選取此選項會將終端使用者直接帶到造成裝置不符合規範的設定。 Android 版公司入口網站應用程式目前在[裝置密碼](/intune-user-help/set-your-pin-or-password-android)、[USB 偵錯](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知來源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定支援此動作。

### <a name="device-setup-progress-indicator-in-android-company-portal---1565657---"></a>Android 版公司入口網站中的裝置設定進度列指示器<!-- 1565657 -->
Android 版公司入口網站應用程式會在使用者註冊其裝置時，顯示裝置設定進度列指示器。 指示器會顯示新的狀態，從開始到結束依序為「正在設定您的裝置...」、「正在註冊您的裝置...」、「即將完成註冊您的裝置...」及「即將完成設定您的裝置...」。

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios--1029830--"></a>支援 iOS 版公司入口網站的憑證式驗證<!--1029830-->
我們已新增 iOS 版公司入口網站應用程式的憑證式驗證 (CBA) 支援。 使用 CBA 的使用者可輸入其使用者名稱，然後點選 [Sign in with a certificate] (使用憑證登入) 連結。 Android 版和 Windows 版公司入口網站應用程式皆已經支援 CBA。 您可以在[登入公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)頁面上深入了解。

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment---1334712---"></a>需要或無須註冊而提供的應用程式現在可以直接安裝，而不會提示註冊。<!-- 1334712 -->

在 Android 公司入口網站應用程式上需要或無需註冊才可使用的公司應用程式，現在皆已可安裝而不會提示需要註冊。

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617----"></a>Microsoft Intune 中的 Windows AutoPilot Deployment 方案支援 <!-- 747617  -->
您可以現在使用 Microsoft Intune Windows AutoPilot 部署計劃，讓您的使用者能夠佈建其公司裝置而不需要 IT 介入。 您可以自訂全新體驗 (OOBE)，並引導使用者將他們的裝置加入 Azure AD 且在 Intune 中註冊。 搭配使用時，Microsoft Intune 和 Windows AutoPilot 不須部署、維護及管理作業系統映像。 如需詳細資料，請參閱 [Enroll Windows devices using Windows AutoPilot Deployment Program](../enrollment/enrollment-autopilot.md) (使用 Windows AutoPilot Deployment 方案註冊 Windows 裝置)。

### <a name="quickstart-for-device-enrollment----1425655---"></a>裝置註冊快速入門 <!-- 1425655 --> 
快速入門現在可在 [裝置註冊]  中取得，提供管理平台和設定註冊流程的參考表格。 每個項目的簡短描述，以及文件連結和逐步指示，提供實用的文件來簡化開始使用。

### <a name="device-categorization---1427491---"></a>裝置分類<!-- 1427491 -->
[裝置] > [概觀]  刀鋒視窗的註冊裝置平台圖，會依平台組織裝置，包括 Android、iOS、macOS、Windows 和 Windows Mobile。  執行其他作業系統的裝置會分組為「其他」。  這包括由 Blackberry、NOKIA 和其他廠商製造的裝置。  

若要了解您租用戶中的哪些裝置受到影響，請選擇 [管理] > [所有裝置]  ，然後使用 [篩選]  限制 [OS]  欄位。

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium - 新的 Mobile Threat Defense 夥伴  <!-- 954681 -->  
您可以根據由 Zimperium (與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作
風險評估的依據是收集自執行 Zimperium 裝置的遙測。 您可以根據透過 Intune 裝置合規性政策啟用的 Zimperium 風險評估，設定 EMS 條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不符合規範的裝置存取公司資源。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978575-1308849---"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978575, 1308849, -->  
我們將為 Windows Defender SmartScreen 類別中的 Windows 10 裝置限制設定檔新增設定。

如需 Windows 10 裝置限制設定檔的詳細資料，請參閱 [Windows 10 及更新版本的裝置限制設定](../configuration/device-restrictions-windows-10.md)。

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>適用於 Windows 和 Windows Mobile 裝置的遠端支援  <!-- 1070473 -->  
Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (需另行購買)，讓您為執行 Windows 和 Windows Mobile 裝置的使用者提供遠端協助。

### <a name="scan-devices-with-windows-defender---1280988--1280990-----"></a>使用 Windows Defender 掃描裝置<!-- 1280988  1280990   -->
您現在可以在受管理的 Windows 10 裝置上，使用 Windows Defender 防毒軟體來執行**快速掃描**、**完整掃描**，和**更新簽章**。 從裝置的概觀刀鋒視窗，選擇要在裝置上執行的動作。 系統會提示您確認動作，然後命令才會傳送到裝置。 

**快速掃描**：快速掃描會掃描惡意程式碼註冊要啟動的位置，例如登錄機碼和已知的 Windows 啟動資料夾。 快速掃描平均會花費五分鐘。 快速掃描與 [隨時開啟即時保護]  設定 (可在檔案開啟、關閉，以及使用者每次瀏覽資料夾時掃描檔案) 結合時，可提供保護以防禦潛藏於系統或核心的惡意程式碼。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**完整掃描**：完整掃描對於已遭遇惡意程式碼威脅的裝置非常實用，可找出是否有任何需要進一步完整清理的尚未作用元件，且適合執行隨選掃描。 完整掃描可能需要一個小時來進行。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**更新簽章**：更新簽章命令會更新 Windows Defender 防毒軟體的惡意程式碼定義和簽章。 這有助於確保 Windows Defender 防毒軟體能有效偵測惡意程式碼。 這項功能僅適用於 Windows 10 裝置，且需要裝置的網際網路連線。 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal----1400455---"></a>[啟用/停用] 按鈕已從 Intune Azure 入口網站的 [Intune 憑證授權單位] 頁面移除 <!-- 1400455 -->
 我們正在消除設定 Intune 上憑證連接器的多餘步驟。 目前，您會下載憑證連接器，然後在 Intune 主控台中啟用它。 不過，如果您在 Intune 主控台中停用連接器，連接器會繼續發出憑證。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
從 10 月開始，[啟用/停用] 按鈕不會再出現在 Azure 入口網站的 [憑證授權單位] 頁面上。 連接器功能將保持不變。 憑證仍會部署到在 Intune 中註冊的裝置。 您可以繼續下載並安裝憑證連接器。 若要停止發出憑證，您現在要解除安裝憑證連接器而非將它停用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
如果您目前已停用憑證連接器，您應該將它解除安裝。

### <a name="new-settings-for-windows-10-team-device-restriction-profile------1308838---"></a>適用於 Windows 10 團隊版裝置限制設定檔的新設定  <!--- 1308838 -->
在此版本中，我們新增了許多設定到 Windows 10 團隊版裝置限制設定檔，以協助您控制 Surface Hub 裝置。

如需此設定檔的詳細資訊，請參閱 [Windows 10 團隊版裝置限制設定](../configuration/device-restrictions-windows-10-teams.md)。

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>防止 Android 裝置使用者變更其裝置的日期和時間 <!-- 1333292 -->
您可以使用 [Android 自訂裝置原則](../configuration/custom-settings-android.md)來防止 Android 裝置使用者變更裝置的日期和時間。

若要這樣做，請設定 Android 自訂原則，將 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 設定為 **TRUE**，然後指派給所需的群組。

### <a name="bitlocker-device-configuration---1397398---"></a>BitLocker 裝置設定<!-- 1397398 -->
[Windows 加密] > [基本設定]  包含新的 [其他磁碟加密的警告]  設定，讓您停用使用者裝置上可能正在使用的其他磁碟加密[警告提示](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowwarningforotherdiskencryption)。  警告提示會要求使用者同意，然後才會在裝置上設定 BitLocker，在使用者確認之前則會封鎖 BitLocker 設定。  新的設定會停用使用者警告。


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant---800882---"></a>企業大量採購方案應用程式現在將會同步到 Intune 租用戶<!-- 800882 -->  
協力廠商開發人員可以私下將應用程式散發給 iTunes Connect 中所指定的授權企業大量採購方案 (VPP) 成員。 這些企業 VPP 成員可以登入大量採購方案 App Store，並購買其應用程式。

在此版本中，終端使用者所購買的企業 VPP 應用程式將開始與其 Intune 租用戶同步。

### <a name="select-apple-countryregion-store-to-sync-vpp-apps----1332311---"></a>選取 Apple 國家/地區市集以同步處理 VPP 應用程式 <!-- 1332311 -->  
上傳您的大量採購方案 (VPP) 權杖時，可以設定 VPP 的國家/地區市集。 Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。

> [!NOTE]  
> 目前 Intune 只會從符合 Intune 地區設定 (建立 Intune 租用戶所在位置) 的 VPP 國家/地區市集同步處理 VPP 應用程式。


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work---1098994---"></a>封鎖 Android for Work 中工作和個人設定檔間的複製和貼上<!-- 1098994 -->
在此版本中，您可以將 Android for Work 的工作設定檔設定為封鎖工作和個人應用程式間的複製和貼上。 您可以在 [工作設定檔設定]  中，於 [Android for Work]  平台的 [裝置限制]  設定檔內找到這項新設定。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores---1281692---"></a>建立僅限於特定地區 Apple App Store 的 iOS 應用程式<!-- 1281692 -->
您將能在 Apple App Store 受控應用程式的建立期間，指定國家/地區的地區設定。

> [!Note]  
> 目前，您僅能建立出現在美國國家/地區市集的 Apple App Store 受控應用程式。

### <a name="update-ios-vpp-user-and-device-licensed-apps----1305564---"></a>更新 iOS VPP 使用者和裝置授權的應用程式 <!-- 1305564 -->  
您可以透過 Intune 服務，設定 iOS VPP 權杖以更新為該權杖所購買的全部應用程式。 Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。

如需設定 VPP 權杖並啟用自動更新的步驟，請參閱 [如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式] (/intune/vpp-apps-ios)。


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model---1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型<!-- 1187917 -->
您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。

### <a name="review-policy-compliance-for-windows-10-update-rings---1067886---"></a>檢閱 Windows 10 更新通道的原則相容性<!-- 1067886 -->
您可以從 [軟體更新] > [依更新通道別部署狀態] 來檢閱 Windows 10 更新通道的原則報告。 原則報告包括已設定更新通道的部署狀態。 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions-----1352223---"></a>新報表列出包括舊版 iOS 的 iOS 裝置  <!-- 1352223 -->
[軟體更新]  工作區提供 [過期的 iOS 裝置]  報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定並有可用更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>檢視應用程式保護原則指派以進行疑難排解<!--  1475003 -->
在此即將發行的版本中，將會新增 [應用程式保護原則]  選項到疑難排解刀鋒視窗中提供的 [指派]  下拉式清單。 您現在可以選取應用程式保護原則，以查看指派給所選取使用者的應用程式保護原則。



### <a name="improvements-to-device-setup-workflow-in-company-portal--1490692--"></a>對公司入口網站中裝置安裝工作流程的改善<!--1490692-->
我們已經改善 Android 版公司入口網站應用程式中的裝置設定工作流程。 我們採用您公司專屬的語言、對使用者來說更簡單明瞭，並盡量將可以合併的畫面合併。 您可以在[應用程式 UI 中的新功能](whats-new-app-ui.md#week-of-october-2-2017)頁面上查看這些變更。

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices--1484985--"></a>已改善在 Android 裝置上要求存取連絡人的相關指引<!--1484985-->

Android 版公司入口網站應用程式通常會要求使用者接受「連絡人」的使用權限。 如果使用者拒絕此存取權，系統現在會顯示應用程式內通知，提醒他們授與此權限以進行條件式存取。 

### <a name="secure-startup-remediation-for-android--1490712--"></a>Android 的安全啟動修復<!--1490712-->

使用 Android 裝置的使用者將能夠點選公司入口網站應用程式中的非合規性原因。 在可能的情況下，這將會將他們帶到 [設定] 應用程式中的正確位置以修正該問題。 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo--1475932--"></a>在 Android Oreo 版公司入口網站應用程式上新增終端使用者的推播通知<!--1475932-->

終端使用者將會看到其他通知，這些通知會指出 Android Oreo 版公司入口網站應用程式正在執行背景工作，例如從 Intune 服務擷取原則。 這樣可讓終端使用者清楚了解公司入口網站在其裝置上執行的系統管理工作。 這是適用於 Android Oreo 版公司入口網站應用程式之整體[公司入口網站 UI 最佳化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)的一部分。 

在 Android Oreo 中啟用的新 UI 項目已進一步最佳化。  終端使用者會看到額外的通知，顯示出公司入口網站執行背景工作 (例如從 Intune 服務擷取原則) 的時間。  這可讓使用者清楚知道公司入口網站在裝置上執行管理工作的時間。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles---1485783---"></a>Android 版公司入口網站應用程式使用工作設定檔的新行為<!-- 1485783 -->

當您使用工作設定檔註冊 Android for Work 裝置時，在該裝置上執行管理工作的是工作設定檔中的公司入口網站應用程式。 

除非您使用的是個人設定檔中已啟用 MAM 的應用程式，否則 Android 版公司入口網站將不再提供任何用途。 為了改善工作設定檔體驗，Intune 將會在順利註冊工作設定檔之後，自動隱藏個人的公司入口網站應用程式。

您可以隨時在個人設定檔中啟用 Android 版公司入口網站應用程式，方法是瀏覽至 [Play 商店中的「公司入口網站」](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)，然後點選 [啟用]  。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode--1428681--"></a>Windows 8.1 版和 Windows Phone 8.1 版的公司入口網站已移至維持模式<!--1428681-->

從 2017 年 10 月開始，Windows 8.1 版和 Windows Phone 8.1 版的公司入口網站應用程式將會移至維持模式。 這表示這些平台的應用程式與現有的案例 (例如註冊和合規性) 將會繼續被支援。 這些應用程式將可透過現有的發行管道 (例如 Microsoft Store) 繼續進行下載。 

一旦進入維持模式，這些應用程式就僅會接收重大安全性更新。 未來將不會針對這些應用程式發行其他的更新或功能。 如需新功能，建議您將裝置更新為 Windows 10 或 Windows 10 行動裝置版。 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>封鎖不支援的 Samsung Knox 裝置註冊 <!-- 1490695 -->

公司入口網站應用程式只會嘗試註冊支援的 Samsung KNOX 裝置。 為了避免 Knox 啟用錯誤而導致 MDM 註冊失敗，如果裝置出現在 [Samsung 發佈的裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中，則系統只會嘗試進行裝置註冊。 有些 Samsung 裝置型號可能支援 Knox，而有些不支援。 在您購買並部署之前，請先向裝置經銷商確認 KNOX 相容性。 您可以在 [Android 和 Samsung Knox Standard 原則設定](supported-devices-browsers.md#intune-supported-web-browsers)中找到已驗證裝置的完整清單。

### <a name="end-of-support-for-android-43-and-lower---1171126-1326920---"></a>終止支援 Android 4.3 與較舊版本<!-- 1171126, 1326920 -->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices--1165314--"></a>通知終端使用者可在已註冊裝置上看到哪些裝置資訊<!--1165314-->
我們正將 [擁有權類型]  加入到所有公司入口網站應用程式的 [裝置詳細資料] 畫面。 這樣可讓使用者直接從[我的公司可以看到哪些資訊？](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)文章深入了解隱私權的詳細資訊。 在不久的將來，這項功能就會推出到所有公司入口網站應用程式。 我們已在 [9 月](#september-2017)針對 iOS 宣佈此功能。

<!-- ########################## -->
## <a name="september-2017"></a>2017 年 9 月

### <a name="intune-supports-ios-11--1428975--"></a>Intune 支援 iOS 11<!--1428975-->
Intune 支援 iOS 11。 這項資訊之前已在 [Intune 支援部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)宣布過。

### <a name="end-of-support-for-ios-80---1164477---"></a>針對 iOS 8.0 終止支援<!-- 1164477 -->
受管理的應用程式與 iOS 版公司入口網站應用程式需要 iOS 9.0 與更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10--1132468--"></a>重新整理動作已新增至 Windows 10 版公司入口網站應用程式<!--1132468-->
Windows 10 公司入口網站應用程式可讓使用者提取以重新整理，或按桌上型電腦的 F5，重新整理應用程式中的資料。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios--739894--"></a>通知終端使用者可看到哪些 iOS 裝置資訊<!--739894-->

我們在 iOS 的公司入口網站應用程式 [裝置詳細資料] 畫面新增了 [擁有權類型]  。 這樣可讓使用者直接從此頁面從 Intune 終端使用者文件尋找有關隱私權的詳細資訊。他們也可以在 [關於] 畫面上找到此資訊。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment---1169910---"></a>允許終端使用者存取 Android 版公司入口網站應用程式，而不需要註冊<!---1169910--->

使用者很快地不必註冊裝置也能存取 Android 的公司入口網站。 使用應用程式保護原則的組織使用者，在開啟公司入口網站應用程式時，將不會再收到註冊裝置的提示。 使用者也可以從公司入口網站安裝應用程式，不用註冊裝置。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android---1396349---"></a>Android 版公司入口網站應用程式中更易了解的措辭<!---1396349--->  

Android 版公司入口網站應用程式的註冊程序已經使用新的文字來簡化，讓使用者可更輕鬆地進行註冊。 如果您有自訂註冊文件，建議您予以更新，以反映新的畫面。 您可以在我們的 [Intune 終端使用者應用程式 UI 更新](whats-new-app-ui.md#week-of-september-11-2017)頁面找到範例影像。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy---677129---"></a>Windows 10 公司入口網站應用程式已新增到 Windows 資訊保護允許原則<!-- 677129 -->

Windows 10 公司入口網站應用程式已更新，現在支援 Windows 資訊保護 (WIP)。 此應用程式可以加入到 WIP 允許原則。 有了此變更，您再也不需要將應用程式加入到[豁免]  清單。


<!-- ########################## -->
## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview---1404453---"></a>裝置概觀改善<!-- 1404453 -->  
裝置概觀改善現在會顯示已註冊的裝置，但不包含 Exchange ActiveSync 所管理的裝置。 Exchange ActiveSync 裝置與已註冊裝置的管理選項不同。 若要在 Azure 入口網站中檢視 Intune 中的已註冊裝置數目以及依平台的已註冊裝置數目，請移至 [裝置]   > [概觀]  。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune 所收集裝置清查的改善
<!-- 961134, 1104426, 1281327, 1333543 -->
在此版本中，我們已對您管理的裝置所收集的清查資訊進行下列改善：
 
- 對於 Android 裝置，您現在可以將資料行新增至裝置清查，以顯示每個裝置的最新修補程式等級。 將 [Security patch level] (安全性修補程式等級)  資料行新增至裝置清單，以查看這項資訊。
- 當您篩選裝置檢視時，現在可以依其註冊日期篩選裝置。 例如，您可以只顯示在所指定日期之後註冊的裝置。
- 我們已改善 [Last Check-in Date] (最後一次簽入日期)  項目所使用的篩選。
- 在裝置清單中，您現在可以顯示公司所擁有裝置的電話號碼。
此外，您還可以使用篩選窗格，依電話號碼來搜尋裝置。

如需裝置清查的詳細資料，請參閱[如何檢視 Intune 裝置清查](../remote-actions/device-inventory.md)。

### <a name="conditional-access-support-for-macos-devices"></a>macOS 裝置的條件式存取支援 
<!-- 720172 -->
您現在可以設定條件式存取原則，要求 Mac 裝置向 Intune 註冊，並符合其裝置的合規性政策。 例如，使用者可以下載適用於 macOS 的 Intune 公司入口網站應用程式，並在 Intune 中註冊其 Mac 裝置。 Intune 會評估 Mac 裝置是否符合 PIN、加密、作業系統版本和系統完整性等需求。

- 深入了解[何謂條件式存取？](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

### <a name="company-portal-app-for-macos-is-in-public-preview---1484796---"></a>對 macOS 來說，公司入口網站應用程式目前為公開預覽<!---1484796--->
macOS 版公司入口網站應用程式現已作為 Enterprise Mobility + Security 中條件式存取公開預覽的一部分提供。 此版本支援 macOS 10.11 及更新版本。 立即於 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) 取得。 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 的新裝置限制設定    
<!--1063965, 1308850  -->
在此版本中，我們已在下列類別中新增 [Windows 10 裝置限制設定檔](/intune/device-restrictions-windows-10)的新設定：

- Windows Defender SmartScreen
- App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>BitLocker 設定的 Windows 10 端點保護裝置設定檔更新
<!--1459533 -->    
在此版本中，我們已對 BitLocker 設定在 Windows 10 端點保護裝置設定檔中的運作方式進行下列改善：
 
- 在 [BitLocker OS 磁碟機設定]  下，針對 [具有不相容 TPM 晶片的 BitLocker]  設定，當您選取 [封鎖]  時，以前這會導致實際允許 BitLocker。 我們現在已修正這個問題，以在選取 BitLocker 時進行封鎖。
- 在 [BitLocker OS 磁碟機設定]  下，針對 [以憑證為基礎的資料修復代理程式]  設定，您現在可以明確地封鎖以憑證為基礎的資料修復代理程式。 不過，預設會允許代理程式。
- 在 [BitLocker 固定式資料磁碟機設定]  下，針對 [資料修復代理程式]  設定，您現在可以明確地封鎖資料修復代理程式。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md)。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users---621669---"></a>Android 公司入口網站使用者和應用程式保護原則使用者的新登入體驗<!-- 621669 -->
使用者現在可以使用 Android 公司入口網站應用程式來瀏覽應用程式、管理裝置及檢視 IT 連絡人資訊，而無需註冊其 Android 裝置。 此外，如果使用者已使用受 Intune 應用程式防護原則保護的應用程式，並啟動 Android 公司入口網站，使用者不會再收到註冊裝置的提示。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization--1405990--"></a>Android 公司入口網站應用程式中用來切換電池最佳化的新設定<!--1405990-->
適用於 Android 的公司入口網站應用程式中的 [設定]  頁面，具有新的設定，可讓使用者輕鬆關閉公司入口網站及 Microsoft Authenticator 應用程式的電池最佳化功能。 設定中所顯示的應用程式名稱，會依管理公司帳戶的應用程式而有所不同。 建議使用者關閉電池最佳化功能，以提升同步電子郵件與資料的公司應用程式效能。 

### <a name="multi-identity-support-for-onenote-for-ios--------1234281---"></a>OneNote for iOS 的多重身分識別支援     <!-- 1234281 -->
終端使用者現在可以搭配使用不同的帳戶 (公司和個人) 與 Microsoft OneNote for iOS。 應用程式保護原則可以套用至工作筆記本中的公司資料，而不會影響其個人筆記本。 例如，原則可讓使用者在工作筆記本中尋找資訊，但會防止使用者將公司資料從工作筆記本複製並貼入個人筆記本。
 
- 深入了解支援 Intune 的[應用程式保護和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>在 Samsung Knox Standard 裝置上允許或封鎖應用程式的新設定
<!-- 1305423 822899-->  
在此版本中，我們新增新的[裝置限制設定](../configuration/device-restrictions-android.md)，可讓您指定下列應用程式清單：
 
- 允許使用者安裝的應用程式
- 封鎖使用者執行的應用程式
- 對使用者隱藏的裝置應用程式
 
您可依 URL、套件名稱，或從管理的應用程式清單中指定應用程式。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>來自 Intune 的新 Azure AD 應用程式型條件式存取原則 UI 連結
<!-- 1016201 -->
IT 管理員現在可以透過 Azure AD 工作負載中的新條件式存取原則 UI，來設定應用程式條件式存取原則。 Azure 入口網站的 [Intune 應用程式防護] 區段中，應用程式條件式存取會暫時保留不動，且會強制並存。 Intune 工作負載中另有提供方便的連結，可連至新的條件式存取原則 UI。

- 深入了解 [Azure AD 上的應用程式型條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference) \(部分機器翻譯\)。

<!-- ########################## -->
## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256--1245463----"></a>依作業系統版本限制 Android 和 iOS 裝置註冊限制 <!--- 1333256,  1245463 --->
Intune 現在支援依作業系統版本號碼限制 iOS 和 Android 註冊。 在 [裝置類型限制]  下，IT 系統管理員現在可以進行平台設定，以便將註冊限制於作業系統值上下限之間。 Android 作業系統版本必須指定為 Major.Minor.Build.Rev，其中 Minor、Build 和 Rev 為選擇性。 iOS 版本必須指定為 Major.Minor.Build，其中 Minor 和 Build 為選擇性。 深入了解[裝置註冊限制](../enrollment/enrollment-restrictions-set.md)。

>[!NOTE]
>請勿將註冊限制為透過 Apple 註冊計劃或 Apple Configurator 進行。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272--1333275-1245709----"></a>限制 Android、iOS 和 macOS 裝置以個人擁有的裝置註冊 <!--- 1333272,  1333275, 1245709 --->
Intune 可以透過將公司裝置 IMEI 編號列入允許清單，來限制個人裝置註冊。 Intune 現在已使用裝置序號，將這項功能擴充到 iOS、Android 和 macOS。 將序號上傳至 Intune，您就可以預先宣告此為公司擁有的裝置。 使用註冊限制，您可以封鎖個人擁有 (BYOD) 的裝置，僅註冊公司擁有的裝置。 深入了解[裝置註冊限制](../enrollment/enrollment-restrictions-set.md)。

若要匯入序號，請移至 [裝置註冊]   > [公司裝置識別碼]  並按一下 [新增]  ，然後上傳 .CSV 檔案 (不含標頭的兩個序號和 IMEI 編號等詳細資料欄位)。 若要限制個人擁有的裝置，請移至 [裝置註冊]   >  [註冊限制]  。 在 [裝置類型限制]  下選取 [預設]  ，然後選取 [平台設定]  。 您可以 [允許]  或 [封鎖]  個人擁有的 iOS、Android 和 macOS 裝置。


### <a name="new-device-action-to-force-devices-to-sync-with-intune---711369---"></a>新的裝置動作會強制裝置與 Intune 同步處理<!-- 711369 -->
在此版本中，我們已新增裝置動作，強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。
如需詳細資料，請參閱[同步處理裝置](../remote-actions/device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update---777100---"></a>強制受監督 iOS 裝置自動安裝最新可用的軟體更新<!-- 777100 -->
新的原則可從 [軟體更新] 工作區取得，您可在此強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 如需詳細資料，請參閱[設定 iOS 更新原則](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile - 新的 Mobile Threat Defense 夥伴 <!-- 954651, 1172027 -->
您可以根據由 Checkpoint SandBlast Mobile (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作？
風險乃依據收集自執行 Checkpoint SandBlast Mobile 裝置的遙測來進行評估。 您可以根據透過 Intune 裝置合規性政策所啟用的 Checkpoint SandBlast Mobile 風險評估，來設定 EMS 條件式存取原則。 您可以根據偵測到的威脅，允許或封鎖不相容的裝置存取公司資源。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business---748101---"></a>將應用程式部署為商務用 Microsoft Store 中的可用項目<!-- 748101 -->
系統管理員現在可以使用此版本將商務用 Microsoft 網上商店指派為可用。 設定為可用時，終端使用者就可以從公司入口網站應用程式或網站安裝應用程式，而不會被重新導向至 Microsoft 網上商店。

### <a name="ui-updates-to-the-company-portal-website--1313244-part-1--"></a>公司入口網站的 UI 更新<!--1313244 part 1-->
我們對[公司入口網站](https://portal.manage.microsoft.com)的 UI 進行了數項更新，以增強終端使用者體驗。

- __應用程式磚的增強功能__：應用程式圖示現在會根據圖示的主要色彩 (如果可偵測)來顯示自動產生的背景。 適用時，此背景會取代先前在應用程式磚上顯示的灰色框線。

    公司入口網站會在未來版本中盡可能顯示大圖示。 建議 IT 系統管理員使用大小下限為 120 x120 像素的高解析度圖示來發佈應用程式。 

- __導覽變更__：導覽列項目移至左上方的漢堡功能表。 移除 [類別] 頁面。 使用者現在可以在瀏覽時依類別篩選內容。

- __精選 App 的更新__：我們已將專用頁面新增至網站 (使用者可在其中瀏覽您選為精選的應用程式)，並對首頁上的 [精選] 區段進行一些 UI 調校。

### <a name="ibooks-support-for-the-company-portal-website--1231841--"></a>公司入口網站的 iBooks 支援<!--1231841-->
我們已將專用頁面新增至公司入口網站，讓使用者可以瀏覽並下載 iBooks。 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>其他技術支援中心疑難排解詳細資料<!---  Applies to 1263399, 1326964, 1341642 --->
Intune 已更新疑難排解顯示，並新增至針對系統管理員和技術服務人員所提供的資訊。 您現在可以看到 [指派]  表格，其中根據群組成員資格來摘要說明所有使用者指派。 此清單包括：
- 行動應用程式
- 相容性原則
- 組態設定檔

此外，[裝置]  資料表現在會包含 [Azure AD 聯結類型]  和 [符合 Azure AD 規範]  資料行。 如需詳細資訊，請參閱[協助使用者針對問題進行疑難排解](../help-desk-operators.md)。



### <a name="intune-data-warehouse-public-preview"></a>Intune 資料倉儲 (公開預覽)
Intune 資料倉儲會每日對資料進行抽樣，以提供您租用戶的歷程檢視。 您可以藉由使用 Power BI 檔案 (PBIX)、與許多分析工具相容的 OData 連結，或與 REST API 互動，來存取資料。 如需詳細資訊，請參閱[使用 Intune 資料倉儲](../developer/reports-nav-create-intune-reports.md)。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10---676547---"></a>Windows 10 版公司入口網站應用程式提供日間和夜間模式<!---676547--->
使用者可以自訂 Windows 10 公司入口網站應用程式的色彩模式。 使用者可在公司入口網站應用程式的 [設定] 區段中進行變更。 使用者重新啟動應用程式後，即會看到變更。 至於 Windows 10 版本 1607 及更新版本，應用程式模式會預設為系統設定。 至於 Windows 10 版本 1511 及更新版本，應用程式模式會預設為日間模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10---807046--"></a>讓終端使用者在 Windows 10 版公司入口網站應用程式中標記其裝置群組<!---807046-->
終端使用者現在可以直接在 Windows 10 公司入口網站應用程式中標記群組，選取其裝置所屬群組。

<!-- ########################## -->
## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins-----1099990---"></a>適用於 Intune 系統管理員全新且以角色為基礎的系統管理存取權  <!-- 1099990 -->  
新增條件式存取管理員角色，來檢視、建立、修改及刪除 Azure AD 條件式存取原則。 先前只有全域管理員和安全性管理員具有此權限。 您可以為 Intune 管理員授與此角色權限，讓他們具有條件式存取原則的存取權。


### <a name="tag-corporate-owned-devices-with-serial-number---1215070---"></a>使用序號標記屬公司擁有的裝置<!-- 1215070 -->  
Intune 現在支援上傳 iOS、macOS 和 Android 序號以作為公司裝置識別碼。 您無法使用序號來封鎖個人裝置進行註冊，因為在註冊期間不會驗證序號。 依序號封鎖個人裝置，將在不久的未來推出。


### <a name="new-remote-actions-for-ios-devices---854689---"></a>適用於 iOS 裝置的新遠端動作<!-- 854689 -->
在此版本中，我們為用於管理 Apple Classroom 的共用 iPad 裝置新增了兩個遠端裝置動作：

- [登出目前的使用者](../remote-actions/device-logout-user.md) - 登出您所選擇 iOS 裝置的目前使用者。
- [移除使用者](../remote-actions/device-remove-user.md) - 會從 iOS 裝置的本機快取中刪除您選擇的使用者。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app---1044681---"></a>使用 iOS Classroom 應用程式支援共用的 iPad<!-- 1044681 -->
在此版本中，我們擴充了對管理 iOS Classroom 應用程式的支援，以包含使用受管理 Apple ID 登入共用 iPad 的學生。


### <a name="changes-to-intune-built-in-apps---1332306---"></a>Intune 內建應用程式的變更<!-- 1332306 -->
原本，Intune 包含許多您可以快速指派的內建應用程式。 應客戶的意見反應，我們已移除此清單，而您不會再看到內建應用程式。
不過，您已指派的任何內建應用程式仍會顯示在應用程式清單中。 若有需要，您可以繼續指派這些應用程式。
在之後的版本中，我們計劃新增一個方法，讓從 Azure 入口網站選取及指派內建應用程式的流程變得更輕鬆。

### <a name="easier-installation-of-office-365-apps----1121362----"></a>安裝 Office 365 應用程式更輕鬆<!--- 1121362 --->
新的 **Office 365 ProPlus** 應用程式類型可讓您輕鬆地將 Office 365 ProPlus 2016 應用程式指派給您管理的執行最新版 Windows 10 的裝置。 此外，如果您有 Microsoft Project 或 Microsoft Visio 的授權，也可以安裝它們。 您想要的應用程式會配套在一起，並以單一應用程式的形式出現在 Intune 主控台的應用程式清單中。
如需詳細資訊，請參閱[如何新增適用於 Windows 10 的 Office 365 應用程式](../apps/apps-add-office365.md)。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business----777044----"></a>支援來自商務用 Microsoft Store 的離線應用程式<!--- 777044 --->
您購買自商務用 Microsoft 網上商店的離線應用程式現在將能同步處理至 Azure 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps-----1257019---"></a>Microsoft 小組現在是以應用程式為基礎之已核准應用程式 CA 清單的一部分  <!-- 1257019 -->
適用於 iOS 和 Android 的 Microsoft Teams 應用程式，現在是針對適用於 Exchange 和 SharePoint Online 之應用程式型條件式存取原則核准的應用程式一部分。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，使用應用程式型條件式存取，將應用程式設定為所有租用戶。

### <a name="managed-browser-and-app-proxy-integration---1287310---"></a>受控瀏覽器和應用程式 Proxy 整合<!-- 1287310 -->
Intune Managed Browser 現在可以整合 Azure AD Application Proxy 服務，讓使用者即使在遠端工作時也能存取內部網路網站。 瀏覽器的使用者只需和平常一樣輸入網站 URL，Managed Browser 便會透過應用程式 Proxy Web 閘道來路由傳送要求。 如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](../apps/app-configuration-managed-browser.md)。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser---682951---"></a>適用於 Intune Managed Browser 的新應用程式組態設定<!-- 682951 -->
在此版本中，我們已新增 iOS 和 Android 的 Intune Managed Browser 應用程式的進一步設定。 您現在能使用應用程式設定原則，針對瀏覽器設定預設的首頁和書籤。
如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](../apps/app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10----951707---"></a>Windows 10 的 BitLocker 設定 <!-- 951707 -->
您現在可以使用新的 Intune 裝置設定檔，設定 Windows 10 裝置的 BitLocker 設定。 例如，您可以要求裝置加密，也可以設定在開啟 BitLocker 時套用的進一步設定。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](../protect/endpoint-protection-windows-10.md)。

### <a name="new-settings-for-windows-10-device-restriction-profile----978527--978550-978569-1050031-1058611-----"></a>適用於 Windows 10 裝置限制設定檔的新設定<!--- 978527,  978550, 978569, 1050031, 1058611,  --->
在此版本中，我們已新增 Windows 10 裝置限制設定檔的新設定，在下列類別中：

- Windows Defender
- 行動數據與連線
- 鎖定畫面體驗
- 隱私權
- 搜尋
- Windows 焦點
- Microsoft Edge 瀏覽器

如需 Windows 10 設定的詳細資訊，請參閱 [Windows 10 和更新版本的裝置限制設定](../configuration/device-restrictions-windows-10.md)。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies--1305217--"></a>Android 版公司入口網站應用程式的應用程式保護原則現在有終端使用者新體驗<!--1305217-->
根據客戶的意見反應，我們已修改 Android 公司入口網站應用程式，以顯示 [存取公司內容]  按鈕。 目的是為了防止終端使用者在他們只需要存取支援應用程式保護原則 (Intune 行動應用程式管理的一項功能) 的應用程式時，不必要地進行註冊程序。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

### <a name="new-menu-action-to-easily-remove-company-portal--1164569--"></a>新的功能表動作可輕鬆移除公司入口網站<!--1164569-->
根據使用者意見反應，Android 版公司入口網站應用程式已新增功能表動作，可從裝置起始公司入口網站的移除。 此動作會將裝置從 Intune 管理移除，來讓使用者可以將應用程式從裝置移除。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面和 [Android 使用者文件](/intune-user-help/unenroll-your-device-from-intune-android)中看到這些變更。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update--676505--"></a>透過 Windows 10 Creators Update 改善應用程式同步處理<!--676505-->
Windows 10 版公司入口網站應用程式現在會針對具有 Windows 10 Creators Update (版本 1703) 之裝置的應用程式安裝要求，自動初始化同步處理。 這會減少應用程式安裝在「待同步」狀態期間出現拖延的問題。 此外，使用者將能從應用程式內手動起始同步處理。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。

### <a name="new-guided-experience-for-windows-10-company-portal---1058938---"></a>Windows 10 公司入口網站新型引導式體驗<!---1058938--->
Windows 10 的公司入口網站應用程式將包含之前尚未確定或註冊之裝置的引導式 Intune 逐步解說體驗。 此全新體驗提供逐步指示，引導使用者向 Azure Active Directory 註冊 (條件式存取功能所需)，以及 MDM 註冊 (裝置管理功能所需)。 此引導式體驗將可從公司入口網站首頁上存取。 未完成註冊的使用者可以繼續使用應用程式，但可使用的功能將會受到限制。

此更新只會顯示在執行 Windows 10 年度更新版 (組建 1607) 或更高版本的裝置上。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 和條件式存取管理主控台正式推出
我們宣佈推出 Azure 入口網站管理主控台中的新 Intune 和條件式存取管理主控台。 您現在可以透過 Azure 入口網站中的 Intune，將所有 Intune MAM 與 MDM 功能合併管理，並妥善利用 Azure AD 群組和目標設定功能。 Azure 中的條件式存取跨 Azure AD 和 Intune，將豐富的功能整合在一個統一主控台。 從系統管理經驗的觀點，移至 Azure 平台可讓您使用新式瀏覽器。

您現在可以在 Azure 入口網站 (portal.azure.com) 中看到沒有「預覽」  標籤的 Intune。

除非您在訊息中心收到的一系列訊息中，有要求您採取動作來移轉群組的訊息，否則現有的客戶目前不需採取任何動作。 您可能也會收到訊息中心通知，說明因為我們這一端有錯誤而使移轉需要較長的時間。 我們會努力繼續移轉任何受影響的客戶。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式中應用程式磚的增強功能
我們已更新首頁上應用程式磚的設計，以反映您針對公司入口網站所設定的商標色彩。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式現在有帳戶選擇器可供使用
如果 iOS 裝置的使用者使用其工作或學校帳戶登入其他 Microsoft 應用程式，當他們登入公司入口網站時，可能會看到新的帳戶選擇器。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

<!-- ########################## -->
## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices--1103950--"></a>在不取消註冊受控裝置的情況下變更 MDM 授權單位<!--1103950-->
您現在可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 在 Configuration Manager 主控台中，您可以將 [MDM 授權單位] 從 [設定為 Configuration Manager (混合式)] 變更為 [Microsoft Intune (獨立)]，反之亦然。


### <a name="improved-notification-for-samsung-knox-startup-pins--1087143--"></a>已改善 Samsung Knox 啟動 PIN 的通知<!--1087143-->
當使用者需要在 Samsung Knox 裝置上設定啟動 PIN 以符合加密規範時，點選對使用者顯示的通知會將他們引導至 [設定] 應用程式中的確切位置。  先前的通知會將使用者引導至密碼變更畫面。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="apple-school-manager-asm-support-with-shared-ipad---748864-770395--"></a>對於共用 iPad 的 Apple School Manager (ASM) 支援<!-- 748864, 770395-->

Intune 現在支援以 Apple School Manager (ASM) 取代 Apple 裝置註冊計劃，來為 iOS 裝置提供全新註冊功能。 下列兩種情況皆需要 ASM 上線：在「共用的 iPad」上使用 Classroom 應用程式，以及透過 Microsoft 學校資料同步處理 (SDS) 將資料從 ASM 同步到 Azure Active Directory。 如需詳細資訊，請參閱[使用 Apple School Manager 啟用 iOS 裝置註冊](../enrollment/apple-school-manager-set-up-ios.md)。

> [!NOTE]
> 若要設定共用的 iPad 搭配 Classroom 應用程式使用，需要在 Azure 中設定 iOS Education，而此功能目前尚未提供。  此功能將於不久後加入。

### <a name="device-management"></a>裝置管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer---675418---"></a>使用 TeamViewer 對 Android 裝置提供遠端協助<!-- 675418 -->

Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (另行購買)，讓您為執行 Android 裝置的使用者提供遠端協助。 如需詳細資訊，請參閱[對 Intune 管理的 Android 裝置提供遠端協助](../remote-actions/teamviewer-support.md)。

### <a name="app-management"></a>應用程式管理

#### <a name="new-app-protection-policies-conditions-for-mam---679864---"></a>適用於 MAM 的新應用程式保護原則條件<!-- 679864 -->

您現在可以在無需註冊使用者的情況下，設定能強制執行下列原則的 MAM 需求：

- 對低應用程式版本
- 最低作業系統版本
- 目標應用程式的最低 Intune APP SDK 版本 (僅限 iOS)

這項功能適用於 Android 和 iOS。 Intune 支援作業系統平台版本、應用程式版本，以及 Intune APP SDK 的最低版本強制。 在 iOS 上，已整合 SDK 的應用程式也可以設定 SDK 層級的最低版本強制。 如果沒有符合應用程式保護原則於上述三個不同層級的最低需求，使用者將無法存取目標應用程式。 此時，使用者可以選擇移除其帳戶 (適用於多重身分識別應用程式)、關閉該應用程式，或更新作業系統或應用程式版本。

您也可設定其他設定，以提供能建議使用者進行作業系統或應用程式升級的非封鎖式通知。 使用者可以關閉此通知，並繼續正常地使用應用程式。

如需詳細資訊，請參閱 [iOS 應用程式保護原則設定](../apps/app-protection-policy-settings-ios.md)和 [Android 應用程式保護原則設定](../apps/app-protection-policy-settings-android.md)。

#### <a name="configure-app-configurations-for-android-for-work---621621---"></a>設定 Android for Work 的應用程式設定<!-- 621621 -->
市集中有一些 Android 應用程式支援受管理設定選項，可以讓 IT 系統管理員控制應用程式在工作設定檔中執行的方式。 您現在可以使用 Intune 來檢視應用程式支援的設定，並使用設定設計工具或 JSON 編輯器從 Azure 入口網站進行設定。 如需詳細資訊，請參閱[使用 Android for Work 的應用程式設定](../apps/app-configuration-policies-use-android.md)。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment---677969---"></a>不需註冊的新 MAM 應用程式設定功能<!-- 677969 -->
您現在可以在沒有註冊通道的情況下，透過 MAM 建立應用程式設定原則。 此功能相當於行動裝置管理 (MDM) 應用程式設定中的應用程式設定原則。 如需使用 MAM 而不註冊的應用程式設定範例，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](../apps/app-configuration-managed-browser.md)。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser---682960---"></a>為 Managed Browser 設定允許和封鎖的 URL 清單<!-- 682960 -->
您現在可以在 Azure 入口網站中使用應用程式組態設定，為 Intune Managed Browser 設定允許和封鎖的網域及 URL 清單。 不論 Intune Managed Browser 是用於受管理或未受管理的裝置上，都適用這些設定。 如需詳細資訊，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](../apps/app-configuration-managed-browser.md)。

#### <a name="app-protection-policy-helpdesk-view---1069473---"></a>應用程式保護原則技術支援中心檢視<!-- 1069473 -->
IT 技術支援使用者現在可以在 [疑難排解] 刀鋒視窗中查看使用者授權狀態，和指派給使用者的應用程式保護原則應用程式的狀態。 如需詳細資訊，請參閱[疑難排解](./help-desk-operators.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="control-website-visits-on-ios-devices---723832---"></a>控制 iOS 裝置上的網站瀏覽<!-- 723832 -->
您現在可以使用下列兩種方法，來控制 iOS 裝置使用者可以瀏覽的網站：

- 使用 Apple 內建網路內容篩選器新增允許和封鎖的 URL。

- 僅允許 Safari 瀏覽器存取指定的網站。 針對您指定的每個網站，會在 Safari 中建立書籤。

如需詳細資訊，請參閱[適用於 iOS 裝置的網路內容篩選器設定](../configuration/ios-device-features-settings.md#web-content-filter)。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps---621614---"></a>預先設定 Android for Work 應用程式的裝置權限<!-- 621614 -->
對於部署到 Android for Work 裝置工作設定檔的應用程式，您現在可以設定個別應用程式的權限狀態。  根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。  例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。 此功能可讓您代表使用者定義權限。  您可以設定權限以 a) 自動拒絕而不通知使用者，b) 自動核准而不通知使用者，或 c) 提示使用者接受或拒絕。 如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](../configuration/device-restrictions-android-for-work.md)。

#### <a name="define-app-specific-pin-for-android-for-work-devices---728976-1102534---"></a>針對 Android for Work 裝置定義應用程式特定的 PIN<!-- 728976, 1102534 -->
工作設定檔做為 Android for Work 裝置管理的 Android 7.0 和更新版本裝置，可讓管理員定義僅適用於工作設定檔中的應用程式的密碼原則。  這些選項包括：

- 僅定義全裝置密碼原則：這是使用者必須用來解鎖整個裝置的密碼。
- 僅定義工作設定檔密碼原則：每當開啟工作設定檔中的應用程式時，系統就會提示使用者輸入密碼。
- 定義裝置和工作設定檔原則：IT 管理員可定義具有不同強度的裝置密碼原則和工作設定檔密碼原則 (例如，使用 4 位數 PIN 來解鎖裝置，但必須使用 6 位數 PIN 來開啟任何工作應用程式)。

如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](../configuration/device-restrictions-android-for-work.md)。

> [!NOTE]
> 此功能僅適用於 Android 7.0 及更新版本。  根據預設，使用者可使用這兩個個別定義的 PIN，或選擇結合這兩個定義的 PIN，以組成包含這兩者的最強式密碼。

#### <a name="new-settings-for-windows-10-devices---978585---"></a>Windows 10 裝置的新設定<!-- 978585 -->
我們已新增可控制數種功能 (例如無線顯示器、裝置探索、工作切換和 SIM 卡錯誤訊息) 的 [Windows 裝置限制設定](../configuration/device-restrictions-windows-10.md)。

#### <a name="updates-to-certificate-configuration---918991-and-823198---"></a>憑證設定的更新<!-- 918991 and 823198 -->
建立 SCEP 憑證設定檔時，針對 [主體名稱格式]，iOS、Android 和 Windows 裝置可使用 [自訂] 選項。 在此更新之前，[自訂] 欄位僅適用於 iOS 裝置。 如需詳細資訊，請參閱[建立 SCEP 憑證設定檔](../protect/certificates-profile-scep.md)。

建立 PKCS 憑證設定檔時，針對 [主體別名]  ，可使用 [自訂 Azure AD 屬性]  。 當您選取 [自訂 Azure AD 屬性]  時，可使用 [部門]  選項。 如需詳細資訊，請參閱[建立 PKCS 憑證設定檔](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode---662059---"></a>設定 Android 裝置處於 Kiosk 模式時可執行的多個應用程式<!-- 662059 -->
Android 裝置處於 kiosk 模式時，之前只能設定一個允許執行的應用程式。 您現在可以使用應用程式識別碼、存放區 URL或藉由選取您已管理的 Android 應用程式來設定多個應用程式。 如需詳細資訊，請參閱 [Kiosk 模式設定](../configuration/device-restrictions-android.md#kiosk)。

<!-- ########################## -->
## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>支援管理 Apple「課堂」應用程式
您現在可在 iPad 裝置上管理 iOS「課堂」應用程式。 使用正確的課堂和學生資料，在老師的 iPad 上設定「課堂」應用程式，然後設定學生的 iPad 向課堂註冊，這樣您就能使用應用程式控制它們。
如需詳細資訊，[設定 iOS 的教育設定](education-settings-configure-ios.md)。

### <a name="support-for-managed-configuration-options-for-android-apps---621621---"></a>支援 Android 應用程式的受控設定選項<!-- 621621 -->
Intune 現在可以設定 Play 商店中支援受控設定選項的 Android 應用程式。  這項功能可讓 IT 人員檢視應用程式所支援的設定值清單，並提供頂級的引導式 UI，讓 IT 人員可以設定這些值。

### <a name="new-android-policy-for-complex-pins---722069---"></a>新增複雜 PIN 的 Android 原則<!-- 722069 -->
您現在可以在 Android 裝置設定檔中，針對執行 Android 5.0 和更新版本的裝置，將必要的[密碼](../configuration/device-restrictions-android.md#password)類型設定為複雜數字。  使用此設定可防止裝置使用者建立包含重複或連續數字的 PIN 碼，例如 1111 或 1234。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work 裝置的其他支援
- **管理密碼和工作設定檔設定**<!-- 612808 -->

  這項新的 Android for Work 裝置限制原則現在可讓您在所管理的 Android for Work 裝置上管理密碼和工作設定檔設定。

- **允許工作與個人設定檔之間的資料共用**<!-- 1045102 -->

Android for Work 裝置限制設定檔現在有新的選項，可協助您設定工作和個人設定檔之間的資料共用。

- **限制工作和個人設定檔間的複製和貼上**<!-- 1046094 -->

  Android for Work 裝置的新自訂裝置設定檔現在可讓您限制是否允許工作和個人應用程式間的複製和貼上動作。

如需詳細資訊，請參閱 [Android for Work 的裝置限制](../configuration/device-restrictions-android-for-work.md)。

### <a name="assign-lob-apps-to-ios-and-android-devices---1057568---"></a>將 LOB 應用程式指派給 iOS 和 Android 裝置<!-- 1057568 -->
您現在可以將 [iOS](../apps/lob-apps-ios.md) 版企業營運 (LOB) 應用程式 (.ipa 檔案) 和 [Android](../apps/lob-apps-android.md) 版企業營運應用程式 (.apk 檔案) 指派給使用者或裝置。


### <a name="new-device-policies-for-ios---723774-723815-723826-723830---"></a>iOS 的新裝置原則<!-- 723774, 723815, 723826, 723830 -->
- **主畫面上的應用程式**：控制使用者會在[其 iOS 裝置的主畫面](../configuration/ios-device-features-settings.md#home-screen-layout)上看到哪些應用程式。 這項原則會變更主畫面的配置，但不會部署任何應用程式。

- **AirPrint 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPrint 裝置](../configuration/ios-device-features-settings.md#airprint) (網路印表機)。

- **AirPlay 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPlay 裝置](../configuration/ios-device-features-settings.md) (例如 Apple TV)。

- **自訂鎖定畫面訊息**：設定使用者將會在其 iOS 裝置的鎖定畫面上看到的自訂訊息，這會取代預設鎖定畫面訊息。 如需詳細資訊，請參閱[啟動 iOS 裝置上的遺失模式](../remote-actions/device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps---723767---"></a>限制 iOS 應用程式的推播通知<!-- 723767 -->
在 Intune 裝置限制設定檔中，您現在可以設定 iOS 裝置的下列[通知設定](../configuration/ios-device-features-settings.md#app-notifications)：

- 完全開啟或關閉指定應用程式的通知。
- 在通知中心內開啟或關閉指定應用程式的通知。
- 指定警示類型，可以是 [無]  、[橫幅]  或 [Modal Alert] (強制回應警示)  。
- 指定此應用程式是否允許徽章。
- 指定是否允許通知音效。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously---737837---"></a>設定 iOS 應用程式在單一應用程式模式中自發執行<!-- 737837 -->
您現在可以使用 Intune 裝置設定檔，設定 iOS 裝置在[自發性單一應用程式模式](../configuration/device-restrictions-ios.md#autonomous-single-app-mode)中執行指定的應用程式。 設定此模式並執行應用程式時，裝置會被鎖定，因此只能執行該應用程式。 一個例子是當您設定應用程式讓使用者在裝置上進行測試時。 當應用程式的動作完成時，或當您移除此原則時，裝置就會回到其正常狀態。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices---723765---"></a>為 iOS 裝置上的電子郵件和網頁瀏覽設定受信任網域<!-- 723765 -->
您現在可以從 iOS 裝置限制設定檔設定下列[網域設定](../configuration/device-restrictions-ios.md#domains)：

- **未標示的電子郵件網域** - 使用者傳送或接收的電子郵件，若不符合您於此處所指定的網域，會標示為不受信任。

- **受管理的 Web 網域** - 從您於此處指定的 URL 下載之文件，會視為受管理的文件 (僅限 Safari)。  

- **Safari 密碼自動填入網域** - 使用者在 Safari 中可以儲存的密碼，只有來自與此處指定的模式相符之 URL 的密碼。 若要使用此設定，裝置必須在受監督的模式下，且未設定供多重使用者之用。 (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal---748782---"></a>iOS 公司入口網站中可以使用 VPP 應用程式<!-- 748782 -->
您現在可以將 iOS 大量採購 (VPP) 應用程式當做「可用」  的安裝指派給使用者。 終端使用者必須有 Apple Store 帳戶，才能安裝應用程式。

### <a name="synchronize-ebooks-from-apple-vpp-store---800878---"></a>從 Apple VPP Store 同步處理電子書<!-- 800878 -->
您現在可以將從 Apple 大量採購程式市集購買的[書籍與 Intune 同步處理](../apps/vpp-apps-ios.md)，然後將這些書籍指派給使用者。

### <a name="multi-user-management-for-samsung-knox-standard-devices---971988---"></a>Samsung Knox Standard 裝置的多使用者管理<!-- 971988 -->
Intune 的[多使用者管理](../enrollment/android-enroll.md)現在支援執行 Samsung Knox Standard 的裝置。 這表示終端使用者可以使用其 Azure Active Directory 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。  當使用者登入時，他們可以存取應用程式，並將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

### <a name="additional-windows-device-restriction-settings---818566---"></a>其他 Windows 裝置限制設定<!-- 818566 -->
我們新增了其他 [Windows 裝置限制設定](../configuration/device-restrictions-windows-10.md)的支援，例如額外的 Microsoft Edge 瀏覽器支援、裝置鎖定畫面自訂、[開始] 功能表自訂、Windows 焦點搜尋集桌布，以及 Proxy 設定。

### <a name="multi-user-support-for-windows-10-creators-update---822547---"></a>Windows 10 Creators Update 的多使用者支援<!-- 822547 -->
我們針對執行 Windows 10 Creators Update 並已加入 Azure Active Directory 網域的裝置，新增了[多使用者管理](../enrollment/windows-enroll.md)的支援。 這表示當不同的標準使用者使用其 Azure AD 認證登入裝置時，將會收到指派給其使用者名稱的任何應用程式和原則。 針對安裝應用程式等自助式案例，使用者目前無法使用公司入口網站來進行。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 電腦的重新開始<!-- 1004830 -->
適用於 Windows 10 電腦的新[「全新開始」裝置動作](../remote-actions/device-fresh-start.md)現在已經可以使用。  當您發出此動作時，將會移除任何安裝在電腦上的應用程式，而且電腦會自動更新為最新版的 Windows。 這可用來協助移除通常會隨新電腦提供之預先安裝的 OEM 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。

### <a name="additional-windows-10-upgrade-paths---903672---"></a>其他 Windows 10 升級路徑<!-- 903672 -->
您現在可以建立[版本升級原則，來將裝置升級為](../configuration/edition-upgrade-configure-windows-10.md)下列其他的 Windows 10 版本：

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 專業教育版
- Windows 10 專業教育版 N

### <a name="bulk-enroll-windows-10-devices---747607---"></a>大量註冊 Windows 10 裝置<!-- 747607 -->
您現在可以使用 Windows 設定設計工具 (WCD) 將執行 Windows 10 Creators Update 的大量裝置加入到 Azure Active Directory 和 Intune。 若要為您的 Azure AD 租用戶啟用[大量 MDM 註冊](../enrollment/windows-bulk-enroll.md)，請使用 Windows 設定設計工具建立會將裝置加入到 Azure AD 租用戶的佈建套件，然後將套件套用至您要大量註冊及管理的公司擁有裝置。 將套件套用至裝置後，裝置會加入 Azure AD、在 Intune 中註冊，並準備好供 Azure AD 使用者登入。  Azure AD 使用者是這些裝置上的標準使用者，並且會接收指派的原則和必要應用程式。 目前不支援自助式和公司入口網站案例。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations---581122-736644---"></a>PIN 和受控儲存位置的新 MAM 設定<!-- 581122, 736644 -->
現在有兩個新的應用程式設定可協助您進行行動應用程式管理 (MAM) 案例：

- **在管理裝置 PIN 碼時停用應用程式 PIN 碼** - 偵測已註冊的裝置上是否有裝置 PIN 碼；如果有，則略過應用程式保護原則觸發的應用程式 PIN 碼。 這項設定可減少對在已註冊裝置上開啟啟用 MAM 的應用程式之使用者顯示的 PIN 提示次數。 這項功能適用於 Android 和 iOS。

- **選取要用於儲存公司資料的儲存體服務** - 可讓您指定要用於儲存公司資料的儲存位置。 使用者可以儲存至所選取的儲存位置服務，這表示將會封鎖未列出的其他所有儲存位置服務。

  支援的儲存位置服務清單：

  - OneDrive
  - 商務用 SharePoint Online
  - 本機儲存體

### <a name="help-desk-troubleshooting-portal---907448---"></a>服務台疑難排解入口網站<!-- 907448 -->
新的[疑難排解入口網站](../help-desk-operators.md)可協助服務台操作員和 Intune 系統管理員檢視使用者及其裝置，並執行工作以解決 Intune 技術問題。

<!-- ########################## -->
## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode--431695--"></a>支援 iOS 遺失模式<!--431695-->
針對 iOS 9.3 和更新的裝置，Intune 新增**遺失模式**的支援。 您現在可以鎖定裝置以防止任何使用，並在裝置的鎖定畫面上顯示訊息和連絡電話號碼。

使用者將無法解除鎖定裝置，除非系統管理員停用「遺失模式」。 啟用「遺失模式」時，您可以使用 [尋找裝置]  動作在 Intune 主控台中的地圖上顯示裝置的地理位置。

裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。

如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](../remote-actions/device-management.md)

### <a name="improvements-to-device-actions-report--677150--"></a>裝置動作報表改善<!--677150-->
我們改善了裝置動作報告以提升效能。 此外，您現在可以依狀態篩選報告。 例如，您可以篩選報告以僅顯示已完成的裝置動作。

### <a name="custom-app-categories--748805--"></a>自訂應用程式類別<!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](../apps/apps-add.md)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices--748823--"></a>指派 LOB 應用程式給使用未註冊裝置的使用者<!--748823-->
您現在可以將市集中的企業營運應用程式指派給使用者，不論其裝置是否已向 Intune 註冊。 如果未向 Intune 註冊使用者裝置，則必須前往「公司入口網站」網站安裝它，而不是公司入口網站應用程式。

### <a name="new-compliance-reports--846671--"></a>新的相容性報表<!--846671-->
您現在有可提供公司內裝置合規性狀態的合規性報告，並可以快速地針對使用者遇到的合規性相關問題進行疑難排解。 您可以檢視的資訊如下

- 整體的裝置合規性狀態
- 個別設定的合規性狀態
- 個別原則的合規性狀態

您也可以使用這些報告來向下鑽研個別裝置，以檢視影響該裝置的特定設定和原則。

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios--951869--"></a>直接存取 Apple 註冊案例<!--951869-->
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Azure 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。


<!-- ########################## -->
## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment--747600-795782--"></a>限制行動裝置註冊的能力<!--747600, 795782-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。

- 限制行動裝置註冊不會限制電腦用戶端註冊。  
- 僅限 iOS 與 Android，有一個額外選項可阻擋註冊個人擁有的裝置。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](../enrollment/device-enrollment.md)所說明。

### <a name="view-all-actions-on-managed-devices--677150--"></a>檢視受控裝置上的所有動作<!--677150-->
新的__裝置動作__報表會顯示曾執行遠端動作的人員，像是裝置恢復出廠預設值，並會另外顯示該動作的狀態。 請參閱[什麼是裝置管理？](../remote-actions/device-management.md)。

### <a name="non-managed-devices-can-access-assigned-apps--664691--"></a>非受控裝置可以存取已指派的應用程式<!--664691-->
iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="custom-app-categories--748805--"></a>自訂應用程式類別<!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](../apps/apps-add.md)。

### <a name="display-device-categories--814654--"></a>顯示裝置類別<!--814654-->
裝置清單現在會以資料行顯示裝置類別。 您也可以在裝置內容刀鋒視窗的內容區段中編輯類別。 請參閱[如何將應用程式新增至 Intune](../apps/apps-add.md)。

### <a name="configure-windows-update-for-business-settings--776716--"></a>設定商務用 Windows Update 的設定<!--776716-->

「Windows 即服務」是一種為 Windows 10 提供更新的新做法。 從 Windows 10 開始，任何新的「功能更新」和「品質更新」都會包含所有先前的更新內容。 這表示只要您安裝了最新的更新，就能確定您的 Windows 10 裝置已完全更新至最新版。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

使用商務用 Windows Update，可以簡化更新管理體驗，因此您不需要核准裝置群組的個別更新。 只要設定更新首度發行策略，您還是可以管理環境中的風險，Windows Update 會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您延後更新的安裝。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置直接存取 Windows Update 進行更新。使用 Intune 設定及管理 **Windows 10 更新響鈴**。 更新響鈴是一組包含何時及如何安裝 Windows 10 更新的設定。 如需詳細資訊，請參閱[設定商務用 Windows Update 的設定](../protect/windows-update-for-business-configure.md)。
