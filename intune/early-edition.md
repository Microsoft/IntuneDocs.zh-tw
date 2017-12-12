---
title: "舊版"
description: 
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 35bf193563deb34ac59df245c622bbc011d80b76
ms.sourcegitcommit: 67ec0606c5440cffa7734f4eefeb7121e9d4f94f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2017
---
# <a name="the-early-edition-for-microsoft-intune---december-2017"></a>Microsoft Intune 的初期版本 - 2017 年 12 月

**舊版**提供 Microsoft Intune 即將發行版本要推出的功能清單。 此資訊以有限的基礎提供，並可能有所變更。 請不要在貴公司以外的地方分享此資訊。 這裡列出的一些功能可能有截止日期，而且可能會延遲到未來的版本。 其他功能正在實驗 (測試) 中進行測試，以確保它們可供客戶使用。 如果您有任何問題或疑慮，請洽詢您的 Microsoft 產品群組連絡人。

此頁面會定期更新。 請回來查看其他更新。

> [!Note]
>下列變更正在 Intune 的開發過程中。 如需新混合式功能的詳細資訊，請查看我們的[混合式新增功能](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)頁面。

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->


## <a name="intune-in-the-azure-portal"></a>Azure 入口網站中的 Intune

### <a name="app-protection-policies-----679615---"></a>應用程式防護原則 <!-- 679615 -->
Intune 應用程式防護原則能提供建立全域預設原則的能力，以針對整個租用戶中的所有使用者快速啟用保護。

### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤銷 iOS 大量採購方案應用程式 <!-- 820863 -->
對於具有一或多個 iOS 大量採購方案 (VPP) 應用程式的指定裝置，您將可撤銷與該裝置相關連的裝置型應用程式授權。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤銷 iOS 大量採購方案權杖的授權 <!-- 820870 -->
您將可針對指定的 VPP 權杖撤銷所有 iOS 大量採購方案 (VPP) 應用程式的授權。

### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>刪除 iOS 大量採購方案權杖 <!-- 820879 -->
您將可使用主控台來刪除 iOS 大量採購方案 (VPP) 權杖。 當您擁有重複的 VPP 權杖執行個體時，這可能是必要的。

### <a name="network-access-control-nac-device-check-in-reporting-----1232250---"></a>網路存取控制 (NAC) 裝置簽入報告 <!-- 1232250 -->
在此項變更之前，IT 系統管理員無法從 Intune 端判斷受 NAC 管理的裝置是否正與其 NAC 解決方案通訊。 當受 NAC 管理的裝置並未與其 NAC 解決方案通訊時，NAC 解決方案會將裝置視為不符合規範，使該裝置被 NAC 解決方案本身封鎖，並於後續進一步被依賴裝置合規性狀態的條件式存取原則封鎖。

透過這項變更，IT 系統管理員就可看到有哪些受 NAC 管理的裝置已成功與其 NAC 解決方案通訊。 此新功能包含兩個位於 Intune 內的 [裝置合規性] 工作負載中的新監視功能，其統計資料如下：
- **過去一小時內的平均 NAC 呼叫**
- **上次的 NAC 傳入要求 (日期/時間)**

### <a name="new-ios-device-action------1244701---"></a>新的 iOS 裝置動作 <!-- 1244701 -->
您可以關閉 iOS 10.3 受監督的裝置。 這個動作會立即關閉裝置，而不會警告使用者。 您可以在 [裝置] 工作負載中選取裝置時，於裝置屬性中找到 [關機 (僅限受監督)] 動作。

### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755-eeready---"></a>針對 SCEP 和 PFX 憑證處理的多連接器支援 <!-- 1361755 eeready -->
使用內部部署 NDES 連接器將憑證傳遞至裝置的客戶，將可在單一租用戶上設定多個連接器。

此新功能支援下列案例：

- **高可用性**

    每個 NDES 連接器都會從 Intune 提取憑證要求。  如果有某個 NDES 連接器離線，其他連接器將可以繼續處理要求。

### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自動重新部署設定 <!-- 1469168 -->
此設定允許具有系統管理權限的使用者，在裝置鎖定畫面上使用 **CTRL + Win + R** 來刪除所有使用者資料和設定。 裝置將會自動重新設定並重新註冊以納入管理。

您可以在 [Windows 10] -> [裝置限制] -> [一般] -> [自動重新部署] 下找到此設定。

### <a name="install-office-apps-on-macos-devices----1494311---"></a>在 macOS 裝置上安裝 Office 應用程式 <!-- 1494311 -->
您將可在 macOS 裝置上安裝 Office 應用程式。 這個新的應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 及 OneNote。 這些應用程式也會隨附 Microsoft 自動更新程式 (MAU)，以協助保護您的應用程式並使它保持在最新狀態。

