---
title: Microsoft Intune 中 Windows 10 的裝置限制設定 | Microsoft Docs
description: 查看有關在 Windows 10 和更新版本的裝置上建立裝置限制的所有設定及其描述的清單。 使用組態設定檔中的這些設定，在 Microsoft Intune 中控制螢幕擷取畫面、密碼要求、kiosk 設定、商店中的應用程式、Microsoft Edge 瀏覽器、Windows Defender、雲端存取及開始功能表等。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/29/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5c9bad56a8214cd736208526865b5f9c8b23db00
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734787"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>使用 Intune 來允許或限制功能的 Windows 10 (和更新版本) 裝置設定

本文列出並描述您可以在 Windows 10 和更新版本裝置上控制的所有不同設定。 作為行動裝置管理 (MDM) 解決方案的一部分，請使用這些設定來允許或停用功能、設定密碼規則、自訂鎖定畫面、使用 Microsoft Defender，以及執行其他作業。

這些設定會新增至 Intune 裝置組態設定檔，然後指派或部署到您的 Windows 10 裝置。

> [!Note]
> 並非所有版本的 Windows 都提供全部選項。 若要查看支援的版本，請參閱 [Policy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (原則 CSP) (開啟另一個 Microsoft 網站)。

## <a name="before-you-begin"></a>開始之前

[建立裝置組態設定檔](device-restrictions-configure.md#create-the-profile)。

## <a name="app-store"></a>App Store

這些設定使用 [ApplicationManagement 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)，它也會列出支援的 Windows 版本。

- **App store** (僅限行動裝置)：  (預設) 可讓終端使用者在行動裝置上存取 App store。 [封鎖]  ：防止使用 App store。
- **自動更新來自市集的應用程式**：  (預設) 允許自動更新從 Microsoft Store 安裝的應用程式。 [封鎖]  ：防止自動安裝更新。
- [安裝信任的應用程式]  ：選擇是否可以安裝非 Microsoft Store 應用程式，也稱為側載。 側載是安裝、然後執行或測試未經 Microsoft Store 認證的應用程式。 例如，僅公司內部使用的應用程式。 選項包括：
  - [未設定]  (預設)：使用預設的作業系統。
  - [封鎖]  ：防止側載。 無法安裝非 Microsoft Store 應用程式。
  - [允許]  ：允許側載。 可以安裝非 Microsoft Store 應用程式。
- [開發人員解除鎖定]  ：允許 Windows 開發人員設定，例如允許終端使用者修改側載的應用程式。 選項包括：
  - [未設定]  (預設)：使用預設的作業系統。
  - [封鎖]  ：防止開發人員模式和側載應用程式。
  - [允許]  ：允許開發人員模式和側載應用程式。

  [啟用您的裝置用於開發](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)有這項功能的詳細資訊。

- **共用的使用者應用程式資料**：選擇 [允許]  ，則應用程式資料可供相同裝置的不同使用者共用，也可與該應用程式的其他執行個體共用。 [未設定]  (預設) 防止與相同應用程式的其他使用者及其他執行個體共用資料。
- **僅使用私人市集**：[允許]  只允許從私人市集下載應用程式，不會從包括零售目錄在內的公用儲存區下載應用程式。 [未設定]  (預設) 只允許從私人市集下載應用程式，不得從公用市集下載。
- **啟動來自市集的應用程式**：[封鎖]  會停用預先安裝於裝置上，或從 Microsoft Store 下載的所有應用程式。 [未設定]  (預設) 允許開啟這些應用程式。
- **將應用程式資料安裝在系統磁碟區**：[封鎖]  阻止應用程式將資料儲存在裝置的系統磁碟區。 [未設定]  (預設) 允許應用程式將資料儲存在系統磁碟區。
- **將應用程式安裝在系統磁碟機**：[封鎖]  會防止應用程式安裝在裝置的系統磁碟機上。 [未設定]  (預設) 允許應用程式安裝在系統磁碟機上。
- **遊戲 DVR** (僅限 Desktop)：[封鎖]  會停用 Windows 遊戲錄影和廣播。 [未設定]  (預設) 允許遊戲錄影和廣播。
- **僅限存放區的應用程式**：此設定會決定使用者從 Microsoft Store 以外的位置安裝應用程式時的使用者體驗。 選項包括：

  - [**未設定**] （預設）：允許使用者從 Microsoft Store 以外的地方安裝應用程式，包括其他原則設定中定義的應用程式。  
  - **任何位置**：關閉應用程式建議，並允許使用者從任何位置安裝應用程式。  
  - **僅限商店**：強制終端使用者只從 Microsoft Store 安裝應用程式。
  - **建議**：從 Microsoft Store 中提供的 web 安裝應用程式時，使用者會看到一則訊息，建議他們從商店下載。  
  - **偏好存放區**：當使用者從 Microsoft Store 以外的地方安裝應用程式時，會發出警告。

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **由使用者控制安裝**：設定為 [未設定]  (預設值) 時，Windows Installer 會阻止使用者變更通常保留給系統管理員的安裝選項，例如，進入安裝檔案的目錄。 [封鎖]  允許使用者變更這些安裝選項，並略過一些 Windows Installer 安全性功能。

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall) \(英文\)

- **以較高的權限安裝應用程式**：設定為 [未設定]  (預設值) 時，系統會在安裝系統管理員未部署或提供的程式時套用目前使用者的權限。 [封鎖]  會指示 Windows Installer 在系統上安裝任何程式時使用較高的權限。 這些權限會延伸至所有程式。

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges) \(英文\)

- **啟動應用程式**：輸入當使用者登入裝置後要開啟的應用程式清單。 請務必使用 Windows 應用程式的套件系列名稱 (PFN) 清單 (以分號分隔)。 若要使此原則生效，Windows 應用程式中的資訊清單必須使用啟動工作。

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon) \(英文\)

## <a name="cellular-and-connectivity"></a>行動數據與連線

這些設定使用[連線原則](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity)和 [Wi-Fi 原則](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) CSP，它也會列出支援的 Windows 版本。

