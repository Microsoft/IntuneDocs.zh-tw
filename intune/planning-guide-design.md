---
title: 建立設計
titlesuffix: Microsoft Intune
description: 本文可協助您建立 Microsoft Intune 僅限雲端設計及實作的設計。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.openlocfilehash: 1d8ccd4e432623cf7d0ce4ce66651a95e13b8473
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186489"
---
# <a name="create-a-design"></a>建立設計

您的 Intune 設計以您完成[本指南其他章節](planning-guide.md)時所收集的資訊及做出的決策為基礎， 並協助您將下列各項結合在一起：

-   目前的環境

-   Intune 部署選項

-   外部相依性的身分識別需求

-   裝置平台考量

-   要傳遞的需求  

雖然有基本的內部部署基礎結構需求，但設計計劃仍有助於確定您獲得符合目的、目標和需求的正確行動裝置管理解決方案。

讓我們詳細檢閱各個區域。 

## <a name="record-your-current-environment"></a>記錄目前的環境
此外，在實作和測試階段期間經常會有設計變更。 請在發生變更時，使用您的設計計劃來記錄這些變更及其背後的原理。

您目前的環境會影響設計決策，應該記錄下以來在進行其他 Intune 設計決策時參考。 以下是如何記錄目前環境的一些範例︰

-   **雲端中的身分識別**

    -   您使用 DirSync 還是 Azure Active Directory (Azure AD) 連線？

    -   您的環境是否為同盟？

    -   是否啟用 Multi-Factor Authentication (MFA)？

-   **電子郵件環境**

    -   是否使用 Exchange？ 在內部部署或雲端？

    -   是否正在進行將 Exchange 移轉到雲端的專案？

-   **目前的行動裝置管理 (MDM) 解決方案**

    -   您目前使用其他 MDM 解決方案嗎？

    -   公司和 BYOD 使用案例使用的 MDM 解決方案為何？

    -   現在使用哪些功能 (例如：應用程式裝置設定、Wi-Fi 設定)？

    -   支援的裝置平台有哪些？

    -   哪些群組和有多少使用者使用 MDM 方案？

-   **憑證解決方案**

    -   您實作過憑證解決方案嗎？

    -   您使用何種類型的憑證？

-   **系統管理**

    -   您如何管理電腦和伺服器環境？

    -   您使用的是 System Center Configuration Manager 嗎？ 您使用的是協力廠商的系統管理平台嗎？

-   **VPN 解決方案**

    -   您的 VPN 解決方案為何？

    -   您會將它同時用於公司和 BYOD 使用案例嗎？

記錄目前的 MDM 環境時，請務必記下可能影響您環境的任何專案或任何其他計劃。 以下示範如何在建立 Intune 設計時記錄目前的環境：

| **解決方案區域** | **目前的環境** | **註解** |
|---|---|---|
| **身分識別** | Azure AD、Azure AD Connect、未同盟、無 MFA | 專案就緒，年底可啟用 MFA |                 
| **電子郵件環境** | Exchange 內部部署、Exchange Online | 目前從 Exchange 內部部署移轉至 Exchange Online。 信箱已移轉 75%。 Intune 試驗開始之前，會移轉最後的 25%。 |                
| **SharePoint** | SharePoint 內部部署 | 不打算移至 SharePoint Online |  
| **目前的 MDM** | Exchange ActiveSync |  |
| **憑證解決方案** | Microsoft Server 2012 R2、AD 憑證服務 | 網站伺服器只使用 PKI |
| **系統管理** | System Center Configuration Manager CB 1606 | 想要調查 Intune 混合式解決方案 |
| **VPN 解決方案** | Cisco AnyConnect |  |


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來開發 Intune 設計計劃。

## <a name="choose-an-intune-deployment-option"></a>選擇 Intune 部署選項

Intune 提供兩種部署選項︰獨立和混合式。 獨立是指 Intune 服務在雲端中執行，混合式則整合 Intune 與 System Center Configuration Manager。 本指南主要用於獨立選項。 [決定哪一個選項符合您的商務需求](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)。

## <a name="intune-tenant-location"></a>Intune 租用戶位置

如果您的組織有全球支援，請務必在訂閱服務時規劃租用戶所在的位置。 國家 (地區) 會在您第一次註冊 Intune 訂閱時定義，並對應至全球下列地區：

-   北美

-   歐洲、中東和非洲地區

-   亞洲及太平洋地區

>[!IMPORTANT]
> 之後無法變更國家 (地區) 與租用戶位置。

## <a name="external-dependencies"></a>外部相依性

外部相依性是和 Intune 分開的服務及產品，但卻是 Intune 需求或可能與 Intune 整合。 請務必找出任何外部相依性需求，以及其設定方式。 一些常見的外部相依性範例包括：

