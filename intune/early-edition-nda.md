---
title: 舊版 - Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 舊版
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: 0efc84da6a9efb594600b9ca33aa5eb7622c8101
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203428"
---
# <a name="the-early-edition-for-microsoft-intune---january-2019"></a>Microsoft Intune 的舊版 - 2019 年 1 月

> [!Note]
> NDA 通知：下列變更正在 Intune 的開發過程中。 這項資訊會在極有限的基礎下根據 NDA 共用。 請不要在社交媒體或公用網站上張貼任何這項資訊，例如 Twitter、UserVoice、Reddit 等等。 

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單 (透過 NDA 共用)。 此資訊以有限的基礎提供，並可能有所變更。 請不要在 UserVoice 上推文、張貼，或在您公司的外部分享這項資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1901 start -->

### <a name="android-enterprise-apps----1352553----"></a>Android Enterprise 應用程式 <!-- 1352553  -->
您將能夠從 Microsoft Intune 刪除受控 Google Play 應用程式。 若要刪除受控 Google Play 應用程式，請在 Azure 入口網站中開啟 Microsoft Intune，然後選取 [用戶端應用程式] > [應用程式]。 從應用程式清單，選取受控 Google Play 應用程式右側的省略符號 (...)，然後從顯示的清單選取 [刪除]。 當您從應用程式清單刪除受控 Google Play 應用程式時，會自動取消核准受控 Google Play 應用程式。

