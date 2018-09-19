---
title: 舊版
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: beee1462c1b6e683287b4d304df386ce525be820
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141630"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Microsoft Intune 的初期版 - 2018 年 9 月

> [!Note]
> NDA 通知：下列變更正在 Intune 的開發過程中。 此資訊會在極有限的基礎下根據 NDA 共用。 請不要在社交媒體或公用網站上張貼任何此資訊，例如 Twitter、UserVoice、Reddit 等等。 

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單 (透過 NDA 共用)。 此資訊以有限的基礎提供，並可能有所變更。 請不要在 UserVoice 上推文、張貼，或在您公司的外部分享此資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>受控 Android 和 iOS 裝置上的 Intune 應用程式使用者帳戶存取 <!-- ! 1248496  -->

身為 Microsoft Intune 系統管理員，您將可以控制在受控裝置上要新增到 Microsoft Office 應用程式的使用者帳戶。 您將可以僅允許組織使用者帳戶進行存取，並封鎖已註冊裝置上的個人帳戶。 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>在執行 Windows 10 的裝置上於 VPN 組態設定檔中建立 DNS 尾碼 <!-- 1333668 -->
當您建立 VPN 裝置組態設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] 平台 > [VPN] 設定檔類型) 時，您需要輸入一些 DNS 設定。 您將也能夠在 Intune 中輸入多個 **DNS 尾碼**。 使用 DNS 尾碼時，您可以使用其簡短名稱來搜尋網路資源，而不需使用完整網域名稱 (FQDN)。 此更新也可讓您在 Intune 中變更 DNS 尾碼的順序。
[Windows 10 VPN 設定](vpn-settings-windows-10.md#dns-settings)列出目前的 DNS 設定。
適用於：Windows 10 裝置

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>適用於 Android 企業工作設定檔的 Always-On VPN 支援 <!-- 1333705 -->
您將可以在 Android 企業裝置上搭配受控的工作設定檔來使用 Always-On VPN 連線。 在使用者將裝置解除鎖定、裝置重新啟動，或是變更無線網路時，Always-On VPN 連線將會保持連線或立即重新連線。 您也可以將連線設定成「鎖定」模式，這會封鎖所有流量，直到 VPN 連線開始作用為止。
Always-On VPN 設定將會位於 [裝置設定] > [設定檔] > [建立設定檔] > [Android 企業] 平台 > [僅限工作設定檔] 下的 [裝置限制] 設定檔類型 > [連線能力] 設定。 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>iOS 和 Android 版 Outlook 應用程式設定原則 <!--1828527 -->
您將能夠為 iOS 建立 iOS 和 Android 版 Outlook 應用程式設定原則。 其他組態設定將會隨著我們針對 iOS 和 Android 版 Outlook 啟用它們之後加入。

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>從遠端鎖定不符合規範的裝置 <!-- 2064495 -->
當裝置不符合規範時，您將能夠在合規性原則上建立從遠端鎖定該裝置的動作。 在 Intune > [裝置合規性] 中建立新原則或選取現有的原則。 選取 [因不符合規範而採取的動作] > [新增]，然後選擇以從遠端鎖定裝置。
支援於： 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 和更新版本 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>已註冊 MDM 之 iOS 裝置上的 Intune 應用程式資料轉送設定 <!-- 2244713 -->
您將能夠把已註冊 MDM 之 iOS 裝置上的 Intune 應用程式資料轉送設定的控制，與指定已註冊使用者的身分識別區分開來。 不使用 IntuneMAMUPN 的系統管理員將不會發現行為變更。 當此功能可用時，使用 IntuneMAMUPN 來控制已註冊裝置上資料轉送行為的系統管理員，應檢閱新的設定並視需要更新其應用程式設定。

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>在 Windows 10 Wi-Fi 設定檔中使用預先共用金鑰 <!-- 2662938 -->
您將能夠搭配 WPA/WPA2-Personal 安全性通訊協定使用預先共用金鑰 (PSK)，來驗證適用於 Windows 10 的 Wi-Fi 組態設定檔。
目前您必須匯入 Wi-Fi 設定檔或是建立自訂的設定檔，才能使用預先共用金鑰。 [適用於 Windows 10 的 Wi-Fi 設定](wi-fi-settings-windows.md)列出目前的設定。 

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>將 Autopilot 裝置同步頻率提升至每 12 小時同步一次 <!-- 2753673 -->
Autopilot 裝置將會每 12 小時同步一次，而不是每 24 小時。

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置 <!-- 1558983 -->
您可以將 Autopilot 設定檔套用至尚未註冊至 Autopilot 的已註冊 Win 10 裝置。 在 Autopilot 設定檔中，選擇 [將所有目標裝置轉換為 Autopilot] 選項，以將所有非 Autopilot 的裝置自動註冊至 Autopilot 部署服務。 等候 48 小時讓註冊處理完畢。 當裝置取消註冊並重設時，Autopilot 將會自動佈建它。 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>建立並指派多個註冊狀態頁面設定檔至 Azure AD 群組 <!-- 2526564-->
您將能夠建立和指派多個註冊狀態頁面設定檔至 Azure AAD 使用者群組。

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune 登陸頁面更新和節點重新命名 <!--2867309 -->
針對 Intune 登陸頁面的更新將包含全新變更的監視磚，以及能讓資料視覺效果更好的圖表。 [行動應用程式] 節點將會變更為 [用戶端應用程式]。

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>使用公司入口網站應用程式提升使用者存取 <!-- 772203 -->
使用者將能夠從公司入口網站應用程式存取重要的帳戶動作，例如密碼重設和其 AAD 設定檔。

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>將 SCEP 憑證發給無使用者的裝置 <!-- 1744554 -->
目前憑證只能發給使用者。 未來您將能夠將 SCEP 憑證發給裝置，包括 Kiosk 等無使用者的裝置 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] 平台 > [SCEP 憑證] 設定檔)。 其他更新將包含：
- SCEP 設定檔中的 [主體] 屬性現已是自訂的文字方塊，且可以包含新的變數。 
- SCEP設定檔中的 [主體別名 (SAN)] 屬性現已是表格格式，且可以包含新的變數。 系統管理員可以在表格中新增屬性，並在自訂的文字方塊中填入值。 SAN 將支援下列屬性： 
  - DNS
  - 電子郵件地址
  - UPN 您將能夠在自訂值文字方塊中以靜態文字新增這些屬性。 例如，DNS 屬性可以新增為 `DNS = {{AzureADDeviceId}}.domain.com`。
  > [!NOTE]
  > 大括弧、分號和直立線符號「{ } ; |」在 SAN 的靜態文字中沒有作用。 大括弧只能括住其中一個新的裝置憑證變數，`Subject` 或 `Subject alternative name` 才會接受它。 新的裝置憑證變數：  
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



