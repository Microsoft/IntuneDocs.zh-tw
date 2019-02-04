---
title: Microsoft Intune 的新功能 - Azure | Microsoft Docs
titlesuffix: ''
description: 了解 Intune Azure 入口網站中的新功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/25/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.openlocfilehash: 21fde80ec80492957b686a66dcfe4db55894c38e
ms.sourcegitcommit: 6f2f2fa70f4e47fa5ad2f3c536ba7116e1bd1d05
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2019
ms.locfileid: "55199484"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

了解每週的 Microsoft Intune 新功能 您也可以找到即將推出的變更、[重要通知](#notices)，以及[過去版本](whats-new-archive.md)的相關資訊。 某些功能在首度發行時可能會花費數週的時間，而可能無法在第一週就提供給所有客戶。

> [!Note]
> 如需混合式行動裝置管理 (MDM) 的新功能資訊，請參閱[混合式新功能頁面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。

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
## <a name="week-of-january-21-2019"></a>2019 年 1 月 21 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 應用程式的快顯通知 <!-- 3136566   -->
您可以隱藏而不顯示每個應用程式指派的終端使用者快顯通知。 從 Intune 選取 [用戶端應用程式] > [應用程式] > 選取應用程式 > [指派] > [包含群組]。 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 應用程式保護原則 UI 更新 <!-- 3251427  -->
我們已變更 Intune 應用程式保護的設定和按鈕標籤，以使它們更容易理解。 部分變更包括：  
- 控制項從 [是] / [否] 的控制項，變更成主要為 [封鎖] / [允許]****，以及 [停用] / [啟用] 的控制項。 標籤也一併更新。  
- 設定已重新格式化，因此設定和其標籤會在控制項中並排顯示，提供更好的瀏覽。   

預設設定和設定數量會保持相同，但這項變更可讓使用者更輕鬆了解、瀏覽和利用這些設定，以套用所選的應用程式保護原則。 如需詳細資訊，請參閱 [iOS 設定](app-protection-policy-settings-ios.md)和 [Android 設定](app-protection-policy-settings-android.md)。

#### <a name="additional-settings-for-outlook----3301182----"></a>Outlook 的其他設定 <!-- 3301182  -->
您現在可以使用 Intune 來設定 iOS 和 Android 版 Outlook 的其他設定。  這些設定包括：只允許在 iOS 和 Android 版 Outlook 中使用公司或學校帳戶。為 Office 365 和混合式新式驗證內部部署帳戶部署新式驗證。選取基本驗證時，針對電子郵件設定檔中的使用者名稱欄位使用 `SAMAccountName`。允許儲存連絡人。設定外部收件者 MailTips。設定 [焦點收件匣]。需要生物特徵識別技術才能存取 iOS 版 Outlook。封鎖外部影像
> [!NOTE]
> 如果您使用 Intune 應用程式防護原則來管理公司身分識別的存取權，您應該考慮不啟用 [require biometrics] \(需要生物識別技術\)。 如需詳細資訊，請參閱 [iOS 存取設定](app-protection-policy-settings-ios.md#access-settings)和 [Android 存取設定](app-protection-policy-settings-android.md#access-settings)中的＜需要公司認證才能存取＞。

#### <a name="delete-android-enterprise-apps----1352553---"></a>刪除 Android Enterprise 應用程式 <!-- 1352553 -->
您可以從 Microsoft Intune 刪除受控的 Google Play 應用程式。 若要刪除受控的 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [用戶端應用程式] > [應用程式]。 從應用程式清單，選取受控的 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

#### <a name="managed-google-play-app-type----1352580---"></a>受控的 Google Play 應用程式類型 <!-- 1352580 -->
[受控的 Google Play] 應用程式類型可讓您將[受控 Google Play 應用程式](https://play.google.com/work/search?q=microsoft&c=apps)明確新增至 Intune。 身為 Intune 系統管理員，您現在可以在 Intune 中瀏覽、搜尋、核准、同步及指派已核准之受控的 Google Play 應用程式。  您不再需要另外瀏覽至受控的 Google Play 主控台，而且您不再需要重新驗證。  在 Intune 中，選取 [用戶端應用程式] > [應用程式] > [新增]。 在 [應用程式類型] 清單中，選取 [受控的 Google Play] 作為應用程式類型。

### <a name="device-configuration"></a>裝置設定

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>使用針對安全性基準 (公開預覽) <!-- 2055484   --> 的 Microsoft 建議設定
注意：此功能仍在推出，近期內將提供。

Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員可以直接從這些基準建立安全性政策，並將它們部署到其使用者。 您也可以自訂最佳做法建議項目，以符合您組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

若要深入了解安全性基準，請參閱[在 Intune 中建立 Windows 10 安全性基準](security-baselines-monitor.md)。

本功能適用於：Windows 10 及更新版本

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>非系統管理員可以在已加入 Azure AD 的 Windows 10 裝置上啟用 BitLocker<!-- 2147379   -->
當您在 Windows 10 裝置上啟用 BitLocker 設定 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [Endpoint Protection] > [Windows 加密]) 時，您會新增 BitLocker 設定。 

此更新包含新的 BitLocker 設定，可允許標準使用者 (非系統管理員) 啟用加密。 

若要查看設定，請前往[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>檢查 Configuration Manager 合規性 <!-- 2192052  eepublished  -->
此更新會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10 及更新版本] > [Configuration Manager 合規性])。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用此設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中就不會符合規範。

[Configuration Manager 合規性](compliance-policy-create-windows.md#configuration-manager-compliance)描述了這項設定。

適用於：Windows 10 及更新版本

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>使用裝置組態設定檔自訂受監督 iOS 裝置上的背景圖案 <!-- 2809324   -->
當您建立 iOS 裝置的裝置組態設定檔時，您可以自訂某些功能 ([裝置設定] > [設定檔] > [建立設定檔] > [iOS] 平台 > [裝置功能] 設定檔類型)。 此更新包括新的**桌布**設定，可讓系統管理員在主畫面或鎖定畫面上使用 .png、.jpg 或 .jpeg 影像。 這些桌布設定只會套用至受監督的裝置。 

如需這些設定的清單，請參閱 [iOS 裝置功能設定](ios-device-features-settings.md)。

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 kiosk 公開上市 <!-- 3594661  -->
在此更新中，在 Windows 10 和更新版本的裝置上的 [Kiosk] 功能是正式推出 (GA)。 若要查看您可以新增和設定的所有設定，請參閱[適用於 Windows 10 (和更新版本) 的 Kiosk 設定](kiosk-settings.md)。

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>[透過藍牙分享連絡人] 已從 Android Enterprise 的 [裝置限制] > [裝置擁有者] 中移除 <!-- 3598396   -->
當您建立 Android Enterprise 裝置的裝置限制設定檔時，有一項 [透過藍牙分享連絡人] 設定。 在此更新中，[透過藍牙分享連絡人] 設定會被移除 ([裝置設定] > [設定檔] > [建立設定檔] > [Android 企業] 平台 > [裝置限制] > [裝置擁有者] 設定檔類型 > [一般])。 

Android Enterprise 裝置擁有者管理不支援 [透過藍牙分享連絡人] 設定。 因此，移除此設定之後，並不會影響任何裝置或租用戶，即使您已在環境中啟用和設定此設定亦然。

若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。

適用於：Android Enterprise 裝置擁有者

#### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Intune 應用程式保護原則 UI 更新 <!-- 3251427 -->
我們已變更 Intune 應用程式保護的設定和按鈕標籤，以使它們更容易理解。 部分變更包括：  
- 控制項從 [是] / [否] 的控制項，變更成主要為 [封鎖] / [允許]****，以及 [停用] / [啟用] 的控制項。 標籤也一併更新。  
- 設定已重新格式化，因此設定和其標籤會在控制項中並排顯示，提供更好的瀏覽。   

預設設定和設定數量會保持相同，但這項變更可讓使用者更輕鬆了解、瀏覽和利用這些設定，以套用所選的應用程式保護原則。 如需詳細資訊，請參閱 [iOS 設定](app-protection-policy-settings-ios.md)和 [Android 設定](app-protection-policy-settings-android.md)。

### <a name="device-management"></a>裝置管理

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>WIP (不含註冊) 裝置的選擇性抹除支援 <!-- 1434452 -->
Windows 資訊保護 (不含註冊) (WIP-WE) 允許客戶保護其 Windows 10 裝置上的公司資料，而不需要完整的 MDM 註冊。 一旦文件受 WIP-WE 原則保護，受保護的資料就可以由 Intune 系統管理員選擇性抹除。 透過選取使用者與裝置並傳送抹除要求，透過 WIP-WE 原則保護的所有資料都會變成無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式] > [應用程式選擇性抹除]。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>新的作業記錄，以及將記錄傳送至 Azure 監視器服務的能力 <!-- 3762211  -->
Intune 具有內建稽核記錄，可在進行變更時追蹤事件。 此更新包含新的記錄功能，包括： 
- 作業記錄 (預覽)，顯示已註冊的使用者和裝置的詳細資料，包括成功和失敗的嘗試。
- 稽核記錄和作業記錄也可傳送到 Azure 監視器，包括儲存體帳戶、事件中樞和 Log Analytics。 這些服務可讓您儲存、使用 Splunk 和 QRadar 等分析，並取得記錄資料的視覺效果。

[將記錄資料傳送至 Intune 中的儲存體、事件中樞或記錄分析](review-logs-using-azure-monitor.md)提供這項功能的詳細資訊。

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>在 iOS DEP 裝置上略過更多設定助理畫面 <!-- 2687509  -->
除了您目前可以略過的畫面之外，當使用者註冊裝置時，您還可以將 iOS DEP 裝置設定為略過 [設定助理] 中的下列畫面：顯示色調、隱私權、Android 移轉、首頁按鈕、iMessage 和 FaceTime、上架、Watch 移轉、外觀、螢幕使用時間、軟體更新、SIM 卡設定。
若要選擇要略過的畫面，請前往 [裝置註冊] > [Apple 註冊] > [註冊方案權杖]> 選擇權杖 > [設定檔] > 選擇設定檔 > [屬性] > [設定助理自訂] > 針對任何您想要略過的畫面選擇 [隱藏] > [確定]。
如果您建立新的設定檔或編輯設定檔，則所選略過畫面需要與 Apple MDM 伺服器同步處理。 使用者可以發出裝置的手動同步處理，這樣在取得設定檔變更時才不會有延遲。
此功能即將推出，但需要幾天時間才可供所有客戶使用。

## <a name="week-of-january-14-2019"></a>2019 年 1 月 14 日當週

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>公司擁有、完全受控的 Android 裝置支援預覽 <!-- 1574342  -->
Intune 現在支援完全受控的 Android 裝置，此為公司擁有的「裝置擁有者」案例，其中的裝置會受到 IT 嚴格管理並隸屬於個別使用者。 這讓系統管理員能夠管理整個裝置、強制設定無法用於工作設定檔之原則控制項的延伸範圍，並限制使用者只能從受控的 Google Play 安裝應用程式。 如需詳細資訊，請參閱[設定 Android 完全受控裝置的 Intune 註冊](android-fully-managed-enroll.md)與[註冊您的專用裝置或完全受控裝置](android-dedicated-devices-fully-managed-enroll.md)。  請注意，此功能處於預覽狀態。 完全受控的 Android 使用者裝置目前不提供某些 Intune 功能，例如憑證、合規性和條件式存取。

## <a name="week-of-january-7-2019"></a>2019 年 1 月 7 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="intune-app-pin----2298397---"></a>Intune 應用程式 PIN <!-- 2298397 -->
身為 IT 系統管理員，您現在能設定終端使用者可在其 Intune 應用程式 PIN 必須變更之前等候的天數。 這項新設定稱為 [PIN reset after number of days] \(在數天後重設 PIN\)，並可在 Azure 入口網站中，藉由選取 [Intune] > [用戶端應用程式] > [應用程式防護原則] > [建立原則] > [設定] > [存取需求] 來使用。 這項功能適用於 [iOS](app-protection-policy-settings-ios.md) 和 [Android](app-protection-policy-settings-android.md) 裝置，並支援正整數值。


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 裝置報告欄位 <!-- 2748738 -->
Intune 提供其他裝置報告欄位，包括應用程式註冊識別碼、Android 製造商、型號和安全性修補程式版本，以及 iOS 型號。 在 Intune 中，您可以藉由選取 [用戶端應用程式] > [應用程式防護狀態]，然後選擇 [應用程式防護報表：iOS、Android] 來使用這些欄位。 此外，這些參數將協助您設定適用於裝置製造商 (Android) 的 [允許] 清單、適用於裝置型號 (Android 和 iOS) 的 [允許] 清單，以及最低的 Android 安全性修補程式版本設定。 


### <a name="device-configuration"></a>裝置設定

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>系統管理範本目前處於公開預覽狀態且已移至它們自己的組態設定檔 <!-- 3322847 -->

Intune 中的系統管理範本 ([裝置設定] > [系統管理範本]) 目前為個人預覽版。 使用此更新：

- 系統管理範本包含約 300 個可在 Intune 中管理的設定。 這些設定先前只存在於群組原則編輯器中。
- 系統管理範本會在公開預覽版中提供。
- 系統管理範本正從 [裝置設定] > [系統管理範本] 移至 [裝置設定] > [設定檔] > [建立設定檔] > 在 [平台] 中選擇 [Windows 10 及更新版本] > 在 [設定檔類型] 中選擇 [系統管理範本]。
- 報告功能已啟用

若要深入了解這項功能，請前往[設定群組原則設定的 Windows 10 範本](administrative-templates-windows.md)。

適用於：Windows 10 及更新版本

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>使用 S/MIME 加密和簽署使用者的多部裝置  <!-- 1333642 -->
此更新包括使用新匯入之憑證設定檔的 S/MIME 電子郵件加密 ([裝置設定] > [設定檔] > [建立設定檔] > 選取平台 > [PKCS imported certificate] \(PKCS 匯入的憑證\) 設定檔類型)。 在 Intune 中，您可以匯入 PFX 格式的憑證。 Intune 接著可以將這些相同的憑證提供給單一使用者所註冊的多個裝置。 這也包括：
- 原生 iOS 電子郵件設定檔支援啟用 PFX 格式之已匯入憑證的 S/MIME 加密。
- Windows Phone 10 裝置上的原生郵件應用程式會自動使用 S/MIME 憑證。
- 私人憑證可以跨多個平台提供。 但並非所有電子郵件應用程式都支援 S/MIME。
- 在其他平台上，您可能需要手動設定郵件應用程式來啟用 S/MIME。  
- 支援 S/MIME 加密的電子郵件應用程式可能會以 MDM 無法支援的方式來處理 S/MIME 電子郵件加密的憑證擷取 (例如從其發行者的憑證存放區中讀取)。
如需這項功能的詳細資訊，請參閱 [S/MIME 電子郵件簽署和加密概觀](certificates-s-mime-encryption-sign.md)。
支援於：Windows、Windows Phone 10、macOS、iOS、Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>在 Windows 10 及更新版裝置上使用 DNS 設定時自動連線且持續規則的新選項 <!-- 1333665, 2999078 -->
在 Windows 10 及更新版本裝置上，您可以建立 VPN 組態設定檔，其中包含可用以解析網域 (例如 contoso.com) 的 DNS 伺服器清單。 此更新包含可用於名稱解析的新設定 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [VPN] > [DNS 設定] >[新增])： 
- **自動連線**：若**已啟用**，裝置就會在連絡您輸入的網域 (例如 contoso.com) 時，自動連線至 VPN。
- **永續性**：根據預設，只要裝置會使用此 VPN 設定檔進行連線，所有的名稱解析原則表格 (NRPT) 規則都會處於作用中狀態。 已在 NRPT 規則上**啟用**此設定時，此規則就會在裝置上維持作用中狀態，即使在 VPN 中斷連線時也一樣。 規則將一直保留，直到移除 VPN 設定檔，或以手動方式移除規則，這可以透過使用 PowerShell 完成。
[Windows 10 VPN 設定](vpn-settings-windows-10.md)將描述這些設定。 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>針對 Windows 10 裝置上的 VPN 設定檔使用受信任的網路偵測 <!-- 1500165 -->
使用受信任的網路偵測時，若使用者已經位於受信任的網路上，您可以防止 VPN 設定檔自動建立 VPN 連線。 在此更新中，您可以新增 DNS 尾碼，在執行 Windows 10 及更新版本之裝置上啟用受信任的網路偵測 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [VPN])。
[Windows 10 VPN 設定](vpn-settings-windows-10.md)會列出目前的 VPN 設定。

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>管理多位使用者所使用的 Windows Holographic for Business 裝置 <!-- 1907917, 1063203 -->
您目前可以使用自訂的 OMA-URI 設定，在 Windows 10 和 Windows Holographic for Business 裝置上設定共用的電腦設定。 在此更新中，會新增設定檔來設定共用的裝置設定 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] > [共用的多重使用者裝置])。
若要深入了解這項功能，請前往[管理共用裝置的 Intune 設定](shared-user-device-settings.md)。
適用於：Windows 10 及更新版本、Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>新的 Windows 10 更新設定 <!--2626030  2512994  -->
針對 [Windows 10 更新通道](windows-update-for-business-configure.md)，您可以設定：
- **自動更新行為** - 使用新選項 [重設為預設]，在執行「2018 年 10 月更新」的 Windows 10 電腦上還原原始的自動更新設定
- **防止使用者暫停 Windows 更新** - 設定新的軟體更新設定，可讓您封鎖或允許使用者從其電腦的 [設定] 暫停更新安裝。 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 電子郵件設定檔可以使用 S/MIME 簽署和加密 <!-- 2662949 -->
您可以建立包含不同設定的電子郵件設定檔。 此更新包含可在 iOS 裝置上用來簽署與加密電子郵件通訊的 S/MIME 設定 ([裝置設定] > [設定檔] > [建立設定檔]> 針對平台選擇 [iOS] > 針對設定檔類型選擇 [電子郵件])。
[iOS 電子郵件組態設定](email-settings-ios.md)會列出這些設定。

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>部分 BitLocker 設定支援 Windows 10 專業版<!-- 2727036 -->
您可以建立組態設定檔，在 Windows 10 裝置上設定 Endpoint Protection 設定，包括 BitLocker。 此更新會針對部分 BitLocker 設定新增對 Windows 10 專業版的支援。 若要查看這些保護設定，請前往[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>共用裝置設定已在 Azure 入口網站中針對 iOS 裝置重新命名為鎖定畫面訊息<!-- 2809362 -->
當您建立適用於 iOS 裝置的組態設定檔時，您可以新增 [共用裝置設定] 設定，以便在鎖定畫面上顯示特定的文字。 此更新包含下列變更： 
- Azure 入口網站中的 [共用裝置設定] 已重新命名為「鎖定畫面訊息 (僅限受監督)」([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [iOS] > 針對設定檔類型選擇 [裝置功能] > [鎖定畫面訊息])。
- 新增鎖定畫面訊息時，您可以在 [資產標籤資訊] 和 [鎖定畫面註腳] 中插入序號、裝置名稱或另一個裝置特定的值以作為變數。 例如，您可以使用大括號來輸入 `Device name: {{devicename}}` 或 `Serial number is {{serialnumber}}`。 [iOS 權杖](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)會列出可使用的可用權杖。
[在鎖定畫面上顯示訊息的設定](shared-device-settings-ios.md)會列出這些設定。

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>新增至 iOS 裝置的新 App Store、文件檢視、遊戲裝置限制設定 <!-- 2827760-->
在 [裝置設定] > [設定檔] > [建立設定檔] > [iOS] 平台 > [裝置限制] 設定檔類型 > [App Store、文件檢視、遊戲] 中，新增下列設定：[允許受控應用程式將連絡人寫入非受控連絡人帳戶]、[允許非受控應用程式從受控連絡人帳戶讀取]。若要查看這些設定，請前往 [iOS 裝置限制](device-restrictions-ios.md#app-store-doc-viewing-gaming)。

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>將通知、提示和 Keyguard 設定新增至 Android 企業裝置擁有者裝置 <!-- 3201839 3201843 -->
以裝置擁有者身分執行時，此更新會包括 Android 企業裝置上的多個新功能。 若要使用這些功能，請前往 [裝置設定] > [設定檔] > [建立設定檔] > 在 [平台] 中選擇 [Android 企業] > 在 [設定檔類型] 中選擇 [僅限裝置擁有者] > [裝置限制]。
新功能包括： 
- 停用系統通知顯示，包括來電、系統警示、系統錯誤及更多功能
- 建議針對第一次開啟的應用程式略過開始教學課程和提示
- 停用進階的 Keyguard 設定，例如相機、通知、指紋解除鎖定及更多功能。若要查看這些設定，請前往 [Android Enterprise 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android 企業裝置擁有者裝置可以使用 Always On VPN 連線 <!-- 3202194 -->
在此更新中，您可以在 Android 企業裝置擁有者裝置上使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Android 企業] > 針對 [僅限裝置擁有者] 選擇 [裝置限制] > [連線能力] 設定中啟用 Always-On VPN。 若要查看這些設定，請前往 [Android Enterprise 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 裝置上的工作管理員中用來結束處理序的新設定 <!-- 3285177 --> 
此更新包含使用 Windows 10 裝置上的工作管理員來結束處理序的新設定。 您可以使用裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > 在 [平台] 中選擇 [Windows 10] > 在 [設定檔類型] 中選擇 [裝置限制] > [一般] 設定)，來選擇允許或阻止此設定。
若要查看這些設定，請前往 [Windows 10 裝置限制設定](device-restrictions-windows-10.md)。
適用於：Windows 10 及更新版本


### <a name="device-enrollment"></a>裝置註冊

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>更詳細的註冊限制失敗訊息 <!-- 3111564 -->
不符合註冊限制時，會提供更詳細的錯誤訊息。 若要查看這些訊息，請前往 [Intune] > [疑難排解] > 然後檢查 [註冊失敗] 表格。 如需詳細資訊，請參閱[註冊失敗清單](help-desk-operators.md#configuration-policies-reference)。



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
您可以建立範圍標籤，限制對角色和應用程式的存取。 您可以將範圍標籤新增至應用程式，僅限具有角色並同時獲派該範圍標籤的人員才能存取應用程式。 無法為使用 Apple 大量採購方案 (VPP) 購買的應用程式指派範圍標籤。  如需詳細資訊，請參閱[使用範圍標籤篩選原則](scope-tags.md)。



## <a name="week-of-december-10-2018"></a>2018 年 12 月 10 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="updates-for-application-transport-security----748318---"></a>更新 Application Transport Security <!-- 748318 -->

Microsoft Intune 支援傳輸層安全性 (TLS) 1.2+ 來提供業界領先的加密功能，以確保 Intune 預設更安全，並可搭配 Microsoft Office 365 等其他 Microsoft 服務使用。 為了符合此需求，iOS 和 macOS 公司入口網站將會強制執行 Apple 的更新 Application Transport Security (ATS) 需求，這些需求也要求使用 TLS 1.2+。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 和 macOS 公司入口網站應用程式的 Intune 客戶。 如需詳細資訊，請參閱 [Intune 支援小組部落格](https://aka.ms/compportalats) \(英文\)。

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 將支援 256 位元的加密金鑰 <!-- 1832174 -->
適用於 Android 的 Intune App SDK 現在會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 SDK 將繼續提供 128 位元金鑰的支援，以取得與使用較舊 SDK 版本之內容和應用程式的相容性。

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>macOS 裝置 <!-- 3503442 --> 需要 Microsoft 自動更新版本 4.50
若要繼續接收公司入口網站和其他 Office 應用程式的更新，Intune 所管理的 macOS 裝置必須先升級到 Microsoft 自動更新 4.5.0。 使用者可能已經擁有此版本的 Office 應用程式。

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune 需要 macOS 10.12 或更新版本 <!-- 2827778 -->
Intune 現在需要 macOS 版本 10.12 或更新版本。 使用先前的 macOS 版本的裝置無法使用公司入口網站來註冊 Intune。 為了收到支援協助和新功能，使用者必須將其裝置升級至 macOS 10.12 或更新版本，並將公司入口網站升級至最新版本。

## <a name="week-of-november-26-2018"></a>2018 年 11 月 26 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>在公司擁有的受監督 iOS 裝置上解除安裝應用程式 <!-- 1281677 -->

您可以移除公司所擁有之受監督 iOS 裝置上的任何應用程式。 您可以透過針對具有**解除安裝**指派類型的使用者或裝置群組，來移除任何應用程式。 針對個人或不受監督的 iOS 裝置，您仍可以僅移除使用 Intune 安裝的應用程式。

#### <a name="downloading-intune-win32-app-content----2617320---"></a>下載 Intune Win32 應用程式內容 <!-- 2617320 -->
Windows 10 RS3 和更新版本的用戶端，將會使用 Windows 10 用戶端上的「傳遞最佳化」元件來下載 Intune Win32 應用程式內容。 傳遞最佳化能提供預設開啟的點對點功能。 傳遞最佳化可以由群組原則進行設定，在未來也將能透過 Intune MDM 進行設定。 如需詳細資訊，請參閱[適用於 Windows 10 的傳遞最佳化](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization) \(部分機器翻譯\)。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>終端使用者裝置和應用程式操作功能表 <!-- 2771453 -->
終端使用者現在可以在裝置和應用程式上使用操作功能表，以觸發重新命名裝置或檢查合規性等常見動作。

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>在受控主畫面應用程式中設定自訂背景 <!-- 3041945 -->
我們將新增一項設定，可讓您在 Android Enterprise、多應用程式、kiosk 模式裝置上自訂受控主畫面應用程式的背景外觀。  若要設定**自訂 URL 背景**，請前往 Azure 入口網站 > [裝置設定] 中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](device-restrictions-android-for-work.md)。

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>會儲存並套用應用程式保護原則指派 <!-- 3104570 -->
您將可以更有效控制[應用程式保護原則指派](app-protection-policies.md#deploy-a-policy-to-users)。 當您選取 [指派] 以設定或編輯某個原則的指派時，您必須先 [儲存] 設定，系統才會套用變更。 使用 [捨棄] 來清除您所做的所有變更，而不將任何變更儲存到包含或排除清單。  透過要求使用者進行 [儲存] 或 [捨棄]，將能確保系統只會將應用程式保護原則指派給您想要的使用者。

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>適用於 Windows 10 及更新版本的新 Microsoft Edge 瀏覽器設定 <!-- 3174639 -->
此更新將會包含新的設定，以協助您控制和管理裝置上的 Microsoft Edge 瀏覽器。 如需這些設定的清單，請參閱[適用於 Windows 10 (及更新版本) 的裝置限制](device-restrictions-windows-10.md#microsoft-edge-browser)。

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>搭配應用程式保護原則的新應用程式支援 <!-- 3330037 -->
您現在可以搭配 [Intune 應用程式保護原則](app-protection-policies.md)管理下列應用程式：
- Stream (iOS)
- To DO (Android、iOS)
- PowerApps (Android、iOS)
- Flow (Android、iOS)

使用應用程式保護原則來保護公司資料，並以和其他 Intune 原則受管理的應用程式相同的方式控制這些應用程式的資料傳輸。 注意：如果 Flow 在主控台中尚不可見，您可在建立或編輯應用程式保護原則時新增 Flow。 若要這麼做，請使用 [+ 更多應用程式] 選項，然後在輸入欄位中指定 Flow 的 [應用程式識別碼]。 針對 Android，請使用 *com.microsoft.flow*，而針對 iOS 則請使用 *com.microsoft.procsimo*。


### <a name="device-configuration"></a>裝置設定

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>顯示 iOS 和 macOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性] > [裝置合規性] 中，會顯示 iOS 和 macOS 作業系統版本，並可用於合規性政策。 此更新包含可同時針對兩個平台設定的組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 藉由在合規性政策中使用組建編號，即可輕鬆地檢查是否已安裝弱點更新。
若要使用此功能，請參閱 [iOS](compliance-policy-create-ios.md#device-health) 和 [macOS](compliance-policy-create-mac-os.md#device-properties) 合規性原則。

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>針對 Windows 10 和更新版本，更新通道將由傳遞最佳化設定取代 <!-- 2753807 -->
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
您現在可以依序號搜尋 Autopilot 裝置。 若要這麼做，請選擇 [裝置註冊] > [Windows 註冊] > [裝置] > 在 [依序號搜尋] 方塊中輸入序號 > 按 Enter。

#### <a name="track-installation-of-office-proplus---2620217---"></a>追蹤 Office 專業增強版的安裝 <!--2620217 -->
使用者可以使用[註冊狀態頁面](windows-enrollment-status.md)來追蹤 [Office 專業增強版](apps-add-office365.md)的安裝進度。 如需詳細資訊，請參閱[設定註冊狀態頁面](windows-enrollment-status.md)。

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Apple School Manager 帳戶的 macOS 裝置註冊計劃 <!--3006133 -->
Intune 現已支援在適用於 Apple School Manager 帳戶的 macOS 裝置上使用裝置註冊計劃。  如需詳細資訊，請參閱[使用 Apple School Manager 或裝置註冊計劃來自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)。

### <a name="new-intune-device-subscription-sku---3312071--"></a>新的 Intune 裝置訂閱 SKU <!--3312071-->
為了協助降低企業中的裝置管理裝置成本，現在提供新的裝置型訂閱 SKU。 此 Intune 裝置 SKU 是依每月每部裝置來授權。 價格會因授權方案而有所不同。 它可直接透過 Office 管理入口網站、[Enterprise 合約](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2) (EA)、[Microsoft 產品和服務合約](https://www.microsoft.com/licensing/mpsa/default) (MPSA)，[Microsoft Open Agreement](https://partner.microsoft.com/licensing/licensing-agreements) 和[雲端解決方案提供者](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453) (CSP) 提供使用。

### <a name="device-management"></a>裝置管理

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>暫時暫停 Android 裝置上的 kiosk 模式以進行變更 <!-- 3041935 -->
在多應用程式 kiosk 模式下使用 Android 裝置時，IT 系統管理員可能需要對裝置進行變更。 此更新包含新的多應用程式 kiosk 設定，允許 IT 系統管理員使用 PIN 暫時暫停 kiosk 模式，並存取整個裝置。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](device-restrictions-android-for-work.md)。

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>啟用 Android Enterprise kiosk 裝置上的虛擬首頁按鈕 <!-- 3042021 -->
新設定可讓使用者點選其裝置上的螢幕按鍵按鈕，以在其多應用程式 kiok 裝置上的受控主畫面應用程式和其他已指派應用程式之間切換。 在使用者的 kiosk 應用程式未對「返回」按鈕做出適當回應情況下，此設定特別有用。 您將能夠為公司擁有的一次性 Android 裝置設定此設定。 若要啟用或停用**虛擬首頁按鈕**，請前往 Azure 入口網站 > 裝置設定中的 Intune。 選取目前或建立一個新的裝置組態設定檔，來編輯其 kiosk 設定。
若要查看 kiosk 設定，請參閱 [Android Enterprise 裝置限制](device-restrictions-android-for-work.md)。

## <a name="week-of-november-12-2018"></a>2018 年 11 月 12 日當週

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>網路存取控制 (NAC) 針對 iOS 支援 Citrix SSO <!-- 3259404 -->

Citrix 已發行 Citrix Gateway 更新以允許 Intune 中 iOS 的 Citrix SSO 的網路存取控制 (NAC)。 您可以在 Intune 中選擇在 VPN 設定檔中包括裝置識別碼，然後將此設定檔推送到您的 iOS 裝置。 您將必須安裝最新的更新到 Citrix Gateway，才能使用此功能。

[在 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md#base-vpn-settings)提供有關使用 NAC 的詳細資訊，包括一些額外需求。 

## <a name="week-of-november-5-2018"></a>2018 年 11 月 5 日當週

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>在 iOS 電子郵件設定檔中支援 iOS 12 OAuth <!--2155106 -->

Intune 的 iOS 電子郵件設定檔支援 iOS 12 Open Authorization (OAuth)。 若要查看此功能，請建立新的設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [iOS] 作為平台 > [電子郵件] 作為設定檔類型)，或更新現有的 iOS 電子郵件設定檔。 如果您在已部署給使用者的設定檔中啟用 OAuth，則會提示使用者重新驗證，並再次下載其電子郵件。

[iOS 電子郵件設定檔](email-settings-ios.md)會包含有關在電子郵件設定檔中使用 OAuth 的詳細資訊。

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>混合式 Azure Active Directory 聯結裝置的 Autopilot 支援 (預覽) <!-- 1048100-->
您現在可以透過使用 Autopilot，來設定混合式 Azure Active Directory 聯結裝置。 裝置必須聯結到您組織的網路，才能使用混合式 Autopilot 功能。 如需詳細資訊，請參閱[使用 Intune 和 Windows Autopilot 部署混合式 Azure AD 聯結裝置](windows-autopilot-hybrid.md)。
此功能將在未來幾天內在整個使用者群中推出。 因此，在推出至您的帳戶之前，您可能無法執行這些步驟。

## <a name="week-of-october-29-2018"></a>2018 年 10 月 29 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>在指定的逾時之後要求非生物特徵辨識 PIN <!-- 1506985 -->
透過在系統管理員指定的逾時之後要求非生物特徵辨識 PIN，Intune 可藉由限制使用生物特徵辨識身分識別來存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法，來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置，可能會向不正確使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [用戶端應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。 如需存取設定的資訊，請參閱 [iOS 設定](app-protection-policy-settings-ios.md#access-settings)和 [Android 設定](app-protection-policy-settings-android.md#access-settings)。

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>已註冊 MDM 之 iOS 裝置上的 Intune 應用程式資料轉送設定 <!-- 2244713 -->
您可以將已註冊 iOS MDM 裝置上 Intune 應用程式資料轉送設定的控制，與指定已註冊使用者的身分識別 (也稱為使用者主體名稱 (UPN)) 區分開來。 不使用 IntuneMAMUPN 的系統管理員將不會發現行為變更。 當此功能可用時，使用 IntuneMAMUPN 來控制已註冊裝置上資料轉送行為的系統管理員，應檢閱新的設定並視需要更新其應用程式設定。

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 應用程式 <!-- 2617325 -->
您可以設定 Win32 應用程式在個別 使用者的使用者內容中安裝，而不是為裝置的所有使用者安裝應用程式。

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 應用程式和 PowerShell 指令碼 <!-- 2617330 -->
終端使用者已不再需要登入裝置來安裝 Win32 應用程式或執行 PowerShell 指令碼。 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>針對用戶端應用程式安裝進行疑難排解 <!-- 1363711 -->
您可以藉由檢閱 [疑難排解] 刀鋒視窗中標示為 [應用程式安裝] 的資料行，來為用戶端應用程式的安裝成功問題進行疑難排解。 若要檢視 [疑難排解] 刀鋒視窗，請在 Intune 入口網站中的 [說明及支援] 下選取 [疑難排解]。

### <a name="device-configuration"></a>裝置設定

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>iOS VPN 用戶端上的網路存取控制支援 <!-- 1333693 -->
透過此更新，您可以在為 Cisco AnyConnect、F5 Access 和 Citrix SSO for iOS 建立 VPN 設定檔時啟用網路存取控制 (NAC)。 此設定可讓裝置的 NAC 識別碼包含在 VPN 設定檔中。 目前尚沒有任何支援此新 NAC 識別碼的 VPN 用戶端或 NAC 合作夥伴解決方案；當提供支援時，我們將透過[支援部落格文章](ttps://aka.ms/iOS12_and_vpn)通知您。

若要使用 NAC，您將需要：
1. 選擇允許 Intune 在 VPN 設定檔中包含裝置識別碼
2. 更新您的 NAC 提供者軟體/韌體，直接從您的 NAC 提供者使用指導方針

如需 iOS VPN 設定檔中此設定的相關資訊，請參閱[在 Microsoft Intune 中的 iOS 裝置上新增 VPN 設定](vpn-settings-ios.md)。 如需網路存取控制的詳細資訊，請參閱[搭配 Intune 的網路存取控制 (NAC) 整合](network-access-control-integrate.md)。 

適用於：iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>從裝置移除電子郵件設定檔，即使只有一個電子郵件設定檔也一樣 <!-- 1818139 -->
之前，「如果」這是唯一的電子郵件設定檔，則無法從裝置移除電子郵件設定檔。 在此更新中，此行為會有所變更。 現在，您可以移除電子郵件設定檔，即使裝置上只有一個電子郵件設定檔也一樣。 如需詳細資訊，請參閱[使用 Intune 將電子郵件設定新增至裝置](email-settings-configure.md)。

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell 指令碼和 AAD <!-- 2309469 -->
Intune 中的 PowerShell 指令碼可以鎖定至 AAD 裝置安全性群組。

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>適用於 Android、Android Enterprise 的新「必要密碼類型」預設設定 <!-- 2649963 -->
當您建立新的合規性原則 (針對 [平台] > [系統安全性]，選擇 [Intune] > [裝置合規性] > [原則] > [建立原則] > [Android] 或 [Android Enterprise]) 時，[必要密碼類型] 的預設值會變更：

從：裝置預設為：至少包含數字

適用於：Android、Android Enterprise

若要查看這些設定，請瀏覽 [Android](compliance-policy-create-android.md) 和 [Android Enterprise](compliance-policy-create-android-for-work.md)。

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 設定檔中使用預先共用金鑰 <!-- 2662938 -->
透過此更新，您可以搭配 WPA/WPA2-Personal 安全性通訊協定使用預先共用金鑰 (PSK)，來驗證適用於 Windows 10 的 Wi-Fi 組態設定檔。 您也可以在Windows 10 2018 年 10 月更新中，為裝置指定計量付費網路的成本設定。

目前您必須匯入 Wi-Fi 設定檔或是建立自訂的設定檔，才能使用預先共用金鑰。 [適用於 Windows 10 的 Wi-Fi 設定](wi-fi-settings-windows.md)列出目前的設定。 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>從您的裝置移除 PKCS 和 SCEP 憑證 <!-- 3218390 -->
在某些案例中，PKCS 和 SCEP 憑證會保留在裝置上，即使從群組中移除原則、刪除設定或合規性部署，或是系統管理員更新現有的 SCEP 或 PKCS 設定檔也一樣。 此更新會變更該行為。 在某些案例中，PKCS 和 SCEP 憑證會從裝置移除；在某些案例中，這些憑證會保留在裝置上。 請參閱[在 Microsoft Intune 中移除 SCEP 和 PKCS 憑證](remove-certificates.md)以了解這些案例。

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>在 macOS 裝置上使用閘道管理員以遵循合規性 <!-- 2504381 -->
此更新包括 macOS 閘道管理員，用於評估裝置合規性。 若要設定閘道管理員屬性，請[為 macOS 裝置新增裝置合規性政策](compliance-policy-create-mac-os.md)。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="enrollment-abandonment-report----1382924---"></a>註冊放棄報表 <!-- 1382924 -->
您可以在 [裝置註冊] > [監視] 下取得新報表，提供已放棄註冊的詳細資料。 如需詳細資訊，請參閱[公司入口網站放棄報表](enrollment-report-company-portal-abandon.md)。

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

#### <a name="intune-app-protection-policies----2984657---"></a>Inunte 應用程式保護原則 <!-- 2984657 -->
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


## <a name="week-of-october-15-2018"></a>2018 年 10 月 15 日當週

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>當您變更 iOS 裝置上的指紋或 Face ID 時會收到提示必須輸入 PIN <!-- 2637704  -->
現在，當使用者在其 iOS 裝置上進行生物特徵辨識變更之後，會收到輸入 PIN 的提示。 這包括變更已註冊的指紋或 Face ID。 提示時間取決於 [重新檢查存取需求前的剩餘時間 (分鐘)] 逾時的設定方式。  若未設定任何 PIN，則系統會提示使用者設定一個。 
 
此功能僅適用於 iOS，並需要整合 Intune APP SDK for iOS 9.0.1 版或更新版本的應用程式參與。 您必須整合此 SDK，才能針對目標應用程式強制執行該行為。 這項整合會輪流發生並取決於特定的應用程式小組。 參與的一些應用程式包括 WXP、Outlook、Managed Browser 和 Yammer。


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
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune] > [用戶端應用程式] > [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗的 [應用程式類型] 清單中，選取 [Office 365 套件] 下的 [Windows 10]。 選取 [應用程式套件設定] 刀鋒視窗中的 [語言]。

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows 企業營運 (LOB) 應用程式副檔名 <!-- 1884873 -->
Windows LOB 應用程式的附檔名現在包含 *.msi*、*.appx*、*.appxbundle*、*.msix* 和 *.msixbundle*。 您可以依序選取 [用戶端應用程式] > [應用程式] > [新增]，在 Microsoft Intune 中新增應用程式。 隨即顯示 [新增應用程式] 窗格，讓您可以選取 [應用程式類型]。 針對 Windows LOB 應用程式，選取 [企業營運] 應用程式作為應用程式類型，並選取 [應用程式套件檔案]，然後輸入具有適當副檔名的安裝檔。

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>使用 Intune 進行 Windows 10 應用程式部署 <!-- 2309001 -->
以企業營運 (LOB) 應用程式和商務用 Microsoft Store 應用程式的現有支援為基礎，系統管理員可以使用 Intune 將其組織的大部分現有應用程式部署到 Windows 10 裝置上的終端使用者。 系統管理員可以使用各種格式 (例如 MSI、Setup.exe 或 MSP)，為 Windows 10 的使用者新增、安裝及解除安裝應用程式。 Intune 會在下載和安裝之前評估需求規則，並使用 Windows 10 控制中心通知終端使用者狀態或重新開機需求。 這項功能會有效率地解除封鎖想要將此工作負載轉移到 Intune 和雲端的組織。 這項功能目前處於公開預覽狀態，我們預期在接下來的幾個月內在該功能中新增重要的新功能。 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>終端使用者裝置和應用程式操作功能表 <!-- 2771453 -->
終端使用者現在可以使用裝置和應用程式上的操作功能表來觸發常見動作，例如重新命名裝置或檢查合規性。 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 公司入口網站鍵盤快速鍵 <!-- 2771518 -->
終端使用者現在能夠於 Windows 公司入口網站中使用鍵盤快速鍵觸發程序應用程式和裝置動作。

### <a name="device-configuration"></a>裝置設定

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>在執行 Windows 10 的裝置上於 VPN 組態設定檔中建立 DNS 尾碼 <!-- 1333668 -->
當您建立 VPN 裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] 平台 > [VPN] 設定檔類型) 時，您需要輸入一些 DNS 設定。 透過此更新，您也可以在 Intune 中輸入多個 **DNS 尾碼**。 使用 DNS 尾碼時，您可以使用其簡短名稱來搜尋網路資源，而不需使用完整網域名稱 (FQDN)。 此更新也可讓您在 Intune 中變更 DNS 尾碼的順序。
[Windows 10 VPN 設定](vpn-settings-windows-10.md#dns-settings)列出目前的 DNS 設定。
適用於：Windows 10 裝置

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>適用於 Android 企業工作設定檔的 Always-On VPN 支援 <!-- 1333705 -->
在此更新中，您將可以在 Android 企業裝置上搭配受控的工作設定檔來使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
您可以在 [裝置設定] > [設定檔] > [建立設定檔] > [Android 企業] 平台 > [裝置限制] > [連線能力] 設定中啟用 Always-On VPN。

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>將 SCEP 憑證發給無使用者的裝置 <!-- 1744554 -->
目前憑證只能發給使用者。 透過此更新，您能夠將 SCEP 憑證發給裝置，包括 kiosk 等無使用者的裝置 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] 平台 > [SCEP 憑證] 設定檔)。 其他更新包括：
- SCEP 設定檔中的 [主體] 屬性現已是自訂的文字方塊，且可以包含新的變數。 
- SCEP設定檔中的 [主體別名 (SAN)] 屬性現已是表格格式，且可以包含新的變數。 系統管理員可以在表格中新增屬性，並在自訂的文字方塊中填入值。 SAN 將支援下列屬性： 
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
當裝置不符合規範時，您可以在合規性原則上建立從遠端鎖定該裝置的動作。 在 Intune > [裝置合規性] 中建立新原則或選取現有的原則 > [屬性]。 選取 [因不符合規範而採取的動作] > [新增]，然後選擇以從遠端鎖定裝置。
支援於： 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 和更新版本 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure 入口網站中針對 Windows 10 及更新版本 Kiosk 設定檔的改進 <!-- 2748224 -->
此更新包含下列對 Windows 10 Kiosk 裝置設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] 平台 > [Kiosk 預覽] 設定檔類型) 的改善： 
- 目前，您可以在相同的裝置上建立多個 Kiosk 設定檔。 透過此更新，Intune 針對每部裝置都只會支援單一 Kiosk 設定檔。 如果您仍需要在單一裝置上有多個 Kiosk 設定檔，則可以使用自訂 URI。
- 在 [多應用程式 kiosk] 設定檔中，您可以針對應用程式格線中的 [[開始] 功能表配置] 選取應用程式磚大小和順序。 如果您想要取得更多自訂項目，您可以繼續上傳 XML 檔案。
- [Kiosk 瀏覽器] 設定會移至 [Kiosk] 設定中。 目前，[Kiosk 網頁瀏覽器] 設定在 Azure 入口網站中具有自己的類別。
適用於：Windows 10 及更新版本




### <a name="device-enrollment"></a>裝置註冊

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置 <!-- 1558983 -->
您可以將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置。 在 Autopilot 設定檔中，選擇 [將所有目標裝置轉換為 Autopilot] 選項，以將所有非 Autopilot 的裝置自動註冊至 Autopilot 部署服務。 等候 48 小時讓註冊處理完畢。 當裝置取消註冊並重設時，Autopilot 將會自動佈建它。

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>建立並指派多個註冊狀態頁面設定檔至 Azure AD 群組 <!-- 2526564 -->
您現在可以[建立並指派](windows-enrollment-status.md)多個註冊狀態頁面設定檔至 Azure AD 群組。

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>從裝置註冊計劃移轉到 Intune 中的 Apple Business Manager <!--2748613-->
Apple Business Manager (ABM) 能在 Intune 中運作，您可以將您的帳戶從裝置註冊計劃 (DEP) 升級到 ABM。 Intune 中的程序都相同。 若要將您的 Apple 帳戶從 DEP 升級到 ABM，請前往 [https://support.apple.com/en-us/HT208817]( https://support.apple.com/en-us/HT208817)。

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>[裝置註冊概觀] 頁面上的 [警示] 和 [註冊狀態] 索引標籤 <!--2748656-->
警示和註冊失敗現在會出現在 [裝置註冊概觀] 頁面的個別索引標籤上。

### <a name="device-management"></a>裝置管理

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>限制應用程式，並封鎖存取 Android 裝置上的公司資源 <!-- 2451462  -->  
在 [裝置合規性] > [原則] > [建立原則] > [Android] > [系統安全性] 中，[裝置安全性] 區段下方有一個名為 [受限應用程式] 的新設定。 若在裝置上安裝特定應用程式，則 [受限應用程式] 設定會使用合規性原則來封鎖對公司資源的存取。 除非從裝置中移除受限制應用程式，否則會將裝置視為不符合規範。
適用於： 
- Android




## <a name="week-of-september-24-2018"></a>2018 年 9 月 24 日當週

### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Microsoft 365 裝置管理的系統管理中心 <!-- 3078424 -->
Microsoft 365 的承諾之一是簡化管理，多年來我們已整合後端的 Microsoft 365 服務來提供端對端案例，例如 Intune 和 Azure AD 條件式存取。 新的 [Microsoft 365 系統管理中心](http://devicemanagement.microsoft.com)可用來合併、簡化及整合管理體驗。 [裝置管理] 的專家工作區可讓您輕鬆地存取所有裝置和應用程式管理資訊，以及您組織需要的工作。 我們預期這會成為企業終端使用者運算小組的主要雲端工作區。

### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>支援更多的協力廠商憑證授權單位 (CA) <!-- 3093107 -->
透過使用簡單憑證註冊通訊協定 (SCEP)，您現在可以在使用 Windows、iOS、Android 和 macOS 的行動裝置上發行新憑證及更新憑證。

### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>Intune 轉為支援 iOS 10 和更新版本 <!-- 2454656 -->  
Intune 註冊、公司入口網站及受控瀏覽器現在只支援執行 iOS 10 和更新版本的 iOS 裝置。 若要檢查組織中受影響的使用者或裝置，請移至 Azure 入口網站中的 Intune > [裝置] > [所有裝置]。 依 OS進行篩選，然後按一下 [資料行] 以呈現 OS 版本詳細資料。 要求這些使用者將其裝置升級至支援的 OS 版本。  

如果您有下面列出的任何裝置，或想要註冊下面列出的任何裝置，請注意，它們只支援 iOS 9 和更早版本。  若要繼續存取 Intune 公司入口網站，您必須將這些裝置升級為支援 iOS 10 或更新版本的裝置：  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad (第 3 代) 
* iPad Mini (第 1 代)  

## <a name="week-of-september-17-2018"></a>2018 年 9 月 17 日當週

### <a name="app-management"></a>應用程式管理

### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>移除重複的應用程式保護狀態磚 <!-- 3083391 -->
[用戶端應用程式 - 概觀] 頁面以及 [用戶端應用程式 - 應用程式保護狀態] 頁面都會顯示 [iOS 使用者狀態] 和 [Android 使用者狀態] 磚。 這些狀態磚已從 [用戶端應用程式 - 概觀] 頁面中移除，以避免重複。 

## <a name="week-of-august-27-2018"></a>2018 年 8 月 27 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>自訂和 Pulse Secure 連線類型之 iOS 個別應用程式 VPN 設定檔的封包通道支援 <!-- 1520957 -->
使用 iOS 個別應用程式 VPN 設定檔時，您可以選擇使用應用程式層通道 (app-proxy) 或封包層通道 (packet-tunnel)。 下列連線類型可以使用這些選項：
- 自訂 VPN
- Pulse Secure：如果您不確定要使用的值，請參閱您 VPN 提供者的文件。

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>在裝置上顯示 iOS 軟體更新時延遲 <!-- 1949583 -->
在 [Intune] > [軟體更新] > [Update policies for iOS] \(更新 iOS 的原則\) 中，您可以設定不想要裝置安裝任何更新的日期和時間。 在未來的更新中，您可以在裝置上以可見的方式顯示軟體更新時延遲 (從 1-90 天)。 
[在 Microsoft Intune 中設定 iOS 更新原則](software-updates-ios.md)會列出目前設定。

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus 版本 <!-- 2213968 -->
使用 Intune 將 Office 365 ProPlus 應用程式指派給 Windows 10 裝置時，您將能選取 Office 版本。 在 Azure 入口網站中，選取 [Microsoft Intune] > [應用程式] > [新增應用程式]。 然後，從 [類型] 下拉式清單中選取 [Office 365 ProPlus Suite (Windows 10)]。 選取 [App Suite 設定] 以顯示相關聯的刀鋒視窗。 將 [更新通道] 設定為值 (例如 [每月])。 選擇性地選取 [是]，以從終端使用者裝置移除其他 Office (msi) 版本。 選取 [特定]，以在終端使用者裝置上安裝所選取通道的特定 Office 版本。 目前，您可以選取要使用之 Office 的 [特定版本]。 可用的版本將會隨著時間變更。 因此，建立新的部署時，可用的版本可能較新，因此沒有特定較舊版本可用。 目前部署將會繼續部署較舊的版本，但每個通道都會持續更新版本清單。 如需詳細資訊，請參閱 [Office 365 ProPlus 更新通道的概觀](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)。

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN 的註冊 DNS 設定支援 <!-- 2282852 -->
透過此更新，您可以設定 Windows 10 VPN 設定檔，動態註冊指派給具有內部 DNS 之 VPN 介面的 IP 位址，而不需要使用自訂設定檔。
如需目前可用之 VPN 設定檔設定的資訊，請參閱 [Windows 10 VPN 設定](vpn-settings-windows-10.md)。 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>macOS 公司入口網站安裝程式現在會在安裝程式檔案名稱中包含版本號碼 <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>iOS 自動應用程式更新 <!-- 2729759 -->
自動應用程式更新適用於 iOS 11.0 版和更新版本的裝置和使用者授權應用程式。




### <a name="device-configuration"></a>裝置設定

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello 是以使用者和裝置為目標 <!-- 1106609 -->
當您建立 [Windows Hello 企業版](windows-hello.md)原則時，該原則會套用至組織 (整個租用戶) 內的所有使用者。 使用此更新，也可以使用裝置設定原則將該原則套用至特定使用者或特定裝置 ([裝置設定] > [設定檔] > [建立設定檔] > [Identity Protection] > [Windows Hello 企業版])。
在 Azure 入口網站的 Intune 中，Windows Hello 設定現在會存在於 [裝置註冊] 和 [裝置設定] 中。 [裝置註冊] 以整個組織 (整個租用戶) 為目標，並支援 Windows AutoPilot (OOBE)。 [裝置設定] 以使用在簽入期間所套用原則的裝置和使用者為目標。
本功能適用於：  
- Windows 10 及更新版本
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler 是 iOS 上 VPN 設定檔的可用連線 <!-- 1769858 -->
當您建立 iOS VPN 裝置設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [iOS] 平台 > [VPN] 設定檔類型) 時，有數種連線類型 (包括 Cisco、Citrix 等等)。 此更新會將 Zscaler 新增為連線類型。 
[執行 iOS 之裝置的 VPN 設定](vpn-settings-ios.md)列出可用的連線類型。

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>適用於 Windows 10 之企業 Wi-Fi 設定檔的 FIPS 模式 <!-- 1879077 -->
您現在可以在 Intune Azure 入口網站中，啟用適用於 Windows 10 之企業 Wi-Fi 設定檔的美國聯邦資訊處理標準 (FIPS) 模式。 如果您在 Wi-Fi 設定檔中啟用 FIPS 模式，也請務必在您的 Wi-Fi 基礎結構中啟用。
[Intune 中適用於 Windows 10 和更新版本之裝置的 Wi-Fi 設定](wi-fi-settings-windows.md)說明如何建立 Wi-Fi 設定檔。

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 及更新版本之裝置上的控制 S 模式 - 公開預覽 <!-- 1958649 -->
透過此功能更新，您可以建立裝置組態設定檔以將 Windows 10 裝置切換出 S 模式，或防止使用者將裝置切換出 S 模式。 此功能位於 Intune > [裝置設定] > [設定檔] >  [Windows 10 and later] \(Windows 10 及更新版本\) > [Edition upgrade and mode switch] \(版本升級和模式切換\) 中。
[引進 Windows 10 S 模式](https://www.microsoft.com/windows/s-mode)提供 S 模式的詳細資訊。
適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。


#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Windows Defender ATP 設定套件會自動新增至組態設定檔 <!-- 2144658 -->
在 Intune 中使用[進階威脅防護和上線](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile)裝置時，您必須先下載設定套件，並將之新增至組態設定檔。 透過此更新，Intune 會從 Windows Defender 資訊安全中心自動取得套件，並將之新增至設定檔。
適用於 Windows 10 及更新版本。

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>要求使用者在裝置設定期間連線 <!--2311457-->
您現在可以設定裝置設定檔，要求裝置連線到網路，再繼續進行 Windows 10 安裝期間的 [網路] 頁面。 此功能尚在預覽階段，需要 Windows 測試人員組建 1809 或更新版本才能使用這項設定。
適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。


#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>限制應用程式，並封鎖存取 iOS 和 Android Enterprise 裝置上的公司資源 <!-- 2451462 -->
在 [裝置合規性] > [原則] > [建立原則] > [iOS] > [系統安全性] 中，會有新的 [Restricted applications] \(受限制的應用程式\) 設定。 如果在裝置上安裝特定應用程式，則這個新的設定會使用合規性原則來封鎖對公司資源的存取。 除非從裝置中移除受限制應用程式，否則會將裝置視為不符合規範。
適用於：iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>iOS 的新式 VPN 支援更新 <!-- 2459928, 1819876, and 2650856 -->
此更新會支援下列 iOS VPN 用戶端： 
- F5 Access (3.0.1 版和更高版本)
- Citrix SSO
- Palo Alto Networks GlobalProtect 5.0 版和更高版本另外在此更新中：
- 現有的 **F5 Access** 連線類型會重新命名為 **F5 Access Legacy** for iOS。
- 現有的 **Palo Alto Networks GlobalProtect** 連線類型會重新命名為 **Palo Alto Networks GlobalProtect (legacy)** for iOS。
具有這些連線類型的現有設定檔會持續使用其各自的舊版 VPN 用戶端。 如果您搭配 iOS 使用 Cisco Legacy AnyConnect、F5 Access Legacy、Citrix VPN 或 Palo Alto Networks GlobalProtect 4.1 版及更舊版本，您應移至新的應用程式。 請盡快這麼做，確保 iOS 裝置在更新為 iOS 12 時可以提供 VPN 存取。
如需 iOS 12 和 VPN 設定檔的詳細資訊，請參閱 [Microsoft Intune 支援小組部落格](https://go.microsoft.com/fwlink/?linkid=2013806)。

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>匯出 Azure 傳統入口網站合規性政策，在 Intune Azure 入口網站中重新建立這些政策 <!-- 2469637 -->
將會取代在 Azure 傳統入口網站中建立的合規性原則。 您可檢閱及刪除任何現有的合規性政策，但無法加以更新。 若需要將任一合規性政策移轉至目前的 Intune Azure 入口網站，可以用逗號分隔的檔案 (*.csv* 檔案) 匯出政策。 然後，使用檔案中的詳細資料，在 Intune Azure 入口網站中，重新建立這些政策。

> [!IMPORTANT]
> Azure 傳統入口網站淘汰之後，您將無法再存取或檢視合規性政策。 因此，請務必在淘汰 Azure 傳統入口網站之前，先匯出您的政策，然後於 Azure 入口網站中重新建立。

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>Better Mobile - 新的 Mobile Threat Defense 夥伴 <!-- 22662717 -->
您可以根據由 Better Mobile (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>除非使用者登入，否則會以單一應用程式模式鎖定公司入口網站 <!--1067692 --> 
如果您在 DEP 註冊期間透過公司入口網站 (而非設定助理) 驗證使用者，您現在可以選擇以單一應用程式模式執行公司入口網站。 此選項會在設定助理完成之後立即鎖定裝置，讓使用者必須登入才能存取裝置。 此程序可確保裝置完成上架，而且在處於沒有任何使用者繫結的狀態下未遭到遺棄。

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>將使用者和易記名稱指派給 AutoPilot 裝置 <!--1346521 -->
您現在可以[將使用者指派給單一 Autopilot 裝置](enrollment-autopilot.md)。 系統管理員也可以提供易記名稱，以在使用 Autopilot 設定其裝置時歡迎使用者。
適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 註冊期間，使用 VPP 裝置授權預先佈建公司入口網站 <!-- 1608345 -->
您現在可以於裝置註冊計劃 (DEP) 註冊期間，使用大量採購方案 (VPP) 裝置授權預先佈建公司入口網站。 若要這麼做，當您[建立或編輯註冊設定檔時](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)，請指定您要用來安裝公司入口網站的 VPP 權杖。 請確定您的權杖未過期，而且您有足夠的公司入口網站應用程式權限。 如果權杖過期或授權不足，則 Intune會改為推送 App Store 公司入口網站 (這會提示您輸入 Apple 識別碼)。

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要確認刪除將用於預先佈建公司入口網站的 VPP 權杖 <!-- 2237634 -->
如果在 DEP 註冊期間將使用大量採購方案 (VPP) 權杖來預先佈建公司入口網站，則需要確認刪除該權杖。

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>封鎖 Windows 個人裝置註冊 <!-- 1849498 -->
您可以在 Intune 中[封鎖 Windows 個人裝置](enrollment-restrictions-set.md#set-device-type-restrictions)註冊[行動裝置管理](windows-enroll.md)。 使用此功能無法封鎖使用 [Intune PC 代理程式](manage-windows-pcs-with-microsoft-intune.md)所註冊的裝置。 此功能會在未來幾週推出，因此您在使用者介面中可能不會立即看到它。

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>在 AutoPIlot 設定檔中指定電腦名稱模式 <!--1849855-->
您可以[指定電腦名稱範本](enrollment-autopilot.md#create-an-autopilot-deployment-profile)，以在 AutoPilot 註冊期間產生並設定[電腦名稱](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)。 適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。


#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>針對 Windows AutoPilot 設定檔，隱藏公司登入頁面和網域錯誤頁面上的變更帳戶選項 <!--1901669 -->
[新增 Windows AutoPilot 設定檔選項](enrollment-autopilot.md#create-an-autopilot-deployment-profile)，讓管理員隱藏公司登入和網域錯誤頁面上的變更帳戶選項。 隱藏這些選項需要在 Azure Active Directory 中設定公司商標。 適用於：最新的 [Windows 測試人員](https://docs.microsoft.com/windows-insider/at-work-pro/)組建 (目前為預覽版)。



### <a name="device-management"></a>裝置管理

#### <a name="delete-jamf-devices----2653306--"></a>刪除 Jamf 裝置 <!-- 2653306-->
您可以刪除受控於 JAMF 的裝置，方法是移至 [裝置] > 選擇 Jamf 裝置 > [刪除]。

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>將術語變更為「淘汰」和「抹除」 <!-- 2175759 -->
為了與圖形 API 保持一致，Intune 使用者介面和文件已變更下列詞彙：
- 「移除公司資料」將變更為「淘汰」
- 「原廠重設」將變更為「抹除」

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>管理員嘗試刪除 MDM Push Certificate 時的確認對話方塊 <!-- 297909500-->
如果任何人嘗試刪除 Apple MDM Push Certificate，確認對話方塊會出現，顯示相關 iOS 和 macOS 裝置的數目。 如果刪除憑證，則必須重新註冊這些裝置。

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全性設定 <!-- 2282430 -->
您可以允許使用者控制應用程式安裝。 如啟用，則可讓以安全性違規方式停止的安裝繼續執行。 您可以指示 Windows Installer 在系統上安裝任何程式時使用提升的權限。 此外，您可以將 Windows 資訊保護 (WIP) 項目編入索引，並將跟其有關的中繼資料儲存在未加密的位置。 停用此原則時，不會編製 WIP 保護項目的索引，且不會出現在 Cortana 或檔案總管的結果中。 預設會停用這些選項的功能。 

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司入口網站的新使用者體驗更新 <!--2000968 -->
我們已依據客戶的意見反應，新增功能至公司入口網站。 您將能於裝置上體驗現有功能和可用性等方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 已獲得全新的現代化回應式設計。 此外還包括：

- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 讓語言更容易使用，讓技術專業術語更少
- 能夠共用應用程式的直接連結
- 已改進大型應用程式目錄的效能
- 增加所有使用者的協助工具  

已更新 [Intune 公司入口網站文件](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)，以反映這些變更。 若要檢視應用程式增強功能的範例，請參閱 [Intune 終端使用者應用程式的 UI 更新](whats-new-app-ui.md)。  

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>合規性報告中增強的破解偵測<!-- 2198738 -->
增強的破解偵測設定狀態現在會顯示在管理主控台的所有合規性報告中。

### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="scope-tags-for-policies---1081974---"></a>原則的範圍標籤 <!--1081974 -->
您可以[建立範圍標籤](scope-tags.md)，限制對 Intune 資源的存取。 將範圍標籤新增至角色指派，然後將範圍標籤新增至設定檔。 此角色只能存取設定檔具有相符範圍標籤 (或無範圍標籤) 的資源。

## <a name="week-of-august-14-2018"></a>2018 年 8 月 14 日當週

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>macOS 支援 Apple 裝置註冊計劃 <!-- 747651 -->
Intune 現在支援將 macOS 裝置註冊到 Apple 裝置註冊計劃 (DEP) 中。 如需詳細資訊，請參閱[使用 Apple 的裝置註冊計劃來自動註冊 macOS 裝置](device-enrollment-program-enroll-macos.md)。

## <a name="week-of-july-23-2018"></a>2018 年 7 月 23 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS 的企業營運 (LOB) 應用程式支援 <!-- 1895847 -->
Microsoft Intune 可讓 macOS LOB 應用程式部署為**必要**或**註冊可用**。 終端使用者可以使用適用於 macOS 的公司入口網站或[公司入口網站](https://portal.manage.microsoft.com)，來取得部署為**可用**的應用程式。

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>kiosk 模組的 iOS 內建應用程式支援 <!-- 2051098 -->
除了市集應用程式和受控應用程式，您現在可以選取在 iOS 裝置上以 kiosk 模式執行的內建應用程式 (例如 Safari)。

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>編輯 Office 365 Pro Plus 應用程式部署 <!-- 2150145 -->
身為 Microsoft Intune 系統管理員，您可以更有效率地編輯 Office 365 Pro Plus 應用程式部署。 此外，您不再需要刪除部署，就能變更套件的任何內容。 在 Azure 入口網站中，選取 [Microsoft Intune] > [用戶端應用程式] > [應用程式]。 從應用程式的清單中，選取您的 Office 365 Pro Plus 套件。  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>現在已提供更新的適用於 Android 的 Intune App SDK <!-- 2744271-->

已提供適用於 Android 的 Intune App SDK 的更新版本，以支援 Android P 版本。 如果您是應用程式開發人員，並使用適用於 Android 的 Intune SDK，則必須安裝 Intune App SDK 的更新版本，以確保 Android 應用程式中的 Intune 功能在 Android P 裝置上可以繼續如預期般運作。 這個版本的 Intune App SDK 提供了一個執行 SDK 更新的內建外掛程式。 您不需要重寫任何已整合的現有程式碼。 如需詳細資訊，請參閱[適用於 Android 的 Intune SDK](https://github.com/msintuneappsdk/ms-intune-app-sdk-android) \(英文\)。 如果您使用 Intune 舊的徽章樣式，建議您使用 [公事包] 圖示。 如需商標詳細資料，請參閱[此 GitHub 存放庫](https://github.com/msintuneappsdk/intune-app-partner-badge) \(英文\)。


### <a name="device-configuration"></a>裝置設定

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>在 macOS 裝置上使用防火牆設定建立裝置合規性原則 <!-- 1497640 -->
當您建立新的 macOS 合規性原則 ([裝置合規性] > [原則] > [建立原則] >  [平台：macOS] > [系統安全性]) 時，會有一些可用的新 [防火牆] 設定： 

- **防火牆**：設定您環境中處理連入連線的方式。
- **連入連線**：除了基本網際網路服務所需的連線 (例如 DHCP、Bonjour 及 IPSec) 之外，[封鎖] 所有連入連線。 這項設定也會封鎖所有的共用服務。
- **隱形模式**：[啟用] 隱形模式以防止電腦回應探查要求。 電腦會繼續回應已授權應用程式的連入要求。

適用對象：macOS 10.12 和更新版本

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 和更新版本的新 Wi-Fi 裝置組態設定檔 <!-- 1879077 -->
您目前可以使用 XML 檔案來匯入和匯出 Wi-Fi 設定檔。 透過此更新，您可以直接在 Intune 中建立 Wi-Fi 裝置組態設定檔，如同一些其他平台。

若要建立設定檔，請開啟 [裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 和更新版本] > [Wi-Fi]。 

適用於 Windows 10 及更新版本。

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>Kiosk - 已淘汰變成灰色，而且無法變更 <!-- 2149998 -->
[Kiosk 功能](device-restrictions-windows-10.md#kiosk-preview---obsolete) ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 和更新版本] > [裝置限制]) 會淘汰，並取代為 [Windows 10 和更新版本的 Kiosk 設定](kiosk-settings.md). 透過此更新，[Kiosk - 已淘汰] 功能會變成灰色，而且無法變更或更新使用者介面。 

若要啟用 Kiosk 模式，請參閱[適用於 Windows 10 和更新版本的 Kiosk 設定](kiosk-settings.md)。

適用於 Windows 10 和更新版本、Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>使用協力廠商憑證授權單位的 API <!-- 2184013 -->
在此更新中，有 Java API 可讓協力廠商憑證授權單位與 Intune 和 SCEP 整合。 然後，使用者可將 SCEP 憑證新增至設定檔，並將它套用至使用 MDM 的裝置。

Intune 目前支援[使用 Active Directory 憑證服務的 SCEP 要求](certificates-scep-configure.md)。

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>切換在 Kiosk 瀏覽器上顯示或不顯示 [結束工作階段] 按鈕 <!-- 2455253 -->
您現在可以設定 Kiosk 瀏覽器是否顯示 [結束工作階段] 按鈕。 您可以在 [裝置設定] > [Kiosk (預覽)] > [Kiosk Web Browser] \(Kiosk 網頁瀏覽器\) 看到控制項。 如果開啟，則使用者按一下此按鈕時，應用程式會提示您確認結束工作階段。 確認時，瀏覽器會清除所有瀏覽資料，並巡覽回預設 URL。

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>建立 eSIM 行動數據組態設定檔 <!-- 2564077 -->
在 [裝置設定] 中，您可以建立 eSIM 行動數據設定檔。 您可以匯入檔案，其中包含您的行動電信業者所提供的行動數據啟用碼。 您接著可以將這些設定檔部署至啟用 eSIM LTE 的 Windows 10 裝置，例如 Surface Pro LTE 和其他具有 eSIM 功能的裝置。

確認您的[裝置支援 eSIM 設定檔](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)與否。

適用於 Windows 10 及更新版本。 




### <a name="device-enrollment"></a>裝置註冊

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>將使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置自動標示為「公司」。 <!-- 2404851 -->
根據預設，使用 Samsung Knox Mobile Enrollment 所註冊的 Android 裝置現在會在 [Device Ownership] \(裝置擁有權\) 下標示為 [公司]。 在使用 Knox Mobile Enrollment 註冊之前，您不需要手動找出使用 IMEI 或序號的公司裝置。

### <a name="device-management"></a>裝置管理

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>裝置刀鋒視窗上的大量刪除裝置 <!-- 1793693 -->

您現在可以在 [裝置] 刀鋒視窗上同時刪除多部裝置。 選擇 [裝置] > [所有裝置] > 選取您要刪除的裝置 > [刪除]。 針對無法刪除的裝置，將會顯示警示。

## <a name="week-of-july-16-2018"></a>2018 年 7 月 16 日當週  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows 版公司入口網站應用程式中的更多同步機會  
Windows 版公司入口網站應用程式現在可讓您直接從 Windows 工作列和 [開始] 功能表起始同步。 如果同步裝置並取得公司資源存取權是您唯一的工作，這項功能特別有用。 若要存取這項新功能，請以滑鼠右鍵按一下已釘選到工作列或 [開始] 功能表的公司入口網站圖示。 在功能表選項 (也稱為捷徑清單) 中，選取 [同步此裝置]。 公司入口網站會開啟至 **[設定]** 頁面並起始您的同步。若要查看新功能，請參閱 [UI 的新功能](whats-new-app-ui.md)。   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows 版公司入口網站應用程式的新瀏覽體驗  

現在，在 Windows 版公司入口網站應用程式中瀏覽或搜尋應用程式時，您可以切換現有的 [磚] 檢視和新增的 [詳細資料] 檢視。 新的檢視會列出應用程式詳細資料，例如名稱、發佈者、發佈日期，以及安裝狀態。  

[應用程式] 頁面的 [已安裝] 檢視可讓您查看有關已完成和進行中之應用程式安裝的詳細資料。 若要查看新檢視的外觀，請參閱 [UI 的新功能](whats-new-app-ui.md)。  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>已改善裝置註冊管理員的公司入口網站應用程式體驗  
當裝置註冊管理員 (DEM) 登入 Windows 版公司入口網站應用程式時，應用程式現在只會列出 DEM 目前執行中的裝置。 這項改善會減少之前應用程式在嘗試顯示所有 DEM 註冊裝置時所發生的逾時。  


## <a name="week-of-july-9-2018"></a>2018 年 7 月 9 日當週

### <a name="app-management"></a>應用程式管理

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>依據未經核准的裝置廠商和型號來封鎖應用程式存取 <!-- 1425689 ! -->
Intune IT 系統管理員可以透過 Intune 應用程式防護原則，強制執行 Android 製造商和/或 iOS 型號的指定清單。 IT 系統管理員可以提供以分號分隔的製造商清單 (適用於 Android 原則) 及裝置型號清單 (適用於 iOS 原則)。 Intune 應用程式防護原則僅適用於 Android 和 iOS。 針對此指定清單，將可以執行兩個個別的動作：
- 針對未指定的裝置，封鎖其存取應用程式的能力。
- 或是針對未指定的裝置，選擇性地抹除該裝置上的公司資料。 

若沒有符合原則需求，使用者將無法存取目標應用程式。 根據設定的不同，系統可能會封鎖該使用者，或選擇性地抹除其位於應用程式內的公司資料。 在 iOS 裝置上，此功能需要應用程式 (亦即，WXP、Outlook、Managed Browser、Yammer) 的參與來就地整合 Intune App SDK，以在目標應用程式中強制執行此功能。 此整合會以輪流的方式發生，並取決於特定的應用程式小組。 在 Android 上，此功能需要有最新版的公司入口網站。 

在使用者裝置上，Intune 用戶端將會根據應用程式防護原則 Intune 刀鋒視窗中所指定字串來進行簡單比對，藉以採取動作。 這會完全取決於裝置報告的值。 因此，我們會建議 IT 系統管理員確定預期的行為是正確無誤的。 這可透過針對小型的使用者群組，在各種不同的裝置製造商和型號上測試此設定來達成。 在 Microsoft Intune 中，選取 [用戶端應用程式] > [應用程式保護原則] 來檢視及新增應用程式保護原則。 如需有關應用程式保護原則的詳細資訊，請參閱[什麼是應用程式保護原則](app-protection-policy.md)與[在 Intune 中使用應用程式防護原則的存取動作選擇性地抹除資料](app-protection-policies-access-actions.md)。

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>存取 macOS 公司入口網站發行前版本組建 <!-- 1734766 -->
使用 Microsoft AutoUpdate 註冊，您可以透過加入測試人員計畫提早收到組建。 註冊可讓您在使用者可使用已更新的公司入口網站之前先行使用。 如需詳細資訊，請參閱 [Microsoft Intune 部落格](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)。

## <a name="week-of-july-2-2018"></a>2018 年 7 月 2 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>監視每個裝置的 iOS 應用程式設定狀態 <!-- 880037 -->
身為 Microsoft Intune 系統管理員，您可以監視每個受控裝置的 iOS 應用程式設定狀態。 從 Azure 入口網站的 [Microsoft Intune] 中，選取 [裝置] > [所有裝置]。 從受控裝置清單中，選取特定的裝置以顯示裝置的刀鋒視窗。 在裝置的刀鋒視窗中，選取 [應用程式設定]。

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>存取適用於應用程式防護原則的動作 <!-- 1483510 -->
您可以設定應用程式防護原則，以明確地針對不符合規範的裝置進行抹除、封鎖或警告。 「抹除」動作能從裝置移除您公司的資料。 如果發生抹除，系統會向裝置使用者告知抹除的原因及補救的步驟。 針對某些設定 (例如最小 OS 版本)，您將能套用多個動作 (例如封鎖和抹除)。 請注意，當應用程式啟動時，便會觸發這些動作。

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>選擇性抹除組織的應用程式資料 <!-- 1507030 -->
不符合應用程式保護原則 (APP) 存取設定的條件時，系統管理員現在可以設定選擇性抹除組識資料作為新的動作。  這項功能可協助系統管理員依據預先設定的準則，自動保護並移除應用程式中的機密組織資料。

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>撤銷透過 VPP 購買的 iOS 應用程式 <!-- 1777384 -->
身為 Microsoft Intune 系統管理員，您可以撤銷所有透過大量採購方案 (VPP) 購買的所選 iOS 應用程式授權。 當使用者授權的應用程式不再指派給使用者時，您可以通知他們。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 回收的授權計數將會反映在 Intune 之 [應用程式] 工作負載中的 [授權的應用程式] 節點。 如需與 iOS VPP 應用程式相關的詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>公司入口網站應用程式中不相容訊息的更新 <!-- 1832222 -->
我們已修訂裝置使用者在裝置不相容時看到的訊息。 訊息保留其原始意義，但已透過更友善的語言和技術性較低的術語更新。 我們也已重新整理文件和補救步驟的連結，將其保持為最新。
下列前後文字是您將看到之傳訊中的一個改善範例：
- **之前**：*這部裝置未在 IT 管理員要求的指定期間內連絡 Intune 服務。若要解決此問題，請在您的裝置上開啟公司入口網站應用程式，然後按一下 [檢查相容性] 按鈕。*
- **之後**：*您的裝置已有一段未向組織簽到。* 若要重新建立連線，請在裝置上開啟公司入口網站應用程式，然後點選 [檢查裝置設定]。

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>撤銷 iOS VPP 應用程式授權 <!-- 1863797 -->
身為系統管理員，您可以回收指派給使用者或裝置的 iOS VPP 應用程式授權。 解除安裝 iOS VPP 應用程式也可讓您回收應用程式授權。 在解除安裝應用程式之前，需要先從目標應用程式群組中刪除使用者或裝置。 從群組移除使用者或裝置，可避免重新安裝應用程式。 完成這些步驟後，您可以選擇將應用程式授權指派給其他使用者或裝置。 如需 iOS VPP 應用程式授權的詳細資訊，請參閱[在 Microsoft Intune 中管理 iOS 大量採購的應用程式](vpp-apps-ios.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>使用 [存取公司或學校資源] 設定來選取裝置類別 <!-- 1058963 eenotready --> 
如果您已啟用[裝置群組對應](https://docs.microsoft.com/intune/device-group-mapping)，現在將在 Windows 10 上的使用者透過 [設定] > [帳戶] > [存取公司或學校資源] 中的 [連線] 按鈕註冊之後，提示他們選取裝置類別。 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>使用 sAMAccountName 作為電子郵件設定檔的帳戶使用者名稱 <!-- 1500307 -->
您可以使用內部部署 **sAMAccountName**，作為 Android、iOS 和 Windows 10 電子郵件設定檔的帳戶使用者名稱。 也可以從Azure Active Directory (Azure AD) 中的 `domain` 或 `ntdomain` 屬性取得網域。 或者，輸入自訂靜態網域。

若要使用這項功能，您必須將來自內部部署 Active Directory 環境的 `sAMAccountName` 屬性同步至 Azure AD。

適用於 [Android](email-settings-android.md)、[iOS](email-settings-ios.md)、[Windows 10 和更新版本](email-settings-windows-10.md)

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>查看衝突的裝置組態設定檔 <!-- 1556983 -->
在 [裝置設定] 中，會顯示現有設定檔的清單。 使用此更新即會新增資料行，以提供衝突之設定檔的詳細資料。 您可以選取衝突的資料列，以查看設定以及發生衝突的設定檔。 

移至[管理組態設定檔](device-profile-monitor.md#view-conflicts)以取得更多資訊。

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>裝置相容性中裝置的新狀態 <!-- 2308882 -->
在 [裝置相容性] > [原則] > 選取原則 > [概觀] 中，已新增下列新狀態：
- 成功
- 錯誤
- 衝突
- 擱置
- 不適用。同時顯示了顯示不同平台裝置計數的影像。 例如，如果您要查看 iOS 設定檔，新的磚會顯示同時指派給此設定檔的非 iOS 裝置計數。 請參閱[裝置合規性原則](compliance-policy-monitor.md#view-status-of-device-policies)。

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>裝置合規性支援協力廠商防毒解決方案 <!-- 2325484 -->
當您建立裝置合規性政策時 ([裝置合規性] > [原則] > [建立原則] > [平台:Windows 10 和更新版本] > [設定] > [系統安全性])，有新的 [[裝置安全性](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)] 選項： 
- **防毒**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 
- **反間諜功能**：當設定為 [必要] 時，您可以使用向 Windows 資訊安全中心註冊的防毒解決方案 (例如 Symantec 和 Windows Defender) 來檢查合規性。 

適用於：Windows 10 及更新版本 

### <a name="device-enrollment"></a>裝置註冊

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>註冊計劃權杖清單中沒有設定檔資料行的裝置 <!-- 1853904 -->
在註冊程式權杖清單中，有一個新資料行會顯示未指派設定檔的裝置數目。 這有助於系統管理員在將設定檔交給使用者之前將其指派給這些裝置。 若要查看新資料行，請前往 [裝置註冊] > [Apple 註冊] > [註冊計劃權杖]。

### <a name="device-management"></a>裝置管理

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 和 Play for Work 的 Google 名稱變更 <!--842873 -->
Intune 已更新 "Android for Work" 術語以反映 Google 的商標變更。 "Android for Work" 和 "Play for Work" 這些詞彙已不再使用。 視內容而定，會使用不同的術語：
- 「Android 企業」指的是整體的現代 Android 管理堆疊。
- 「工作設定檔」或「設定檔擁有者」指的是使用工作設定檔管理的 BYOD 裝置。
- 「受控 Google Play」則是指 Google 應用程式存放區。

#### <a name="rules-for-removing-devices----1609459---"></a>用於移除裝置的規則 <!-- 1609459 -->
新規則已可用，可讓您自動移除在所設定天數內未簽入的裝置。 若要查看新規則，請移至 [Intune] 窗格，然後依序選取 [裝置] 和 [裝置清除規則]。

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>公司所擁有且適用於 Android 裝置的單次使用支援 <!-- 1630973 -->

Intune 現在支援高度受控、鎖定、Kiosk 樣式的 Android 裝置。 這可讓系統管理員將裝置的用途進一步鎖定為單一應用程式或一小組的應用程式，並可防止使用者在裝置上啟用其他應用程式或執行其他動作。 若要設定 Android Kiosk，請移至 [Intune] > [裝置註冊] > [Android 註冊] > [Kiosk 及工作裝置註冊]。 如需詳細資訊，請參閱[設定 Android 企業 Kiosk 裝置註冊](android-kiosk-enroll.md)。

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>已上傳之重複公司裝置識別碼的每一資料列檢閱 <!-- 2203794-->
上傳公司識別碼時，Intune 現在會提供任何重複項目的清單，並可讓您選擇取代或保留現有資訊。 選擇 [裝置註冊] > [公司裝置識別碼] > [新增識別碼] 之後，如果有重複項目，則會出現報表。 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>手動新增公司裝置識別碼 <!-- 2203803 -->
您現在可以手動新增公司裝置識別碼。 請選擇 [裝置註冊] > [公司裝置識別碼] > [新增]。 

## <a name="week-of-june-25-2018"></a>2018年 6 月 25 日當週

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 新的 Mobile Threat Defense 夥伴 <!-- 1169249 -->

您可以根據由 Pradeo (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

## <a name="week-of-june-18-2018"></a>2018年 6 月 18 日當週

### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Intune 應用程式防護原則的 Microsoft Edge 行動支援 <!-- 1817882 -->

行動裝置的 Microsoft Edge 瀏覽器現在支援 Intune 中所定義的應用程式防護原則。

## <a name="week-of-june-11-2018"></a>2018年 6 月 11 日當週

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>使用 FIPS 模式和 NDES 憑證連接器 <!-- 1333688 -->
當您在啟用聯邦資訊處理標準 (FIPS) 模式的電腦上安裝 NDES 憑證連接器時，發行和撤銷憑證無法如預期運作。 在此更新中，NDES 憑證連接器隨附 FIPS 支援。 

此更新還包括：

- NDES 憑證連接器需要 .NET 4.5 Framework，這會自動隨附於 Windows Server 2016 和 Windows Server 2012 R2。 之前，.NET 3.5 Framework 是最低必要版本。
- NDES 憑證連接器隨附 TLS 1.2 支援。 因此，如果安裝 NDES 憑證連接器的伺服器支援 TLS 1.2，則會使用 TLS 1.2。 如果伺服器不支援 TLS 1.2，則會使用 TLS 1.1。 目前，使用 TLS 1.1 在裝置與伺服器之間進行驗證。

如需詳細資訊，請參閱[設定並使用 SCEP 憑證](certificates-scep-configure.md)和[設定並使用 PKCS 憑證](certficates-pfx-configure.md)。

## <a name="week-of-june-4-2018"></a>2018年 6 月 4日當週

### <a name="app-management"></a>應用程式管理

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>在 Kiosk 模式中擷取商務用 Microsoft Store 應用程式的相關聯應用程式使用者模型識別碼 (AUMID) <!-- 1560077 ! -->
Intune 目前可以擷取商務用 Microsoft Store (WSfB) 應用程式的應用程式使用者模型識別碼 (AUMID)，以提供改善的 Kiosk 設定檔設定。

如需商務用 Microsoft Store 應用程式的詳細資訊，請參閱[管理來自商務用 Microsoft Store 的應用程式](windows-store-for-business.md)。

#### <a name="new-company-portal-branding-page----1916370---"></a>新的公司入口網站商標頁面 <!-- 1916370 -->
公司入口網站商標頁面有新的版面配置、訊息和工具提示。


### <a name="device-configuration"></a>裝置設定

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Palo Alto Networks GLOBalProtect VPN 設定檔的支援 <!-- 1333680 ! -->
透過這項更新，您可以選擇 Palo Alto Networks GLOBalProtect 作為在 Intune 中 VPN 設定檔的 VPN 連線類型 ([裝置設定] > [設定檔] > [建立設定檔] > [設定檔類型] > [VPN])。 在此版本中，支援下列平台： 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>新增本機裝置安全性選項設定 <!-- 1403702 -->
您現在能夠為 Windows 10 裝置設定額外的 [本機裝置安全性選項] 設定。 可使用額外設定的區域包括 Microsoft Network Client、Microsoft Network Server、[網路存取和安全性] 及 [互動式登入]。 當您建立 Windows 10 裝置設定原則時，在 [Endpoint Protection] 類別中找到這些設定。

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>在 Windows 10 裝置上啟用 Kiosk 模式 <!-- 1560072 ! -->
在 Windows 10 裝置上，您可以建立組態設定檔並啟用 Kiosk 模式 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10] > [裝置限制] > [Kiosk])。 在此更新中，[Kiosk (預覽)] 設定已重新命名為 [Kiosk (已淘汰)]。 我們不建議繼續使用 [Kiosk (已淘汰)]，但該功能在 7 月更新之前將會持續運作。 [Kiosk (已淘汰)] 已由新的 [Kiosk] 設定檔類型 ([建立設定檔] > [Windows 10] > [Kiosk (預覽)]) 取代，此設定檔類型將會包含在 Windows 10 RS4 及更新版本上設定 Kiosk 的設定。

適用於 Windows 10 及更新版本。

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>已重新推出裝置設定檔圖形化使用者圖表 <!-- 2160133 -->
在改善裝置設定檔圖形化圖表 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀]) 上所顯示的數值計數之際，暫時移除了圖形化使用者圖表。

此更新已重新推出圖形化使用者圖表，如 Azure 入口網站中所示。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>支援 Windows Autopilot 註冊而不需要使用者驗證 <!-- 1165118 -->
Intune 現在支援 Windows Autopilot 註冊，而不需要使用者驗證。 這是 Windows Autopilot 部署設定檔中 [Autopilot 部署模式] 設為 [自我部署] 的新選項。  裝置必須執行 Windows 10 Insider Preview 組建 17672 或更新版本，並擁有 TPM 2.0 晶片才能成功完成此類型的註冊。 由於不需要任何使用者驗證，您只應將此選項指派給您擁有實體控制權的裝置。

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>針對 Autopilot 設定 OOBE 時的新語言/地區設定 <!-- 1821766 -->
在全新體驗期間，將會有新的組態設定可供設定 Autopilot 設定檔的語言和地區。 若要查看新設定，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔] > [部署模式] = [自我部署] > [設定的預設值]。

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>適用於設定裝置鍵盤的新設定 <!-- 1821768 -->
在全新體驗期間，將會有新設定可供設定 Autopilot 設定檔的鍵盤。 若要查看新設定，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔] > [建立設定檔] > [部署模式] = [自我部署] > [設定的預設值]。

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>將 AutoPilot 設定檔移至群組目標設定 <!-- 1877935 -->
AutoPilot 部署設定檔可以指派給包含 AutoPilot 裝置的 Azure AD 群組。

### <a name="device-management"></a>裝置管理

#### <a name="set-compliance-by-device-location----851881----"></a>依裝置位置設定合規性 <!-- 851881 ! -->
在某些情況下，您可能會想要依網路連線將公司資源的存取限制於特定的位置。 您現在可以依據裝置的 IP 位址建立合規性原則 ([裝置合規性] > [位置])。 如果裝置移出該 IP 範圍，則該裝置將會無法存取公司資源。

適用於：公司入口網站應用程式已更新的 Android 裝置 6.0 和更新版本

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>防止 Windows 10 企業版 RS4 AutoPilot 裝置上的消費者應用程式和體驗<!-- 1621980 -->
您將能夠防止在「Windows 10 企業版 RS4 AutoPilot」裝置上安裝消費者應用程式和體驗。 若要查看此功能，請移至 [Intune] > [裝置設定] > [設定檔] > [建立設定檔] > [平台] = [Windows 10 或更新版本] > [設定檔類型] = [裝置限制] > [設定] > [Windows 焦點] > [消費者功能]。 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>解除安裝 Windows 10 軟體更新的最新版本 <!-- 1732948 -->
如果您發現 Windows 10 電腦上發生重大問題，可以選擇解除安裝 (復原) 最新的功能更新或最新的品質更新。 解除安裝功能或品質更新只適用於裝置所在的維護通道。 解除安裝將會觸發原則，以在 Windows 10 電腦上還原先前的更新。 特別是對於功能更新，您可以將能夠套用解除安裝最新版本的時間限制為 2-60 天。 若要設定軟體更新解除安裝選項，請從 Azure 入口網站內的 [Microsoft Intune] 刀鋒視窗中選取 [軟體更新]。 然後，從 [軟體更新] 刀鋒視窗中，選取 [Windows 10 更新通道]。 接著可以選擇 [概觀] 區段中的 [解除安裝] 選項。

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>搜尋所有裝置的 IMEI 和序號 <!-- 1793685 -->
您目前能在所有裝置的刀鋒視窗上搜尋 IMEI 和序號 (電子郵件、UPN、裝置名稱和管理名稱仍然可用)。 在 Intune 中，選擇 [裝置] > [所有裝置] > 在搜尋方塊中輸入您的搜尋。

#### <a name="management-name-field-will-be-editable----1875989---"></a>管理名稱欄位將可以編輯 <!-- 1875989 -->
您目前可在裝置的 [屬性] 刀鋒視窗上編輯管理名稱欄位。 如果要編輯此欄位，請選擇 [裝置] > [所有裝置] > 選擇裝置 > [屬性]。 您可以使用管理名稱欄位來唯一識別裝置。

#### <a name="new-all-devices-filter-device-category----1878520---"></a>[新增全部] 裝置篩選條件：裝置類別 <!-- 1878520 -->
您現在可以依裝置類別篩選 [所有裝置] 清單。 若要這樣做，請選擇 [裝置] > [所有裝置] > [篩選] > [裝置類別]。

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>使用 TeamViewer 來共用 iOS 和 MacOS 裝置的螢幕畫面 <!-- 1985547 -->
系統管理員現在可以連線至 [TeamViewer](device-profile-android-teamviewer.md)，並與 iOS 和 macOS 裝置建立螢幕畫面共用工作階段。 iPhone、iPad 及 macOS 使用者都可以與任何其他電腦或行動裝置即時共用其螢幕畫面。 

#### <a name="multiple-exchange-connector-support----2070451---"></a>多重 Exchange 連接器支援 <!-- 2070451 -->
您不會再受到每個租用戶只能有一個 Microsoft Intune Exchange Connector 的限制了。 Intune 現在支援多個 Exchange 連接器，使您可以用多個內部部署 Exchange 組織來設定 Intune 條件式存取。

透過 Intune 內部部署 Exchange 連接器，您可以根據裝置是否已在 Intune 註冊且符合 Intune 裝置合規性政策，來管理裝置對於您內部部署 Exchange 信箱的存取。 若要設定連接器，請從 Azure 入口網站下載 Intune 內部部署 Exchange 連接器，並安裝在您 Exchange 組織中的伺服器。 在 Microsoft Intune 儀表板中，選擇 [內部部署存取]，然後在 [安裝] 下選擇 [Exchange ActiveSync 連接器]。 下載 Exchange 內部部署連接器，並將其安裝在您 Exchange 組織中的伺服器。 您現在已經沒有一個租用戶只能有一個 Exchange 連接器的限制，因此您如果有其他 Exchange 組織，亦可遵循此相同流程為每個 Exchange 組織下載並安裝連接器。

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>新的裝置硬體詳細資料：CCID <!-- 2156657 -->
每個裝置現在都包含晶片卡介面裝置 (CCID) 資訊。 若要查看它，請選擇 [裝置] > [所有裝置] > 選擇裝置 > [硬體] > 檢查 [網路詳細資料] 下的內容 >

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>將所有使用者和所有裝置指派為範圍群組 <!-- 2196803 -->
您現在能以範圍群組的形式指派所有使用者、所有裝置，以及所有使用者和所有裝置。 若要這樣做，請選擇 [Intune 角色] > [所有角色] > [原則和設定檔管理員] > [指派] > 選擇指派 > [範圍 (群組)]。

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>iOS 和 macOS 裝置現在包含 UDID 資訊 <!-- 2219806 -->
若要查看 iOS 和 macOS 裝置的唯一裝置識別碼 (UDID)，請移至 [裝置] > [所有裝置] > 選擇裝置 > [硬體]。 UDID 只適用於公司裝置 (如 [裝置] > [所有裝置] > 選擇裝置 > [屬性] > [裝置擁有權] 下的設定)。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>改善的應用程式安裝疑難排解 <!-- 928990 -->
在受 Microsoft Intune MDM 管理的裝置上，應用程式安裝有時可能會失敗。 當這些應用程式安裝失敗時，使用者可能無法輕易地了解失敗的原因，或是對問題進行疑難排解。 我們正在推出應用程式疑難排解功能的公開預覽。 您將會在每個個別裝置的底下看到名為 [受控應用程式] 的新節點。 這會列出透過 Intune MDM 傳遞的應用程式。 在該節點中，您將會看到應用程式安裝狀態的清單。 如果您選取個別的應用程式，將會看到針對該特定應用程式的疑難排解檢視。 在疑難排解檢視中，您將會看到應用程式的端對端生命週期，例如針對該應用程式進行建立、修改、設為目標，以及傳遞至裝置的時間。 此外，如果應用程式安裝沒有成功，系統將會針對導致該錯誤的原因為您顯示錯誤碼及協助訊息。 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Inunte 應用程式保護原則和 Microsoft Edge <!-- 1818968 -->
適用於行動裝置 (iOS 和 Android) 的 Microsoft Edge 瀏覽器現在支援 Microsoft Intune 應用程式保護原則。 使用其公司 Azure AD 帳戶登入 Edge 應用程式的 iOS 和 Android 裝置使用者，將會受到 Intune 的保護。 在 iOS 裝置上，[要求受控瀏覽器的 Web 內容] 原則可讓使用者開啟受控 Microsoft Edge 中的連結。

## <a name="week-of-may-14-2018"></a>2018 年 5 月 14 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>要求安裝原則、應用程式、憑證及網路設定檔 <!-- 1553555 -->

在佈建 AutoPilot 裝置期間，系統管理員能夠禁止使用者存取 Windows 10 RS4 桌面，直到 Intune 安裝原則、應用程式及憑證和網路設定檔為止。 如需詳細資訊，請參閱[設定註冊狀態頁面](windows-enrollment-status.md)。

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>設定應用程式保護原則 <!-- 2144597 Part 2 -->

在 Azure 入口網站，不用移至 Intune 應用程式保護服務刀鋒視窗，您現在只需移至 Intune。 目前在 Intune 中只有一個應用程式保護原則的位置。 請注意，所有應用程式保護原則都在 Intune [應用程式保護原則] 底下的 [行動應用程式] 刀鋒視窗上。 這項整合有助於簡化雲端管理系統管理。 請記住，所有應用程式保護原則都已經在 Intune 中，而您可以修改任何先前已設定的原則。 Intune 應用程式原則保護 (APP) 和條件式存取 (CA) 原則現在會在 [條件式存取] 下，這可以在 [Microsoft Intune] 刀鋒視窗的 [管理] 區段找到，或在 [Azure Active Directory] 刀鋒視窗的 [安全性] 區段找到。 如需有關修改條件式存取原則詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 如需其他資訊，請參閱[什麼是應用程式保護原則？](app-protection-policy.md)

## <a name="week-of-may-7-2018"></a>2018 年 5 月 7 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>Samsung Knox Mobile Enrollment 支援 <!--1112863-->

當 Intune 與 Samsung Knox Mobile Enrollment (KME) 搭配使用時，您可以註冊大量公司擁有的 Android 裝置。 使用 WiFi 或行動電話通訊網路的使用者第一次開啟其裝置時，只需輕點幾下即可註冊。 使用 Knox 部署應用程式時，可以使用藍牙或 NFC 註冊裝置。 如需詳細資訊，請參閱[使用 Samsung Knox Mobile Enrollment 自動註冊 Android 裝置](android-samsung-knox-mobile-enroll.md)。

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>要求 Windows 10 版公司入口網站中的說明 <!-- 1874137 -->

當使用者啟動工作流程以取得有關問題的說明時，Windows 10 版公司入口網站現在會將應用程式記錄檔直接傳送給 Microsoft。 這樣可以更輕鬆地進行疑難排解並解決向 Microsoft 提出的問題。

## <a name="week-of-april-23-2018"></a>2018 年 4 月 23 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>在 Android 上針對 MAM PIN 提供密碼支援<!-- 1438086 -->

Intune 系統管理員可以將應用程式的啟動要求設定為使用密碼，而不是使用數字型的 MAM PIN 碼。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 Intune 支援密碼的方式與數字 PIN 類似，能夠透過管理主控台設定長度下限、允許重複的字元及順序。 若要使用此功能，Android 上必須要有最新版的公司入口網站。 此功能已經可供 iOS 使用。

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS 的企業營運 (LOB) 應用程式支援 <!-- 1473977 -->
Microsoft Intune 將可讓您從 Azure 入口網站安裝 macOS LOB 應用程式。 您將能夠在以 GitHub 中提供的工具對 macOS LOB 應用程式進行前處理之後，將其新增至 Intune。 在 Azure 入口網站中，從 [Intune] 刀鋒視窗選擇 [用戶端應用程式]。 在 [用戶端應用程式] 刀鋒視窗上，選擇 [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗上，選取 [企業營運應用程式]。 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>適用於 Android Enterprise 工作設定檔應用程式指派的內建所有使用者和所有裝置群組 <!-- 1813073 -->
您可以利用內建的 [所有使用者] 和 [所有裝置] 群組來進行 Android Enterprise 工作設定檔應用程式指派。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>Intune 會重新安裝被使用者解除安裝的必要應用程式 <!-- 1947010 -->
如果終端使用者解除安裝必要的應用程式，Intune 會在 24 小時內自動重新安裝應用程式，而不會等待 7 天的重新評估週期。

### <a name="device-configuration"></a>裝置設定

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>裝置設定檔圖表和狀態清單顯示群組中的所有裝置 <!-- 1449153 -->
當您設定裝置設定檔 ([裝置設定] > [設定檔]) 時，可以選擇裝置設定檔，例如 iOS。 您會將這個設定檔指派給包含 iOS 裝置和非 iOS 裝置的群組。 圖形化圖表計數會顯示設定檔已套用至 iOS「和」非 iOS 裝置 ([裝置設定] > [設定檔] > 選取現有的設定檔 > [概觀])。 當您在 [概觀] 索引標籤中選取圖形化圖表時，[裝置狀態] 會列出群組中的所有裝置，而不是只列出 iOS 裝置。 

在此更新中，圖形化圖表 ([裝置設定]  >  [設定檔] > 選取現有的設定檔 > [概觀]) 只會顯示特定裝置設定檔的計數。 例如，如果設定裝置設定檔適用於 iOS 裝置，圖表只會列出 iOS 裝置的計數。 選取圖形化圖表和開啟 [裝置狀態] 只會列出 iOS 裝置。

進行此更新時，會暫時移除圖形化使用者圖表。 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>適用於 Windows 10 的一律開啟 VPN<!--1333666 -->

目前，可藉由使用以 OMA-URI 建立的自訂虛擬私人網路 (VPN) 設定檔，在 Windows 10 裝置上使用[一律開啟](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)。

在此更新中，系統管理員將能夠直接在 Azure 入口網站的 Intune 中，為 Windows 10 VPN 設定檔啟用 Always On。 「一律開啟」VPN 設定檔會在下列情況下自動連線：

- 使用者登入其裝置
- 裝置上的網路發生變更
- 裝置上的螢幕在關閉後恢復開啟

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>教育版設定檔的新印表機設定 <!-- 1308900 -->

教育版設定檔的新設定位於 [印表機] 類別下：[印表機]、[預設印表機]、[新增印表機]。

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>在個人的設定檔中顯示呼叫者識別碼 - Android Enterprise 工作設定檔 <!--1098984 -->
在裝置上使用個人設定檔時，終端使用者可能無法從工作連絡人看到呼叫者識別碼詳細資料。 

在此更新中，[Android Enterprise] > [裝置限制] > [工作設定檔設定] 中會有一個新的設定：
- 在個人設定檔中顯示工作連絡人呼叫者識別碼

啟用 (未設定) 時，工作連絡呼叫者詳細資料會顯示在個人設定檔中。 封鎖時，工作連絡呼叫者詳細資料不會顯示在個人設定檔中。 

適用於：Android OS 6.0 版和更新版本上的 Android 工作設定檔裝置

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>在 Endpoint Protection 設定中新增新的 Windows Defender Credential Guard 設定 <!--1102252 --><!--from 1802 and 1804-->

在此更新中，[Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard) ([裝置設定]  >  [設定檔]  >  [端點保護]) 包含下列設定： 

- **Windows Defender Credential Guard**：開啟搭載虛擬化安全性的 Credential Guard。 若同時啟用了**安全開機的平台安全性層級**與**虛擬化安全性**，啟用此功能將有助於在下次重新開機時保護認證。 這些選項包括：
  - **已停用**：若先前開啟 Credential Guard 時也啟用了 [在不含鎖定情況下啟用] 選項，將會從遠端關閉 Credential Guard。

  - **在包含 UEFI 鎖定的情況下啟用**：確保無法使用登錄機碼或群組原則停用 Credential Guard。 若要在使用此設定後停用 Credential Guard，必須將群組原則設為 [已停用]。 接著移除每位真實存在之使用者每部電腦的安全性功能。 下列步驟會清除 UEFI 中保存的設定。 只要 UEFI 設定持續存在，就會啟用 Credential Guard。

  - **在不含鎖定情況下啟用**：允許使用群組原則從遠端停用 Credential Guard。 使用此設定的裝置至少必須執行 Windows 10 (1511 版)。

設定 Credential Guard 時會自動啟用下列相關技術： 

  - **啟用虛擬化安全性 (VBS)**：在下次重新開機期間開啟虛擬化安全性 (VBS)。 虛擬化安全性使用 Windows Hypervisor 支援安全性服務，需要安全開機功能。
  - **使用直接記憶體存取 (DMA) 進行安全開機**：透過安全開機和直接記憶體存取開啟 VBS。 DMA 保護需要硬體支援，而且只可在設定正確的裝置上啟用。 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>在 SCEP 憑證上使用自訂主體名稱 <!-- 2064190 -->
您可以使用在 SCEP 憑證設定檔中，使用自訂主體常見的名稱 **OnPremisesSamAccountName**。 例如，您可以使用 `CN={OnPremisesSamAccountName})`。

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>在 Android Enterprise 工作設定檔上封鎖相機和螢幕擷取 <!-- 1098977 -->
當您為 Android 裝置設定裝置限制時，有兩個新屬性可用於封鎖： 
- 相機：封鎖對裝置上所有相機的存取
- 螢幕擷取：封鎖螢幕擷取，同時也防止在沒有安全視訊輸出的顯示裝置上顯示內容

適用於 Android Enterprise 工作設定檔。


### <a name="device-enrollment"></a>裝置註冊

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>適用於具有 macOS High Sierra 10.13.2+ 之裝置上使用者的新註冊步驟 <!--1734567 -->
macOS High Sierra 10.13.2 引進了「使用者核准的」MDM 註冊概念。 核准的註冊讓 Intune 可以管理一些高度安全性的設定。 如需詳細資訊，請參閱以下的 Apple 支援文件： https://support.apple.com/HT208019。

除非使用者開啟 [系統偏好設定] 手動提供核准，否則使用 macOS 公司入口網站註冊的裝置會被視為「未經使用者核准」。 為此，macOS 公司入口網站現在會在註冊程序結尾，將 macOS 10.13.2 和更新版本的使用者導向以供他們手動核准其註冊。 Intune 管理主控台將會針對已註冊裝置是否獲得使用者核准進行回報。



### <a name="device-management"></a>裝置管理

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>進階威脅防護 (ATP) 和 Intune 已完全整合<!-- 1629303 -->

[進階威脅防護 (ATP)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection) 會顯示 Windows 10 裝置的風險層級。 在 Windows Defender 資訊安全中心 (ATP 入口網站)，您可以建立與 Microsoft Intune 的連線。 一旦建立之後，Intune 合規性原則會用來判斷可接受的威脅層級。 如果超過威脅層級時，那麼 Azure Active Directory (AD) 條件存取原則可封鎖存取組織內的不同應用程式。

這項功能可讓 ATP 掃描檔案、偵測威脅，以及報告 Windows 10 裝置上的任何風險。

請參閱[在 Intune 中啟用具有條件存取的 ATP](advanced-threat-protection.md)。

#### <a name="support-for-user-less-devices----1637553---"></a>支援無使用者裝置 <!-- 1637553 -->
Intune 可以評估不具使用者之裝置 (例如 Microsoft Surface Hub) 的合規性。 合規性原則可以針對特定裝置。 因此，可以針對沒有相關使用者的裝置判斷是否符合規範 (和不符合規範)。

#### <a name="delete-autopilot-devices----1713650---"></a>刪除 AutoPilot 裝置 <!-- 1713650 -->
Intune 系統管理員可以[刪除 Autopilot 裝置](enrollment-autopilot.md#delete-autopilot-devices)。

#### <a name="improved-device-deletion-experience---1832333---"></a>改進的裝置刪除體驗 <!--1832333 -->
您現在無須移除公司資料，或是將裝置重設為原廠預設值，就能[從 Intune 刪除裝置](devices-wipe.md#delete-devices-from-the-intune-portal)。

若要查看新體驗，請登入 Intune，然後選取 [裝置] > [所有裝置] > 裝置的名稱 > [刪除]。

如果您仍然想要確認抹除/淘汰，可以使用標準裝置生命週期途徑，方法是先發出 [移除公司資料] 和 [重設成出廠預設值]，再進行 [刪除]。 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>在處於遺失模式時於 iOS 上播放音效 <!-- 1947769 -->
當受監督的 iOS 裝置處於「行動裝置管理」(MDM) 的[遺失模式](device-lost-mode.md)時，您可以[播放音效](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device) ([裝置]  >  [所有裝置]  **> 選取 iOS 裝置 > [概觀]** >  [更多])。 此音效會持續播放，直到裝置解除遺失模式，或使用者停用了裝置上的音效。 適用於 iOS 裝置 9.3 和更新版本。

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>禁止或允許在 Intune 裝置上執行的搜尋中出現 Web 結果 <!--1972804-->

系統管理員現在可以禁止裝置上的搜尋出現 Web 結果。

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>改進 Apple MDM Push Certificate 上傳失敗的錯誤訊息傳遞 <!-- 2172331 -->

錯誤訊息將會說明更新現有的 MDM 憑證時，必須使用相同的 Apple ID。

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>在虛擬機器上的 macOS 測試公司入口網站 <!-- 2216679 -->

我們已發佈指導，協助 IT 系統管理員在 Parallels Desktop 與 VMware Fusion 之虛擬機器上的 macOS 中測試公司入口網站應用程式。 深入了解如何[虛擬 macOS 機器進行測試](macos-enroll.md#enroll-virtual-macos-machines-for-testing)。


### <a name="user-interface"></a>使用者介面

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>改進 Windows 10 公司入口網站中的裝置磚 <!--2213364 -->

這些磚在更新之後將更方便視障使用者使用，而且可以為螢幕閱讀工具提供更好的效能。

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>在 macOS 版公司入口網站應用程式中傳送診斷報告 <!-- 2216677 -->
macOS 裝置版的公司入口網站應用程式在更新之後，改進了使用者回報 Intune 相關錯誤的方式。 您的員工可以透過公司入口網站應用程式，進行下列作業：

- 將診斷報告直接上傳給 Microsoft 開發人員小組。
- 透過電子郵件將事件識別碼傳送給 IT 支援小組。

如需詳細資訊，請參閱[傳送 macOS 的錯誤](/intune-user-help/send-errors-macos)。

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Intune 在 Windows 10 版的公司入口網站中，採用了 Fluent Design System <!-- 1195010 -->
Windows 10 版的 Intune 公司入口網站應用程式已更新為使用 [Fluent Design System's navigation view](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics) \(Fluent Design System 的瀏覽檢視\)。 您會發現應用程式側邊多了一個垂直靜態清單，列有最上層的所有頁面。 按一下任何連結都能快速檢視及來回切換頁面。 我們仍持續努力為 Intune 建立適應性更好、更彈性、更直觀及更加容易上手的體驗，而這只是好幾個更新中的第一個。 若要查看更新後的外觀，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

## <a name="week-of-april-16-2018"></a>2018 年 4 月 16 日當週

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>使用適用於 iOS 的 Cisco AnyConnect 用戶端 <!-- 1333708 -->

針對 iOS 建立新的 VPN 設定檔時，現在有兩個選項：**Cisco AnyConnect** 和 **Cisco Legacy AnyConnect**。 Cisco AnyConnect 設定檔支援 4.0.7x 和較新版本。 現有的 iOS Cisco AnyConnect VPN 設定檔會標記為 **Cisco Legacy AnyConnect**，但仍會繼續以目前的方式搭配 Cisco AnyConnect 4.0.5x 和較舊版本運作。

> [!NOTE]
> 這項變更只適用於 iOS。 Android、Android Enterprise 工作設定檔及 macOS 平台仍然只有一個 Cisco AnyConnect 選項。

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>現在可以使用 Intune 註冊 Jamf 註冊的 macOS 裝置 <!-- 2370684 -->

版本 1.3 和 1.4 的 macOS 公司入口網站並未使用 Intune 成功註冊 Jamf 裝置。 版本 1.4.2 的 macOS 入口網站已修正此問題。


## <a name="week-of-april-9-2018"></a>2018 年 4 月 9 日當週  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>更新 Android 版公司入口網站應用程式的說明體驗 <!-- 1631531 -->

我們已更新 Android 公司入口應用程式的說明體驗，以符合 Android 平台的最佳做法。 現在，當使用者在應用程式中遇到問題時，可以點選 [功能表] > [說明]，然後：
- 向 Microsoft 傳送診斷記錄。
- 傳送描述問題和事件識別碼的電子郵件給公司支援人員。  

若要了解已更新的說明體驗，請參閱[使用電子郵件來傳送記錄](/intune-user-help/send-logs-to-your-it-admin-by-email-android)和[將錯誤傳送給 Microsoft](/intune-user-help/send-logs-to-microsoft-android)。


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>新註冊失敗趨勢圖和失敗原因表 <!-- 1471783 -->

在 [註冊概觀] 頁面上，您可以檢視註冊失敗趨勢和前五大失敗原因。 按一下圖表或資料表，即可向下鑽研至詳細資料來尋找疑難排解建議和補救建議。

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>更新設定應用程式保護原則的位置 <!-- 2144597 -->

在 Azure 入口網站的 Microsoft Intune 服務內，我們會暫時將您從 [Intune 應用程式防護] 服務刀鋒視窗重新導向至 [行動應用程式] 刀鋒視窗。 請注意，您所有的應用程式防護原則都已經在 Intune 中應用程式組態底下的 [行動應用程式] 刀鋒視窗上。 若前往 Intune 應用程式防護，您就會直接前往 Intune。 在 2018 年 4 月，我們將停止重新導向，並完全移除 [Intune 應用程式防護] 服務刀鋒視窗，如此一來 Intune 中的應用程式防護原則只會有一個位置。 

**此變更會對我造成什麼影響？**
這項變更會影響 Intune 獨立部署客戶和混合部署 (Intune 搭配 Configuration Manager) 客戶。 此整合將有助於簡化您的雲端管理。

**我需要為這項變更做什麼準備？**
請將 [Intune] 標記為我的最愛，而不是 [Intune 應用程式防護] 服務刀鋒視窗，並確定您熟悉 Intune 內 [行動應用程式] 刀鋒視窗中的應用程式保護原則工作流程。 在短時間內，我們會進行重新導向，然後就會移除 [應用程式保護] 刀鋒視窗。 請記住，所有應用程式保護原則都已經在 Intune 中，而您可以修改任何條件式存取原則。 如需有關修改條件式存取原則詳細資訊，請參閱 [Azure Active Directory 中的條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。 如需其他資訊，請參閱[什麼是應用程式保護原則？](app-protection-policy.md) 


## <a name="week-of-april-2-2018"></a>2018 年 4 月 2 日當週

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!--1412866 -->
我們已經發行 iOS 版 公司入口網站應用程式的主要使用者經驗更新。 此更新採用全新現代化外觀的視覺設計。 應用程式的功能不變，但強化了可用性與協助工具功能。  

此外還包括：
- iPhone X 的支援。
- 應用程式啟動速度與載入回應的速度變快，可以節省使用者寶貴的時間。
- 增加更多的進度列，方便使用者掌握最新旳狀態資訊。
- 改善使用者上傳記錄的方式，方便在發生問題時回報。  

若要查看更新後的外觀，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>使用 Intune APP 和 CA 來保護內部部署 Exchange 資料 <!-- 1056954 -->
您現在可以搭配 Outlook Mobile 使用 Intune「應用程式原則保護」(APP) 和「條件式存取」(CA) 來保護對內部部署 Exchange 資料的存取。 若要在 Azure 入口網站內新增或修改應用程式保護原則，請選取 [Microsoft Intune] > [用戶端應用程式] > [應用程式保護原則]。 開始使用此功能之前，請確定您符合 [iOS 版和 Android 版 Outlook 的需求](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)。

## <a name="notices"></a>通知

### <a name="upcoming-password-enforcement-change-for-macos-10142-in-intune---1873216--"></a>Intune 中 macOS 10.14.2 即將發生的密碼強制變更 <!--1873216-->
我們在七月的 MC145129 中分享了 Intune 打算整合 Apple 最近推出的「在下次驗證時變更密碼」設定 (針對執行 macOS 10.13 與更新版本的裝置)。 我們最近打算在二月針對 macOS 10.14.2 與更新版本推出此設定。 

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
若您擁有或即將擁有執行 macOS 10.14.2 與更新版本的裝置，這會對您造成影響。 既然 Apple 已推出「在下次驗證時變更密碼」設定，Intune 可以強制使用者在系統推播密碼原則時將其密碼更新為符合規範的密碼。 當我們整合此新的 Apple 功能後，即使您 macOS 使用者的密碼已符合規範，仍會收到更新密碼的要求。 請注意，若密碼已符合規範且您沒有不得使用重複之密碼的需求，則終端使用者將能更新為其現有密碼。 當終端使用者嘗試驗證或登入其裝置時，他們只會看到要求更新其密碼的要求。 如果您在裝置標示為符合規範前都一直封鎖公司資源，則執行 macOS 10.14.2 之裝置上的使用者可能會被封鎖而無法存取公司資源，例如電子郵件或 SharePoint 網站，直到他們重設密碼為止。 在未來，設定和合規性密碼原則的所有更新，都會強制目標使用者更新密碼。 我們在實作此變更之前的客戶研究指出大部分的客戶都不會受此變更影響，因為終端使用者通常會在收到以密碼註冊或重設其密碼以符合規範的要求時更新其密碼

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
建議通知您的技術支援中心。 當此變更推出時，我們將會更新這個 [新功能] 頁面。如果您不想讓系統強制套用此 macOS 裝置密碼原則，建議您取消指派或刪除您現有的 macOS 原則。


### <a name="reminder-intune-support-experience-for-premier-customers-now-in-azure-instead-of-mpo---2828727--"></a>提醒：頂級客戶的 Intune 支援體驗現在位於 Azure instead 中，而非 MPO 中 <!--2828727-->
我們在九月於 MC147649 中分享我們會在十二月移除從 Microsoft 線上頂級支援 (MPO) 入口網站 (premier.microsoft.com) 建立 Intune 支援要求的功能。 現在，在些許的延遲之後，在一月底，系統會將您重新導向以僅在 Azure 上於 Intune 中建立支援要求。 


#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
在一月底之後，為繼續加強頂級支援體驗，您將無法在 MPO 中建立支援要求。  當您嘗試這樣做時，您將會看到一個將無法關閉的提示，說明您將被重新導向到 Azure 上的 Intune。 在這裡，您可以建立將轉送到 Intune 專屬 Microsoft 支援服務的支援票證，以及時診斷及解決您的問題。 請注意，無法在 Azure 入口網站中檢視在 MPO 入口網站中建立的支援要求。 

Azure 入口網站有新的支援體驗，就像我們最近在 MC171941 中所公告一樣。 您可以在 [https://aka.ms/new_support_experience](https://aka.ms/new_support_experience) 與「額外資訊」連結找到詳細資訊。

若您使用混合式行動裝置管理 (混合式 MDM) 或使用共同管理，您可以繼續使用 MPO 來建立 ConfigMgr 的支援要求，但應該使用 Azure 入口網站來建立 Intune 的支援要求。 提醒您，混合式 MDM [已過時](https://docs.microsoft.com/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)，您應該計劃儘快移轉到 Azure 上的 Intune。 如需詳細資訊，請參閱 [Move from Hybrid Mobile Device Management to Intune on Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) (從混合式行動裝置管理移到 Azure 上的 Intune)。

請注意，只有全域管理員、Intune 服務管理員與服務支援管理員角色可以在 Azure 入口網站中建立支援票證。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
- 停止使用 MPO 並使用 Azure 上的 Intune 來建立及管理您的所有 Intune 支援要求。  
- 通知您的技術服務人員並視需要更新文件。
- 若您有使用者目前正於 MPO 中建立支援要求，但他們並沒有全域管理員或 Intune 服務管理員角色，請將 Azure Active Directory 中的服務支援管理員角色指派給他們，以便他們可以繼續在 Azure 入口網站中建立支援票證。

#### <a name="additional-information"></a>其他資訊
[https://aka.ms/IntuneSupport_MPO_to_Azure](https://aka.ms/IntuneSupport_MPO_to_Azure)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>規劃變更：iOS 版 Intune 公司入口網站應用程式的使用者體驗更新
很高興宣布 Intune 很快就會發佈主要使用者體驗更新到 iOS 公司入口網站應用程式。 該更新包括重新設計的首頁視覺呈現，以及進階篩選和更快的應用程式與書籍存取速度。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
這個使用者體驗更新 (維持了目前的 iOS 公司入口網站功能) 包含：
- 具有原生 iOS 外觀和感覺的首頁 
- 內容清單篩選功能，以及搜尋功能，包括依內容類型 (應用程式或電子書) 篩選的功能，以及可用性 (必要裝置管理或不需註冊的可用性)
- 搜尋電子書的功能
- 應用程式與電子書搜尋記錄 若您已加入 Apple TestFlight 計畫，當發行前版本的 Intune 已更新 iOS 公司入口網站應用程式推出時，您將會收到通知。 若您未加入 Apple TestFlight 計畫，現在註冊不會太晚。 註冊可讓您在使用者可使用已更新的公司入口網站應用程式之前先行使用。 您也有機會直接提供意見反應給 Intune 小組。  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？
您不需要採取任何動作，這些變更將會在即將推出的 iOS CP 應用程式版本中發行。 

#### <a name="additional-information"></a>其他資訊
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="plan-for-change-exchange-online-to-intune-connector-will-not-be-available-in-intune----3105122---"></a>規劃變更：Exchange Online 至 Intune 連接器將不會在 Intune 中提供 <!-- 3105122 -->
為了簡化 Exchange Online 和條件式存取的使用體驗，我們將會停用 Exchange Online 至 Intune「服務對服務」連接器。 此變更將會從 12 月服務更新開始，並在 2019 年 2 月服務更新完成。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
您之所以接收到此訊息的原因，是因為我們的記錄顯示您可能正在您的環境中使用「服務對服務」連接器功能。 「服務對服務」連接器支援針對適用於 Exchange Online 之 Exchange Active Sync Only 裝置的 Intune 管理，且不支援內部部署基礎結構。 此連接器在主控台上的顯示方式，會讓人認為它是條件式存取 (CA) 的必要項目，但事實上 CA 並不需要它。 為了在主控台中釐清此情況，我們將會在針對 Intune 服務的 12 月更新中停用設定新連接器的按鈕。 接著，在 2019 年 2 月，所有現有的 Exchange Online 至 Intune 連接器都會被停用。

如果您在您的環境中使用這些連接器，在我們於 2 月停用連接器之後，您將無法在 Intune 中監視或抹除 Exchange Active Sync Only 裝置。 此變更期間預期不會對您的使用者造成任何影響。

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>我該如何為此變更做準備？

如果您已設定服務對服務連接器，並具有 Exchange Active Sync Only 裝置，請切換成其他方法以管理您的裝置。 下列選項可供您選擇：

- 在行動裝置管理 (MDM) 中註冊裝置
- 使用 Intune 應用程式防護原則來管理裝置
- 使用在這裡的文件中所概述的 Exchange 控制項。 

#### <a name="additional-information"></a>其他資訊
[設定 Intune 和 Exchange Online 的 Exchange 服務連接器](https://docs.microsoft.com/intune/exchange-service-connector-configure)



### <a name="plan-for-change-performance-updates-to-intune-for-education---1750215--"></a>規劃變更：Intune 教育版的效能更新 <!--1750215-->
我們將為 Intune 教育版新增一些更新，以提高您指派設定給使用者或裝置時的速度和可靠性。 在此變更過程中，您的原則或設定指派將於 11 月底前移至新群組。

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？

身為 Intune 教育版客戶，您有兩個動態 Azure Active Directory (Azure AD) 群組：[所有使用者] 和 [所有裝置]。 透過這些更新，Azure AD 群組 [所有使用者] 和 [所有裝置] 將不會顯示在 Intune 教育版主控台中。 不過，它們仍會顯示在 Azure 上的 Intune 主控台中，並將重新命名為 [所有使用者 (已淘汰，請勿使用)] 和 [所有裝置 (已淘汰，請勿使用)]。

當更新推出時，您將不再需要使用 Azure AD 群組來指派 Intune 中的應用程式和設定。 相反地，您的「設定」指派將會移至 Intune 教育版主控台中我們將為您建立的新群組，這些新群組仍會和以前一樣顯示為 [所有使用者] 和 [所有裝置]。 這些變更是在後端進行，因此您不會注意到 Intune 教育版主控台有何不同。 預期不會影響您的終端使用者或已註冊的裝置。 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
您無須採取任何動作，我們將為您移動原則指派。 如果您目前在 Intune 教育版主控台中指派原則，請繼續這麼做。

如果您目前將原則指派給 Azure 上 Intune 中的 Azure AD 群組 (如上所述)，請開始改為將這些原則指派給 Intune 教育版主控台中的 [所有使用者] 和 [所有裝置] 群組。 當您看到 Azure AD 群組在主控台中重新命名為已淘汰時，請停止在 Azure AD 中指派原則。 如果您目前基於任何其他目的使用重新命名的群組，則應加以刪除。


### <a name="take-action-please-update-your-android-device-restriction-or-compliance-policy-password-settings-in-intune"></a>採取動作：請在 Intune 中更新 Android 裝置限制或合規性原則的密碼設定
Intune 將針對 Android 4.4 和更新版本的裝置移除「裝置預設」這個可用密碼類型。 由於 Android 平台和裝置的預設差異，裝置通常會將該原則視為選擇性原則。 若要清除在 Android 上強制執行這項設定所產生的混淆，我們將會在即將推出的版本中從 UI 移除這項設定。 
#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
- 如果您的目的是在裝置上要求密碼，建議您不要使用「裝置預設」，您可以編輯 Android 平台設定檔，清楚表達所需的密碼類型。
- 如果您的目的是讓終端使用者決定是否要建立密碼，請選取 [不設定] 按鈕。 我們從 UI 移除這項設定時，如果仍然設定了此設定，系統將在您下一次編輯設定檔時提示您選擇「裝置預設」以外的值。
我需要為這項變更做什麼準備？
檢閱 Android 和 Android 企業裝置限制與合規性原則中的密碼設定。 這些會列在 [合規性原則] 的 [系統安全性]，以及 [裝置限制] 的 [裝置密碼] 或 [工作設定檔] 設定底下。 其他資訊包含更多詳細資料的連結和指定這些設定的螢幕擷取畫面。
#### <a name="additional-information"></a>其他資訊
https://aka.ms/PasswordSettings 

