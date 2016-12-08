---
title: "Windows 10 原則設定 | Microsoft Intune"
description: "使用本主題中所列的原則設定，以協助您設定已註冊之 Windows 10 桌上型和 Windows 10 行動裝置版裝置的內建與自訂設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 10/03/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 00a602d9-b339-4fd8-ab70-defbf6686855
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad36bfd7b4f60626181ecaf27c51a9b108005979
ms.openlocfilehash: 8c970a4d1362def67e17da656b5e12e5bab2667b


---

# <a name="intune-policy-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 裝置的 Intune 原則設定

本主題包含的資訊可協助您了解可用來管理 Windows 10 裝置的 Intune 原則設定。 請搭配閱讀本主題以及[使用 Microsoft Intune 原則管理您裝置上的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)中的程序，替註冊的 Windows 10 桌面版及 Windows 10 行動裝置版設定內建及自訂的設定。 您無法將原則和執行 [Intune 電腦用戶端軟體](/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)的電腦搭配使用。

有兩個原則類型供您選擇：

- **自訂原則**：使用適用於 Windows 10 和 Windows 10 行動裝置版的 Microsoft Intune **自訂原則**來部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定，此設定可用來控制裝置上的功能。 Windows 10 透過[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) 讓許多設定可用。
- **一般設定原則**：當您想要從 Microsoft Intune 提供的內建清單中選取設定時，使用此原則類型。

## <a name="custom-policy-settings"></a>自訂原則設定

在自訂原則中提供下列設定。

### <a name="general"></a>一般

輸入名稱，並選擇性地輸入可協助您在 Intune 主控台中識別該原則的描述。

### <a name="oma-uri-settings"></a>OMA-URI 設定

