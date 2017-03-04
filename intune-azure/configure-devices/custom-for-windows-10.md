---
title: "Windows 10 裝置的 Intune 自訂設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解可用於 Windows 10 自訂設定檔中的相關設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7bcea136-7260-4042-b21b-c7dab86b380d
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 647415914fb0f44807eff7baf7a56ea3a382f027
ms.lasthandoff: 02/18/2017


---

# <a name="custom-device-settings-for-windows-10-devices-in-microsoft-intune"></a>Microsoft Intune 中 Windows 10 裝置的自訂裝置設定

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

 使用適用於 Windows 10 和 Windows 10 行動裝置版的 Microsoft Intune **自訂**設定檔，部署 OMA-URI (開放行動聯盟的統一資源識別項) 設定，此設定可用來控制裝置上的功能。 Windows 10 透過[原則設定服務提供者 (原則 CSP)](https://technet.microsoft.com/itpro/windows/manage/how-it-pros-can-use-configuration-service-providers) 讓許多設定可用。

1. 請使用[如何在 Microsoft Intune 中設定自訂裝置設定](how-to-configure-custom-settings.md)中的指示，即可開始使用。
2. 在 [建立設定檔] 刀鋒視窗中選擇 [設定]，可新增一或多個 OMA URI 設定。
3. 在 [自訂 OMA URI 設定] 刀鋒視窗中，按一下 [新增] 可新增新的值。 您也可以按一下 [匯出]，建立所有值的清單 (以逗號分隔值 (.csv) 的方式設定的檔案)。
4. 為您想要新增的各個 OMA-URI 設定輸入下列資訊。 使用本主題中的清單，了解您可使用的相關設定︰
    - **設定名稱** - 輸入 OMA-URI 設定的唯一名稱，協助您在設定清單中識別該設定。
    - **設定描述** - 選擇性地輸入設定的描述。
    - **資料類型** - 從以下項目選擇︰
        - **字串**
        - **字串 (XML)**
        - **日期和時間**
        - **整數**
        - **浮點數**
        - **布林值**
    - **OMA-URI (區分大小寫)** - 指定您想要為其提供設定的 OMA-URI。
    - **值** - 指定要與您輸入的 OMA-URI 產生關聯的值。
5. 當您完成時，請返回 [建立設定檔] 刀鋒視窗，然後點擊 [建立]。
隨即會建立設定檔，並會出現在 [設定檔清單] 刀鋒視窗上。

## <a name="example"></a>範例
在下方的螢幕擷取畫面中，已啟用 **Connectivity/AllowVPNOverCellular** 設定。 這可讓 Windows 10 裝置在行動電話通訊網路上時，開啟 VPN 連線。

> ![包含 VPN 設定的自訂原則範例](./media/custom-policy-example.png)


## <a name="policy-settings"></a>原則設定

|原則名稱與 URI|詳細資料|
|---------------|------------|-----------|
|**允許自動更新**<br>./Vendor/MSFT/Policy/Config/Update/AllowAutoUpdate|僅限桌面版<br>**資料類型：** 整數<br />**值︰****0** - **5** (預設︰**1**)|
|**排程安裝日期**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallDay|僅限行動裝置版<br>**資料類型：** 整數<br />**值：**<br>**0** - 每一天 (預設值)<br>**1** - 星期日<br>**2** - 星期一<br>**3** - 星期二<br>**4** - 星期三<br>**5** - 星期四<br>**6** - 星期五<br>**7** - 星期六|
|**排程安裝時間**<br>./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：****0** – **23** 小時 (**0** 為午夜) (預設：**3**)|
|**DeviceLock/AllowIdleReturnWithoutPassword**<br>./Vendor/MSFT/Policy/Config/DeviceLock/AllowIdleReturnWithoutPassword|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 使用者無法設定密碼寬限期計時器；值設定為「每次」<br>**1** - 使用者可設定密碼寬限期計時器 (預設)|
|**WiFi/AllowWiFi**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowWiFi|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許 **使用 Wi-Fi 連線**。<br>**1** - **允許使用 Wi-Fi 連線** (預設值)|
|**WiFi/AllowInternetSharing**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowInternetSharing|桌面版和行動裝置版<br>**資料類型：** 整數<br />**值︰****0** – 不允許網際網路共用，**1** - 允許網際網路共用 (預設)|
|**WiFi/AllowAutoConnectToWiFiSenseHotspots**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowAutoConnectToWiFiSenseHotspots|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**WiFi/AllowManualWiFiConfiguration**<br>./Vendor/MSFT/Policy/Config/WiFi/AllowManualWiFiConfiguration|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許在佈建的 MDM 外部使用 Wi-Fi 連線。<br>**1** - 允許在已經佈建的 MDM 外部加入新的網路 SSID (預設值)|
|**System/AllowLocation**<br>./Vendor/MSFT/Policy/Config/System/AllowLocation|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**System/AllowTelemetry**<br>./Vendor/MSFT/Policy/Config/System/AllowTelemetry|桌面版和行動裝置版<br>**資料類型：** 整數<br />**值：**<br>**0** - 不允許 (僅適用於企業版的設定)<br>**1** - 有限<br>**2** - 完整 (預設值)<br>**3** - 完整和診斷資訊|
|**System/AllowExperimentation**<br>./Vendor/MSFT/Policy/Config/System/AllowExperimentation|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許<br>**1** - 只有設定 (預設值)<br>**2** - 設定和試驗|
|**Security/AntiTheftMode**<br>./Vendor/MSFT/Policy/Config/Security/AntiTheftMode|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許反竊取模式<br>**1** - 使用者喜好設定 (預設值)|
|**Connectivity/AllowUSBConnection**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowUSBConnection|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**System/AllowUserToResetPhone**<br>./Vendor/MSFT/Policy/Config/System/AllowUserToResetPhone|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Connectivity/AllowCellularDataRoaming**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowCellularDataRoaming|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Connectivity/AllowVPNOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNOverCellular|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許透過行動電話通訊的 VPN<br>**1** - VPN 可以使用包括行動電話在內的任何連線 (預設值)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Connectivity/AllowVPNRoamingOverCellular**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowVPNRoamingOverCellular|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Connectivity/AllowBluetooth**<br>./Vendor/MSFT/Policy/Config/Connectivity/AllowBluetooth|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** – 不允許使用者開啟藍芽。<br>**1** – 已保留。 使用者可以開啟和設定藍芽 (在 Windows Phone 8.1 for MDM、EAS、Windows 10 desktop 或 Windows 10 Mobile 中不支援)<br>**2** - 已允許。 使用者可以開啟並設定藍牙 (預設值)|
|**Experience/AllowScreenCapture**<br>./Vendor/MSFT/Policy/Config/Experience/AllowScreenCapture|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Experience/AllowTaskSwitcher**<br>./Vendor/MSFT/Policy/Config/Experience/AllowTaskSwitcher|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Experience/AllowVoiceRecording**<br>./Vendor/MSFT/Policy/Config/Experience/AllowVoiceRecording|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Experience/AllowSyncMySettings**<br>./Vendor/MSFT/Policy/Config/Experience/AllowSyncMySettings|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** – 不允許漫遊，**1** - 允許漫遊 (預設)|
|**Experience/AllowManualMDMUnenrollment**<br>./Vendor/MSFT/Policy/Config/Experience/AllowManualMDMUnenrollment|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Accounts/AllowMicrosoftAccountConnection**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowMicrosoftAccountConnection|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Accounts/AllowAddingNonMicrosoftAccountsManually**<br>./Vendor/MSFT/Policy/Config/Accounts/AllowAddingNonMicrosoftAccountsManually|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Security/AllowManualRootCertificateInstallation**<br>./Vendor/MSFT/Policy/Config/Security/AllowManualRootCertificateInstallation|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Security/AllowAddProvisioningPackages**<br>./Vendor/MSFT/Policy/Config/Security/AllowAddProvisioningPackages|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Search/DisableBackoff**<br>./Vendor/MSFT/Policy/Config/Search/DisableBackoff|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** (預設)、**1**|
|**Search/PreventRemoteQueries**<br>./Vendor/MSFT/Policy/Config/Search/PreventRemoteQueries|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0****1**(預設)|
|**Search/AllowUsingDiacritics**<br>./Vendor/MSFT/Policy/Config/Search/AllowUsingDiacritics|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** (預設)、**1**|
|**Search/AlwaysUseAutoLangDetection**<br>./Vendor/MSFT/Policy/Config/Search/AlwaysUseAutoLangDetection|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** (預設)、**1**|
|**Search/DisableRemovableDriveIndexing**<br>./Vendor/MSFT/Policy/Config/Search/DisableRemovableDriveIndexing|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** (預設)、**1**|
|**Search/PreventIndexingLowDiskSpaceMB**<br>./Vendor/MSFT/Policy/Config/Search/PreventIndexingLowDiskSpaceMB|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0****1**(預設)|
|**Search/AllowIndexingEncryptedStoresOrItems**<br>./Vendor/MSFT/Policy/Config/Search/AllowIndexingEncryptedStoresOrItems|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** (預設)、**1**|
|**Security/AllowRemoveProvisioningPackage**<br>./Vendor/MSFT/Policy/Config/Security/AllowRemoveProvisioningPackage|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Security/RequireProvisioningPackageSignature**<br>./Vendor/MSFT/Policy/Config/Security/RequireProvisioningPackageSignature|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** (預設)、**1**|
|**AboveLock/AllowActionCenterNotifications**<br>./Vendor/MSFT/Policy/Config/AboveLock/AllowActionCenterNotifications|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**TextInput/AllowIMENetworkAccess**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMENetworkAccess|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不允許<br>系統會關閉開放式擴充字典。<br>使用者無法：<br>-新增開放式擴充字典<br />-新增搜尋整合設定檔<br>-使用雲端候選字功能<br>-將註冊的字詞傳送給使用者。<br>**1** - 允許<br>預設可加入並使用開放式擴充字典。 此外根據預設，將會使用搜尋整合功能。<br>使用者可以：<br>使用雲端候選字功能。|
|**TextInput/AllowIMELogging**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowIMELogging|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 關閉錯誤轉換記錄功能。<br>**1** - 開啟錯誤轉換記錄功能 (預設)|
|**TextInput/AllowJapaneseNonPublishingStandardGlyph**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseNonPublishingStandardGlyph|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**TextInput/AllowJapaneseIVSCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIVSCharacters|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**TextInput/AllowJapaneseUserDictionary**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseUserDictionary|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設)|
|**TextInput/AllowJapaneseIMESurrogatePairCharacters**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowJapaneseIMESurrogatePairCharacters|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**TextInput/ExcludeJapaneseIMEExceptShiftJIS**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptShiftJIS|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不篩選任何字元 (預設值)<br>**1** - 篩選 Shift JIS 字元以外的所有字元|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br />**0** - 不篩選任何字元 (預設值)<br>**1** - 篩選 JIS0208 字元以外的所有字元|
|**TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC**<br>./Vendor/MSFT/Policy/Config/TextInput/ExcludeJapaneseIMEExceptJIS0208andEUDC|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不篩選任何字元 (預設值)<br>**1** - 篩選 JIS0208 字元或 EUDC 字元以外的所有字元|
|**TextInput/AllowInputPanel**<br>./Vendor/MSFT/Policy/Config/TextInput/AllowInputPanel|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Bluetooth/AllowDiscoverableMode**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowDiscoverableMode|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Bluetooth/AllowAdvertising**<br>./Vendor/MSFT/Policy/Config/Bluetooth/AllowAdvertising|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowDataSense**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDataSense|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowVPN**<br>./Vendor/MSFT/Policy/Config/Settings/AllowVPN|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowWorkplace**<br>./Vendor/MSFT/Policy/Config/Settings/AllowWorkplace|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowDateTime**<br>./Vendor/MSFT/Policy/Config/Settings/AllowDateTime|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowLanguage**<br>./Vendor/MSFT/Policy/Config/Settings/AllowLanguage|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowRegion**<br>./Vendor/MSFT/Policy/Config/Settings/AllowRegion|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowSignInOptions**<br>./Vendor/MSFT/Policy/Config/Settings/AllowSignInOptions|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowYourAccount**<br>./Vendor/MSFT/Policy/Config/Settings/AllowYourAccount|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowPowerSleep**<br>./Vendor/MSFT/Policy/Config/Settings/AllowPowerSleep|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Settings/AllowAutoPlay**<br>./Vendor/MSFT/Policy/Config/Settings/AllowAutoPlay|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Experience/AllowCortana**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCortana|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**Search/SafeSearchPermissions**<br>./Vendor/MSFT/Policy/Config/Search/SafeSearchPermissions|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 嚴格，針對成人內容進行最高程度的篩選<br>**1** - 中等，針對成人內容進行中等程度的篩選 (將不會篩選有效的搜尋結果 - 預設值)|
|**Experience/AllowCopyPaste**<br>./Vendor/MSFT/Policy/Config/Experience/AllowCopyPaste|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**強制開始大小**<br>./Vendor/MSFT/Policy/Config/Start/ForceStartSize|僅限行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 允許使用者變更大小 (預設值)<br>**1** - 強制執行非全螢幕<br>**2** - 強制執行全螢幕|
|**Update/RequireDeferUpgrade**<br>./Vendor/MSFT/Policy/Config/Update/RequireDeferUpgrade|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0**：不延遲升級 (留在最新分支、CB - 預設值)<br>**1**：啟用更新且延後升級 (裝置遵循商務、CBB、規則的最新分支)<br />如需詳細資料，請參閱：<br>[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226.aspx)<br>[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpdatePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpdatePeriod|桌面版和行動裝置版<br>**描述：**最多延後 4 週進行軟體更新的原則<br />**資料類型：** 整數<br />**值：**<br> **0**：立即套用更新 (預設值)<br>**1**-**4**：延遲軟體更新的週數。<br />如需詳細資料，請參閱：<br>[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226.aspx)<br>[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/DeferUpgradePeriod**<br>./Vendor/MSFT/Policy/Config/Update/DeferUpgradePeriod|桌面版和行動裝置版<br>**描述：**延遲最多 8 個月進行功能升級的原則<br />**資料類型：** 整數<br />**值：**<br>**0**：立即套用更新 (預設值)<br>**1**-**8**：延遲功能升級的月數。<br />如需詳細資料，請參閱：<br>[Windows 10 服務簡介](https://technet.microsoft.com/library/mt598226.aspx)<br>[規劃 Windows 10 部署](https://technet.microsoft.com/library/mt574241.aspx)|
|**Update/PauseDeferrals**<br>./Vendor/MSFT/Policy/Config/Update/PauseDeferrals|桌面版和行動裝置版<br>**描述：**允許裝置停止接收更新及升級 5 週。<br />**資料類型：** 整數<br />**值：**<br>**0**：立即套用更新 (預設值)<br>**1**︰暫停更新及升級 (5 週後過期)|

## <a name="windows-defender-settings"></a>Windows Defender 設定

|原則名稱與 URI|詳細資料|
|---------------|-----------|
|**AllowRealtimeMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowRealtimeMonitoring|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowBehaviorMonitoring**<br>./Vendor/MSFT/Policy/Config/Defender/AllowBehaviorMonitoring|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowIntrusionPreventionSystem**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIntrusionPreventionSystem|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowIOAVProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowIOAVProtection|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowScriptScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScriptScanning|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowOnAccessProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowOnAccessProtection|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**RealTimeScanDirection**<br>./Vendor/MSFT/Policy/Config/Defender/RealTimeScanDirection|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** – 監視所有檔案 (預設)<br>**1** - 監視傳入檔案<br>**2** - 監視傳出檔案|
|**DaysToRetainCleanedMalware**<br>./Vendor/MSFT/Policy/Config/Defender/DaysToRetainCleanedMalware|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - **90** - 代表惡意程式碼將保留多久的時間<br>**預設：****0** - 永遠保留在隔離資料夾中，且不會自動移除|
|**AllowUserUIAccess**<br>./Vendor/MSFT/Policy/Config/Defender/AllowUserUIAccess|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**ScanParameter**<br>./Vendor/MSFT/Policy/Config/Defender/ScanParameter|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**1** - 快速掃描 (預設值)<br>**2** - 完整掃描|
|**ScheduleScanDay**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanDay|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 每天 (預設值)<br>**1** - 星期一<br>**2** - 星期二<br>**3** - 星期三<br>**4** - 星期四<br>**5** - 星期五<br>**6** - 星期六<br>**7** - 星期日<br>**8** - 未排定掃描|
|**ScheduleScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleScanTime|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 12:00 am<br>**60** - 1:00 am<br>**120** - 2:00 am (預設值)<br>**180** - 3:00 am<br>**240** - 4:00 am<br>**300** - 5:00 am<br>**360** - 6:00 am<br>**420** - 7:00 am<br>**480** - 8:00 am<br>**540** - 9:00 am<br>**600** - 10:00 am<br>**660** - 11:00 am<br>**720** - 12:00 pm<br>**780** - 1:00 pm<br>**840** - 2:00 pm<br>**900** - 3:00 pm<br>**960** - 4:00 pm<br>**1020** - 5:00 pm<br>**1080** - 6:00 pm<br>**1140** - 7:00 pm<br>**1200** - 8:00 pm<br>**1260** - 9:00 pm<br>**1320** - 10:00 pm<br>**1381** - 維護期間|
|**ScheduleQuickScanTime**<br>./Vendor/MSFT/Policy/Config/Defender/ScheduleQuickScanTime|僅限桌面版<br>**資料類型：** 整數<br />**值：**<br>**0** - 12:00 am<br>**60** - 1:00 am<br>**120** - 2:00 am (預設值)<br>**180** - 3:00 am<br>**240** - 4:00 am<br>**300** - 5:00 am<br>**360** - 6:00 am<br>**420** - 7:00 am<br>**480** - 8:00 am<br>**540** - 9:00 am<br>**600** - 10:00 am<br>**660** - 11:00 am<br>**720** - 12:00 pm<br>**780** - 1:00 pm<br>**840** - 2:00 pm<br>**900** - 3:00 pm<br>**960** - 4:00 pm<br>**1020** - 5:00 pm<br>**1080** - 6:00 pm<br>**1140** - 7:00 pm<br>**1200** - 8:00 pm<br>**1260** - 9:00 pm<br>**1320** - 10:00 pm<br>**1380** - 11:00 pm|
|**AVGCPULoadFactor**<br>./Vendor/MSFT/Policy/Config/Defender/AVGCPULoadFactor|僅限桌面版<br />**資料類型：** 整數<br />**值：****0** - **100** (預設：**50**)|
|**AllowArchiveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowArchiveScanning|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowEmailScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowEmailScanning|僅限桌面版<br />**資料類型：** 整數<br>**值︰****0** - 不允許 (預設)，**1** – 允許|
|**AllowFullScanRemovableDriveScanning**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanRemovableDriveScanning|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許 (預設)，**1** – 允許|
|**AllowFullScanOnMappedNetworkDrives**<br>./Vendor/MSFT/Policy/Config/Defender/AllowFullScanOnMappedNetworkDrives|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**AllowScanningNetworkFiles**<br>./Vendor/MSFT/Policy/Config/Defender/AllowScanningNetworkFiles|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** – 不允許，**1** – 允許 (預設) - 若設為允許，也會在 RTP 開啟時執行|
|**SignatureUpdateInterval**<br>./Vendor/MSFT/Policy/Config/Defender/SignatureUpdateInterval|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 不會在某個時間間隔檢查簽章<br>**1** - 每小時檢查簽章<br>**2** – 每隔 2 小時檢查一次，依此類推。<br>**24** - 每天檢查<br>**預設值︰** 8 – 每隔 8 小時檢查一次|
|**AllowCloudProtection**<br>./Vendor/MSFT/Policy/Config/Defender/AllowCloudProtection|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** - 不允許，**1** – 允許 (預設值)|
|**SubmitSamplesConsent**<br>./Vendor/MSFT/Policy/Config/Defender/SubmitSamplesConsent|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 一律要求確認 (預設值)<br>**1** - 自動傳送安全的範例<br>**2** - 一律不傳送<br>**3** - 自動傳送所有的範例|
|**ExcludedExtensions**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedExtensions|僅限桌面版<br />**資料類型：**字串<br />**值：**<br>*&lt;以分號分隔的副檔名清單&gt;*例如 **obj;lib**<br>**預設值：**不排除任何副檔名|
|**ExcludedPaths**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedPaths|僅限桌面版<br />**資料類型：**字串<br />**值：**<br />*&lt;以分號分隔的路徑清單&gt;*<br />範例：**c:\test;c:\test1.exe**<br />**預設值：** 不排除任何路徑|
|**ExcludedProcesses**<br>./Vendor/MSFT/Policy/Config/Defender/ExcludedProcesses|僅限桌面版<br />**資料類型：**字串<br />**值：**<br>*&lt;以分號分隔的路徑清單&gt;*<br>範例：**c:\test.exe;c:\test1.exe**<br>**預設值：** 不排除任何程序|

## <a name="edge-browser-settings"></a>Edge 瀏覽器設定

|原則名稱與 URI|詳細資料|
|---------------|------------|-----------|
|**允許瀏覽器**<br>./Vendor/MSFT/Policy/Config/Browser/AllowBrowser|僅限行動裝置版<br />**資料類型：** 整數<br />**值︰****0**：關閉瀏覽，**1**︰開啟瀏覽 (預設)|
|**AllowSearchSuggestionsinAddressBar**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSearchSuggestionsinAddressBar|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值︰****0**︰不要顯示建議，**1**︰顯示建議 (預設)|
|**SendIntranetTraffictoInternetExplorer**<br>./Vendor/MSFT/Policy/Config/Browser/SendIntranetTraffictoInternetExplorer|僅限桌面版<br />**資料類型：** 整數<br />**值：**<br>**0** - 已停用 (在 Microsoft Edge 瀏覽器中開啟內部網路網站 - 預設值)<br>**1** - 已啟用 (在 Internet Explorer 中開啟內部網路網站)。|
|**允許不要追蹤**<br>./Vendor/MSFT/Policy/Config/Browser/AllowDoNotTrack|桌面版和行動裝置版)<br />**資料類型：** 整數<br />**值︰****0** – 停用 (不傳送 DNT - 預設)，**1** – 啟用 (傳送 DNT)|
|**設定 SmartScreen**<br>./Vendor/MSFT/Policy/Config/Browser/AllowSmartScreen|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：****0** – 不允許，**1** – 允許 (預設)|
|**允許快顯視窗**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPopups|僅限桌面版<br />**資料類型：** 整數<br />**值：****0** – 封鎖快顯視窗 (預設)，**1** – 允許快顯視窗|
|**允許 Cookie**<br>./Vendor/MSFT/Policy/Config/Browser/AllowCookies|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** – 允許來自所有網站的 Cookie (預設)<br>**1** - 只封鎖僅協力廠商 Cookie<br>**2** - 封鎖所有 Cookie|
|**允許儲存密碼**<br>./Vendor/MSFT/Policy/Config/Browser/AllowPasswordManager|桌面版和行動裝置版<br />**資料類型：** 整數<br />**值：**<br>**0** - 密碼管理員已停用； <br>**1** - 啟用密碼管理員 (預設值)|
|**允許自動填入**<br>./Vendor/MSFT/Policy/Config/Browser/AllowAutofill|僅限桌面版<br />**資料類型：** 整數<br />**值︰****0** – 停用 (預設)，**1** – 啟用|
|**設定企業站台清單**<br>./Vendor/MSFT/Policy/Config/Browser/EnterpriseModeSiteList|僅限桌面版<br />**資料類型：**字串<br />**值︰<br>**0** – 未設定<br>**1** – 使用 IE 的企業模式網站清單，如已設定 (預設)<br>**2** – 指定企業網站清單位置|