- [Wi-Fi 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **行動數據頻道** 當終端使用者連線到行動電話通訊網路時，選擇是否讓終端使用者使用資料，例如瀏覽網頁。 選項包括：
  - [未設定]  (預設)：使用作業系統的預設值，這可能會允許行動數據頻道。 終端使用者可以關閉它。
  - [封鎖]  ：不允許行動數據頻道。 終端使用者可以開啟它。
  - [允許]  ：允許行動數據頻道。 終端使用者無法關閉它。

- **數據漫遊**：[封鎖]  可防止裝置上的行動數據漫遊。 [未設定]  (預設) 存取資料時允許網路之間的漫遊。
- **透過行動電話通訊網路的 VPN**：[封鎖]  防止裝置在連線到行動電話通訊網路時存取 VPN 連線。 [未設定]  (預設) 允許 VPN 使用包括行動電話在內的任何連線。
- **透過行動電話通訊網路的 VPN 漫遊**：[封鎖]  阻止裝置在行動電話通訊網路漫遊時存取 VPN 連線。 [未設定]  (預設) 在漫遊時允許 VPN 連線。
- **連線的裝置服務**：[封鎖]  停用連線的裝置平台 (CDP) 元件。 CDP 能夠探索並連線到其他裝置 (透過藍牙/區域網路或雲端) 來支援遠端應用程式啟動、遠端傳訊、遠端應用程式工作階段，以及其他跨裝置體驗。 [未設定]  (預設) 允許連線的裝置服務，這可探索並連線到其他藍牙裝置。
- **NFC**：[封鎖]  防止近距離無線通訊 (NFC) 功能。 [未設定]  (預設) 可讓使用者啟用並設定裝置上的 NFC 功能。
- **Wi-Fi**：[封鎖]  可防止使用者在裝置上啟用、設定及使用 Wi-Fi 連線。 [未設定]  (預設) 允許 Wi-Fi 連線。
- **自動連線至 Wi-Fi 熱點**：[封鎖]  防止裝置自動連線至 Wi-Fi 熱點。 [未設定]  (預設) 讓裝置自動連線到免費 Wi-Fi 熱點並自動接受任何連線條款和條件。
- **手動設定 Wi-Fi**：[封鎖]  防止裝置連線至 MDM 伺服器安裝網路外的 Wi-Fi。 [未設定]  (預設) 允許終端使用者新增及設定自己的 Wi-Fi 連線網路 SSID。
- **Wi-Fi 掃描間隔**：輸入裝置掃描 Wi-Fi 網路的頻率。 輸入 1 (最頻繁) 到 500 (最不頻繁) 的值。 預設值為 `0` (零)。

### <a name="bluetooth"></a>Bluetooth

這些設定使用[藍牙原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth)，它也會列出支援的 Windows 版本。

- **藍牙**：[封鎖]  防止使用者啟用藍牙。 [未設定]  (預設) 允許在裝置上使用藍牙。
- **藍牙探索**：[封鎖]  防止其他藍牙啟用的裝置探索此裝置。 [未設定]  (預設) 允許其他藍牙啟用的裝置，例如耳機，探索此裝置。
- **藍牙預先配對**：[封鎖]  防止特定的藍牙裝置與主機裝置自動配對。 [未設定]  (預設) 允許與主機裝置自動配對。
- **藍牙通知**：[封鎖]  防止裝置傳送出藍牙通知。 [未設定]  (預設) 允許裝置傳送出藍牙通知。
- **藍牙允許的服務**：[新增]  允許之藍牙服務和設定檔的十六進位字串清單，例如 `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`。

  [ServicesAllowedList usage guide](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide) (ServicesAllowedList 使用指南) 有服務清單的詳細資訊。

## <a name="cloud-and-storage"></a>雲端與儲存體

這些設定使用[帳戶原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts)，它也會列出支援的 Windows 版本。

- **Microsoft 帳戶**：[封鎖]  防止終端使用者建立 Microsoft 帳戶與裝置的關聯性。 [未設定]  (預設) 允許新增及使用 Microsoft 帳戶。
- **非 Microsoft 帳戶**：[封鎖]  防止終端使用者以使用者介面新增非 Microsoft 帳戶。 [未設定]  (預設) 讓使用者新增未與 Microsoft 帳戶建立關聯的電子郵件帳戶。
- **Microsoft 帳戶的設定同步**：[未設定]  (預設) 允許與 Microsoft 帳戶建立關聯的裝置和應用程式設定在裝置之間同步。 [封鎖]  防止此同步。
- **Microsoft 帳戶登入小幫手**：設為 [未設定]  (預設) 時，終端使用者可以啟動和停止 **Microsoft 帳戶登入小幫手** (wlidsvc) 服務。 此作業系統服務可讓使用者登入其 Microsoft 帳戶。 [停用]  防止終端使用者控制 Microsoft 登入小幫手服務 (wlidsvc)。

## <a name="cloud-printer"></a>雲端印表機

這些設定使用 [EnterpriseCloudPrint 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint)，它也會列出支援的 Windows 版本。

- **印表機探索 URL**：輸入用於尋找雲端印表機的 URL。 例如，輸入 `https://cloudprinterdiscovery.contoso.com`。
- **印表機存取授權 URL**：輸入驗證端點 URL 以取得 OAuth 權杖。 例如，輸入 `https://azuretenant.contoso.com/adfs`。
- **Azure 原生用戶端應用程式 GUID**：輸入經允許可從 OAuthAuthority 取得 OAuth 權杖的用戶端應用程式 GUID。 例如，輸入 `E1CF1107-FF90-4228-93BF-26052DD2C714`。
- **列印服務資源 URI**：輸入 Azure 入口網站中所設定列印服務的 OAuth 資源 URI。 例如，輸入 `http://MicrosoftEnterpriseCloudPrint/CloudPrint`。
- **要查詢的印表機上限**：輸入您要接受查詢的印表機數目上限。 預設值為 `20`。
- **印表機探索服務資源 URI**：輸入 Azure 入口網站中所設定印表機探索服務的 OAuth 資源 URI。 例如，輸入 `http://MopriaDiscoveryService/CloudPrint`。

> [!TIP]
> 設定 [Windows Server 混合式雲端列印](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)之後，您可以設定這些設定，然後將它們部署到 Windows 裝置。

## <a name="control-panel-and-settings"></a>控制台和設定

- **設定應用程式**：[封鎖]  防止終端使用者存取 Windows 設定應用程式。 [未設定]  (預設) 可讓使用者在裝置中開啟設定應用程式。
  - **系統**：[封鎖]  防止存取設定應用程式的 [系統] 區域。 [未設定]  (預設) 允許存取。
    - **修改電源及睡眠設定** (僅限 Desktop)：[封鎖]  防止終端使用者變更裝置的電源及睡眠設定。 [未設定]  (預設) 可讓使用者變更電源與睡眠設定。
  - **裝置**：[封鎖]  防止存取裝置設定應用程式的 [裝置] 區域。 [未設定]  (預設) 允許存取。
  - **網路與網際網路**：[封鎖]  防止存取裝置設定應用程式的 [網路與網際網路] 區域。 [未設定]  (預設) 允許存取。
  - **個人化**：[封鎖]  防止存取裝置設定應用程式的 [個人化] 區域。 [未設定]  (預設) 允許存取。
  - **應用程式**：[封鎖]  防止存取裝置設定應用程式的 [應用程式] 區域。 [未設定]  (預設) 允許存取。
  - **帳戶**：[封鎖]  防止存取裝置設定應用程式的 [帳戶] 區域。 [未設定]  (預設) 允許存取。
  - **時間與語言**：[封鎖]  防止存取裝置設定應用程式的 [時間與語言] 區域。 [未設定]  (預設) 允許存取。
    - **修改系統時間**：[封鎖]  防止終端使用者變更裝置的日期和時間設定。 [未設定]  會讓使用者變更這些設定。
    - **修改區域設定** (僅限 Desktop)：[封鎖]  防止終端使用者變更裝置的區域設定。 [未設定]  會讓使用者變更這些設定。
    - **修改語言設定** (僅限 Desktop)：[封鎖]  防止終端使用者變更裝置的語言設定。 [未設定]  會讓使用者變更這些設定。

      [設定原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **遊戲**：[封鎖]  防止存取裝置設定應用程式的 [遊戲] 區域。 [未設定]  (預設) 允許存取。
  - **輕鬆存取**：[封鎖]  防止存取裝置設定應用程式的 [輕鬆存取] 區域。 [未設定]  (預設) 允許存取。
  - **隱私權**：[封鎖]  防止存取裝置設定應用程式的 [隱私權] 區域。 [未設定]  (預設) 允許存取。
  - **更新與安全性**：[封鎖]  防止存取裝置設定應用程式的 [更新與安全性] 區域。 [未設定]  (預設) 允許存取。

## <a name="display"></a>顯示

這些設定使用[顯示原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display)，它也會列出支援的 Windows 版本。

GDI DPI 縮放比例會讓非 DPI 感知的應用程式變成依監視器 DPI 感知。

- **開啟應用程式的 GDI 縮放比例**：[新增]  您希望開啟 GDI DPI 縮放比例的舊版應用程式。 例如，輸入 `filename.exe` 或 `%ProgramFiles%\Path\Filename.exe`。

  您清單中的所有舊版應用程式都會開啟 GDI DPI 縮放比例。

- **關閉應用程式的 GDI 縮放比例**：[新增]  您希望關閉 GDI DPI 縮放比例的舊版應用程式。 例如，輸入 `filename.exe` 或 `%ProgramFiles%\Path\Filename.exe`。

  您清單中的所有舊版應用程式都會關閉 GDI DPI 縮放比例。

您也可以 [匯入]  具有應用程式清單的 .csv 檔案。

## <a name="general"></a>一般

這些設定使用[體驗原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)，它也會列出支援的 Windows 版本。 

- **螢幕擷取** (僅限行動裝置)：[封鎖]  防止終端使用者在裝置上取得螢幕擷取畫面。 [未設定]  (預設) 允許此功能。
- **複製並貼上** (僅限行動裝置)：[封鎖]  防止終端使用者在裝置的應用程式之間使用複製並貼上。 [未設定]  (預設) 允許此功能。
- **手動取消註冊**：[封鎖]  防止終端使用者使用裝置上的工作場所控制台刪除工作場所帳戶。 [未設定]  (預設) 允許此功能。

  如果電腦已加入 Azure AD，且啟用自動註冊，則不會套用此原則設定。

- **手動安裝根憑證** (僅限行動裝置)：[封鎖]  防止終端使用者手動安裝根憑證及中繼 CAP 憑證。 [未設定]  (預設) 允許此功能。
- **相機**：[封鎖]  防止終端使用者在裝置上使用相機。 [未設定]  (預設) 允許此功能。
- **OneDrive 檔案同步**：[封鎖]  防止終端使用者將裝置中的檔案同步至 OneDrive。 [未設定]  (預設) 允許此功能。
- **卸除式存放裝置**：[封鎖]  防止終端使用者使用外部存放裝置，如裝置的 SD 卡。 [未設定]  (預設) 允許此功能。
- **地理位置**：[封鎖]  防止終端使用者啟用裝置的位置服務。 [未設定]  (預設) 允許此功能。
- **網際網路共用**：[封鎖]  防止裝置共用網際網路連線。 [未設定]  (預設) 允許此功能。
- **重設手機**：[封鎖]  防止終端使用者在裝置上抹除或執行原廠重設。 [未設定]  (預設) 允許此功能。
- **USB 連線**：[封鎖]  防止透過裝置的 USB 連線存取外部存放裝置。 [未設定]  (預設) 允許此功能。 這項設定不會影響 USB 充電。
- **防竊模式** (僅限行動裝置)：[封鎖]  防止終端使用者選取裝置的防竊模式喜好設定。 [未設定]  (預設) 允許此功能。
- **Cortana**：[封鎖]  停用裝置的 Cortana 語音助理。 Cortana 關閉時，使用者仍可搜尋，在裝置上尋找項目。 [未設定]  (預設) 允許 Cortana。
- **錄音** (僅限行動裝置)：[封鎖]  防止終端使用者在裝置上使用裝置錄音機。 [未設定]  (預設) 允許應用程式的錄音功能。
- **修改裝置名稱** (僅限行動裝置)：[封鎖]  防止終端使用者變更裝置名稱。 [未設定]  (預設) 允許此功能。
- **新增佈建套件**：[封鎖]  防止執行階段設定代理程式在裝置上安裝佈建套件。 [未設定]  (預設) 允許此功能。
- **移除佈建套件**：[封鎖]  防止執行階段設定代理程式移除裝置上的佈建套件。 [未設定]  (預設) 允許此功能。
- **裝置探索**：[封鎖]  防止其他裝置找到此裝置。 [未設定]  (預設) 允許此功能。
- **工作切換器** (僅限行動裝置)：[封鎖]  防止在裝置上切換工作。 [未設定]  (預設) 允許此功能。
- **SIM 卡錯誤對話方塊** (僅限行動裝置)：[封鎖]  在沒有偵測到 SIM 卡情況下會顯示於裝置上的錯誤訊息。 [未設定]  (預設) 會顯示錯誤訊息。
- **Ink 工作區** 選擇使用者是否以及如何存取 Ink 工作區。 選項包括：
  - [未設定]  (預設)：開啟 Ink 工作區，並允許使用者在鎖定畫面上方使用它。
  - **在鎖定畫面上停用**：啟用 Ink 工作區，並開啟功能。 但是，使用者無法在鎖定畫面上方存取它。
  - **停用**：停用存取 Ink 工作區。 這會關閉功能。

  [WindowsInkWorkspace 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **自動重新部署**：選擇 [允許]  ，讓具有系統管理權限的使用者能夠在裝置鎖定畫面使用 **CTRL + Win + R** 刪除所有使用者資料和設定。 裝置會自動重新設定並重新註冊以納入管理。 [未設定]  (預設) 會防止此功能。
- **要求使用者在裝置設定期間連線到網路**：選擇 [必要]  ，讓裝置在 Windows 設定期間先連線到網路，再通過 [網路] 頁面。 [未設定]  (預設) 讓使用者通過 [網路] 頁面，即使它不連線到網路。

  此設定會在下一次抹除或重設裝置時生效。 和任何其他 Intune 設定相似，裝置必須向 Intune 註冊並由 Intune 管理才能接收組態設定。 然而一旦註冊並接收原則，然後重設裝置後，便會在下一次 Windows 設定期間時實行設定。

- **直接記憶體存取**：[封鎖]  會防止所有隨插即用 PCI 下游連接埠的直接記憶體存取 (DMA)，直到使用者登入 Windows 為止。 [啟用]  (預設值) 會允許存取 DMA，就算使用者未登入也一樣。

  CSP：[DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- [結束來自工作管理員的處理序]  ：此設定會決定非系統管理員是否可以使用工作管理員結束工作。 [封鎖]  可防止標準使用者 (非系統管理員) 使用 [工作管理員] 來結束裝置上的處理序或工作。 [未設定]  (預設) 可讓標準使用者使用 [工作管理員] 結束處理序或工作。

## <a name="locked-screen-experience"></a>鎖定畫面體驗

- **控制中心通知** (僅限行動裝置)：[封鎖]  防止控制中心通知出現在裝置的鎖定畫面。 [未設定]  (預設) 讓使用者選擇哪些應用程式可在鎖定畫面上顯示通知。

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **鎖定畫面圖片 URL** (僅限 Desktop)：輸入作為 Windows 鎖定畫面桌布使用之 JPG、JPEG 或 PNG 格式圖片的 URL。 例如，輸入 `https://contoso.com/image.png`。 這項設定會鎖定映像，且以後不能變更。
- **使用者可設定的畫面逾時** (僅限行動裝置)：[允許]  讓使用者設定畫面逾時。 [未設定]  (預設) 不提供使用者此選項。

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **鎖定畫面上的 Cortana** (僅限 Desktop)：[封鎖]  會在裝置位於鎖定畫面上時防止使用者與 Cortana 互動。 [未設定]  (預設) 可與 Cortana 互動。

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **鎖定畫面上的快顯通知**：[封鎖]  防止在裝置鎖定畫面上顯示快顯通知。 [未設定]  (預設) 允許這些通知。

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **畫面逾時** (僅限行動裝置)：設定螢幕從鎖定到關閉的持續時間 (秒)。 支援的值為 11-1800。 例如，輸入 `300` 將此逾時設為 5 分鐘。

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

## <a name="messaging"></a>訊息傳送

這些設定使用[傳訊原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging)，它也會列出支援的 Windows 版本。

- **訊息同步**(僅限行動裝置)：[封鎖]  會停用文字訊息的備份及還原，也會停用 Windows 裝置之間的訊息同步。 停用有利於防止資訊儲存在不受組織控制的伺服器上。 [未設定]  (預設) 讓使用者變更這些設定，且可同步其訊息。
- **多媒體訊息** (僅限行動裝置)：[封鎖]  停用裝置的多媒體訊息傳送和接收功能。 就企業而言，使用此原則停用裝置的多媒體訊息，作為稽核或管理需求的一部分。 [未設定]  (預設) 允許傳送和接收多媒體訊息。
- **RCS** (僅限行動裝置)：[封鎖]  停用裝置上的 Rich Communication Services (RCS) 傳送和接收功能。 就企業而言，使用此原則停用裝置的 RCS，作為稽核或管理需求的一部分。 [未設定]  (預設) 允許傳送和接收 RCS。

## <a name="microsoft-edge-browser"></a>Microsoft Edge 瀏覽器

這些設定使用[瀏覽器原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)，它也會列出支援的 Windows 版本。

### <a name="use-microsoft-edge-kiosk-mode"></a>使用 Microsoft Edge kiosk 模式

可用設定會因您選擇的項目而變更。 選項包括：

- [否]  (預設)：Microsoft Edge 並非正在 Kiosk 模式中執行。 您可以使用所有 Microsoft Edge 設定，且可進行變更和設定。
- [數位/互動告示板 (單一應用程式 Kiosk)]  ：篩選 Microsoft Edge 設定，只提供適用於數位/互動告示板 Microsoft Edge Kiosk 模式的設定，用於 Windows 10 單一應用程式 Kiosk。 選擇此設定，以全螢幕方式開啟 URL，並只顯示網站的內容。 [設定數位告示板](https://docs.microsoft.com/windows/configuration/setup-digital-signage)提供此功能的詳細資訊。
- [InPrivate 公開瀏覽 (單一應用程式 Kiosk)]  ：篩選 Microsoft Edge 設定，只提供適用於 InPrivate 公開瀏覽 Microsoft Edge Kiosk 模式的設定，用於 Windows 10 單一應用程式 Kiosk。 執行 Microsoft Edge 的多分頁版本。
- [標準模式 (多應用程式 Kiosk)]  ：篩選 Microsoft Edge 設定，只提供適用於標準 Microsoft Edge Kiosk 模式的設定。 執行具備所有瀏覽功能的 Microsoft Edge 完整版本。
- [公開瀏覽 (多應用程式 Kiosk)]  ：篩選 Microsoft Edge 設定，只提供適用於在 Windows 10 多應用程式 Kiosk 上公開瀏覽的設定。  執行 Microsoft Edge InPrivate 的多分頁版本。

> [!TIP]
> 如需這些選項作用的詳細資訊，請參閱 [Microsoft Edge Kiosk 模式設定類型](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)。

此裝置限制設定檔直接與您使用 [Windows Kiosk 設定](kiosk-settings-windows.md)建立的 Kiosk 設定檔相關。 總括來說：

1. 建立 [Windows Kiosk 設定](kiosk-settings-windows.md)設定檔，來在 Kiosk 模式下執行裝置。 選取 Microsoft Edge 作為應用程式，並在 Kiosk 設定檔中設定 Microsoft Edge Kiosk 模式。
2. 建立本文中描述的裝置限制設定檔，並設定 Microsoft Edge 中允許的特定功能及設定。 請務必選擇和您在 Kiosk 設定檔 ([Windows Kiosk 設定](kiosk-settings-windows.md)) 中所選取項目相同的 Microsoft Edge Kiosk 模式類型。 

    [支援的 Kiosk 模式設定](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode)是良好資源。

> [!IMPORTANT] 
> 請務必將此 Microsoft Edge 設定檔指派給與您 Kiosk 設定檔 ([Windows Kiosk 設定](kiosk-settings-windows.md)) 相同的裝置。

[ConfigureKioskMode CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>[開始] 體驗

- **啟動 Microsoft Edge 並顯示**：選擇 Microsoft Edge 啟動時開啟的頁面。 選項包括：
  - **自訂起始畫面**：輸入起始畫面，例如 `http://www.contoso.com`。 Microsoft Edge 會載入您輸入的起始畫面。
  - **新索引標籤頁**：Microsoft Edge 會載入您在 [新增索引標籤 URL]  設定中輸入的任何內容。
  - **上一個工作階段的頁面**：Microsoft Edge 會載入上一個工作階段的頁面。
  - **本機應用程式設定中的起始網頁**：Microsoft Edge 以作業系統定義的預設起始頁面啟動。

- **允許使用者變更起始頁面**：[是]  (預設) 讓使用者變更起始頁面。 系統管理員可以使用 `EdgeHomepageUrls` 輸入使用者在開啟 Microsoft Edge 時預設看到的起始畫面。 [否]  會封鎖使用者變更起始畫面。
- **允許新索引標籤頁上的 Web 內容**：設定為 [是]  (預設) 時，Microsoft Edge 會開啟 [新增索引標籤 URL]  設定中輸入的 URL。 如果 [新增索引標籤 URL]  設定為空白，Microsoft Edge 會開啟 Microsoft Edge 設定中列出的新索引標籤頁面。 使用者可以變更它。 設定為 [否]  時，Microsoft Edge 會以空白頁開啟新的索引標籤。 使用者無法變更它。
- **新索引標籤 URL**：輸入要在 [新索引標籤] 頁面開啟的 URL。 例如，輸入 `https://www.bing.com` 或 `https://www.contoso.com`。

- **首頁按鈕**：選擇選取 [首頁] 按鈕時會發生什麼事。 選項包括：
  - **起始畫面**：開啟您在 [啟動 Microsoft Edge 並顯示]  設定中選擇的選項
  - **新索引標籤頁**：開啟您在 [新索引標籤 URL]  設定中輸入的 URL。
  - **首頁按鈕 URL**：輸入要開啟的 URL。 例如，輸入 `https://www.bing.com` 或 `https://www.contoso.com`。
  - **隱藏首頁按鈕**：隱藏 [首頁] 按鈕
- **允許使用者變更首頁按鈕**：[是]  讓使用者變更 [首頁] 按鈕。 使用者的變更覆寫任何的系統管理員設定，以 [首頁] 按鈕。 [否]  (預設) 會封鎖使用者變更系統管理員的 [首頁] 按鈕設定方式。
- **顯示首次執行體驗頁面** (僅限行動裝置)：[是]  (預設) 會顯示 Microsoft Edge 第一次使用的簡介頁面。 [否]  會在您第一次執行 Microsoft Edge 時阻止顯示簡介頁面。 這項功能可讓企業 (如註冊零輸出設定的組織) 封鎖這個頁面。
- **首次執行體驗 URL 清單位置** (僅限 Windows 10 行動裝置)：輸入指向包含第一次執行頁面 URL 之 XML 檔案的 URL。 例如，輸入 `https://www.contoso.com/sites.xml`。

- [在閒置時間後重新整理瀏覽器]  ：輸入閒置時間數 (分鐘)，在經過此時時間後便會重新整理瀏覽器，範圍介於 0 到 1440 分鐘。 預設為 `5` 分鐘。 當設為 `0` (零) 時，瀏覽器便不會在閒置後重新整理。

  此設定只有在於 [InPrivate 公開瀏覽 (單一應用程式 Kiosk)](#use-microsoft-edge-kiosk-mode) 中執行時才可使用。

- **允許快顯視窗** (僅限 Desktop)：[是]  (預設) 允許網頁瀏覽器顯示快顯視窗。 [否]  防止瀏覽器顯示快顯視窗。
- **將內部網路流量傳送到 Internet Explorer** (僅限 Desktop)：[是]  可讓使用者在 Internet Explorer 而非 Microsoft Edge 中開啟內部網路網站。 這項設定是針對回溯相容性。 [否]  (預設) 允許使用者使用 Microsoft Edge。
- **企業模式網站清單位置** (僅限 Desktop)：輸入指向 XML 檔案的 URL，此檔案包含以企業模式開啟的網站清單。 使用者無法變更此清單。 例如，輸入 `https://www.contoso.com/sites.xml`。
- **在 Internet Explorer 中開啟網站時出現的訊息**：使用此設定將 Microsoft Edge 設定為在 Internet Explorer 11 中開啟網站之前顯示通知。 選項包括：
  - **不要顯示訊息**：使用作業系統的預設行為，這可能不會顯示訊息。
  - **顯示網站在 Internet Explorer 11 中開啟的訊息**：在 IE 中開啟網站時顯示訊息。 在 IE 中開啟網站。 
  - **顯示訊息，同時顯示在 Microsoft Edge 中開啟網站的選項**：在 Microsoft Edge 中開啟網站時顯示訊息。 此訊息包含**繼續使用 Microsoft Edge** 連結，因此使用者可以選擇 Microsoft Edge 而非 IE。

  > [!IMPORTANT]
  > 此設定要求您使用 [企業模式網站清單位置]  設定、[將內部網路流量傳送到 Internet Explorer]  設定，或兩者都使用。

- **允許 Microsoft 相容性清單**：[是]  (預設) 允許使用 Microsoft 相容性清單。 [否]  防止 Microsoft Edge 中的 Microsoft 相容性清單。 Microsoft 的此清單可協助 Microsoft Edge 正確顯示具有已知的相容性問題的網站。
- **預先載入起始畫面與新索引標籤頁**：[是]  (預設) 會使用作業系統的預設行為，這可能要預先載入這些頁面。 預先載入可將啟動 Microsoft Edge 的時間降至最低，並載入新的索引標籤。 [否]  會防止 Microsoft Edge 預先載入起始畫面與新索引標籤頁面。
- **預先啟動起始畫面與新索引標籤頁**：[是]  (預設) 會使用作業系統的預設行為，這可能要預先啟動這些頁面。 預先啟動有助於 Microsoft Edge 的效能，並將啟動 Microsoft Edge 所需的時間降至最低。 [否]  會防止 Microsoft Edge 預先啟動起始畫面與新索引標籤頁面。

### <a name="favorites-and-search"></a>我的最愛和搜尋

- **顯示我的最愛列**：選擇在任何 Microsoft Edge 頁面上 [我的最愛] 列的內容。 選項包括：
  - **在 [開始] 和 [新索引標籤] 頁面上**：當 Microsoft Edge 啟動時，在所有的索引標籤頁面中顯示 [我的最愛] 列。 終端使用者無法變更此設定。
  - **在所有頁面上**：在所有頁面上顯示 [我的最愛] 列。 終端使用者無法變更此設定。
  - **隱藏**：在所有頁面上隱藏 [我的最愛] 列。 終端使用者無法變更此設定。
- **允許變更我的最愛**：[是]  (預設) 會使用作業系統預設值，讓使用者變更清單。 [否]  防止終端使用者新增、匯入、排序或編輯 [我的最愛] 清單。
  - **我的最愛清單**：將 URL 清單新增至我的最愛檔案。 例如：新增 `http://contoso.com/favorites.html`。
- **在 Microsoft 瀏覽器之間同步我的最愛** (僅限 Desktop)：[是]  可強制 Windows 同步 Internet Explorer 和 Microsoft Edge 之我的最愛。 在瀏覽器之間共用對我的最愛的新增、刪除、修改及順序變更。  [否]  (預設) 會使用作業系統預設值，這可讓使用者選擇在瀏覽器間同步我的最愛。
- **預設搜尋引擎**：選擇裝置上的預設搜尋引擎。 使用者可以隨時變更此值。 選項包括：
  - 用戶端 Microsoft Edge 設定中的搜尋引擎
  - Bing
  - Google
  - Yahoo
  - 自訂值：在 **OpenSearch Xml URL** 中，至少輸入 XML 檔案包含簡短名稱的 HTTPS URL 和搜尋引擎的 URL。 例如，輸入 `https://www.contoso.com/opensearch.xml`。
- **顯示搜尋建議**：[是]  (預設) 會在您於網址列中鍵入搜尋片語時，讓搜尋引擎建議網站。 [否]  會防止此功能。
- [允許變更搜尋引擎]  ：[是]  (預設) 可讓使用者在 Microsoft Edge 中新增新的搜尋引擎，或是變更預設搜尋引擎。 選擇 [否]  以防止使用者自訂搜尋引擎。

  此設定只有在於[標準模式 (多應用程式 Kiosk)](#use-microsoft-edge-kiosk-mode) 中執行時才可使用。

### <a name="privacy-and-security"></a>隱私權和安全性

- **允許 InPrivate 瀏覽**：[是]  (預設) 允許在 Microsoft Edge 中使用 InPrivate 瀏覽。 關閉所有 InPrivate 索引標籤之後，Microsoft Edge 會刪除裝置的瀏覽資料。 [否]  可防止終端使用者開啟 InPrivate 瀏覽工作階段。
- **儲存瀏覽歷程記錄**：[是]  (預設) 允許儲存 Microsoft Edge 的瀏覽歷程記錄。 [否]  防止儲存瀏覽歷程記錄。
- **在結束時清除瀏覽資料** (僅限 Desktop)：[是]  會在使用者結束 Microsoft Edge 時，清除歷程記錄和瀏覽資料。 [否]  (預設) 會使用作業系統預設值，這可能會快取瀏覽資料。
- **在使用者裝置之間同步處理瀏覽器設定**：選擇在裝置之間同步處理瀏覽器設定的方式。 選項包括：
  - **允許**：允許在使用者裝置之間同步處理 Microsoft Edge 瀏覽器設定
  - **封鎖並啟用使用者覆寫**：防止在使用者裝置之間同步處理 Microsoft Edge 瀏覽器設定。 使用者可以覆寫此設定。
  - **封鎖**：封鎖在使用者裝置之間同步 Microsoft Edge 瀏覽器設定。 使用者無法覆寫此設定。

選取 [禁止並允許使用者覆寫] 後，使用者可以覆寫管理員指定。

- **允許密碼管理員**：[是]  (預設) 允許 Microsoft Edge 自動使用密碼管理員，讓使用者儲存及管理裝置上的密碼。 [否]  防止 Microsoft Edge 使用密碼管理員。
- **Cookis**：選擇網頁瀏覽器上處理 cookie 的方式。 選項包括：
  - **允許**：Cookie 會儲存在裝置上。
  - **封鎖所有 Cookie**：Cookie 不會儲存在裝置上。
  - **只封鎖第三方 Cookie**：協力廠商或合作對象 Cookie 不會儲存在裝置上。
- **允許表單自動填滿**：[是]  (預設) 讓使用者變更瀏覽器的自動完成設定，自動填入表單欄位。 [否]  會停用 Microsoft Edge 的自動填寫功能。
- **傳送不追蹤標頭**：[是]  會向要求追蹤資訊的網站傳送不追蹤標頭 (建議選項)。 [否]  (預設) 不會傳送讓網站追蹤使用者的標頭。 使用者可以設定。
- **顯示 WebRTC localhost IP 位址**：[是]  (預設) 會在使用此通訊協定通話時顯示使用者的 localhost IP 位址。 [否]  防止顯示使用者的 localhost IP 位址。 
- **允許收集動態磚資料**：[是]  (預設) 讓 Microsoft Edge 收集釘選到 [開始] 功能表的動態磚資訊。 [否]  防止收集這項資訊，這可能會讓使用者體驗受限。
- **使用者可以覆寫憑證錯誤**：[是]  (預設) 可讓使用者存取有安全通訊端層/傳輸層安全性 (SSL/TLS) 錯誤的網站。 [否]  (建議項目，可提高安全性) 防止使用者存取有 SSL 或 TLS 錯誤的網站。

### <a name="additional"></a>Additional

- **允許 Microsoft Edge 瀏覽器** (僅限行動裝置)：[是]  (預設) 允許在行動裝置上使用 Microsoft Edge 網頁瀏覽器。 [否]  可防止在裝置上使用 Microsoft Edge。 如果您選擇 [否]  ，則其他的個別設定僅適用於 Desktop。
- **允許網址列下拉式清單**：[是]  (預設) 讓 Microsoft Edge 顯示網址列下拉式建議清單。 [否]  可阻止 Microsoft Edge 在您鍵入時，於下拉式清單中顯示建議清單。 設定為 [否]  時，您：
  - 協助將 Microsoft Edge 與 Microsoft 服務之間的網路頻寬降到最低。
  - 停用 Microsoft Edge > [設定] 中的 [在我輸入的同時顯示搜尋與網站建議]  。
- **允許全螢幕模式**：[是]  (預設) 允許 Microsoft Edge 使用全螢幕模式，這樣會只顯示 Web 內容並隱藏 Microsoft Edge UI。 [否]  防止 Microsoft Edge 的全螢幕模式。
- **允許關於旗標頁面**：[是]  (預設) 會使用作業系統預設值，這會允許存取 `about:flags` 頁面。 `about:flags` 頁面可讓使用者變更開發人員設定並啟用實驗功能。 [否]  防止終端使用者存取 Microsoft Edge 的 `about:flags` 頁面。
- **允許開發人員工具**：[是]  (預設) 讓使用者以 F12 開發人員工具來建置和偵錯預設網頁。 [否]  防止終端使用者使用 F12 開發人員工具。
- **允許 JavaScript**：[是]  (預設) 允許在 Microsoft Edge 瀏覽器中執行 JavaScript 等指令碼。 [否]  防止在瀏覽器中執行 Java 指令碼。
- **使用者可以安裝延伸模組**：[是]  (預設) 允許終端使用者在裝置上安裝 Microsoft Edge 延伸模組。 [否]  會防止安裝。
- **允許側載開發人員延伸模組**：[是]  (預設) 會使用作業系統預設，這會允許側載。 側載會安裝並執行未經驗證的延伸模組。 [否]  防止 Microsoft Edge使用 [載入延伸模組]  功能側載。 它不會防止使用 PowerShell 等其他方式側載延伸模組。
- **必要的延伸模組**：選擇 Microsoft Edge 中的終端使用者無法關閉哪些擴充功能。 輸入套件系列名稱，然後選取 [新增]  。 [尋找套件系列名稱 (PFN)](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn) 會提供一些指引。

  您也可以**匯入** CSV 檔案，其中包含套件系列名稱。 或者，[匯出]  您輸入的套件系列名稱。

## <a name="network-proxy"></a>網路 Proxy

這些設定使用 [NetworkProxy 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp)，它也會列出支援的 Windows 版本。

- **自動偵測 Proxy 設定**：[封鎖]  會停用裝置自動偵測 Proxy 自動設定 (PAC) 指令碼。 [未設定]  (預設) 會啟用此設定。 啟用時，裝置會嘗試尋找 PAC 指令碼的路徑。
- **使用 Proxy 指令碼**：選擇 [允許]  輸入 PAC 指令碼路徑以設定 Proxy 伺服器。 [未設定]  (預設) 不讓您輸入 PAC 指令碼的 URL。
  - **設定指令碼位址 URL**：輸入您想要用於設定 Proxy 伺服器的 PAC 指令碼 URL。
- **使用手動 Proxy 伺服器**：選擇 [允許]  手動輸入 Proxy 伺服器的名稱或 IP 位址及 TCP 通訊埠號碼。 [未設定]  (預設) 不讓您手動輸入 Proxy 伺服器的詳細資料。
  - **位址**：輸入 Proxy 伺服器的名稱或 IP 位址。
  - **連接埠號碼**：輸入 Proxy 伺服器的連接埠號碼。
  - **Proxy 例外狀況**：輸入任何不得使用 Proxy 伺服器的 URL。 請使用分號來分隔每個項目。
  - **為本機位址略過 Proxy 伺服器**： **[未設定]** (預設) 防止在內部網路使用本機位址的 Proxy 伺服器。 **允許** 使用本機位址的 Proxy 伺服器。

## <a name="password"></a>密碼

這些設定使用 [DeviceLock 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)，它也會列出支援的 Windows 版本。

- **密碼**：**要求**使用者輸入密碼才可存取該裝置。 [未設定]  (預設) 允許不用密碼存取裝置。 僅適用于本機帳戶。 網域帳戶密碼仍然由 Active Directory （AD）和 Azure AD 設定。

  - **需要的密碼類型**：選擇密碼類型。 選項包括：
    - [未設定]  ：密碼可以包含數字和字母。
    - [數值]  ：密碼只能是數字。
    - [英數字元]  ：密碼必須混合數字和字母。
  - [密碼長度下限]  ：輸入 4-16 個所需的最少數字或字元。 例如，輸入 `6` 表示密碼長度至少需要六個字元。
  
    > [!IMPORTANT]
    > 在 Windows 桌面上變更密碼需求時，使用者會在下次登入時受到影響，因為此時裝置會從閒置變成作用中。 系統仍會提示密碼符合需求的使用者變更其密碼。
    
  - **登入失敗幾次後即抹除裝置**：輸入要抹除裝置前允許的驗證失敗次數，最多為 11。 您輸入的有效數字視版本而定。 [DeviceLock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts)會列出支援的值。 `0` (零) 可停用裝置抹除功能。

    此設定因版本不同也會有不同影響。 如需此設定的特定詳細資訊，請參閱 [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) \(英文\)。

  - **在停止活動最少幾分鐘後鎖定螢幕**：輸入裝置必須處於閒置狀態多久的時間，才會鎖住螢幕。
  - **密碼到期 (天數)** ：輸入裝置必須變更密碼的天數，從 1 到 365。 例如，輸入 `90`，密碼會在 90 天後到期。
  - **不得重複使用以前用過的密碼**：輸入不得重複使用以前用過的密碼次數，從 1 到 24。 列如，輸入 `5` 讓使用者無法將新密碼設定為其目前密碼或之前使用過的四個密碼之一。
  - **裝置從閒置狀態回復時需要密碼** (僅限行動裝置)：選擇 [必要]  讓使用者必須輸入密碼才能解除鎖定閒置的裝置。 [未設定]  (預設) 當裝置從閒置狀態恢復時不需要 PIN 或密碼。
  - [簡單密碼]  ：設定為 [封鎖]  讓使用者無法建立簡單的密碼，例如 `1234` 或 `1111`。 設定為 [未設定]  (預設) 讓使用者建立類似 `1234` 或 `1111` 的密碼。 這項設定也會允許或封鎖使用 Windows 圖片密碼。
- [在 AADJ 期間自動加密]  ：[封鎖]  可防止當裝置加入 Azure AD，並準備裝置進行初次使用時啟動自動 BitLocker 裝置加密。 [未設定]  (預設) 會使用作業系統預設，該預設可能會啟用加密。 請參閱 [BitLocker 裝置加密](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption)。

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- [聯邦資訊處理標準 (FIPS) 原則]  ：[允許]  會使用聯邦資訊處理標準 (FIPS) 原則，該標準是美國政府針對加密、雜湊和簽署提出的標準。 [未設定]  (預設) 會使用作業系統預設值，而不使用 FIPS。

  [Cryptography/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- [Windows Hello 裝置驗證]  ：[允許]  使用者使用 Windows Hello 隨附裝置，例如手機、健身手環或 IoT 裝置登入 Windows 10 電腦。 [未設定]  (預設) 會使用作業系統預設，該預設可能會防止 Windows Hello 隨附裝置向 Windows 驗證。

  [Authentication/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- [Web 登入]  ：啟用非 ADFS (Active Directory 同盟服務) 同盟提供者的 Windows 登入支援，例如安全性聲明標記語言 (SAML)。 SAML 使用安全權杖，提供網頁瀏覽器單一登入 (SSO) 體驗。 選項包括：

  - [未設定]  (預設)：使用裝置上的作業系統預設。
  - [啟用]  ：啟用 Web 認證提供者進行登入。
  - [停用]  ：停用 Web 認證提供者進行登入。

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- [慣用的 Azure AD 租用戶網域]  ：輸入您 Azure AD 組織中現有的網域名稱。 當使用者在此網域登入時，他們便不需要鍵入網域名稱。 例如，輸入 `contoso.com`。 `contoso.com` 網域中的使用者可以使用其使用者名稱登入，例如 `abby`，而非 `abby@contoso.com`。

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>個別應用程式的隱私權例外狀況

您可以新增應用程式，其隱私權行為應與「預設隱私權」中所定義的不同。

- **套件名稱**：應用程式套件系列名稱。
- **應用程式名稱**：應用程式的名稱。

### <a name="exceptions"></a>例外狀況

- **帳戶資訊**：定義此應用程式能否存取使用者名稱、圖片及其他連絡人資訊。
- **背景應用程式**：定義此應用程式能否在背景執行。
- **行事曆**：定義此應用程式能否存取行事曆。
- **通話記錄**：定義此應用程式能否存取我的通話記錄。
- **相機**：定義此應用程式能否存取網路攝影機。
- **連絡人**：定義此應用程式能否存取連絡人。
- **電子郵件**：定義此應用程式能否存取及傳送電子郵件。
- **位置**：定義此應用程式能否存取位置資訊。
- **訊息中心**：定義此應用程式能否讀取或傳送文字或 MMS 訊息。
- **麥克風**：定義此應用程式能否使用麥克風。
- **動作**：定義此應用程式能否存取裝置動作資訊。
- **通知**：定義此應用程式能否存取通知。
- **電話**：定義此應用程式能否存取手機。
- **無線電**：有些應用程式會在您的裝置上使用無線電波 (例如，藍牙) 來傳送及接收資料，因此必須開啟或關閉這些無線電波。 定義此應用程式能否控制這些無線電波。
- **工作**：定義此應用程式能否存取您的工作。
- [受信任的裝置]  ：若此應用程式可使用受信任的裝置，請選擇此選項。 受信任裝置是您已連線的硬體，或隨附於裝置的硬體。 例如，將電視、投影機等作為信任的裝置使用。
- **意見反應與診斷**：定義此應用程式能否存取診斷資訊。
- **與裝置同步** - 選擇此應用程式是否自動與未和該裝置直接配對的無線裝置共用及同步資訊。

## <a name="personalization"></a>個人化

這些設定使用[個人化原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp)，它也會列出支援的 Windows 版本。

- **桌面背景圖片 URL** (僅限 Desktop)：輸入要作為 Windows 桌面桌布使用之 .jpg、.jpeg 或 .png 格式圖片的 URL。 使用者無法變更此圖片。 例如，輸入 `https://contoso.com/logo.png`。

## <a name="printer"></a>印表機

- **印表機**：已新增的本機印表機清單。
- **預設印表機**：設定預設印表機。
- **使用者存取新增新印表機**：允許或封鎖使用本機印表機。

## <a name="privacy"></a>隱私權

這些設定使用[隱私權原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy)，它也會列出支援的 Windows 版本。

- **輸入個人化**：[封鎖]  可防止使用語音聽寫以及和 Cortana 及其他使用 Microsoft 雲端式語音辨識的應用程式通話。 此功能已停用，且使用者不能啟用線上語音辨識使用設定。 [未設定]  (預設) 可讓使用者選擇。 如果您允許這些服務，Microsoft 可能會收集語音資料來 改善服務。
- **自動接受配對及隱私權使用者同意提示**：選擇 [允許]  讓 Windows 在執行應用程式時自動接受配對及隱私權同意訊息。 [未設定]  (預設) 會在開啟應用程式時，防止自動接受配對及隱私權使用者同意視窗。
- **發佈使用者活動**：[封鎖]  會防止共用體驗以及在活動摘要中探索最近使用的資源。 [未設定]  (預設) 啟用這項功能讓應用程式可以發佈終端使用者活動。
- **僅限本機活動**： [封鎖]  會防止共用體驗，以及僅根據本機活動，在工作切換器中探索最近使用的資源。 [未設定]  (預設) 會啟用此設定。

您可以設定可供裝置上所有應用程式存取的資訊。 您也可以使用**個別應用程式隱私權例外狀況**，以個別應用程式為基礎來定義例外狀況。

### <a name="exceptions"></a>例外狀況

- **帳戶資訊**：定義此應用程式能否存取使用者名稱、圖片及其他連絡人資訊。
- **背景應用程式**：定義此應用程式能否在背景執行。
- **行事曆**：定義此應用程式能否存取行事曆。
- **通話記錄**：定義此應用程式能否存取我的通話記錄。
- **相機**：定義此應用程式能否存取網路攝影機。
- **連絡人**：定義此應用程式能否存取連絡人。
- **電子郵件**：定義此應用程式能否存取及傳送電子郵件。
- **位置**：定義此應用程式能否存取位置資訊。
- **訊息中心**：定義此應用程式能否讀取或傳送文字或 MMS 訊息。
- **麥克風**：定義此應用程式能否使用麥克風。
- **動作**：定義此應用程式能否存取裝置動作資訊。
- **通知**：定義此應用程式能否存取通知。
- **電話**：定義此應用程式能否存取手機。
- **無線電**：有些應用程式會在您的裝置上使用無線電波 (例如，藍牙) 來傳送及接收資料，因此必須開啟或關閉這些無線電波。 定義此應用程式能否控制這些無線電波。
- **工作**：定義此應用程式能否存取您的工作。
- [受信任的裝置]  ：若此應用程式可使用受信任的裝置，請選擇此選項。 受信任裝置是您已連線的硬體，或隨附於裝置的硬體。 例如，將電視、投影機等作為信任的裝置使用。
- **意見反應與診斷**：選擇此應用程式能否存取診斷資訊。
- **與裝置同步** - 定義此應用程式能否自動與未和此電腦、平板電腦或手機直接配對的無線裝置共用及同步資訊。

## <a name="projection"></a>投影

這些設定使用 [WirelessDisplay 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay)，它也會列出支援的 Windows 版本。

- **來自無線顯示器接收器的使用者輸入**：[封鎖]  防止來自無線顯示器接收器的使用者輸入。 [未設定]  (預設) 讓無線顯示器將鍵盤、滑鼠、畫筆和觸控輸入傳送回來源裝置。
- **投影到此 PC**：[封鎖]  阻止其他裝置尋找投影裝置。 [未設定]  (預設) 讓裝置成為可探索的，並可以投影到鎖定畫面上方的裝置。
- **要求提供 PIN 以進行配對**：選擇 [必要]  於連線至投影裝置時一律提示要求 PIN。 [未設定]  (預設) 不需要 PIN 碼與投影裝置的裝置配對。

## <a name="reporting-and-telemetry"></a>報告與遙測

- **共用使用方式資料**：選擇提交診斷資料的層級。 選項包括：
  - [未設定]  ：不共用任何資料。
  - [安全性]  ：讓 Windows 更安全的必要資訊，包括已連線使用者體驗與遙測元件的設定、惡意軟體移除工具及 Windows Defender 的相關資料。
  - [基本]  ：基本裝置資訊，包括品質相關資料、應用程式相容性、應用程式使用量資料和安全性層級的資料。
  - [增強]  ：額外的見解，包括：Windows、Windows Server、System Center 和應用程式的使用方式、執行方式、進階的可靠性資料，以及基本和安全性層級的資料。
  - [完整]  ：找出及協助修正問題的所有必要資料，加上安全性、基本和增強層級的資料。

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **將Microsoft Edge瀏覽數據發送到Microsoft 365 Analytics** ：若要使用這項功能，請將 [共用使用方式資料]  設定為 [增強]  或是 [完整]  。 此功能控制 Microsoft Edge 針對具有設定商業識別碼的企業裝置傳送至 Microsoft 365 Analytics 的資料。 選項包括：
  - [未設定]  ：會使用 OS 預設值，這可能不會傳送任何瀏覽歷程記錄資料
  - **僅傳送內部網路資料**：允許系統管理員傳送內部網路資料歷程記錄
  - **僅傳送網際網路資料**：允許系統管理員傳送網際網路資料歷程記錄
  - **傳送內部網路與網際網路資料**：允許系統管理員傳送內部網路與網際網路資料歷程記錄

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **遙測 Proxy 伺服器**：輸入要用來轉送「已連線使用者體驗與遙測」要求 (使用安全通訊端層 (SSL) 連線) 之 Proxy 伺服器的完整網域名稱 (FQDN) 或 IP 位址。 此設定的格式是*伺服器*:*連接埠*。 若具名 Proxy 失敗，或若啟用此原則時未輸入 Proxy，則不傳送已連線使用者體驗與遙測資料，並將此資料留在本機裝置上。

  範例格式：

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

按一下 [確定]  以儲存您的變更。

## <a name="search"></a>搜尋

這些設定使用[搜尋原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)，它也會列出支援的 Windows 版本。 

- **安全搜尋 (僅限行動裝置)** ：控制 Cortana 在搜尋結果中篩選成人內容的方式。 選項包括：
  - **使用者定義**：讓終端使用者選擇他們自己的設定。
  - **嚴格**：針對成人內容進行最高程度的篩選。
  - **中**：針對成人內容進行中等程度的篩選。 不篩選有效的搜尋結果。
- **在 [搜尋] 中顯示網頁搜尋結果**：設為 [封鎖]  時，使用者無法搜尋，且不會在 [搜尋] 中顯示網頁搜尋結果。 [未設定]  (預設) 讓使用者搜尋網頁，並在裝置上顯示結果。

## <a name="start"></a>開始

這些設定使用[啟動原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start)，它也會列出支援的 Windows 版本。  

- **[開始] 功能表配置**：覆寫預設的 [開始] 配置以及自訂桌面裝置的 [開始] 功能表。 上傳包含您自訂項目的 XML 檔案，包括應用程式的列出順序等等。 使用者無法變更您輸入的 [開始] 功能表配置。
- **將網站釘選為 [開始] 功能表中的磚**：從 Microsoft Edge 匯入影像，作為電腦裝置 Windows [開始] 功能表中的連結顯示。
- **從工作列取消釘選應用程式**：[封鎖]  會防止使用者從工作列取消釘選應用程式。 [未設定]  (預設) 允許使用者從工作列取消釘選應用程式。
- **快速切換使用者**：[封鎖]  可防止同時登入的使用者未經登出即切換使用者。 [未設定]  (預設) 會在使用者磚顯示 [切換使用者]  。
- **最常使用的應用程式**：[封鎖]  會隱藏最常使用的應用程式，使其不顯示在 [開始] 功能表中。 它也會停用「設定」應用程式中相對應的切換。 [未設定]  (預設) 顯示最常使用的應用程式。
- **最近新增的應用程式**：[封鎖]  會隱藏最近新增的應用程式，使其不顯示在 [開始] 功能表中。 它也會停用「設定」應用程式中相對應的切換。 [未設定]  (預設) 在 [開始] 功能表中顯示最近新增的應用程式。
- **開始畫面模式**：選擇開始畫面的顯示方式。 選項包括：
  - **使用者定義**：不強制開始畫面的大小。 使用者可以設定大小。
  - **全螢幕**：強制開始畫面的全螢幕大小。
  - **非全螢幕**：強制開始畫面的非全螢幕大小。
- **捷徑清單中最近開啟的項目**：[封鎖]  會隱藏最近的捷徑清單，使其不顯示在 [開始] 功能表和工作列中。 它也會停用「設定」應用程式中相對應的切換。 [未設定]  (預設) 會在捷徑清單中顯示最近開啟的項目。
- **應用程式清單**：選擇如何顯示所有的應用程式清單。 選項包括：
  - **使用者定義**：不強制任何設定。 使用者選擇如何顯示裝置的應用程式清單。
  - **摺疊**：隱藏所有應用程式清單。
  - **摺疊及停用「設定」應用程式**：隱藏所有應用程式清單，並停用設定應用程式的 [在開始功能表中顯示應用程式清單]  。
  - **移除且停用「設定」應用程式**：隱藏所有應用程式清單、移除所有應用程式按鈕，並停用設定應用程式的 [在開始功能表中顯示應用程式清單]  。
- **電源按鈕**：[封鎖]  會隱藏 [電源] 按鈕，使其不顯示在 [開始] 功能表中。 [未設定]  (預設) 會顯示 [電源] 按鈕。
- **使用者磚**：[封鎖]  會隱藏使用者磚，使其不顯示在 [開始] 功能表中。 [未設定]  (預設) 會顯示使用者磚，並設定下列設定：
  - **鎖定**：[封鎖]  會隱藏 [鎖定]  選項，使其不顯示在 [開始] 功能表的使用者磚中。 [未設定]  (預設) 會顯示 [鎖定]  選項。
  - [登出]  ：[封鎖]  會隱藏 [登出]  選項，使其不顯示在 [開始] 功能表的使用者磚中。 [未設定]  (預設) 會顯示 [登出]  選項。
- **關機**：[封鎖]  會隱藏 [更新並關機]  和 [關機]  選項，使其不顯示在 [開始] 功能表的 [電源] 按鈕中。 [未設定]  (預設) 會顯示這些選項。
- **睡眠**：[封鎖]  會隱藏 [睡眠]  選項，使其不顯示在 [開始] 功能表的 [電源] 按鈕中。 [未設定]  (預設) 會顯示此選項。
- **休眠**：[封鎖]  會隱藏 [休眠]  選項，使其不顯示在 [開始] 功能表的 [電源] 按鈕中。 [未設定]  (預設) 會顯示此選項。
- **切換帳戶**：[封鎖]  會隱藏 [切換帳戶]  選項，使其不顯示在 [開始] 功能表的使用者磚中。 [未設定]  (預設) 會顯示此選項。
- []**重新啟動選項**：[封鎖]  會隱藏 [更新並重新啟動]  和 [重新啟動]  選項，使其不顯示在 [開始] 功能表的 [電源] 按鈕中。 [未設定]  (預設) 會顯示這些選項。
- **[開始] 上的 [文件]** ：隱藏或顯示 Windows [開始] 功能表中的 [文件] 資料夾。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- **[開始] 上的 [下載]** ：隱藏或顯示 Windows [開始] 功能表中的 [下載] 資料夾。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- [] **[開始] 上的 [檔案總管]** ：隱藏或顯示 Windows [開始] 功能表中的 [檔案總管]。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- [] **[開始] 上的 HomeGroup**：隱藏或顯示 Windows [開始] 功能表中的 HomeGroup 捷徑。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- **[開始] 上的 [音樂]** ：隱藏或顯示 Windows [開始] 功能表中的 [音樂] 資料夾。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- [] **[開始] 上的 [網路]** ：隱藏或顯示 Windows [開始] 功能表中的 [網路]。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- [[開始] 上的 [個人] 資料夾]  ：隱藏或顯示 Windows [開始] 功能表中的 [個人] 資料夾。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- **[開始] 上的 [圖片]** ：隱藏或顯示 Windows [開始] 功能表中的 [圖片] 資料夾。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- [[開始] 上的 [設定]]  ：隱藏或顯示 Windows [開始] 功能表中的設定捷徑。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。
- **[開始] 上的 [影片]** ：隱藏或顯示 Windows [開始] 功能表中的 [影片] 資料夾。 選項包括：
  - [未設定]  (預設)：不強制任何設定。 使用者選擇顯示或隱藏捷徑。
  - [隱藏]  ：隱藏捷徑，並停用設定應用程式的設定。
  - [顯示]  ：顯示捷徑，並停用設定應用程式的設定。

## <a name="windows-defender-smart-screen"></a>Windows Defender SmartScreen 篩選工具

- []**適用於 Microsoft Edge 的 SmartScreen**：[必要]  會關閉 Windows Defender SmartScreen，並防止使用者開啟它。 [未設定]  (預設) 開啟 SmartScreen。 可協助保護使用者免受潛在威脅，並防止使用者關閉它。

  Microsoft Edge 使用 Windows Defender SmartScreen (已開啟) 保護使用者免於潛在的網路釣魚詐騙和惡意軟體攻擊。

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- []**惡意網站存取**：[封鎖]  防止使用者略過 Windows Defender SmartScreen 篩選工具警告，並阻止他們進入網站。 [未設定]  (預設) 可讓使用者略過警告，繼續前往網站。

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- []**未經驗證的檔案下載**：[封鎖]  會防止使用者略過 Windows Defender SmartScreen 篩選工具警告，並阻止他們下載未經驗證的檔案。 [未設定]  (預設) 可讓使用者略過警告，繼續下載未經驗證的檔案。

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Windows 焦點

這些設定使用[體驗原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)，它也會列出支援的 Windows 版本。

- []**Windows 焦點**：[封鎖]  會關閉鎖定畫面、Windows 提示、Microsoft 消費者功能，以及其他相關功能的 Windows 焦點。 如果您的目標是要將裝置網路流量降到最低，請將此設為 [封鎖]  。 [未設定]  (預設) 允許 Windows 焦點功能，並可由終端使用者控制。 啟用時，您也可以允許或封鎖下列設定：

  - []**鎖定畫面上的 Windows 焦點**：[封鎖]  阻止 Windows 焦點在裝置鎖定畫面上顯示資訊。 [未設定]  (預設) 會啟用此設定。
  - []**Windows 焦點中的第三方建議**：[封鎖]  阻止 Windows 焦點建議不是由 Microsoft 發佈的內容。 [未設定]  (預設) 允許來自 Windows 焦點功能 (例如鎖定畫面焦點、[開始] 功能表中所建議應用程式及 Windows 提示) 中協力廠商軟體發行者的應用程式及內容建議。
  - []**消費者功能**：[封鎖]  會關閉通常僅供消費者使用的體驗，例如開始建議、成員資格通知、應用程式安裝後的全新體驗及重新導向磚。 [未設定]  (預設) 可允許這些功能。
  - []**Windows 提示**：[封鎖]  會停用快顯的 Windows 提示。 [未設定]  (預設) 允許顯示 Windows 提示。
  - []**控制中心的 Windows 焦點**：[封鎖]  防止控制中心顯示 Windows 焦點通知。 [未設定]  (預設) 可能會在控制中心顯示通知，建議可協助使用者在 Windows 提高生產力的應用程式或功能。
  - []**Windows Spotlight 個人化**：[封鎖]  防止 Windows 使用診斷資料為使用者提供自訂的體驗。 [未設定]  (預設) 可讓 Microsoft 使用診斷資料提供個人化的建議、提示，並針對使用者需求提供量身打造的 Windows。
  - []**Windows 歡迎使用功能**：[封鎖]  會關閉 Windows 焦點的 Windows 歡迎使用功能。 當 Windows 及其應用程式有更新和變更時，不會顯示 Windows 歡迎使用功能。 [未設定]  (預設) 允許 Windows 歡迎使用功能向使用者顯示新功能或更新功能的資訊。

## <a name="microsoft-defender-antivirus"></a>Microsoft Defender 防毒軟體

這些設定使用 [Defender 原則 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)，它也會列出支援的 Windows 版本。

- **即時監視**：[啟用]  可關閉即時掃描惡意程式碼、間諜軟體和其他垃圾軟體。 [未設定]  (預設) 允許此功能。

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **行為監視**：[啟用]  會關閉 Defender 在裝置上檢查某些已知模式的可疑活動。 [未設定]  (預設) 允許 Windows Defender 行為監視。

  [Defender/AllowBehaviorMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **網路檢查系統 (NIS)** ：NIS 可協助保護裝置免於遭受網路型入侵。 它會使用 Microsoft Endpoint Protection 中心提供之已知弱點的病毒碼，協助偵測及阻擋惡意流量。

  [未設定]  (預設) 會停用此功能。 使用者不會被封鎖而無法連接到已知的弱點。 當設定為 [**啟用**] 時，會開啟網路保護和網路封鎖，且使用者無法將其關閉。 使用者遭到封鎖而無法連接到已知的弱點。

  [Defender/EnableNetworkProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **掃描所有下載**： [**未設定**] （預設）會掃描從網際網路下載的所有檔案。 當設定為 [**啟用**] 時，就會停用這項功能。 因此，Defender 不會掃描所有下載的網際網路檔案。

  [Defender/AllowIOAVProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **掃描 Microsoft Web 瀏覽器中所載入的指令碼**：  (預設) 讓 Defender 掃描 Internet Explorer 中所用的指令碼。 [啟用]  可防止此掃描。

  [Defender/AllowScriptScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- []**Defender 的使用者存取**：[封鎖]  會向終端使用者隱藏 Windows Defender 使用者介面。 也會隱藏所有 Windows Defender 通知。 [未設定]  (預設) 允許使用者存取 Windows Defender UI。 變更此設定後，要在使用者電腦下次重新啟動時才會生效。

  [Defender/AllowUserUIAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **安全情報更新間隔（以小時為單位）** ：輸入 Defender 檢查新安全性情報的間隔，從0-24。 選項包括：

  - [**未設定**] （預設）：每8小時檢查一次更新。
  - 不**檢查**： Defender 不會檢查是否有新的安全情報更新。
  - [1-24]  ：`1` 為每小時檢查一次、`2` 為每兩小時檢查一次、`24` 為每天檢查一次等等。
  
  [Defender/SignatureUpdateInterval CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **監視檔案與程式活動**：允許 Defender 監視裝置上的檔案和程式活動。 選項包括：

  - **未設定**（預設）：監視所有檔案
  - **已停用監視**
  - **監視所有檔案**
  - **僅監視傳入檔案**
  - **僅監視傳出檔案**

  [Defender/RealTimeScanDirection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- []**刪除受隔離惡意程式碼前的天數**：在您輸入天數內繼續追蹤解析的惡意程式碼，讓您可以手動檢查先前受影響的裝置。 如果您將此天數設定為 `0`，則惡意程式碼會保留在隔離資料夾中且不會自動移除。 設為 `90` 時，隔離項目會在系統上儲存 90 天，然後移除。

  [Defender/DaysToRetainCleanedMalware CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **掃描期間的 CPU 使用率限制**：限制掃描可以使用的 CPU 量 (從 `0` 到 `100`)。
- **掃描**封存檔案： [**啟用**] 會關閉 Defender 掃描封存檔案（例如 Zip 或 Cab 檔案）。 [未設定]  (預設) 允許此掃描。

  [Defender/AllowArchiveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- []**掃描內送郵件訊息**：[啟用]  允許 Defender 在電子郵件訊息到達裝置時加以掃描。 [未設定]  (預設) 會防止電子郵件掃描。

  [Defender/AllowEmailScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- []**在完整掃描期間掃描卸除式磁碟機**：[啟用]  會防止完整掃描卸除式磁碟機。 [未設定]  (預設) 可讓 Defender 掃描 USB 隨身碟等卸除式磁碟機。

  在快速掃描期間，可能仍會掃描卸載式磁片磁碟機。

  [Defender/AllowFullScanRemovableDriveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- []**在完整掃描期間掃描對應的網路磁碟機**：[啟用]  讓 Defender 掃描對應網路磁碟機上的檔案。 [未設定]  (預設) 會防止完整掃描。 如果磁碟機上的檔案是唯讀，則 Defender 無法移除在其中發現的任何惡意程式碼。

  在快速掃描期間，可能仍會掃描對應的網路磁碟機機。

  [Defender/AllowFullScanOnMappedNetworkDrives CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **掃描從網路資料夾中開啟的檔案**：  (預設) 讓 Defender 掃描共用網路磁碟機上的檔案；例如，從 UNC 路徑存取的檔案。 [啟用]  可防止此掃描。 如果磁碟機上的檔案是唯讀，則 Defender 無法移除在其中發現的任何惡意程式碼。

  [Defender/AllowScanningNetworkFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **雲端保護**：  (預設) 允許 Microsoft Active Protection Service 從您所管理裝置接收惡意程式碼活動的相關資訊。 [啟用]  會封鎖這項功能。

  [Defender/AllowCloudProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **在提交範例之前提示使用者**：控制可能需要進一步分析的潛在惡意檔案，是否自動傳送給 Microsoft。 選項包括：

  - [**未設定**] （預設）：自動傳送安全的範例。
  - **一律提示**
  - **在傳送個人資料之前提示**
  - **永不傳送資料**
  - **傳送所有資料而不提示**：自動傳送資料。

  [Defender/SubmitSamplesConsent CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- [執行每日快速掃描的時間]  ：選擇要執行每日快速掃描的小時。 [未設定]  不執行每日掃描。 若您需要更多自訂，請設定 [要執行的系統掃描類型]  設定。

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- [要執行的系統掃描類型]  ：排程系統掃描，包含掃描層級，以及要執行掃描的日期和時間。 選項包括：
  - [未設定]  ：不在裝置上排程系統掃描。 終端使用者可以視需要在裝置上手動執行掃描。
  - [停用]  ：停用裝置上的任何系統掃描。 若您使用會掃描裝置的合作夥伴防毒軟體解決方案，請選擇此選項。
  - [快速掃描]  ：查看惡意程式碼最可能註冊的常見位置，例如登錄機碼和已知的 Windows 啟動資料夾。
    - [排程日]  ：選擇要執行掃描的天。
    - [排程時間]  ：選擇要執行掃描的小時。
  - [完整掃描]  ：查看惡意程式碼可能註冊的常見位置，同時掃描裝置上的每個檔案和資料夾。
    - [排程日]  ：選擇要執行掃描的天。
    - [排程時間]  ：選擇要執行掃描的小時。

  > [!TIP]
  > 這項設定可能會和 [執行每日快速掃描的時間]  設定衝突。 一些建議：  
  >
  > - 如果您想要排程每日快速掃描和每週完整掃描，則：
  >   1. 設定**執行每日快速掃描**設定的時間。
  >   2. 設定要**執行的系統掃描類型**，以進行完整掃描。
  > 
  > - 如果您每天只想要一次快速掃描（沒有完整掃描），請使用 [設定：**時間] 來執行每日快速掃描**或**要執行的系統掃描類型**。 例如，若要在每個星期二早上 6 點執行快速掃描，請設定 [要執行的系統掃描類型]  設定。
  > 
  > - 請不要同時設定 [執行每日快速掃描的時間]  並將 [要執行的系統掃描類型]  設為 [快速掃描]  。 這些設定可能會衝突，導致掃描無法執行。

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- []**偵測潛在的不必要應用程式**：選擇 Windows 用以偵測潛在不必要應用程式的保護層級。 選項包括：
  - [未設定]  (預設)：已停用 Windows Defender 潛在的垃圾應用程式保護。
  - [封鎖]  ：Windows Defender 偵測到潛在的垃圾應用程式，並封鎖偵測到的項目。 這些項目會和其他威脅一起顯示在歷程記錄中。
  - [稽核]  ：Windows Defender 偵測到潛在的垃圾應用程式，但不採取任何行動。 您可以檢閱 Windows Defender 可能對其採取行動的應用程式相關資訊。 例如，在事件檢視器中搜尋 Windows Defender 建立的事件。

  如需潛在垃圾應用程式的詳細資訊，請參閱[偵測及封鎖潛在的垃圾應用程式](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)。

  [Defender/PUAProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **對偵測到的惡意程式碼威脅採取的動作**：選擇您想要如何處理惡意程式碼執行緒。 [**未設定**] （預設）可讓 Microsoft Defender 選擇最佳選項。 當設定為 [啟用]  時，可選擇您希望 Defender 針對它偵測到的每種威脅等級 (低、中、高及嚴重) 所採取的動作。 選項包括：
  
  - **清除**
  - **隔離**
  - **移除**
  - **允許**
  - **使用者定義**
  - **封鎖**

  如果您的動作不可行，Windows Defender 會選擇最佳選項，以確保威脅已補救。 

  [Defender/ThreatSeverityDefaultAction CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender 防毒軟體排除

- **不進行掃描和即時保護的檔案和資料夾**：將一或多個 **C:\Path** 或 **%ProgramFiles%\Path\filename.exe** 等檔案與資料夾，新增至排除清單。 任何即時或已排程的掃描都不會包含這些檔案和資料夾。
- **不進行掃描和即時保護的副檔名**：新增一或多個檔案副檔名，像是 **jpg** 或 **txt** 至排除清單中。 任何即時掃描或排定的掃描，都不會包含有這些副檔名的任何檔案。
- **排除不進行掃描和即時保護的程序** - 新增一或多個類型為 **.exe**、 **.com** 或 **.scr** 等處理序至排除清單中。 任何即時或已排程的掃描都不會包含這些處理序。

## <a name="next-steps"></a>後續步驟

如需每項設定的其他技術詳細資料，以及支援哪些 Windows 版本，請參閱 [Windows 10 Policy CSP Reference](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider) (Windows 10 原則 CSP 參考)
