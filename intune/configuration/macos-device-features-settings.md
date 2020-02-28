---
title: Microsoft Intune 中的 macOS 裝置功能設定 - Azure | Microsoft Docs
description: 請在 Microsoft Intune 中查看針對 AirPrint 設定 macOS 裝置的設定，並自訂 [登入] 視窗以顯示或隱藏電源按鈕。 請參閱取得適用於您網路中 AirPrint 伺服器的 IP 位址、路徑及連接埠設定步驟。 在裝置組態設定檔中使用這些設定，可設定 macOS 裝置功能。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: df5b53be159fd082090e61fd736e4c9329644c85
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512733"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune 中的 macOS 裝置功能設定

Intune 包含一些內建設定，用來自訂您 macOS 裝置上的功能。 例如，系統管理員可以新增 AirPrint 印表機、選擇使用者登入的方式、設定電源控制、使用單一登入驗證等。

使用這些功能來控制 macOS 裝置，作為行動裝置管理 (MDM) 解決方案的一部分。

本文會列出這些設定，並說明每個設定的用途。 同時也會列出使用終端機應用程式 (模擬器) 來取得 AirPrint 印表機之 IP 位址、路徑和連接埠的步驟。 如需裝置功能的詳細資訊，請移至[新增 iOS/iPadOS 或 macOS 裝置功能設定](device-features-configure.md)。

## <a name="before-you-begin"></a>開始之前

[建立 macOS 裝置組態設定檔](device-features-configure.md)。

> [!NOTE]
> 這些設定適用於不同的註冊類型，而其中有部分設定適用於所有註冊選項。 如需不同註冊類型的詳細資訊，請參閱 [macOS 註冊](../enrollment/macos-enroll.md)。

## <a name="airprint"></a>AirPrint

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊 

