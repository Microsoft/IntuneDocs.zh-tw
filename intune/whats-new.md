---
title: "Microsoft Intune 的新功能"
titlesuffix: Azure portal
description: "了解 Intune Azure 入口網站中的新功能"
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/22/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: angrobe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 861d28b75d72a2784fc1c73a6f770d44cf1a21b3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune 的新功能

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

了解每週的 Microsoft Intune 新功能 您也可以了解[即將推出的變更](#whats-coming)、關於服務的[重要通知](#notices)，以及[過去版本](whats-new-archive.md)的相關資訊。

> [!Note]
> 如需混合式行動裝置管理 (MDM) 的新功能資訊，請參閱[混合式新功能頁面](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)。


<!-- Common categories:  
  ### Device enrollment
  ### Device management
  ### App management
  ### Device configuration
  ### Role-based access control
  ### Intune apps
  ### Monitor and troubleshoot

-->   

## <a name="week-of-january-22-2018"></a>2018 年 1 月 22 日當週

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10 的公司入口網站應用程式提供遠端鎖定 <!--676506-->
使用者現在可以從 Windows 10 的公司入口網站應用程式遠端鎖定其裝置。 這不會顯示在他們正使用的本機裝置上。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>針對 Windows 10 公司入口網站應用程式，可以更容易解決合規性問題 <!--676546-->
如果終端使用者是使用 Windows 裝置，便可以在公司入口網站應用程式中點選不符合規範的原因。 如此一來，系統會盡可能將使用者直接移至設定應用程式的正確位置，以修正問題。

## <a name="week-of-december-11-2017"></a>2017 年 12 月 11 日當週

### <a name="device-configuration"></a>裝置設定

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自動重新部署設定 <!-- 1469168 -->
**自動重新部署**設定允許具有系統管理權限的使用者，在裝置鎖定畫面上使用 **CTRL + Win + R** 來刪除所有使用者資料和設定。 裝置會自動重新設定並重新註冊以納入管理。 您可以在 [Windows 10] > [裝置限制] > [一般] > [自動重新部署] 下找到此設定。 如需詳細資料，請參閱 [Windows 10 的 Intune 裝置限制設定](device-restrictions-windows-10.md#general)。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>支援 Windows 10 版本升級原則中的其他來源版本  <!-- 903672,  1119689 -->
您現在可以使用 Windows 10 版本升級原則，從其他 Windows 10 版本 (Windows 10 專業版、Windows 10 專業教育版、Windows 10 Cloud 等) 進行升級。 在此版本之前，支援的版本升級路徑十分有限。 如需詳細資訊，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 資訊安全中心 (WDSC) 裝置組態設定檔設定 <!-- 1335507 -->

Intune 在 [端點保護] 下新增了新的裝置組態設定檔設定區段，名為 [Windows Defender 資訊安全中心]。 IT 系統管理員可以設定使用者可存取的 Windows Defender 資訊安全中心應用程式方針。 如果 IT 系統管理員在 Windows Defender 資訊安全中心應用程式中隱藏某個方針，則與該隱藏方針相關聯的所有通知都不會顯示在使用者的裝置上。

以下是系統管理員可從 Windows Defender 資訊安全中心裝置組態設定檔設定中隱藏的方針：
- 病毒與威脅防護
- 裝置效能與健康情況
- 防火牆與網路保護
- 應用程式與瀏覽器控制
- 家長監護選項

IT 系統管理員也可以自訂使用者可接收的通知。 例如，您可以設定是否讓使用者接收由 WDSC 中可見方針所產生的所有通知，或僅接收重要通知。 非重大通知包括 Windows Defender 防毒軟體活動的定期摘要，以及掃描完成時的通知。 所有其他通知都被視為重大通知。 此外，您也可以自訂通知內容本身，例如，您可以在顯示於使用者裝置上的通知中內嵌 IT 連絡資訊。

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>針對 SCEP 和 PFX 憑證處理的多連接器支援 <!-- 1361755 -->

使用內部部署 NDES 連接器將憑證傳遞至裝置的客戶，現在可在單一租用戶上設定多個連接器。

此新功能支援下列案例：

- **高可用性**

每個 NDES 連接器都會從 Intune 提取憑證要求。  如果有某個 NDES 連接器離線，其他連接器將可以繼續處理要求。

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>客戶主體名稱可以使用 AAD_DEVICE_ID 變數  <!-- 1468599 -->

當您在 Intune 中建立 SCEP 憑證設定檔時，現在可在建置自訂的主體名稱時使用 AAD_DEVICE_ID 變數。   當使用此 SCEP 設定檔要求憑證時，該變數會以要求憑證之裝置的 AAD 裝置識別碼來取代。


### <a name="device-management"></a>裝置管理

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>使用 Intune 的裝置合規性引擎管理 Jamf 註冊的 macOS 裝置 <!-- 1592747 -->
您現在可以使用 Jamf 將 macOS 裝置狀態資訊傳送到 Intune，然後 Intune 會評估裝置是否符合 Intune 主控台中定義的合規性原則。 根據裝置合規性狀態以及其他條件 (例如位置、使用者風險等)，條件式存取將會針對存取雲端的 macOS 裝置和與 Azure AD 連線之內部部署應用程式 (包括 Office 365) 強制執行合規性檢查。 深入了解[設定 Jamf 整合](conditional-access-integrate-jamf.md)與[強制執行 Jamf 受控裝置的合規性](conditional-access-assign-jamf.md)。

#### <a name="new-ios-device-action------1424701---"></a>新的 iOS 裝置動作 <!-- 1424701 -->

您現在可以關閉 iOS 10.3 受監督的裝置。 這個動作會立即關閉裝置，而不會警告使用者。 您可以在 [裝置] 工作負載中選取裝置時，於裝置屬性中找到 [關機 (僅限受監督)] 動作。

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>不允許 Samsung Knox 裝置的日期/時間變更 <!-- 1468103 -->

我們已加入新的功能，可讓您封鎖 Samsung Knox 裝置上的日期與時間變更。 您可以在 [裝置組態設定檔] > [裝置限制 (Android)] > [一般] 中找到此功能。

#### <a name="surface-hub-resource-account-supported----1566442----"></a>支援 Surface Hub 資源帳戶 <!-- 1566442  -->

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

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>在 macOS 裝置上安裝 Office 應用程式 <!-- 1494311 -->
您現在可在 macOS 裝置上安裝 Office 應用程式。 這個新的應用程式類型可讓您安裝 Word、Excel、PowerPoint、Outlook 及 OneNote。 這些應用程式也會隨附於 Microsoft AutoUpdate (MAU)，以協助保護您的應用程式並使它保持在最新狀態。

### <a name="app-management"></a>應用程式管理

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>刪除 iOS 大量採購方案權杖 <!-- 820879 -->
您可以使用主控台來刪除 iOS 大量採購方案 (VPP) 權杖。 當您擁有重複的 VPP 權杖執行個體時，這可能是必要的。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="end-user-messaging-for-accounts---1573558-for-1712--"></a>帳戶的終端使用者傳訊 <!--1573558 for 1712-->

「公司入口網站」網站的使用者將無法執行需要您租用戶寫入存取權的動作。 這些使用者將會看到適當的錯誤訊息，說明其帳戶正在維護中。 相同的變更也即將在 Android、iOS、macOS 與 Windows 版「公司入口網站」應用程式上套用。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)中看到此錯誤。



### <a name="role-based-access-control"></a>以角色為基礎的存取控制

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>名為 Current User 的新實體集合限於目前作用中的使用者資料 <!-- 1667026 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](reports-ref-current-user.md)。


### <a name="updated-graph-apis----1736360---"></a>更新的 Graph API <!-- 1736360 -->

