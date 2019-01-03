---
title: 前幾個月的 Microsoft Intune 新功能 - Azure | Microsoft Docs
titlesuffix: ''
description: 檢閱 Intune 新功能頁面中較舊的公告
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 290d60732130a82fb3daf7779142605ebc0bfeaa
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112998"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune 的新功能 - 前幾個月

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="march-2018"></a>2018 年 3 月

### <a name="app-management"></a>應用程式管理

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune 即將到期的 iOS 企業營運 (LOB) 應用程式警示 <!-- 748789 -->

在 Azure 入口網站中，Intune 會提醒您有即將到期的 iOS 企業營運應用程式。 上傳新版 iOS 企業營運應用程式之後，Intune 就會從應用程式清單中移除到期通知。 此到期通知只對新上傳的 iOS 企業營運應用程式有效。 在 iOS LOB 應用程式佈建設定檔到期前 30 天會出現警告。 到期時，警示就會變更為 [已到期]。

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>以十六進位碼自訂您的公司入口網站佈景主題 <!--1049561 -->

您可以使用十六進位碼自訂公司入口網站應用程式的佈景主題色彩。 當您輸入您的十六進位碼時，Intune 會判斷可在文字色彩與背景色彩之間提供最高程度對比的文字色彩。 您可以在 [用戶端應用程式] > **[公司入口網站]** 中預覽文字色彩，與公司標誌比對。

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise 依據群組來包含和排除應用程式指派 <!-- 1813081 -->

Android Enterprise (先前稱為 Android for Work) 支援包含及排除群組，但不支援預先建立的 [所有使用者] 和 [所有裝置] 內建群組。 如需詳細資訊，請參閱 [Microsoft Intune 的包含與排除應用程式指派](apps-inc-exl-assignments.md)。


### <a name="device-management"></a>裝置管理

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>在 IE、Microsoft Edge 或 Chrome 中將所有裝置匯出成 CSV 檔案 <!-- 2258071 -->
在 [裝置] > [所有裝置] 中，您可以將裝置**匯出**成 CSV 格式的清單。 裝置超過 10,000 部的 Internet Explorer (IE) 使用者可以成功將其裝置匯出成多個檔案。 每個檔案最多可包含 10,000 部裝置。

裝置超過 30,000 部的 Edge 和 Chrome 使用者可以成功將其裝置匯出成多個檔案。 每個檔案最多可包含 30,000 部裝置。

[管理裝置](device-management.md)可以針對您可以對所管理裝置執行的操作，提供更多的詳細資料。

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune 服務中的新安全性增強功能  <!-- 1637539 -->   

我們已在 Azure 上的 Intune 中導入一個切換，可供 Intune 獨立客戶用來將沒有任何已指派原則的裝置視為 [符合規範] (關閉安全性功能)，或將這些裝置視為 [不符合規範] (開啟安全性功能)。 這將可確保只有在評估裝置合規性之後，才能存取資源。

此功能影響您的方式會依您是否已經指派合規性原則而有所不同。

- 如果您是新的或現有的帳戶，而且未將任何合規性原則指派給裝置，則此切換自動設定為 [符合規範]。 在主控台中，預設是將此功能設定為關閉。 這不會影響任何使用者。
- 如果您是現有的帳戶，而且有任何已獲指派合規性原則的裝置，則此切換會自動設定為 [不符合規範]。 隨著三月更新的首度發行，預設就會將此功能設定為開啟。

如果您使用合規性原則搭配「條件式存取」(CA)，並且開啟此功能，CA 現在就會封鎖任何未至少已獲指派一個合規性原則的裝置。 除非您至少將一個合規性原則指派給所有裝置，否則與這些裝置關聯且先前已獲允許存取電子郵件的使用者將會失去其存取權。   

請注意，雖然預設切換狀態隨著 Intune 服務的三月更新而立即顯示在 UI 中，但系統並不會立即實施此切換狀態。 在我們讓您的帳戶擁有可運作的切換以進行正式發行前的小眾測試之前，您對此切換進行的任何變更將不會影響裝置合規性。 當我們完成您帳戶的正式發行前小眾測試之後，會透過「訊息中心」通知您。 在您的 Intune 服務進行三月更新之後，這可能會花費幾天的時間。