### <a name="surface-hub-resource-account-supported----1566442-eeready---"></a>支援 Surface Hub 資源帳戶 <!-- 1566442 eeready -->
將會加入新的裝置動作，以便系統管理員對與 Surface Hub 相關聯的資源帳戶進行定義及更新。

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

### <a name="intune-now-provides-the-account-move-operation-----1573558-1579830---"></a>Intune 現在提供帳戶移動作業 <!-- 1573558, 1579830 -->
**帳戶移動**可將租用戶從某個 Azure 縮放單位 (ASU) 移轉至另一個。 **帳戶移動**可用於客戶起始的案例 (當您呼叫 Intune 支援小組並要求它時)，也可用於由 Microsoft 驅動的案例 (當 Microsoft 需要對後端對服務進行調整時)。 在**帳戶移動**期間，租用戶會進入唯讀模式 (ROM)。 諸如註冊、重新命名裝置、更新合規性狀態等服務作業，在 ROM 期間都將會失敗。

### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 資訊安全中心 (WDSC) 裝置組態設定檔設定 <!-- 1335507 -->
Intune 在 [端點保護] 下新增了新的裝置組態設定檔設定區段，名為 [Windows Defender 資訊安全中心]。 IT 系統管理員可以設定使用者可存取的 Windows Defender 資訊安全中心應用程式方針。 如果 IT 系統管理員在 Windows Defender 資訊安全中心應用程式中隱藏某個方針，則與該隱藏方針相關聯的所有通知都不會顯示在使用者的裝置上。

以下是系統管理員可從 Windows Defender 資訊安全中心裝置組態設定檔設定中隱藏的方針：
- 病毒與威脅防護
- 裝置效能與健康情況
- 防火牆與網路保護
- 應用程式與瀏覽器控制
- 家長監護選項

IT 系統管理員也可以自訂使用者可接收的通知。 例如，您可以設定是否讓使用者接收由 WDSC 中可見方針所產生的所有通知，或僅接收重要通知。 非重大通知包括 Windows Defender 防毒軟體活動的定期摘要，以及掃描完成時的通知。 所有其他通知都被視為重大通知。 此外，您也可以自訂通知內容本身，例如，您可以在顯示於使用者裝置上的通知中內嵌 IT 連絡資訊。




<!-- the following are present prior to 1712 -->
### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>將 Office 365 行動應用程式指派給使用內建應用程式類型的 iOS 和 Android 裝置 <!-- 1332318 -->
**內建** - 應用程式類型能讓您更輕鬆地建立 Office 365 應用程式，並將它們指派給您管理的 iOS 及 Android 裝置。 這些應用程式包括 0365 應用程式，例如 Word、Excel、PowerPoint 和 OneDrive。 您可以將特定的應用程式指派給應用程式類型，並編輯應用程式資訊設定。

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS 的單一登入支援 <!-- 1333645 -->  
您可以讓 iOS 使用者使用單一登入。 編碼成在單一登入裝載中尋找使用者認證的 iOS 應用程式，因為有此裝載設定更新，所以很實用。 您也可以使用 UPN 和 Intune 裝置識別碼來設定主體名稱和領域。

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>允許來自受管理應用程式的文字通訊協定 <!-- 1414050  -->
受 Intune App SDK 管理的應用程式可以傳送簡訊。

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>使用 Intune 從遠端鎖定受管理的 macOS 裝置 <!-- 1437691 -->
您可以鎖定遺失的 macOS 裝置，並設定 6 位數的復原 PIN。 鎖定時，[裝置概觀] 刀鋒視窗會顯示 PIN，直到傳送另一個裝置動作為止。

如需詳細資訊，請參閱[使用 Intune 從遠端鎖定受管理的裝置](device-remote-lock.md)。


### <a name="assignment-conflict-resolution-has-changed-for-ios-store-apps----1480316---"></a>iOS 市集應用程式之指派衝突的解析已變更 <!-- 1480316 -->
使用者可能會遇到 iOS 市集應用程式可用性的變更。 目前，已指派給兩個群組，在**必要且可用**與**不適用**之間發生衝突的應用程式，會解析成**必要且可用**。 因為這項變更，發生此衝突的應用程式會解析成**不適用**。

當一個應用程式指派給多個具有不同應用程式用途的群組時，此變更會處理此混亂。

如果您希望在 11 月服務版本前向資訊工作者入口網站和公司入口網站提供您的應用程式，您有兩個選項：

1. 移除群組的**不適用**指派。
2. 建立不包含指派**必要且可用**用途之成員的新群組，並將該群組指派為**不適用**。