### <a name="managed-google-play-app-type----1352580---"></a>受控的 Google Play 應用程式類型 <!-- 1352580 -->
[受控的 Google Play] 應用程式類型可讓您將[受控 Google Play 應用程式](https://play.google.com/work/search?q=microsoft&c=apps)明確新增至 Intune。 身為 Intune 系統管理員，您現在能夠在 Intune 中瀏覽、搜尋、核准、同步及指派已核准的受控 Google Play 應用程式。 您不再需要另外瀏覽至受控的 Google Play 主控台，而且您不再需要重新驗證。 在 Intune 中，選取 [用戶端應用程式] > [應用程式] > [新增]。 在 [應用程式類型] 清單中，選取 [受控的 Google Play] 作為應用程式類型。

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>公司擁有、完全受控的 Android 裝置支援預覽 <!-- 1574342  -->
Intune 將支援完全受控的 Android 裝置，此為公司擁有的「裝置擁有者」案例，其中的裝置會受到 IT 嚴格管理並隸屬於個別使用者。 這讓系統管理員能夠管理整個裝置、強制設定無法用於工作設定檔之原則控制項的延伸範圍，並限制使用者只能從受控的 Google Play 安裝應用程式。 若要設定完全受控的 Android 裝置，請移至 [裝置註冊] > [Android 註冊] > [公司擁有、完全受控的使用者裝置]。 請注意，此功能處於預覽狀態。 完全受控的 Android 使用者裝置目前不提供某些 Intune 功能，例如憑證、合規性和條件式存取。

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>線上授權商務用 Microsoft Store 應用程式的部署 <!-- 1672660  -->
您將能夠在裝置內容中指派必要的線上授權商務用 Microsoft Store 應用程式。 以此方式部署商務用 Microsoft Store 應用程式，即可在裝置上為所有使用者安裝應用程式。 這僅適用於 Windows 10 RS4+ 電腦裝置。 您可以從 MSFB 線上授權應用程式的用戶端應用程式指派頁面，存取在裝置內容中安裝的選項。

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>設定設定檔，以在設定助理期間略過一些畫面 <!-- 2276470  -->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- Android 移轉
- 顯示色調
- 隱私權
- iCloudStorage

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522----"></a>將 Autopilot 設定檔指派給所有裝置虛擬群組 <!--2715522  -->
您將可以將 Autopilot 設定檔指派給所有裝置虛擬群組。 若要進行此動作，請選擇 [裝置註冊] > [Windows 註冊] > [部署設定檔]> 選擇設定檔 > [指派] > 在 [指派對象] 下方，選擇 [所有裝置]。 如需 Autopilot 設定檔的詳細資訊，請參閱[使用 Windows AutoPilot 註冊 Windows 裝置](enrollment-autopilot.md)。

### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324----"></a>使用裝置組態設定檔自訂受監督 iOS 裝置上的背景圖案 <!-- 2809324  -->
當您建立 iOS 裝置的裝置組態設定檔時，您將能夠在 [裝置設定] > [設定檔] > [建立設定檔] > [iOS] 平台 > [裝置限制] 設定檔類型中，允許和限制一些設定。 此更新包含新的 [底色圖案] 設定，可讓系統管理員使用 .png、.jpg 或 .jpeg 影像作為底色圖案；預覽影像；以及防止使用者變更底色圖案。 底色圖案設定只會套用至受監督的裝置。 如需目前的設定清單，請參閱 [iOS 裝置限制設定](device-restrictions-ios.md)。

### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 應用程式的快顯通知 <!-- 3136566   -->
您將能夠隱藏而不顯示每個應用程式指派的終端使用者快顯通知。 從 Intune 選取 [用戶端應用程式] > [應用程式] > 選取應用程式 > [指派] > [包含群組]。 

### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396---"></a>[透過藍牙分享連絡人] 已從 Android Enterprise 的 [裝置限制] > [裝置擁有者] 中移除 <!-- 3598396 -->
當您建立 Android Enterprise 裝置的裝置限制設定檔時，有一項 [透過藍牙分享連絡人] 設定。 在此更新中，透過藍牙分享連絡人 設定將會被移除 (裝置設定 > 設定檔 > 建立設定檔 > Android Enterprise 平台 > 裝置限制 > 裝置擁有者 設定檔類型 > 一般)。 

Android Enterprise 裝置擁有者管理不支援 [透過藍牙分享連絡人] 設定。 因此，移除此設定之後，並不會影響任何裝置或租用戶，即使您已在環境中啟用和設定此設定亦然。

若要查看目前的設定清單，請前往[允許或限制功能的 Android Enterprise 裝置設定](device-restrictions-android-for-work.md)。

適用於：Android Enterprise 裝置擁有者

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 企業 APP-WE 應用程式部署 <!-- 1171203 -->
針對未註冊的無註冊應用程式保護原則 (APP-WE) 部署案例中的 Android 裝置，您就能使用受控的 Google Play，將市集應用程式和 LOB 應用程式部署給使用者。 具體來說，IT 可以為終端使用者提供應用程式目錄和安裝體驗，藉由允許從不明來源進行安裝，就不再需要終端使用者放寬其裝置的安全性狀態。 此外，此部署案例將提供已改善的使用者體驗。

### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune App SDK 將支援 256 位元的加密金鑰 <!-- 1832174 -->
適用於 Android 的 Intune App SDK 將會在應用程式保護原則啟用加密時，使用 256 位元的加密金鑰。 SDK 將繼續提供 128 位元金鑰的支援，以取得與使用較舊 SDK 版本之內容和應用程式的相容性。


### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 原則會更新驗證方法與公司入口網站應用程式安裝  <!-- 1927359 -->
在已透過 [設定助理] 註冊的裝置上 (透過 Apple 的公司裝置註冊方法之一)，Intune 將不再支援公司入口網站 (當使用者從 App Store 手動安裝時)。 只有當您在註冊期間使用 Apple 設定助理進行驗證時，此變更才有意義。 此變更也只會影響透過下列各項註冊的 iOS 裝置：  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple 裝置註冊方案 (DEP)

如果使用者從 App Store 安裝公司入口網站應用程式，接著嘗試透過它註冊這些裝置，則它們將會收到錯誤。 這些裝置只有在註冊期間透過 Intune 自動推送時，才會使用公司入口網站。 位於 Azure 入口網站上 Intune 中的註冊設定檔將會更新，如此您就能指定裝置的驗證方式，以及它們是否會收到公司入口網站應用程式。 如果您想讓 DEP 裝置使用者擁有公司入口網站，將必須在註冊設定檔中指定喜好設定。 此外，公司入口網站應用程式中的 [識別您的裝置] 畫面很快就會變成過時。  
若要在已經註冊的 DEP 裝置上安裝公司入口網站，您將必須移至 [Intune] > [用戶端應用程式]，然後使用應用程式設定原則來將它推送為受控應用程式。 有關如何執行這些步驟的詳細資料，將在未來的文件中加以概述。

### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379---"></a>非系統管理員可以在已加入 Azure AD 的 Windows 10 裝置上啟用 BitLocker<!-- 2147379 -->
當您在 Windows 10 裝置上啟用 BitLocker 設定 ([裝置設定] > [設定檔] > [建立設定檔] > 針對平台選擇 [Windows 10 及更新版本] > 針對設定檔類型選擇 [Endpoint Protection] > [Windows 加密]) 時，您會新增 BitLocker 設定。 此更新包含新的 BitLocker 設定，可允許標準使用者 (非系統管理員) 啟用加密。 若要查看目前的設定，請參閱[適用於 Windows 10 的 Endpoint Protection 設定](endpoint-protection-windows-10.md#windows-encryption)。


### <a name="additional-settings-for-outlook----3301182---"></a>Outlook 的其他設定 <!-- 3301182 -->
您現在可以使用 Intune 來設定 iOS 和 Android 版 Outlook 的其他設定。  這些設定包括：
- 只允許在 iOS 和 Android 版 Outlook 中使用公司或學校帳戶
- 為 Office 365 和混合式新式驗證內部部署帳戶部署新式驗證
- 選取基本驗證時，針對電子郵件設定檔中的使用者名稱欄位使用 `SAMAccountName`
- 允許儲存連絡人
- 設定外部收件者寄件提醒
- 設定 [焦點收件匣]
- 需要生物識別技術才能存取 iOS 版 Outlook 
- 封鎖外部影像

> [!NOTE]
> 如果您使用 Intune 應用程式防護原則來管理公司身分識別的存取權，您應該考慮不啟用 [require biometrics] \(需要生物識別技術\)。 如需詳細資訊，請參閱 [iOS 存取需求](app-protection-policy-settings-ios.md#access-settings)和 [Android 存取需求](app-protection-policy-settings-android.md#access-settings)中的＜需要公司認證才能存取＞。

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>系統管理範本目前處於公開預覽狀態且已移至它們自己的組態設定檔 <!-- 3322847 -->
Intune 中的系統管理範本 ([裝置設定] > [系統管理範本]) 目前為個人預覽版。 使用此更新：系統管理範本包含約 300 個可在 Intune 中管理的設定。 這些設定先前只存在於群組原則編輯器中。
系統管理範本會在公開預覽版中提供。系統管理範本正從 [裝置設定] > [系統管理範本] 移至 [裝置設定] > [設定檔] >[建立設定檔] > 在 [平台] 中選擇 [Windows 10 及更新版本]、在 [設定檔類型] 中選擇 [系統管理範本]。
已啟用報告。適用對象：Windows 10 及更新版本

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 公司入口網站深色模式 <!-- 3300524 -->
Intune macOS 公司入口網站現在支援 macOS 的深色模式。 當您在 macOS 10.14+ 裝置上啟用 [深色模式] 時，公司入口網站會將其外觀調整為反映該模式的色彩。

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>使用針對安全性基準 <!-- 2055484 --> 的 Microsoft 建議設定
Intune 會和其他著重安全性的服務整合，包含 Windows Defender ATP 和 Office 365 ATP。 客戶持續不斷要求一種常見策略，以及橫跨 Microsoft 365 服務，極具凝聚力的一組端點對端點安全性工作流程。 我們的目標是調整策略，建置能擔任安全性作業和常見系統管理工作間橋樑的解決方案。 在 Intune 中，我們試圖透過發佈一組 Microsoft 建議的「安全性基準」(**Intune** > **安全性基準**)，來達到此目標。  系統管理員將能夠直接從這些基準建立安全性政策，並將它們部署到其使用者。 他們也可以自訂最佳做法建議項目，以符合其組織的需求。 Intune 會確保裝置符合這些基準的規範，並會通知系統管理員不合規的使用者或裝置。

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>無使用者註冊的部署 WIP 原則 <!-- 1434452 -->
Windows 資訊保護 (WIP) 原則將能在無須 MDM 使用者註冊其 Windows 10 裝置的情況下部署。 此設定允許公司根據 WIP 設定保護其公司文件，同時允許使用者維持其自身 Windows 裝置的管理。 一旦使用 WIP 原則保護文件，Intune 系統管理員便可以選擇性抹除受保護的資料。 透過選取使用者和裝置，並傳送抹除要求，所有透過 WIP 原則保護的資料都會無法使用。 從 Azure 入口網站中的 Intune，選取 [行動應用程式] > [應用程式選擇性抹除]。


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>適用於 Web 資料的應用程式防護原則 (APP) 設定 <!-- 2662995 -->
Android 及 iOS 裝置上適用於 Web 內容的應用程式原則設定會進行更新，提升處理 HTTP 和 HTTPS Web 連結的能力，以及透過 iOS 通用連結和 Android 應用程式連結進行資料轉送的能力。  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。



<!-- 1807 start -->

### <a name="check-for-configuration-manager-compliance----2192052---"></a>檢查 Configuration Manager 合規性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用 Intune 設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本



## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



