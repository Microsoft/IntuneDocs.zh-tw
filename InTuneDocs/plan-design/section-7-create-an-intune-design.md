---
title: "建立 Intune 設計 | Microsoft Docs"
description: "本文可協助您建立 Microsoft Intune 僅限雲端設計及實作的設計。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: ab6d9b6b296fb4e1fb0aaa9496fede28976728dc
ms.openlocfilehash: ce51e92f9643ddc77e84e6b4c65825d397a37ddc
ms.lasthandoff: 04/14/2017


---

# <a name="create-an-intune-design"></a>建立 Intune 設計

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

本指南此節應與第 2 節中的其他主題一起使用。 此設計會以您為完成本指南前面幾節所收集的資訊及決定為基礎。 這個設計部分會著重在 Intune 獨立版，也就是 Microsoft 雲端服務。

雖然有基本的內部部署基礎結構需求，但您要有設計計畫，以確定您獲得符合目的、目標和需求的正確行動裝置管理解決方案。

此外，在實作和測試階段也常會發生設計變更，請務必記錄這些變更及其發生背後的原理。 我們繼續討論下列區域︰

-   目前的環境

-   Intune 部署選項

-   外部相依性的身分識別需求

-   裝置平台考量

-   要傳遞的需求  

讓我們詳細檢閱各個區域。 

## <a name="record-your-environment"></a>記錄您的環境

建立設計前的第一步，是記錄目前的環境。 目前的環境會影響設計決策，應該記錄下以來在進行其他 Intune 設計決策時參考。 以下是如何記錄目前環境的一些範例︰

-   **雲端中的身分識別**

    -   您使用 DirSync 還是 Azure Active Directory (AAD) 連線？

    -   您的環境是否為同盟？

    -   是否啟用設定多重要素驗證？

-   **電子郵件環境**

    -   是否使用 Exchange，內部部署或雲端？

    -   是否正在進行將 Exchange 移轉到雲端的專案？

-   **目前的 MDM 解決方案**

    -   您目前使用其他 MDM 解決方案嗎？

    -   公司和 BYOD 使用案例使用的 MDM 解決方案為何？

    -   現在使用哪些功能 (例如應用程式裝置設定、Wi-Fi 設定等等)？

    -   支援的裝置平台有哪些？

    -   哪些群組和有多少使用者使用 MDM 方案？

-   **憑證解決方案**

    -   您實作過憑證解決方案嗎？

    -   您使用何種類型的憑證？

-   **系統管理**

    -   您如何管理電腦和伺服器環境？

    -   使用的是 System Center Configuration Manager 嗎？ 您使用的是協力廠商的系統管理平台嗎？

-   **VPN 解決方案**

    -   您的 VPN 解決方案為何？

    -   同時用於公司和 BYOD 使用案例嗎？

記錄目前的 MDM 環境時，請務必記下目前可對環境進行變更的所有專案或任何其他計畫。 下例是一種記錄目前環境的方式，可在您建立 Intune 設計時提供協助︰

| **解決方案區域** | **目前的環境** | **註解** |
|:---:|:---:|:---:|
| **身分識別** | Azure AD、Azure AD Connect、未同盟、無 MFA | 專案就緒，年底可啟用 MFA |                 
| **電子郵件環境** | Exchange 內部部署、Exchange Online | 目前從 Exchange 內部部署移轉至 Exchange Online。 信箱已移轉 75%。 Intune 試驗開始之前，會移轉最後的 25%。 |                
| **SharePoint** | SharePoint 內部部署 | 不打算移至 SharePoint Online |  
| **目前的 MDM** | Exchange ActiveSync |  |
| **憑證解決方案** | Microsoft Server 2012 R2、AD 憑證服務 | 網站伺服器只使用 PKI |
| **系統管理** | System Center Configuration Manager CB 1606 | 想要調查 Intune 混合式解決方案 |
| **VPN 解決方案** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>選擇 Intune 部署選項