**其他資訊**：[https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>增強的越獄偵測 <!-- 846515 -->

加強的越獄偵測是一項新的合規性設定，可改進 Intune 評估已越獄裝置的方式。 此設定會使裝置更頻繁地簽入 Intune ，這會使用裝置的位置服務並影響電池使用量。

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>重設 Android O 裝置的密碼 <!-- 1238299 -->
您將能夠使用工作設定檔重設已註冊 Android 8.0 裝置的密碼。 當您向 Android 8.0 裝置傳送「重設密碼」要求時，它會將新的裝置解除鎖定密碼或受控設定檔查問設定成目前的使用者。 這會傳送密碼或查問，並立即生效。

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>讓合規性原則以裝置群組中的裝置為目標 <!--1307012 -->

您可以讓合規性原則以使用者群組中的使用者為目標。 在此更新中，您可以讓合規性原則以裝置群組中的裝置為目標。 隨著裝置群組一起作為目標的裝置不會收到任何合規性動作。

#### <a name="new-management-name-column----1333586---"></a>新的管理名稱資料行 <!-- 1333586 -->
 [裝置] 刀鋒視窗中會提供名為 [管理名稱] 的新資料行。 此名稱會依照下列公式自動產生且不可編輯，並會指派給每一個裝置：
- 所有裝置的預設名稱：<username><em><devicetype></em><enrollmenttimestamp>
- 針對大量新增裝置：<PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

這是在 [裝置] 刀鋒視窗中的可選資料行。 預設並不會提供此資料行，您只能藉由使用資料行選取器來存取它。 裝置名稱不會受到這個新資料行影響。

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>每 15 分鐘都會提示 iOS 裝置輸入PIN <!--1550837 -->
將合規性或設定原則套用至 iOS 裝置之後，系統會每隔 15 分鐘提示使用者設定 PIN。 系統會持續提示使用者，直到設定 PIN 為止。

#### <a name="schedule-your-automatic-updates---1805514---"></a>排程自動更新 <!--1805514 -->
Intune 可讓您使用 [Windows Update Ring 設定](windows-update-for-business-configure.md)來控制自動更新安裝。 在此更新中，您可以排定重複發生的更新，包括週、日及時間。

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>使用完整辨別名稱作為 SCEP 憑證的主體 <!--2221763 -->
當您建立 SCEP 憑證設定檔時，會輸入主體名稱。 在此更新中，您可以使用完整辨別名稱作為主體。 針對 [主體名稱]，選取 [自訂]，然後輸入 `CN={{OnPrem_Distinguished_Name}}`。 若要使用 `{{OnPrem_Distinguished_Name}}` 變數，請務必將使用 [Azure Active Directory (AD) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) 的 `onpremisesdistingishedname` 使用者屬性與 Azure AD 同步。

### <a name="device-configuration"></a>裝置設定

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>啟用藍牙連絡人共用 - Android for Work <!--1098983 -->
Android 預設會防止工作設定檔中的連絡人與藍牙裝置同步。 因此，工作設定檔連絡人不會顯示在藍牙裝置的呼叫者識別碼上。

在此更新中，[Android for Work] > [裝置限制] > [工作設定檔設定] 會有一個新的設定：
- 透過藍牙的連絡人共用

Intune 系統管理員可以設定這些設定，以啟用共用。 將裝置與汽車藍牙裝置配對時，這十分有用，而汽車藍牙裝置顯示免持式使用的呼叫者識別碼。 啟用時，會顯示工作設定檔連絡人。 未啟用時，不會顯示工作設定檔連絡人。

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>設定閘道管理員以控制 macOS 應用程式下載來源 <!-- 1690459 -->

您可以藉由控制可下載應用程式的位置，以設定 Gatekeeper 來為您的裝置提供應用程式安全防護。 您可以設定下列下載來源：**Mac App Store**、**Mac App Store 和已識別的開發人員**或**任何位置**。 您可以藉由按住 Control 並同時按一下來覆寫這些 Gatekeeper 控制措施，以設定使用者是否可以安裝應用程式。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到這些設定。

#### <a name="configure-the-mac-application-firewall----1690461---"></a>設定 Mac 應用程式防火牆 <!-- 1690461 -->

您可以設定 Mac 應用程式防火牆。 您可以利用此項目以每一應用程式為單位控制連線，而非以每一連接埠為單位。 這讓您能更輕鬆地取得防火牆保護的優點，也可協助防止不想要的應用程式控制為合法應用程式開啟之網路連接埠。

您可以在**裝置設定** -> **建立設定檔** -> **macOS** -> **Endpoint Protection** 中找到此功能。

啟用防火牆設定後，您可以使用兩種策略來設定防火牆：

- 封鎖所有連入連線

   您可以為目標裝置封鎖所有連入連線。 如果您選擇這樣做，系統就會針對所有應用程式封鎖連入連線。

- 允許或封鎖特定應用程式

   您可以允許或封鎖特定的應用程式，使其無法接收連入連線。 您也可以啟用隱形模式，以避免回應探查要求。

####  <a name="detailed-error-codes-and-messages----1376342---"></a>詳細的錯誤碼和訊息<!-- 1376342 -->

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

#### <a name="disable-checks-on-device-restart---1805490---"></a>停用裝置重新啟動的檢查 <!--1805490 -->
Intune 可讓您控制[管理軟體更新](windows-update-for-business-configure.md)。 在此更新中，預設會提供並啟用 <strong>[重新啟動檢查]</strong> 屬性。 若要跳過重新啟動裝置時進行的典型檢查 (如作用中使用者、電池電量等等) 時，請選取 [跳過]。

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>可供部署通道使用的新 Windows 10 Insider Preview 通道 <!-- 1746293 -->
現在，當您建立 Windows 10 部署通道時，可以選擇選取下列 Windows 10 Insider Preview 維護通道：
- Windows 測試人員組建 &#8208; 快
- Windows 測試人員組建 &#8208; 慢
- 發行 Windows 測試人員組建 

如需有關這些通道的詳細資訊，請參閱[管理 Insider Preview 組建](https://insider.windows.com/for-business-organization-admin/)。   
如需有關在 Intune 中建立部署通道的詳細資訊，請參閱[管理 Intune 中的軟體更新](windows-update-for-business-configure.md)。

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>新的 Windows Defender 惡意探索防護設定 <!-- 1631893 -->

有六項新的 [攻擊面縮減] 設定和擴充的 [受控資料夾存取權: 資料夾保護] 功能可用。 這些設定位於：Device configuration\Profiles\
建立 profile\Endpoint protection\Windows Defender 惡意探索防護。

#### <a name="attack-surface-reduction"></a>攻擊表面縮減

|設定名稱  |設定選項  |描述  |
|---------|---------|---------|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖可執行檔執行，除非它們符合普遍性、存留期或信任的清單準則。|

#### <a name="controlled-folder-access"></a>受控資料夾存取權

|              設定名稱               |                                                              設定選項                                                              | 描述 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 資料夾防護 (已實作) | 未設定、啟用、僅稽核 (已實作)<br><br> <strong>新增</strong><br>封鎖磁碟修改、稽核磁碟修改 |             |

保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

### <a name="intune-apps"></a>Intune 應用程式

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 網站可以要求使用 Intune Managed Browser 應用程式，並支援 Managed Browser (公開預覽) 的單一登入 <!-- 710595 -->

使用 Azure Active Directory (Azure AD) 時，您現在可在行動裝置上限制只有 Intune Managed Browser 應用程式可以存取網站。 在 Managed Browser 中，網站資料會受到保護，而且會與使用者個人資料分開管理。 此外，Managed Browser 將針對受 Azure AD 保護的網站支援單一登入。 登入 Managed Browser，或是在裝置上具有由 Intune 所管理另一個應用程式時使用 Managed Browser 之際，將能讓使用者在無需輸入其認證的情況下，允許 Managed Browser 存取受 Azure AD 保護的公司網站。 這項功能適用於 Outlook Web Access (OWA) 和 SharePoint Online 等網站，以及其他如透過 Azure App Proxy 所存取內部網路資源的企業網站。 如需詳細資訊，請參閱 [Access controls in Azure Active Directory conditional access](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls) (Azure Active Directory 條件式存取中的存取控制)。

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Android 版公司入口網站的視覺效果更新 <!--976944 -->

我們已更新 Android 版公司入口網站應用程式，以遵循 Android 的 [Material Design](https://material.io/) 指導方針。 您可以在[應用程式 UI 最新內容](whats-new-app-ui.md)一文中看到新圖示的影像。

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>改善的公司入口網站註冊 <!-- 1874230 eeready-->
使用者如果是在 Windows 10 1703 組建或更新版本上使用公司入口網站來註冊裝置，現在將能夠在不離開應用程式的情況下，完成第一個註冊步驟。
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens 和 Surface Hub 現在會出現在裝置清單 <!--1725868 --> 中
我們已新增支援，可向 Android 版公司入口網站應用程式顯示已在 Intune 註冊的 HoloLens 和 Surface Hub 裝置。

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>為大量採購方案 (VPP) 電子書自訂書籍類別 <!-- 1488911 -->
您可以建立自訂電子書類別，然後將 VPP 電子書指派給這些自訂電子書類別。 終端使用者便可以看見新建立的電子書類別，以及指派給這些類別的書籍。 如需詳細資訊，請參閱[使用 Microsoft Intune 管理大量採購的應用程式與書籍](vpp-apps.md)。  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>針對 Windows 版公司入口網站應用程式傳送意見反應選項的支援已變更 <!-- 2070166 -->
從 2018 年 4 月 30 日起，Windows 版公司入口網站應用程式中的 [傳送意見反應] 選項僅可在執行 Windows 10 年度更新 (1607) 及更新版本的裝置上執行。 搭配下列版本使用 Windows 版公司入口網站應用程式時，不再支援傳送意見反應的選項：  
- Windows 10，1507 版本  
- Windows 10，1511 版本  
- Windows Phone 8.1 

如果您的裝置執行的是 Windows 10 RS1 或更新版本，請從市集下載最新的 Windows 版公司入口網站應用程式。 如果您執行的是不支援的版本，請繼續透過下列通道傳送意見反應： 
- Windows 10 上的 [意見反應中樞] 應用程式
- 電子郵件 WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>新的 Windows Defender 應用程式防護設定 <!-- 1631890 -->

- **啟用圖形加速**：系統管理員能夠啟用 Windows Defender 應用程式防護的虛擬圖形處理器。 此設定可讓 CPU 將圖形轉譯卸載至 vGPU。 使用圖形運算密集的網站或觀賞容器內的影片時，這可以改善效能。

- **SaveFilestoHost**：系統管理員可以讓檔案從容器中執行的 Microsoft Edge 傳遞到主機檔案系統。 開啟這個功能可讓使用者從容器中的 Microsoft Edge 將檔案下載到主機檔案系統。

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>根據管理狀態將 MAM 保護原則設為目標 <!-- 1665993 -->
您可以根據裝置管理狀態將 MAM 原則設為目標：
- **Android 裝置** - 您可以將非受控裝置、受 Intune 管理的裝置及受 Intune 管理的 Android Enterprise 設定檔 (先前稱為 Android for Work) 設為目標。
- **iOS 裝置** - 您可以將非受控裝置 (僅限 MAM) 或受 Intune 管理的裝置設為目標。

    > [!NOTE]
    > - 此功能的 iOS 支援會在 2018 年的整個 4 月首度發行。

如需詳細資訊，請參閱[根據裝置管理狀態將應用程式保護原則設為目標](app-protection-policies.md)。

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>改進 Windows 版公司入口網站應用程式中的語言 <!-- 1683758 -->
我們已改進 Windows 10 版公司入口網站中的語言，不僅對使用者來說更簡單明瞭，也更專屬於您的公司。 若要查看我們所做改進的範例影像，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>在我們的文件中新增有關使用者隱私權的部分 <!-- 1440709 -->
我們努力讓使用者對其資料和隱私權有更多的控制，因此我們發佈了文件更新，說明如何檢視及移除公司入口網站應用程式儲存在本機的資料。 您可以在下列位置找到這些更新：

- **Android**：[如何從 Intune 移除 Android 裝置](/intune-user-help/unenroll-your-device-from-intune-android)
- **Android (如果使用者已拒絕使用條款)**：[如果您已拒絕「使用條款」，請移除您的裝置](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**：[從 Intune 移除 iOS 裝置](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**：[從 Intune 移除 Windows 裝置](/intune-user-help/unenroll-your-device-from-intune-windows)

## <a name="february-2018"></a>2018 年 2 月

### <a name="device-enrollment"></a>裝置註冊

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 -->

Intune 現在支援註冊最多達 100 個來自不同 [Apple 裝置註冊計劃 (DEP)](device-enrollment-program-enroll-ios.md) 或 [Apple School Manager](apple-school-manager-set-up-ios.md) 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>查看每位使用者的註冊限制 <!-- 1634444 eeready wnready -->
在 [疑難排解] 刀鋒視窗中，您現在可以從 [指派] 清單中選取 [註冊限制]，以查看對每位使用者有效的[註冊限制](enrollment-restrictions-set.md)。

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>適用於 Apple 大量註冊的使用者驗證新選項 <!-- 747625 eeready -->

> [!NOTE]
> 新的租用戶會立即看到此項目。 現有租用戶的這項功能會在 4 月推出。 全部推出之後，您可能無法存取這些新功能。

Intune 現在可讓您將公司入口網站應用程式用於下列註冊方法，以對裝置進行驗證：

- Apple 裝置註冊方案
- Apple School Manager
- Apple Configurator 註冊

使用 [公司入口網站] 選項時，可以強制執行 Azure Active Directory 多重要素驗證，而不會封鎖這些註冊方法。

使用 [公司入口網站] 選項時，針對使用者親和性註冊，Intune 會跳過 iOS 設定輔助程式中的使用者驗證。 這表示該裝置一開始會註冊為無使用者的裝置，因此不會收到使用者群組的設定或原則。 它只會接收裝置群組的設定和原則。 不過，Intune 會自動在裝置上安裝公司入口網站應用程式。 第一位啟動並登入公司入口網站應用程式的使用者，將會在 Intune 中與該裝置產生關聯。 此時，使用者將會收到其使用者群組的設定和原則。 使用者關聯需要重新註冊才可以變更。

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>Intune 支援多個 Apple DEP / Apple School Manager 帳戶 <!-- 747685 eeready -->

Intune 現在支援註冊最多達 100 個來自不同 Apple 裝置註冊計劃 (DEP) 或 Apple School Manager 帳戶的裝置。 每個上傳的權杖可以針對註冊設定檔和裝置來個別管理。 不同的註冊設定檔可以根據上傳的 DEP/School Manager 權杖來自動指派。 如果上傳了多個 School Manager 權杖，則一次只能與 Microsoft School Data Sync 共用一個權杖。

移轉之後，透過 Graph 來管理 Apple DEP 或 ASM 的搶鮮版 (Beta) Graph API 與發佈的指令碼將無法再運作。 新的搶鮮版 (Beta) Graph API 正在開發，將會在移轉後發行。

### <a name="remote-printing-over-a-secure-network----1709994----"></a>透過安全網路進行遠端列印 <!-- 1709994  -->
PrinterOn 的無線行動列印方案，可讓使用者隨時隨地透過安全的網路來進行遠端列印。 PrinterOn 將與適用於 iOS 和 Android 的 Intune APP SDK 整合。 您將能透過管理主控台中的 [應用程式保護原則] 刀鋒視窗，讓應用程式保護原則以此應用程式為目標。 終端使用者將能夠透過 Play 商店或 iTunes 下載 'PrinterOn for Microsoft' 應用程式，以在其 Intune 生態系統內使用。

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>macOS 公司入口網站支援使用裝置註冊管理員註冊 <!-- 1352411 -->

使用者現在於使用 macOS 公司入口網站進行註冊時，已可以使用裝置註冊管理員。

### <a name="device-management"></a>裝置管理

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 健全狀況狀態和威脅狀態報告 <!--854704 -->

瞭解 Windows Defender 的健全狀況狀態是管理 Windows 電腦的關鍵。  使用此更新，Intune 會在 Windows Defender 代理程式的健全狀況狀態中新增報告和動作。 在[裝置合規性工作負載](compliance-policy-monitor.md)中使用狀態積存報表，即可看到需要下列任一項的裝置：
- 簽章更新
- 重新啟動
- 手動介入
- 完整掃描
- 需要介入的其他代理程式狀態

每個狀態類別的鑽研報表都會列出需要注意的個別電腦，或那些回報為**清除**的電腦。

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>裝置限制的新隱私權設定 <!--1308926 -->
裝置現在有[兩項新的隱私權設定](device-restrictions-windows-10.md#privacy)可用：
- **發佈使用者活動**：將此項設定為 [封鎖] 以防止共用體驗以及在工作切換器中探索最近使用的資源。
- **僅限本機活動**：將此項設定為 [封鎖] 以防止共用體驗，以及僅根據本機活動，在工作切換器中探索最近使用的資源。

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>Microsoft Edge 瀏覽器的新設定 <!--1469166 -->
現在使用 Microsoft Edge 瀏覽器的裝置有[兩項新設定](device-restrictions-windows-10.md#microsoft-edge-browser)可用：[我的最愛檔案路徑] 和 [我的最愛的變更]。

### <a name="app-management"></a>應用程式管理

#### <a name="protocol-exceptions-for-applications---1035509---"></a>應用程式的通訊協定例外狀況 <!--1035509 -->

您現在可以建立 Intune 行動應用程式管理 (MAM) 資料傳輸原則的例外狀況，開啟特定的非受控應用程式。 這類應用程式必須為 IT 所信任。 當資料傳輸原則設為**僅限受管理應用程式** 時，除您建立的例外狀況，資料傳輸仍僅限於受 Intune 管理的應用程式。 您可以使用通訊協定 (iOS) 或套件 (Android) 來建立限制。

例如，您可以將 Webex 套件新增為 MAM 資料傳輸原則的例外狀況。 這樣可以直接在 Webex 應用程式中開啟受控 Outlook 電子郵件訊息中的 Webex 連結。 其他非受控應用程式中的資料傳輸仍會受到限制。 如需詳細資訊，請參閱[應用程式的資料傳輸原則例外狀況](app-protection-policies-exception.md)。

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 搜尋結果中的 Windows 資訊保護 (WIP) 加密資料 <!-- 1469193 -->
Windows 資訊保護 (WIP) 原則中的設定現在可讓您控制 Windows 搜尋結果是否包含 WIP 加密資料。 在 Windows 資訊保護原則的 [進階設定] 中，選取 [允許 Windows 搜尋索引子搜尋加密項目] 來設定此應用程式保護原則選項。 應用程式保護原則必須設為 *Windows 10* 平台，且應用程式原則 [註冊狀態] 必須設為 [註冊]。 如需詳細資訊，請參閱[允許 Windows 搜尋索引子搜尋加密項目](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)。

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>設定自行更新的行動 MSI 應用程式 <!-- 1740840 -->
您可以設定已知的自行更新行動 MSI 應用程式略過版本檢查程序。 這項功能對於不陷入競爭狀況很有用。 例如，當應用程式開發人員正在執行自動更新的應用程式，也正被 Intune 更新時，就可能發生這種競爭狀況。 雙方都可能嘗試在 Windows 用戶端上強制執行某個版本的應用程式，這可能造成衝突。 對於這些自動更新的 MSI 應用程式，您可以在 [應用程式資訊] 刀鋒視窗中設定 [略過應用程式版本] 設定。 當此設定切換為 [是] 時，Microsoft Intune 將會忽略 Windows 用戶端上安裝的應用程式版本。

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune 支援的相關應用程式授權集 <!-- 1864117 -->
Azure 入口網站中的 Intune 現在支援相關的應用程式授權集，作為 UI 中單一應用程式項目。 此外，從商務用 Microsoft Store 同步處理的任何離線授權應用程式都會合併到單一應用程式項目，而個別套件的所有部署詳細資料都會移轉至單一項目。 若要在 Azure 入口網站中檢視相關的應用程式授權集，請選取 [用戶端應用程式] 刀鋒視窗中的 [應用程式授權]。

### <a name="device-configuration"></a>裝置設定
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>自動加密的 Windows 資訊保護 (WIP) 檔案副檔名 <!-- 1463582 -->
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

|設定名稱  |設定選項  |描述  |
|---------|---------|---------|
|執行電子郵件中受密碼保護的可執行檔內容|封鎖、稽核、未設定|避免執行透過電子郵件下載的受密碼保護可執行檔。|
|進階勒索軟體防護|啟用、稽核、未設定|使用積極的勒索軟體防護。|
|從 Windows 本機安全性授權子系統設立認證竊取旗標|啟用、稽核、未設定|從 Windows 本機安全性授權子系統設立認證竊取旗標 (lsass.exe)。|
|從 PSExec 和 WMI 命令建立處理程序|封鎖、稽核、未設定|封鎖源自 PSExec 和 WMI 命令的處理程序建立。|
|從 USB 執行的不受信任和不帶正負號的處理程序|封鎖、稽核、未設定|封鎖從 USB 執行的不受信任和不帶正負號的處理程序。|
|不符合普遍性、存留期或受信任清單條件的可執行檔|封鎖、稽核、未設定|封鎖可執行檔執行，除非它們符合普遍性、存留期或信任的清單準則。|

##### <a name="controlled-folder-access"></a>受控資料夾存取權

|              設定名稱               |                                                              設定選項                                                              | 描述 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 資料夾防護 (已實作) | 未設定、啟用、僅稽核 (已實作)<br><br> <strong>新增</strong><br>封鎖磁碟修改、稽核磁碟修改 |             |

保護檔案和資料夾免於惡意應用程式未經授權的變更。<br><br>**啟用**：免於不受信任的應用程式修改或刪除受保護資料夾中的檔案，也不讓這些應用程式在磁碟磁區寫入資料。<br><br>
**僅封鎖磁碟修改**：<br>封鎖不受信任的應用程式在磁碟磁區寫入資料。 不受信任的應用程式仍然可以修改或刪除受保護資料夾中的檔案。|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Windows 10 和更新版本系統安全性設定新增項目的相容性原則 <!--1704133-->

Windows 10 相容性設定的新增項目現在已可供使用，但需要防火牆及 Windows Defender 防毒軟體才能包含此內容。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>支援來自商務用 Microsoft 網上商店的離線應用程式 <!--1222672-->
您從商務用 Microsoft Store 購買的離線應用程式現在會同步處理至 Azure 入口網站。 您可以將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>防止終端使用者在工作設定檔中手動新增或移除帳戶 <!-- 1728700 -->

當您將 Gmail 應用程式部署到 Android for Work 設定檔時，現在可以使用 Android for Work 裝置限制設定檔中的 [Add and remove accounts] (新增與移除帳戶) 設定，防止終端使用者在工作設定檔中手動新增或移除帳戶。


## <a name="january-2018"></a>2018 年 1 月

### <a name="device-enrollment"></a>裝置註冊

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>過期的權杖與即將過期之權杖的警示 <!-- 1639263 -->
概觀頁面現在會針對過期的權杖與即將過期的權杖顯示警示。 當您按一下單一權杖的警示時，將會移至權杖的詳細資料頁面。  當您按一下多個權杖的警示時，將會移至所有權杖的清單，其中包含權杖的狀態。 系統管理員應該在到期日之前更新其權杖。

### <a name="device-management"></a>裝置管理

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS 裝置的遠端「清除」命令支援 <!-- 1438084 -->

系統管理員可以針對 macOS 裝置遠端發出「清除」命令。

> [!IMPORTANT]
> 清除命令無法回復，應該謹慎使用。

清除命令會從裝置移除所有資料，包括作業系統。 這樣做也會從 Intune 管理移除裝置。 系統不會向使用者發出任何警告，且將在發出命令之際，立即開始清除。

您必須設定 6 位數的復原 PIN。 此 PIN 可用來將已清除的裝置解除鎖定，並開始重新安裝作業系統。 開始進行清除後，PIN 會出現在 Intune 中裝置 [概觀] 刀鋒視窗的狀態列上。 在清除進行期間，PIN 會持續顯示。 完成清除後，裝置會完全從 Intune 管理中消失。 請務必記錄復原 PIN，以供還原裝置的人員來使用。

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>撤銷 iOS 大量採購方案權杖的授權 <!-- 820870 -->
您可針對指定的 VPP 權杖，撤銷所有 iOS Volume Purchasing Program (VPP) 應用程式的授權。

### <a name="app-management"></a>應用程式管理

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>撤銷 iOS 大量採購方案應用程式 <!-- 820863 -->
對於具有一或多個 iOS Volume Purchasing Program (VPP) 應用程式的指定裝置，您可將裝置撤銷與其建立關聯的裝置應用程式授權。 撤銷應用程式授權將不會從該裝置解除安裝相關聯的 VPP 應用程式。 若要解除安裝 VPP 應用程式，您必須將指派動作變更為 [解除安裝]。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式](vpp-apps-ios.md)。

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>將 Office 365 行動應用程式指派給使用內建應用程式類型的 iOS 和 Android 裝置 <!-- 1332318 -->
**內建**應用程式類型讓您可更輕鬆地建立 Office 365 應用程式，並將其指派給您管理的 iOS 及 Android 裝置。 這些應用程式包括 0365 應用程式，例如 Word、Excel、PowerPoint 和 OneDrive。 您可以將特定的應用程式指派給應用程式類型，並編輯應用程式資訊設定。

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>依據群組來包含和排除應用程式指派 <!-- 1406920 -->

在應用程式指派期間和選取指派類型後，您可選取要包含的群組及要排除的群組。

### <a name="device-configuration"></a>裝置設定

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>您可包含和排除指派，將應用程式設定原則指派給群組  <!-- 1480316 -->

您可使用包含和排除指派的組合，將應用程式設定原則指派給一群使用者和裝置。 您可選擇自選群組或虛擬群組作為指派。 虛擬群組可以包括 [所有使用者]、[所有裝置] 或 [所有使用者及所有裝置]。

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>支援 Windows 10 版本升級原則 <!-- 903672(archived), 1119689 -->  
您可以建立 Windows 10 版本升級原則，以將 Windows 10 裝置升級至 Windows 10 教育版、Windows 10 教育版 N、Windows 10 專業版、Windows 10 專業版 N、Windows 10 專業教育版和 Windows 10 專業教育版 N。如需 Windows 10 版本升級的詳細資料，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune 的條件式存取原則只能從 Azure 入口網站使用 <!-- 1737088 1634311 -->

從這個版本開始，您必須在 [Azure 入口網站](https://portal.azure.com)，從 [Azure Active Directory] > [條件式存取] 設定及管理您的條件式存取原則。 為了方便起見，您也可以從 Azure 入口網站中的 Intune 存取此刀鋒視窗，位置是 [Intune] > [條件式存取]。

#### <a name="updates-to-compliance-emails---1637547---"></a>更新合規性電子郵件 <!--1637547 -->

當傳送電子郵件以報告不符合規範的裝置時，會包含不符合規範之裝置的相關詳細資料。

### <a name="intune-apps"></a>Intune 應用程式

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android 裝置之「解決」動作的新功能 <!--1583480-->

Android 公司入口網站應用程式將**更新裝置設定**的「解決」動作擴充為解決[裝置加密問題](/intune-user-help/encrypt-your-device-android)。

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10 的公司入口網站應用程式提供遠端鎖定 <!--676506-->
使用者現在可以從 Windows 10 的公司入口網站應用程式遠端鎖定其裝置。 這不會顯示在他們正使用的本機裝置上。

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>針對 Windows 10 公司入口網站應用程式，可以更容易解決合規性問題 <!--676546-->
使用 Windows 裝置的終端使用者將可在公司入口網站應用程式中點選不相容的原因。 在可能的情況下，這將會將他們帶到 [設定] 應用程式中的正確位置以修正該問題。

## <a name="december-2017"></a>2017 年 12 月

### <a name="device-configuration"></a>裝置設定

#### <a name="new-automatic-redeployment-setting----1469168---"></a>新的自動重新部署設定 <!-- 1469168 -->
**自動重新部署**設定允許具有系統管理權限的使用者，在裝置鎖定畫面上使用 **CTRL + Win + R** 來刪除所有使用者資料和設定。 裝置會自動重新設定並重新註冊以納入管理。 您可以在 [Windows 10] > [裝置限制] > [一般] > [自動重新部署] 下找到此設定。 如需詳細資料，請參閱 [Windows 10 的 Intune 裝置限制設定](device-restrictions-windows-10.md#general)。

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>支援 Windows 10 版本升級原則中的其他來源版本  <!-- 903672,  1119689 -->
您現在可以使用 Windows 10 版本升級原則，從其他 Windows 10 版本 (Windows 10 專業版、Windows 10 專業教育版、Windows 10 Cloud 等) 進行升級。 在此版本之前，支援的版本升級路徑十分有限。 如需詳細資訊，請參閱[如何設定 Windows 10 版本升級](edition-upgrade-configure-windows-10.md)。

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>新的 Windows Defender 資訊安全中心 (WDSC) 裝置組態設定檔設定 <!-- 1335507 -->

Intune 在 [端點保護] 下新增了新的裝置組態設定檔設定區段，名為 [Windows Defender 資訊安全中心]。 IT 系統管理員可以設定終端使用者可存取的 Windows Defender 資訊安全中心應用程式方針。 如果 IT 系統管理員在 Windows Defender 資訊安全中心應用程式中隱藏某個方針，則與該隱藏方針相關聯的所有通知都不會顯示在使用者的裝置上。

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


### <a name="role-based-access-control"></a>角色型存取控制

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>名為 Current User 的新實體集合限於目前作用中的使用者資料 <!-- 1667026 -->

**User** 實體集合包含企業中具有所指派授權的所有 Azure Active Directory (Azure AD) 使用者。 例如，某個使用者可能在上個月內被新增到 Intune 然後又被移除。 雖然在報告的時候這個使用者不會出現，但使用者和狀態會出現在資料中。 您可以建立一個報告，其中顯示使用者的歷程記錄在您資料中出現的期間。

相較之下，新的 **Current User** 實體集合只包含尚未被移除的使用者。 **Current User** 實體集合只包含目前作用中的使用者。 如需 **Current User** 實體的詳細資訊，請參閱 [Current User 實體的參考](reports-ref-current-user.md)。


### <a name="updated-graph-apis----1736360---"></a>更新的 Graph API <!-- 1736360 -->

在此版本中，我們已更新一些 Intune 的搶鮮版 (Beta) Graph API。 如需詳細資訊，請查看每月 [Graph API 變更記錄](https://developer.microsoft.com/graph/docs/concepts/changelog) \(英文\)。

### <a name="monitor-and-troubleshoot"></a>監視及疑難排解

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune 支援 Windows 資訊保護 (WIP) 拒絕應用程式 <!-- 1479103 -->
您可以在 Intune 中指定拒絕的應用程式。 如果應用程式遭到拒絕，它會被封鎖而無法存取公司資訊，效果與允許的應用程式清單相反。 如需詳細資訊，請參閱 [Recommended deny list for Windows Information Protection](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection) (Windows 資訊保護的建議拒絕清單)。


## <a name="november-2017"></a>2017 年 11 月

### <a name="troubleshoot-enrollment-issues-----746324---"></a>對註冊問題進行疑難排解  <!-- 746324 -->

[疑難排解] 工作區現在會顯示使用者註冊問題。 其中包含問題的詳細資料與建議的補救步驟，可協助系統管理員和技術服務人員針對相關問題進行疑難排解。 未擷取特定註冊問題，某些錯誤可能也沒有補救建議。

### <a name="group-assigned-enrollment-restrictions----747598---"></a>群組指派註冊限制 <!-- 747598 -->

身為 Intune 系統管理員，您現在可以[為使用者群組建立自訂的裝置類型和裝置限制註冊限制](enrollment-restrictions-set.md)。

Intune Azure 入口網站可讓您每種限制類型最多建立 25 個執行個體，以指派給使用者群組。 群組指派的限制會覆寫預設的限制。

限制類型的所有執行個體都使用嚴格排序的清單維護。 此順序會定義衝突解決方法的優先順序值。 受到多個限制執行個體影響的使用者，只受擁有最高優先順序值的執行個體限制。 您可以變更指定的執行個體優先順序，只要將它拖曳到清單中的不同位置即可。

當 Android for Work 設定從 [Android For Work 註冊] 功能表移轉到 [註冊限制] 功能表時，即發佈這項功能。 因為這項移轉可能需要花費數天，而您的帳戶可能要升級 11 月版本的其他組件後，您才會看到 [註冊限制] 的群組指派成為啟用狀態。

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>支援多個網路裝置註冊服務 (NDES) 連接器<!-- 1528104 -->

NDES 可讓行動裝置依據簡單憑證註冊通訊協定 (SCEP) 在沒有網域認證的情況下取得憑證。
使用這項更新，可支援多個 NDES 連接器。

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>從 Android 裝置獨立管理 Android for Work 裝置<!-- 1490731 EEready-->

Intune 支援從 Android 平台獨立管理 Android for Work 裝置的註冊。 這些設定在 [裝置註冊] > [註冊限制] > [裝置類型限制] 下管理。 (原位於 [裝置註冊] > [Android for Work 註冊] > [Android for Work 註冊設定] 下。)

根據預設，Android for Work 裝置設定與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。

如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

使用新設定時，請考慮下列各點：

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

### <a name="google-play-protect-support-on-android----908720---"></a>Android 中的 Google Play Protect 支援 <!-- 908720 -->

在 Android Oreo 版本中，Google 引進名為 Google Play Protect 的安全性功能套件，可讓使用者和組織執行安全的應用程式和保護 Android 映像。 Intune 現在支援 Google Play Protect 功能，包括 SafetyNet 遠端證明。 系統管理員可以設定合規性原則需求，藉此要求設定 Google Play Protect 且其狀況良好。
[SafetyNet 裝置證明] 設定可要求裝置連線至 Google 服務，以驗證裝置狀況良好且未遭入侵。 系統管理員也可以設定 Android for Work 的組態設定檔設定，以要求已安裝的應用程式必須經過 Google Play 服務驗證。 如果裝置不符合 Google Play Protect 需求的規範，條件式存取可能會禁止使用者存取公司資源。

- 了解[如何建立可啟用「Google Play 安全防護」的裝置合規性原則](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)。

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>允許來自受管理應用程式的文字通訊協定 <!-- 1414050  -->

Intune App SDK 管理的應用程式可傳送 SMS 訊息。


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>已更新應用程式安裝報表，以包含安裝擱置中狀態 <!-- 1249446 -->  

透過 [用戶端應用程式] 工作負載中的 [應用程式] 清單，每個應用程式可存取的**應用程式安裝狀態**報告，現在包含使用者和裝置的**安裝擱置中**計數。

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>適用於行動裝置威脅偵測的 iOS 11 應用程式清查 API <!-- 1391759 -->

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

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>將混合式 MDM 使用者和裝置移轉至 Intune 獨立版 <!-- 1463747 wnready -->
Azure 入口網站中現在提供新的程序和工具，以將使用者和其裝置從混合式 MDM 移至 intune，讓您可以執行下列工作：
- 將原則與設定檔從 Configuration Manager 主控台複製到 Azure 入口網站的 Intune
- 將使用者子集移至 Azure 入口網站的 Intune，同時將其餘部分保留在混合式 MDM 中
- 將裝置移轉至 Azure 入口網站的 Intune 但不需要重新註冊

如需詳細資料，請參閱[將混合式 MDM 使用者和裝置移轉至 Intune 獨立版](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)。

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>內部部署 Exchange Connector 高可用性支援<!-- 676614 -->
在 Exchange Connector 使用指定的 CAS 建立與 Exchange 的連線之後，連接器現在便能夠探索其他 CAS。 如果無法使用主要的 CAS，連接器將容錯移轉至另一個 CAS (如果有的話)，直到有可用的主要 CAS 為止。 如需詳細資訊，請參閱[內部部署 Exchange Connector 高可用性支援](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)。

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>從遠端重新啟動 iOS 裝置 (僅受監督) <!-- 1424595 -->

您現在可以使用裝置動作觸發受監督的 iOS 10.3+ 裝置，令它重新啟動。 如需使用裝置重新啟動動作的詳細資訊，請參閱[使用 Intune 從遠端重新啟動裝置](device-restart.md)。

> [!Note]
> 此命令需要受監督的裝置和**裝置鎖定**存取權限。 裝置隨即重新啟動。 密碼鎖定的 iOS 裝置重新啟動後，不會重新加入 Wi-Fi 網路；重新啟動後，它們可能無法與伺服器通訊。

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS 的單一登入支援 <!-- 1333645 -->  

您可以讓 iOS 使用者使用單一登入。 編碼成在單一登入裝載中尋找使用者認證的 iOS 應用程式，因為有此裝載設定更新，所以很實用。 您也可以使用 UPN 和 Intune 裝置識別碼來設定主體名稱和領域。 如需詳細資料，請參閱[設定 Intune 以進行 iOS 裝置單一登入](sso-ios.md)。

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>新增個人裝置的「尋找我的 iPhone」<!--1427287-->
您現在可以檢視 iOS 裝置是否開啟 [啟用鎖定]。 這項功能以前位在 intune 傳統入口網站。

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>使用 Intune 從遠端鎖定受管理的 macOS 裝置 <!-- 1437691 -->

您可以鎖定遺失的 macOS 裝置，並設定 6 位數的復原 PIN。 鎖定時，[裝置概觀] 刀鋒視窗會顯示 PIN，直到傳送另一個裝置動作為止。

如需詳細資訊，請參閱[使用 Intune 從遠端鎖定受管理的裝置](device-remote-lock.md)。

### <a name="new-scep-profile-details-supported----1559808---"></a>支援新的 SCEP 設定檔詳細資料 <!-- 1559808 -->

現在於 Windows、iOS、macOS 和 Android 平台上建立 SCEP 設定檔時，系統管理員可以設定其他設定。  系統管理員可以設定 IMEI、序號或一般名稱，包括使用主體名稱格式的電子郵件。

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>重設為原廠設定時保留資料 <!--1588489 -->
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


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>顯示 Windows 10 更新通道指派 <!-- 1621837 -->
當要針對您正在檢視的使用者進行**疑難排解**時，您會看到所有 Windows 10 更新通道指派。  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender 進階威脅防護回報頻率設定 <!-- 1455974  -->
Windows Defender 進階威脅防護 (WDATP) 服務允許管理員管理受管理裝置的回報頻率。 使用新的 [加速遙測回報頻率] 選項，WDATP 可以更頻繁地收集資料及評估風險。 回報預設值最佳化速度及效能。 增加回報頻率對高風險裝置很重要。 此設定位在**裝置設定**的 **Windows Defender ATP** 設定檔中。

### <a name="audit-updates----1412961---"></a>稽核更新 <!-- 1412961 -->  
Intune 稽核會提供與 Intune 相關的變更作業記錄。  擷取所有建立、更新、刪除和遠端工作作業，並保留一年。  Azure 入口網站提供每個工作負載過去 30 天的稽核資料檢視，且可篩選。  對應的圖形 API 可讓您擷取去年儲存的稽核資料。

[稽核] 位在**監視器**群組下。 每個工作負載都有 [稽核記錄檔] 功能表項目。

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS 版公司入口網站應用程式已推出 <!--1541700-->
macOS 版 Intune 公司入口網站有已經最佳化的更新體驗，可完全顯示使用者註冊之所有裝置所需的所有資訊與合規性通知。 此外，「Intune 公司入口網站」部署至裝置之後，適用於 macOS 的 Microsoft AutoUpdate 會提供其更新。 您可以透過從 macOS 裝置登入「Intune 公司入口網站」來下載新的 macOS 版「Intune 公司入口網站」。

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner 現在是已核准應用程式的行動裝置應用程式管理 (MAM) 清單的一部分  <!-- 1248473 -->
iOS 版和 Android 版的 Microsoft Planner 應用程式現在是行動裝置應用程式管理 (MAM) 已核准的應用程式的一部分。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，將應用程式設定至所有租用戶。
- 深入了解[已核准應用程式的 MAM 清單](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)。

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS 裝置上的個別 App VPN 的需求更新頻率   <!-- 1547061 -->  
系統管理員現在可能會移除 iOS 裝置上應用程式的個別 App VPN 需求；受影響的裝置將在它們下一次 Intune 簽入後 (通常在 15 分鐘內發生)。  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>適用於 Exchange 連接器的 System Center Operations Manager 管理組件支援 <!-- 885457 -->
適用於 Exchange 連接器的 System Center Operations Manager (SCOM) 管理組件現在可協助您剖析 Exchange 連接器記錄。 此功能可在您需要針對問題進行疑難排解時，為您提供不同方式來監視服務。

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 裝置的共同管理  <!-- 1243445 -->
共同管理是一種可讓您從傳統管理過渡到現代化管理的解決方案，並提供您使用分段式方法的轉換過程。 本質上來說，共同管理解決方案可讓 Windows 10 裝置同時受 Configuration Manager 和 Microsoft Intune 管理，並聯結到 Active Directory (AD) 和 Azure Active Directory (Azure AD)。  如果您無法一次到位，此設定提供隨時間逐步實行現代化的轉換過程，讓您依據組織進展的步調來進行。  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>依 OS 版本限制 Windows 註冊 <!-- 245498 -->
您現在能夠以 Intune 系統管理員的身分指定裝置註冊的 Windows 10 最低與最高版本。 您現可在 [平台設定] 刀鋒視窗設定這些限制。

Intune 會繼續支援註冊 Windows 8.1 電腦與手機。 不過，只有 Windows 10 版本能夠設定最低與最高限制。 若要允許 8.1 裝置的註冊，請在最低限制留空。

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 未指派裝置的警示  <!-- 1631236 -->
在 [Microsoft Intune] > [裝置註冊] > [概觀] 頁面上，有新的警示可供 Windows AutoPilot 未指派的裝置使用。 此警示能夠顯示有多少 AutoPilot 方案的裝置未指派 AutoPilot 部署設定檔。 您可以使用警示中的資訊來建立設定檔，並加以指派至未指派的裝置。 當您按一下警示時，會看到 Windows AutoPilot 裝置的完整清單，以及這些裝置的詳細資訊。 如需詳細資訊，請參閱[使用 Windows AutoPilot 部署方案註冊 Windows 裝置](https://docs.microsoft.com/intune/enrollment-autopilot)。


### <a name="refresh-button-for-devices-list-------1333581---"></a>裝置清單的 [重新整理] 按鈕    <!-- 1333581 -->
因為裝置清單並不會自動重新整理，所以您可以使用新的 [重新整理] 按鈕來更新清單中顯示的裝置。

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>支援 Symantec 雲端憑證授權單位 (CA)  <!-- 1333638 -->    
Intune 現在支援 Symantec 雲端 CA，因此 Intune 憑證連接器可以將來自 Symantec 雲端 CA 的 PKCS 憑證簽發給受 Intune 管理的裝置。 如果您已經使用 Intune 憑證連接器與 Microsoft 憑證授權單位 (CA)，則可以使用現有的 Intune 憑證連接器安裝程式來新增 Symantec CA 支援。

### <a name="new-items-added-to-device-inventory-----1404455---"></a>新增至裝置清查的項目   <!--1404455 -->
下列新項目現在可用於[已註冊裝置執行的清查](device-inventory.md)：

- Wi-Fi Mac 位址
- 儲存空間總計
- 可用空間總計
- MEID
- 用戶載波

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>依據裝置的 Android 安全性修補程式下限，來設定應用程式的存取權<!-- 1278463 -->   
系統管理員可以定義裝置必須安裝的 Android 安全性修補程式下限，才能以受管理帳戶來存取受管理的應用程式。

> [!Note]  
> 這項功能只能限制 Android 6.0+ 裝置上由 Google 發行的安全性修補程式。

### <a name="app-conditional-launch-support----1193313---"></a>支援條件式啟動應用程式 <!-- 1193313 -->
現在，IT 系統管理員可以透過 Azure 管理入口網站，設定在應用程式啟動時強制執行密碼，而不是透過行動裝置應用程式管理 (MAM) 的數字 PIN。 如上進行設定後，使用者就必須在出現提示時設定並使用密碼，才能存取啟用 MAM 的應用程式。 密碼的定義為數字 PIN 和至少一個特殊字元或大寫/小寫字母。 此版 Intune 將**僅在 iOS 上**啟用這項功能。 Intune 支援密碼的方式與數字 PIN 類似，它會設定長度下限，並允許重複的字元和順序。 此功能需要應用程式 (亦即，WXP、Outlook、Managed Browser、Yammer) 的參與來就地整合 Intune App SDK 與此功能的程式碼，以在目標應用程式中強制執行密碼設定。

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>裝置安裝狀態報告中的企業營運應用程式版本號碼 <!-- 1233999 -->
在此版本中，裝置安裝狀態報告會顯示適用於 iOS 和 Android 的企業營運應用程式版本號碼。 您可以使用這些資訊來針對應用程式進行疑難排解，或找出執行過時應用程式版本的裝置。

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>系統管理員現在可以使用裝置組態設定檔來設定裝置的防火牆設定 <!-- 951708 -->   
系統管理員可以開啟裝置的防火牆，並針對網域、私用網路和公用網路設定各種通訊協定。  您可以在 "Endpoint Protection" 設定檔中找到這些防火牆設定。

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender 應用程式防護可依據組織的定義，協助保護裝置避免不受信任網站的威脅 <!-- 958257 -->   
系統管理員可以使用 Windows 資訊保護工作流程，或裝置設定下方的全新「網路界限」設定檔，將網站定義為「受信任」網站或「公司」網站。 如果使用 Microsoft Edge 進行檢視，則會開啟任何未列在 64 位元 Windows 10 裝置受信任網路界限上的網站，而不是在 Hyper-V 虛擬電腦的瀏覽器中開啟。

您可以在 "Endpoint Protection" 設定檔的裝置組態設定檔中，找到應用程式防護。 系統管理員可以從該處設定虛擬瀏覽器和主機電腦之間的互動、不受信任的網站和信任網站之間的互動，並儲存虛擬瀏覽器中產生的資料。 若要在裝置上使用應用程式防護，您必須先設定網路界限。 每部裝置都只能定義一個網路界限。  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise 的 Windows Defender 應用程式控制具有僅信任已獲授權應用程式的模式 <!-- 1031096 -->    
每天有高達數千種的惡意檔案流竄出來，單純使用防毒特徵偵測來對抗惡意程式碼時，可能再也無法有效抵禦新的攻擊。 使用 Windows 10 Enterprise 的 Windows Defender 應用程式控制時，您可以將裝置設定的模式，從信任防毒軟體或其他安全性解決方案未封鎖的應用程式，變更為讓作業系統僅信任獲得企業授權的應用程式。 您可以將 Windows Defender 應用程式控制中的應用程式指派為信任。

使用 Intune 時，您可以在「僅限稽核」模式或「強制執行」模式中設定應用程式控制原則。 在「僅限稽核」模式中執行時，不會封鎖應用程式。 「僅限稽核」模式會在本機用戶端記錄檔中記錄所有事件。 您也可以設定是否只允許執行 Windows 元件和 Microsoft Store 應用程式，或允許依據智慧型安全性圖表的定義，執行評價良好的其他應用程式。

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender 惡意探索防護是 Windows 10 的全新入侵偵測功能 <!-- 1063615 -->   
Window Defender 惡意探索防護包含自訂規則，可降低擅用應用程式的可能性、避免巨集和指令碼的威脅、自動封鎖評價不良的 IP 位址網路連線，並協助資料抵禦勒索軟體和未知的威脅。 Window Defender 惡意探索防護是由下列元件所組成：

- **降低攻擊介面 (ASR)** 提供的規則可讓您避免巨集、指令碼和電子郵件的威脅。
- **控制存取資料夾**會自動封鎖對受保護資料夾內容的存取。
- **網路篩選**會封鎖任何應用程式與評價不良 IP/網域的輸出連線。
- **惡意探索保護**可提供記憶體限制、控制流程限制和原則限制，以用來保護應用程式不受惡意探索的威脅。

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼<!-- 790537 -->

Intune 管理延伸模組可讓您在 Intune 中上傳 PowerShell 指令碼，以便在 Windows 10 裝置上執行。 延伸模組可補充 Windows 10 的行動裝置管理 (MDM) 功能，讓您更輕鬆地轉移至新式管理。 如需詳細資料，請參閱[在 Intune 中管理適用於 Windows 10 裝置的 PowerShell 指令碼](intune-management-extension.md)。

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10 的新裝置限制設定      <!-- 1308850 -->
-    傳訊 (僅限行動裝置) - 停用測試或 MMS 訊息
-    密碼 - 可啟用 FIPS 和使用 Windows Hello 次要裝置以進行驗證的設定 
-    顯示 - 可開啟或關閉舊版應用程式 GDI 縮放比例的設定

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 Kiosk 模式的裝置限制 <!-- 1308872 -->   
您可以將 Windows 10 裝置使用者限制在 kiosk 模式中，使其僅可使用一組預先定義的應用程式。  若要這樣做，請建立 Windows 10 裝置限制設定檔，然後進行 Kiosk 設定。

Kiosk 模式支援兩種模式：**單一應用程式** (只允許使用者執行一個應用程式) 或**多重應用程式** (允許存取一組應用程式)。  您可定義使用者帳戶和裝置名稱，以決定支援的應用程式。  當使用者登入時，就只能使用定義的應用程式。  若要進一步了解，請參閱 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)。 

Kiosk 模式具有下列要求：

- Intune 必須為 MDM 授權單位。
- 目標裝置上必須已安裝應用程式。
- 裝置必須[已正確佈建](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)。

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>可建立網路界限的新裝置組態設定檔 <!-- 1311967 -->   
稱為**網路界限**的新裝置組態設定檔可以與其他裝置組態設定檔一起找到。 您可以使用這個設定檔，將線上資源定義為公司資源和受信任的資源。 您必須先定義裝置的網路界限之後，裝置才可以使用 Windows Defender 應用程式防護和 Windows 資訊保護等功能。 每部裝置都只能定義一個網路界限。

您可以定義要信任的企業雲端資源、IP 位址範圍和內部 Proxy 伺服器。 定義好之後，Windows Defender 應用程式防護和 Windows 資訊保護等其他功能才可以使用網路界限。

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender 防毒軟體的兩個其他設定 <!-- 1338409 -->  
**檔案封鎖層級**

| | |
|---|---|
| 未設定 | [尚未設定] 會使用預設的 Windows Defender 防毒軟體封鎖層級，並提供強式偵測，而不會增加偵測合法檔案的風險。 |
| 高 | [高] 適用於強力偵測層級。
| 高 +  | [高 +] 可提供 [高] 層級與額外的保護措施，但可能會影響用戶端效能。
| 零容錯  | [零容錯] 會封鎖所有未知的可執行檔。 |

雖然可能性很低，但設定為 [高] 有可能會導致部分合法檔案受到偵測。
建議您將檔案封鎖層級設為預設值 [尚未設定]。

**延長掃描檔案的逾時 (依雲端)**  

| | |
|--|--|
| 秒數 (0-50) | 指定 Windows Defender 防毒軟體在封鎖檔案前應等候雲端結果的時間上限。 預設時間量為 10 秒：此處所指定的任何額外時間 (最多 50 秒) 均會加上預設的 10 秒。 在大部分情況下，掃描需要的時間遠比最大值少很多。 延長的時間可讓雲端徹底調查可疑的檔案。 建議您啟用此設定，並至少多指定 20 秒。 |

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>為 Windows 10 裝置新增 Citrix VPN <!-- 1512457 -->  
您可為其所擁有的 Windows 10 裝置設定 Citrix VPN。 設定 Windows 10 和更新版本的 VPN 時，您可以在 [基本 VPN] 刀鋒視窗的 [選取連線類型] 清單中，選擇 Citrix VPN。

> [!Note]
> iOS 和 Android 中已有 Citrix 設定。

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>iOS 上的 Wi-Fi 連線支援預先共用金鑰<!-- 1550823 -->
客戶可在 iOS 裝置上設定 Wi-Fi 設定檔，以使用預先共用金鑰 (PSK) 進行 WPA/WPA2 個人連線。 當裝置註冊到 Intune 時，會將這些設定檔推送到使用者的裝置。

將設定檔推送到裝置後，下一個步驟則取決於設定檔設定。  若設定為自動連線，就會在下次需要網路時這麼做。  若設定為手動連線，使用者就必須手動啟用連線。  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>存取 iOS 的受管理應用程式記錄檔<!-- 1469920 -->
安裝 Managed Browser 的使用者現在可以檢視所有 Microsoft 所發行應用程式的管理狀態，並傳送記錄檔來針對受管理的 iOS 應用程式進行疑難排解。

了解如何在 iOS 裝置上啟用受管理瀏覽器的疑難排解模式，請參閱[如何在 iOS 上使用受管理的瀏覽器存取受管理的應用程式記錄檔](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)。

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>iOS 版公司入口網站 2.9.0 版中裝置設定工作流程的改善 <!-- 1417174 -->

已改善 iOS 版公司入口網站應用程式中的裝置設定工作流程。 語言對使用者來說更簡單明瞭，而且我們已盡量將可以合併的畫面合併。 透過在整個設定文字中使用您的公司名稱，讓語言更特定於您的公司。 您可以在  [[應用程式 UI 中的新增功能]](whats-new-app-ui.md) 頁面中看到這個更新的工作流程。


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>使用者實體包含資料倉儲資料模型中的最新使用者資料<!-- 1544273 -->
Intune 資料倉儲資料模型的第一個版本只包含最新的歷程 Intune 資料。 報表製作者無法擷取使用者的目前狀態。 在這項更新中，**使用者實體**會填入最新的使用者資料。


## <a name="october-2017"></a>2017 年 10 月

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>顯示 iOS 和 Android 的企業營運應用程式版本號碼<!-- 1380712 -->

Intune 的應用程式現在會顯示 iOS 和 Android 的企業營運應用程式版本號碼。 此號碼會顯示在 Azure 入口網站的應用程式清單及 [應用程式概觀] 刀鋒視窗中。 使用者可以在公司入口網站應用程式及入口網站中看到應用程式號碼。

__完整版本號碼__ 完整的版本號碼可識別特定的應用程式版本。 此號碼會顯示為_版本_(_組建_)。 例如，2.2(2.2.17560800)

完整的版本號碼有兩個部分：

 - **版本**  
   版本號碼是人類可讀的應用程式版本號碼。 可供使用者識別不同的應用程式版本。

 - **組建編號**  
    組建編號是內部編號，用於偵測應用程式與以程式設計方式管理應用程式。 組建編號是指參考程式碼變更的應用程式反覆項目。

深入了解版本號碼及開發企業營運應用程式，請參閱[開始使用 Microsoft Intune App SDK](app-sdk-get-started.md#line-of-business-app-version-numbers)。

### <a name="device-and-app-management-integration----677972---"></a>裝置與應用程式管理整合 <!-- 677972 -->   
Intune 早已開始整合應用程式和裝置管理的 IT 系統管理員體驗；現在，Intune 的行動裝置管理 (MDM) 與行動應用程式管理 (MAM) 都可從 Azure 入口網站存取。 這些變更都是為了簡化您的裝置和應用程式管理體驗。

如需深入了解已宣布的 MDM 和 MAM 變更，請參閱 [Intune 支援小組部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)。

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple 裝置的新註冊警示 <!-- 1471790 -->
註冊的 [概觀] 頁面會顯示對 IT 管理員極有幫助，有關 Apple 裝置管理的警示。 在下列情況中 [概觀] 頁面會顯示警示：Apple MDM Push Certificate 即將到期或已過期時、裝置註冊計劃權杖即將到期或已過期時、裝置註冊計劃中有未指派的裝置時。

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>支援在不註冊裝置的情況下替換應用程式設定 <!-- 1080364 -->

您可以在未註冊裝置的應用程式中，使用應用程式設定的動態值權杖。 如需詳細資訊，請參閱[在不註冊裝置的情況下新增受管理應用程式的應用程式設定原則](app-configuration-policies-managed-app.md)。

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10 版公司入口網站應用程式的更新 <!--1299474-->
Windows 10 版「公司入口網站」應用程式中的 [設定] 頁面已更新，以使設定和預期的使用者動作在所有設定中更加一致。 它也已更新為符合其他 Windows 應用程式的配置。 您可以在 [應用程式 UI 中的新增功能](whats-new-app-ui.md) 頁面中找到之前/之後影像。

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>通知終端使用者可看到哪些 Windows 10 裝置資訊 <!--1337920-->
我們已將 [擁有權類型] 新增至 Windows 10 版公司入口網站應用程式的 [裝置詳細資料] 畫面。 這樣可讓使用者直接從此頁面從 Intune 終端使用者文件尋找有關隱私權的詳細資訊。使用者也可以在 [關於] 畫面上找到此資訊。

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Android 版公司入口網站應用程式的意見反應提示 <!--1165249-->
Android 版公司入口網站應用程式現在會要求終端使用者提供意見反應。 此意見反應會直接傳給至 Microsoft，並讓使用者得以在公開的 Google Play 商店上評論應用程式。 意見反應並非必要，使用者可以輕易地將之關閉，以繼續使用應用程式。

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>協助您的使用者自助使用適用於 Android 的公司入口網站應用程式 <!-- 1573324, 1573150, 1558616, 1564878 -->

Android 版公司入口網站應用程式新增了終端使用者指示，能幫助他們了解，並盡可能自行解決新的使用案例。
- 如果使用者已達可新增裝置的數目上限，系統會引導他們前往 [Azure Active Directory 網站](https://account.activedirectory.windowsazure.com/r/#/profile)移除裝置。
- 有提供步驟協助終端使用者[修正 Samsung Knox 裝置的啟動錯誤](https://go.microsoft.com/fwlink/?linkid=859718)或[關閉省電模式](/intune-user-help/power-saving-mode-android)。 如果這些解決方案都無法解決他們的問題，我們會提供[向 Microsoft 提交記錄檔](/intune-user-help/send-logs-to-microsoft-android)的說明。

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android 裝置的新「解決」動作 <!-- 1583480 -->

Android 公司入口網站應用程式在 [更新裝置設定] 頁面中推出「解決」動作。 選取此選項會將終端使用者直接帶到造成裝置不符合規範的設定。 Android 版公司入口網站應用程式目前在[裝置密碼](/intune-user-help/set-your-pin-or-password-android)、[USB 偵錯](/intune-user-help/you-need-to-turn-off-usb-debugging-android)和[未知來源](/intune-user-help/you-need-to-turn-off-unknown-sources-android)設定支援此動作。

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Android 版公司入口網站中的裝置設定進度列指示器 <!-- 1565657 -->
Android 版公司入口網站應用程式會顯示使用者註冊其裝置時的裝置設定進度列指示器。 指示器會顯示新的狀態，從開始到結束依序為「正在設定您的裝置...」、「正在註冊您的裝置...」、「即將完成註冊您的裝置...」及「即將完成設定您的裝置...」。

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>支援 iOS 版公司入口網站的憑證式驗證 <!--1029830-->
我們已新增支援 iOS 版公司入口網站應用程式的憑證式驗證 (CBA)。 使用 CBA 的使用者可輸入其使用者名稱，然後點選 [Sign in with a certificate] (使用憑證登入) 連結。 Android 版和 Windows 版公司入口網站應用程式皆已經支援 CBA。 您可以在[登入公司入口網站應用程式](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal)頁面上深入了解。

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>需要或無須註冊而提供的應用程式現在可以直接安裝，而不會提示註冊。 <!-- 1334712 -->

在 Android 公司入口網站應用程式上需要或無需註冊才可使用的公司應用程式，現在皆已可安裝而不會提示需要註冊。

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617---"></a>Microsoft Intune 中的 Windows AutoPilot 部署方案支援  <!-- 747617  -->
您可以現在使用 Microsoft Intune Windows AutoPilot 部署計劃，讓您的使用者能夠佈建其公司裝置而不需要 IT 介入。 您可以自訂全新體驗 (OOBE)，並引導使用者將他們的裝置加入 Azure AD 且在 Intune 中註冊。 搭配使用時，Microsoft Intune 和 Windows AutoPilot 不須部署、維護及管理作業系統映像。 如需詳細資料，請參閱 [Enroll Windows devices using Windows AutoPilot Deployment Program](https://docs.microsoft.com/intune/enrollment-autopilot) (使用 Windows AutoPilot Deployment 方案註冊 Windows 裝置)。

### <a name="quick-start-for-device-enrollment----1425655---"></a>裝置註冊的快速入門  <!-- 1425655 --> 
快速入門現在提供於 [裝置註冊]，並提供管理平台和設定註冊程序的參考表格。 每個項目的簡短描述，以及文件連結和逐步指示，提供實用的文件來簡化開始使用。

### <a name="device-categorization----1427491---"></a>裝置分類 <!-- 1427491 -->
[裝置] > [概觀] 刀鋒視窗的註冊裝置平台圖，會依平台組織裝置，包括 Android、iOS、macOS、Windows 和 Windows Mobile。  執行其他作業系統的裝置會分組為「其他」。  這包括由 Blackberry、NOKIA 和其他廠商製造的裝置。  

若要了解您租用戶中的哪些裝置受到影響，請選擇 [管理] > [所有裝置]，然後使用 [篩選] 限制 [OS] 欄位。

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium - 新的 Mobile Threat Defense 夥伴   <!-- 954681 -->  
您可以根據由 Zimperium (與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評定，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作
風險評估的依據是收集自執行 Zimperium 裝置的遙測。 您可以根據透過 Intune 裝置合規性政策啟用的 Zimperium 風險評估，設定 EMS 條件式存取原則。透過該原則，您可以根據偵測到的威脅來允許或封鎖不符合規範的裝置存取公司資源。

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978575, 1308849, -->  
我們將為 Windows Defender SmartScreen 類別中的 Windows 10 裝置限制設定檔新增設定。

如需 Windows 10 裝置限制設定檔的詳細資料，請參閱 [Windows 10 及更新版本的裝置限制設定]( device-restrictions-windows-10.md)。

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>適合 Windows 和 Windows Mobile 裝置的遠端支援  <!-- 1070473 -->  
Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (需另行購買)，讓您為執行 Windows 和 Windows Mobile 裝置的使用者提供遠端協助。

### <a name="scan-devices-with-windows-defender----1280988-1280990---"></a>使用 Windows Defender 掃描裝置 <!-- 1280988  1280990   -->
您現在可以在受管理的 Windows 10 裝置上，使用 Windows Defender 防毒軟體來執行**快速掃描**、**完整掃描**，和**更新簽章**。 從裝置的概觀刀鋒視窗，選擇要在裝置上執行的動作。 系統會提示您確認動作，然後命令才會傳送到裝置。 

**快速掃描**：快速掃描會掃描惡意程式碼註冊要啟動的位置，例如登錄機碼和已知的 Windows 啟動資料夾。 快速掃描平均會花費五分鐘。 快速掃描與 [隨時開啟即時保護] 設定 (可在檔案開啟、關閉，以及使用者每次瀏覽資料夾時掃描檔案) 結合時，可提供保護以防禦潛藏於系統或核心的惡意程式碼。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**完整掃描**：完整掃描對於已遭遇惡意程式碼威脅的裝置非常實用，可找出是否有任何需要進一步完整清理的尚未作用元件，且適合執行隨選掃描。 完整掃描可能需要一個小時來進行。 掃描完成時，使用者可在其裝置上查看掃描結果。 

**更新簽章**：更新簽章命令會更新 Windows Defender 防毒軟體的惡意程式碼定義和簽章。 這有助於確保 Windows Defender 防毒軟體能有效偵測惡意程式碼。 這項功能僅適用於 Windows 10 裝置，且需要裝置的網際網路連線。 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>[啟用/停用] 按鈕從 Intune Azure 入口網站的 [Intune 憑證授權單位] 頁面移除  <!-- 1400455 -->
 我們正在消除設定 Intune 上憑證連接器的多餘步驟。 目前，您會下載憑證連接器，然後在 Intune 主控台中啟用它。 不過，如果您在 Intune 主控台中停用連接器，連接器會繼續發出憑證。

#### <a name="how-does-this-affect-me"></a>此變更會對我造成什麼影響？
從 10 月開始，[啟用/停用] 按鈕不會再出現在 Azure 入口網站的 [憑證授權單位] 頁面上。 連接器功能將保持不變。 憑證仍會部署到在 Intune 中註冊的裝置。 您可以繼續下載並安裝憑證連接器。 若要停止發出憑證，您現在要解除安裝憑證連接器而非將它停用。

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>我需要為這項變更做什麼準備？
如果您目前已停用憑證連接器，您應該將它解除安裝。

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>適用於 Windows 10 團隊版裝置限制設定檔的新設定 <!--- 1308838 -->
在此版本中，我們新增了許多設定到 Windows 10 團隊版裝置限制設定檔，以協助您控制 Surface Hub 裝置。

如需此設定檔的詳細資訊，請參閱 [Windows 10 團隊版裝置限制設定](device-restrictions-windows-10-teams.md)。

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>防止 Android 裝置的使用者變更其裝置的日期和時間  <!-- 1333292 -->
您可以使用 [Android 自訂裝置原則](custom-settings-android.md)來防止 Android 裝置使用者變更裝置的日期和時間。

若要這樣做，請設定 Android 自訂原則，將 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange 設定為 **TRUE**，然後指派給所需的群組。

### <a name="bitlocker-device-configuration---1397398---"></a>BitLocker 裝置設定 <!-- 1397398 -->
[Windows 加密] > [基本設定] 包含新的 [其他磁碟加密的警告] 設定，讓您停用使用者裝置上可能正在使用的其他磁碟加密[警告提示](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)。  警告提示會要求使用者同意，然後才會在裝置上設定 BitLocker，在使用者確認之前則會封鎖 BitLocker 設定。  新的設定會停用使用者警告。


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>企業大量採購方案應用程式現在將會同步到 Intune 租用戶 <!-- 800882 -->  
協力廠商開發人員可以私下將應用程式散發給 iTunes Connect 中所指定的授權企業大量採購方案 (VPP) 成員。 這些企業 VPP 成員可以登入大量採購方案 App Store，並購買其應用程式。

在此版本中，終端使用者所購買的企業 VPP 應用程式將開始與其 Intune 租用戶同步。

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>選取 Apple 國家/地區市集以同步處理 VPP 應用程式 <!-- 1332311 -->  
上傳您的大量採購方案 (VPP) 權杖時，可以設定 VPP 的國家/地區市集。 Intune 會從指定的 VPP 國家/地區市集同步處理所有地區設定的 VPP 應用程式。

> [!NOTE]  
> 目前 Intune 只會從符合 Intune 地區設定 (建立 Intune 租用戶所在位置) 的 VPP 國家/地區市集同步處理 VPP 應用程式。


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>封鎖 Android for Work 中工作和個人設定檔間的複製和貼上 <!-- 1098994 -->
在此版本中，您可以將 Android for Work 的工作設定檔設定為封鎖工作和個人應用程式間的複製和貼上。 您可以在 [工作設定檔設定] 中，於 [Android for Work] 平台的 [裝置限制] 設定檔內找到這項新設定。

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>建立僅限於特定地區 Apple App Store 的 iOS 應用程式 <!-- 1281692 -->
您可以在 Apple App Store 受管理的應用程式建立期間，指定國家/地區的地區設定。

> [!Note]  
> 目前，您僅能建立出現在美國市集的 Apple App Store 受管理應用程式。

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>更新 iOS VPP 使用者和裝置授權的應用程式 <!-- 1305564 -->  
您可以透過 Intune 服務，設定 iOS VPP 權杖以更新為該權杖所購買的全部應用程式。 Intune 會偵測應用程式市集內的 VPP 應用程式更新，並在裝置簽入時將更新自動推送至裝置。

如需設定 VPP 權杖並啟用自動更新的步驟，請參閱 [如何使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式] (/intune/vpp-apps-ios)。


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>使用者裝置關聯實體集合已新增至 Intune 資料倉儲資料模型 <!-- 1187917 -->
您現在可以使用使用者裝置關聯資訊 (關聯使用者和裝置實體集合) 來建立報表和資料視覺效果。 資料模型的存取可透過擷取自資料倉儲 Intune 頁面的 Power BI 檔案 (PBIX)、透過 OData 端點，或開發自訂用戶端來存取。

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>檢閱 Windows 10 更新通道的原則合規性 <!-- 1067886 -->
您可以從 [軟體更新] > [依更新通道別部署狀態] 來檢閱 Windows 10 更新通道的原則報告。 原則報告包括已設定更新通道的部署狀態。 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions----1352223---"></a>新報表列出包括舊版 iOS 的 iOS 裝置   <!-- 1352223 -->
[軟體更新] 工作區提供 [過期的 iOS 裝置] 報表。 在此報表中，您可以檢視受監督的 iOS 裝置清單，這些是 iOS 更新原則之前鎖定並有可用更新的裝置。 針對每部裝置，您可以檢視狀態，以了解為何尚未自動更新裝置。 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>檢視應用程式保護原則指派以進行疑難排解 <!--  1475003 -->
在此即將發行的版本中，將會新增 [應用程式保護原則] 選項到疑難排解刀鋒視窗中提供的 [指派] 下拉式清單。 您現在可以選取應用程式保護原則，以查看指派給所選取使用者的應用程式保護原則。



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>對公司入口網站之裝置安裝工作流程的改善 <!--1490692-->
我們已改善 Android 版公司入口網站應用程式中的裝置安裝工作流程。 我們採用您公司專屬的語言、對使用者來說更簡單明瞭，並盡量將可以合併的畫面合併。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md#week-of-october-2-2017)頁面中，查看這些變更。

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>改善在 Android 裝置上要求存取連絡人的相關指引 <!--1484985-->

Android 版公司入口網站應用程式通常會要求使用者接受「連絡人」權限。 如果使用者拒絕此存取權，系統現會顯示應用程式內通知，提醒他們授與此權限以進行條件式存取。 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Android 的安全啟動修復 <!--1490712-->

如果使用者是使用 Android 裝置，可以點選公司入口網站應用程式中的不相容原因。 在可能的情況下，這將會將他們帶到 [設定] 應用程式中的正確位置以修正該問題。 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>在 Android Oreo 的公司入口網站應用程式上新增終端使用者的推播通知 <!--1475932-->

終端使用者將會看到其他通知，這些通知會指出 Android Oreo 版公司入口網站應用程式正在執行背景工作，例如從 Intune 服務擷取原則。 這樣可讓終端使用者清楚了解公司入口網站在其裝置上執行的系統管理工作。 這是適用於 Android Oreo 版公司入口網站應用程式之整體[公司入口網站 UI 最佳化](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)的一部分。 

在 Android Oreo 中啟用的新 UI 項目已進一步最佳化。  終端使用者會看到額外的通知，顯示出公司入口網站執行背景工作 (例如從 Intune 服務擷取原則) 的時間。  這可讓使用者清楚知道公司入口網站在裝置上執行管理工作的時間。

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>Android 公司入口網站應用程式使用工作設定檔的新行為 <!-- 1485783 -->

當您使用工作設定檔註冊 Android for Work 裝置時，是由工作設定檔中的公司入口網站應用程式來執行裝置上的管理工作。 

除非您使用的是個人設定檔中已啟用 MAM 的應用程式，否則 Android 版公司入口網站將不再提供任何用途。 為了改善工作設定檔體驗，Intune 將會在順利註冊工作設定檔之後，自動隱藏個人的公司入口網站應用程式。

您可以隨時在個人設定檔中啟用 Android 版公司入口網站應用程式，方法是瀏覽至 [Play 商店中的「公司入口網站」](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)，然後點選 [啟用]。

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 和 Windows Phone 8.1 版公司入口網站移至維持模式 <!--1428681-->

自 2017 年 10 月起，Windows 8.1 和 Windows Phone 8.1 公司入口網站應用程式將會移至維持模式。 這表示這些平台的應用程式與現有的案例 (例如註冊和合規性) 將會繼續被支援。 這些應用程式將可透過現有的發行管道 (例如 Microsoft Store) 繼續進行下載。 

一旦進入維持模式，這些應用程式就僅會接收重大安全性更新。 未來將不會針對這些應用程式發行其他的更新或功能。 如需新功能，建議您將裝置更新為 Windows 10 或 Windows 10 行動裝置版。 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>封鎖不支援的 Samsung Knox 裝置註冊  <!-- 1490695 -->

公司入口網站應用程式只會嘗試註冊支援的 Samsung KNOX 裝置。 為了避免 Knox 啟用錯誤而導致 MDM 註冊失敗，如果裝置出現在 [Samsung 發佈的裝置清單](https://www.samsungknox.com/knox-supported-devices/knox-workspace)中，則系統只會嘗試進行裝置註冊。 有些 Samsung 裝置型號可能支援 Knox，而有些不支援。 在您購買並部署之前，請先向裝置經銷商確認 KNOX 相容性。 您可以在 [Android 和 Samsung Knox Standard 原則設定](supported-devices-browsers.md#intune-supported-web-browsers)中找到已驗證裝置的完整清單。

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>結束對 Android 4.3 和較舊版本的支援<!-- 1171126, 1326920 -->
受管理的應用程式與 Android 版公司入口網站應用程式將需要 Android 4.4 或更新的版本，才能存取公司資源。 今年 12 月會強制淘汰所有已註冊的裝置，以致無法存取公司資源。 如果您未經由 MDM 來使用應用程式保護原則，應用程式將不再接收更新，應用程式的體驗品質也會隨著時間而下降。

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>通知使用者可在已註冊裝置上看到哪些裝置資訊 <!--1165314-->
針對所有公司入口網站應用程式的 [裝置詳細資料] 畫面，我們會新增 [擁有權類型]。 這樣可讓使用者直接從[我的公司可以看到哪些資訊？](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)文章深入了解隱私權的詳細資訊。 在不久的將來，這項功能就會推出到所有公司入口網站應用程式。 我們已在 [9 月](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)針對 iOS 宣佈此功能。

## <a name="september-2017"></a>2017 年 9 月

### <a name="intune-supports-ios-11---1428975--"></a>Intune 支援 iOS 11 <!--1428975-->
Intune 支援 iOS 11。 這項資訊之前已在 [Intune 支援部落格](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)宣布過。

### <a name="end-of-support-for-ios-80----1164477---"></a>結束對 iOS 8.0 的支援<!-- 1164477 -->
受管理的應用程式和 iOS 公司入口網站應用程式需要 iOS 9.0 及更新版本才能存取公司資源。 今年 9 月前未更新的裝置將不再能存取公司入口網站或這些應用程式。 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>重新整理動作已新增至 Windows 10 的公司入口網站應用程式 <!--1132468-->
Windows 10 公司入口網站應用程式可讓使用者提取以重新整理，或按桌上型電腦的 F5，重新整理應用程式中的資料。

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>通知終端使用者可看到哪些 iOS 裝置資訊 <!--739894-->

我們在 iOS 的公司入口網站應用程式 [裝置詳細資料] 畫面新增了 [擁有權類型]。 這樣可讓使用者直接從此頁面從 Intune 終端使用者文件尋找有關隱私權的詳細資訊。他們也可以在 [關於] 畫面上找到此資訊。

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>允許使用者存取適用於 Android 的公司入口網站應用程式，不需要註冊。<!---1169910--->

使用者很快地不必註冊裝置也能存取 Android 的公司入口網站。 使用應用程式保護原則的組織使用者，在開啟公司入口網站應用程式時，將不會再收到註冊裝置的提示。 使用者也可以從公司入口網站安裝應用程式，不用註冊裝置。 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android 公司入口網站應用程式中更易了解的措辭 <!---1396349--->  

Android 版公司入口網站應用程式的註冊程序已經使用新的文字來簡化，讓使用者可更輕鬆地進行註冊。 如果您有自訂註冊文件，建議您予以更新，以反映新的畫面。 您可以在我們的 [Intune 終端使用者應用程式 UI 更新](whats-new-app-ui.md#week-of-september-11-2017)頁面找到範例影像。

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows 10 公司入口網站應用程式已新增到 Windows 資訊保護允許原則 <!-- 677129 -->

Windows 10 公司入口網站應用程式已更新，現在支援 Windows 資訊保護 (WIP)。 此應用程式可以加入到 WIP 允許原則。 有了此變更，您再也不需要將應用程式加入到[豁免] 清單。


## <a name="august-2017"></a>2017 年 8 月

### <a name="improvements-to-device-overview----1404453---"></a>裝置概觀改善 <!-- 1404453 -->  
裝置概觀改善現在會顯示已註冊的裝置，但不包含 Exchange ActiveSync 所管理的裝置。 Exchange ActiveSync 裝置與已註冊裝置的管理選項不同。 若要在 Azure 入口網站中檢視 Intune 中的已註冊裝置數目以及依平台的已註冊裝置數目，請移至 [裝置] > [概觀]。

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune 所收集裝置清查的改善
<!-- 961134, 1104426, 1281327, 1333543 --> 在此版本中，我們已對您管理的裝置所收集的清查資訊進行下列改善：
 
-   對於 Android 裝置，您現在可以將資料行新增至裝置清查，以顯示每個裝置的最新修補程式等級。 將 [Security patch level] (安全性修補程式等級) 資料行新增至裝置清單，以查看這項資訊。
-   當您篩選裝置檢視時，現在可以依其註冊日期篩選裝置。 例如，您可以只顯示在所指定日期之後註冊的裝置。
-   我們已改善 [Last Check-in Date] (最後一次簽入日期) 項目所使用的篩選。
-   在裝置清單中，您現在可以顯示公司所擁有裝置的電話號碼。
此外，您還可以使用篩選窗格，依電話號碼來搜尋裝置。

如需裝置清查的詳細資料，請參閱[如何檢視 Intune 裝置清查](device-inventory.md)。

### <a name="conditional-access-support-for-macos-devices"></a>macOS 裝置的條件式存取支援 
<!-- 720172 --> 您現在可以設定條件式存取原則，要求 Mac 裝置向 Intune 註冊，並符合其裝置的合規性原則。 例如，使用者可以下載適用於 macOS 的 Intune 公司入口網站應用程式，並在 Intune 中註冊其 Mac 裝置。 Intune 會評估 Mac 裝置是否符合 PIN、加密、作業系統版本和系統完整性等需求。

- 深入了解 [macOS 裝置的條件式存取支援](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)。

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>對 macOS 來說，公司入口網站應用程式目前為公開預覽 <!---1484796--->
公開預覽中目前提供 macOS 的公司入口網站應用程式，以於 Enterprise Mobility + Security 中進行條件式存取。 此版本支援 macOS 10.11 及更新版本。 立即於 [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal) 取得。 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10 的新裝置限制設定    
<!--1063965, 1308850  --> 在此版本中，我們已在下列類別中新增 [Windows 10 裝置限制設定檔](/intune/device-restrictions-windows-10)的新設定：

-   Windows Defender SmartScreen
-   App Store

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>BitLocker 設定的 Windows 10 端點保護裝置設定檔更新
<!--1459533 -->     在此版本中，我們已對 BitLocker 設定在 Windows 10 端點保護裝置設定檔中的運作方式進行下列改善：
 
-   在 [BitLocker OS 磁碟機設定] 下，針對 [具有不相容 TPM 晶片的 BitLocker] 設定，當您選取 [封鎖] 時，以前這會導致實際允許 BitLocker。 我們現在已修正這個問題，以在選取 BitLocker 時進行封鎖。
-   在 [BitLocker OS 磁碟機設定] 下，針對 [以憑證為基礎的資料修復代理程式] 設定，您現在可以明確地封鎖以憑證為基礎的資料修復代理程式。 不過，預設會允許代理程式。
-   在 [BitLocker 固定式資料磁碟機設定] 下，針對 [資料修復代理程式] 設定，您現在可以明確地封鎖資料修復代理程式。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](endpoint-protection-windows-10.md)。


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 公司入口網站使用者和應用程式保護原則使用者的新登入體驗<!-- 621669 -->
使用者現在可以使用 Android 公司入口網站應用程式來瀏覽應用程式、管理裝置及檢視 IT 連絡人資訊，而無需註冊其 Android 裝置。 此外，如果使用者已使用受 Intune 應用程式防護原則保護的應用程式，並啟動 Android 公司入口網站，使用者不會再收到註冊裝置的提示。

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>Android 公司入口網站應用程式中用來切換電池最佳化的新設定 <!--1405990-->
適用於 Android 的公司入口網站應用程式中的 [設定] 頁面，具有新的設定，可讓使用者輕鬆關閉公司入口網站及 Microsoft Authenticator 應用程式的電池最佳化功能。 設定中所顯示的應用程式名稱，會依管理公司帳戶的應用程式而有所不同。 建議使用者關閉電池最佳化功能，以提升同步電子郵件與資料的公司應用程式效能。 

### <a name="multi-identity-support-for-onenote-for-ios----1234281---"></a>OneNote for iOS 的多重身分識別支援      <!-- 1234281 -->
終端使用者現在可以搭配使用不同的帳戶 (公司和個人) 與 Microsoft OneNote for iOS。 應用程式保護原則可以套用至工作筆記本中的公司資料，而不會影響其個人筆記本。 例如，原則可讓使用者在工作筆記本中尋找資訊，但會防止使用者將公司資料從工作筆記本複製並貼入個人筆記本。
 
- 深入了解支援 Intune 的[應用程式保護和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>在 Samsung Knox Standard 裝置上允許或封鎖應用程式的新設定
<!-- 1305423 822899-->  
在此版本中，我們新增新的[裝置限制設定](device-restrictions-android.md)，可讓您指定下列應用程式清單：
 
- 允許使用者安裝的應用程式
- 封鎖使用者執行的應用程式
- 對裝置使用者隱藏的應用程式  
您可依 URL、套件名稱，或從管理的應用程式清單中指定應用程式。

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>來自 Intune 的新 Azure AD 應用程式條件式存取原則 UI 連結
<!-- 1016201 --> IT 管理員現在可以透過 Azure AD 工作負載中的新條件式存取原則 UI，來設定應用程式條件式存取原則。 Azure 入口網站的 [Intune 應用程式防護] 區段中，應用程式條件式存取會暫時保留不動，且會強制並存。 Intune 工作負載中另有提供方便的連結，可連至新的條件式存取原則 UI。

- 深入了解 [Azure AD 上的應用程式條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)。



## <a name="july-2017"></a>2017 年 7 月

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256-1245463----"></a>依作業系統版本限制 Android 和 iOS 裝置註冊限制  <!--- 1333256,  1245463 --->
Intune 現在支援依作業系統版本號碼限制 iOS 和 Android 註冊。 在 [裝置類型限制] 下，IT 系統管理員現在可以進行平台設定，以便將註冊限制於作業系統值上下限之間。 Android 作業系統版本必須指定為 Major.Minor.Build.Rev，其中 Minor、Build 和 Rev 為選擇性。 iOS 版本必須指定為 Major.Minor.Build，其中 Minor 和 Build 為選擇性。 深入了解[裝置註冊限制](enrollment-restrictions-set.md)。

>[!NOTE]
>請勿將註冊限制為透過 Apple 註冊計劃或 Apple Configurator 進行。

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272-1333275-1245709---"></a>限制 Android、iOS 和 macOS 裝置以個人擁有的裝置註冊  <!--- 1333272,  1333275, 1245709 --->
Intune 可以透過將公司裝置 IMEI 編號列入允許清單，來限制個人裝置註冊。 Intune 現在已使用裝置序號，將這項功能擴充到 iOS、Android 和 macOS。 將序號上傳至 Intune，您就可以預先宣告此為公司擁有的裝置。 使用註冊限制，您可以封鎖個人擁有 (BYOD) 的裝置，僅註冊公司擁有的裝置。 深入了解[裝置註冊限制](enrollment-restrictions-set.md)。

若要匯入序號，請移至 [裝置註冊] > [公司裝置識別碼] 並按一下 [新增]，然後上傳 .CSV 檔案 (不含標頭的兩個序號和 IMEI 編號等詳細資料欄位)。 若要限制個人擁有的裝置，請移至 [裝置註冊]  >  [註冊限制]。 在 [裝置類型限制] 下選取 [預設]，然後選取 [平台設定]。 您可以 [允許] 或 [封鎖] 個人擁有的 iOS、Android 和 macOS 裝置。


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>新的裝置動作會強制裝置與 Intune 同步處理<!-- 711369 -->
在此版本中，我們已新增裝置動作，強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。
如需詳細資料，請參閱[同步處理裝置](device-sync.md)

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>強制受監督的 iOS 裝置自動安裝最新可用的軟體更新<!-- 777100 -->
新的原則可從 [軟體更新] 工作區取得，您可在此強制受監督的 iOS 裝置自動安裝最新可用的軟體更新。 如需詳細資料，請參閱[設定 iOS 更新原則](/intune/software-updates-ios)

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile - 新的 Mobile Threat Defense 夥伴  <!-- 954651, 1172027 -->
您可以根據由 Checkpoint SandBlast Mobile (一個與 Microsoft Intune 整合的 Mobile Threat Defense 解決方案) 所進行的風險評估，使用條件式存取來控制行動裝置對公司資源的存取。

#### <a name="how-integration-with-intune-works"></a>整合 Intune 如何運作？
風險乃依據收集自執行 Checkpoint SandBlast Mobile 裝置的遙測來進行評估。 您可以根據透過 Intune 裝置合規性政策所啟用的 Checkpoint SandBlast Mobile 風險評估，來設定 EMS 條件式存取原則。 您可以根據偵測到的威脅，允許或封鎖不相容的裝置存取公司資源。


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>將應用程式部署為商務用 Microsoft 網上商店中的可用項目 <!-- 748101 -->
系統管理員現在可以使用此版本將商務用 Microsoft 網上商店指派為可用。 設定為可用時，終端使用者就可以從公司入口網站應用程式或網站安裝應用程式，而不會被重新導向至 Microsoft 網上商店。

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>公司入口網站的 UI 更新 <!--1313244 part 1-->
我們對[公司入口網站](https://portal.manage.microsoft.com)的 UI 進行了數項更新，以增強終端使用者體驗。

- __應用程式磚的增強功能__：應用程式圖示現在會根據圖示的主要色彩 (如果可偵測)來顯示自動產生的背景。 適用時，此背景會取代先前在應用程式磚上顯示的灰色框線。

    公司入口網站會在未來版本中盡可能顯示大圖示。 建議 IT 系統管理員使用大小下限為 120 x120 像素的高解析度圖示來發佈應用程式。 

- __導覽變更__：導覽列項目移至左上方的漢堡功能表。 移除 [類別] 頁面。 使用者現在可以在瀏覽時依類別篩選內容。

- __精選 App 的更新__：我們已將專用頁面新增至網站 (使用者可在其中瀏覽您選為精選的應用程式)，並對首頁上的 [精選] 區段進行一些 UI 調校。

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>公司入口網站的 iBooks 支援 <!--1231841-->
我們已將專用頁面新增至公司入口網站，讓使用者可以瀏覽並下載 iBooks。 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>其他技術服務人員疑難排解詳細資料 <!---  Applies to 1263399, 1326964, 1341642 --->
Intune 已更新疑難排解顯示，並新增至針對系統管理員和技術服務人員所提供的資訊。 您現在可以看到 [指派] 表格，其中根據群組成員資格來摘要說明所有使用者指派。 此清單包括：
- 行動應用程式
- 相容性原則
- 組態設定檔

此外，[裝置] 資料表現在會包含 [Azure AD 聯結類型] 和 [符合 Azure AD 規範] 資料行。 如需詳細資訊，請參閱[協助使用者針對問題進行疑難排解](help-desk-operators.md)。



### <a name="intune-data-warehouse-public-preview"></a>Intune 資料倉儲 (公開預覽)
Intune 資料倉儲會每日對資料進行抽樣，以提供您租用戶的歷程檢視。 您可以藉由使用 Power BI 檔案 (PBIX)、與許多分析工具相容的 OData 連結，或與 REST API 互動，來存取資料。 如需詳細資訊，請參閱[使用 Intune 資料倉儲](reports-nav-create-intune-reports.md)。


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10 的公司入口網站應用程式提供日間和夜間模式<!---676547--->
使用者可以自訂 Windows 10 公司入口網站應用程式的色彩模式。 使用者可在公司入口網站應用程式的 [設定] 區段中進行變更。 使用者重新啟動應用程式後，即會看到變更。 至於 Windows 10 版本 1607 及更新版本，應用程式模式會預設為系統設定。 至於 Windows 10 版本 1511 及更新版本，應用程式模式會預設為日間模式。

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>讓使用者在 Windows 10 的公司入口網站應用程式中標記其裝置群組<!---807046-->
終端使用者現在可以直接在 Windows 10 公司入口網站應用程式中標記群組，選取其裝置所屬群組。



## <a name="june-2017"></a>2017 年 6 月

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>適用於 Intune 管理員的全新且以角色為基礎的系統管理存取權 <!-- 1099990 -->  
新增條件式存取管理員角色，來檢視、建立、修改及刪除 Azure AD 條件式存取原則。 先前只有全域管理員和安全性管理員具有此權限。 您可以為 Intune 管理員授與此角色權限，讓他們具有條件式存取原則的存取權。


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>使用序號標記屬公司擁有的裝置 <!-- 1215070 -->  
Intune 現在支援上傳 iOS、macOS 和 Android 序號以作為公司裝置識別碼。 您無法使用序號來封鎖個人裝置進行註冊，因為在註冊期間不會驗證序號。 依序號封鎖個人裝置，將在不久的未來推出。


### <a name="new-remote-actions-for-ios-devices----854689---"></a>適用於 iOS 裝置的新遠端動作<!-- 854689 -->
在此版本中，我們為用於管理 Apple Classroom 的共用 iPad 裝置新增了兩個遠端裝置動作：

-   [登出目前的使用者](device-logout-user.md) - 會登出您所選擇之 iOS 裝置的目前使用者。
-   [移除使用者](device-remove-user.md) - 會從 iOS 裝置的本機快取中刪除您選擇的使用者。


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>使用 iOS Classroom 應用程式支援共用的 iPad <!-- 1044681 -->
在此版本中，我們擴充了對管理 iOS Classroom 應用程式的支援，以包含使用受管理 Apple ID 登入共用 iPad 的學生。


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune 內建應用程式的變更 <!-- 1332306 -->
原本，Intune 包含許多您可以快速指派的內建應用程式。 應客戶的意見反應，我們已移除此清單，而您不會再看到內建應用程式。
不過，您已指派的任何內建應用程式仍會顯示在應用程式清單中。 若有需要，您可以繼續指派這些應用程式。
在之後的版本中，我們計劃新增一個方法，讓從 Azure 入口網站選取及指派內建應用程式的流程變得更輕鬆。

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>安裝 Office 365 應用程式更輕鬆<!--- 1121362 --->
新的 **Office 365 ProPlus** 應用程式類型可讓您輕鬆地將 Office 365 ProPlus 2016 應用程式指派給您管理的執行最新版 Windows 10 的裝置。 此外，如果您有 Microsoft Project 或 Microsoft Visio 的授權，也可以安裝它們。 您想要的應用程式會配套在一起，並以單一應用程式的形式出現在 Intune 主控台的應用程式清單中。
如需詳細資訊，請參閱[如何新增適用於 Windows 10 的 Office 365 應用程式](apps-add-office365.md)。


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>支援來自商務用 Microsoft 網上商店的離線應用程式 <!--- 777044 --->
您購買自商務用 Microsoft 網上商店的離線應用程式現在將能同步處理至 Azure 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 離線應用程式會透過 Intune 安裝，而不透過市集。

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>Microsoft 小組現在是以應用程式為基礎的已核准應用程式 CA 清單的一部分<!-- 1257019 -->
適用於 iOS 和 Android 的 Microsoft Teams 應用程式，現在是針對適用於 Exchange 和 SharePoint Online 之以應用程式為基礎的條件式存取原則核准的應用程式一部分。 可以透過 Azure 入口網站中的 [Intune 應用程式防護] 刀鋒視窗，使用以應用程式為基礎的條件式存取，將應用程式設定為所有租用戶。

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>受管理的瀏覽器和應用程式 Proxy 整合<!-- 1287310 -->
Intune Managed Browser 現在可以整合 Azure AD Application Proxy 服務，讓使用者即使在遠端工作時也能存取內部網路網站。 瀏覽器使用者可以和平常一樣地輸入網站的 URL，Managed Browser 便會透過應用程式 Proxy Web 閘道路由傳送要求。 如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>適用於 Intune Managed Browser 的新應用程式組態設定 <!-- 682951 -->
在此版本中，我們已新增 iOS 和 Android 的 Intune Managed Browser 應用程式的進一步設定。 您現在能使用應用程式設定原則，針對瀏覽器設定預設的首頁和書籤。
如需詳細資訊，請參閱[使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10 的 BitLocker 設定 <!-- 951707 -->
您現在可以使用新的 Intune 裝置設定檔，設定 Windows 10 裝置的 BitLocker 設定。 例如，您可以要求裝置加密，也可以設定在開啟 BitLocker 時套用的進一步設定。
如需詳細資訊，請參閱 [Windows 10 和更新版本的 Endpoint Protection 設定](endpoint-protection-windows-10.md)。

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>適用於 Windows 10 裝置限制設定檔的新設定 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
在此版本中，我們已新增 Windows 10 裝置限制設定檔的新設定，在下列類別中：

-  Windows Defender
-  行動數據與連線
-  鎖定畫面體驗
-  隱私權
-  搜尋
-  Windows 焦點
-  Microsoft Edge 瀏覽器

如需 Windows 10 設定的詳細資訊，請參閱 [Windows 10 和更新版本的裝置限制設定](device-restrictions-windows-10.md)。


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>Android 公司入口網站應用程式的應用程式保護原則現在有了新的使用者體驗<!--1305217-->
根據客戶的意見反應，我們已修改 Android 公司入口網站應用程式，以顯示 [存取公司內容] 按鈕。 目的是讓使用者再只需要存取支援應用程式保護原則 (Intune 行動應用程式管理的功能) 的應用程式時，可以避免不必要的註冊程序。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面上查看這些變更。

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>新的功能表動作，可輕鬆地移除公司入口網站<!--1164569-->
根據使用者意見反應，Android 版公司入口網站應用程式已新增功能表動作，可從裝置起始公司入口網站的移除。 此動作會將裝置從 Intune 管理移除，來讓使用者可以將應用程式從裝置移除。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面和 [Android 使用者文件](/intune-user-help/unenroll-your-device-from-intune-android)中看到這些變更。

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>透過 Windows 10 Creators Update 改進應用程式同步<!--676505-->
Windows 10 版公司入口網站應用程式現在會針對具有 Windows 10 Creators Update (版本 1703) 之裝置的應用程式安裝要求，自動初始化同步處理。 這會減少應用程式安裝在「待同步」狀態期間停止的問題。 此外，使用者將能從應用程式內手動起始同步處理。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面上查看這些變更。

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 公司入口網站新型引導式體驗 <!---1058938--->
Windows 10 的公司入口網站應用程式將包含之前尚未確定或註冊之裝置的引導式 Intune 逐步解說體驗。 新型體驗能提供逐步指示，可引導使用者註冊至 Azure Active Directory (取得條件式存取功能所需) 及 MDM 註冊 (取得裝置管理功能所需)。 引導式體驗能透過公司入口網站首頁取得。 未完成註冊的使用者可以繼續使用應用程式，但可使用的功能將會受到限制。

此更新只會在執行 Windows 10 年度更新版 (組建 1607) 或更新版本的裝置上顯示。 您可以在[應用程式 UI 的新功能](whats-new-app-ui.md)頁面看到這些變更。


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 和條件式存取管理主控台正式推出
我們宣佈推出 Azure 入口網站管理主控台中的新 Intune 和條件式存取管理主控台。 您現在可以透過 Azure 入口網站中的 Intune，將所有 Intune MAM 與 MDM 功能合併管理，並妥善利用 Azure AD 群組和目標設定功能。 Azure 中的條件式存取跨 Azure AD 和 Intune，將豐富的功能整合在一個統一主控台。 從系統管理經驗的觀點，移至 Azure 平台可讓您使用新式瀏覽器。

您現在可以在 Azure 入口網站 (portal.azure.com) 中看到沒有「預覽」標籤的 Intune。

除非您在訊息中心收到的一系列訊息中，有要求您採取動作來移轉群組的訊息，否則現有的客戶目前不需採取任何動作。 您可能也會收到訊息中心通知，說明因為我們這一端有錯誤而使移轉需要較長的時間。 我們會努力繼續移轉任何受影響的客戶。

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式中應用程式磚的增強功能
我們已更新首頁上應用程式磚的設計，以反映您針對公司入口網站所設定的商標色彩。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>iOS 版公司入口網站應用程式現在有帳戶選擇器可供使用
如果 iOS 裝置的使用者使用其工作或學校帳戶登入其他 Microsoft 應用程式，當他們登入公司入口網站時，可能會看到新的帳戶選擇器。 如需詳細資訊，請參閱[應用程式 UI 的新功能](whats-new-app-ui.md)。

## <a name="may-2017"></a>2017 年 5 月

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>在不取消註冊受管理裝置的情況下變更 MDM 授權單位 <!--1103950-->
您現在可以在不需要連絡 Microsoft 支援服務的情況下變更 MDM 授權單位，且不需要取消註冊並重新註冊您現有的受管理裝置。 在 Configuration Manager 主控台中，您可以將 [MDM 授權單位](/sccm/mdm/deploy-use/change-mdm-authority)從 [設定為 Configuration Manager] \(混合式\) 變更為 [Microsoft Intune] \(獨立\)，反之亦然。


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>已改進 Samsung Knox 啟動 PIN 的通知 <!--1087143-->
當使用者需要在 Samsung Knox 裝置上設定啟動 PIN 以符合加密規範時，點選對使用者顯示的通知會將他們引導至 [設定] 應用程式中的確切位置。  先前的通知會將使用者引導至密碼變更畫面。

### <a name="device-enrollment"></a>裝置註冊

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>對於共用 iPad 的 Apple School Manager (ASM) 支援<!-- 748864, 770395-->

Intune 現在支援以 Apple School Manager (ASM) 取代 Apple 裝置註冊計劃，來為 iOS 裝置提供全新註冊功能。 下列兩種情況皆需要 ASM 上線：在「共用的 iPad」上使用 Classroom 應用程式，以及透過 Microsoft 學校資料同步處理 (SDS) 將資料從 ASM 同步到 Azure Active Directory。 如需詳細資訊，請參閱[使用 Apple School Manager 啟用 iOS 裝置註冊](apple-school-manager-set-up-ios.md)。

> [!NOTE]
> 若要設定共用的 iPad 搭配 Classroom 應用程式使用，需要在 Azure 中設定 iOS Education，而此功能目前尚未提供。  此功能將於不久後加入。

### <a name="device-management"></a>裝置管理

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>使用 TeamViewer 對 Android 裝置提供遠端協助<!-- 675418 -->

Intune 現在可使用 [TeamViewer](https://www.teamviewer.com) 軟體 (另行購買)，讓您為執行 Android 裝置的使用者提供遠端協助。 如需詳細資訊，請參閱[對 Intune 管理的 Android 裝置提供遠端協助](device-profile-android-teamviewer.md)。

### <a name="app-management"></a>應用程式管理

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>適用於 MAM 的新應用程式保護原則條件 <!-- 679864 -->

您現在可以在無需註冊使用者的情況下，設定能強制執行下列原則的 MAM 需求：

- 對低應用程式版本
- 最低作業系統版本
- 目標應用程式的最低 Intune APP SDK 版本 (僅限 iOS)

這項功能適用於 Android 和 iOS。 Intune 支援作業系統平台版本、應用程式版本，以及 Intune APP SDK 的最低版本強制。 在 iOS 上，已整合 SDK 的應用程式也可以設定 SDK 層級的最低版本強制。 如果沒有符合應用程式保護原則於上述三個不同層級的最低需求，使用者將無法存取目標應用程式。 此時，使用者可以選擇移除其帳戶 (適用於多重身分識別應用程式)、關閉該應用程式，或更新作業系統或應用程式版本。

您也可設定其他設定，以提供能建議使用者進行作業系統或應用程式升級的非封鎖式通知。 使用者可以關閉此通知，並繼續正常地使用應用程式。

如需詳細資訊，請參閱 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)和 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)。

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>設定 Android for Work 的應用程式設定<!-- 621621 -->
市集中有一些 Android 應用程式支援受管理設定選項，可以讓 IT 系統管理員控制應用程式在工作設定檔中執行的方式。 您現在可以使用 Intune 來檢視應用程式支援的設定，並使用設定設計工具或 JSON 編輯器從 Azure 入口網站進行設定。 如需詳細資訊，請參閱[使用 Android for Work 的應用程式設定](app-configuration-policies-use-android.md)。

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>不需註冊的新 MAM 應用程式設定功能<!-- 677969 -->
您現在可以在沒有註冊通道的情況下，透過 MAM 建立應用程式設定原則。 此功能相當於行動裝置管理 (MDM) 應用程式設定中的應用程式設定原則。 如需使用 MAM 而不註冊的應用程式設定範例，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>為 Managed Browser 設定允許和封鎖的 URL 清單<!-- 682960 -->
您現在可以在 Azure 入口網站中使用應用程式組態設定，為 Intune Managed Browser 設定允許和封鎖的網域及 URL 清單。 不論 Intune Managed Browser 是用於受管理或未受管理的裝置上，都適用這些設定。 如需詳細資訊，請參閱[搭配 Microsoft Intune 使用 Managed Browser 原則管理網際網路存取](app-configuration-managed-browser.md)。

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>應用程式保護原則技術支援檢視<!-- 1069473 -->
IT 技術支援使用者現在可以在 [疑難排解] 刀鋒視窗中查看使用者授權狀態，和指派給使用者的應用程式保護原則應用程式的狀態。 如需詳細資訊，請參閱[疑難排解](./help-desk-operators.md)。

### <a name="device-configuration"></a>裝置設定

#### <a name="control-website-visits-on-ios-devices----723832---"></a>控制 iOS 裝置上的網站瀏覽<!-- 723832 -->
您現在可以使用下列兩種方法，來控制 iOS 裝置使用者可以瀏覽的網站：

- 使用 Apple 內建網路內容篩選器新增允許和封鎖的 URL。

- 僅允許 Safari 瀏覽器存取指定的網站。 針對您指定的每個網站，會在 Safari 中建立書籤。

如需詳細資訊，請參閱[適用於 iOS 裝置的網路內容篩選器設定](web-content-filter-settings-ios.md)。

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>預先設定 Android for Work 應用程式的裝置權限 <!-- 621614 -->
對於部署到 Android for Work 裝置工作設定檔的應用程式，您現在可以設定個別應用程式的權限狀態。  根據預設，需要裝置權限 (例如存取位置或裝置相機) 的 Android 應用程式會提示使用者接受或拒絕授與權限。  例如，若應用程式會使用裝置的麥克風，則系統會提示使用者授與應用程式使用麥克風的權限。 此功能可讓您代表使用者定義權限。  您可以設定權限以 a) 自動拒絕而不通知使用者，b) 自動核准而不通知使用者，或 c) 提示使用者接受或拒絕。 如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>針對 Android for Work 裝置定義應用程式特定的 PIN <!-- 728976, 1102534 -->
工作設定檔做為 Android for Work 裝置管理的 Android 7.0 和更新版本裝置，可讓管理員定義僅適用於工作設定檔中的應用程式的密碼原則。  這些選項包括：

- 僅定義全裝置密碼原則：這是使用者必須用來解鎖整個裝置的密碼。
- 僅定義工作設定檔密碼原則：每當開啟工作設定檔中的應用程式時，系統就會提示使用者輸入密碼。
- 定義裝置和工作設定檔原則：IT 管理員可定義具有不同強度的裝置密碼原則和工作設定檔密碼原則 (例如，使用 4 位數 PIN 來解鎖裝置，但必須使用 6 位數 PIN 來開啟任何工作應用程式)。

如需詳細資訊，請參閱 [Microsoft Intune 中的 Android for Work 裝置限制設定](device-restrictions-android-for-work.md)。

> [!NOTE]
> 此功能僅適用於 Android 7.0 及更新版本。  根據預設，使用者可使用這兩個個別定義的 PIN，或選擇結合這兩個定義的 PIN，以組成包含這兩者的最強式密碼。

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 裝置的新設定<!-- 978585 -->
我們已新增可控制數種功能 (例如無線顯示器、裝置探索、工作切換和 SIM 卡錯誤訊息) 的 [Windows 裝置限制設定](device-restrictions-windows-10.md)。

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>憑證設定的更新<!-- 918991 and 823198 -->
建立 SCEP 憑證設定檔時，針對 [主體名稱格式]，iOS、Android 和 Windows 裝置可使用 [自訂] 選項。 在此更新之前，[自訂] 欄位僅適用於 iOS 裝置。 如需詳細資訊，請參閱[建立 SCEP 憑證設定檔](certificates-scep-configure.md#create-a-scep-certificate-profile)。

建立 PKCS 憑證設定檔時，針對 [主體別名]，可使用 [自訂 Azure AD 屬性]。 當您選取 [自訂 Azure AD 屬性] 時，可使用 [部門] 選項。 如需詳細資訊，請參閱[建立 PKCS 憑證設定檔](certficates-pfx-configure.md#create-a-pkcs-certificate-profile)。

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>設定 Android 裝置處於 kiosk 模式時可執行的多個應用程式<!-- 662059 -->
Android 裝置處於 kiosk 模式時，之前只能設定一個允許執行的應用程式。 您現在可以使用應用程式識別碼、存放區 URL或藉由選取您已管理的 Android 應用程式來設定多個應用程式。 如需詳細資訊，請參閱 [Kiosk 模式設定](device-restrictions-android.md#kiosk)。



## <a name="april-2017"></a>2017 年 4 月

### <a name="support-for-managing-the-apple-classroom-app"></a>支援管理 Apple「課堂」應用程式
您現在可在 iPad 裝置上管理 iOS「課堂」應用程式。 使用正確的課堂和學生資料，在老師的 iPad 上設定「課堂」應用程式，然後設定學生的 iPad 向課堂註冊，這樣您就能使用應用程式控制它們。
如需詳細資訊，[設定 iOS 的教育設定](education-settings-configure-ios.md)。

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>支援 Android 應用程式的受管理設定選項 <!-- 621621 -->
Intune 現在可以設定 Play 商店中支援受控設定選項的 Android 應用程式。  這項功能可讓 IT 人員檢視應用程式所支援的設定值清單，並提供頂級的引導式 UI，讓 IT 人員可以設定這些值。

### <a name="new-android-policy-for-complex-pins----722069---"></a>新增複雜 PIN 碼的 Android 原則 <!-- 722069 -->
您現在可以在 Android 裝置設定檔中，針對執行 Android 5.0 和更新版本的裝置，將必要的[密碼](device-restrictions-android.md#password)類型設定為複雜數字。  使用此設定可防止裝置使用者建立包含重複或連續數字的 PIN 碼，例如 1111 或 1234。

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work 裝置的其他支援
- **管理密碼和工作設定檔設定** <!-- 612808 -->

  這項新的 Android for Work 裝置限制原則現在可讓您在所管理的 Android for Work 裝置上管理密碼和工作設定檔設定。

- **允許工作和個人設定檔間的資料共用** <!-- 1045102 -->

Android for Work 裝置限制設定檔現在有新的選項，可協助您設定工作和個人設定檔之間的資料共用。

- **限制工作和個人設定檔間的複製和貼上** <!-- 1046094 -->

  Android for Work 裝置的新自訂裝置設定檔現在可讓您限制是否允許工作和個人應用程式間的複製和貼上動作。

如需詳細資訊，請參閱 [Android for Work 的裝置限制](device-restrictions-android-for-work.md)。

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>將 LOB 應用程式指派給 iOS 和 Android 裝置 <!-- 1057568 -->
您現在可以將 [iOS](lob-apps-ios.md) 版企業營運 (LOB) 應用程式 (.ipa 檔案) 和 [Android](lob-apps-android.md) 版企業營運應用程式 (.apk 檔案) 指派給使用者或裝置。


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS 的新裝置原則 <!-- 723774, 723815, 723826, 723830 -->
- **主畫面上的應用程式**：控制使用者會在[其 iOS 裝置的主畫面](home-screen-settings-ios.md)上看到哪些應用程式。 這項原則會變更主畫面的配置，但不會部署任何應用程式。

- **AirPrint 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPrint 裝置](air-print-settings-ios-macos.md) (網路印表機)。

- **AirPlay 裝置的連線**：控制 iOS 裝置的使用者可以連線到哪些 [AirPlay 裝置](airplay-settings-ios.md) (例如 Apple TV)。

- **自訂鎖定畫面訊息**：設定使用者將會在其 iOS 裝置的鎖定畫面上看到的自訂訊息，這會取代預設鎖定畫面訊息。 如需詳細資訊，請參閱[啟動 iOS 裝置上的遺失模式](device-lost-mode.md)

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>限制 iOS 應用程式的推播通知 <!-- 723767 -->
在 Intune 裝置限制設定檔中，您現在可以設定 iOS 裝置的下列[通知設定](app-notification-settings-ios.md)：

- 完全開啟或關閉指定應用程式的通知。
- 在通知中心內開啟或關閉指定應用程式的通知。
- 指定警示類型，可以是 [無]、[橫幅] 或 [Modal Alert] (強制回應警示)。
- 指定此應用程式是否允許徽章。
- 指定是否允許通知音效。

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>設定 iOS 應用程式在單一應用程式模式中自發執行 <!-- 737837 -->
您現在可以使用 Intune 裝置設定檔，設定 iOS 裝置在[自發性單一應用程式模式](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)中執行指定的應用程式。 設定此模式並執行應用程式時，裝置會被鎖定，因此只能執行該應用程式。 一個例子是當您設定應用程式讓使用者在裝置上進行測試時。 當應用程式的動作完成時，或當您移除此原則時，裝置就會回到其正常狀態。

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>為 iOS 裝置上的電子郵件和網頁瀏覽設定受信任的網域 <!-- 723765 -->
您現在可以從 iOS 裝置限制設定檔設定下列[網域設定](device-restrictions-ios.md#domains)：

- **未標示的電子郵件網域** - 使用者傳送或接收的電子郵件，若不符合您於此處所指定的網域，會標示為不受信任。

- **受管理的 Web 網域** - 從您於此處指定的 URL 下載之文件，會視為受管理的文件 (僅限 Safari)。  

- **Safari 密碼自動填入網域** - 使用者在 Safari 中可以儲存的密碼，只有來自與此處指定的模式相符之 URL 的密碼。 若要使用此設定，裝置必須在受監督的模式下，且未設定供多重使用者之用。 (iOS 9.3+)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>IOS 公司入口網站中可以使用 VPP 應用程式 <!-- 748782 -->
您現在可以將 iOS 大量採購 (VPP) 應用程式當做「可用」的安裝指派給使用者。 終端使用者必須有 Apple Store 帳戶，才能安裝應用程式。

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>從 Apple VPP Store 同步處理電子書 <!-- 800878 -->
您現在可以將從 Apple 大量採購程式市集購買的[書籍與 Intune 同步處理](vpp-apps-ios.md)，然後將這些書籍指派給使用者。

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung Knox Standard 裝置的多使用者管理 <!-- 971988 -->
Intune 的[多使用者管理](android-enroll.md)現在支援執行 Samsung Knox Standard 的裝置。 這表示終端使用者可以使用其 Azure Active Directory 認證登入和登出裝置，而且該裝置不論是否正在使用，都會集中管理。  當使用者登入時，他們可以存取應用程式，並將任何原則套用到這些應用程式。 當使用者登出時，會清除所有應用程式資料。

### <a name="additional-windows-device-restriction-settings----818566---"></a>其他 Windows 裝置限制設定 <!-- 818566 -->
我們新增了其他 [Windows 裝置限制設定](device-restrictions-windows-10.md)的支援，例如額外的 Edge 瀏覽器支援、裝置鎖定畫面自訂、[開始] 功能表自訂、Windows 焦點搜尋集桌布，以及 Proxy 設定。

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 Creators Update 的多使用者支援 <!-- 822547 -->
我們針對執行 Windows 10 Creators Update 並已加入 Azure Active Directory 網域的裝置，新增了[多使用者管理](windows-enroll.md)的支援。 這表示當不同的標準使用者使用其 Azure AD 認證登入裝置時，將會收到指派給其使用者名稱的任何應用程式和原則。 針對安裝應用程式等自助式案例，使用者目前無法使用公司入口網站來進行。

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 電腦的 Fresh Start<!-- 1004830 -->
適用於 Windows 10 電腦的新[「全新開始」裝置動作](device-fresh-start.md)現在已經可以使用。  當您發出此動作時，將會移除任何安裝在電腦上的應用程式，而且電腦會自動更新為最新版的 Windows。 這可用來協助移除通常會隨新電腦提供之預先安裝的 OEM 應用程式。 您可以設定是否在發出此裝置動作時保留使用者資料。

### <a name="additional-windows-10-upgrade-paths----903672---"></a>其他 Windows 10 升級路徑 <!-- 903672 -->
您現在可以建立[版本升級原則，來將裝置升級為](edition-upgrade-configure-windows-10.md)下列其他的 Windows 10 版本：

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 專業教育版
- Windows 10 專業教育版 N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>大量註冊 Windows 10 裝置 <!-- 747607 -->
您現在可以使用 Windows 設定設計工具 (WCD) 將執行 Windows 10 Creators Update 的大量裝置加入到 Azure Active Directory 和 Intune。 若要為您的 Azure AD 租用戶啟用[大量 MDM 註冊](windows-bulk-enroll.md)，請使用 Windows 設定設計工具建立會將裝置加入到 Azure AD 租用戶的佈建套件，然後將套件套用至您要大量註冊及管理的公司擁有裝置。 將套件套用至裝置之後，裝置會加入 Azure AD、在 Intune 中註冊，並準備好供 Azure AD 使用者登入。  Azure AD 使用者是這些裝置上的標準使用者，並且會接收指派的原則和必要應用程式。 目前不支援自助式和公司入口網站案例。

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>PIN 碼和受管理儲存位置的新 MAM 設定 <!-- 581122, 736644 -->
現在有兩個新的應用程式設定可協助您進行行動應用程式管理 (MAM) 案例：

- **在管理裝置 PIN 碼時停用應用程式 PIN 碼** - 偵測已註冊的裝置上是否有裝置 PIN 碼；如果有，則略過應用程式保護原則觸發的應用程式 PIN 碼。 這項設定可減少對在已註冊裝置上開啟啟用 MAM 的應用程式之使用者顯示的 PIN 提示次數。 這項功能適用於 Android 和 iOS。

- **選取要用於儲存公司資料的儲存體服務** - 可讓您指定要用於儲存公司資料的儲存位置。 使用者可以儲存至所選取的儲存位置服務，這表示將會封鎖未列出的其他所有儲存位置服務。

  支援的儲存位置服務清單：

  - OneDrive
  - 商務用 SharePoint Online
  - 本機儲存體

### <a name="help-desk-troubleshooting-portal----907448---"></a>服務台疑難排解入口網站 <!-- 907448 -->
新的[疑難排解入口網站](help-desk-operators.md)可協助服務台操作員和 Intune 系統管理員檢視使用者及其裝置，並執行工作以解決 Intune 技術問題。

## <a name="march-2017"></a>2017 年 3 月

### <a name="support-for-ios-lost-mode---431695--"></a>支援 iOS 遺失模式 <!--431695-->
針對 iOS 9.3 和更新的裝置，Intune 新增**遺失模式**的支援。 您現在可以鎖定裝置以防止任何使用，並在裝置的鎖定畫面上顯示訊息和連絡電話號碼。

使用者將無法解除鎖定裝置，除非系統管理員停用「遺失模式」。 啟用「遺失模式」時，您可以使用 [尋找裝置] 動作在 Intune 主控台中的地圖上顯示裝置的地理位置。

裝置必須是透過 DEP 註冊之公司擁有的 iOS 裝置，且處於受監督模式。

如需詳細資訊，請參閱[什麼是 Microsoft Intune 裝置管理？](device-management.md)

### <a name="improvements-to-device-actions-report---677150--"></a>裝置動作報告改善 <!--677150-->
我們改善了裝置動作報告以提升效能。 此外，您現在可以依狀態篩選報告。 例如，您可以篩選報告以僅顯示已完成的裝置動作。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](apps-add.md)。

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>指派 LOB 應用程式給使用未註冊裝置的使用者 <!--748823-->
您現在可以將市集中的企業營運應用程式指派給使用者，不論其裝置是否已向 Intune 註冊。 如果未向 Intune 註冊使用者裝置，則必須前往「公司入口網站」網站安裝它，而不是公司入口網站應用程式。

### <a name="new-compliance-reports---846671--"></a>新的合規性報告 <!--846671-->
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

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>直接存取 Apple 註冊案例 <!--951869-->
對於在 2017 年 1 月之後建立的 Intune 帳戶，Intune 已經啟用使用 Azure 入口網站中的「註冊裝置」工作負載直接存取 Apple 註冊案例。 Apple 註冊預覽原本只能從 Azure 入口網站中的連結存取。 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用這些功能。 移轉的排程尚未宣布，但將會盡快提供詳細資料。 如果您現有的帳戶無法存取預覽，我們強烈建議您建立試用帳戶來測試新的體驗。


## <a name="february-2017"></a>2017 年 2 月

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>限制行動裝置註冊的能力 <!--747600, 795782-->
Intune 正在新增新的註冊限制，以控制哪些行動裝置平台可以註冊。 Intune 將行動裝置平台分為 iOS、macOS、Android、Windows 和 Windows Mobile。

* 限制行動裝置註冊不會限制電腦用戶端註冊。  
* 僅限 iOS 與 Android，有一個額外選項可阻擋註冊個人擁有的裝置。

Intune 會將所有的新裝置標示為個人，除非 IT 系統管理員採取動作將它們標示為公司擁有，如[本文章](device-enrollment.md)所說明。

### <a name="view-all-actions-on-managed-devices---677150--"></a>檢視受管理裝置上的所有動作 <!--677150-->
新的__裝置動作__報表會顯示曾執行遠端動作的人員，像是裝置恢復出廠預設值，並會另外顯示該動作的狀態。 請參閱[什麼是裝置管理？](device-management.md)。

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>未受管理的裝置可以存取已指派的應用程式 <!--664691-->
iOS 和 Android 使用者能夠在他們未受管理的裝置上，安裝指派給他們的「無須註冊即可使用」應用程式，這屬於公司入口網站的設計變更。 使用 Intune 認證，使用者能夠登入公司入口網站，並查看指派給他們的應用程式清單。 「無須註冊即可使用」應用程式的應用程式套件，可透過公司入口網站下載取得。 這項變更不會影響需要註冊才能安裝的應用程式，因為如果使用者想要安裝這些應用程式，系統會提示他們註冊裝置。

### <a name="custom-app-categories---748805--"></a>自訂應用程式類別 <!--748805-->
您現在可以建立、編輯和指派您新增至 Intune 之應用程式的類別。 目前只能以英文指定類別。
請參閱[如何將應用程式新增至 Intune](apps-add.md)。

### <a name="display-device-categories---814654--"></a>顯示裝置類別 <!--814654-->
裝置清單現在會以資料行顯示裝置類別。 您也可以在裝置內容刀鋒視窗的內容區段中編輯類別。 請參閱[如何將應用程式新增至 Intune](apps-add.md)。

### <a name="configure-windows-update-for-business-settings---776716--"></a>設定商務用 Windows Update 的設定 <!--776716-->

「Windows 即服務」是一種為 Windows 10 提供更新的新做法。 從 Windows 10 開始，任何新的「功能更新」和「品質更新」都會包含所有先前的更新內容。 這表示只要您安裝了最新的更新，就能確定您的 Windows 10 裝置已完全更新至最新版。 不同於舊版 Windows，您現在必須安裝整個更新而不是部分更新。

使用商務用 Windows Update，可以簡化更新管理體驗，因此您不需要核准裝置群組的個別更新。 只要設定更新首度發行策略，您還是可以管理環境中的風險，Windows Update 會確保在適當的時間安裝更新。 Microsoft Intune 可讓您在裝置上設定更新設定，並可讓您延後更新的安裝。 Intune 不會儲存更新，只會儲存更新原則指派。 裝置直接存取 Windows Update 進行更新。使用 Intune 設定及管理 **Windows 10 更新響鈴**。 更新響鈴是一組包含何時及如何安裝 Windows 10 更新的設定。 如需詳細資訊，請參閱[設定商務用 Windows Update 的設定](windows-update-for-business-configure.md)。
