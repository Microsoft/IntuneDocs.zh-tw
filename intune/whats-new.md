---
title: Microsoft Intune 的新功能 - Azure | Microsoft Docs
titleSuffix: ''
description: 了解 Intune Azure 入口網站中的新功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 25a3acda374266a0fbd16feabde7787204555ea2
ms.sourcegitcommit: 876719180e0d73b69fc053cf67bb8cc40b364056
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2019
ms.locfileid: "66264178"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能

了解每週的 Microsoft Intune 新功能 您也可以找到[即將推出的變更](in-development.md)、[重要通知](#notices)，以及[過去版本](whats-new-archive.md)的相關資訊。 

> [!Note]
> 某些功能在首度發行時可能會花費數週的時間，而可能無法在第一週就提供給所有客戶。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-may-20-2019"></a>2019 年 5 月 20 日當週 

### <a name="app-management"></a>應用程式管理

#### <a name="windows-company-portal-app----3316993---"></a>Windows 公司入口網站應用程式 <!-- 3316993 -->
Windows 公司入口網站應用程式將新增標籤為 [裝置]  的頁面。 [裝置]  頁面會向終端使用者顯示其所有已註冊裝置。 使用者會在使用 10.3.4291.0 版或更新版本時，於公司入口網站看到這項變更。 如需設定公司入口網站的相關資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 裝置 OrderID 屬性名稱變更為群組標籤 <!-- 4659453 -->

為了更容易查看，Autopilot 裝置上的 **OrderID** 屬性名稱已變更為**群組標籤**。 當您使用 CSV 上傳 Autopilot 裝置資訊時，必須使用群組標籤作為資料行標題，而非 OrderID。  

## <a name="week-of-may-13-2019"></a>2019 年 5 月 13 日當週 

### <a name="app-management"></a>應用程式管理

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Intune 原則會更新驗證方法與公司入口網站應用程式安裝  <!-- 1927359 idready wnready-->
在已透過 [設定助理] 註冊的裝置上 (透過 Apple 的公司裝置註冊方法之一)，Intune 將不再支援公司入口網站 (當使用者從 App Store 手動安裝時)。 只有當您在註冊期間使用 Apple 設定助理進行驗證時，此變更才有意義。 此變更也只會影響透過下列各項註冊的 iOS 裝置：  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple 裝置註冊方案 (DEP)

如果使用者從 App Store 安裝公司入口網站應用程式，接著嘗試透過它註冊這些裝置，則它們將會收到錯誤。 這些裝置應該只有已在註冊期間透過 Intune 自動推送時，才會使用公司入口網站。 位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 如果您想讓 DEP 裝置使用者擁有公司入口網站，將必須在註冊設定檔中指定喜好設定。 

此外，會在 iOS 公司入口網站應用程式中移除 [識別您的裝置]  畫面。 因此，想要啟用條件式存取或部署公司應用程式的管理員必須更新 DEP 註冊設定檔。 此需求只有在 DEP 註冊是透過安裝小幫手驗證時才適用。 在該情況下，您必須將公司入口網站推送到裝置。 若要這樣做，請選擇 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [屬性]  > 將 [安裝公司入口網站]  設定為 [是]  。

若要在已經註冊的 DEP 裝置上安裝公司入口網站，您將必須移至 [Intune] > [用戶端應用程式]，然後使用應用程式設定原則來將它推送為受控應用程式。 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>設定終端使用者如何使用應用程式保護原則來更新企業營運 (LOB) 應用程式 <!-- 3568384 -->
您現在可以設定終端使用者可從何處取得企業營運 (LOB) 應用程式的更新版本。 終端使用者將可在 [應用程式最小版本]  條件式啟動對話方塊中看見此功能，其將提示終端使用者更新為 LOB 應用程式的最小版本。 您必須提供這些更新詳細資料作為 LOB 應用程式保護原則 (APP) 一部分。 此功能適用於 iOS 和 Android。 在 iOS 上，此功能需要整合 (或使用包裝工具包裝) 應用程式與 Intune SDK for iOS 10.0.7 版或更新版本。 在 Android 上，此功能需要最新版的公司入口網站。 若要設定終端使用者更新 LOB 應用程式的方式，應用程式需要透過金鑰 `com.microsoft.intune.myappstore` 傳送給它的受控應用程式設定原則。 傳送的值將定義終端使用者要從哪個存放區下載應用程式。 如果透過公司入口網站部署應用程式，則值必須為 `CompanyPortal`。 針對任何其他存放區，您必須輸入完整的 URL。

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Intune 管理延伸模組 PowerShell 指令碼  <!-- 3734186 idready -->
您可以設定 PowerShell 指令碼，以在裝置上使用使用者的管理員權限來執行。 如需詳細資訊，請參閱[在 Windows 10 裝置上的 Intune 中使用 PowerShell 指令碼](intune-management-extension.md)和 [Win32 應用程式管理](apps-win32-app-management.md)。

#### <a name="android-enterprise-app-management----4459905---"></a>Android 企業應用程式管理 <!-- 4459905 -->
為讓 IT 系統管理員輕鬆地設定及使用 Android 企業管理，Intune 會自動新增四個通用 Android 企業相關應用程式到 Intune 系統管理主控台。 四個 Android 企業應用程式如下：

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - 用於 Android 企業完全受控案例。
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -  協助您登入您的帳戶 (若您使用雙因素驗證)。
- **[Intune 公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - 用於 應用程式保護原則 (APP) 與 Android 企業公司設定檔案例。
- [受控家用案例](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) - 用於 Android 企業專用/資訊站案例。

之前，IT 系統管理員需要在安裝期間於[受控 Google Play 商店](https://play.google.com/store/apps)中手動尋找及核准這些應用程式。 此變更移除了先前那些手動步驟，讓客戶可以更輕鬆、更快速地使用 Android 企業管理。

系統管理員在第一次連線到其 Intune 租用戶的受控 Google Play 商店時，將會看到這四個應用程式自動新增到其 Intune 應用程式清單。 如需詳細資訊，請參閱[將您的 Intune 帳戶連結到受控 Google Play 帳戶](connect-intune-android-enterprise.md)。 針對已連結其租用戶或已使用 Android 企業的租用戶，系統管理員不需要採取任何動作。 在 2019 年 5 月服務推出之後 7 天內，那四個應用程式將會自動顯示。

### <a name="device-configuration"></a>裝置設定

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Defender ATP 的 Intune 安全性工作 (公開預覽)     <!-- 3208597 -->
在公開預覽中，您可以使用 Intune 來管理 Microsoft Defender 進階威脅防護 (ATP) 的安全性工作。 這會與 ATP 整合，並新增一個以風險為基礎的方法來探索、設定優先順序及補救端點弱點和錯誤設定，同時減少從探索到風險降低之間的時間。

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組 <!-- 3617671   idstaged-->
許多 Windows 10 及更新版本的裝置都具有信賴平台模組 (TPM) 晶片組。 這個更新引進新的合規性設定，此設定會檢查裝置上的 TPM 晶片版本。 

[Windows 10 與更新版本的合規性原則設定](compliance-policy-create-windows.md#device-security)說明此設定。

適用於：Windows 10 及更新版本

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>在 iOS 裝置上，防止終端使用者修改其個人熱點，並停用 Siri 伺服器記錄 <!-- 4097904   --> 
您會在 iOS 裝置上建立裝置限制設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 選取 [iOS] 作為平台  > 選取 [裝置限制]  作為設定檔類型)。 此更新包括您可以設定的新設定：

- **內建應用程式**：在伺服器端記錄 Siri 命令
- **無線**：使用者修改個人熱點 (僅限受監督)

若要查看這些設定，請移至[適用於 iOS 的內建應用程式設定](device-restrictions-ios.md#built-in-apps)和[適用於 iOS 的無線設定](device-restrictions-ios.md#wireless)。

適用於：iOS 12.2 與更新版本

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>適用於 macOS 裝置的新教室應用程式裝置限制設定 <!-- 4097905   --> 
您可以為 macOS 裝置建立裝置設定設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 選取 [macOS]  作為平台 > 選取 [裝置限制]  作為設定檔類型)。 此更新包括新的教室應用程式設定、封鎖螢幕擷取畫面的選項，以及停用 iCloud 照片圖庫的選項。

若要查看目前的設定，請前往 [macOS 裝置設定以使用 Intune 允許或限制功能](device-restrictions-macos.md)。

適用於：macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>將用來存取 App Store 設定的 iOS 密碼重新命名<!-- 4557891  -->
將 [存取 App Store 的密碼]  設定重新命名為 [所有購買都需要 iTunes 密碼]  ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (針對平台) > [裝置限制]  (針對設定檔類型) > [App Store、文件檢視、遊戲]  )。

若要查看可用的設定，請移至 [App Store、文件檢視、遊戲的 iOS 設定](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

適用於：iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender 進階威脅防護基準 (預覽)  <!--  3754134 -->
我們已新增 [Microsoft Defender 進階威脅防護](security-baseline-settings-defender-atp.md)設定的安全性基準預覽。  

### <a name="device-enrollment"></a>裝置註冊

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows 註冊狀態頁面 (ESP) 現已全面上市 <!-- 3605348 -->
註冊狀態頁面現已結束預覽。 如需詳細資訊，請參閱[設定註冊狀態頁面](windows-enrollment-status.md)。


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune 使用者介面更新 - 建立 Autopilot 註冊設定檔  <!-- 4593669 -->
建立 Autopilot 註冊設定檔的使用者介面已更新，以符合 Azure 使用者介面樣式。 如需詳細資訊，請參閱[建立 Autopilot 註冊設定檔](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile) \(英文\)。 接下來，將其他 Intune 案例更新為這個新的 UI 樣式。

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>針對所有 Windows 裝置啟用 Autopilot 重設 <!-- 4225665 -->
Autopilot 重設目前適用於所有 Windows 裝置，即使未設定為使用註冊狀態頁面的裝置也適用。 如果未在初始裝置註冊期間針對裝置設定註冊狀態頁面，則裝置將在登入之後直接前往桌面。 在 Intune 中最多可能需要 8 小時來進行同步處理並顯示符合規範。 如需詳細資訊，請參閱[使用遠端 Windows Autopilot 重設來重設裝置](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote) \(部分機器翻譯\)。

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>搜尋所有裝置時不需要精確的 IMEI 格式 <!--30407680 -->
您不需要在搜尋**所有裝置**時，於 IMEI 編號中包含空格。

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>在 Apple 入口網站刪除裝置將反映在 Intune 入口網站中 <!--2489996 -->
若從 Apple 的裝置註冊計劃或 Apple 商務管理員入口網站刪除裝置，在下次同步時，會自動將該裝置從 Intune 刪除。


### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>加密報表已結束公開預覽   <!-- 4587546      -->
現已正式推出[適用於 BitLocker 和裝置加密的報表](encryption-monitor.md)，其不再是公開預覽的一部分。 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>適用於 iOS 和 Android 裝置的 Outlook 簽章和生物特徵辨識設定 <!-- 4050557 -->
您現在可以指定是否要在 iOS 和 Android 裝置上的 Outlook 中啟用預設簽章。 此外，您可以選擇允許使用者在 iOS 上的 Outlook 中變更生物特徵辨識設定。

## <a name="week-of-may-6-2019"></a>2019 年 5 月 6 日當週 

### <a name="device-configuration"></a>裝置設定

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>iOS 裝置 F5 Access 的網路存取控制 (NAC) 支援 <!-- 4500808 -->

F5 發行了 BIG-IP 13 的更新，可在 Intune 中於 iOS 上的 F5 Access 提供 NAC 功能。 若要使用此功能：

- 將 BIG-IP 更新為 13.1.1.5 版。 不支援 BIG-IP 14。
- 針對 NAC 整合 BIG-IP 與 Intune。 步驟位於 [Overview:Configuring APM for device posture checks with endpoint management systems](https://support.f5.com/kb/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) (概觀：設定 APM 以向端點管理系統確認裝置狀態)。
- 在 Intune 中，確認 VPN 設定檔中的 [啟用網路存取控制 (NAC)]  設定。

若要查看可用的設定，請前往[在 iOS 裝置上進行 VPN 設定](vpn-settings-ios.md)。

適用於：iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>已更新適用於 Microsoft Intune 的 PFX 憑證連接器 <!-- doc-vso 1521237  -->  
我們發行了[適用於 Microsoft Intune 的 PFX 認證連接器](certficates-pfx-configure.md#whats-new-for-connectors)更新，可將輪詢間隔從 5 分鐘縮短為 30 秒。

## <a name="week-of-april-22-2019"></a>2019 年 4 月 22 日當週

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>使用合規性管理員來建立 Microsoft Intune 的評定<!-- 4404750 -->

[合規性管理員](https://servicetrust.microsoft.com/ComplianceManager) (這會開啟另一個 Microsoft 網站) 是 Microsoft 服務信任入口網站中以工作流程為基礎的風險評定工具。 它可讓您追蹤、指派及驗證您組織中與 Microsoft 服務相關的合規性活動。 您可以使用 Office 365、Azure、Dynamics、專業服務和 Intune 來建立您自己的合規性評定。 Intune 提供兩個評定 - FFIEC 和 GDPR。

合規性管理員藉由將控制項細分為由 Microsoft 管理的控制項及由您組織管理的控制項，來協助您專注於工作。 您可以完成評定，然後匯出和列印評定。

[美國聯邦金融檢查委員會 (Federal Financial Institutions Examination Council，FFIEC)](https://www.microsoft.com/trustcenter/compliance/FFIEC) (這會開啟另一個 Microsoft 網站) 合規性是由 FFIEC 發行的一組線上銀行標準。 使用 Intune 的金融機構最常有此評定要求。 其闡釋 Intune 如何協助符合與公用網路工作負載相關的 FFIEC 網路安全性指導方針。 Intune 的 FFIEC 評定是合規性管理員中的第二項 FFIEC 評定。

您可在下列範例中看到 FFIEC 控制項的細分。 Microsoft 涵蓋 64 個控制項。 您會負責其餘 12 個控制項。

![查看 FFIEC 的範例 Intune 評定，其中包含客戶動作和 Microsoft 動作](./media/intune-ffiec-assessment-status.png)

[一般資料保護規定 (GDPR)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview) (這會開啟另一個 Microsoft 網站) 是協助保護個人及其資料權利的歐盟 (EU) 法律。 GDPR 是協助遵守隱私權法規最常有的評定要求。 

您可在下列範例中看到 GDPR 控制項的細分。 Microsoft 涵蓋 49 個控制項。 您會負責其餘 66 個控制項。

![查看 GDPR 的範例 Intune 評定，其中包含客戶動作和 Microsoft 動作](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019 年 4 月 15 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Android 應用程式防護原則的 OpenSSL 加密 <!-- 3747362 -->
Android 裝置上 Intune 應用程式防護原則 (APP) 現在使用符合 FIPS 140-2 規範的 OpenSSL 加密程式庫。 如需詳細資訊，請參閱 [Microsoft Intune 的 Android 應用程式防護原則設定](app-protection-policy-settings-android.md)的[加密](app-protection-policy-settings-android.md#encryption)一節。

#### <a name="enable-win32-app-dependencies----2617348----"></a>啟用 Win32 應用程式相依性 <!-- 2617348  -->
身為管理員，您可以要求將其他應用程式安裝為相依性，再安裝您的 Win32 應用程式。 具體來說，裝置必須安裝相依的應用程式，才能安裝 Win32 應用程式。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  以顯示 [新增應用程式]  刀鋒視窗。 選取 [Windows 應用程式 (Win32)]  作為 [應用程式類型]  。 新增應用程式之後，您可以選取 [相依性]  以新增必須先安裝才能安裝 Win32 應用程式的相依應用程式。 如需詳細資訊，請參閱 [Intune 獨立版 - Win32 應用程式管理](apps-win32-app-management.md)。 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>商務用 Microsoft Store 應用程式的應用程式版本安裝資訊 <!-- 3537391   -->
應用程式安裝報表包含商務用 Microsoft Store 應用程式的應用程式版本資訊。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]  。 選取 [商務用 Microsoft Store 應用程式]  ，然後在 [監視]  區段下選取 [裝置安裝狀態]  。

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>新增 Win32 應用程式需求規則 <!-- 3676883   -->
您可以建立以 PowerShell 指令碼、登錄值和檔案系統資訊為基礎的需求規則。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 然後在 [新增應用程式]  刀鋒視窗中，選取 [Windows 應用程式 (Win32)]  作為 [應用程式類型]  。  選取 [需求]   > [新增]  以設定其他需求規則。 然後，選取 [檔案類型]  、[登錄]  或 [指令碼]  作為 [需求類型]  。 如需詳細資訊，請參閱 [Win32 應用程式管理](apps-win32-app-management.md)。

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>設定在已註冊 Intune 並加入 Azure AD 之裝置上安裝您的 Win32 應用程式 <!-- 3695227  -->
您可以指派在已註冊 Intune 並加入 Azure AD 的裝置上安裝 Win32 應用程式。 如需 Intune 中 Win32 應用程式的詳細資訊，請參閱 [Win32 應用程式管理](apps-win32-app-management.md)。

#### <a name="device-overview-shows-primary-user---794259----"></a>裝置概觀會顯示主要使用者 <!--794259  -->
裝置概觀頁面會顯示主要使用者，也稱為使用者裝置親和性使用者 (UDA)。 若要查看裝置的主要使用者，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置。 主要使用者會出現在 [概觀]  頁面頂端附近。

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>Android Enterprise 工作設定檔裝置的其他受控 Google Play 應用程式報告 <!-- 4105925  -->
針對部署到 Android Enterprise 工作設定檔裝置的受控 Google Play 應用程式，您可以檢視裝置上所安裝應用程式的特定版本號碼。 這只適用於必要的應用程式。 未來版本中將會針對可用的應用程式啟用相同功能。 

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS 協力廠商鍵盤 <!-- 4111843   -->
iOS **協力廠商鍵盤**設定的 Intune 應用程式防護原則 (APP) 支援將因 iOS 平台的變更結束。 您將無法在 Intune 管理主控台中設定此設定，且無法在 Intune 應用程式 SDK 中於用戶端上實行此設定。

### <a name="device-configuration"></a>裝置設定

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>在 macOS 裝置上設定登入設定及控制重新啟動選項 <!-- 1210083  -->
在 iOS 裝置上，您可以建立裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 選擇 [macOS]  平台 > [裝置功能]  設定檔類型)。 此更新包含新的登入視窗設定，例如顯示自訂橫幅、選擇使用者登入的方式、顯示或隱藏電源設定等。

若要查看這些設定，請前往 [macOS 裝置功能設定](macos-device-features-settings.md)。

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>在以多應用程式 kiosk 模式執行的 Android Enterprise 裝置擁有者專用裝置上設定 WiFi <!--3041940  -->
當以多應用程式 kiosk 模式的專用裝置執行時，可啟用 Android Enterprise 裝置擁有者的設定。 在此更新中，使用者可以設定並連線到 WiFi 網路 ([Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [僅限裝置擁有者]、[裝置限制]  設定檔類型 > [專用裝置]   > [Kiosk 模式：   多應用程式] > [WiFi 設定]  )。 

若要查看您可以設定的所有設定，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。

適用於：以多應用程式 kiosk 模式執行的 Android Enterprise 專用裝置


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>在以多應用程式 kiosk 模式執行的 Android Enterprise 裝置擁有者專用裝置上設定藍牙和配對 <!-- 3041941  -->
當以多應用程式 kiosk 模式的專用裝置執行時，可啟用 Android Enterprise 裝置擁有者的設定。 在此更新中，終端使用者可以啟用藍牙，並透過藍牙配對裝置 ([Intune]   > [裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台 > [僅限裝置擁有者]、[裝置限制]  設定檔類型 > [專用裝置]   > [Kiosk 模式  ：  多應用程式] > [藍牙設定]  )。 

若要查看您可以設定的所有設定，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。

適用於：以多應用程式 kiosk 模式執行的 Android Enterprise 專用裝置

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>在 Intune 中建立和使用 OEMConfig 裝置組態設定檔 <!-- 3305883  -->
在此更新中，Intune 支援透過 OEMConfig 設定 Android Enterprise 裝置。 具體來說，您可以建立裝置組態設定檔，並使用 OEMConfig 將設定套用到 Android Enterprise 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android Enterprise]  平台)。

對 OEM 的支援目前是依個別 OEM 來提供。 如果您想要的 OEMConfig 應用程式不在 OEMConfig 應用程式清單中，請連絡 `IntuneOEMConfig@microsoft.com`。

若要深入了解此功能，請前往[在 Microsoft Intune 中透過 OEMConfig 使用和管理 Android Enterprise 裝置](android-oem-configuration-overview.md)。

適用於：Android Enterprise

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows 更新通知  <!-- 3316758, 3316782  -->
Windows 更新通道設定中新增了兩項「使用者體驗設定」  ，可從 Intune 主控台進行管理。 您現在可以：
- 封鎖或允許使用者[掃描 Windows 更新](windows-update-settings.md#block-user-from-scanning-for-windows-updates)。
- 管理使用者所看到的 [Windows 更新通知層級](windows-update-settings.md#windows-update-notification-level)。

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>新增 Android Enterprise 裝置擁有者的裝置限制設定 <!-- 3574254  -->
在 Android Enterprise 裝置上，您可以建立裝置限制設定檔來允許或限制功能、設定密碼規則等 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 選擇 [Android Enterprise]  平台 > [僅限裝置擁有者] > [裝置限制]  設定檔類型)。 

此更新包含新的密碼設定、允許完全受控的裝置對 Google Play 商店中應用程式進行完整存取等。 若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。 

適用於：完全受控的 Android Enterprise 裝置

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>在 Windows 10 裝置合規性政策中檢查是否有 TPM 晶片組 <!-- 3617671 -->

此功能已延後，應該會包含在未來版本中。

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>更新 Windows 10 及更新版本裝置上 Microsoft Edge 瀏覽器的 UI 變更 <!-- 3775833   -->
當您建立裝置組態設定檔時，您可以允許或限制 Windows 10 及更新版本裝置上的 Microsoft Edge 功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [裝置限制]  設定檔類型 > [Microsoft Edge 瀏覽器]  )。 在此更新中，Microsoft Edge 設定會有更詳細的說明，因此更容易了解。 

若要查看這些功能，請前往 [Microsoft Edge 瀏覽器裝置限制設定](device-restrictions-windows-10.md#microsoft-edge-browser)。

適用於：Windows 10 及更新版本

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>擴充完全受控的 Android Enterprise 裝置支援 (預覽)  <!--   3903241, 3903244, 3903246   -->
仍在公開預覽階段，我們已擴充完全受控的 Android Enterprise 裝置支援 ([2019 年 1 月首次宣告](whats-new.md#week-of-january-14-2019))，包括： 

- 在完全受控的專用裝置上，您可以建立[合規性政策](compliance-policy-create-android-for-work.md)來包含密碼規則和作業系統需求 ([裝置合規性]   > [原則]   > [建立原則]   > [Android Enterprise]  平台 > [裝置擁有者]  設定檔類型)。 

  在專用裝置上，裝置可能會顯示為 [不符合規範]  。 專用裝置上無法使用條件式存取。 請務必完成任何工作或動作，以確保專用裝置符合您所指派原則的規範。

- [條件式存取](conditional-access.md) - 適用於 Android 的條件式存取原則也會適用於完全受控的 Android Enterprise 裝置。 使用者現在可以使用 **Microsoft Intune 應用程式**，在 Azure Active Directory 中註冊其完全受控的裝置。 然後，查看並解決任何合規性問題以存取組織資源。

- 新增終端使用者應用程式 (Microsoft Intune 應用程式) - 新增適用於完全受控 Android 裝置的終端使用者應用程式，稱為 **Microsoft Intune**。 這是輕量型且現代化的全新應用程式，提供與公司入口網站應用程式類似的功能，但適用於完全受控的裝置。 如需詳細資訊，請參閱 [Google Play 上的 Microsoft Intune 應用程式](https://play.google.com/store/apps/details?id=com.microsoft.intune)。

若要設定完全受控的 Android 裝置，請前往 [裝置註冊]   > [Android 註冊]   > [公司擁有、完全受控的使用者裝置]  。 完全受控的 Android 裝置支援仍在預覽階段，某些 Intune 功能可能無法完全正常運作。  

若要深入了解此預覽，請參閱我們的部落格 [Microsoft Intune - Preview 2 for Android Enterprise Fully Managed devices](https://aka.ms/preview2_AE_fullymanaged) (Microsoft Intune - 完全受控的 Android Enterprise 裝置 Preview 2)。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>設定設定檔，以在設定助理期間略過一些畫面 <!-- 2276470  wnstaged-->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- 外觀
- 顯示色調
- iCloudStorage，如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。  使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。
如需詳細資訊，請參閱[使用裝置註冊計劃或 Apple School Manager 自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)。

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>註冊公司 iOS 裝置時的大量裝置命名<!--3566569  -->
使用 Apple 的其中一個公司註冊方法 (DEP/ABM/ASM) 時，您可以將裝置名稱格式設定為自動命名連入的 iOS 裝置。 您可以指定格式來包含範本中的裝置類型和序號。 若要執行這項操作，請選擇 [Intune]   > [裝置註冊]   > [Apple 註冊]   > [註冊計劃權杖]   > [選取權杖]   >[建立設定檔]   > [裝置命名格式]  。 您可以編輯現有的設定檔，但只有新同步的裝置會套用名稱。

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>更新註冊狀態頁面上的預設逾時訊息 <!-- 3959331 -->
我們已更新當註冊狀態頁面 (ESP) 超過 ESP 設定檔中指定的逾時值時，使用者所看到的預設逾時訊息。 此新的預設訊息會向使用者顯示，並協助他們了解要對其 ESP 部署採取的下一個動作。  

### <a name="device-management"></a>裝置管理

#### <a name="retire-noncompliant-devices-----1827291-----"></a>淘汰不符合規範的裝置  <!-- 1827291   -->
此功能已延後，即將在未來版本中推出。


### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Intune 資料倉儲 V1.0 變更反映回到搶鮮版 (Beta) <!-- 4403765 -->
當 V1.0 首次在 V1.0 1808 中引進時，它與搶鮮版 (Beta) API 明顯不同。 在 1903 中，這些變更將會反映回到搶鮮版 (Beta) API 版本。 如果您有使用搶鮮版 (Beta) API 版本的重要報表，強烈建議將這些報表切換到 V1.0 以避免中斷性變更。 如需詳細資訊，請參閱 [Intune 資料倉儲 API 的變更記錄檔](reports-changelog.md#1903-part-2)。

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>監視安全性基準狀態 (公開預覽) <!-- 3082047 --> 
安全性基準監視中已新增[每個類別的檢視](security-baselines-monitor.md#per-category-view) (安全性基準仍在預覽階段)。 每個類別的檢視會顯示基準中每個類別，以及落入該類別中每個狀態群組的裝置百分比。 您現在可以查看不符合每個類別、設定錯誤或不適用的裝置數目。

### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP 權杖的範圍標籤 <!--2371886  -->
您現在可以將範圍標籤新增至 Apple VPP 權杖。 只有獲派相同範圍標籤的使用者，才能存取具有該標籤的 Apple VPP 權杖。 使用該權杖購買的 VPP 應用程式和電子書會繼承其範圍標籤。 如需範圍標籤的詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。







## <a name="week-of-april-1-2019"></a>2019 年 4 月 1 日當週

### <a name="device-configuration"></a>裝置設定

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>更新憑證連接器  <!-- ICM 113304612 -->
[Intune 憑證連接器和是用於 Microsoft Intune 的 PFX 憑證連接器](certficates-pfx-configure.md#whats-new-for-connectors)均已發行更新。 新的版本會修正幾個已知問題。  

### <a name="app-management"></a>應用程式管理

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!-- 2536024 -->
適用於 iOS 裝置的公司入口網站應用程式首頁已經過重新設計。 透過這項變更，首頁將會改善採用 iOS UI 模式的能力，也會改善探索應用程式和電子書的能力。

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>適用於 iOS 12 裝置使用者的公司入口網站註冊變更 <!--3448635 -->  
iOS 版公司入口網站註冊畫面和步驟，為了配合 Apple iOS 12.2 中發行的 MDM 註冊變更已有所更新。 更新的工作流程會提示使用者：  

* 允許 Safari 先開啟公司入口網站並下載管理設定檔，再返回公司入口網站應用程式。  
* 開啟設定應用程式以在其裝置上安裝管理設定檔。
* 返回公司入口網站應用程式以完成註冊。  

如需更新的註冊步驟和畫面，請參閱 [Enroll iOS device in Intune](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios) (在 Intune 中註冊 iOS 裝置)。  

## <a name="week-of-march-25-2019"></a>2019 年 3 月 25 日當週

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Microsoft Intune 中的 [資料倉儲] 刀鋒視窗提供對 Power BI 合規性應用程式的支援 <!-- 4260871 -->
之前，[Intune 資料倉儲]  刀鋒視窗中的 [下載 Power BI 檔案]  連結會下載 Intune 資料倉儲報表 (.pbix 檔案)。 此報表已取代為 Power BI 合規性應用程式。 Power BI 合規性應用程式不需要特殊載入或設定。 它會直接在 Power BI Online 入口網站中開啟，並根據您的認證顯示 Intune 租用戶特定資料。 在 Intune 中，選取 [Intune] 刀鋒視窗右側的 [設定 Intune 資料倉儲]  連結。 然後，按一下 [取得 Power BI 應用程式]  。 如需詳細資訊，請參閱[使用 Power BI 連線至資料倉儲](reports-proc-get-a-link-powerbi.md)。

## <a name="week-of-march-18-2019"></a>2019 年 3 月 18 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>部署 Microsoft Visio 和 Microsoft Project <!-- 3725386  -->
如果您擁有 Microsoft Visio Pro for Office 365 和 Microsoft Project Online Desktop Client 的授權，您現在可以使用 Microsoft Intune 將這些應用程式當作獨立應用程式部署到 Windows 10 裝置。 從 Intune，選取 [用戶端應用程式]   > [應用程式]   > [新增]  以顯示 [新增應用程式]  刀鋒視窗。 在 [新增應用程式]  刀鋒視窗中，選取 [Windows 10]  作為 [應用程式類型]  。 然後，選取 [設定應用程式套件]  以選取要安裝的應用程式。 如需適用於 Windows 10 裝置的 Office 365 應用程式詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](apps-add-office365.md)。

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 產品名稱變更 <!-- 3593653  -->
**Microsoft Visio Pro for Office 365** 現在稱為 **Microsoft Visio Online 方案 2**。  如需 Microsoft Visio 的詳細資訊，請參閱 [Visio Online 方案 2](https://products.office.com/visio/visio-online-plan-2)。 如需適用於 Windows 10 裝置的 Office 365 應用程式詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](apps-add-office365.md)。

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune 應用程式防護原則 (APP) 字元限制設定 <!-- 3291302  -->
Intune 管理員可以指定 Intune 應用程式 [限制使用其他應用程式剪下、複製及貼上]  原則設定的例外狀況。  身為管理員，您可以指定能從受控應用程式剪下或複製的字元數。 此設定可允許共用指定的字元數給任何應用程式，而不管 [限制使用其他應用程式剪下、複製及貼上] 設定。 請注意，Android 版 Intune 公司入口網站應用程式版本必須是 5.0.4364.0 版或更新版本。 如需詳細資訊，請參閱 [iOS 資料保護](app-protection-policy-settings-ios.md#data-protection)、[Android 資料保護](app-protection-policy-settings-android.md#data-protection)和[檢閱用戶端應用程式防護記錄](app-protection-policy-settings-log.md#app-protection-policy-settings)。

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>適用於 Office 專業增強版部署的 Office 部署工具 (ODT) XML <!-- 3192477   -->
在 Intune 管理主控台中建立 Office 專業增強版的執行個體時，您將能夠提供 Office 部署工具 (ODT) XML。 如果現有 Intune UI 選項不符合您的需求，這可提高自訂能力。 如需詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](https://docs.microsoft.com/intune/apps-add-office365)和 [Office 部署工具的設定選項](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)。

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>現在會以自動產生的背景來顯示應用程式圖示 <!-- 1429026  -->
在 Windows 公司入口網站應用程式中，現在會根據應用程式圖示主要色彩 (如果可偵測) 以自動產生的背景來顯示圖示。 適用時，此背景會取代先前在應用程式磚上顯示的灰色框線。 使用者會在公司入口網站 10.3.3451.0 以後版本中看到這項變更。

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>在 Windows 大量註冊之後使用公司入口網站應用程式安裝可用的應用程式 <!-- 2751523   -->
使用 [Windows 大量註冊](windows-bulk-enroll.md) (佈建套件) 註冊到 Intune 中的 Windows 裝置，將能夠使用公司入口網站應用程式來安裝可用的應用程式。 如需公司入口網站應用程式的詳細資訊，請參閱[手動新增 Windows 10 公司入口網站](store-apps-company-portal-app.md)和[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。

> [!Note]
> 這項功能尚未完全部署給所有客戶。 如果您無法在大量註冊的裝置上使用公司入口網站，您可能必須等到這項變更推出到您的帳戶。

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams 應用程式可作為 Office 應用程式套件的一部分選取 <!-- 3828932  -->
Microsoft Teams 應用程式可加入作為 Office 專業增強版應用程式套件安裝的一部分或從中排除。 這項功能適用於 Office 專業增強版組建編號 16.0.11328.20116+。 使用者必須登出裝置後再重新登入，才能完成安裝。 在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 選取其中一個 [Office 365 套件]  應用程式類型，然後選取 [設定應用程式套件]  。

### <a name="device-configuration"></a>裝置設定

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>在 Windows 10 及更新版本裝置上以 kiosk 模式執行多個應用程式時自動啟動應用程式 <!-- 2351390 -->

在 Windows 10 及更新版本裝置上，您可在 kiosk 模式下執行裝置，並執行多個應用程式。 在此更新中，有一項 [自動啟動]  設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [Kiosk]  設定檔類型 > [多應用程式 Kiosk]  )。 使用此設定在使用者登入裝置時自動啟動應用程式。

若要查看所有 kiosk 設定的清單和描述，請參閱[在 Intune 中讓 Windows 10 及更新版本裝置設定以 kiosk 形式執行](kiosk-settings-windows.md)。

適用於：Windows 10 及更新版本

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>作業記錄也會顯示不符合規範裝置的相關詳細資料 <!-- 4063755  -->
將 Intune 記錄路由傳送到 Azure 監視器功能時，您也可以路由傳送作業記錄。 在此更新中，作業記錄也會提供不符合規範裝置的相關資訊。 

如需此功能的詳細資訊，請參閱[在 Intune 中將記錄資料傳送至儲存體、事件中樞或記錄分析](review-logs-using-azure-monitor.md)。

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>將記錄路由傳送到 Azure 監視器的更多 Intune 工作負載 <!-- 3804627 -->
在 Intune 中，您可以將稽核與作業記錄路由傳送到 Azure 監視器的事件中樞、儲存體和記錄分析 ([Intune]   > [監視]   > [診斷設定]  )。 在此更新中，您可以將這些記錄路由傳送到更多 Intune 工作負載，包括合規性、設定、用戶端應用程式等。 

若要深入了解如何將記錄路由傳送到 Azure 監視器，請參閱[將記錄資料傳送至儲存體、事件中樞或記錄分析](review-logs-using-azure-monitor.md)。

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>在 Intune 中建立和使用適用於 Android Zebra 裝置的行動延伸模組 <!-- 3305880   -->
在此更新中，Intune 支援設定 Android Zebra 裝置。 具體來說，您可以建立裝置組態設定檔，並使用 StageNow 產生的行動延伸模組 (MX) 設定檔將設定套用到 Android Zebra 裝置 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android]  平台 > [MX 設定檔 (僅限 Zebra)]  設定檔類型)。

如需此功能的詳細資訊，請參閱[在 Intune 中透過行動延伸模組使用和管理 Zebra 裝置](android-zebra-mx-overview.md)。

適用於：Android

### <a name="device-management"></a>裝置管理

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 裝置的加密報表 (公開預覽)<!-- 2351538 -->  
使用新[加密報表 (預覽)](encryption-monitor.md) 來檢視 Windows 10 裝置加密狀態的相關詳細資料。 可用的詳細資料包含裝置 TPM 版本、加密整備和狀態、錯誤報告等。  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>從 Intune 入口網站存取 BitLocker 修復金鑰 (公開預覽) <!-- 2351547   -->  
您現在可以使用 Intune 來檢視 Azure Active Directory 中 BitLocker 金鑰識別碼和 BitLocker 修復金鑰的相關[詳細資料](encryption-monitor.md)。

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>對 iOS 和 Android 裝置上 Intune 案例的 Microsoft Edge 支援 <!-- 3411007 -->
Microsoft Edge 將支援與 Intune Managed Browser 相同的所有管理案例，並將在終端使用者體驗中新增增強功能。 Microsoft Edge 企業功能是由 Intune 原則啟用，其中包含雙重身分識別、應用程式防護原則整合、Azure 應用程式 Proxy 整合，以及受控的我的最愛和首頁捷徑。 如需詳細資訊，請參閱 [Microsoft Edge 支援](app-configuration-managed-browser.md#microsoft-edge-support)。

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune 連接器淘汰僅限 EAS 裝置的支援 <!--3105122  -->
Intune 主控台不再支援檢視和管理使用 Intune 連接器連線到 Exchange Online 的僅限 EAS 裝置。 相反地，您有下列選項：
- 在行動裝置管理 (MDM) 中註冊裝置
- 使用 Intune 應用程式防護原則來管理裝置
- 如 [Clients and mobile in Exchange Online](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online) (Exchange Online 中的用戶端和行動裝置) 中所述使用 Exchange 控制項

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>使用 [名稱] 搜尋確切裝置的所有裝置頁面 <!--4254930 -->
您現在可以搜尋確切裝置名稱。 移至 [Intune]   > [裝置]   > [所有裝置]  > 在搜尋方塊中，以 {} 括住裝置名稱來搜尋入完全相符的項目。 例如， **{Device12345}** 。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>租用戶狀態頁面上的其他連接器支援 <!-- 3617202  -->
[[租用戶狀態] 頁面](tenant-status.md) 現在會顯示其他連接器的狀態資訊，包括 *Windows Defender 進階威脅防護* (ATP) 及其他 Mobile Threat Defense 連接器。

### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Intune 唯讀權限將授與某些 Azure Active Directory 角色 <!-- 3637917  -->
Intune 唯讀權限已授與下列 Azure Active Directory 角色。 透過 Azure AD 角色授與的權限會取代透過 Intune 角色型存取控制 (RBAC) 授與的權限。

Intune 稽核資料的唯讀權限：

- 合規性管理員
- 合規性資料管理員

所有 Intune 資料的唯讀權限：

- 安全性系統管理員
- 安全性操作員
- 安全性讀取者

如需詳細資訊，請參閱[角色型存取控制](role-based-access-control.md)。

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>iOS 應用程式佈建設定檔的範圍標籤 <!--2934430   -->
您可以將範圍標籤新增至 iOS 應用程式佈建設定檔，僅限具有角色並同時獲派該範圍標籤的人員才能存取 iOS 應用程式佈建設定檔。 如需詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>應用程式設定原則的範圍標籤 <!--2371891   -->
您可以將範圍標籤新增至應用程式設定原則，僅限具有角色並同時獲派該範圍標籤的人員才能存取應用程式設定原則。 應用程式設定原則只能指定給或關聯到獲派相同範圍標籤的應用程式。 如需詳細資訊，請參閱[使用 RBAC 和範圍標籤](scope-tags.md)。

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>對 iOS 和 Android 裝置上 Intune 案例的 Microsoft Edge 支援 <!-- 3411007 -->
Microsoft Edge 將支援與 Intune Managed Browser 相同的所有管理案例，並將在終端使用者體驗中新增增強功能。 Microsoft Edge 企業功能是由 Intune 原則啟用，其中包含雙重身分識別、應用程式防護原則整合、Azure 應用程式 Proxy 整合，以及受控的我的最愛和首頁捷徑。 如需詳細資訊，請參閱 [Microsoft Edge 支援](app-configuration-managed-browser.md#microsoft-edge-support)。

## <a name="week-of-february-25-2019"></a>2019 年 2 月 25 日當週

### <a name="device-configuration"></a>裝置設定

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell 模組 <!-- 951068  -->
Intune PowerShell 模組透過 Microsoft Graph 支援 Intune API，現在於 [Microsoft PowerShell 資源庫](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)中提供使用。

- [如何使用此模組的相關詳細資料](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [使用此模組的案例範例](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>改善傳遞最佳化的支援  <!--3183757  -->
我們已在 Intune 中擴充設定傳遞最佳化的支援。 您現在可以直接從 Intune 主控台設定[傳遞最佳化設定](delivery-optimization-settings.md)的擴充清單，並將它指定給您的裝置。


## <a name="week-of-february-18-2019"></a>2019 年 2 月 18 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune 會在 Android 裝置上利用 Google Play Protect API <!-- 2577355   -->
某些 IT 系統管理員面臨到在 BYOD 的情況下，終端使用者的行動電話最後可能會遭到 Root 或 JB 破解。 這項行為雖然有時並非惡意，但還是會導致為了保護終端使用者裝置上組織資料所設定的許多 Intune 原則遭到略過。 因此，Intune 會針對已註冊和取消註冊的裝置提供 Root 和 JB 破解偵測。 在此版本中，Intune 現在會利用 Google Play Protect API，在我們現有的 Root 破解偵測檢查中新增對已取消註冊裝置的檢查。 雖然 Google 不會共用所發生 Root 破解偵測檢查的全部內容，但我們預期這些 API 會偵測到其裝置基於任何原因而遭到 Root 破解的使用者，這些原因從裝置自訂到能夠在舊版裝置上取得新版 OS 更新。 接著可防止這些使用者存取公司資料，或從其啟用原則的應用程式抹除其公司帳戶。 為了提高價值，IT 系統管理員現在於 [Intune 應用程式防護] 刀鋒視窗中有數項報告更新：「標有旗標的使用者」報告將會顯示透過 Google Play Protect 的 SafetyNet API 掃描偵測到哪些使用者，而「潛在有害的應用程式」報告將會顯示透過 Google 的 Verify Apps API 掃描偵測到哪些應用程式。 這項功能適用於 Android。

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>[疑難排解] 刀鋒視窗提供 Win32 應用程式資訊 <!-- 2617342   -->
您現在可以從 Intune 應用程式 [疑難排解]  刀鋒視窗收集 Win32 應用程式安裝的失敗記錄檔。 如需應用程式安裝疑難排解的詳細資訊，請參閱[針對應用程式安裝問題進行疑難排解](troubleshoot-app-install.md)和[針對 Win32 應用程式問題進行疑難排解](apps-win32-app-management.md#troubleshoot-win32-app-issues)。

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>iOS 應用程式的應用程式狀態詳細資料 <!-- 3761235   -->
新增下列應用程式安裝錯誤訊息：
- 在共用的 iPad 上安裝 VPP 應用程式時失敗
- 停用 App Store 時失敗
- 找不到應用程式的 VPP 授權
- 無法使用 MDM 提供者來安裝系統應用程式
- 裝置處於遺失模式或 kiosk 模式時，無法安裝應用程式
- 使用者未登入 App Store 時，無法安裝應用程式

在 Intune 中，選取 [用戶端應用程式]   > [應用程式]  >「應用程式名稱」> [裝置安裝狀態]  。 [狀態詳細資料]  欄將會提供新的錯誤訊息。

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>在 Windows 10 版公司入口網站應用程式中新增 [應用程式類別] 畫面<!-- 3834780  -->
新增了稱為 [應用程式類別]  的畫面，以改善 Windows 10 版公司入口網站中的應用程式瀏覽和選取體驗。 使用者現在會看到其應用程式依類別排序，例如 [精選]  、[教育]  和 [生產力]  。 這項變更會出現在公司入口網站 10.3.3451.0 版和更新版本。 若要檢視新的畫面，請參閱[應用程式 UI 中的新功能](https://docs.microsoft.com/intune/whats-new-app-ui)。 如需公司入口網站中應用程式的詳細資訊，請參閱[在裝置上安裝和共用應用程式](/intune-user-help/install-apps-cpapp-windows)。  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI 合規性應用程式 <!-- 1455231 doc-work-item -->
在 Power BI Online 中使用 [Intune 合規性 (資料倉儲)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 應用程式，來存取您的 Intune 資料倉儲。 透過此 Power BI 應用程式中，您現在不需要任何設定也不需要離開網頁瀏覽器即可存取和共用預先建立的報表。 如需其他資訊，請參閱[變更記錄檔 - Power BI 合規性應用程式](reports-changelog.md#power-bi-compliance-app)。


### <a name="device-configuration"></a>裝置設定

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell 指令碼可在 64 位元裝置上以 64 位元主機執行 <!-- 1862675   -->
當您將 PowerShell 指令碼新增至裝置組態設定檔時，指令碼一律會以 32 位元執行，即使在 64 位元作業系統上也一樣。 在此更新中，系統管理員可以在 64 位元裝置上以 64 位元 PowerShell 主機執行指令碼 ([裝置設定]   > [PowerShell 指令碼]   > [新增]   > [設定]   > [Run script in 64 bit PowerShell Host] \(以 64 位元 PowerShell 主機執行指令碼\)  )。

如需使用 PowerShell 的詳細資料，請參閱 [Intune 中的 PowerShell 指令碼](intune-management-extension.md)。

適用於：Windows 10 及更新版本

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS 使用者會收到更新其密碼的提示 <!-- 1873216 -->
Intune 將在 macOS 裝置上強制執行 **ChangeAtNextAuth** 設定。 此設定會影響具有合規性密碼原則或裝置限制密碼設定檔的終端使用者和裝置。 終端使用者會收到一次更新其密碼的提示。 每當使用者第一次執行需要驗證的工作時 (例如登入裝置)就會發生此提示。 當使用者執行任何需要系統管理權限的工作時 (例如要求 keychain 存取權)，也會收到更新其密碼的提示。 

系統管理員所做的任何新的或現有密碼原則變更，都會再次提示終端使用者更新其密碼。

適用於：  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>將 SCEP 憑證指派給無使用者的 macOS 裝置  <!-- 2340521  -->
您可以使用裝置屬性將簡單憑證註冊通訊協定 (SCEP) 憑證指派給 macOS 裝置 (包括不具使用者親和性的裝置)，並建立憑證設定檔與 Wi-Fi 或 VPN 設定檔的關聯。 這會擴充我們已有的支援，以便[將 SCEP 憑證指派給具有和不具使用者親和性的裝置](certificates-scep-configure.md#create-a-scep-certificate-profile) (執行 Windows、iOS 和 Android)。  此更新會新增選項，可在您設定 macOS 的 SCEP 憑證設定檔時，選取 [裝置]  憑證類型。

適用於： 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune 條件式存取 UI 更新   <!-- 2432313   -->
我們已改善 Intune 主控台中的條件式存取 UI。 這些地方包括：
-  以 Azure Active Directory 中的刀鋒視窗取代 Intune [條件式存取]  刀鋒視窗。 這會確保您可以從 Intune 主控台存取[條件式存取](conditional-access.md) (仍是 Azure AD 技術) 的完整設定和組態。 
- 我們已將 [內部部署存取]  刀鋒視窗重新命名為 [Exchange 存取]  ，並將 [Exchange 服務連接器]  設定重新放置到此重新命名的刀鋒視窗。  這項變更會整合您[設定和監視 Exchange Online 和內部部署相關詳細資料](exchange-connector-install.md)的位置。  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>Kiosk 瀏覽器和 Microsoft Edge 瀏覽器應用程式可在 Windows 10 裝置上以 kiosk 模式執行 <!-- 2935135   -->
您可以使用 kiosk 模式的 Windows 10 裝置來執行一或多個應用程式。 此更新包含在 kiosk 模式中使用瀏覽器應用程式的數項變更，包括：

- 新增 Microsoft Edge 瀏覽器或 Kiosk 瀏覽器以作為 kiosk 裝置上的應用程式執行 ([裝置設定]   > [設定檔]   > [新增設定檔]   > [Windows 10 及更新版本]  平台 > [Kiosk]  設定檔類型)。
- 可允許或限制的新功能和設定 ([裝置設定]   > [設定檔]   > [新增設定檔]   > [Windows 10 及更新版本]  平台 > [裝置限制]  設定檔類型)，包括：

  - Microsoft Edge 瀏覽器：
  - 使用 Microsoft Edge kiosk 模式
  - 在閒置時間後重新整理瀏覽器

 - 我的最愛和搜尋：
  - 允許變更搜尋引擎

如需這些設定的清單，請參閱：

- [讓 Windows 10 和更新版本的裝置設定以 kiosk 形式執行](kiosk-settings-windows.md)
- [Microsoft Edge 瀏覽器裝置限制](device-restrictions-windows-10.md#microsoft-edge-browser)
- [我的最愛和搜尋裝置限制](device-restrictions-windows-10.md##favorites-and-search)

適用於：Windows 10 及更新版本

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>iOS 和 macOS 裝置的新裝置限制設定 <!-- 3448774   -->
您可以在執行 iOS 和 macOS 的裝置上限制一些設定和功能 ([裝置設定]   > [設定檔]   > [新增設定檔]   > [iOS]  或 [macOS]  平台 > [裝置限制]  設定檔類型)。 此更新會新增您可以控制的更多功能和設定，包括在 macOS 裝置上設定螢幕使用時間，變更 eSIM 設定和行動數據方案等。 此外，您也可在 macOS 裝置上對使用者延遲顯示軟體更新，以及封鎖內容快取。 

若要查看您可以限制的功能和設定，請參閱：

- [iOS 裝置限制設定](device-restrictions-ios.md)
- [macOS 裝置限制設定](device-restrictions-macos.md)

適用於：

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>"Kiosk" 裝置現在稱為 Android Enterprise 裝置的「專用裝置」 <!-- 3598402   -->
為了配合 Android 術語，**kiosk** 已變更為 Android Enterprise 裝置的**專用裝置** ([裝置設定]   > [設定檔]   > [建立設定檔]  > [Android Enterprise] 平台 > [僅限裝置擁有者]   > [裝置限制]   > [專用裝置]  )。

若要查看可用的設定，請前往[允許或限制功能的裝置設定](device-restrictions-android-for-work.md#dedicated-device-settings)。

適用於：  
Android 企業

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari 及對使用者延遲顯示軟體更新等 iOS 設定將會移至 Intune UI <!-- 3640850, 3803313   -->
針對 iOS 裝置，您可以進行 Safari 設定及設定軟體更新。 在此更新中，這些設定將會移至 Intune UI 的不同部分：

- Safari 設定已從 [Safari]  ([裝置設定]   > [設定檔]   > [新增設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型) 移至 [[內建應用程式]](device-restrictions-ios.md#built-in-apps)  。
- [Delaying user software update visibility for supervised iOS devices] \(對使用者延遲顯示受監督 iOS 裝置的軟體更新\)  設定 ([軟體更新]   > [更新 iOS 的原則]  ) 將會移至 [裝置限制]   > [[一般]](device-restrictions-ios.md#general)  。  如需現有原則影響的詳細資訊，請參閱 [iOS 軟體更新](software-updates-ios.md#configure-the-policy)。 

如需這些設定的清單，請參閱：

- [iOS 裝置限制](device-restrictions-ios.md) 
- [iOS 軟體更新](software-updates-ios.md)

本功能適用於： 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>在 iOS 裝置上，[啟用裝置設定的限制] 已重新命名為 [螢幕使用時間] <!-- 3699164   -->
您可以在受監督的 iOS 裝置上設定 [啟用裝置設定的限制]  ([裝置設定]   > [設定檔]   > [新增設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型 > [一般]  )。 在此更新中，此設定已重新命名為 [螢幕使用時間 (僅限受監督)]  。 

其行為完全一樣。 明確說來： 

- iOS 11.4.1 和更早版本：[封鎖]  可防止終端使用者在裝置設定中設定自己的限制。 
- iOS 12.0 和更新版本：[封鎖]  可防止終端使用者在裝置設定中設定自己的 [螢幕使用時間]  ，包括內容與隱私權限制。 升級為 iOS 12.0 的裝置不會再於裝置設定中看到 [限制] 索引標籤。 這些設定位於 [螢幕使用時間]  中。 

如需這些設定的清單，請參閱 [iOS 裝置限制](device-restrictions-ios.md#general)。

適用於： 
- iOS


### <a name="device-management"></a>裝置管理

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>重新命名已註冊的 Windows 裝置 <!-- 1911112  -->
您現在可以重新命名已註冊的 Windows 10 裝置 (RS4 或更新版本)。 若要這樣做，請選擇 [Intune]   > [裝置]   > [所有裝置]  > 選擇裝置 > [重新命名裝置]  。 此功能目前不支援重新命名混合式 Azure AD Windows 裝置。

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>自動將範圍標籤指派給管理員所建立並具有該範圍的資源 <!-- 3173823  -->
當系統管理員建立資源時，任何指派給系統管理員的範圍標籤都會自動指派給這些新資源。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>失敗的註冊報表會移至 [裝置註冊] 刀鋒視窗 <!-- 3560202  -->
**註冊失敗**報表已移至 [裝置註冊]  刀鋒視窗的 [監視]  區段。 已新增兩欄 ([註冊方法] 和 [OS 版本])。

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>公司入口網站放棄報表已重新命名為 [未完成的使用者註冊] <!--3815076 eemiss -->
**公司入口網站放棄**報表已重新命名為 [未完成的使用者註冊]  。


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019 年 2 月 4 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune macOS 公司入口網站深色模式 <!-- 3300524  -->
Intune macOS 公司入口網站現在支援 macOS 的深色模式。 當您在 macOS 10.14+ 裝置上啟用 [深色模式] 時，公司入口網站會將其外觀調整為反映該模式的色彩。

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019 年 1 月 21 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 應用程式的快顯通知 <!-- 3136566   -->
您可以隱藏而不顯示每個應用程式指派的終端使用者快顯通知。 從 Intune 選取 [用戶端應用程式]   > [應用程式]  > 選取應用程式 > [指派]   > [包含群組]  。 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 應用程式防護原則 UI 更新 <!-- 3251427  -->
我們已變更 Intune 應用程式保護的設定和按鈕標籤，以使它們更容易理解。 部分變更包括：  
- 控制項從 [是]   / [否]  的控制項，變更成主要為 [封鎖]   / [允許]  ，以及 [停用]   / [啟用]  的控制項。 標籤也一併更新。  
- 設定已重新格式化，因此設定和其標籤會在控制項中並排顯示，提供更好的瀏覽。   

預設設定和設定數量會保持相同，但這項變更可讓使用者更輕鬆了解、瀏覽和利用這些設定，以套用所選的應用程式保護原則。 如需詳細資訊，請參閱 [iOS 設定](app-protection-policy-settings-ios.md)和 [Android 設定](app-protection-policy-settings-android.md)。

### <a name="additional-settings-for-outlook----3301182----"></a>Outlook 的其他設定 <!-- 3301182  -->
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
> 如果您使用 Intune 應用程式防護原則來管理公司身分識別的存取權，您應該考慮不啟用 [require biometrics] \(需要生物識別技術\)  。 如需詳細資訊，請參閱 [iOS 存取設定](app-protection-policy-settings-ios.md#access-requirements)和 [Android 存取設定](app-protection-policy-settings-android.md#access-requirements)中的＜需要公司認證才能存取＞  。

如需詳細資訊，請參閱 [Microsoft Outlook 組態設定](app-configuration-policies-outlook.md)。

#### <a name="delete-android-enterprise-apps----1352553---"></a>刪除 Android Enterprise 應用程式 <!-- 1352553 -->
您可以從 Microsoft Intune 刪除受控的 Google Play 應用程式。 若要刪除受控的 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [用戶端應用程式]   > [應用程式]  。 從應用程式清單，選取受控的 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]  。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

#### <a name="managed-google-play-app-type----1352580---"></a>受控的 Google Play 應用程式類型 <!-- 1352580 -->
[受控的 Google Play]  應用程式類型可讓您將[受控 Google Play 應用程式](https://play.google.com/work/search?q=microsoft&c=apps)明確新增至 Intune。 身為 Intune 系統管理員，您現在可以在 Intune 中瀏覽、搜尋、核准、同步及指派已核准之受控的 Google Play 應用程式。  您不再需要另外瀏覽至受控的 Google Play 主控台，而且您不再需要重新驗證。  在 Intune 中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [應用程式類型]  清單中，選取 [受控的 Google Play]  作為應用程式類型。

### <a name="default-android-pin-keyboard----3802457---"></a>預設 Android PIN 鍵盤 <!-- 3802457 -->
若終端使用者已在其 Android 裝置上設定 Intune 應用程式防護原則 (APP) PIN 且 PIN 類型為 [數值]，則現在會看到預設 Android 鍵盤，而不是先前所設計的固定 Android 鍵盤 UI。 這是為了在 Android 和 iOS 上使用預設鍵盤時能夠保持一致所做的變更，適用於 PIN 類型為 [數值] 及/或 [密碼]。 如需 Android 上終端使用者存取設定的詳細資訊，請參閱 [Android 存取需求](app-protection-policy-settings-android.md#access-requirements)。

### <a name="device-configuration"></a>裝置設定

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>使用針對安全性基準的 Microsoft 建議設定 (公開預覽) <!-- 2055484   -->

Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員可以直接從這些基準建立安全性政策，並將它們部署到其使用者。 您也可以自訂最佳做法建議項目，以符合您組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

這項功能處於公開預覽狀態，因此現在建立之任何設定檔都不會移至正式運作 (GA) 的安全性基準範本。 您不應該在生產環境中規劃使用這些預覽範本。

若要深入了解安全性基準，請參閱[在 Intune 中建立 Windows 10 安全性基準](security-baselines-monitor.md)。

本功能適用於：Windows 10 及更新版本

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>非系統管理員可在已加入 Azure AD 的 Windows 10 裝置上啟用 BitLocker<!-- 2147379   -->
當您在 Windows 10 裝置上啟用 BitLocker 設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選擇 [Windows 10 及更新版本]  > 針對設定檔類型選擇 [Endpoint Protection]  > [Windows 加密]  ) 時，您會新增 BitLocker 設定。 

此更新包含新的 BitLocker 設定，可允許標準使用者 (非系統管理員) 啟用加密。 

若要查看設定，請前往[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>檢查 Configuration Manager 合規性 <!-- 2192052  eepublished  -->
此更新會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性]   > [原則]   > [建立原則]   > [Windows 10 及更新版本]   > [Configuration Manager 合規性]  )。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用此設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中就不會符合規範。

[Configuration Manager 合規性](compliance-policy-create-windows.md#configuration-manager-compliance)描述了這項設定。

適用於：Windows 10 及更新版本

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>使用裝置組態設定檔自訂受監督 iOS 裝置上的背景圖案 <!-- 2809324   -->
當您建立 iOS 裝置的裝置組態設定檔時，您可以自訂某些功能 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [裝置功能]  設定檔類型)。 此更新包括新的**桌布**設定，可讓系統管理員在主畫面或鎖定畫面上使用 .png、.jpg 或 .jpeg 影像。 這些桌布設定只會套用至受監督的裝置。 

如需這些設定的清單，請參閱 [iOS 裝置功能設定](ios-device-features-settings.md)。

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 kiosk 已正式運作 <!-- 3594661  -->
在此更新中，在 Windows 10 和更新版本的裝置上的 [Kiosk] 功能是正式推出 (GA)。 若要查看您可以新增和設定的所有設定，請參閱[適用於 Windows 10 (和更新版本) 的 Kiosk 設定](kiosk-settings.md)。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>[透過藍牙分享連絡人] 已從 Android Enterprise 的 [裝置限制] > [裝置擁有者] 中移除 <!-- 3598396   -->
當您建立 Android Enterprise 裝置的裝置限制設定檔時，有一項 [透過藍牙分享連絡人]  設定。 在此更新中，[透過藍牙分享連絡人]  設定會被移除 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Android 企業]  平台 > [裝置限制] > [裝置擁有者]  設定檔類型 > [一般]  )。 

Android Enterprise 裝置擁有者管理不支援 [透過藍牙分享連絡人]  設定。 因此，移除此設定之後，並不會影響任何裝置或租用戶，即使您已在環境中啟用和設定此設定亦然。

若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。

適用於：Android Enterprise 裝置擁有者

### <a name="device-management"></a>裝置管理

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>WIP (不含註冊) 裝置的選擇性抹除支援 <!-- 1434452 -->
Windows 資訊保護 (不含註冊) (WIP-WE) 允許客戶保護其 Windows 10 裝置上的公司資料，而不需要完整的 MDM 註冊。 一旦文件受 WIP-WE 原則保護，受保護的資料就可以由 Intune 系統管理員選擇性抹除。 透過選取使用者與裝置並傳送抹除要求，透過 WIP-WE 原則保護的所有資料都會變成無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式]   > [應用程式選擇性抹除]  。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>新的作業記錄，以及將記錄傳送至 Azure 監視器服務的能力 <!-- 3762211  -->
Intune 具有內建稽核記錄，可在進行變更時追蹤事件。 此更新包含新的記錄功能，包括： 
- 作業記錄 (預覽)，顯示已註冊的使用者和裝置的詳細資料，包括成功和失敗的嘗試。
- 稽核記錄和作業記錄也可傳送到 Azure 監視器，包括儲存體帳戶、事件中樞和 Log Analytics。 這些服務可讓您儲存、使用 Splunk 和 QRadar 等分析，並取得記錄資料的視覺效果。

[將記錄資料傳送至 Intune 中的儲存體、事件中樞或記錄分析](review-logs-using-azure-monitor.md)提供這項功能的詳細資訊。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>在 iOS DEP 裝置上略過更多設定助理畫面 <!-- 2687509  -->
除了您目前可以略過的畫面之外，當使用者註冊裝置時，您還可以將 iOS DEP 裝置設定為略過 [設定助理] 中的下列畫面：顯示色調、隱私權、Android 移轉、首頁按鈕、iMessage 和 FaceTime、上架、Watch 移轉、外觀、螢幕使用時間、軟體更新、SIM 卡設定。
若要選擇要略過的畫面，請前往 [裝置註冊]   > [Apple 註冊]   > [註冊方案權杖]  > 選擇權杖 > [設定檔]  > 選擇設定檔 > [屬性]   > [設定助理自訂]  > 針對任何您想要略過的畫面選擇 [隱藏]  > [確定]  。
如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。 使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android Enterprise APP-WE 應用程式部署 <!-- 1171203 -->
針對未註冊之無註冊應用程式防護原則 (APP-WE) 部署案例中的 Android 裝置，您現在可以使用受控的 Google Play，將市集應用程式和 LOB 應用程式部署給使用者。 具體來說，您可以為終端使用者提供應用程式目錄和安裝體驗，藉由允許從不明來源進行安裝，就不再需要終端使用者放寬其裝置的安全性狀態。 此外，此部署案例將提供已改善的使用者體驗。

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019 年 1 月 14 日當週

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>公司擁有且完全受控的 Android 裝置支援預覽 <!-- 1574342  -->
Intune 現在支援完全受控的 Android 裝置，此為公司擁有的「裝置擁有者」案例，其中的裝置會受到 IT 嚴格管理並隸屬於個別使用者。 這讓系統管理員能夠管理整個裝置、強制設定無法用於工作設定檔之原則控制項的延伸範圍，並限制使用者只能從受控的 Google Play 安裝應用程式。 如需詳細資訊，請參閱[設定 Android 完全受控裝置的 Intune 註冊](android-fully-managed-enroll.md)與[註冊您的專用裝置或完全受控裝置](android-dedicated-devices-fully-managed-enroll.md)。  請注意，此功能處於預覽狀態。 完全受控的 Android 使用者裝置目前不提供某些 Intune 功能，例如憑證、合規性和條件式存取。

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019 年 1 月 7 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="intune-app-pin----2298397---"></a>Intune 應用程式 PIN <!-- 2298397 -->
身為 IT 系統管理員，您現在能設定終端使用者可在其 Intune 應用程式 PIN 必須變更之前等候的天數。 這項新設定稱為 [PIN reset after number of days] \(在數天後重設 PIN\)  ，並可在 Azure 入口網站中，藉由選取 [Intune]   > [用戶端應用程式]   > [應用程式防護原則]   > [建立原則]   > [設定]   > [存取需求]  來使用。 這項功能適用於 [iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md) 裝置，並支援正整數值。


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 裝置報告欄位 <!-- 2748738 -->
Intune 提供其他裝置報告欄位，包括應用程式註冊識別碼、Android 製造商、型號和安全性修補程式版本，以及 iOS 型號。 在 Intune 中，您可以藉由選取 [用戶端應用程式]   > [應用程式防護狀態]  ，然後選擇 [應用程式防護報表：iOS、Android]  來使用這些欄位。 此外，這些參數將協助您設定適用於裝置製造商 (Android) 的 [允許]  清單、適用於裝置型號 (Android 和 iOS) 的 [允許]  清單，以及最低的 Android 安全性修補程式版本設定。 


### <a name="device-configuration"></a>裝置設定

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>系統管理範本目前處於公開預覽狀態且已移至它們自己的組態設定檔 <!-- 3322847 -->

Intune 中的系統管理範本 ([裝置設定]   > [系統管理範本]  ) 目前為公開預覽狀態。 使用此更新：

- 系統管理範本包含約 300 個可在 Intune 中管理的設定。 這些設定先前只存在於群組原則編輯器中。
- 系統管理範本會在公開預覽版中提供。
- 系統管理範本正從 [裝置設定]   > [系統管理範本]  移至 [裝置設定]   > [設定檔]   > [建立設定檔]  > 在 [平台]  中選擇 [Windows 10 及更新版本]  > 在 [設定檔類型]  中選擇 [系統管理範本]  。
- 報告功能已啟用

若要深入了解這項功能，請前往[設定群組原則設定的 Windows 10 範本](administrative-templates-windows.md)。

適用於：Windows 10 及更新版本

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>使用 S/MIME 加密和簽署使用者的多部裝置  <!-- 1333642 -->
此更新包括使用新匯入之憑證設定檔的 S/MIME 電子郵件加密 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 選取平台 > [PKCS imported certificate] \(PKCS 匯入的憑證\)  設定檔類型)。 在 Intune 中，您可以匯入 PFX 格式的憑證。 Intune 接著可以將這些相同的憑證提供給單一使用者所註冊的多個裝置。 這也包括：
- 原生 iOS 電子郵件設定檔支援啟用 PFX 格式之已匯入憑證的 S/MIME 加密。
- Windows Phone 10 裝置上的原生郵件應用程式會自動使用 S/MIME 憑證。
- 私人憑證可以跨多個平台提供。 但並非所有電子郵件應用程式都支援 S/MIME。
- 在其他平台上，您可能需要手動設定郵件應用程式來啟用 S/MIME。  
- 支援 S/MIME 加密的電子郵件應用程式可能會以 MDM 無法支援的方式來處理 S/MIME 電子郵件加密的憑證擷取 (例如從其發行者的憑證存放區中讀取)。
如需這項功能的詳細資訊，請參閱 [S/MIME 電子郵件簽署和加密概觀](certificates-s-mime-encryption-sign.md)。
支援於：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>在 Windows 10 及更新版裝置上使用 DNS 設定時自動連線且持續規則的新選項 <!-- 1333665, 2999078 -->
在 Windows 10 及更新版本裝置上，您可以建立 VPN 組態設定檔，其中包含可用以解析網域 (例如 contoso.com) 的 DNS 伺服器清單。 此更新包含可用於名稱解析的新設定 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [Windows 10 及更新版本]  > 針對設定檔類型選擇 [VPN]  > [DNS 設定]   >[新增]  )： 
- **自動連線**：若**已啟用**，裝置就會在連絡您輸入的網域 (例如 contoso.com) 時，自動連線至 VPN。
- **永續性**：根據預設，只要裝置會使用此 VPN 設定檔進行連線，所有的名稱解析原則表格 (NRPT) 規則都會處於作用中狀態。 已在 NRPT 規則上**啟用**此設定時，此規則就會在裝置上維持作用中狀態，即使在 VPN 中斷連線時也一樣。 規則將一直保留，直到移除 VPN 設定檔，或以手動方式移除規則，這可以透過使用 PowerShell 完成。
[Windows 10 VPN 設定](vpn-settings-windows-10.md)將描述這些設定。 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>針對 Windows 10 裝置上的 VPN 設定檔使用受信任的網路偵測 <!-- 1500165 -->
使用受信任的網路偵測時，若使用者已經位於受信任的網路上，您可以防止 VPN 設定檔自動建立 VPN 連線。 在此更新中，您可以新增 DNS 尾碼，在執行 Windows 10 及更新版本之裝置上啟用受信任的網路偵測 ([裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選擇 [Windows 10 及更新版本]  > 針對設定檔類型選擇 [VPN]  )。
[Windows 10 VPN 設定](vpn-settings-windows-10.md)會列出目前的 VPN 設定。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>管理多位使用者所使用的 Windows Holographic for Business 裝置 <!-- 1907917, 1063203 -->
您目前可以使用自訂的 OMA-URI 設定，在 Windows 10 和 Windows Holographic for Business 裝置上設定共用的電腦設定。 在此更新中，會新增設定檔來設定共用的裝置設定 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]   > [共用的多重使用者裝置]  )。
若要深入了解這項功能，請前往[管理共用裝置的 Intune 設定](shared-user-device-settings.md)。
適用於：Windows 10 及更新版本、Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>新的 Windows 10 更新設定 <!--2626030  2512994  -->
針對 [Windows 10 更新通道](windows-update-for-business-configure.md)，您可以設定：
- **自動更新行為** - 使用新選項 [重設為預設]  ，在執行「2018 年 10 月更新」  的 Windows 10 電腦上還原原始的自動更新設定
- **防止使用者暫停 Windows 更新** - 設定新的軟體更新設定，可讓您封鎖或允許使用者從其電腦的 [設定]  暫停更新安裝。 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 電子郵件設定檔可以使用 S/MIME 簽署和加密 <!-- 2662949 -->
您可以建立包含不同設定的電子郵件設定檔。 此更新包含可在 iOS 裝置上用來簽署與加密電子郵件通訊的 S/MIME 設定 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [iOS]  > 針對設定檔類型選擇 [電子郵件]  )。
[iOS 電子郵件組態設定](email-settings-ios.md)會列出這些設定。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>部分 BitLocker 設定支援 Windows 10 專業版<!-- 2727036 -->
您可以建立組態設定檔，在 Windows 10 裝置上設定 Endpoint Protection 設定，包括 BitLocker。 此更新會針對部分 BitLocker 設定新增對 Windows 10 專業版的支援。 若要查看這些保護設定，請前往[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>共用裝置設定已在 Azure 入口網站中針對 iOS 裝置重新命名為鎖定畫面訊息<!-- 2809362 -->
當您建立適用於 iOS 裝置的組態設定檔時，您可以新增 [共用裝置設定]  設定，以便在鎖定畫面上顯示特定的文字。 此更新包含下列變更： 
- Azure 入口網站中的 [共用裝置設定]  已重新命名為「鎖定畫面訊息 (僅限受監督)」([裝置設定]   > [設定檔]   > [建立設定檔]  > 針對平台選擇 [iOS]  > 針對設定檔類型選擇 [裝置功能]  > [鎖定畫面訊息]  )。
- 新增鎖定畫面訊息時，您可以在 [資產標籤資訊]  和 [鎖定畫面註腳]  中插入序號、裝置名稱或另一個裝置特定的值以作為變數。 例如，您可以使用大括號來輸入 `Device name: {{devicename}}` 或 `Serial number is {{serialnumber}}`。 [iOS 權杖](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)會列出可使用的可用權杖。
[在鎖定畫面上顯示訊息的設定](shared-device-settings-ios.md)會列出這些設定。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>新增至 iOS 裝置的新 App Store、文件檢視、遊戲裝置限制設定 <!-- 2827760-->
在 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  平台 > [裝置限制]  設定檔類型 > [App Store、文件檢視、遊戲]  中，新增下列設定：[允許受控應用程式將連絡人寫入非受控連絡人帳戶]、[允許非受控應用程式從受控連絡人帳戶讀取]。若要查看這些設定，請前往 [iOS 裝置限制](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>將通知、提示和 Keyguard 設定新增至 Android Enterprise 裝置擁有者裝置 <!-- 3201839 3201843 -->
以裝置擁有者身分執行時，此更新會包括 Android 企業裝置上的多個新功能。 若要使用這些功能，請前往 [裝置設定]   > [設定檔]   > [建立設定檔]  > 在 [平台]  中選擇 [Android 企業]  > 在 [設定檔類型]  中選擇 [僅限裝置擁有者]   > [裝置限制]  。

新功能包括： 

- 停用系統通知的顯示，包括來電、系統警示、系統錯誤及更多功能。
- 針對第一次開啟的應用程式建議略過開始教學課程和提示。
- 停用進階的 Keyguard 設定，例如相機、通知、指紋解除鎖定及更多功能。


若要查看這些設定，請前往 [Android Enterprise 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise 裝置擁有者裝置可以使用 Always On VPN 連線 <!-- 3202194 -->
在此更新中，您可以在 Android 企業裝置擁有者裝置上使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定]   > [設定檔]   > [建立設定檔]   > 針對平台選擇 [Android 企業]  > 針對 [僅限裝置擁有者] 選擇 [裝置限制]  > [連線能力]  設定中啟用 Always-On VPN。 若要查看這些設定，請前往 [Android Enterprise 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 裝置上工作管理員中用來結束處理序的新設定 <!-- 3285177 --> 
此更新包含使用 Windows 10 裝置上的工作管理員來結束處理序的新設定。 您可以使用裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]  > 在 [平台]  中選擇 [Windows 10]  > 在 [設定檔類型]  中選擇 [裝置限制]   > [一般]  設定)，來選擇允許或阻止此設定。
若要查看這些設定，請前往 [Windows 10 裝置限制設定](device-restrictions-windows-10.md)。
適用於：Windows 10 及更新版本


### <a name="device-enrollment"></a>裝置註冊

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>更詳細的註冊限制失敗訊息 <!-- 3111564 -->
不符合註冊限制時，會提供更詳細的錯誤訊息。 若要查看這些訊息，請前往 [Intune]   > [疑難排解]  > 然後檢查 [註冊失敗] 表格。 如需詳細資訊，請參閱[註冊失敗清單](help-desk-operators.md#enrollment-failure-reference)。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="tenant-status-dashboard-----1124854---"></a>租用戶狀態儀表板  <!-- 1124854 -->
新的[租用戶狀態頁面](tenant-status.md)提供可讓您檢視租用戶狀態和相關詳細資料的單一位置。  此儀表板分成四個區域：
- **租用戶詳細資料** - 顯示資訊，包括您的租用戶名稱和位置、您的 MDM 授權單位、您租用戶中的總註冊裝置數，以及您的授權計數。 此區段也會列出您租用戶目前的服務版本。
- **連接器狀態** - 顯示您已設定的可用連接器相關資訊，也可能會列出尚未啟用的連接器。  
   每個連接器會根據其目前狀態，標記為 [狀況良好]、[警告] 或 [狀況不良]。 選取一個連接器以鑽研並檢視詳細資料，或為它設定其他資訊。
-  **Intune 服務健全狀況** - 顯示您租用戶的作用中事件或中斷相關詳細資料。 此區段中的資訊是直接從 Office 訊息中心所擷取。
-  **Intune 新聞** - 顯示您租用戶的作用中訊息。 包括您的租用戶收到最新 Intune 功能時的通知等訊息。  此區段中的資訊是直接從 Office 訊息中心所擷取。

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Windows 10 公司入口網站中的新說明及支援體驗 <!-- 1488939-->
新的公司入口網站 [說明及支援] 頁面協助使用者為應用程式和存取問題進行疑難排解，並要求協助。 他們可以從此新頁面，傳送有關錯誤和診斷記錄詳細資料的電子郵件，並找到其組織的技術服務人員詳細資料。 他們也將找到 [常見問題集] 區段，其中含有相關 Intune 文件的連結。 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune 的新說明及支援體驗   <!-- #3307080 -->
我們將於未來幾天為所有租用戶推出新的 [說明及支援] 體驗。 此新體驗適用於 Intune，並可在使用 [Azure 入口網站](https://portal.azure.com/)中的 Intune 刀鋒視窗時存取。
新體驗可讓您用自己的文字描述問題，並收到疑難排解深入解析和網站型修復內容。 這些解決方案透過規則型的機器學習演算法提供，由使用者查詢所驅動。 除了特定問題的指導之外，您也可以使用新的案例建立工作流程，透過電子郵件或電話來開啟支援案例。 此新體驗會取代一組靜態預先選取選項的舊版 [說明及支援] 體驗，這些選項是以您開啟 [說明及支援] 時所在控制台的區域為依據。 如需詳細資訊，請參閱[如何取得 Microsoft Intune 支援](get-support.md)。

### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="scope-tags-for-apps----1081941---"></a>應用程式的範圍標籤 <!-- 1081941 -->
您可以建立範圍標籤，限制對角色和應用程式的存取。 您可以將範圍標籤新增至應用程式，僅限具有角色並同時獲派該範圍標籤的人員才能存取應用程式。 目前，無法將從受控 Google Play 或應用程式 (使用 Apple 大量採購方案 (VPP) 購買) 新增至 Intune 的應用程式指派到範圍標籤 (往後將會提供支援)。 如需詳細資訊，請參閱[使用範圍標籤篩選原則](scope-tags.md)。

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>2018 年 12 月 10 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="updates-for-application-transport-security----748318---"></a>更新 Application Transport Security <!-- 748318 -->

Microsoft Intune 支援傳輸層安全性 (TLS) 1.2+ 來提供業界領先的加密功能，以確保 Intune 預設更安全，並可搭配 Microsoft Office 365 等其他 Microsoft 服務使用。 為了符合此需求，iOS 和 macOS 公司入口網站將會強制執行 Apple 的更新 Application Transport Security (ATS) 需求，這些需求也要求使用 TLS 1.2+。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 和 macOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請參閱 [Intune 支援小組部落格](https://aka.ms/compportalats) \(英文\)。

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 將支援 256 位元的加密金鑰 <!-- 1832174 -->
適用於 Android 的 Intune App SDK 現在會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 SDK 將繼續提供 128 位元金鑰的支援，以取得與使用較舊 SDK 版本之內容和應用程式的相容性。

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>macOS 裝置需要 Microsoft 自動更新版本 4.50 <!-- 3503442 -->
若要繼續接收公司入口網站和其他 Office 應用程式的更新，Intune 所管理的 macOS 裝置必須先升級到 Microsoft 自動更新 4.5.0。 使用者可能已經擁有此版本的 Office 應用程式。

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune 需要 macOS 10.12 或更新版本 <!-- 2827778 -->
Intune 現在需要 macOS 版本 10.12 或更新版本。 使用先前的 macOS 版本的裝置無法使用公司入口網站來註冊 Intune。 為了收到支援協助和新功能，使用者必須將其裝置升級至 macOS 10.12 或更新版本，並將公司入口網站升級至最新版本。

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>2018 年 11 月 26 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>在公司擁有的受監督 iOS 裝置上解除安裝應用程式 <!-- 1281677 -->

您可以移除公司所擁有之受監督 iOS 裝置上的任何應用程式。 您可以透過針對具有**解除安裝**指派類型的使用者或裝置群組，來移除任何應用程式。 針對個人或不受監督的 iOS 裝置，您仍可以僅移除使用 Intune 安裝的應用程式。

#### <a name="downloading-intune-win32-app-content----2617320---"></a>下載 Intune Win32 應用程式內容 <!-- 2617320 -->
Windows 10 RS3 和更新版本的用戶端，將會使用 Windows 10 用戶端上的「傳遞最佳化」元件來下載 Intune Win32 應用程式內容。 傳遞最佳化能提供預設開啟的點對點功能。 傳遞最佳化可以由群組原則進行設定，在未來也將能透過 Intune MDM 進行設定。 如需詳細資訊，請參閱[適用於 Windows 10 的傳遞最佳化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) \(部分機器翻譯\)。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>終端使用者裝置和應用程式內容功能表 <!-- 2771453 -->
終端使用者現在可以在裝置和應用程式上使用操作功能表，以觸發重新命名裝置或檢查合規性等常見動作。

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>在受控主畫面應用程式中設定自訂背景  <!-- 3041945 -->
我們將新增一項設定，可讓您在 Android Enterprise、多應用程式、kiosk 模式裝置上自訂受控主畫面應用程式的背景外觀。  若要設定**自訂 URL 背景**，請前往 Azure 入口網站 > [裝置設定] 中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](device-restrictions-android-for-work.md)。

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>會儲存並套用應用程式防護原則指派 <!-- 3104570 -->
您將可以更有效控制[應用程式保護原則指派](app-protection-policies.md#deploy-a-policy-to-users)。 當您選取 [指派]  以設定或編輯某個原則的指派時，您必須先 [儲存]  設定，系統才會套用變更。 使用 [捨棄]  來清除您所做的所有變更，而不將任何變更儲存到包含或排除清單。  透過要求使用者進行 [儲存] 或 [捨棄]，將能確保系統只會將應用程式保護原則指派給您想要的使用者。

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>適用於 Windows 10 及更新版本的新 Microsoft Edge 瀏覽器設定 <!-- 3174639 -->
此更新將會包含新的設定，以協助您控制和管理裝置上的 Microsoft Edge 瀏覽器。 如需這些設定的清單，請參閱[適用於 Windows 10 (及更新版本) 的裝置限制](device-restrictions-windows-10.md#microsoft-edge-browser)。

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>搭配應用程式防護原則的新應用程式支援 <!-- 3330037 -->
您現在可以搭配 [Intune 應用程式保護原則](app-protection-policies.md)管理下列應用程式：
- Stream (iOS)
- To DO (Android、iOS)
- PowerApps (Android、iOS)
- Flow (Android、iOS)

使用應用程式保護原則來保護公司資料，並以和其他 Intune 原則受管理的應用程式相同的方式控制這些應用程式的資料傳輸。 注意：如果 Flow 在主控台中尚不可見，您可在建立或編輯應用程式保護原則時新增 Flow。 若要這麼做，請使用 [+ 更多應用程式]  選項，然後在輸入欄位中指定 Flow 的 [應用程式識別碼]  。 針對 Android，請使用 *com.microsoft.flow*，而針對 iOS 則請使用 *com.microsoft.procsimo*。


### <a name="device-configuration"></a>裝置設定

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>顯示 iOS 和 macOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性]   > [裝置合規性]  中，會顯示 iOS 和 macOS 作業系統版本，並可用於合規性政策。 此更新包含可同時針對兩個平台設定的組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 藉由在合規性政策中使用組建編號，即可輕鬆地檢查是否已安裝弱點更新。
若要使用此功能，請參閱 [iOS](compliance-policy-create-ios.md#device-health) 和 [macOS](compliance-policy-create-mac-os.md#device-properties) 合規性原則。

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>針對 Windows 10 及更新版本，更新通道將由傳遞最佳化設定取代 <!-- 2753807 -->
傳遞最佳化是適用於 Windows 10 和更新版本的新組態設定檔。 此功能可提供更加流暢的使用體驗，以將軟體更新傳遞到您組織中的裝置。 此更新也能協助您使用組態設定檔，在新的與現有的更新通道中傳遞設定。
若要設定傳遞最佳化組態設定檔，請參閱 [Windows 10 (和更新版本) 的傳遞最佳化設定](delivery-optimization-windows.md)。

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>新增至 iOS 和 macOS 裝置的新裝置限制設定 <!-- 2827760 -->
此更新包含適用於 iOS 和 macOS 裝置，與 iOS 12 所發行的新設定：

**iOS 設定**： 
- 一般：封鎖應用程式移除 (僅限受監督)
- 一般：封鎖 USB 限制模式 (僅限受監督)
- 一般：強制自動日期和時間 (僅限受監督)
- 密碼：封鎖密碼自動填入 (僅限受監督)
- 密碼：封鎖密碼鄰近性要求 (僅限受監督)
- 密碼：封鎖密碼共用 (僅限受監督)

**macOS 設定**： 
- 密碼：封鎖密碼自動填入
- 密碼：封鎖密碼鄰近性要求
- 密碼：封鎖密碼共用

若要深入了解這些設定，請參閱 [iOS](device-restrictions-ios.md) 和 [macOS](device-restrictions-macos.md) 裝置限制設定。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>選取註冊狀態頁面上追蹤的應用程式<!-- 2531007 -->
您可以選擇要在註冊狀態頁面上追蹤哪些應用程式。 在安裝這些應用程式之前，使用者將無法使用該裝置。 如需詳細資訊，請參閱[設定註冊狀態頁面](windows-enrollment-status.md)。

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>依序號搜尋 Autopilot 裝置 <!--2595788 -->
您現在可以依序號搜尋 Autopilot 裝置。 若要這麼做，請選擇 [裝置註冊]   > [Windows 註冊]   > [裝置]  > 在 [依序號搜尋]  方塊中輸入序號 > 按 Enter。

#### <a name="track-installation-of-office-proplus---2620217---"></a>追蹤 Office 專業增強版的安裝 <!--2620217 -->
使用者可以使用[註冊狀態頁面](windows-enrollment-status.md)來追蹤 [Office 專業增強版](apps-add-office365.md)的安裝進度。 如需詳細資訊，請參閱[設定註冊狀態頁面](windows-enrollment-status.md)。

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示 <!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Apple School Manager 帳戶的 macOS 裝置註冊計劃 <!--3006133 -->
Intune 現已支援在適用於 Apple School Manager 帳戶的 macOS 裝置上使用裝置註冊計劃。  如需詳細資訊，請參閱[使用 Apple School Manager 或裝置註冊計劃來自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)。

### <a name="new-intune-device-subscription-sku---3312071--"></a>新的 Intune 裝置訂閱 SKU <!--3312071-->
為了協助降低企業中的裝置管理裝置成本，現在提供新的裝置型訂閱 SKU。 此 Intune 裝置 SKU 是依每月每部裝置來授權。 價格會因授權方案而有所不同。 它可直接透過 Microsoft 365 系統管理中心，以及透過 [Enterprise 合約](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA)、[Microsoft 產品和服務合約](https://www.microsoft.com/licensing/mpsa/default) (MPSA)、[Microsoft Open Agreement](https://partner.microsoft.com/licensing/licensing-agreements) 和[雲端解決方案提供者](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) 提供使用。

### <a name="device-management"></a>裝置管理

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>暫停 Android 裝置上的 kiosk 模式以進行變更 <!-- 3041935 -->
在多應用程式 kiosk 模式下使用 Android 裝置時，IT 系統管理員可能需要對裝置進行變更。 此更新包含新的多應用程式 kiosk 設定，允許 IT 系統管理員使用 PIN 暫時暫停 kiosk 模式，並存取整個裝置。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](device-restrictions-android-for-work.md)。

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>啟用 Android Enterprise kiosk 裝置上的虛擬首頁按鈕  <!-- 3042021 -->
新設定可讓使用者點選其裝置上的螢幕按鍵按鈕，以在其多應用程式 kiok 裝置上的受控主畫面應用程式和其他已指派應用程式之間切換。 在使用者的 kiosk 應用程式未對「返回」按鈕做出適當回應情況下，此設定特別有用。 您將能夠為公司擁有的一次性 Android 裝置設定此設定。 若要啟用或停用**虛擬首頁按鈕**，請前往 Azure 入口網站 > 裝置設定中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](device-restrictions-android-for-work.md)。

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>2018 年 11 月 12 日當週

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>網路存取控制 (NAC) 針對 iOS 支援 Citrix SSO <!-- 3259404 -->

Citrix 已發行 Citrix Gateway 更新以允許 Intune 中 iOS 的 Citrix SSO 的網路存取控制 (NAC)。 您可以在 Intune 中選擇在 VPN 設定檔中包括裝置識別碼，然後將此設定檔推送到您的 iOS 裝置。 您將必須安裝最新的更新到 Citrix Gateway，才能使用此功能。

[在 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md#base-vpn-settings)提供有關使用 NAC 的詳細資訊，包括一些額外需求。 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>2018 年 11 月 5 日當週

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>在 iOS 電子郵件設定檔中支援 iOS 12 OAuth <!--2155106 -->

Intune 的 iOS 電子郵件設定檔支援 iOS 12 Open Authorization (OAuth)。 若要查看此功能，請建立新的設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  作為平台 > [電子郵件]  作為設定檔類型)，或更新現有的 iOS 電子郵件設定檔。 如果您在已部署給使用者的設定檔中啟用 OAuth，則會提示使用者重新驗證，並再次下載其電子郵件。

[iOS 電子郵件設定檔](email-settings-ios.md)會包含有關在電子郵件設定檔中使用 OAuth 的詳細資訊。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>已加入混合式 Azure Active Directory 裝置的 Autopilot 支援 (預覽) <!-- 1048100-->
您現在可以透過使用 Autopilot，來設定混合式 Azure Active Directory 聯結裝置。 裝置必須聯結到您組織的網路，才能使用混合式 Autopilot 功能。 如需詳細資訊，請參閱[使用 Intune 和 Windows Autopilot 部署混合式 Azure AD 聯結裝置](windows-autopilot-hybrid.md)。
此功能將在未來幾天內在整個使用者群中推出。 因此，在推出至您的帳戶之前，您可能無法執行這些步驟。

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>2018 年 10 月 29 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>在指定的逾時之後要求非生物特徵辨識 PIN <!-- 1506985 -->
透過在系統管理員指定的逾時之後要求非生物特徵辨識 PIN，Intune 可藉由限制使用生物特徵辨識身分識別來存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法，來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置，可能會向不正確使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]  。 選取 [用戶端應用程式]   > [應用程式保護原則]   > [新增原則]   > [設定]  。 找出特定設定的 [存取]  區段。 如需存取設定的資訊，請參閱 [iOS 設定](app-protection-policy-settings-ios.md#access-requirements)和 [Android 設定](app-protection-policy-settings-android.md#access-requirements)。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 註冊裝置上的 Intune 應用程式資料轉送設定 <!-- 2244713 -->
您可以將已註冊 iOS MDM 裝置上 Intune 應用程式資料轉送設定的控制，與指定已註冊使用者的身分識別 (也稱為使用者主體名稱 (UPN)) 區分開來。 不使用 IntuneMAMUPN 的系統管理員將不會發現行為變更。 當此功能可用時，使用 IntuneMAMUPN 來控制已註冊裝置上資料轉送行為的系統管理員，應檢閱新的設定並視需要更新其應用程式設定。

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 應用程式 <!-- 2617325 -->
您可以設定 Win32 應用程式在個別 使用者的使用者內容中安裝，而不是為裝置的所有使用者安裝應用程式。

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 應用程式和 PowerShell 指令碼 <!-- 2617330 -->
終端使用者已不再需要登入裝置來安裝 Win32 應用程式或執行 PowerShell 指令碼。 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>針對用戶端應用程式安裝進行疑難排解 <!-- 1363711 -->
您可以藉由檢閱 [疑難排解]  刀鋒視窗中標示為 [應用程式安裝]  的資料行，來為用戶端應用程式的安裝成功問題進行疑難排解。 若要檢視 [疑難排解]  刀鋒視窗，請在 Intune 入口網站中的 [說明及支援]  下選取 [疑難排解]  。

### <a name="device-configuration"></a>裝置設定

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>iOS VPN 用戶端上的網路存取控制支援 <!-- 1333693 -->
透過此更新，您可以在為 Cisco AnyConnect、F5 Access 和 Citrix SSO for iOS 建立 VPN 設定檔時啟用網路存取控制 (NAC)。 此設定可讓裝置的 NAC 識別碼包含在 VPN 設定檔中。 目前尚沒有任何支援此新 NAC 識別碼的 VPN 用戶端或 NAC 合作夥伴解決方案；當提供支援時，我們將透過[支援部落格文章](ttps://aka.ms/iOS12_and_vpn)通知您。

若要使用 NAC，您將需要：
1. 選擇允許 Intune 在 VPN 設定檔中包含裝置識別碼
2. 更新您的 NAC 提供者軟體/韌體，直接從您的 NAC 提供者使用指導方針

如需 iOS VPN 設定檔中此設定的相關資訊，請參閱[在 Microsoft Intune 中的 iOS 裝置上新增 VPN 設定](vpn-settings-ios.md)。 如需網路存取控制的詳細資訊，請參閱[搭配 Intune 的網路存取控制 (NAC) 整合](network-access-control-integrate.md)。 

適用於：iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>從裝置移除電子郵件設定檔，即使只有一個電子郵件設定檔也一樣 <!-- 1818139 -->
之前，「如果」  這是唯一的電子郵件設定檔，則無法從裝置移除電子郵件設定檔。 在此更新中，此行為會有所變更。 現在，您可以移除電子郵件設定檔，即使裝置上只有一個電子郵件設定檔也一樣。 如需詳細資訊，請參閱[使用 Intune 將電子郵件設定新增至裝置](email-settings-configure.md)。

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell 指令碼和 AAD <!-- 2309469 -->
Intune 中的 PowerShell 指令碼可以鎖定至 AAD 裝置安全性群組。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>適用於 Android、Android Enterprise 的新「必要密碼類型」預設設定<!-- 2649963 -->
當您建立新的合規性原則 (針對 [平台] > [系統安全性]，選擇 [Intune]   > [裝置合規性]   > [原則]   > [建立原則]   > [Android]  或 [Android Enterprise]  ) 時，[必要密碼類型]  的預設值會變更：

從：裝置預設為：至少包含數字

適用於：Android、Android Enterprise

若要查看這些設定，請瀏覽 [Android](compliance-policy-create-android.md) 和 [Android Enterprise](compliance-policy-create-android-for-work.md)。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 設定檔中使用預先共用金鑰 <!-- 2662938 -->
透過此更新，您可以搭配 WPA/WPA2-Personal 安全性通訊協定使用預先共用金鑰 (PSK)，來驗證適用於 Windows 10 的 Wi-Fi 組態設定檔。 您也可以在Windows 10 2018 年 10 月更新中，為裝置指定計量付費網路的成本設定。

目前您必須匯入 Wi-Fi 設定檔或是建立自訂的設定檔，才能使用預先共用金鑰。 [適用於 Windows 10 的 Wi-Fi 設定](wi-fi-settings-windows.md)列出目前的設定。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>從您的裝置移除 PKCS 和 SCEP 憑證 <!-- 3218390 -->
在某些案例中，PKCS 和 SCEP 憑證會保留在裝置上，即使從群組中移除原則、刪除設定或合規性部署，或是系統管理員更新現有的 SCEP 或 PKCS 設定檔也一樣。 此更新會變更該行為。 在某些案例中，PKCS 和 SCEP 憑證會從裝置移除；在某些案例中，這些憑證會保留在裝置上。 請參閱[在 Microsoft Intune 中移除 SCEP 和 PKCS 憑證](remove-certificates.md)以了解這些案例。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>在 macOS 裝置上使用閘道管理員以符合規範 <!-- 2504381 -->
此更新包括 macOS 閘道管理員，用於評估裝置合規性。 若要設定閘道管理員屬性，請[為 macOS 裝置新增裝置合規性政策](compliance-policy-create-mac-os.md)。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="enrollment-abandonment-report----1382924---"></a>註冊放棄報表 <!-- 1382924 -->
您可以在 [裝置註冊]   > [監視]  下取得新報表，提供已放棄註冊的詳細資料。 如需詳細資訊，請參閱[公司入口網站放棄報表](enrollment-report-company-portal-abandon.md)。

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>新的 Azure Active Directory 使用條款功能 <!-- 2870393 -->
Azure Active Directory 具備您可以改使用的條款功能，而無須使用現有 Intune 條款及條件。 Azure AD 使用條款功能可提供更多彈性，讓您決定要顯示哪些條款以及顯示的時機、具備更佳的當地語系化支援、對轉譯條款的方式擁有更大控制能力，以及改善回報。 Azure AD 使用條款需要 Azure Active Directory Premium P1，該項目也是 Enterprise Mobility + Security E3 套件的一部分。 若要深入了解，請參閱[管理公司的使用者存取條款及條件](terms-and-conditions-create.md)一文。

#### <a name="android-device-owner-mode-support---3188762--"></a>Android 裝置擁有者模式支援 <!--3188762-->
針對 Samsung Knox 行動裝置註冊，Intune 現在支援將裝置註冊於 Android 裝置擁有者管理模式。 使用 WiFi 或行動電話通訊網路的使用者第一次開啟其裝置時，只需輕點幾下即可註冊。 如需詳細資訊，請參閱[使用 Samsung Knox Mobile Enrollment 自動註冊 Android 裝置](android-samsung-knox-mobile-enroll.md)。

### <a name="device-management"></a>裝置管理
#### <a name="new-settings-for-software-updates------1907869---"></a>軟體更新的新設定   <!-- 1907869 -->  
- 您現在可以設定某些通知，以警告終端使用者完成最新軟體更新安裝所需的重新啟動。   
- 您現在可以為非工作時間發生的重新啟動設定重新啟動警告提示，可支援 BYOD 案例。

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>透過交互識別碼群組 Windows Autopilot 註冊裝置 <!-- 2075110 -->
Intune 現在支援在透過 Configuration Manager 使用[適用於現有裝置的 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)註冊時，使用交互識別碼來為 Windows 裝置分組。 交互識別碼是 Autopilot 設定檔的參數。 Intune 會自動將 [Azure AD 裝置屬性 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects) 設為相等的 "OfflineAutopilotprofile-<correlator ID>"。 這會允許透過離線 Autopilot 註冊的 enrollmentprofileName 屬性，根據交互識別碼建立任意 Azure AD 動態群組。 如需詳細資訊，請參閱[現有裝置的 Windows Autopilot](enrollment-autopilot.md#windows-autopilot-for-existing-devices)。

#### <a name="intune-app-protection-policies----2984657---"></a>Intune 應用程式防護原則 <!-- 2984657 -->
Intune 應用程式保護原則可讓您為 Intune 保護的應用程式 (如 Microsoft Outlook 和 Microsoft Word) 設定各種資料保護設定。 我們已變更這些設定的外觀與風格 ([iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md))，以便輕鬆找到個別設定。 原則設定有三個類別：
- **資料重新配置** - 此群組包含資料外洩防護 (DLP) 控制項，例如剪下、複製、貼上以及另存新檔的限制。 這些設定會決定使用者如何與應用程式中的資料互動。
- **存取需求** - 此群組包含每個應用程式的 PIN 選項，用於決定終端使用者如何在工作環境中存取應用程式。  
- **條件式啟動** - 此群組包含最低作業系統設定、越獄和 Root 裝置偵測以及離線寬限期等設定。  
  
設定的功能不會變更，但可讓您在處理原則編寫流程時更容易找到。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>針對 LOB 應用程式，Intune 將支援最大 8 GB 套件大小 <!-- 1727158 -->
Intune 會將企業營運 (LOB) 應用程式的最大套件大小增加為 8 GB。 如需詳細資訊，請參閱[將應用程式新增至 Microsoft Intune](apps-add.md)。

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>新增公司入口網站應用程式的自訂品牌形象 <!-- 1916266 -->
作為 Microsoft Intune 系統管理員，您可以上傳自訂品牌影像，該影像會在 iOS 公司入口網站應用程式的使用者設定檔頁面上，作為背景影像顯示。 如需設定公司入口網站應用程式的詳細資訊，請參閱[如何設定 Microsoft Intune 公司入口網站應用程式](company-portal-app.md)。

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>Intune 會在更新終端使用者電腦上的 Office 時保留 Office 當地語系化語言 <!-- 2971030 -->
當 Intune 在您終端使用者的電腦上安裝 Office 時，終端使用者會自動取得與其先前 .MSI Office 安裝相同的語言套件。 如需詳細資訊，請參閱[使用 Microsoft Intune 將 Office 365 應用程式指派給 Windows 10 裝置](apps-add-office365.md)。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Microsoft 365 裝置管理入口網站中的新 Intune 支援體驗 <!-- 3076965 -->
我們正於 [Microsoft 365 裝置管理入口網站]( http://devicemanagement.microsoft.com)中，為 Intune 推出新的說明及支援體驗。 新體驗可讓您用自己的文字描述問題，並收到疑難排解深入解析和網站型修復內容。 這些解決方案透過規則型的機器學習演算法提供，由使用者查詢所驅動。  

除了特定問題的指導之外，您也可以使用新的案例建立工作流程，透過電子郵件或電話來開啟支援案例。  

針對參與推出的客戶，此新體驗會取代一組靜態預先選取選項的目前說明和支援體驗，這些選項會基於您開啟說明及支援時所在控制台的區域。  

*這個新的說明及支援體驗正在推出至部分 (並非全部) 租用戶，並且可在 [裝置管理] 入口網站中找到。從可用的 Intune 租用戶中隨機選取這個新體驗的參與者。在我們擴展推出時，將會新增新租用戶。*  

如需詳細資訊，請參閱＜如何取得 Microsoft Intune 支援＞中的[說明及支援體驗](get-support.md#help-and-support-experience)。  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>適用於 Intune 的 PowerShell 模組 - 現供預覽 <!-- 951068 -->
新的 PowerShell 模組透過 Microsoft Graph 支援 Intune API，現在於 [GitHub]( https://aka.ms/intunepowershell) 上提供預覽。 如需如何使用此模組的詳細資料，請參閱該位置的讀我檔案。 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>2018 年 10 月 15 日當週

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>當您變更 iOS 裝置上的指紋或 Face ID 時會收到輸入 PIN 的提示  <!-- 2637704  -->
現在，當使用者在其 iOS 裝置上進行生物特徵辨識變更之後，會收到輸入 PIN 的提示。 這包括變更已註冊的指紋或 Face ID。 提示時間取決於 [重新檢查存取需求前的剩餘時間 (分鐘)]  逾時的設定方式。  若未設定任何 PIN，則系統會提示使用者設定一個。 
 
此功能僅適用於 iOS，並需要整合 Intune APP SDK for iOS 9.0.1 版或更新版本的應用程式參與。 您必須整合此 SDK，才能針對目標應用程式強制執行該行為。 這項整合會輪流發生並取決於特定的應用程式小組。 參與的一些應用程式包括 WXP、Outlook、Managed Browser 和 Yammer。


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>2018 年 10 月 1 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>使用公司入口網站應用程式存取重要設定檔屬性 <!-- 772203 -->
終端使用者現在可以從公司入口網站應用程式，存取重要帳戶屬性和動作，例如密碼重設。 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>受控 Android 和 iOS 裝置上的 Intune 應用程式使用者帳戶存取 <!-- 1248496 -->
身為 Microsoft Intune 系統管理員，您可以控制在受控裝置上要新增至 Microsoft Office 應用程式的使用者帳戶。 您可以僅允許組織使用者帳戶進行存取，並封鎖已註冊裝置上的個人帳戶。 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Outlook iOS 和 Android 應用程式設定原則 <!--1828527 -->
您現在可以為透過 ActiveSync 通訊協定利用基本驗證的內部部署使用者，建立適用於 iOS 和 Android 的 Outlook iOS 及 Android 應用程式設定原則。 其他組態設定會隨著我們針對 iOS 和 Android 版 Outlook 啟用它們之後新增。

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 語言套件 <!-- 1833450 -->
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune]   > [用戶端應用程式]   > [應用程式]   > [新增]  。 在 [新增應用程式]  刀鋒視窗的 [應用程式類型]  清單中，選取 [Office 365 套件]  下的 [Windows 10]  。 選取 [應用程式套件設定]  刀鋒視窗中的 [語言]  。

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 企業營運 (LOB) 應用程式副檔名 <!-- 1884873 -->
Windows LOB 應用程式的副檔名現在包含 *.msi*、 *.appx*、 *.appxbundle*、 *.msix* 和 *.msixbundle*。 您可以依序選取 [用戶端應用程式]   > [應用程式]   > [新增]  ，在 Microsoft Intune 中新增應用程式。 隨即顯示 [新增應用程式]  窗格，讓您可以選取 [應用程式類型]  。 針對 Windows LOB 應用程式，選取 [企業營運]  應用程式作為應用程式類型，並選取 [應用程式套件檔案]  ，然後輸入具有適當副檔名的安裝檔。

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>使用 Intune 進行 Windows 10 應用程式部署 <!-- 2309001 -->
以企業營運 (LOB) 應用程式和商務用 Microsoft Store 應用程式的現有支援為基礎，系統管理員可以使用 Intune 將其組織的大部分現有應用程式部署到 Windows 10 裝置上的終端使用者。 系統管理員可以使用各種格式 (例如 MSI、Setup.exe 或 MSP)，為 Windows 10 的使用者新增、安裝及解除安裝應用程式。 Intune 會在下載和安裝之前評估需求規則，並使用 Windows 10 控制中心通知終端使用者狀態或重新開機需求。 這項功能會有效率地解除封鎖想要將此工作負載轉移到 Intune 和雲端的組織。 這項功能目前處於公開預覽狀態，我們預期在接下來的幾個月內在該功能中新增重要的新功能。 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定 <!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>終端使用者裝置和應用程式內容功能表 <!-- 2771453 -->
終端使用者現在可以使用裝置和應用程式上的操作功能表來觸發常見動作，例如重新命名裝置或檢查合規性。 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 公司入口網站鍵盤快速鍵 <!-- 2771518 -->
終端使用者現在能夠於 Windows 公司入口網站中使用鍵盤快速鍵觸發程序應用程式和裝置動作。

### <a name="device-configuration"></a>裝置設定

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>在執行 Windows 10 的裝置上於 VPN 組態設定檔中建立 DNS 尾碼<!-- 1333668 -->
當您建立 VPN 裝置組態設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [VPN]  設定檔類型) 時，您需要輸入一些 DNS 設定。 透過此更新，您也可以在 Intune 中輸入多個 **DNS 尾碼**。 使用 DNS 尾碼時，您可以使用其簡短名稱來搜尋網路資源，而不需使用完整網域名稱 (FQDN)。 此更新也可讓您在 Intune 中變更 DNS 尾碼的順序。
[Windows 10 VPN 設定](vpn-settings-windows-10.md#dns-settings)列出目前的 DNS 設定。
適用於：Windows 10 裝置

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>適用於 Android 企業工作設定檔的 Always-On VPN 支援 <!-- 1333705 -->
在此更新中，您將可以在 Android 企業裝置上搭配受控的工作設定檔來使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定]   > [設定檔]   > [建立設定檔]   > [Android 企業]  平台 > [裝置限制]   > [連線能力]  設定中啟用 Always-On VPN。

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>將 SCEP 憑證發給無使用者的裝置 <!-- 1744554 -->
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
>  - `{{FullyQualifiedDomainName}}` 只適用於 Windows 和已加入網域的裝置。 
>  -  在裝置憑證的主體或 SAN 中指定 IMEI、序號和完整網域名稱等裝置屬性時，請留意這些屬性可能會被能夠存取該裝置的人員竄改。 

[建立 SCEP 憑證設定檔](certificates-scep-configure.md#create-a-scep-certificate-profile)列出目前在建立 SCEP 組態設定檔時的變數。 

適用於：Windows 10 及更新版本和 iOS (支援 Wi-Fi)

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>從遠端鎖定不符合規範的裝置 <!-- 2064495 -->
當裝置不符合規範時，您可以在合規性原則上建立從遠端鎖定該裝置的動作。 在 Intune > [裝置合規性]  中建立新原則或選取現有的原則 > [屬性]  。 選取 [因不符合規範而採取的動作]   > [新增]  ，然後選擇以從遠端鎖定裝置。
支援於： 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 和更新版本 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure 入口網站中針對 Windows 10 及更新版本 Kiosk 設定檔的改善 <!-- 2748224 -->
此更新包含下列對 Windows 10 Kiosk 裝置設定檔 ([裝置設定]   > [設定檔]   > [建立設定檔]   > [Windows 10 及更新版本]  平台 > [Kiosk 預覽]  設定檔類型) 的改善： 
- 目前，您可以在相同的裝置上建立多個 Kiosk 設定檔。 透過此更新，Intune 針對每部裝置都只會支援單一 Kiosk 設定檔。 如果您仍需要在單一裝置上有多個 Kiosk 設定檔，則可以使用自訂 URI。
- 在 [多應用程式 kiosk]  設定檔中，您可以針對應用程式格線中的 [[開始] 功能表配置]  選取應用程式磚大小和順序。 如果您想要取得更多自訂項目，您可以繼續上傳 XML 檔案。
- [Kiosk 瀏覽器] 設定會移至 [Kiosk]  設定中。 目前，[Kiosk 網頁瀏覽器]  設定在 Azure 入口網站中具有自己的類別。
適用於：Windows 10 及更新版本




### <a name="device-enrollment"></a>裝置註冊

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置 <!-- 1558983 -->
您可以將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置。 在 Autopilot 設定檔中，選擇 [將所有目標裝置轉換為 Autopilot]  選項，以將所有非 Autopilot 的裝置自動註冊至 Autopilot 部署服務。 等候 48 小時讓註冊處理完畢。 當裝置取消註冊並重設時，Autopilot 將會自動佈建它。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>建立並指派多個註冊狀態頁面設定檔至 Azure AD 群組 <!-- 2526564 -->
您現在可以[建立並指派](windows-enrollment-status.md)多個註冊狀態頁面設定檔至 Azure AD 群組。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>從裝置註冊計劃移轉到 Intune 中的 Apple Business Manager <!--2748613-->
Apple Business Manager (ABM) 能在 Intune 中運作，您可以將您的帳戶從裝置註冊計劃 (DEP) 升級到 ABM。 Intune 中的程序都相同。 若要將您的 Apple 帳戶從 DEP 升級到 ABM，請前往 [https://support.apple.com/HT208817]( https://support.apple.com/HT208817)。

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>[裝置註冊概觀] 頁面上的 [警示] 和 [註冊狀態] 索引標籤 <!--2748656-->
警示和註冊失敗現在會出現在 [裝置註冊概觀] 頁面的個別索引標籤上。

### <a name="device-management"></a>裝置管理

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>限制應用程式，並封鎖存取 Android 裝置上的公司資源 <!-- 2451462  -->  
在 [裝置合規性]   > [原則]   > [建立原則]   > [Android]   > [系統安全性]  中，[裝置安全性]  區段下方有一個名為 [受限應用程式]  的新設定。 若在裝置上安裝特定應用程式，則 [受限應用程式]  設定會使用合規性原則來封鎖對公司資源的存取。 除非從裝置中移除受限制應用程式，否則會將裝置視為不符合規範。
適用於： 
- Android

<!-- ########################### -->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