Intune 提供兩種部署選項︰獨立和混合式。 您必須決定哪一種符合您的業務需求。 獨立是指 Intune 服務在雲端中執行，混合式則整合 Intune 與 System Center Configuration Manager。

- 深入了解[在 Microsoft Intune 獨立部署與使用 System Center Configuration Manager 的混合式行動裝置管理之間進行選擇](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Intune 租用戶位置

如果貴組織有全球支援，請務必規劃租用戶訂閱服務時所在的位置。 國家 (地區) 會在您第一次註冊 Intune 訂閱時定義，並對應至全球下列地區︰

-   北美

-   歐洲、中東和非洲地區

-   亞洲及太平洋地區

>[!IMPORTANT]
> 之後無法變更國家 (地區)/租用戶位置。

## <a name="external-dependencies"></a>外部相依性

外部相依性是和 Intune 分開的服務及產品，但卻是 Intune 需求或可能與 Intune 整合。 請務必找出任何外部相依性需求，以及其設定方式。 以下列出一些常見的外部相依性範例。

-   權杖服務 (STS)

-   使用者和裝置群組

-   PKI

下面會更詳細地探索這些常見的外部相依性

### <a name="identity"></a>權杖服務 (STS)

身分識別是我們識別誰是貴組織使用者以及誰註冊裝置的方法。 Intune 需要 Azure Active Directory (Azure AD) 作為使用者身分識別提供者。 如果您已使用這項服務，就可以運用您在雲端中現有的身分識別。 此外，建議使用 Azure AD Connect 同步處理您內部部署的使用者身分識別與 Microsoft 雲端服務。 如果貴組織已使用 Office 365，Intune 使用相同的 Azure Active Directory 環境極為重要。

您可以在下文找到有關 Intune 身分識別需求的詳細資訊。

-   深入了解[設計考量概觀](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)。

-   深入了解[判斷目錄同步處理需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)。

-   深入了解[判斷混合式身分識別解決方案的多重要素驗證需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)。

### <a name="user-and-device-groups"></a>使用者和裝置群組

使用者和裝置群組決定部署的目標。 這可能包括原則、應用程式和設定檔的部署目標。 僅限雲端的 Intune 支援使用者和裝置群組 - 您必須判斷需要哪些使用者和裝置群組。 建議在內部部署 Active Directory 中建立所有群組，再同步處理至 Azure Active Directory。 您可以在下文中找到有關使用者和裝置群組規劃和建立的詳細資訊。

-   深入了解 [Plan your user and device groups](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups) (規劃您的使用者和裝置群組)。

-   了解[在 Microsoft Intune 中使用群組管理使用者和裝置](https://docs.microsoft.com/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。

### <a name="public-key-infrastructure-pki"></a>公開金鑰基礎結構 (PKI)

公開金鑰基礎結構向裝置或使用者提供憑證，以安全的方式向服務進行驗證。 Intune 支援 Microsoft PKI 基礎結構。 裝置和使用者憑證可以核發給行動裝置，以滿足憑證式驗證的需求。 實作憑證之前，您必須先判斷是否需要憑證、網路基礎結構可否支援憑證式驗證，以及現有環境目前是否使用憑證。

如果您打算使用 VPN、Wi-Fi 或電子郵件設定檔憑證和 Intune，您必須確定有受支援的[PKI 基礎結構就緒](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles)，隨時可建立及部署憑證設定檔。

此外，如果要核發 SCEP 憑證，您需要判斷哪部伺服器會裝載網路裝置註冊服務 (NDES) 功能，以及通訊進行的方式。

在 Intune 中設定憑證的詳細資訊：

-   [設定 SCEP 的憑證基礎結構](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep)。

-   [設定 PFX 憑證基礎結構](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx)。

-   [設定 Intune 憑證設定檔](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles)。

-   [使用 Microsoft Intune 存取公司資源](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune)。

## <a name="device-platform-considerations"></a>裝置平台考量

您需要進一步了解您的裝置，才能正確了解它們。

-   判斷支援的裝置平台

-   裝置

-   裝置擁有權

-   大量註冊

讓我們更詳細地檢閱這些區域。

### <a name="determine-supported-device-platforms"></a>判斷支援的裝置平台

您需要知道哪些裝置會放在環境中，並確認 Intune 是否會在建立您的設計時支援它們。 Intune 支援 iOS、Android 和 Windows 平台。

-   深入了解 [Intune 支援的裝置](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)。

### <a name="devices"></a>裝置

Intune 管理行動裝置以保護公司資料，讓終端使用者能夠從更多地點工作。 Intune 支援多重裝置平台，因此建議您記錄貴組織設計中支援的裝置及作業系統平台。 這會擴及＜使用案例需求＞一節中建立的裝置與平台。

也建議您掌握版本參考清單，以便依作業系統平台和版本檢查裝置功能。 範例如下：

| **裝置平台** | **作業系統版本** |
|:---:|:---:|
| iOS - iPhone | 9.0+ |                
| iOS - iPad | 8.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Windows 10 平板電腦 | 10+ |

### <a name="device-ownership"></a>裝置擁有權

Intune 支援公司擁有的和 BYOD 擁有權。 裝置如果是由裝置註冊管理員或裝置註冊程式所註冊，即視為公司擁有的。 例如，裝置可以透過 Apple DEP 註冊，標記為公司，然後放在會接收目標公司原則和應用程式的裝置群組中。

如需公司與 BYOD 使用案例的詳細資訊，請參閱[第 3 節︰決定使用案例的需求](section-3-determine-use-case-requirements.md)。

### <a name="bulk-enrollment"></a>大量註冊

有多個註冊選項可在 Intune 中註冊裝置，透過公司入口網站輔助自助註冊。 有多種方式可以完成大量註冊，視平台而定。 如需大量註冊，請先決定大量註冊方法並納入設計中。 請在下文中尋找不同大量註冊方法的詳細資訊。

-   深入了解[大量註冊](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)。

## <a name="feature-requirements"></a>功能需求

我們會在這些章節中檢視下列符合您使用案例需求的功能︰

-   條款和條件原則

-   設定原則

-   資源設定檔

-   應用程式

-   相容性原則

-   條件式存取

讓我們詳細檢閱各個區域。

### <a name="terms-and-conditions-policies"></a>條款和條件原則

條款和條件可用以說明終端使用者註冊前必須同意的原則或條件。 Intune 支援將多項條款與條件原則新增及部署到使用者群組的能力。 您需要決定是否需要條款和條件原則。 如果是的話，組織中由誰負責提供這項資訊。

-   了解有關 Intune 的 [Microsoft Intune 的條款和條件原則設定](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)。 下例說明如何記錄條款與條件原則。

| **條款及條件名稱** | **使用案例** | **目標群組** |
|:---:|:---:|:---:|
| 公司條款與條件 | 公司 | 公司使用者 |                 
| BYOD 條款與條件 | BYOD | BYOD 使用者 |                

### <a name="configuration-policies"></a>設定原則

設定原則用來管理裝置的安全性設定和功能。 設計設定原則時，請參閱＜使用案例需求＞一節，決定 Intune 裝置所需的設定。 記錄應設定的設定值及方式，同時記錄它們的目標使用者或裝置群組。

每個平台應該至少建立一個設定原則。 如有需要，每個平台可以建立多個設定原則。 下例是用於不同平台和使用案例的四個不同設定原則的設計。

| **原則名稱** | **裝置平台** | **設定** | **目標群組** |   
|:---:|:---:|:---:|:---:|
| 公司 - iOS | iOS | PIN 是必要項，長度︰6，限制雲端備份 | 公司裝置 |                                                           
| 公司 - Android | Android | PIN 是必要項，長度︰6，限制雲端備份 | 公司裝置 |                                                           
| BYOD – iOS  | iOS | PIN 是必要項，長度︰4 | BYOD 裝置 |
| BYOD – Android  | Android | PIN 是必要項，長度︰4 | BYOD 裝置 |

### <a name="profiles"></a>Profiles

設定檔用來協助終端使用者連線到公司資料。 Intune 支援許多類型的設定檔。 請參考使用案例和需求，以判斷何時設定[設定檔](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune)。 所有裝置設定檔依平台類型分類，應該納入設計文件中。

-   憑證設定檔

-   Wi-Fi 設定檔

-   VPN 設定檔

-   電子郵件設定檔

讓我們詳細檢閱每種設定檔類型。

##### <a name="certificate-profiles"></a>憑證設定檔

憑證設定檔可讓 Intune 向使用者或裝置核發憑證。 Intune 支援下列項目：

-   簡單憑證註冊通訊協定 (SCEP)

-   受信任的根憑證

-   PFX 憑證。

建議您記錄哪個使用者群組需要憑證、需要多少憑證設定檔，以及將它們部署到哪些使用者群組。

>[!NOTE]
> 請記住，SCEP 憑證需要受信任的根憑證，因此請確保所有 SCEP 憑證的目標使用者也會收到受信任的根憑證。 如果需要 SCEP 憑證，請設計與記錄需要哪些 SCEP 憑證範本。

下例說明如何在設計期間記錄憑證︰

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| 根 CA | 公司根 CA | Android、iOS、Windows Mobile | 公司、BYOD  |                                                           
| SCEP | 使用者憑證 | Android、iOS、Windows Mobile | 公司、BYOD |                                                           

##### <a name="wi-fi-profile"></a>Wi-Fi 設定檔

Wi-Fi 設定檔用來自動將行動裝置連接到無線網路。 Intune 支援將 Wi-Fi 設定檔部署到所有支援的平台。

-   深入了解[將裝置設為連接至您的公司 Wi-Fi 網路](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune)

下例是 Wi-Fi 設定檔的設計︰

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | 亞洲 Wi-Fi 設定檔 | Android | 公司、BYOD 亞洲地區|                                                           
| Wi-Fi | 北美地區 Wi-Fi 設定檔 | Android、iOS、Windows 10 Mobile | 公司、BYOD 北美地區 |                                                           

##### <a name="vpn-profile"></a>VPN 設定檔

VPN 設定檔讓使用者從遠端位置安全存取您的網路。 Intune 支援原生行動 VPN 連線和協力廠商的 VPN 設定檔。

-   深入了解 [Microsoft Intune 中的 VPN 連線](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune)。

下例說明記錄 VPN 設定檔的設計。

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| VPN | VPN Cisco 任何連線設定檔 | Android、iOS、Windows 10 Mobile | 公司、BYOD 北美地區及德國|                                                           
| VPN | Pulse Secure | Android | 公司、BYOD 亞洲地區 |                                                           

##### <a name="email-profile"></a>電子郵件設定檔

電子郵件設定檔允許電子郵件用戶端自動設定連線資訊與安裝電子郵件設定。 Intune 支援某些裝置上的電子郵件設定檔。

-   深入了解[使用電子郵件設定檔與 Microsoft Intune 來設定公司電子郵件存取權](https://docs.microsoft.com/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune)和支援的平台。

下例說明記錄電子郵件設定檔的設計：

| **類型** | **設定檔名稱** | **裝置平台** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| 電子郵件設定檔 | iOS 電子郵件設定檔 | iOS | 公司 – 資訊工作者 BYOD |                                                           
| 電子郵件設定檔 | Android Knox 電子郵件設定檔 | Android Knox | BYOD |

### <a name="apps"></a>應用程式

Intune 支援以多種方式向使用者或裝置遞送應用程式。 遞送的應用程式類型可能是軟體安裝程式應用程式、公用應用程式市集的應用程式、外部連結，或受管理的 iOS 應用程式。 除了個別的應用程式部署，您可以透過 iOS 和 Windows 的大量採購方案管理和部署大量採購的應用程式。 下文是 Intune 如何支援應用程式和大量採購方案的詳細資訊。

-   深入了解[應用程式類型](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)

-   深入了解 [Manage iOS apps you purchased through a volume-purchase program with Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune) (使用 Microsoft Intune 管理透過大量採購方案購買的 iOS 應用程式)。

-   深入了解[以 Microsoft Intune 管理購自商務用 Windows 市集的應用程式](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune)。

#### <a name="app-type-requirements"></a>應用程式類型需求

因為可以將應用程式部署至使用者和裝置，所以建議您決定哪些應用程式會由 Intune 管理。 收集清單時，請嘗試回答下列問題︰

-   應用程式是否需要與雲端服務整合？

-   所有應用程式都可供 BYOD 使用者使用嗎？

-   這些應用程式有哪些部署選項可用？

-   貴公司需要為協力廠商提供軟體即服務 (SaaS) 應用程式資料的存取權嗎？

-   應用程式是否需要從使用者裝置存取網際網路？

-   應用程式是從應用程式市集公開取得，還是自訂的企業營運應用程式？


>[!TIP]
> 請參閱[使用 Microsoft Intune 新增應用程式](https://docs.microsoft.com/intune/deploy-use/add-apps)。

#### <a name="app-protection-policies"></a>應用程式保護原則

應用程式保護原則透過定義應用程式管理公司資料的方式，減少資料遺失。 Intune 支援為配合行動裝置應用程式管理而建置的任何應用程式的應用程式保護原則。 在設計應用程式保護原則時，您需要決定在指定的應用程式中對公司資料設置的限制。 建議您檢閱[應用程式保護原則](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)如何運作。 下例說明如何記錄現有的應用程式以及需要何種保護。

| **應用程式** | **目的** | **平台** | **使用案例** | **應用程式保護原則** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | 可用 | iOS | 公司 - 主管 | 不可破解、加密檔案 |                                                         
| Word | 可用 | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | 公司、BYOD | 不可破解、加密檔案 |                                                         

#### <a name="compliance-policies"></a>相容性原則

相容性原則決定裝置是否符合特定需求。 Intune 使用相容性原則判斷裝置視為相容或不相容。 相容性狀態也可用來限制存取公司資源。 如果需要條件式存取，建議設計 [Microsoft Intune 的裝置相容性原則](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)。 請參考需求和使用案例，判斷需要多少裝置相容性原則以及哪些使用者群組是目標使用者群組。 此外，您還需要決定，裝置離線多久不簽入，才會視為不相容。

下例說明如何設計相容性原則︰

| **原則名稱** | **裝置平台** | **設定** | **目標群組** |   
|:---:|:---:|:---:|:---:|
| 相容性原則 | iOS、Android - Samsung Knox、非 Knox、Windows 10 Mobile | PIN - 必要項、不能破解 | 公司、BYOD |

#### <a name="conditional-access-policies"></a>條件式存取原則

條件式存取用於僅允許相容裝置存取公司資源。 Intune 適合整個 Enterprise Mobility + Security (EMS) 控制對公司資源的存取。 您必須判斷條件式存取是否必要，以及必須保護的項目。

-   深入了解[使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)。

為線上存取，判斷哪些平台和使用者群組會是條件式存取原則的目標。

此外，您需要判斷 Exchange Online 或 Exchange 內部部署是否需要安裝/設定 Intune 服務對服務連接器。

深入了解如何安裝及設定 Intune 服務對服務連接器︰

-   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange 內部部署](https://docs.microsoft.com/intune/deploy-use/intune-on-premises-exchange-connector)

下例說明如何記錄條件式存取原則︰

| **服務** | **新式驗證的平台** | **基本驗證** | **使用案例** |   
|:---:|:---:|:---:|:---:|
| Exchange Online | iOS、Android | 封鎖 Intune 支援平台上不相容的裝置 | 公司、BYOD |
| SharePoint Online | iOS、Android |  | 公司、BYOD |

## <a name="next-section"></a>下一節

下一節提供有關 [Intune 實作程序](section-8-onboarding-process.md)的指引。

