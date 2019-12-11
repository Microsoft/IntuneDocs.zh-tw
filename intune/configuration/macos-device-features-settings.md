---
title: Microsoft Intune 中的 macOS 裝置功能設定 - Azure | Microsoft Docs
description: 請在 Microsoft Intune 中查看針對 AirPrint 設定 macOS 裝置的設定，並自訂 [登入] 視窗以顯示或隱藏電源按鈕。 請參閱取得適用於您網路中 AirPrint 伺服器的 IP 位址、路徑及連接埠設定步驟。 在裝置組態設定檔中使用這些設定，可設定 macOS 裝置功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5519bdc405e725556db18d36fa98289c4edb5090
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992910"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 裝置功能設定

Intune 包含一些內建設定，用來自訂您 macOS 裝置上的功能。 例如，系統管理員可以新增 AirPrint 印表機、選擇使用者登入的方式、設定電源控制、使用單一登入驗證等。

使用這些功能來控制 macOS 裝置，作為行動裝置管理 (MDM) 解決方案的一部分。

本文會列出這些設定，並說明每個設定的用途。 同時也會列出使用終端機應用程式 (模擬器) 來取得 AirPrint 印表機之 IP 位址、路徑和連接埠的步驟。 如需裝置功能的詳細資訊，請移至[新增 iOS 或 macOS 裝置功能設定](device-features-configure.md)。

## <a name="before-you-begin"></a>開始之前

[建立 macOS 裝置組態設定檔](device-features-configure.md)。

> [!NOTE]
> 這些設定適用于不同的註冊類型，有些設定會套用至所有註冊選項。 如需不同註冊類型的詳細資訊，請參閱[macOS 註冊](../enrollment/macos-enroll.md)。

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用于：裝置註冊和自動裝置註冊 

