---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6cc33bc6e03d2e0370c9e2c2dd9d3462296710e6
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329679"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Microsoft Intune 的舊版 - 2018 年 8 月

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

<!-- 1808 start -->



### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>會顯示 iOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性] > [裝置合規性] 中，會顯示 iOS 作業系統版本。 在未來的更新中，也會顯示組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 顯示組建編號，即可輕鬆地檢查是否已安裝弱點更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>公司入口網站的新使用者體驗更新 <!--2000968 -->
將會根據客戶的意見反應，將新功能新增至公司入口網站。 您可在 Android、iOS 和 Windows 裝置上體驗現有功能和可用性方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 將獲得全新的現代化回應式設計。 此外還包括：
- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 更容易使用的語言，較少的技術專業術語
- 可以共用應用程式的直接連結
- 改善大型應用程式目錄的效能
- 增加所有使用者的協助工具

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>設定設定檔，以在設定助理期間略過一些畫面 <!-- 2276470 -->
當您建立 macOS 註冊設定檔時，可以將它設定成在使用者完成設定助理時略過下列任何畫面：
- Android 移轉
- 顯示色調
- 隱私權
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>內部部署連接器之更新程序中的變更 <!-- 2277554 -->
根據客戶的意見反應，將會變更內部部署連接器更新方式。 在您初次安裝內部部署連接器之後，將會自動更新。 這項變更會從新的適用於 Microsoft Intune 的 PFX 憑證連接器開始，之後將推出至其他類型的內部部署連接器。 



<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>適用於 Windows 之公司入口網站應用程式中的更多同步處理機會 <!-- 2683177 -->
適用於 Windows 之公司入口網站應用程式正在向 Windows 工作列和開始功能表捷徑清單新增裝置同步處理動作。 按一下任一位置以快速同步處理您的裝置，並取得公司資源的存取權。  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>從 Windows 10 的公司入口網站應用程式重設裝置密碼 <!-- 2101282 --> 
您的員工很快可以直接從 Windows 10 的公司入口網站應用程式重設其裝置的 PIN 或密碼。 此功能將用於支援密碼重設的遠端及本機 Intune 受控裝置。 根據裝置類型，針對遠端裝置所提出的要求將會移除裝置的目前密碼，或建立暫時密碼。 要求重設本機裝置的使用者，將會重新導向至裝置的 [設定] 應用程式。  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>適用於 Windows 之公司入口網站應用程式的新瀏覽體驗 <!-- 2317227 -->  
在適用於 Windows 的公司入口網站應用程式中瀏覽或搜尋應用程式時，您能夠切換現有的**磚**檢視和新增的**詳細資料**檢視。 新的檢視會列出應用程式詳細資料，例如名稱、發佈者、發佈日期，以及安裝狀態。  

[應用程式] 頁面會引入**已安裝**檢視，其可讓您查看有關已完成和進行中之應用程式安裝的詳細資料。 想要分享有關新變更的意見反應或想法嗎？ 請在公司入口網站應用程式中將您的意見反應傳送給我們。

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>已改善裝置註冊管理員使用者的公司入口網站應用程式體驗 <!-- 675800 -->
當裝置註冊管理員 (DEM) 登入適用於 Windows 的公司入口網站應用程式時，應用程式只會列出 DEM 目前執行中的裝置。 這項改善會減少之前應用程式在嘗試載入所有 DEM 註冊裝置時所發生的逾時。  

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>在 DEP 註冊期間，使用 VPP 裝置授權預先佈建公司入口網站 <!-- 1608345 -->
您將可以在裝置註冊計劃 (DEP) 註冊期間，使用大量採購方案 (VPP) 裝置授權預先佈建公司入口網站。 若要這麼做，當您建立或編輯註冊設定檔時，請指定您要用來安裝公司入口網站的 VPP 權杖。 請確定您的權杖未過期，而且您有足夠的公司入口網站應用程式權限。 如果權杖過期或授權不足，則 Intune會改為推送 App Store 公司入口網站 (這會提示您輸入 Apple 識別碼)。

### <a name="check-for-sccm-compliance----2192052---"></a>檢查 SCCM 相容性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager (SCCM) 相容性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 SCCM 將訊號傳送給 Intune 相容性。 使用 Intune 設定，您可能需要所有 SCCM 訊號傳回「相容」。

例如，您需要在裝置上安裝所有軟體更新。 在 SCCM 中，此需求會有「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>需要確認刪除將用於預先佈建公司入口網站的 VPP 權杖 <!-- 2237634 -->
如果在 DEP 註冊期間將使用大量採購方案 (VPP) 權杖來預先佈建公司入口網站，則需要確認刪除該權杖。

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全性設定 <!-- 2282430 -->
您可以允許使用者控制應用程式安裝。 如啟用，則可讓以安全性違規方式停止的安裝繼續執行。 您可以指示 Windows Installer 在系統上安裝任何程式時使用提升的權限。 此外，您可以將 Windows 資訊保護 (WIP) 項目編入索引，並將跟其有關的中繼資料儲存在未加密的位置。 停用此原則時，不會編製 WIP 保護項目的索引，且不會出現在 Cortana 或檔案總管的結果中。 預設會停用這些選項的功能。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>在應用程式啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 -->

透過在應用程式啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [用戶端應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 語言套件 <!-- 1833450 -->
身為 Intune 系統管理員，您可以為透過 Intune 管理的 Office 365 Pro Plus 應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune] > [用戶端應用程式] > [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗的 [應用程式類型] 清單中，選取 [Office 365 套件] 下的 [Windows 10]。 選取 [應用程式套件設定] 刀鋒視窗中的 [語言]。

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>預覽公司入口網站的新使用者體驗更新 <!--2000968 -->
我們正在依據客戶的意見反應，將新功能新增至公司入口網站/iOS 應用程式目錄。 您可在 Android、iOS 和 Windows 裝置上體驗現有功能和可用性方面的重大改善。 網站的各個區域 (例如裝置詳細資料、意見反應和支援，以及裝置概觀) 將獲得全新的現代化回應式設計。 此外還包括：

- 簡化所有裝置平台中的工作流程
- 改善裝置識別和註冊流程
- 更有用的錯誤訊息
- 更容易使用的語言，較少的技術專業術語
- 可以共用應用程式的直接連結
- 改善大型應用程式目錄的效能
- 增加所有使用者的協助工具

更新目前為預覽狀態。 您可在 http://aka.ms/webcpflighting 註冊加入預覽

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>在應用程式冷啟動和逾時時需要非生物特徵辨識密碼 <!-- 1506985 --> 

透過在應用程式冷啟動時和系統管理員指定的逾時之後要求非生物特徵辨識密碼，Intune 可藉由限制使用生物識別存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [用戶端應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>在 Windows 10 Desktop 裝置上，將所需之企業營運 (LOB) 應用程式部署給所有使用者的能力 <!-- 1627835 RS4 -->
客戶將能夠部署必要的企業營運 Windows 10 應用程式，以安裝在裝置內容中。 這會向裝置上的所有使用者開放使用這些應用程式。 這僅適用於 Windows 10 Desktop 裝置。

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

Android 公司入口網站應用程式的說明和意見反應體驗將更新，以與 Android 應用程式的最佳做法保持一致。 Android 公司入口網站應用程式將於接下來幾個月內更新，以將 [說明與意見反應] 功能表項目劃分為分開的 [說明] 與 [傳送意見反應] 功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