如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。

> [!Note]
> 在此版本後，您將無法再於 Intune 傳統主控台中檢視或修改行動裝置管理 (MDM) 應用程式指派。 不過，您可以使用 Azure 主控台或 Intune 圖形 API 指派應用程式。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731---"></a>從 Android 裝置獨立管理 Android for Work 裝置<!-- 1490731 -->
Intune 會支援從 Android 平台獨立管理 Android for Work 裝置的註冊。 這些設定在 [裝置註冊] > [註冊限制] > [裝置類型限制] 下管理。 (原位於 [裝置註冊] > [Android for Work 註冊] > [Android for Work 註冊設定] 下。)

根據預設，Android for Work 裝置設定會與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。
 
如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

使用新設定時，請考慮下列事項：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>之前是否從未啟動 Android for Work 註冊
在預設的裝置類型限制中封鎖新的 Android for Work 平台。 啟動功能後，您可以允許裝置註冊 Android for Work。 若要這樣做，請變更預設值，或建立新的裝置類型限制來取代預設的裝置類型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>是否曾啟動 Android for Work 註冊
如果曾經啟動過，您的情況會隨您選擇的設定而異：

| 設定 | 預設裝置類型限制中的 Android for Work 狀態 | 附註 |
| --- | --- | --- |
| **將所有裝置當成 Android 管理** | 封鎖 | 所有 Android 裝置都必須註冊，但不是 Android for Work。 |
| **將支援的裝置當成 Android for Work 管理** | 允許 | 所有支援 Android for Work 的裝置都必須註冊 Android for Work。 |
| **將這些群組中僅限使用者的受支援裝置當成 Android for Work 管理** | 封鎖 | 已建立不同的裝置類型限制原則，以覆寫預設值。 此原則會定義您先前選取的群組，以允許 Android for Work 註冊。 所選群組內的使用者仍可以繼續註冊他們的 Android for Work 裝置。 所有其他使用者則限制不能註冊 Android for Work。 |

無論什麼情況，都會保留您預期的法規。 您不需要執行任何動作，即能維持您環境中 Android for Work 的全域或各群組額度。

這些變更會在 11 月更新中推出，但可能要一段時間後才會在您的帳戶上執行。 當這些變更對您的帳戶生效時，您會在 Office 365 入口網站中收到確認通知。


### <a name="configure-an-ios-app-pin----1586774---"></a>設定 iOS 應用程式 PIN <!-- 1586774 -->
您很快就可以要求目標 iOS 應用程式的 PIN。 您可以透過 Azure 入口網站設定 PIN 需求及以天計的到期日期。 必要時，使用者必須設定並使用新的 PIN，才能存取 iOS 應用程式。 只有使用 Intune App SDK 啟用應用程式保護的 iOS 應用程式才支援這項功能。

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>新增個人裝置的「尋找我的 iPhone」<!--1427287-->
您可以檢視 iOS 裝置是否開啟 [啟用鎖定]。 這項功能以前位在 intune 傳統入口網站。

<!-- the following are present prior to 1711 -->

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->   
使用 Azure Active Directory (Azure AD) 時，您能夠限制行動裝置使用 Intune Managed Browser 應用程式存取網站。 在 Managed Browser 中，網站資料的安全受到保護，並會與使用者的個人資料區隔開來。 此外，針對受 Azure AD 保護的網站，Managed Browser 也支援單一登入功能。 當使用者登入 Managed Browser，或在裝置上搭配使用 Managed Browser 與受 Intune 管理的其他應用程式時，即可在不需輸入認證的情況下，讓 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及透過 Azure App Proxy 存取的內部網路資源等其他公司網站。


<!-- the following are present prior to 1710 -->



### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支援 Windows 10 版本升級原則 <!-- 903672(archived), 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級為 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資料，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。




<!-- the following are present prior to 1709 -->



### <a name="android-for-work-support-for-lookout----1087312---"></a>適用於 Lookout 的 Android for Work 支援 <!-- 1087312 -->   
具有 Lookout 的 Intune 連接器將在使用 Lookout for Work 應用程式時支援 Android for Work 裝置。 您能在容器內部或外部部署 Lookout 應用程式。

### <a name="intune-app-protection-and-citrix-mdx-development-tools----709185---"></a>Intune 應用程式防護和 Citrix MDX 開發工具 <!-- 709185 -->
您可以搭配使用 Citrix XenMobile MDX 和 Microsoft Intune 來管理裝置和應用程式。 如此一來，您就可以使用 Citrix 的 mVPN 技術，透過 Intune 應用程式防護原則來管理應用程式。