- **IP 位址**：輸入印表機的 IPv4 或 IPv6 位址。 如果您使用主機名稱來識別印表機，可以透過在終端機應用程式中偵測該印表機來取得 IP 位址。 本文中的[取得 IP 位址和路徑](#get-the-ip-address-and-path)會提供更多詳細資料。
- **路徑**：輸入印表機的路徑。 您網路上印表機的路徑通常是 `ipp/print`。 本文中的[取得 IP 位址和路徑](#get-the-ip-address-and-path)會提供更多詳細資料。
- **連接埠** (iOS 11.0 和更新版本)：輸入 AirPrint 目的地的接聽連接埠。 如果將此屬性留白，AirPrint 就會使用預設連接埠。
- **TLS** (iOS 11.0 和更新版本)：選取 [啟用]  以保護 AirPrint 與傳輸層安全性 (TLS) 的連線。

- **新增** AirPrint 伺服器。 您可以新增許多 AirPrint 伺服器。

您也可以**匯入**包括 AirPrint 印表機清單的逗號分隔檔 (.csv)。 此外，當您於 Intune 中新增 AirPrint 印表機之後，也可以**匯出**此清單。

### <a name="get-the-ip-address-and-path"></a>取得 IP 位址和路徑

若要新增 AirPrinter 伺服器，您需要有印表機的 IP 位址、資源路徑及連接埠。 下列步驟說明如何取得此資訊。

1. 在連線到與 AirPrint 印表機相同之區域網路 (子網路) 的 Mac 上，開啟 [終端機]  (從 **/Applications/Utilities**)。
2. 在 [終端機] 應用程式中，輸入 `ippfind`，然後選取 Enter 鍵。

    記下印表機資訊。 例如，可能會傳回類似 `ipp://myprinter.local.:631/ipp/port1` 的內容。 第一個部分是印表機的名稱。 最後一個部分 (`ipp/port1`) 是資源路徑。

3. 在 [終端機] 中，輸入 `ping myprinter.local`，然後選取 Enter 鍵。

   記下 IP 位址。 例如，可能會傳回類似 `PING myprinter.local (10.50.25.21)` 的內容。

4. 使用 IP 位址和資源路徑值。 在此範例中，IP 位址是 `10.50.25.21`，而資源路徑則是 `/ipp/port1`。

## <a name="login-items"></a>登入項目

### <a name="settings-apply-to-all-enrollment-types"></a>設定適用于：所有註冊類型

- 檔案 **、資料夾和自訂應用程式**：**新增**您想要在使用者登入裝置時開啟的檔案、資料夾、自訂應用程式或系統應用程式的路徑。 系統應用程式或為貴組織建立或自訂的應用程式通常會在 `Applications` 資料夾中，路徑類似于 `/Applications/AppName.app`。 

  您可以新增許多檔案、資料夾和應用程式。 例如，輸入：  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  新增任何應用程式、資料夾或檔案時，請務必輸入正確的路徑。 並非所有專案都位於 [`Applications`] 資料夾中。 如果使用者將專案從某個位置移到另一個位置，則路徑會變更。 當使用者登入時，將不會開啟此移動的專案。

## <a name="login-window"></a>登入視窗

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用于：裝置註冊和自動裝置註冊

#### <a name="window-layout"></a>視窗版面配置

- **在功能表列中顯示其他資訊**：選取功能表列上的時間區域時，[允許]  顯示主機名稱和 macOS 版本。 [未設定]  (預設) 不會在功能表列上顯示這項資訊。
- **橫幅**：輸入在裝置登入畫面中顯示的訊息。 例如，輸入您的組織資訊、歡迎訊息、失物招領資訊等。
- **選擇登入格式**：選擇使用者登入裝置的方式。 選項包括：
  - **提示輸入使用者名稱及密碼** (預設)：要求使用者輸入使用者名稱和密碼。
  - **列出全部使用者，提示輸入密碼**：要求使用者從使用者清單中選取其使用者名稱，然後輸入其密碼。 同時設定：

    - **本機使用者**：[隱藏]  不會在使用者清單中顯示本機使用者帳戶，其中可能包含標準和系統管理員帳戶。 只會顯示網路和系統使用者帳戶。 [未設定]  (預設) 會在使用者清單中顯示本機使用者帳戶。
    - **行動帳戶**：[隱藏]  不會在使用者清單中顯示行動帳戶。 [未設定]  (預設) 會在使用者清單中顯示行動帳戶。 有些行動帳戶可能會顯示為網路使用者。
    - **網路使用者**：選取 [顯示]  在使用者清單中列出網路使用者。 [未設定]  (預設) 不會在使用者清單中顯示網路使用者帳戶。
    - **管理使用者**：[隱藏]  不會在使用者清單中顯示系統管理員使用者帳戶。 [未設定]  (預設) 會在使用者清單中顯示系統管理員使用者帳戶。
    - **其他使用者**：選取 [顯示]  在使用者清單中列出 [其他...]  使用者。 [未設定]  (預設) 不會在使用者清單中顯示其他使用者帳戶。

#### <a name="login-screen-power-settings"></a>登入畫面電源設定

- **[關機] 按鈕**：[隱藏]  不會在登入畫面上顯示 [關機] 按鈕。 [未設定]  (預設) 會顯示 [關機] 按鈕。
- **[重新開機] 按鈕**：[隱藏]  不會在登入畫面上顯示 [重新開機] 按鈕。 [未設定]  (預設) 會顯示 [重新開機] 按鈕。
- **[睡眠] 按鈕**：[隱藏]  不會在登入畫面上顯示 [睡眠] 按鈕。 [未設定]  (預設) 會顯示 [睡眠] 按鈕。

#### <a name="other"></a>其他

- **讓使用者無法從 [主控台] 登入**：[停用]  會隱藏用來登入的 macOS 命令列。 如果是一般使用者，請 [停用]  這項設定。 [未設定]  (預設) 可讓進階使用者使用 macOS 命令列登入。 為了進入主控台模式，使用者要在 [使用者名稱] 欄位中輸入 `>console`，然後必須在主控台視窗中進行驗證。

#### <a name="apple-menu"></a>Apple 功能表

使用者登入裝置之後，下列設定會影響它們可執行的功能。

- **停用 [關機]** ：[停用]  可防止使用者在登入之後選取 [關機]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [關機]  功能表項目。
- **停用 [重新開機]** ：[停用]  可防止使用者在登入之後選取 [重新開機]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [重新開機]  功能表項目。
- **停用 [關閉電源]** ：[停用]  可防止使用者在登入之後選取 [關閉電源]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [關閉電源]  功能表項目。
- **停用 [登出]** (macOS 10.13 和更新版本)：[停用]  可防止使用者在登入之後選取 [登出]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [登出]  功能表項目。
- **停用 [鎖定畫面]** (macOS 10.13 和更新版本)：[停用]  可防止使用者在登入之後選取 [鎖定畫面]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [鎖定畫面]  功能表項目。

## <a name="single-sign-on-app-extension"></a>單一登入應用程式擴充功能

本功能適用於：

- macOS 10.15 與更新版本

### <a name="settings-apply-to-all-enrollment-types"></a>設定適用于：所有註冊類型 

- **Sso 應用程式延伸模組類型**：選擇認證 SSO 應用程式延伸模組的類型。 選項包括：

  - **未設定**：未使用應用程式延伸模組。 若要停用應用程式延伸模組，請將 SSO 應用程式延伸模組類型切換為 [**未設定**]。
  - 重新**導向**：使用一般、可自訂的重新導向應用程式擴充功能，透過新式驗證流程執行 SSO。 請確定您知道您組織的應用程式擴充功能的延伸模組和小組識別碼。
  - **認證**：使用可自訂的一般認證應用程式延伸模組，透過挑戰和回應驗證流程來執行 SSO。 請確定您知道您組織的 SSO 應用程式擴充功能的延伸模組識別碼和小組識別碼。  
  - **Kerberos**：使用 Apple 的內建 Kerberos 延伸模組，其包含在 macOS Catalina 10.15 和更新版本中。 此選項是**認證**應用程式延伸模組的 Kerberos 特定版本。

  > [!TIP]
  > 使用 [重新**導向**] 和 [**認證**類型] 時，您可以新增自己的設定值來傳遞延伸模組。 如果您使用**認證**，請考慮使用 Apple 在**Kerberos**類型中提供的內建設定。

- **延伸**模組識別碼（重新導向和認證）：輸入用來識別 SSO 應用程式延伸模組的套件組合識別碼，例如 `com.apple.ssoexample`。
- **小組**識別碼（重新導向和認證）：輸入 SSO 應用程式擴充功能的小組識別碼。 小組識別碼是 Apple 產生的10個字元的 Alphanumerical （數位和字母）字串，例如 `ABCDE12345`。 

  [找出您的小組識別碼](https://help.apple.com/developer-account/#/dev55c3c710c)（開啟 Apple 的網站）有詳細資訊。

- **領域**（認證和 Kerberos）：輸入驗證領域的名稱。 領域名稱應為大寫，例如 `CONTOSO.COM`。 一般來說，您的領域名稱與您的 DNS 功能變數名稱相同，但全部大寫。

- **網域**（認證和 Kerberos）：輸入可透過 SSO 進行驗證之網站的網域或主機名稱。 例如，如果您的網站是 `mysite.contoso.com`，則 `mysite` 是主機名稱，而 `contoso.com` 則是功能變數名稱。 當使用者連線到這些網站的任何一個時，應用程式延伸模組會處理驗證挑戰。 此驗證可讓使用者使用臉部識別碼、Touch ID 或 Apple pincode/密碼來登入。

  - 單一登入應用程式延伸模組 Intune 設定檔中的所有網域都必須是唯一的。 即使您使用不同類型的 SSO 應用程式擴充功能，您也無法在任何登入應用程式延伸模組設定檔中重複網域。
  - 這些網域不會區分大小寫。

- **Url** （僅限重新導向）：輸入您身分識別提供者的 URL 首碼，其代表重新導向應用程式延伸模組執行 SSO。 當使用者重新導向至這些 Url 時，SSO 應用程式延伸模組將會介入並提示 SSO。

  - Intune 單一登入應用程式延伸模組設定檔中的所有 Url 都必須是唯一的。 即使您使用不同類型的 SSO 應用程式擴充功能，您也無法在任何 SSO 應用程式延伸模組設定檔中重複網域。
  - Url 的開頭必須是 HTTP://或 HTTPs://。

- **其他**設定（重新導向和認證）：輸入其他延伸模組特定的資料，以傳遞至 SSO 應用程式延伸模組：
  - 機**碼**：輸入您想要新增的專案名稱，例如 `user name`。
  - **類型**：輸入資料的類型。 選項包括：

    - 字串
    - 布林值：在 [設定**值**] 中，輸入 `True` 或 `False`。
    - 整數：在 [設定**值**] 中，輸入數位。
    
  - **值**：輸入資料。
  
  - **新增**：選取以新增您的設定金鑰。

- **Keychain 使用**方式（僅限 Kerberos）：選擇 [**封鎖**] 以防止密碼儲存並儲存在 Keychain 中。 [**未設定**] （預設）會允許儲存密碼並儲存在 keychain 中。  
- **臉部識別碼、TOUCH id 或密碼**（僅限 Kerberos）： [**需要**] 會強制使用者輸入其臉部識別碼、Touch id 或 Apple 密碼，以登入您所新增的網域。 [**未設定**] （預設）不會要求使用者使用生物識別或密碼來登入。
- **預設領域**（僅限 Kerberos）：選擇 [**啟用**] 以設定您輸入為預設領域的**領域**值。 [**未**設定] （預設）不會設定預設領域。

  > [!TIP]
  > - 如果您要在您的組織中設定多個 Kerberos SSO 應用程式延伸模組，請**啟用**此設定。
  > - 如果您要使用多個領域，請**啟用**此設定。 它會設定您輸入為預設領域的**領域**值。
  > - 如果您只有一個領域，請將它保留為 [**未設定**] （預設值）。

- **自動**探索（僅限 Kerberos）：當設定為 [**封鎖**] 時，Kerberos 擴充功能不會自動使用 LDAP 和 DNS 來判斷其 Active Directory 的網站名稱。 [**未設定**] （預設）可讓延伸模組自動尋找 Active Directory 的網站名稱。
- **密碼變更**（僅限 Kerberos）： [**封鎖**] 會防止使用者變更他們用來登入您所輸入網域的密碼。 [**未設定**] （預設）允許變更密碼。  
- **密碼同步**（僅限 Kerberos）：選擇 [**啟用**] 可將使用者的本機密碼同步至 Azure AD。 [**未設定**] （預設）會停用 Azure AD 的密碼同步。 使用此設定做為 SSO 的替代或備份。 如果使用者已使用 Apple 行動帳戶登入，則此設定無法正常執行。
- **Windows Server Active Directory 密碼複雜性**（僅限 Kerberos）：選擇 [**需要**] 以強制使用者密碼符合 Active Directory 的密碼複雜性需求。 如需詳細資訊，請參閱[密碼必須符合複雜性需求](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements)。 [**未設定**] （預設）不會要求使用者符合 Active Directory 的密碼需求。
- **密碼長度下限**（僅限 Kerberos）：輸入可組成使用者密碼的最小字元數。 [**未設定**] （預設）不會在使用者上強制執行最小密碼長度。
- **密碼重複使用限制**（僅限 Kerberos）：輸入在網域上可以重複使用先前的密碼之前，必須使用的新密碼數目（從1-24）。 [**未設定**] （預設）不會強制執行密碼重複使用限制。
- **密碼最短使用期限**（僅限 Kerberos）：輸入在使用者可以變更密碼前，必須在網域上使用密碼的天數。 [**未設定**] （預設）不會強制執行最短的密碼使用期限，因此可以加以變更。
- **密碼到期通知**（僅限 Kerberos）：輸入密碼到期的天數，讓使用者收到其密碼即將到期的通知。 [**未設定**] （預設）會使用 `15` 天。
- **密碼到期** (僅 Kerberos)：輸入多少天後必須變更裝置密碼。 [**未設定**] （預設）表示使用者密碼永遠不會過期。
- **密碼變更 URL** （僅限 Kerberos）：輸入使用者起始 Kerberos 密碼變更時所啟動的 URL。
- **主體名稱**（僅限 Kerberos）：輸入 Kerberos 主體的使用者名稱。 您不需要包含領域名稱。 例如，在 `user@contoso.com`中，`user` 是主體名稱，而 `contoso.com` 是領域名稱。

  > [!TIP]
  > - 您也可以在主體名稱中使用變數，方法是輸入大括弧 `{{ }}`。 例如，若要顯示使用者名稱，請輸入 `Username: {{username}}`。 
  > - 不過，由於變數不會在 UI 中驗證，而且會區分大小寫，因此請小心使用變數替代。 請務必輸入正確的資訊。
  
- **Active Directory 網站碼**（僅限 Kerberos）：輸入 Kerberos 延伸應使用之 Active Directory 網站的名稱。 您可能不需要變更此值，因為 Kerberos 延伸模組可能會自動找到 Active Directory 的網站碼。
- 快取**名稱**（僅限 Kerberos）：輸入 Kerberos 快取的一般安全性服務（GSS）名稱。 您很可能不需要設定此值。  
- **密碼需求訊息**（僅限 Kerberos）：輸入對使用者顯示之組織密碼需求的文字版本。 如果您不需要 Active Directory 的密碼複雜性需求，或未輸入最小密碼長度，則會顯示訊息。  
- **應用程式**套件組合識別碼（僅限 Kerberos）：**新增**應在您的裝置上使用單一登入的應用程式套件組合識別碼。 這些應用程式會被授與 Kerberos 票證授權票證、驗證票證的存取權，以及向已獲授權存取的服務驗證使用者。
- **網域領域對應**（僅限 Kerberos）：**新增**應對應至您領域的網域 DNS 尾碼。 當主機的 DNS 名稱不符合領域名稱時，請使用此設定。 您很可能不需要建立此自訂網域到領域的對應。
- **PKINIT certificate** （僅限 Kerberos）：**選取**可用於 Kerberos 驗證的初始驗證（PKINIT）憑證的公開金鑰加密。 您可以從已在 Intune 中新增的[PKCS](../protect/certficates-pfx-configure.md)或[SCEP](../protect/certificates-scep-configure.md)憑證中進行選擇。 如需憑證的詳細資訊，請參閱[在 Microsoft Intune 中使用憑證進行驗證](../protect/certificates-configure.md)。

## <a name="associated-domains"></a>相關網域

在 Intune 中，您可以︰

- 新增許多應用程式對網域的關聯。
- 將許多網域與相同的應用程式產生關聯。

本功能適用於：

- macOS 10.15 與更新版本

### <a name="settings-apply-to-all-enrollment-types"></a>設定適用于：所有註冊類型

- **應用程式**識別碼：輸入要與網站產生關聯之應用程式的應用程式識別碼。 [應用程式識別碼] 包含 [team ID] 和 [套件組合識別碼]： `TeamID.BundleID`。

  小組識別碼是 Apple 為您的應用程式開發人員產生的10個字元的 Alphanumerical （字母和數位）字串，例如 `ABCDE12345`。 [找出您的小組識別碼](https://help.apple.com/developer-account/#/dev55c3c710c) （開啟 Apple 的網站）的詳細資訊。

  套件組合識別碼可唯一識別應用程式，而且通常會以反向功能變數名稱標記法來格式化。 例如，搜尋工具的配套識別碼是 `com.apple.finder`。 若要尋找套件組合識別碼，請使用終端機中的 AppleScript：

  `osascript -e 'id of app "ExampleApp"'`

- **網域**：輸入要與應用程式建立關聯的網站網域。 網域包含服務類型和完整的主機名稱，例如 `webcredentials:www.contoso.com`。

  您可以在網域開頭之前輸入 `*.` （星號萬用字元和句點），以符合相關聯網域的所有子域。 需要句點。 確切的網域優先順序高於萬用字元網域。 因此，*如果*在完整的子域中找不到相符項，則會比對父系網域中的模式。

  服務類型可以是：

  - **authsrv**：單一登入應用程式擴充功能
  - **applink**：通用連結
  - **webcredentials**：密碼自動填入

- **新增**：選取以新增您的應用程式和相關聯的網域。

> [!TIP]
> 若要進行疑難排解，請在您的 macOS 裝置上開啟 [**系統喜好**設定] > **設定檔**。 確認您建立的設定檔位於 [裝置設定檔] 清單中。 如果列出，請確定**相關聯的網域**設定是在設定檔中，而且包含正確的應用程式識別碼和網域。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以在[iOS](ios-device-features-settings.md)上設定裝置功能。