<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>另一個 MDM 所使用的 Apple VPP 權杖 <!-- 1488946 -->
如果 Intune 和另一個 MDM 都正在使用 Apple 大量採購方案 (VPP) 權杖，則 Intune 會偵測並顯示詳細資料。

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>會顯示 iOS 版本號碼和組建編號 <!-- 1892471 -->
在 [裝置合規性] > [裝置合規性] 中，會顯示 iOS 作業系統版本。 在未來的更新中，也會顯示組建編號。
發行安全性更新時，Apple 通常會保留版本號碼，但更新組建編號。 顯示組建編號，即可輕鬆地檢查是否已安裝弱點更新。

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>[裝置合規性] 儀表板中的已淘汰裝置 <!-- 1981119 -->
在未來的更新中，將會從 [裝置合規性] 儀表板中移除已淘汰裝置。 這會變更您的合規性數字。


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>內部部署連接器之更新程序中的變更 <!-- 2277554 -->
根據客戶的意見反應，將會變更內部部署連接器更新方式。 在您初次安裝內部部署連接器之後，將會自動更新。 此變更會從新的適用於 Microsoft Intune 的 PFX 憑證連接器開始，之後將推出至其他類型的內部部署連接器。 

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Azure 入口網站中針對 Windows 10 及更新版本 Kiosk 設定檔的改進 <!-- 2748224 eeready -->
將改進 Windows 10 Kiosk 裝置設定檔 ([裝置設定] > [設定檔] > [建立設定檔] > [Windows 10 及更新版本] 平台 > [Kiosk 預覽] 設定檔類型)： 
- 目前，您可以在相同的裝置上建立多個 Kiosk 設定檔。 透過此更新，Intune 針對每部裝置都只會支援單一 Kiosk 設定檔。 如果您仍需要在單一裝置上有多個 Kiosk 設定檔，則可以使用自訂 URI。
在 [多應用程式 kiosk] 設定檔中，您可以針對應用程式格線中的 [[開始] 功能表配置] 選取應用程式磚大小和順序。 如果您想要取得更多自訂項目，您可以繼續上傳 XML 檔案。
- [Kiosk 瀏覽器] 設定會移至 [Kiosk] 設定中。 目前，[Kiosk 網頁瀏覽器] 設定在 Azure 入口網站中具有自己的類別。
適用對象：Windows 10 和更新版本

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>已改善裝置註冊管理員使用者的公司入口網站應用程式體驗 <!-- 675800 -->
當裝置註冊管理員 (DEM) 登入適用於 Windows 的公司入口網站應用程式時，應用程式只會列出 DEM 目前執行中的裝置。 此改善會減少之前應用程式在嘗試載入所有 DEM 註冊裝置時所發生的逾時。  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>檢查 Configuration Manager 合規性 <!-- 2192052 -->
未來更新將會包括新的 System Center Configuration Manager 合規性設定 ([裝置相容性] > [原則] > [建立原則] > [Windows 10])。 Configuration Manager 會將訊號傳送至 Intune 合規性。 您可以使用 Intune 設定來要求所有傳回的 Configuration Manager 訊號都需是「符合規範」。