您可以尋找程式碼存放庫，其中包含適用於 iOS 和 Android 的 Intune App Wrapping Tool 和 Intune App SDK，並與 Citrix MDX mVPN 技術整合。


### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>內部部署 Exchange Connector 高可用性支援<!-- 676614 -->   
內部部署 Exchange Connector 可以有多個用戶端存取伺服器 (CAS) 角色。 例如，如果主要的 CAS 失敗，則 Exchange Connector 就會收到切換回其他 CAS 的查詢。 這項功能可確保服務不中斷。

### <a name="system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>適用於 Exchange connector 的 System Center Operations Manager 管理組件<!-- 885457 -->   
適用於 Exchange Connector 的 System Center Operations Manager 管理組件將可協助您剖析 Exchange Connector 記錄。 此管理組件可在您需要針對問題進行疑難排解時，為您提供不同方式來監視 Intune。





## <a name="intune-apps"></a>Intune 應用程式

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>協助您的使用者自助使用適用於 Android 的公司入口網站應用程式 <!---1573324, 1573150, 1558616, 1564878--->
Android 公司入口網站應用程式新增的使用者指示，能幫助他們了解，並盡可能自行解決新的使用狀況。 

- 顯示的新訊息說明已部署加密合規性原則，但根據 [Google 的建議指導方針](https://developer.android.com/reference/android/app/admin/DevicePolicyManager.html#setStorageEncryption(android.content.ComponentName, boolean)，[裝置製造商不加密裝置](/intune-user-help/your-device-appears-encrypted-but-cp-says-otherwise-android)。
- 如果使用者已經達到可新增裝置的上限，他們會被引導至 (Azure Active Directory 入口網站)[https://account.activedirectory.windowsazure.com/r/#/profile] 來移除裝置。 
- 使用者會得到遵循步驟，協助他們[修正 Samsung KNOX 裝置的啟動錯誤](https://go.microsoft.com/fwlink/?linkid=859718)或[關閉省電模式](/intune-user-help/power-saving-mode-android)。 如果這些解決方案都無法解決他們的問題，我們會提供如何[向 Microsoft 提交記錄](/intune-user-help/send-logs-to-microsoft-ios)的說明。 


### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android 裝置的新「解決」動作 <!---1583480--->
Android 公司入口網站應用程式在 [更新裝置設定] 頁面中推出「解決」動作。 選取此選項會直接將使用者引導至造成裝置不相容的設定。 Android 公司入口網站應用程式目前支援此動作處理[裝置密碼](/intune-user-help/set-your-pin-or-password-android)、[裝置加密](/intune-user-help/encrypt-your-device-android)、[USB 偵錯](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知來源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定。 




<!-- the following are present prior to 1711 -->


### <a name="redirecting-macos-users-to-our-new-company-portal-app---1380728--"></a>將 macOS 使用者重新導向至新的公司入口網站應用程式 <!--1380728-->   
當使用者登入公司入口網站，並註冊 macOS 裝置時，系統會指示他們下載 macOS 版的新公司入口網站應用程式以 完成程序。 使用 OS X El Capitan 10.11 或更新版本的 macOS 裝置會發生這種情況。 


<!-- the following are present prior to 1710 -->



### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>需要或無須註冊而提供的應用程式現在可以直接安裝，而不會提示註冊。 <!-- 1334712 -->
在 Android 公司入口網站應用程式中需要或無須註冊而提供的應用程式，現在可以安裝而不會提示註冊。


<!-- the following are present prior to 1709 -->

### <a name="intune-managed-browser-support-for-ios-and-android----1374196---"></a>iOS 和 Android 的 Intune Managed Browser 支援 <!-- 1374196 -->
自 2017 年 10 月起，Android 應用程式上的 Intune Managed Browser 應用程式只會支援執行 Android 4.4 和更新版本的裝置。 iOS 上的 Intune Managed Browser 應用程式只支援執行 iOS 9.0 及更新版本的裝置。 較舊版本的 Android 和 iOS 能夠繼續使用 Managed Browser，但是無法安裝新版的應用程式，而且可能無法存取所有的應用程式功能。 建議您將這些裝置更新為受支援的作業系統版本。


### <a name="improved-error-message-for-when-a-user-reaches-the-maximum-number-of-devices-allowed-to-enroll----1270370---"></a>改進使用者達到允許註冊的裝置數目上限時的錯誤訊息 <!-- 1270370 -->
終端使用者不會看到一般錯誤訊息，而是會看到實用且可採取動作的錯誤訊息：「您已註冊 IT 系統管理員所允許的裝置數目上限。請移除已註冊的裝置，或向您的 IT 系統管理員取得協助。」




## <a name="notices"></a>通知

目前沒有任何作用中的通知。




### <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。