-   權杖服務 (STS)

-   使用者和裝置群組

-   公開金鑰基礎結構 (PKI)

下面會更詳細地探索這些常見的外部相依性

### <a name="identity"></a>權杖服務 (STS)

身分識別是我們識別誰是貴組織使用者以及誰註冊裝置的方法。 Intune 需要 Azure Active Directory (Azure AD) 作為使用者身分識別提供者。 如果您已使用這項服務，就可以使用您在雲端中現有的身分識別。 此外，建議使用 Azure AD Connect 同步處理您內部部署的使用者身分識別與 Microsoft 雲端服務。 如果您的組織已使用 Office 365，請務必讓 Intune 使用相同的 Azure AD 環境。

深入了解下列 Intune 身分識別需求：

- [身分識別需求](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions)。

- [目錄同步作業需求](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。

- [Multi-Factor Authentication 需求](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)。

### <a name="user-and-device-groups"></a>使用者和裝置群組

使用者和裝置群組決定部署的目標，包括原則、應用程式和設定檔。 您必須判斷需要哪些使用者和裝置群組。

建議在內部部署 Active Directory 中建立所有群組，再同步處理至 Azure AD。 深入了解使用者和裝置群組的規劃和建立：

-   [規劃您的使用者和裝置群組](users-add.md)。

-   [建立使用者和裝置群組](groups-add.md)。

### <a name="public-key-infrastructure-pki"></a>公開金鑰基礎結構 (PKI)
公開金鑰基礎結構向裝置或使用者提供憑證，以安全的方式向服務進行驗證。 Intune 支援 Microsoft PKI 基礎結構。 裝置和使用者憑證可以核發給行動裝置，以滿足憑證式驗證的需求。 使用憑證之前，您必須先判斷是否需要憑證、網路基礎結構可否支援憑證式驗證，以及現有環境目前是否使用憑證。

如果您打算使用 VPN、Wi-Fi 或電子郵件設定檔憑證和 Intune，請確定您有受支援的 [PKI 基礎結構就緒](certificates-configure.md)，隨時可建立及部署憑證設定檔。

此外，如果要核發 SCEP 憑證，您需要判斷哪部伺服器會裝載網路裝置註冊服務 (NDES) 功能，以及通訊進行的方式。

深入了解：

-   [如何設定 Intune 憑證設定檔](certificates-configure.md)

-   [如何設定 SCEP 的憑證基礎結構](certificates-scep-configure.md)

-   [如何設定 PFX 的憑證基礎結構](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>裝置平台考量

請進一步檢閱您裝置的下列層面，以了解如何正確地進行管理。

-   支援的裝置平台

-   裝置

-   裝置擁有權

-   大量註冊

讓我們更詳細地檢閱這些區域。

### <a name="determine-supported-device-platforms"></a>判斷支援的裝置平台

您需要知道哪些裝置會放在環境中，並確認 Intune 是否會在建立您的設計時支援它們。 Intune 支援 iOS、Android 和 Windows 平台。

[Intune 支援裝置的完整清單](supported-devices-browsers.md)。

### <a name="devices"></a>裝置

Intune 管理行動裝置以保護公司資料，讓終端使用者能夠從更多地點工作。 Intune 支援許多裝置平台，因此建議您記錄貴組織設計中支援的裝置及作業系統平台和版本。 例如：

| **裝置平台** | **作業系統版本** |
|:---:|:---:|
| iOS - iPhone | 10.0 + |                
| iOS - iPad | 10.0 + |               
| Android – Samsung Knox Standard | 4.0+ |
| Windows 10 平板電腦 | 10+ |


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來開發裝置清單。
### <a name="device-ownership"></a>裝置擁有權

Intune 支援公司擁有的裝置和個人裝置。 如果您透過裝置註冊管理員或裝置註冊計劃註冊裝置，該裝置即視為公司擁有的。 例如，裝置透過 Apple 裝置註冊計劃 (DEP) 註冊，標記為公司，然後放在會接收目標公司原則和應用程式的裝置群組中。

如需公司與 BYOD 使用案例的詳細資訊，請參閱[第 3 節︰決定使用案例的需求](planning-guide-requirements.md)。

### <a name="bulk-enrollment"></a>大量註冊

 您可以根據平台透過不同的方式來註冊大量的裝置。 如果您需要大量註冊，請先[決定大量註冊方法](device-enrollment.md)並將它納入設計中。

## <a name="feature-requirements"></a>功能需求

我們會在這些章節中檢視下列符合您使用案例需求的功能：

-   條款和條件原則

-   設定原則

-   資源設定檔

-   應用程式

-   相容性原則

-   條件式存取

讓我們詳細檢閱各個區域。

### <a name="terms-and-conditions-policies"></a>條款和條件原則

您可以使用[條款及條件](terms-and-conditions-create.md)來說明終端使用者必須接受才能註冊其裝置的原則或條件。 Intune 支援將多項條款與條件原則新增及部署到使用者群組的能力。

您需要決定是否需要條款和條件原則。 如果是的話，組織中由誰負責提供這項資訊。 下例說明如何記錄條款與條件原則。

| **條款及條件名稱** | **使用案例** | **目標群組** |
|:---:|:---:|:---:|
| 公司條款與條件 | 公司 | 公司使用者 |                 
| BYOD 條款與條件 | BYOD | BYOD 使用者 |                


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)將條款與條件對應至使用者群組。

### <a name="configuration-policies"></a>設定原則

您可以使用設定原則來管理裝置的安全性設定和功能。 設計設定原則時，請參閱＜使用案例需求＞一節，決定 Intune 裝置所需的設定。 記錄設定值及應設定的方式。 另外記錄其目標使用者或裝置群組。

每個平台應該至少建立一個設定原則。 如有需要，每個平台可以建立數個設定原則。 下例是用於不同平台和使用案例之四個不同設定原則的設計。

| **原則名稱** | **裝置平台** | **設定** | **目標群組** |   
|:---:|:---:|:---:|:---:|
| 公司 - iOS | iOS | PIN 是必要項，長度︰6，限制雲端備份 | 公司裝置 |                                                           
| 公司 - Android | Android | PIN 是必要項，長度︰6，限制雲端備份 | 公司裝置 |                                                           
| BYOD – iOS  | iOS | PIN 是必要項，長度︰4 | BYOD 裝置 |
| BYOD – Android  | Android | PIN 是必要項，長度︰4 | BYOD 裝置 |


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別設定原則需求。

### <a name="profiles"></a>Profiles

您可以使用設定檔來協助終端使用者連線到公司資料。 Intune 支援許多類型的設定檔。 請參考使用案例和需求，以判斷何時設定設定檔。 所有裝置設定檔依平台類型分類，應該納入設計文件中。

-   憑證設定檔

-   Wi-Fi 設定檔

-   VPN 設定檔

-   電子郵件設定檔

讓我們詳細檢閱每種設定檔類型。

#### <a name="certificate-profiles"></a>憑證設定檔

憑證設定檔可讓 Intune 向使用者或裝置核發憑證。 Intune 支援下列項目：

-   簡單憑證註冊通訊協定 (SCEP)

-   受信任的根憑證

-   PFX 憑證。

建議您記錄哪個使用者群組需要憑證、您需要多少憑證設定檔，以及將它們部署到哪些使用者群組。

>[!NOTE]
> 請記住，SCEP 憑證需要受信任的根憑證，因此請確保所有 SCEP 憑證的目標使用者也會收到受信任的根憑證。 如果您需要 SCEP 憑證，請設計與記錄您需要哪些 SCEP 憑證範本。

下例說明如何在設計期間記錄憑證︰

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| 根 CA | 公司根 CA | Android、iOS、Windows Mobile | 公司、BYOD  |                                                           
| SCEP | 使用者憑證 | Android、iOS、Windows Mobile | 公司、BYOD |                                                           


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別憑證設定檔需求。

#### <a name="wi-fi-profile"></a>Wi-Fi 設定檔

Wi-Fi 設定檔用來自動將行動裝置連線到無線網路。 Intune 支援將 Wi-Fi 設定檔部署到所有支援的平台。 深入了解[將裝置設為連接至您的公司 Wi-Fi 網路](wi-fi-settings-configure.md)

下例是 Wi-Fi 設定檔的設計︰

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | 亞洲 Wi-Fi 設定檔 | Android | 公司、BYOD 亞洲地區|                                                           
| Wi-Fi | 北美地區 Wi-Fi 設定檔 | Android、iOS、Windows 10 Mobile | 公司、BYOD 北美地區 |                                                           


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別 Wi-Fi 設定檔需求。

#### <a name="vpn-profile"></a>VPN 設定檔

VPN 設定檔讓使用者從遠端位置安全存取您的網路。 Intune 支援原生行動 VPN 連線和協力廠商的 VPN 設定檔。 深入了解 [Microsoft Intune 中的 VPN 連線](vpn-settings-configure.md)。

下例說明記錄 VPN 設定檔的設計。

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco 任何連線設定檔 | Android、iOS、Windows 10 Mobile | 公司、BYOD 北美地區及德國|                                                           
| VPN | Pulse Secure | Android | 公司、BYOD 亞洲地區 |                                                           


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別 VPN 設定檔需求。
#### <a name="email-profile"></a>電子郵件設定檔

電子郵件設定檔允許電子郵件用戶端自動設定連線資訊與電子郵件設定。 Intune 支援某些裝置上的電子郵件設定檔。 深入了解[電子郵件設定檔和支援的平台](email-settings-configure.md)。

下例說明記錄電子郵件設定檔的設計：

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| 電子郵件設定檔 | iOS 電子郵件設定檔 | iOS | 公司 – 資訊工作者 BYOD |                                                           
| 電子郵件設定檔 | Android Knox 電子郵件設定檔 | Android Knox | BYOD |


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別電子郵件設定檔需求。
### <a name="apps"></a>應用程式

您可以使用 Intune 透過數種方式向使用者或裝置遞送應用程式。 應用程式類型包括軟體安裝程式應用程式、公用應用程式市集的應用程式、外部連結，或受管理的 iOS 應用程式。 除了個別的應用程式部署，您可以透過 iOS 和 Windows 的大量採購方案管理和部署大量採購的應用程式。 深入了解：

-   [您可以遞送的應用程式類型](app-management.md)

-   [商務用 iOS 大量採購方案 (VPP)](vpp-apps-ios.md)

-   [商務用 Microsoft 網上商店應用程式](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>應用程式類型需求

因為可以將應用程式部署至使用者和裝置，所以建議您決定哪些應用程式會由 Intune 管理。 收集清單時，請嘗試回答下列問題︰

-   應用程式是否需要與雲端服務整合？

-   所有應用程式都可供 BYOD 使用者使用嗎？

-   這些應用程式有哪些部署選項可用？

-   貴公司需要為協力廠商提供軟體即服務 (SaaS) 應用程式資料的存取權嗎？

-   應用程式是否需要從使用者裝置存取網際網路？

-   應用程式是從應用程式市集公開取得，還是自訂的企業營運 (LOB) 應用程式？


#### <a name="app-protection-policies"></a>應用程式保護原則

應用程式保護原則透過定義應用程式管理公司資料的方式，減少資料遺失。 Intune 支援為配合行動裝置應用程式管理而建置的任何應用程式的應用程式保護原則。 當您設計應用程式保護原則時，您需要決定想在指定的應用程式中對公司資料設置的限制。 建議您檢閱[應用程式保護原則](app-protection-policy.md)如何運作。 下例說明如何記錄現有的應用程式以及需要何種保護。

| **應用程式** | **目的** | **平台** | **使用案例** | **應用程式保護原則** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | 可用 | iOS | 公司 - 主管 | 不可破解、加密檔案 |                                                         
| Word | 可用 | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | 公司、BYOD | 不可破解、加密檔案 |                                                         


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別應用程式保護原則需求。
#### <a name="compliance-policies"></a>合規性政策

相容性原則決定裝置是否符合特定需求。 Intune 使用相容性原則判斷裝置視為相容或不相容。 相容性狀態也可用來限制或允許存取公司資源。 如果需要條件式存取，建議您設計[裝置相容性原則](device-compliance.md)。

請參考需求和使用案例，判斷您需要多少裝置相容性原則以及哪些使用者群組是目標使用者群組。 此外，您還需要決定，裝置離線多久不簽入，才會視為不相容。

下例說明如何設計相容性原則︰

| **原則名稱** | **裝置平台** | **設定** | **目標群組** |   
|:---:|:---:|:---:|:---:|
| 相容性原則 | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | PIN - 必要項、不能破解 | 公司、BYOD |


您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別合規性政策需求。
#### <a name="conditional-access-policies"></a>條件式存取原則

條件式存取用於僅允許相容裝置存取電子郵件和其他公司資源。 Intune 可搭配 Enterprise Mobility + Security (EMS) 控制對公司資源的存取。 您必須決定條件式存取是否必要，以及必須保護的項目。 深入了解[使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取](conditional-access.md)。

為線上存取，決定哪些平台和使用者群組會是條件式存取原則的目標。 此外，請判斷您是否需要針對 Exchange Online 或 Exchange 內部部署安裝或設定 Intune 服務對服務連接器。 深入了解如何安裝及設定 Intune 服務對服務連接器︰<!---these links are correct--->

-   [Exchange Online](/intune-classic/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange 內部部署](exchange-connector-install.md)

下例說明如何記錄條件式存取原則︰

| **服務** | **新式驗證的平台** | **基本驗證** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS、Android | 封鎖 Intune 支援平台上不相容的裝置 | 公司、BYOD |
| SharePoint Online | iOS、Android |  | 公司、BYOD |

您可以[下載上述資料表的範本](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)來識別條件式存取原則需求。

## <a name="next-steps"></a>接下來的步驟

下一節提供有關 [Intune 實作程序](planning-guide-onboarding.md)的指引。