例如，您需要在裝置上安裝所有軟體更新。 在 Configuration Manager 中，此要求將會對應「已安裝」狀態。 如果裝置上的任何程式處於未知狀態，則裝置在 Intune 中將會不相容。

適用於 Windows 10 和更新版本

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 權杖將過期或公司入口網站授權將不足的警示<!-- 2237572 -->
如果您在 DEP 註冊期間使用大量採購方案 (VPP) 預先佈建公司入口網站，則 Intune 會在 VPP 權杖即將過期以及公司入口網站授權即將不足時提醒您。

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows Installer 的其他安全性設定 <!-- 2282430 -->
您將可以允許使用者控制應用程式安裝。 如啟用，則可讓以安全性違規方式停止的安裝繼續執行。 您將可以指示 Windows Installer 在系統上安裝任何程式時都使用提升的權限。 此外，您將可以將 Windows 資訊保護 (WIP) 項目編入索引，並將跟它們有關的中繼資料儲存在未加密的位置。 停用此原則時，不會編製 WIP 保護項目的索引，且不會出現在 Cortana 或檔案總管的結果中。 預設會停用這些選項的功能。 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS 上的應用程式設定可封鎖第三方鍵盤 <!-- 1248481 -->
在 iOS 裝置上，Intune 系統管理員可以在存取原則保護應用程式中的組織資料時，封鎖第三方鍵盤的使用。 當應用程式保護原則 (APP) 設定為封鎖第三方鍵盤時，裝置使用者會在第一次使用第三方鍵盤與公司資料互動時收到一則訊息。 本機鍵盤以外的所有選項都會被封鎖，裝置使用者不會看到它們。 裝置使用者只會看到對話方塊訊息一次。 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 語言套件 <!-- 1833450 -->
身為 Intune 系統管理員，您將可以為透過 Intune 管理的 Office 365 專業增強版應用程式部署其他語言。 可用的語言清單包括語言套件的**類型** (核心、部分和校訂)。 在 Azure 入口網站中，選取 [Microsoft Intune] > [行動裝置應用程式] > [應用程式] > [新增]。 在 [新增應用程式] 刀鋒視窗的 [應用程式類型] 清單中，選取 [Office 365 套件] 下的 [Windows 10]。 選取 [應用程式套件設定] 刀鋒視窗中的 [語言]。

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>在指定的逾時之後要求非生物特徵辨識 <!-- 1506985 --> 

透過在系統管理員指定的逾時之後要求非生物特徵辨識 PIN，Intune 可藉由限制使用生物特徵辨識身分識別來存取公司資料，為啟用行動應用程式管理 (MAM) 的應用程式增強安全性。 這些設定會影響依賴 Touch ID (iOS)、Face ID (iOS)、 Android 生物特徵辨識或其他未來的生物特徵辨識驗證方法來存取其啟用 APP/MAM 之應用程式的使用者。 這些設定可讓 Intune 系統管理員能夠更細微地控制使用者存取，並排除具有多個指紋或其他生物特徵辨識存取方法的裝置可能會向不正確的使用者顯示公司資料的情況。 在 Azure 入口網站中，開啟 [Microsoft Intune]。 選取 [行動裝置應用程式] > [應用程式保護原則] > [新增原則] > [設定]。 找出特定設定的 [存取] 區段。

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>更新 Android 的公司入口網站應用程式之說明與意見反應體驗 <!--1631531 -->

Android 公司入口網站應用程式的說明和意見反應體驗將更新，以與 Android 應用程式的最佳做法保持一致。 Android 公司入口網站應用程式將於接下來幾個月內更新，以將 [說明與意見反應] 功能表項目劃分為分開的 [說明] 與 [傳送意見反應] 功能表項目。 **說明**頁面將有**常見問題集**章節和**電子郵件支援** 按鈕，引導使用者上傳記錄給 Microsoft，並將電子郵件傳送給描述問題的公司支援。 **傳送意見反應**會透過標準 Microsoft 意見反應提交來引導使用者，並會提示使用者選擇「我喜歡某些項目」、「我不喜歡某些項目 」，或是「我有個想法」。



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>通知

目前沒有任何作用中的通知。

### <a name="see-also"></a>另請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。