- **IP 位址**：輸入印表機的 IPv4 或 IPv6 位址。 如果您使用主機名稱來識別印表機，可以透過在終端機應用程式中偵測該印表機來取得 IP 位址。 本文中的[取得 IP 位址和路徑](#get-the-ip-address-and-path)會提供更多詳細資料。
- **路徑**：輸入印表機的路徑。 您網路上印表機的路徑通常是 `ipp/print`。 本文中的[取得 IP 位址和路徑](#get-the-ip-address-and-path)會提供更多詳細資料。
- **連接埠** (iOS 11.0+、iPadOS 13.0+)：輸入 AirPrint 目的地的接聽連接埠。 如果將此屬性留白，AirPrint 就會使用預設連接埠。
- **TLS** (iOS 11.0+、iPadOS 13.0+)：選取 [啟用]  以使用傳輸層安全性 (TLS) 保護 AirPrint 連線。

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

### <a name="settings-apply-to-all-enrollment-types"></a>設定適用於：所有註冊類型

- **檔案、資料夾與自訂應用程式**：[新增]  您要在使用者登入裝置時開啟的檔案、資料夾、自訂應用程式或系統應用程式的路徑。 系統應用程式，或針對您組織所建置或自訂的應用程式，通常會位於 `Applications` 資料夾中，並具有類似 `/Applications/AppName.app` 的路徑。 

  您可以新增許多檔案、資料夾與應用程式。 例如，輸入：  
  
  - `/Applications/Calculator.app`
  - `/Applications`
  - `/Applications/Microsoft Office/root/Office16/winword.exe`
  - `/Users/UserName/music/itunes.app`
  
  新增任何應用程式、資料夾或檔案時，請務必輸入正確的路徑。 並非所有項目都位於 `Applications` 資料夾。 如果使用者將項目從某個位置移動到另一個位置，路徑便會變更。 這個已移動的項目並不會在使用者登入時開啟。

## <a name="login-window"></a>登入視窗

### <a name="settings-apply-to-device-enrollment-and-automated-device-enrollment"></a>設定適用於：裝置註冊與自動裝置註冊

#### <a name="window-layout"></a>視窗版面配置

- **在選單列中顯示其他資訊**：選取功能表列上的時間區域時，[允許]  可顯示主機名稱和 macOS 版本。 [未設定]  (預設) 不會在功能表列上顯示這項資訊。
- **橫幅**：輸入在裝置登入畫面中顯示的訊息。 例如，輸入您的組織資訊、歡迎訊息、失物招領資訊等。
- **選擇登入格式**：選擇使用者登入裝置的方式。 選項包括：
  - **提示輸入使用者名稱及密碼** (預設)：要求使用者輸入使用者名稱和密碼。
  - **列出全部使用者，提示使用密碼**：要求使用者從使用者清單中選取其使用者名稱，然後輸入其密碼。 同時設定：

    - **本機使用者**：[隱藏]  不會在使用者清單中顯示本機使用者帳戶，其中可能包含標準和系統管理員帳戶。 只會顯示網路和系統使用者帳戶。 [未設定]  (預設) 會在使用者清單中顯示本機使用者帳戶。
    - **行動裝置帳戶**：[隱藏]  不會在使用者清單中顯示行動裝置帳戶。 [未設定]  (預設) 會在使用者清單中顯示行動帳戶。 有些行動帳戶可能會顯示為網路使用者。
    - **網路使用者**：選取 [顯示]  會在使用者清單中列出網路使用者。 [未設定]  (預設) 不會在使用者清單中顯示網路使用者帳戶。
    - **管理使用者**：[隱藏]  不會在使用者清單中顯示系統管理員使用者帳戶。 [未設定]  (預設) 會在使用者清單中顯示系統管理員使用者帳戶。
    - **其他使用者**：選取 [顯示]  在使用者清單中列出 [其他]  使用者。 [未設定]  (預設) 不會在使用者清單中顯示其他使用者帳戶。

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
- **停用 [登出]** \(macOS 10.13 和更新版本\)：[停用]  可防止使用者在登入之後選取 [登出]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [登出]  功能表項目。
- **停用 [鎖定螢幕]** \(macOS 10.13 和更新版本\)：[停用]  可防止使用者在登入之後選取 [鎖定螢幕]  選項。 [未設定]  (預設) 可讓使用者在裝置上選取 [鎖定畫面]  功能表項目。

## <a name="single-sign-on-app-extension"></a>單一登入應用程式擴充功能

本功能適用於：

- macOS 10.15 與更新版本

### <a name="settings-apply-to-all-enrollment-types"></a>設定適用於：所有註冊類型 

- **SSO 應用程式延伸模組類型**：選擇認證 SSO 應用程式延伸模組的類型。 選項包括：

  - **未設定**：不使用應用程式延伸模組。 若要停用應用程式延伸模組，請將 SSO 應用程式延伸模組類型切換成 [未設定]  。
  - **重新導向**：使用一般、可自訂的重新導向應用程式延伸模組，搭配新式驗證流程執行 SSO。 請確定您知道您組織應用程式延伸模組的延伸模組與小組識別碼。
  - **認證**：使用一般、可自訂的認證應用程式延伸模組來搭配挑戰和回應驗證流程執行 SSO。 請確定您知道您組織 SSO 應用程式延伸模組的延伸模組識別碼與小組識別碼。  
  - **Kerberos**：使用 Apple 的內建 Kerberos 延伸模組，其已包含在 macOS Catalina 10.15 與更新版本上。 此選項為 [認證]  應用程式延伸模組的 Kerberos 特定版本。

  > [!TIP]
  > 使用 [重新導向]  與 [認證]  類型時，您會新增自己的設定值來透過延伸模組傳遞。 如果您是使用 [認證]  ，請考慮使用由 Apple 在 [Kerberos]  類型中所提供的內建組態設定。

- **延伸模組識別碼** ([重新導向] 與 [認證])：輸入能識別您 SSO 應用程式延伸模組的套件組合識別碼，例如 `com.apple.ssoexample`。
- **小組識別碼** ([重新導向] 與 [認證])：輸入您 SSO 應用程式延伸模組的小組識別碼。 小組識別碼是由 Apple 產生之 10 個字元的英數 (數字與字母) 字串，例如 `ABCDE12345`。 

  [尋找您的小組識別碼](https://help.apple.com/developer-account/#/dev55c3c710c) (會開啟 Apple 的網站) 提供詳細資訊。

- **領域** ([認證] 與 [Kerberos])：輸入驗證領域的名稱。 領域名稱應為大寫，例如 `CONTOSO.COM`。 您的領域名稱通常會與您的 DNS 網域名稱相同，但全部都是大寫。

- **網域** ([認證] 與 [Kerberos])：輸入可以透過 SSO 驗證之網站的網域或主機名稱。 例如，如果您的網站是 `mysite.contoso.com`，則 `mysite` 是主機名稱，而 `contoso.com` 則是網域名稱。 當使用者連線到上述其中一個網站時，應用程式延伸模組會處理驗證挑戰。 此驗證可讓使用者使用 Face ID、Touch ID 或 Apple PIN 碼/密碼來登入。

  - 您單一登入應用程式延伸模組 Intune 設定檔中的所有網域都不能重複。 您不能在任何單一登入應用程式延伸模組設定檔中重複使用網域，即使您是使用不同類型的 SSO 應用程式延伸模組也一樣。
  - 這些網域不會區分大小寫。

- **URL** (僅限 [重新導向])：輸入 [重新導向] 應用程式延伸模組會代為執行 SSO 之識別提供者的 URL 前置詞。 當系統將使用者重新導向到這些 URL 時，SSO 應用程式延伸模組將會介入並提示進行 SSO。

  - 您的 Intune 單一登入應用程式延伸模組設定檔中的所有 URL 都不能重複。 您不能在任何 SSO 應用程式延伸模組設定檔中重複使用網域，即使您是使用不同類型的 SSO 應用程式延伸模組也一樣。
  - URL 的開頭必須是 http:// 或 https://。

- **其他設定** ([重新導向] 與 [認證])：輸入其他延伸模組特定的資料以傳遞至 SSO 應用程式延伸模組：
  - **機碼**：輸入您要新增之項目的名稱，例如 `user name`。
  - **類型**：輸入資料的類型。 選項包括：

    - 字串
    - 布林值：在 [設定值]  中，輸入 `True` 或 `False`。
    - 整數：在 [設定值]  中，輸入數字。
    
  - **值**：輸入資料。
  
  - **新增**：選取以新增您的設定金鑰。

- **鑰匙串使用方式** (僅限 [Kerberos])：選擇 [封鎖]  來防止將密碼儲存並保存在鑰匙串中。 [未設定]  \(預設\) 允許將密碼儲存並保存在鑰匙串中。  
- **Face ID、Touch ID 或密碼** (僅限 [Kerberos])：[需要]  會強制使用者輸入其 Face ID、Touch ID 或 Apple 密碼以登入您所新增的網域。 [未設定]  \(預設\) 不會要求使用者使用生物特徵辨識技術或密碼來登入。
- **預設領域** (僅限 [Kerberos])：選擇 [啟用]  以將您輸入的 [領域]  值設定為預設領域。 [未設定]  \(預設\) 不會設定預設領域。

  > [!TIP]
  > - 如果您要在組織中設定多個 Kerberos SSO 應用程式延伸模組，就必須 [啟用]  此設定。
  > - 如果您會使用多個領域，請 [啟用]  此設定。 其會將您輸入的 [領域]  值設定為預設領域。
  > - 如果您只有單一領域，請將其保留為 [未設定]  \(預設\)。

- **自動探索** (僅限 [Kerberos])：當設定為 [封鎖]  時，Kerberos 延伸模組不會自動使用 LDAP 與 DNS 來判斷其 Active Directory 網站名稱。 [未設定]  \(預設\) 會允許延伸模組自動找出 Active Directory 網站名稱。
- **密碼變更** (僅限 [Kerberos])：[封鎖]  會防止使用者變更其用來登入您所輸入之網域的密碼。 [未設定]  \(預設\) 會允許密碼變更。  
- **密碼同步** (僅限 [Kerberos])：選擇 [啟用]  來將您使用者的本機密碼同步至 Azure AD。 [未設定]  \(預設\) 會停用針對 Azure AD 的密碼同步。 請使用此設定作為 SSO 的替代方案或備案。 如果使用者是使用 Apple 行動帳戶來登入，此設定無法運作。
- **Windows Server Active Directory 密碼複雜度** (僅限 [Kerberos])：選擇 [需要]  來強制使用者密碼符合 Active Directory 的密碼複雜度需求。 請參閱[密碼必須符合複雜性需求](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/password-must-meet-complexity-requirements) \(部分機器翻譯\) 以取得詳細資訊。 [未設定]  \(預設\) 不會要求使用者符合 Active Directory 的密碼需求。
- **密碼長度下限** (僅限 [Kerberos])：輸入可以組成使用者密碼的字元數目下限。 [未設定]  \(預設\) 不會對使用者強制密碼長度下限。
- **密碼重複使用限制** (僅限 [Kerberos])：輸入在可以於網域上使用先前的密碼之前，必須使用的新密碼數目 (從 1 到 24)。 [未設定]  \(預設\) 不會強制密碼重複使用限制。
- **密碼最短存留期** (僅限 [Kerberos])：輸入在使用者可以變更密碼之前，該密碼必須先在網域上使用的天數。 [未設定]  \(預設\) 不會在密碼可以變更之前強制密碼最短存留期。
- **密碼到期通知** (僅限 [Kerberos])：輸入系統會在密碼到期的幾天之前通知使用者其密碼即將到期。 [未設定]  \(預設\) 會使用 `15` 天。
- **密碼到期** (僅限 Kerberos)：輸入必須變更裝置密碼前的天數。 [未設定]  \(預設\) 表示使用者密碼永遠不會到期。
- **密碼變更 URL** (僅限 [Kerberos])：輸入會在使用者起始 Kerberos 密碼變更時啟動的 URL。
- **主體名稱** (僅限 [Kerberos])：輸入 Kerberos 主體的使用者名稱。 您不需要包含領域名稱。 例如，在 `user@contoso.com` 中，`user` 是主體名稱，而 `contoso.com` 則是領域名稱。

  > [!TIP]
  > - 您也可以在主體名稱中使用變數，方法是輸入大括弧 `{{ }}`。 例如，若要顯示使用者名稱，請輸入 `Username: {{username}}`。 
  > - 不過，請小心使用變數替代，因為變數不會在 UI 中驗證，而且會區分大小寫。 請務必輸入正確的資訊。
  
- **Active Directory 站台碼** (僅限 [Kerberos])：輸入 Kerberos 延伸模組應使用的 Active Directory 網站名稱。 您可能不需要變更此值，因為 Kerberos 延伸模組可能會自動尋找 Active Directory 站台碼。
- **快取名稱** (僅限 [Kerberos])：輸入 Kerberos 快取的一般安全性服務 (GSS) 名稱。 您通常不會需要設定此值。  
- **密碼需求訊息** (僅限 [Kerberos])：輸入要向使用者顯示的組織密碼需求文字版本。 如果您不要求 Active Directory 的密碼複雜度需求，或不輸入密碼長度下限，便會顯示此訊息。  
- **應用程式套件組合識別碼** (僅限 [Kerberos])：[新增]  應在您的裝置上使用單一登入的應用程式套件組合識別碼。 系統會將 Kerberos 票證授權票證 (驗證票證) 的存取權授與這些應用程式，使應用程式能夠將使用者驗證至其具有存取權的服務。
- **網域領域對應** (僅限 [Kerberos])：[新增]  應對應至您領域的網域 DNS 尾碼。 在主機的 DNS 名稱不符合領域名稱的情況下使用此設定。 您通常不會需要建立此自訂網域對領域對應。
- **PKINIT 憑證** (僅限 [Kerberos])：[選取]  可用於 Kerberos 驗證的初始驗證公開金鑰加密 (PKINIT) 憑證。 您可以從自己已在 Intune 中新增的 [PKCS](../protect/certficates-pfx-configure.md) 或 [SCEP](../protect/certificates-scep-configure.md) 憑證中選擇。 如需憑證的詳細資訊，請參閱[在 Microsoft Intune 中使用憑證進行驗證](../protect/certificates-configure.md)。

## <a name="associated-domains"></a>相關網域

在 Intune 中，您可以︰

- 新增許多應用程式對網域關聯。
- 將許多網域與相同的應用程式關聯。

本功能適用於：

- macOS 10.15 與更新版本

### <a name="settings-apply-to-all-enrollment-types"></a>設定適用於：所有註冊類型

- **應用程式識別碼**：輸入要與網站相關聯之應用程式的應用程式識別碼。 應用程式識別碼包含小組識別碼與套件組合識別碼：`TeamID.BundleID`。

  小組識別碼是由 Apple 為您的應用程式開發人員產生之 10 個字元的英數 (字母與數字) 字串，例如 `ABCDE12345`。 [尋找您的小組識別碼](https://help.apple.com/developer-account/#/dev55c3c710c)  (會開啟 Apple 的網站) 提供詳細資訊。

  套件組合識別碼能唯一識別應用程式，且其格式通常是反向網域名稱標記法。 例如，Finder 的套件組合識別碼為 `com.apple.finder`。 若要尋找套件組合識別碼，請在終端機中使用 AppleScript：

  `osascript -e 'id of app "ExampleApp"'`

- **網域**：輸入要與應用程式相關聯的網站網域。 網域包含服務類型與完整主機名稱，例如 `webcredentials:www.contoso.com`。

  您可以在網域開頭的前方輸入 `*.` (星號萬用字元與句號) 來表示相關聯網域的所有子網域。 句號為必要。 與萬用字元網域相比，確切的網域具有較高的優先順序。 因此，來自父網域的模式「只會在」  於完整子網域中找不到相符項目時進行比對。

  服務類型可以是：

  - **authsrv**：單一登入應用程式擴充功能
  - **applink**：通用連結
  - **webcredentials**：密碼自動填寫

- **新增**：選取來新增您的應用程式與關聯的網域。

> [!TIP]
> 若要進行疑難排解，請在您的 macOS 裝置上開啟 [系統偏好設定]   > [描述檔]  。 確認您所建立的設定檔已位於裝置設定檔清單。 如果已加以列出，請確定設定檔中具有 [相關網域設定]  ，而且其包含正確的應用程式識別碼與網域。

## <a name="next-steps"></a>後續步驟

[指派設定檔](device-profile-assign.md)並[監視其狀態](device-profile-monitor.md)。

您也可以在 [iOS/iPadOS](ios-device-features-settings.md) 上設定裝置功能。