為您想要新增的各個 OMA-URI 設定輸入下列資訊。 使用本主題的 [Windows 10 URI 設定參考](/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune#Windows-10-URI-settings)您可使用的設定︰

- **設定名稱**：輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
- **設定描述**：選擇性地輸入設定的描述。
- **資料類型**︰從下列資料類型中選擇：
    - **字串**
    - **字串 (XML)**
    - **日期和時間**
    - **整數**
    - **浮點數**
    - **布林值**
- **OMA-URI (區分大小寫)**：指定您想要為其提供設定的 OMA-URI。
- **值**：指定要與您輸入的 OMA-URI 產生關聯的值。

### <a name="example"></a>範例
在下列螢幕擷取畫面中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 這可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

> ![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)

## <a name="windows-10-uri-settings"></a>- Windows 10 URI 設定
使用此章節了解可使用 **Windows 10 自訂原則**加以設定的 OMA-URI 設定。

### <a name="policy"></a>原則

|原則名稱與 URI|詳細資料|
|---------------|------------|-----------|
|**允許自動更新**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|僅限桌面版<br>**資料類型：** 整數<br />**值︰****0** - **5** (預設︰**1**)|
|**排程安裝日期**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|僅限行動裝置版<br>**資料類型：** 整數<br />**值：**<br>**0** - 每一天 (預設值)<br>**1** - 星期日<br>**2** - 星期一<br>**3** - 星期二<br>**4** - 星期三<br>**5** - 星期四<br>**6** - 星期五<br>**7** - 星期六|
|**排程安裝時間**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** - **23** 小時 (**0** 為午夜) (預設值：**3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 使用者無法設定密碼寬限期計時器；值設定為「每次」<br>**1** - 使用者可設定密碼寬限期計時器 (預設)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許 **使用 Wi-Fi 連線**<br>**1** - 允許**使用 Wi-Fi 連線** (預設值)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|桌面版和行動裝置版<br>**資料類型：** 整數<br />**值：<br>****0** - 不允許網際網路共用 <br> **1** - 允許網際網路共用 (預設值)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 只允許使用設定 MDM 的 Wi-Fi 連線。<br>**1** - 除了 MDM 已建立的 SSID 之外，還允許新增網路 SSID (預設值)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|桌面版和行動裝置版<br>**資料類型：** 整數<br />**值：**<br>**0** - 不允許 (僅適用於企業版的設定)<br>**1** - 有限<br>**2** - 完整 (預設值)<br>**3** - 完整和診斷資訊|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許<br>**1** - 只有設定 (預設值)<br>**2** - 設定和試驗|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許反竊取模式<br>**1** - 使用者喜好設定 (預設值)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|僅限行動裝置版<br />**資料類型：** 整數<br />**值<br>** **0** - 不允許<br> **1** - 允許 (預設值)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br>**1** - 允許 (預設值)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許透過行動電話通訊的 VPN<br>**1** - VPN 可以使用包括行動電話在內的任何連線 (預設值)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** – 不允許使用者開啟藍芽。<br>**1** – 已保留。 使用者可以開啟和設定藍牙 (Windows Phone 8.1 for MDM、EAS、Windows 10 Desktop 或 Windows 10 行動裝置版不支援)。<br>**2** - 已允許。 使用者可以開啟和設定藍牙 (預設值)。|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許漫遊<br> **1** - 允許漫遊 (預設值)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** - 不允許<br> **1** - 允許 (預設值)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** - 不允許<br> **1** - 允許 (預設值)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|僅限行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** (預設值)<br> **1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0**<br> **1** (預設值)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** (預設值)<br> **1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** (預設值)<br> **1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰<br>****0** (預設值)<br> **1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0**<br> **1** (預設值)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br> **0** (預設值)<br> **1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰<br>****0** (預設值)<br> **1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許。<br>系統會關閉開放式擴充字典。<br>使用者無法：<br>-新增開放式擴充字典。<br />-新增搜尋整合設定檔。<br>-使用雲端候選字功能。<br>-將註冊的字詞傳送給使用者。<br>**1** - 允許<br>預設可加入並使用開放式擴充字典。 此外，預設會使用搜尋整合功能。<br>使用者可以：<br>-使用雲端候選字功能。|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 關閉錯誤轉換記錄功能<br>**1** - 開啟錯誤轉換記錄功能 (預設)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許 <br>**1** - 允許 (預設值)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不篩選任何字元 (預設值)<br>**1** - 篩選 Shift JIS 字元以外的所有字元|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br />**0** - 不篩選任何字元 (預設值)<br>**1** - 篩選 JIS0208 字元以外的所有字元|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不篩選任何字元 (預設值)<br>**1** - 篩選 JIS0208 字元或 EUDC 字元以外的所有字元|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|僅限桌面版<br />**資料類型：** 整數<br />**值<br>** **0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值<br>** **0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 嚴格，針對成人內容進行最高程度的篩選<br>**1** - 中等，針對成人內容進行中等程度的篩選 (將不會篩選有效的搜尋結果) (預設值)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**強制開始大小**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 允許使用者變更大小 (預設值)<br>**1** - 強制執行非全螢幕<br>**2** - 強制執行全螢幕|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不延遲升級 (留在最新分支，CB) (預設值)<br>**1** - 啟用更新且延後升級 (裝置遵循商務用最新分支 CBB 規則)<br />如需詳細資料，請參閱：<br>[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226.aspx)<br>[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|桌面版和行動裝置版<br>**描述：**最多延後四週進行軟體更新的原則<br />**資料類型：** 整數<br />**值：**<br> **0** - 立即套用更新 (預設值)<br>**1**-**4** - 延遲軟體更新的週數<br />如需詳細資料，請參閱：<br>[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226.aspx)<br>[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|桌面版和行動裝置版<br>**描述：**最多延遲八個月進行功能升級的原則<br />**資料類型：** 整數<br />**值：**<br>**0** - 立即套用更新 (預設值)<br>**1**-**8**- 延遲功能升級的月數<br />如需詳細資料，請參閱：<br>[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226.aspx)<br>[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|桌面版和行動裝置版<br>**描述：**允許裝置停止接收更新及升級，為期五週。<br />**資料類型：** 整數<br />**值：**<br>**0**- 立即套用更新 (預設值)<br>**1**- 暫停更新及升級 (五週後過期)|

### <a name="windows-defender"></a>Windows Defender

|原則名稱與 URI|詳細資料|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br> **0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** – 監視所有檔案 (預設)<br>**1** - 監視傳入檔案<br>**2** - 監視傳出檔案|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - **90** - 代表惡意程式碼的保留期限<br>**0** - 將惡意程式碼永遠保留在隔離資料夾中，且不會自動移除 (預設值)|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**1** - 快速掃描 (預設值)<br>**2** - 完整掃描|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 每天 (預設值)<br>**1** - 星期一<br>**2** - 星期二<br>**3** - 星期三<br>**4** - 星期四<br>**5** - 星期五<br>**6** - 星期六<br>**7** - 星期日<br>**8** - 未排定掃描|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 12:00 am<br>**60** - 1:00 am<br>**120** - 2:00 am (預設值)<br>**180** - 3:00 am<br>**240** - 4:00 am<br>**300** - 5:00 am<br>**360** - 6:00 am<br>**420** - 7:00 am<br>**480** - 8:00 am<br>**540** - 9:00 am<br>**600** - 10:00 am<br>**660** - 11:00 am<br>**720** - 12:00 pm<br>**780** - 1:00 pm<br>**840** - 2:00 pm<br>**900** - 3:00 pm<br>**960** - 4:00 pm<br>**1020** - 5:00 pm<br>**1080** - 6:00 pm<br>**1140** - 7:00 pm<br>**1200** - 8:00 pm<br>**1260** - 9:00 pm<br>**1320** - 10:00 pm<br>**1381** - 維護期間|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|僅限桌面版<br>**資料類型：** 整數<br />**值：**<br>**0** - 12:00 am<br>**60** - 1:00 am<br>**120** - 2:00 am (預設值)<br>**180** - 3:00 am<br>**240** - 4:00 am<br>**300** - 5:00 am<br>**360** - 6:00 am<br>**420** - 7:00 am<br>**480** - 8:00 am<br>**540** - 9:00 am<br>**600** - 10:00 am<br>**660** - 11:00 am<br>**720** - 12:00 pm<br>**780** - 1:00 pm<br>**840** - 2:00 pm<br>**900** - 3:00 pm<br>**960** - 4:00 pm<br>**1020** - 5:00 pm<br>**1080** - 6:00 pm<br>**1140** - 7:00 pm<br>**1200** - 8:00 pm<br>**1260** - 9:00 pm<br>**1320** - 10:00 pm<br>**1380** - 11:00 pm|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - **100** (預設值：**50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|僅限桌面版<br />**資料類型：** 整數<br>**值︰<br>****0** - 不允許 (預設值)<br> **1** - 允許|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|僅限桌面版<br />**資料類型：** 整數<br />**值︰<br>****0** - 不允許 (預設值)<br> **1** - 允許|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值) - 若設為允許並開啟了 RTP 也會執行|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不會在某個時間間隔檢查簽章<br>**1** - 每小時檢查簽章<br>**2** – 每兩小時檢查一次 <br>**24** - 每天檢查<br>**8** - 每八小時檢查一次 (預設值)|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 一律要求確認 (預設值)<br>**1** - 自動傳送安全的範例<br>**2** - 一律不傳送<br>**3** - 自動傳送所有的範例|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|僅限桌面版<br />**資料類型：**字串<br />**值：**<br>*&lt;以分號分隔的副檔名清單&gt;* 例如：**obj;lib**<br>**預設值 -** 不排除任何副檔名|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|僅限桌面版<br />**資料類型：**字串<br />**值：**<br />*&lt;以分號分隔的路徑清單&gt;*<br />範例：**c:\test;c:\test1.exe**<br />**預設值 -** 不排除任何路徑|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|僅限桌面版<br />**資料類型：**字串<br />**值：**<br>*&lt;以分號分隔的路徑清單&gt;*<br>範例：**c:\test.exe;c:\test1.exe**<br>**預設值 -** 不排除任何處理序|

### <a name="edge-browser"></a>Edge 瀏覽器

|原則名稱與 URI|詳細資料|
|---------------|------------|-----------|
|**允許瀏覽器**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰<br>****0** - 關閉瀏覽 <br>**1** - 開啟瀏覽 (預設值)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不要顯示建議<br> **1** - 顯示建議 (預設值)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 已停用 (在 Edge 瀏覽器中開啟內部網路網站 - 預設值)<br>**1** - 已啟用 (在 Internet Explorer 中開啟內部網路網站)|
|**允許不要追蹤**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|桌面版和行動裝置版)<br />**資料類型：** 整數<br />**值：<br>****0** - 已停用 (未傳送 DNT - 預設值)<br> **1** - 已啟用 (傳送 DNT)|
|**設定 SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：<br>****0** - 不允許<br> **1** - 允許 (預設值)|
|**允許快顯視窗**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|僅限桌面版<br />**資料類型：** 整數<br />**值：<br>****0**- 封鎖快顯視窗 (預設值)<br> **1** - 允許快顯視窗|
|**允許 Cookie**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** – 允許來自所有網站的 Cookie (預設)<br>**1** - 只封鎖僅協力廠商 Cookie<br>**2** - 封鎖所有 Cookie|
|**允許儲存密碼**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 密碼管理員已停用 <br>**1** - 啟用密碼管理員 (預設值)|
|**允許自動填入**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|僅限桌面版<br />**資料類型：** 整數<br />**值**：<br> **0** - 已停用 (預設值)<br> **1** - 已啟用|
|**設定企業站台清單**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|僅限桌面版<br />**資料類型：**字串<br />**值：**<br>**0** - 尚未設定<br>**1** - 使用 IE 的企業模式網站清單 (如已設定) (預設值)<br>**2** - 指定企業網站清單的位置|

## <a name="general-configuration-policy-settings"></a>一般設定原則設定

使用 Windows 10 的 Microsoft Intune **一般設定原則**，為已註冊的 Windows 10 Desktop 和 Windows 10 行動裝置版裝置設定內建設定。

### <a name="password"></a>密碼

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**需要密碼才可解除鎖定裝置**|-|
|**所需的密碼類型**|指定密碼必須為英數字元，還是只能是數字|
|**需要的密碼類型** - **最小字元集數**| 指定密碼中必須包含多少字元集 (小寫字母、大寫字母、數字與符號)|
|**密碼長度下限**|僅適用於 Windows 10 行動裝置版|
|**抹除裝置前允許的重複登入失敗次數**。|若為執行 Windows 10 的裝置︰如果裝置已啟用 BitLocker，將會在登入失敗達您所指定的次數時置於 BitLocker 復原模式。 如果裝置未啟用 BitLocker，便不會套用此設定。<br>若為執行 Windows 10 行動裝置版的裝置︰登入失敗達您所指定的次數時，就會抹除裝置。|
|**關閉螢幕前的非使用狀態分鐘數**|指定裝置必須閒置多久的時間，才會鎖定螢幕|
|**密碼到期 (天數)**|指定在多久之後必須變更該裝置的密碼|
|**記住密碼歷程記錄**|指定是否要限制使用者建立先前使用過的密碼|
|**記住密碼歷程記錄** - **不得重複使用以前用過的密碼**|指定裝置記憶的先前使用過密碼數目|
|**裝置從閒置狀態恢復時必須輸入密碼**|指定使用者必須輸入密碼才能解除鎖定裝置 (限 Windows 10 行動裝置版)|

### <a name="encryption"></a>加密

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**在行動裝置上要求加密**|在目標裝置上啟用加密<br>(僅限 Windows 10 行動裝置版)|

### <a name="system"></a>System (系統)

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**允許螢幕擷取**|讓使用者擷取裝置螢幕作為映像 (限 Windows 10 行動裝置版)|
|**允許手動取消註冊**|可讓使用者從裝置手動刪除工作場所帳戶|
|**允許手動安裝根憑證**|適用於 Windows 10 行動裝置版|
|**允許將診斷與使用狀況資料傳送給 Microsoft**|可能的值為：<br><br>**否** - 沒有資料會傳送到 Microsoft<br>**基本** - 將有限資訊傳送給 Microsoft<br>**增強** - 將增強的診斷資料傳送給 Microsoft<br>**完整 (建議)** - 傳送和**增強**相同的資料，再加上裝置狀態的相關額外資料|


### <a name="account-and-synchronization"></a>帳戶和同步處理

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許 Microsoft 帳戶**|讓使用者建立 Microsoft 帳戶與裝置之間的關聯|
|**允許手動新增非 Microsoft 帳戶**|讓使用者將電子郵件帳戶新增至未與 Microsoft 帳戶相關聯的裝置|
|**允許同步處理 Microsoft 帳戶的設定**|允許與 Microsoft 帳戶相關聯的裝置和應用程式設定在裝置之間進行同步處理|

### <a name="microsoft-edge"></a>Microsoft Edge

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**允許網頁瀏覽器**|允許在裝置上使用 Edge 網頁瀏覽器<br>(僅限 Windows 10 行動裝置版)|
|**允許網址列中的搜尋建議**|讓您的搜尋引擎在您輸入搜尋片語時建議網站|
|**允許將內部網路流量傳送到 Internet Explorer**|讓使用者在 Internet Explorer 中開啟內部網路網站<br>(僅限 Windows 10 Desktop)|
|**允許不要追蹤**|設定 Edge 瀏覽器以傳送「不要追蹤」標頭給使用者瀏覽的網站|
|**啟用 SmartScreen**||
|**允許動態指令碼處理**|允許在 Edge 瀏覽器中執行 JavaScript 等指令碼|
|**允許快顯視窗**|僅使用於 Windows 10 桌面版|
|**允許 Cookie**||
|**允許自動填入**|可讓使用者變更瀏覽器中的自動完成設定<br>(僅限 Windows 10 Desktop)|
|**允許密碼管理員**|啟用或停用 Edge 密碼管理員功能|
|**企業模式網站清單位置**|指定在何處尋找以企業模式開啟的網站清單。 使用者無法編輯這份清單。<br>(僅限 Windows 10 Desktop)|

### <a name="apps"></a>應用程式

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許應用程式市集**|僅適用於 Windows 10 行動裝置版|



### <a name="cellular"></a>行動電話通訊

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許數據漫遊**|存取資料時允許網路之間的漫遊|
|**允許透過行動數據使用 VPN**|控制裝置是否可以在連線到行動電話通訊網路時存取 VPN 連線|
|**允許透過行動數據進行 VPN 漫遊**|控制裝置是否可以在漫遊到行動電話通訊網路時存取 VPN 連線|

### <a name="hardware"></a>硬體

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|
|**允許相機**|-|
|**允許抽取式存放裝置**|指定是否可以與裝置搭配使用 SD 卡等外部存放裝置|
|**允許 Wi-Fi**|僅適用於 Windows 10 行動裝置版|
|**允許網際網路共用**|允許在裝置上使用網際網路連線共用|
|**允許手動設定 Wi-Fi**|控制使用者可以設定自己的 Wi-Fi 連線或只能使用由 Wi-Fi 設定檔設定的連線<br>(僅限 Windows 10 行動裝置版)|
|**允許自動連線到免費的 Wi-Fi 熱點**|讓裝置自動連線到免費 Wi-Fi 熱點並自動接受任何連線條款和條件|
|**允許地理位置**|指定裝置是否可以使用定位服務資訊|
|**允許 NFC**|允許裝置使用它的近距離無線通訊功能|
|**允許藍牙**|-|
|**允許可透過藍牙搜尋的模式**|讓其他藍芽啟用的裝置探索此裝置|
|**允許藍牙通知**|允許裝置透過藍牙接收廣告|
|**允許重設手機**|控制使用者是否可以將裝置重設成出廠預設值|
|**允許 USB 連線**|控制裝置是否可以透過 USB 連接來存取外接式存放裝置|
|**允許防竊模式**|設定是否啟用 Windows 防竊模式|

### <a name="features"></a>功能

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許複製並貼上**|僅適用於 Windows 10 行動裝置版|
|**允許錄音**|僅適用於 Windows 10 行動裝置版|
|**允許 Cortana**|啟用或停用 Cortana 語音助理|
|**允許行動中心通知**|在裝置鎖定畫面上啟用或停用重要訊息中心通知<br>(僅限 Windows 10 行動裝置版)|

### <a name="windows-defender"></a>Windows Defender

所有設定都僅限 Windows 10 Desktop。

|設定名稱|其他資訊 (如有需要)|
|----------------|----------------------|---------------------|
|**允許即時監視**|啟用惡意程式碼、間諜軟體和其他垃圾軟體的即時掃描|
|**允許行為監視**|讓 Defender 在裝置上檢查某些已知模式的可疑活動|
|**啟用網路檢查系統**|網路檢查系統 (NIS) 可使用 Microsoft Endpoint Protection 中心提供的已知弱點簽章來協助偵測及阻擋惡意流量，以幫助保護裝置不受網路型入侵程式的影響|
|**掃描所有下載**|控制 Defender 是否掃描所有從網際網路下載的檔案|
|**允許指令碼掃描**|讓 Defender 掃描 Internet Explorer 中所使用的指令碼|
|**監視檔案和程式活動**|允許 Defender 監視裝置上的檔案和程式活動|
|**追蹤已解決惡意程式碼的天數**|在您指定的天數內，讓 Defender 繼續追蹤已解決的惡意程式碼，讓您可以手動檢查先前受影響的裝置。 如果您將此天數設為 **0**，惡意程式碼會保留在「隔離」資料夾，而且不會自動移除。 |
|**允許用戶端 UI 存取**|控制是否對使用者隱藏 Windows Defender 使用者介面。<br>變更此設定後，要在使用者電腦下次重新啟動時才會生效。|
|**排程每日快速掃描**|讓您排程每天在您選取的時間進行快速掃描|
|**排程系統掃描**|讓您排程在您指定的日期和時間定期進行完整或快速系統掃描|
|**限制掃描期間的 CPU 使用量**|讓您限制允許使用掃描的 CPU 數量 (從 **1** 至 **100**)|
|**掃描封存檔**|允許 Defender 掃描封存的檔案，例如 .zip 或 .cab 檔案。|
|**掃描電子郵件訊息**|允許 Defender 在電子郵件訊息到達裝置時加以掃描|
|**掃描卸除式磁碟機**|讓 Defender 掃描 USB 隨身碟等卸除式磁碟機|
|**掃描對應的網路磁碟機**|讓 Defender 在對應的網路磁碟機上掃描檔案。<br>如果磁碟機上的檔案是唯讀，Defender 將無法移除在其中發現的任何惡意程式碼。|
|**掃描從網路共用資料夾開啟的檔案**|讓 Defender 在共用網路磁碟機上掃描檔案 (例如，從 UNC 路徑存取者)。<br>如果磁碟機上的檔案是唯讀，Defender 將無法移除在其中發現的任何惡意程式碼。|
|**簽章更新間隔**|指定 Defender 檢查新簽章檔案的間隔。|
|**允許雲端保護**|允許或封鎖 Microsoft Active Protection Service 從您管理的裝置接收惡意程式碼活動的相關資訊。 此資訊未來可用於改善本服務。|
|**提示使用者提交範例**|控制可能需要由 Microsoft 進一步分析以判斷其是否為惡意的檔案，是否自動傳送給 Microsoft|
|**偵測潛在垃圾應用程式**|保護已註冊的 Windows 桌上型裝置，以避免執行被 Windows Defender 歸類為潛在垃圾應用程式的軟體。 您可以不執行這些應用程式，也可以使用稽核模式，在安裝潛在垃圾應用程式時回報。|
|**執行掃描或使用即時保護時所要排除的檔案和資料夾**|將一或多個 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe** 等檔案和資料夾新增至排除清單。 任何即時或已排程的掃描都不會包含這些檔案和資料夾。|
|**執行掃描或使用即時保護時所要排除的副檔名**|將一個或多個 **jpg** 或 **txt** 等副檔名新增至排除清單。 任何即時或已排程的掃描都不會包含有這些副檔名的任何檔案。|
|**執行掃描或使用即時保護時所要排除的處理程序**|將一或多個 **.exe**、**.com** 或 **.scr** 等類型的處理程序新增至排除清單。 任何即時或已排程的掃描都不會包含這些處理程序。|


### <a name="updates"></a>Updates

|設定名稱|其他資訊 (如有需要)|
|----------------|---------------|
|**允許自動更新**|允許自動更新。 設定下列其中一項設定來控制更新行為：<br />**通知下載**<br />**在維護時間自動安裝**<br />**在維護時間自動安裝並重新開機**<br />**在排程時間自動安裝並重新開機**︰請注意，選取這個選項時，您也可以進行下列設定：[對使用者隱藏通知] 和 [定義排程更新的安裝日]。<br>(僅限 Windows 10 Desktop)|
|**允許發行前版本功能**|可讓 Microsoft 將發行前版本設定和功能部署至 Windows 10 裝置。 您可以選取只允許設定，或安裝所有預先發行的設定與功能。|

### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 原則管理裝置的設定及功能](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=Nov16_HO4-->