在此版本中，我們已更新一些 Intune 的搶鮮版 (Beta) Graph API。 如需詳細資訊，請查看每月 [Graph API 變更記錄](https://developer.microsoft.com/graph/docs/concepts/changelog) \(英文\)。


## <a name="week-of-december-4-2017"></a>2017 年 12 月 4 日當週

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune 支援 Windows 資訊保護 (WIP) 拒絕應用程式 <!-- 1479103 -->
您可以在 Intune 中指定拒絕的應用程式。 如果應用程式遭到拒絕，它會被封鎖而無法存取公司資訊，效果與允許的應用程式清單相反。 如需詳細資訊，請參閱 [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Windows 資訊保護的建議拒絕清單)。


## <a name="week-of-november-27-2017"></a>2017 年 11 月 27 日當週

### <a name="device-enrollment"></a>裝置註冊

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>對註冊問題進行疑難排解  <!-- 746324 -->

[疑難排解] 工作區現在會顯示使用者註冊問題。 其中包含問題的詳細資料與建議的補救步驟，可協助系統管理員和技術服務人員針對相關問題進行疑難排解。 未擷取特定註冊問題，某些錯誤可能也沒有補救建議。

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>群組指派註冊限制 <!-- 747598 -->

身為 Intune 系統管理員，您現在可以[為使用者群組建立自訂的裝置類型和裝置限制註冊限制](enrollment-restrictions-set.md)。

Intune Azure 入口網站讓您每種限制類型最多可建立 25 個執行個體，指派給使用者群組。 群組指派的限制會覆寫預設的限制。

限制類型的所有執行個體都使用嚴格排序的清單維護。 此順序會定義衝突解決方法的優先順序值。 受到多個限制執行個體影響的使用者，只受擁有最高優先順序值的執行個體限制。 您可以變更指定的執行個體優先順序，只要將它拖曳到清單中的不同位置即可。

當 Android for Work 設定從 [Android For Work 註冊] 功能表移轉到 [註冊限制] 功能表時，即發佈這項功能。 因為這項移轉可能需要花費數天，而您的帳戶可能要升級 11 月版本的其他組件後，您才會看到 [註冊限制] 的群組指派成為啟用狀態。

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>支援多個網路裝置註冊服務 (NDES) 連接器<!-- 1528104 -->

NDES 可讓行動裝置依據簡單憑證註冊通訊協定 (SCEP) 在沒有網域認證的情況下取得憑證。
使用這項更新，可支援多個 NDES 連接器。

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>從 Android 裝置獨立管理 Android for Work 裝置<!-- 1490731 EEready-->

**注意**：這些變更會在 11 月更新中推出，但可能要一段時間後才會在您的帳戶上執行。 當這些變更對您的帳戶生效時，您會在 Office 365 入口網站中收到確認通知。 推出後，會有額外的管理性選項。 推出期間不會變更任何使用者體驗。

Intune 支援從 Android 平台獨立管理 Android for Work 裝置的註冊。 這些設定在 [裝置註冊] > [註冊限制] > [裝置類型限制] 下管理。 (原位於 [裝置註冊] > [Android for Work 註冊] > [Android for Work 註冊設定] 下。)

根據預設，Android for Work 裝置設定與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。

如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

使用新設定時，請考慮下列事項：

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>之前是否從未啟動 Android for Work 註冊

在預設的裝置類型限制中封鎖新的 Android for Work 平台。 啟動功能後，您可以允許裝置註冊 Android for Work。 若要這樣做，請變更預設值，或建立新的裝置類型限制來取代預設的裝置類型限制。

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>是否曾啟動 Android for Work 註冊

如果曾經啟動過，您的情況會隨您選擇的設定而異：

| Setting | 預設裝置類型限制中的 Android for Work 狀態 | 附註 |
| --- | --- | --- |
| **將所有裝置當成 Android 管理** | 封鎖 | 所有 Android 裝置都必須註冊，但不是 Android for Work。 |
| **將支援的裝置當成 Android for Work 管理** | 允許 | 所有支援 Android for Work 的裝置都必須註冊 Android for Work。 |
| **將這些群組中僅限使用者的受支援裝置當成 Android for Work 管理** | 封鎖 | 已建立不同的裝置類型限制原則，以覆寫預設值。 此原則會定義您先前選取的群組，以允許 Android for Work 註冊。 所選群組內的使用者仍可以繼續註冊他們的 Android for Work 裝置。 所有其他使用者則限制不能註冊 Android for Work。 |

無論什麼情況，都會保留您預期的法規。 您不需要執行任何動作，即能維持您環境中 Android for Work 的全域或各群組額度。

### <a name="app-management"></a>應用程式管理

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>已更新應用程式安裝報表，以包含安裝擱置中狀態 <!-- 1249446 -->  

透過 [行動裝置應用程式] 工作負載中的 [應用程式] 清單，每個應用程式可存取的**應用程式安裝狀態**報告，現在包含使用者及裝置的**安裝擱置中**計數。

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>適用於行動裝置威脅偵測的 iOS 11 應用程式清查 API <!-- 1391759 -->

Intune 會從個人和公司擁有的裝置收集應用程式清查資訊，供行動裝置威脅偵測 (MTD) 提供者擷取，例如 Lookout for Work。 您可以收集 iOS 11+ 裝置使用者的應用程式清查。

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


### <a name="device-management"></a>裝置管理

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>將混合式 MDM 使用者和裝置移轉至 Intune 獨立版 <!-- 1463747 wnready -->
我們在 Azure 入口網站中有新的處理程序和工具，將使用者及其裝置從混合式 MDM 移至 intune，這可讓您執行下列作業：
- 將原則與設定檔從 Configuration Manager 主控台複製到 Azure 入口網站的 Intune
- 將使用者子集移至 Azure 入口網站的 Intune，同時將其餘部分保留在混合式 MDM 中
- 將裝置移轉至 Azure 入口網站的 Intune 但不需要重新註冊

如需詳細資料，請參閱[將混合式 MDM 使用者和裝置移轉至 Intune 獨立版](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)。

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>內部部署 Exchange Connector 高可用性支援<!-- 676614 -->
在 Exchange Connector 使用指定的 CAS 建立與 Exchange 的連線之後，連接器現在便能夠探索其他 CAS。 如果無法使用主要的 CAS，連接器將容錯移轉至另一個 CAS (如果有的話)，直到有可用的主要 CAS 為止。 如需詳細資訊，請參閱[內部部署 Exchange Connector 高可用性支援](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)。

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>從遠端重新啟動 iOS 裝置 (僅受監督) <!-- 1424595 -->

您現在可以使用裝置動作觸發受監督的 iOS 10.3+ 裝置，令它重新啟動。 如需使用裝置重新啟動動作的詳細資訊，請參閱[使用 Intune 從遠端重新啟動裝置](device-restart.md)。

> [!Note]
> 此命令需要受監督的裝置和**裝置鎖定**存取權限。 裝置隨即重新啟動。 密碼鎖定的 iOS 裝置重新啟動後，不會重新加入 Wi-Fi 網路；重新啟動後，它們可能無法與伺服器通訊。

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS 的單一登入支援 <!-- 1333645 -->  

您可以讓 iOS 使用者使用單一登入。 編碼成在單一登入裝載中尋找使用者認證的 iOS 應用程式，因為有此裝載設定更新，所以很實用。 您也可以使用 UPN 和 Intune 裝置識別碼來設定主體名稱和領域。 如需詳細資料，請參閱[設定 Intune 以進行 iOS 裝置單一登入](sso-ios.md)。

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>新增個人裝置的「尋找我的 iPhone」<!--1427287-->
您現在可以檢視 iOS 裝置是否開啟 [啟用鎖定]。 這項功能以前位在 intune 傳統入口網站。


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>使用 Intune 從遠端鎖定受管理的 macOS 裝置 <!-- 1437691 -->

您可以鎖定遺失的 macOS 裝置，並設定 6 位數的復原 PIN。 鎖定時，[裝置概觀] 刀鋒視窗會顯示 PIN，直到傳送另一個裝置動作為止。

如需詳細資訊，請參閱[使用 Intune 從遠端鎖定受管理的裝置](device-remote-lock.md)。

#### <a name="new-scep-profile-details-supported----1559808---"></a>支援新的 SCEP 設定檔詳細資料 <!-- 1559808 -->

現在於 Windows、iOS、macOS 和 Android 平台上建立 SCEP 設定檔時，系統管理員可以設定其他設定。  系統管理員可以設定 IMEI、序號或一般名稱，包括使用主體名稱格式的電子郵件。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>重設為原廠設定時保留資料 <!--1588489 -->
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

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>顯示 Windows 10 更新通道指派 <!-- 1621837 -->
當要針對您正在檢視的使用者進行**疑難排解**時，您會看到所有 Windows 10 更新通道指派。  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender 進階威脅防護回報頻率設定 <!-- 1455974  -->
Windows Defender 進階威脅防護 (WDATP) 服務允許管理員管理受管理裝置的回報頻率。 使用新的 [加速遙測回報頻率] 選項，WDATP 可以更頻繁地收集資料及評估風險。 回報預設值最佳化速度及效能。 增加回報頻率對高風險裝置很重要。 此設定位在**裝置設定**的 **Windows Defender ATP** 設定檔中。

#### <a name="audit-updates----1412961---"></a>稽核更新 <!-- 1412961 -->  
Intune 稽核會提供與 Intune 相關的變更作業記錄。  擷取所有建立、更新、刪除和遠端工作作業，並保留一年。  Azure 入口網站提供每個工作負載過去 30 天的稽核資料檢視，且可篩選。  對應的圖形 API 可讓您擷取去年儲存的稽核資料。

[稽核] 位在**監視器**群組下。 每個工作負載都有 [稽核記錄檔] 功能表項目。




## <a name="week-of-november-20-2017"></a>2017 年 11 月 20 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="google-play-protect-support-on-android----908720---"></a>Android 中的 Google Play Protect 支援 <!-- 908720 -->

在 Android Oreo 版本中，Google 引進名為 Google Play Protect 的安全性功能套件，可讓使用者和組織執行安全的應用程式和保護 Android 映像。 Intune 將支援 Google Play Protect 功能，包括 SafetyNet 遠端證明。 系統管理員可設定合規性原則需求，藉此要求設定 Google Play Protect 且其狀況良好。
[SafetyNet 裝置證明] 設定可要求裝置連線至 Google 服務，以驗證裝置狀況良好且未遭入侵。 系統管理員也可以設定 Android for Work 的組態設定檔設定，以要求已安裝的應用程式必須經過 Google Play 服務驗證。 如果裝置不符合 Google Play Protect 的需求規範，條件式存取可能會禁止使用者存取公司資源。

- 了解[如何建立可啟用「Google Play 安全防護」的裝置合規性原則](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)。

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>允許來自受管理應用程式的文字通訊協定 <!-- 1414050  -->

受 Intune App SDK 管理的應用程式可以傳送簡訊。

## <a name="week-of-november-13-2017"></a>2017 年 11 月 13 日當週

### <a name="intune-apps"></a>Intune 應用程式
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS 版公司入口網站應用程式已推出 <!--1541700-->
macOS 版 Intune 公司入口網站有已經最佳化的更新體驗，可完全顯示使用者註冊之所有裝置所需的所有資訊與合規性通知。 此外，「Intune 公司入口網站」部署至裝置之後，適用於 macOS 的 Microsoft AutoUpdate 會提供其更新。 您可以透過從 macOS 裝置登入「Intune 公司入口網站」來下載新的 macOS 版「Intune 公司入口網站」。

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner 現在是已核准應用程式的行動裝置應用程式管理 (MAM) 清單的一部分  <!-- 1248473 -->
iOS 版和 Android 版的 Microsoft Planner 應用程式現在是行動裝置應用程式管理 (MAM) 已核准的應用程式的一部分。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，將應用程式設定至所有租用戶。
- 深入了解[已核准應用程式的 MAM 清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS 裝置上的個別 App VPN 的需求更新頻率   <!-- 1547061 -->  
系統管理員現在可能會移除 iOS 裝置上應用程式的個別 App VPN 需求；受影響的裝置將在它們下一次 Intune 簽入後 (通常在 15 分鐘內發生)。  

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>適用於 Exchange 連接器的 System Center Operations Manager 管理組件支援 <!-- 885457 -->
適用於 Exchange 連接器的 System Center Operations Manager (SCOM) 管理組件現在可協助您剖析 Exchange 連接器記錄。 這可在您需要針對問題進行疑難排解時，為您提供不同方式來監視服務。

## <a name="week-of-november-6-2017"></a>2017 年 11 月 6 日當週

### <a name="device-enrollment"></a>裝置註冊
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 裝置的共同管理  <!-- 1243445 -->
共同管理是一種可讓您從傳統管理過渡到現代化管理的解決方案，並提供您使用分段式方法的轉換過程。 本質上來說，共同管理解決方案可讓 Windows 10 裝置同時受 Configuration Manager 和 Microsoft Intune 管理，並聯結到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  如果您無法一次到位，此設定提供隨時間逐步實行現代化的轉換過程，讓您依據組織進展的步調來進行。  

#### <a name="new-enrollment-status-page-for-windows-10-enrollments---1063201--"></a>Windows 10 註冊的全新註冊狀態頁面 <!--1063201-->    
現在，您可以設定要在使用者註冊 Windows 10 裝置時顯示的問候語。 請使用**註冊狀態畫面**，設定要在使用者註冊 Windows 10 裝置時顯示的自訂訊息和超連結。  **註冊狀態畫面**亦可讓使用者檢視要套用到其裝置的原則設定進度。  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>依 OS 版本限制 Windows 註冊 <!-- 245498 -->
您現在能夠以 Intune 系統管理員的身分指定裝置註冊的 Windows 10 最低與最高版本。 您現可在 [平台設定] 刀鋒視窗設定這些限制。

Intune 會繼續支援註冊 Windows 8.1 電腦與手機。 不過，只有 Windows 10 版本能夠設定最低與最高限制。 若要允許 8.1 裝置的註冊，請在最低限制留空。

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 未指派裝置的警示  <!-- 1631236 -->
在 [Microsoft Intune] > [裝置註冊] > [概觀] 頁面上，有新的警示可供 Windows AutoPilot 未指派的裝置使用。 此警示能夠顯示有多少 AutoPilot 方案的裝置未指派 AutoPilot 部署設定檔。 您可以使用警示中的資訊來建立設定檔，並加以指派至未指派的裝置。 當您按一下警示時，會看到 Windows AutoPilot 裝置的完整清單，以及這些裝置的詳細資訊。 如需詳細資訊，請參閱[使用 Windows AutoPilot 部署方案註冊 Windows 裝置](https://docs.microsoft.com/intune/enrollment-autopilot)。

### <a name="device-management"></a>裝置管理

#### <a name="refresh-button-for-devices-list-------1333581---"></a>裝置清單的 [重新整理] 按鈕    <!-- 1333581 -->
因為裝置清單並不會自動重新整理，所以您可以使用新的 [重新整理] 按鈕來更新清單中顯示的裝置。

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>支援 Symantec 雲端憑證授權單位 (CA)  <!-- 1333638 -->    
Intune 現在支援 Symantec 雲端 CA，因此 Intune 憑證連接器可將來自 Symantec 雲端 CA 的 PKCS 憑證簽發給受 Intune 管理的裝置。 如果您已經使用 Intune 憑證連接器與 Microsoft 憑證授權單位 (CA)，可利用現有的 Intune 憑證連接器安裝程式來新增 Symantec CA 支援。

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>新增至裝置清查的項目   <!--1404455 -->
在本版本中，我們新增了下列項目到[已註冊裝置執行的清查](device-inventory.md)：

- Wi-Fi Mac 位址
- 儲存空間總計
- 可用空間總計
- MEID
- 用戶載波


### <a name="app-management"></a>應用程式管理
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>依據裝置的 Android 安全性修補程式下限，來設定應用程式的存取權<!-- 1278463 -->   
系統管理員可以定義裝置必須安裝的 Android 安全性修補程式下限，才能以受管理帳戶來存取受管理的應用程式。

> [!Note]  
> 這項功能只能限制 Android 6.0+ 裝置上由 Google 發行的安全性修補程式。

#### <a name="app-conditional-launch-support----1193313---"></a>支援條件式啟動應用程式 <!-- 1193313 -->
現在，IT 系統管理員可以透過 Azure 管理入口網站，設定在應用程式啟動時強制執行密碼，而不是透過行動裝置應用程式管理 (MAM) 的數字 PIN。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 此版 Intune 將**僅在 iOS 上**啟用這項功能。 Intune 支援密碼的方式與數字 PIN 類似，它會設定長度下限，並允許重複的字元和順序。 此功能需要應用程式 (亦即，WXP、Outlook、Managed Browser、Yammer) 的參與來就地整合 Intune App SDK 與此功能的程式碼，以在目標應用程式中強制執行密碼設定。

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>裝置安裝狀態報告中的企業營運應用程式版本號碼 <!-- 1233999 -->
在此版本中，裝置安裝狀態報告會顯示適用於 iOS 和 Android 的企業營運應用程式版本號碼。 您可以使用這些資訊來針對應用程式進行疑難排解，或找出執行過時應用程式版本的裝置。


### <a name="device-configuration"></a>裝置設定
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>系統管理員現在可以使用裝置組態設定檔來設定裝置的防火牆設定 <!-- 951708 -->   
系統管理員可以開啟裝置的防火牆，並針對網域、私用網路和公用網路設定各種通訊協定。  您可以在 "Endpoint Protection" 設定檔中找到這些防火牆設定。

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender 應用程式防護可依據組織的定義，協助保護裝置避免不受信任網站的威脅 <!-- 958257 -->   
系統管理員可以使用 Windows 資訊保護工作流程，或裝置設定下方的全新「網路界限」設定檔，將網站定義為「受信任」網站或「公司」網站。 如果網站未列在 64 位元 Windows 10 裝置受信任的網路界限中，而您使用 Microsoft Edge 來檢視，則系統會改為在 Hyper-V 虛擬電腦的瀏覽器中開啟。

您可以在 "Endpoint Protection" 設定檔的裝置組態設定檔中，找到應用程式防護。 系統管理員可以從該處設定虛擬瀏覽器和主機電腦之間的互動、不受信任的網站和信任網站之間的互動，並儲存虛擬瀏覽器中產生的資料。 若要在裝置上使用應用程式防護，您必須先設定網路界限。 每部裝置都只能定義一個網路界限。  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise 的 Windows Defender 應用程式控制具有僅信任已獲授權應用程式的模式 <!-- 1031096 -->    
每天有高達數千種的惡意檔案流竄出來，單純使用防毒特徵偵測來對抗惡意程式碼時，可能再也無法有效抵禦新的攻擊。 使用 Windows 10 Enterprise 的 Windows Defender 應用程式控制時，您可以將裝置設定的模式，從信任防毒軟體或其他安全性解決方案未封鎖的應用程式，變更為讓作業系統僅信任獲得企業授權的應用程式。 您可以將 Windows Defender 應用程式控制中的應用程式指派為信任。

使用 Intune 時，您可以在「僅限稽核」模式或「強制執行」模式中設定應用程式控制原則。 在「僅限稽核」模式中執行時，不會封鎖應用程式。 「僅限稽核」模式會在本機用戶端記錄檔中記錄所有事件。 您也可以設定是否只允許執行 Windows 元件和 Microsoft Store 應用程式，或允許依據智慧型安全性圖表的定義，執行評價良好的其他應用程式。

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender 惡意探索防護是 Windows 10 的全新入侵偵測功能 <!-- 1063615 -->   
Window Defender 惡意探索防護包含自訂規則，可降低擅用應用程式的可能性、避免巨集和指令碼的威脅、自動封鎖評價不良的 IP 位址網路連線，並協助資料抵禦勒索軟體和未知的威脅。 Window Defender 惡意探索防護是由下列元件所組成：

- **降低攻擊介面 (ASR)** 提供的規則可讓您避免巨集、指令碼和電子郵件的威脅。
- **控制存取資料夾**會自動封鎖對受保護資料夾內容的存取。
- **網路篩選**會封鎖任何應用程式與評價不良 IP/網域的輸出連線。
- **惡意探索保護**可提供記憶體限制、控制流程限制和原則限制，以用來保護應用程式不受惡意探索的威脅。


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼<!-- 790537 -->

Intune 管理延伸模組可讓您在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 延伸模組可補充 Windows 10 的行動裝置管理 (MDM) 功能，讓您更輕鬆地轉移至新式管理。 如需詳細資料，請參閱[在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼](intune-management-extension.md)。

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 的新裝置限制設定      <!-- 1308850 -->
-    傳訊 (僅限行動裝置) - 停用測試或 MMS 訊息
-    密碼 - 可啟用 FIPS 和使用 Windows Hello 次要裝置以進行驗證的設定 
-    顯示 - 可開啟或關閉舊版應用程式 GDI 縮放比例的設定

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 Kiosk 模式的裝置限制 <!-- 1308872 -->   
您可以將 Windows 10 裝置使用者限制在 kiosk 模式中，使其僅可使用一組預先定義的應用程式。  若要這樣做，請建立 Windows 10 裝置限制設定檔，然後進行 Kiosk 設定。

Kiosk 模式支援兩種模式：**單一應用程式** (只允許使用者執行一個應用程式) 或**多重應用程式** (允許存取一組應用程式)。  您可定義使用者帳戶和裝置名稱，以決定支援的應用程式。  當使用者登入時，就只能使用定義的應用程式。  若要進一步了解，請參閱 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

Kiosk 模式具有下列要求：

- Intune 必須為 MDM 授權單位。
- 目標裝置上必須已安裝應用程式。
- 裝置必須[已正確佈建](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>可建立網路界限的新裝置組態設定檔 <!-- 1311967 -->   
我們已在其他裝置組態設定檔的相同位置，建立名為**網路界限**的裝置組態設定檔。 您可以使用這個設定檔，將線上資源定義為公司資源和受信任的資源。 您必須先定義裝置的網路界限之後，裝置才可以使用 Windows Defender 應用程式防護和 Windows 資訊保護等功能。 每部裝置都只能定義一個網路界限。

您可以定義要信任的企業雲端資源、IP 位址範圍和內部 Proxy 伺服器。 定義好之後，Windows Defender 應用程式防護和 Windows 資訊保護等其他功能才可以使用網路界限。

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender 防毒軟體的兩個其他設定 <!-- 1338409 -->  
**檔案封鎖層級**

| | |
|---|---|
| 尚未設定 | [尚未設定] 會使用預設的 Windows Defender 防毒軟體封鎖層級，並提供強式偵測，而不會增加偵測合法檔案的風險。 |
| 高 | [高] 適用於強力偵測層級。
| 高 +  | [高 +] 可提供 [高] 層級與額外的保護措施，但可能會影響用戶端效能。
| 零容錯  | [零容錯] 會封鎖所有未知的可執行檔。 |

雖然可能性很低，但設定為 [高] 有可能會導致部分合法檔案受到偵測。
建議您將檔案封鎖層級設為預設值 [尚未設定]。

**延長掃描檔案的逾時 (依雲端)**  

| | |
|--|--|
| 秒數 (0-50) | 指定 Windows Defender 防毒軟體在封鎖檔案前應等候雲端結果的時間上限。 預設時間量為 10 秒：此處所指定的任何額外時間 (最多 50 秒) 均會加上預設的 10 秒。 在大部分情況下，掃描需要的時間遠比最大值少很多。 延長的時間可讓雲端徹底調查可疑的檔案。 建議您啟用此設定，並至少多指定 20 秒。 |

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>為 Windows 10 裝置新增 Citrix VPN <!-- 1512457 -->  
您可為其所擁有的 Windows 10 裝置設定 Citrix VPN。 設定 Windows 10 和更新版本的 VPN 時，您可以在 [基本 VPN] 刀鋒視窗的 [選取連線類型] 清單中，選擇 Citrix VPN。

> [!Note]
> iOS 和 Android 中已有 Citrix 設定。

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>iOS 上的 Wi-Fi 連線支援預先共用金鑰<!-- 1550823 -->
客戶可在 iOS 裝置上設定 Wi-Fi 設定檔，以使用預先共用金鑰 (PSK) 進行 WPA/WPA2 個人連線。 當裝置註冊到 Intune 時，會將這些設定檔推送到使用者的裝置。

將設定檔推送到裝置後，下一個步驟則取決於設定檔設定。  若設定為自動連線，就會在下次需要網路時這麼做。  若設定為手動連線，使用者就必須手動啟用連線。  

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>存取 iOS 的受管理應用程式記錄檔<!-- 1469920 -->
安裝 Managed Browser 的使用者現在可以檢視所有 Microsoft 所發行應用程式的管理狀態，並傳送記錄檔來針對受管理的 iOS 應用程式進行疑難排解。

深入了解如何在 iOS 裝置上的 Managed Browser 啟用疑難排解模式，請參閱 [How to access to managed app logs using the Managed Browser on iOS](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios) (如何在 iOS 上使用 Managed Browser 存取受管理應用程式記錄檔)。

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 版公司入口網站 2.9.0 版中裝置設定工作流程的改善 <!-- 1417174 -->

我們已改善 iOS 版公司入口網站應用程式中的裝置設定工作流程。 語言對使用者來說更簡單明瞭，而且我們已盡量將可以合併的畫面合併。 我們也透過在整個設定文字中使用您的公司名稱，讓語言更特定於您的公司。 您可以在 [應用程式 UI 中的新增功能] [](whats-new-app-ui.md) 頁面中看到這個更新的工作流程。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>使用者實體包含資料倉儲資料模型中的最新使用者資料<!-- 1544273 -->
Intune 資料倉儲資料模型的第一個版本只包含最新的歷程 Intune 資料。 報表製作者無法擷取使用者的目前狀態。 在這項更新中，**使用者實體**會填入最新的使用者資料。


## <a name="week-of-october-30-2017"></a>2017 年 10 月 30 日當週

### <a name="app-management"></a>應用程式管理

#### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>顯示 iOS 和 Android 的企業營運應用程式版本號碼<!-- 1380712 -->

Intune 的應用程式現在會顯示 iOS 和 Android 的企業營運應用程式版本號碼。 此號碼會顯示在 Azure 入口網站的應用程式清單及 [應用程式概觀] 刀鋒視窗中。 使用者可以在公司入口網站應用程式及入口網站中看到應用程式號碼。

__完整版本號碼__ 完整的版本號碼可識別特定的應用程式版本。 此號碼會顯示為_版本_(_組建_)。 例如，2.2(2.2.17560800)

完整的版本號碼有兩個部分：

 - **版本**  
   版本號碼是人類可讀的應用程式版本號碼。 可供使用者識別不同的應用程式版本。

 - **組建編號**  
    組建編號是內部編號，用於偵測應用程式與以程式設計方式管理應用程式。 組建編號是指參考程式碼變更的應用程式反覆項目。

深入了解版本號碼及開發企業營運應用程式，請參閱[開始使用 Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers)。

#### <a name="device-and-app-management-integration----677972---"></a>裝置與應用程式管理整合 <!-- 677972 -->   
Intune 早已開始整合應用程式和裝置管理的 IT 系統管理員體驗；現在，Intune 的行動裝置管理 (MDM) 與行動應用程式管理 (MAM) 都可從 Azure 入口網站存取。 這些變更都是為了簡化您的裝置和應用程式管理體驗。

如需深入了解已宣布的 MDM 和 MAM 變更，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)。

#### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple 裝置的新註冊警示 <!-- 1471790 -->
註冊的 [概觀] 頁面會顯示對 IT 管理員極有幫助，有關 Apple 裝置管理的警示。 在下列情況中 [概觀] 頁面會顯示警示：Apple MDM Push Certificate 即將到期或已過期時、裝置註冊計劃權杖即將到期或已過期時、裝置註冊計劃中有未指派的裝置時。

#### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>支援在不註冊裝置的情況下替換應用程式設定 <!-- 1080364 -->

您可以在未註冊裝置的應用程式中，使用應用程式設定的動態值權杖。 如需詳細資訊，請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 版公司入口網站應用程式的更新 <!--1299474-->
Windows 10 版「公司入口網站」應用程式中的 [設定] 頁面已更新，以使設定和預期的使用者動作在所有設定中更加一致。 它也已更新為符合其他 Windows 應用程式的配置。 您可以在 [應用程式 UI 中的新增功能](whats-new-app-ui.md) 頁面中找到之前/之後影像。

#### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>通知終端使用者可看到哪些 Windows 10 裝置資訊 <!--1337920-->
我們在 Windows 10 版公司入口網站應用程式的 [裝置詳細資料] 畫面新增了 [擁有權類型]。 如此一來，使用者就能夠直接從 Intune 終端使用者文件的此頁面，了解有關隱私權的更多資訊。他們也能夠在 [關於] 畫面上找到此資訊。

#### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Android 版公司入口網站應用程式的意見反應提示 <!--1165249-->
Android 版公司入口網站應用程式現在會要求使用者意見反應。 此意見反應將直接傳送給 Microsoft，並讓使用者有機會在公開的 Google Play 商店中檢閱應用程式。 意見反應並不是必要的，可以輕鬆地關閉，讓使用者可以繼續使用應用程式。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

#### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>協助您的使用者自助使用適用於 Android 的公司入口網站應用程式 <!-- 1573324, 1573150, 1558616, 1564878 -->

Android 版公司入口網站應用程式新增了終端使用者指示，能幫助他們了解，並盡可能自行解決新的使用案例。
- 如果終端使用者已經達到可新增裝置數目的上限，將會被引導至 [Azure Active Directory 入口網站](https://account.activedirectory.windowsazure.com/r/#/profile)以移除裝置。
- 終端使用者將會收到遵循的步驟，以協助[修正 Samsung Knox 裝置的啟動錯誤](https://go.microsoft.com/fwlink/?linkid=859718)或[關閉省電模式](/intune-user-help/power-saving-mode-android)。 如果這些解決方案都無法解決他們的問題，我們會提供如何[向 Microsoft 提交記錄](/intune-user-help/send-logs-to-microsoft-android)的說明。

#### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android 裝置的新「解決」動作 <!-- 1583480 -->

Android 公司入口網站應用程式在 [更新裝置設定] 頁面中推出「解決」動作。 選取此選項會直接將使用者引導至造成裝置不相容的設定。 Android 版公司入口網站應用程式目前在[裝置密碼](/intune-user-help/set-your-pin-or-password-android)、[USB 偵錯](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知來源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定支援此動作。

#### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Android 版公司入口網站中的裝置設定進度列指示器 <!-- 1565657 -->
Android 版公司入口網站應用程式會顯示使用者註冊其裝置時的裝置設定進度列指示器。 指示器會顯示新的狀態，從「正在設定您的裝置...」開始，然後依序是「正在註冊您的裝置...」、「正在完成註冊您的裝置...」、「正在完成設定您的裝置...」。

## <a name="week-of-october-23-2017"></a>2017 年 10 月 23 日當週

### <a name="intune-apps"></a>Intune 應用程式
#### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>支援 iOS 版公司入口網站的憑證式驗證 <!--1029830-->
我們已新增支援 iOS 版公司入口網站應用程式的憑證式驗證 (CBA)。 使用 CBA 的使用者可輸入其使用者名稱，然後點選 [Sign in with a certificate] (使用憑證登入) 連結。 Android 和 Windows 版公司入口網站應用程式已支援 CBA。 若要深入了解，請參閱[登入公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)頁面。

#### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>需要或無須註冊而提供的應用程式現在可以直接安裝，而不會提示註冊。 <!-- 1334712 -->

在 Android 公司入口網站應用程式上需要或無需註冊才可使用的公司應用程式，現在皆已可安裝而不會提示需要註冊。

## <a name="week-of-october-16-2017"></a>2017 年 10 月 16 日當週
### <a name="device-enrollment"></a>裝置註冊
#### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune-----747617----"></a>Microsoft Intune 中的 Windows AutoPilot Deployment 方案支援<!-- 747617  -->
您可以現在使用 Microsoft Intune Windows AutoPilot 部署計劃，讓您的使用者能夠佈建其公司裝置而不需要 IT 介入。 您可以自訂全新體驗 (OOBE)，並引導使用者將他們的裝置加入 Azure AD 且在 Intune 中註冊。 搭配使用時，Microsoft Intune 和 Windows AutoPilot 不須部署、維護及管理作業系統映像。 如需詳細資料，請參閱 [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot) (使用 Windows AutoPilot Deployment 方案註冊 Windows 裝置)。

#### <a name="quick-start-for-device-enrollment-----1425655---"></a>裝置註冊的快速入門  <!-- 1425655 --> 
快速入門現在提供於 [裝置註冊]，並提供管理平台和設定註冊程序的參考表格。 每個項目的簡短描述，以及文件連結和逐步指示，提供實用的文件來簡化開始使用。

#### <a name="device-categorization----1427491---"></a>裝置分類 <!-- 1427491 -->
[裝置] > [概觀] 刀鋒視窗的註冊裝置平台圖，會依平台組織裝置，包括 Android、iOS、macOS、Windows 和 Windows Mobile。  執行其他作業系統的裝置會分組為「其他」。  這包括由 Blackberry、NOKIA 和其他廠商製造的裝置。  

若要了解您租用戶中的哪些裝置受到影響，請選擇 [管理] > [所有裝置]，然後使用 [篩選] 限制 [OS] 欄位。

### <a name="device-management"></a>裝置管理
#### <a name="zimperium---new-mobile-threat-defense-partner------954681---"></a>Zimperium - 新的 Mobile Threat Defense 夥伴<!-- 954681 -->  
您可以根據由 Zimperium (與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

##### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作
風險評估的依據是收集自執行 Zimperium 裝置的遙測。 您可以根據透過 Intune 裝置合規性政策啟用的 Zimperium 風險評估，設定 EMS 條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不符合規範的裝置存取公司資源。

#### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978575, 1308849, -->  
我們將為 Windows Defender SmartScreen 類別中的 Windows 10 裝置限制設定檔新增設定。

如需 Windows 10 裝置限制設定檔的詳細資料，請參閱 [Windows 10 及更新版本的裝置限制設定]( device-restrictions-windows-10.md)。

#### <a name="remote-support-for-windows-and-windows-mobile-devices------1070473---"></a>適用於 Windows 和 Windows Mobile 裝置的遠端支援 <!-- 1070473 -->  
Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (需另行購買)，讓您為執行 Windows 和 Windows Mobile 裝置的使用者提供遠端協助。

#### <a name="scan-devices-with-windows-defender----1280988--1280990-----"></a>使用 Windows Defender 掃描裝置 <!-- 1280988  1280990   -->
您現在可以在受管理的 Windows 10 裝置上，使用 Windows Defender 防毒軟體來執行**快速掃描**、**完整掃描**，和**更新簽章**。 從裝置的概觀刀鋒視窗，選擇要在裝置上執行的動作。 系統會提示您確認動作，然後命令才會傳送到裝置。 

**快速掃描**：快速掃描會掃描惡意程式碼註冊要啟動的位置，例如登錄機碼和已知的 Windows 啟動資料夾。 快速掃描平均會花費五分鐘。 快速掃描與 [隨時開啟即時保護] 設定 (可在檔案開啟、關閉，以及使用者每次瀏覽資料夾時掃描檔案) 結合時，可提供保護以防禦潛藏於系統或核心的惡意程式碼。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**完整掃描**：完整掃描對於已遭遇惡意程式碼威脅的裝置非常實用，可找出是否有任何需要進一步完整清理的尚未作用元件，且適合執行隨選掃描。 完整掃描可能需要一個小時來進行。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**更新簽章**：更新簽章命令會更新 Windows Defender 防毒軟體的惡意程式碼定義和簽章。 這有助於確保 Windows Defender 防毒軟體能有效偵測惡意程式碼。 這項功能僅適用於 Windows 10 裝置，且需要裝置的網際網路連線。 

#### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>[啟用/停用] 按鈕從 Intune Azure 入口網站的 [Intune 憑證授權單位] 頁面移除  <!-- 1400455 -->
 我們正在消除設定 Intune 上憑證連接器的多餘步驟。 目前，您會下載憑證連接器，然後在 Intune 主控台中啟用它。 不過，如果您在 Intune 主控台中停用連接器，連接器會繼續發出憑證。

##### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
從 10 月開始，[啟用/停用] 按鈕不會再出現在 Azure 入口網站的 [憑證授權單位] 頁面上。 連接器功能將保持不變。 憑證仍會部署到在 Intune 中註冊的裝置。 您可以繼續下載並安裝憑證連接器。 若要停止發出憑證，您現在要解除安裝憑證連接器而非將它停用。

##### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
如果您目前已停用憑證連接器，您應該將它解除安裝。

### <a name="device-configuration"></a>裝置設定
#### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>適用於 Windows 10 團隊版裝置限制設定檔的新設定 <!--- 1308838 -->
在此版本中，我們新增了許多設定到 Windows 10 團隊版裝置限制設定檔，以協助您控制 Surface Hub 裝置。

如需此設定檔的詳細資訊，請參閱 [Windows 10 團隊版裝置限制設定](device-restrictions-windows-10-teams.md)。

#### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time-----1333292---"></a>防止 Android 裝置的使用者變更其裝置的日期和時間 <!-- 1333292 -->
您可以使用 [Android 自訂裝置原則](custom-settings-android.md)來防止 Android 裝置使用者變更裝置的日期和時間。

若要這樣做，請設定 Android 自訂原則，將 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 設定為 **TRUE**，然後指派給所需的群組。

#### <a name="bitlocker-device-configuration----1397398---"></a>BitLocker 裝置設定 <!-- 1397398 -->
[Windows 加密] > [基本設定] 包含新的 [其他磁碟加密的警告] 設定，讓您停用使用者裝置上可能正在使用的其他磁碟加密[警告提示](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)。  警告提示會要求使用者同意，然後才會在裝置上設定 BitLocker，在使用者確認之前則會封鎖 BitLocker 設定。  新的設定會停用使用者警告。


### <a name="app-management"></a>應用程式管理
#### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>企業大量採購方案應用程式現在將會同步到 Intune 租用戶 <!-- 800882 -->  
協力廠商開發人員可以私下將應用程式散發給 iTunes Connect 中所指定的授權企業大量採購方案 (VPP) 成員。 這些企業 VPP 成員可以登入大量採購方案 App Store，並購買其應用程式。

在此版本中，終端使用者所購買的企業 VPP 應用程式將開始與其 Intune 租用戶同步。

#### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>選取 Apple 國家/地區市集以同步處理 VPP 應用程式 <!-- 1332311 -->  
上傳您的大量採購方案 (VPP) 權杖時，可以設定 VPP 的國家/地區市集。 Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。

> [!NOTE]  
> 目前 Intune 只會從符合 Intune 地區設定 (建立 Intune 租用戶所在位置) 的 VPP 國家/地區市集同步處理 VPP 應用程式。


### <a name="intune-apps"></a>Intune 應用程式
#### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>封鎖 Android for Work 中工作和個人設定檔間的複製和貼上 <!-- 1098994 -->
在此版本中，您可以將 Android for Work 的工作設定檔設定為封鎖工作和個人應用程式間的複製和貼上。 您可以在 [工作設定檔設定] 中，於 [Android for Work] 平台的 [裝置限制] 設定檔內找到這項新設定。

#### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>建立僅限於特定地區 Apple App Store 的 iOS 應用程式 <!-- 1281692 -->
您可以在 Apple App Store 受管理的應用程式建立期間，指定國家/地區的地區設定。

> [!Note]  
> 目前，您僅能建立出現在美國市集的 Apple App Store 受管理應用程式。

####  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 使用者和裝置授權的應用程式 <!-- 1305564 -->  
您可以透過 Intune 服務，設定 iOS VPP 權杖以更新為該權杖所購買的全部應用程式。 Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。

如需設定 VPP 權杖並啟用自動更新的步驟，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式] (/intune/vpp-apps-ios)。


### <a name="monitor-and-troubleshoot"></a>監視及疑難排解
#### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->
您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。

#### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>檢閱 Windows 10 更新通道的原則合規性 <!-- 1067886 -->
您可以從 [軟體更新] > [依更新通道別部署狀態] 來檢閱 Windows 10 更新通道的原則報告。 原則報告包括已設定更新通道的部署狀態。 

#### <a name="new-report-that-lists-ios-devices-with-older-ios-versions------1352223---"></a>列出舊版 iOS 之 iOS 裝置的新報表   <!-- 1352223 -->
[軟體更新] 工作區提供 [過期的 iOS 裝置] 報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定並有可用更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 

#### <a name="view-app-protection-policy-assignments-for-troubleshooting-----1475003---"></a>檢視應用程式保護原則指派以進行疑難排解 <!--  1475003 -->
在此即將發行的版本中，將會新增 [應用程式保護原則] 選項到疑難排解刀鋒視窗中提供的 [指派] 下拉式清單。 您現在可以選取應用程式保護原則，以查看指派給所選取使用者的應用程式保護原則。



## <a name="week-of-october-2-2017"></a>2017 年 10 月 2 日當週
### <a name="intune-apps"></a>Intune 應用程式
#### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>對公司入口網站之裝置安裝工作流程的改善 <!--1490692-->
我們已改善 Android 版公司入口網站應用程式中的裝置安裝工作流程。 我們採用您公司專屬的語言、對使用者來說更簡單明瞭，並盡量將可以合併的畫面合併。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md#week-of-october-2-2017)頁面中，查看這些變更。

#### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>改善在 Android 裝置上要求存取連絡人的相關指引 <!--1484985-->

Android 版公司入口網站應用程式通常會要求使用者接受「連絡人」權限。 如果使用者拒絕此存取權，系統現會顯示應用程式內通知，提醒他們授與此權限以進行條件式存取。 

#### <a name="secure-startup-remediation-for-android---1490712--"></a>Android 的安全啟動修復 <!--1490712-->

如果使用者是使用 Android 裝置，可以點選公司入口網站應用程式中的不相容原因。 如此一來，系統會盡可能將使用者直接移至設定應用程式的正確位置，以修正問題。 

#### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>在 Android Oreo 的公司入口網站應用程式上新增終端使用者的推播通知 <!--1475932-->

終端使用者將會看到其他通知，這些通知會指出 Android Oreo 版公司入口網站應用程式正在執行背景工作，例如從 Intune 服務擷取原則。 這樣可讓終端使用者清楚了解公司入口網站在其裝置上執行的系統管理工作。 這是適用於 Android Oreo 版公司入口網站應用程式之整體[公司入口網站 UI 最佳化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)的一部分。 

在 Android Oreo 中啟用的新 UI 項目已進一步最佳化。  終端使用者會看到額外的通知，顯示出公司入口網站執行背景工作 (例如從 Intune 服務擷取原則) 的時間。  這可讓使用者清楚知道公司入口網站在裝置上執行管理工作的時間。

#### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司入口網站應用程式使用工作設定檔的新行為 <!-- 1485783 -->

當您使用工作設定檔註冊 Android for Work 裝置時，是由工作設定檔中的公司入口網站應用程式來執行裝置上的管理工作。 

除非您使用個人設定檔中啟用 MAM 的應用程式，否則 Android 公司入口網站應用程式不再有任何用途。 為了改善工作設定檔的體驗，Intune 會在成功註冊工作設定檔後，自動隱藏個人的公司入口網站應用程式。

您可以隨時啟用個人設定檔中的 Android 公司入口網站應用程式，方法是瀏覽 [Play Store 中的公司入口網站](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)，然後點選 [啟用]。

#### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 和 Windows Phone 8.1 版公司入口網站移至維持模式 <!--1428681-->

自 2017 年 10 月起，Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式將會移至維持模式。 這表示這些平台將會繼續支援應用程式和現有的案例 (例如註冊和合規性)。 這些應用程式仍可透過現有的發行通道 (例如 Microsoft 市集) 下載取得。 

一旦進入維持模式，這些應用程式僅會接收重大安全性更新。 但是，將不會針對這些應用程式發行額外的更新或功能。 如需新功能，建議您將裝置更新為 Windows 10 或 Windows 10 行動裝置版。 


### <a name="device-enrollment"></a>裝置註冊

#### <a name="block-unsupported-samsung-knox-device-enrollment-----1490695---"></a>封鎖不支援的 Samsung Knox 裝置註冊 <!-- 1490695 -->

公司入口網站應用程式只會嘗試註冊支援的 Samsung Knox 裝置。 為了避免 Knox 啟用錯誤而導致 MDM 註冊失敗，如果裝置出現在 [Samsung 發佈的裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中，則系統只會嘗試進行裝置註冊。 有些 Samsung 裝置型號可能支援 Knox，而有些不支援。 在您購買及部署之前，請先跟裝置轉銷商確認 KNOX 相容性。 您可以在 [Android 和 Samsung Knox Standard 原則設定](/intune/supported-devices-browsers.md#intune-supported-devices)中找到已驗證裝置的完整清單。

#### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>結束對 Android 4.3 和較舊版本的支援<!-- 1171126, 1326920 -->
受管理的應用程式和 Android 公司入口網站應用程式需要 Android 4.4 及更新版本才能存取公司資源。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您使用不含 MDM 的應用程式保護原則，應用程式就不會接收更新，其體驗品質會隨著時間而降低。

#### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>通知使用者可在已註冊裝置上看到哪些裝置資訊 <!--1165314-->
針對所有公司入口網站應用程式的 [裝置詳細資料] 畫面，我們會新增 [擁有權類型]。 如此一來，使用者就能夠直接從[公司可以看到哪些資訊？](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)一文中，了解隱私權的詳細資訊。 在不久的將來，這項功能就會跨所有公司入口網站應用程式推出。 iOS 的這項功能已於 [9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)推出。


## <a name="week-of-september-25-2017"></a>2017 年 9 月 25 日當週

### <a name="device-enrollment"></a>裝置註冊

#### <a name="intune-supports-ios-11---1428975--"></a>Intune 支援 iOS 11 <!--1428975-->
Intune 支援 iOS 11。 這項資訊之前已在 [Intune 支援部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)宣布過。

#### <a name="end-of-support-for-ios-80----1164477---"></a>結束對 iOS 8.0 的支援<!-- 1164477 -->
受管理的應用程式和 iOS 公司入口網站應用程式需要 iOS 9.0 及更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。 

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>重新整理動作已新增至 Windows 10 的公司入口網站應用程式 <!--1132468-->
Windows 10 公司入口網站應用程式可讓使用者提取以重新整理，或按桌上型電腦的 F5，重新整理應用程式中的資料。



## <a name="notices"></a>通知

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>規劃變更：立即在 Azure 上使用 Intune 進行 MDM 管理 <!-- 1227338 -->
一年多前，我們公佈了 [Azure 上的 Intune 公開預覽版 ](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)，六個月前追加了 Intune 的[新管理員體驗正式運作](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)。 自 2018 年 4 月 2 日起，使用 Intune 獨立版的客戶將無法繼續在傳統 Silverlight 主控台中使用行動裝置管理 (MDM)。 但您可以使用 [Azure 上的 Intune](https://aka.ms/Intune_on_Azure) 處理 MDM 需求。 如果仍在使用 MDM 的傳統主控台，請停止使用並熟悉 Azure 上的 Intune。 我們不希望這項變更影響任何使用者。 Silverlight 仍提供傳統的電腦管理。 您可以在[這裡](https://aka.ms/Intune_on_Azure_mdm)深入了解這項變更，以及它對您的影響。


### <a name="plan-for-change-easy-assist-end-of-life----1556480---"></a>規劃變更：Easy Assist 生命週期結束 <!-- 1556480 -->
Intune 會使用 Microsoft Easy Assist 進行電腦管理遠端協助。 您可能不知道 Microsoft Easy Assist 為 Office Live Meeting 的元件，而該服務已於 2017 年 12 月 31 日被取代。 因此，Intune 的 Easy Assist 供應項目生命週期也將於 2017 年 12 月 31 日結束。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>從 Android 裝置獨立管理 Android for Work 裝置<!-- 1490731 EEready-->    
**注意**：這些變更會在 11 月更新中推出，但可能要一段時間後才會在您的帳戶上執行。 當這些變更對您的帳戶生效時，您會在 Office 365 入口網站中收到確認通知。 推出後，會有額外的管理性選項。 推出期間不會變更任何使用者體驗。

Intune 支援從 Android 平台獨立管理 Android for Work 裝置的註冊。 這些設定在 [裝置註冊] > [註冊限制] > [裝置類型限制] 下管理。 (原位於 [裝置註冊] > [Android for Work 註冊] > [Android for Work 註冊設定] 下。)

根據預設，Android for Work 裝置設定會與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。

如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

使用新設定時，請考慮下列事項：

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>之前是否從未啟動 Android for Work 註冊

在預設的裝置類型限制中封鎖新的 Android for Work 平台。 啟動功能後，您可以允許裝置註冊 Android for Work。 若要這樣做，請變更預設值，或建立新的裝置類型限制來取代預設的裝置類型限制。

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>是否曾啟動 Android for Work 註冊

如果曾經啟動過，您的情況會隨您選擇的設定而異：

| Setting | 預設裝置類型限制中的 Android for Work 狀態 | 附註 |
| --- | --- | --- |
| **將所有裝置當成 Android 管理** | 封鎖 | 所有 Android 裝置都必須註冊，但不是 Android for Work。 |
| **將支援的裝置當成 Android for Work 管理** | 允許 | 所有支援 Android for Work 的裝置都必須註冊 Android for Work。 |
| **將這些群組中僅限使用者的受支援裝置當成 Android for Work 管理** | 封鎖 | 已建立不同的裝置類型限制原則，以覆寫預設值。 此原則會定義您先前選取的群組，以允許 Android for Work 註冊。 所選群組內的使用者仍可以繼續註冊他們的 Android for Work 裝置。 所有其他使用者則限制不能註冊 Android for Work。 |

無論什麼情況，都會保留您預期的法規。 您不需要執行任何動作，即能維持您環境中 Android for Work 的全域或各群組額度。

### <a name="deprecating-support-for-os-x-mavericks-1010-and-previous-versions-of-macos---1489263-plan-for-change-for-1802--"></a>即將取代 OS X Mavericks 10.10 與舊版 macOS 的支援<!--1489263, plan for change for 1802-->
我們宣布即將在 2018 年 2 月開始不再支援 OS X Yosemite 10.10 與舊版 macOS 的裝置註冊。 Intune 完全支援 OS X El Capitan 10.11 與更新版本。

### <a name="new-path-for-managed-devices-in-graph-api----1586728---"></a>Graph API 中受管理裝置的新路徑 <!-- 1586728 -->
我們針對 Graph API 搶鮮版 (Beta) 中用來存取受管理裝置的路徑進行了變更。 

| | |
|--|--|
| 目前的路徑 |  https://graph.microsoft.com/beta/managedDevices |
| 新的路徑 | https://graph.microsoft.com/beta/deviceManagement/managedDevices |

在 10 月期間，這兩個路徑都能運作。 但在 10 月的服務版本之後，就只能使用新的路徑。  如果您使用 Graph API 來存取受管理的裝置，請使用新路徑來更新並驗證您的指令碼和應用程式。 如需了解其他變更，請查看每月的 [Graph API 變更記錄](https://developer.microsoft.com/graph/docs/concepts/changelog)。


### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Intune 傳統入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取 Azure 入口網站，我們強烈建議您建立試用帳戶來測試新的體驗。

### <a name="administration-roles-being-replaced-in-azure-portal"></a>Azure 入口網站中將被取代的系統管理角色
在 Intune 傳統入口網站 (Silverlight) 中使用的現有行動應用程式管理 (MAM) 系統管理角色 (參與者、擁有者或唯讀) 在 Intune Azure 入口網站中會被取代為一組新的、完整的角色型系統管理控制 (RBAC)。 當您移轉至 Azure 入口網站之後，必須將系統管理員重新指派至這些新的系統管理角色。 如需 RBAC 和新角色的詳細資訊，請參閱 [Microsoft Intune 的角色型存取控制](/intune/role-based-access-control)。

## <a name="whats-coming"></a>未來動態

### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866--"></a>iOS 版公司入口網站應用程式的使用者體驗更新 <!--1412866-->

我們將發行 iOS 版公司入口網站應用程式的重大使用者體驗更新。 此項更新的重點是全面視覺效果的重新設計，包括提高使用性和存取範圍的現代化外觀及操作。 保留目前所有的 iOS 公司入口網站功能。

我們會透過 Apple TestFlight 計劃，提供更新公司入口網站應用程式的發行前版本讓您使用，並歡迎您提供意見反應。 請在 https://aka.ms/intune_ios_cp_testflight 註冊存取 TestFlight。

### <a name="conditional-access-policies-for-intune-will-only-be-available-from-the-azure-portal-----1737088---"></a>Intune 的條件式存取原則只在 Azure 入口網站提供 <!-- 1737088 -->
我們正在簡化您設定與管理條件式存取的方法。 目前，您可以在 [Intune 應用程式防護] (MAM) 刀鋒視窗中，透過 [Windows Azure 入口網站](https://manage.windowsazure.com)的傳統 Azure AD 體驗管理條件式存取。 自 1 月開始，您只能夠從 [Azure Active Directory] > [條件式存取]，在 [Azure 入口網站](https://portal.azure.com)設定與管理原則。 為了方便起見，您也可以在 [Intune] > [條件式存取]，從 Azure 入口網站的 Intune 存取此刀鋒視窗。

### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine---1592747--"></a>使用 Intune 的裝置合規性引擎管理 Jamf 註冊的 macOS 裝置 <!--1592747-->
從 2018 年初開始，Jamf 會將 macOS 裝置狀態資訊傳送到 Intune，然後 Intune 會評估它是否符合 Intune 主控台中定義的合規性原則。 根據裝置合規性狀態以及其他條件 (例如位置、使用者風險等)，條件式存取將會針對存取雲端的 macOS 裝置和與 Azure AD 連線之內部部署應用程式 (包括 Office 365) 強制執行合規性檢查。

### <a name="changes-in-support-for-the-intune-ios-company-portal-app-----1164474----"></a>Intune iOS 公司入口網站應用程式的支援變更 <!-- 1164474  -->
iOS 的 Microsoft Intune 公司入口網站應用程式很快將會有更新，屆時將只支援執行 iOS 9.0 或更新版本的裝置。 支援 iOS 8 的公司入口網站版本仍然可以使用非常短的一段時間。 不過，請注意，如果您也使用啟用 MAM 的 iOS 應用程式，我們支援 iOS 9.0 及更新版本，因此您會想要確保您的終端使用者更新到最新的作業系統。 

#### <a name="how-does-this-affect-me"></a>此變更對我造成什麼影響？
我們讓您事先知道這項資訊，雖然我們沒有特定的日期，您仍有時間進行規劃。 請確認您的使用者更新為 iOS 9+，且當公司入口網站應用程式發行時，要求您的終端使用者更新其公司入口網站應用程式。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
鼓勵您的使用者更新到 iOS 9.0 或更新版本，以便完全利用 Intune 的新功能。  鼓勵使用者安裝新版的公司入口網站，並利用它將提供的新功能。

在 Azure 入口網站中移至 Intune，檢視 [裝置] > [所有裝置]，並依 iOS 版本篩選，以查看作業系統早於 iOS 9 的任何目前裝置。


### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple 要求必須更新 Application Transport Security <!--748318-->
Apple 宣布將會強制執行 Application Transport Security (ATS) 的特定需求。 ATS 可用來對透過 HTTPS 進行的所有應用程式通訊，強制執行更嚴格的安全性。 此變更會影響使用 iOS 公司入口網站應用程式的 Intune 客戶。

我們已透過 Apple TestFlight 方案，提供符合新 ATS 需求的 iOS 版公司入口網站應用程式。 如果您想試用該版本以便測試 ATS 合規性，請傳送電子郵件到 <a href="mailto:CompanyPortalBeta@microsoft.com?subject=Register to TestFlight ATS Company Portal app">CompanyPortalBeta@microsoft.com</a>，並附上您的姓氏、名字、電子郵件地址和公司名稱。 如需詳細資訊，請檢閱我們的 [Intune 支援部落格](https://aka.ms/compportalats)。

## <a name="see-also"></a>另請參閱
* [Microsoft Intune 部落格](http://go.microsoft.com/fwlink/?LinkID=273882)
* [雲端平台藍圖](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [公司入口網站 UI 中的新增功能](whats-new-app-ui.md)
* [前幾個月的新功能](whats-new-archive.md)
