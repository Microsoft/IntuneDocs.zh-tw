---
title: 應用程式保護原則概觀
titleSuffix: Microsoft Intune
description: 了解 Microsoft Intune 應用程式保護原則如何協助保護公司資料，避免資料遺失。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1c086943-84a0-4d99-8295-490a2bc5be4b
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, get-started, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: f11ccb51e08e96595dfcb9118c1f479f1b0fc3de
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692114"
---
# <a name="app-protection-policies-overview"></a>應用程式保護原則概觀

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

應用程式保護原則 (APP) 是確保組織資料能夠被保護或保留在受控應用程式中的規則。 原則可以是在使用者嘗試存取或移動「公司」資料時，強制執行的一項規則，或者是當使用者在應用程式內時，禁止執行或受到監視的一組動作。 受管理應用程式是已套用應用程式保護原則的應用程式，而且可由 Intune 管理。

行動應用程式管理 (MAM) 應用程式防護原則可讓您管理和保護應用程式內的組織資料。 透過**沒有註冊的 MAM** (MAM-WE)，便幾乎可以管理位於任何[裝置](app-management.md#app-management-capabilities-by-platform)上包含敏感性資料的公司或學校相關應用程式，這包括**攜帶您自己的裝置** (BYOD) 案例中的個人裝置。 許多生產力應用程式 (例如 Microsoft Office 應用程式) 可以由 Intune MAM 管理。 請參閱可供公開使用的 [Microsoft Intune 受保護應用程式](apps-supported-intune-apps.md)官方清單。

## <a name="how-you-can-protect-app-data"></a>如何保護應用程式資料
您的員工使用行動裝置處理公私事務。 確保員工生產力的同時，想要防止故意和不小心的資料外洩。 您還想要保護從您非受控裝置存取的公司資料。

您可以使用 Intune 應用程式保護原則，而**不受任何行動裝置管理 (MDM) 解決方案影響**。 不論是否在裝置管理解決方案中註冊裝置，這項獨立性都可協助您保護貴公司的資料。 您可以實作**應用程式層級原則**，以限制存取公司資源，並將資料保留在 IT 部門範疇內。

### <a name="app-protection-policies-on-devices"></a>裝置上的應用程式防護原則

可為裝置上執行的應用程式所設定應用程式保護原則，包括下列：

- **在 Microsoft Intune 中註冊：** 這些裝置通常是公司所擁有的裝置。

- **在協力廠商的行動裝置管理 (MDM) 解決方案中註冊：** 這些裝置通常是公司所擁有的裝置。

  > [!NOTE]
  > 行動應用程式管理原則不應搭配使用協力廠商的行動應用程式管理或安全容器解決方案。

- **未在任何行動裝置管理解決方案中註冊：** 這些裝置通常是員工所擁有的裝置，且沒有在 Intune 或其他 MDM 解決方案中受控或註冊。

> [!IMPORTANT]
> 您可以為連接至 Office 365 服務的 Office 行動應用程式建立行動應用程式管理原則。 您也可以透過建立適用於 iOS 版 Outlook 以及已啟用混合式新式驗證的 Android 的 Intune 應用程式保護原則，來保護對 Exchange 內部部署信箱的存取。 開始使用此功能之前，請確定您符合 [iOS 版和 Android 版 Outlook 的需求](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx)。 連線到內部部署 Exchange 或 SharePoint 服務的其他應用程式不支援應用程式保護原則。

## <a name="benefits-of-using-app-protection-policies"></a>使用應用程式保護原則的優點

使用應用程式保護原則的重要優點如下：

- **在應用程式層級保護公司資料。** 因為行動應用程式管理不需要裝置管理，您可以同時在受控與非受控的裝置上保護公司資料。 管理的重心是使用者身分識別，不需要管理裝置。

- **終端使用者生產力不受影響，且在個人環境內使用應用程式時，不會套用原則。** 原則只會套用在工作內容上，所以您能夠在不碰到個人資料的情況下保護公司資料。

- **應用程式保護原則可確保應用程式層保護就定位。** 例如，您可以：
  - 需要 PIN 才能在工作環境中開啟應用程式 
  - 控制應用程式之間的資料共用 
  - 防止將公司應用程式資料儲存到個人儲存位置

- **除了 MAM 以外，MDM 也會確保裝置受到保護**。 例如，您可以要求存取裝置的 PIN，或者將受管理的應用程式部署到裝置。 也可以透過 MDM 解決方案將應用程式部署到裝置，取得對應用程式管理的更多控制。

搭配使用 MDM 與應用程式保護原則還有其他多項優點，且公司可以在使用或不使用 MDM 的狀況下使用應用程式保護原則。 例如，請考慮使用公司所核發手機和自己個人平板電腦的員工。 公司的手機會在 MDM 中註冊，並受到應用程式保護原則的保護，而個人裝置只會受到應用程式保護原則的保護。

如果您在未設定裝置狀態的情況下將 MAM 原則套用至使用者，則使用者將在 BYOD 裝置和 Intune 管理的裝置上取得 MAM 原則。 您也可以根據受控狀態來套用 MAM 原則。 因此，當您建立應用程式保護原則時，請在 [以所有應用程式類型為目標]  旁邊選取 [否]  。 接著，執行下列其中一項動作：
- 將較不嚴格的 MAM 原則套用至 Intune 管理的裝置，並將較嚴格的 MAM 原則套用至非 MDM 註冊的裝置。
- 僅將 MAM 原則套用至未註冊的裝置。

## <a name="supported-platforms-for-app-protection-policies"></a>支援應用程式保護原則的平台

Intune 提供各種功能，可協助您在所要的裝置上取得所需的應用程式並執行。 如需詳細資訊，請參閱[各種平台的應用程式管理功能](app-management.md#app-management-capabilities-by-platform)。

Intune 應用程式保護原則平台支援與 Office 行動應用程式平台支援，在針對 Android 和 iOS 上是一致的。 如需詳細資料，請參閱 [Office 系統需求](https://products.office.com/office-system-requirements#coreui-contentrichblock-9r05pwg)的**行動應用程式**一節。

> [!IMPORTANT]
> 裝置上需要有 Intune 公司入口網站，才能在 Android 上接收 [應用程式保護原則]。 如需詳細資訊，請參閱 [Intune 公司入口網站存取應用程式需求](../fundamentals/end-user-mam-apps-android.md#access-apps)。

## <a name="how-app-protection-policies-protect-app-data"></a>應用程式保護原則如何保護應用程式資料

### <a name="apps-without-app-protection-policies"></a>沒有應用程式保護原則的應用程式

在沒有條件限制下使用應用程式時，公司和個人資料會互相混合。 公司資料最終會放在個人儲存空間等位置或傳送到範圍外的應用程式，進而導致資料外洩。 下圖中的箭號顯示資料在公司與個人應用程式之間無限制地移動和移至儲存位置。

![沒有原則時在應用程式之間移動資料的概念影像](./media/app-protection-policy/apps-without-protection-policies.png)

### <a name="data-protection-with-app-protection-policies-app"></a>使用應用程式保護原則 (APP) 保護資料

您可以使用應用程式保護原則來防止公司資料儲存到裝置的本機儲存體 (請參閱下圖)。 您也可以限制將資料移到其他未受應用程式保護原則保護的應用程式。 應用程式保護原則設定包括︰
- 資料重新配置原則，如 [儲存組織資料複本]  和 [限制剪下、複製及貼上]  。
- 存取原則設定，例如 [需要簡單 PIN 碼才可存取]  、[禁止受控應用程式在經 JB 或 Root 破解的裝置上執行]  。

![顯示公司資料正受原則保護的概念影像](./media/app-protection-policy/apps-with-protection-policies.png)

### <a name="data-protection-with-app-on-devices-managed-by-an-mdm-solution"></a>在 MDM 解決方案所管理的裝置上使用應用程式保護資料

下圖顯示 MDM 與應用程式保護原則共同提供的多層保護。

![此圖顯示應用程式保護原則在 BYOD 裝置上的運作方式](./media/app-protection-policy/app-protection-policies-with-mdm.png)

MDM 解決方案會藉由提供下列各項來增加價值：

- 註冊裝置
- 將應用程式部署至裝置
- 提供持續的裝置合規性和管理

應用程式防護原則會藉由提供下列各項來增加價值：

- 協助保護公司資料不外洩至消費性應用程式和服務
- 將「另存新檔」  、「剪貼簿」  或 *PIN* 等限制套用到用戶端應用程式
- 必要時抹除應用程式中的公司資料，但不從裝置移除那些應用程式

### <a name="data-protection-with-app-for-devices-without-enrollment"></a>在沒有註冊的裝置上使用應用程式保護資料

下圖說明在沒有 MDM 的情況下，資料保護原則於應用程式層級的運作方式。

![顯示應用程式保護原則在沒有註冊的裝置 (非受控裝置) 上運作方式的影像](./media/app-protection-policy/app-protection-policies-without-mdm.png)

對於未在任何 MDM 解決方案中註冊的 BYOD 裝置，應用程式保護原則可在應用程式層級保護公司資料。
但有一些限制需要注意，例如：

- 您無法將應用程式部署到裝置。 使用者必須從存放區取得應用程式。
- 您無法在這些裝置上佈建憑證設定檔。
- 您無法在這些裝置上佈建公司 Wi-Fi 和 VPN 設定。

## <a name="apps-you-can-manage-with-app-protection-policies"></a>您可以使用應用程式保護原則管理的應用程式

與 [Intune App SDK](../developer/app-sdk.md) 整合或由 [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) 包裝的應用程式，都可以使用應用程式保護原則加以管理。 查看已使用這些工具建置並可供公開使用的 [Microsoft Intune 受保護應用程式](apps-supported-intune-apps.md)官方清單。

Intune SDK 開發小組會針對用原生 Android、iOS (Obj-C、Swift)、Xamarin、Xamarin.Forms 及 Cordova 平台所建置的應用程式，主動地進行測試並維護支援。 雖然有部分客戶成功搭配其他平台 (例如 React Native 和 NativeScript) 整合 Intune SDK，我們並沒有針對使用我們所不支援之平台的應用程式開發人員提供明確的指引或外掛程式。

[Intune App SDK](../developer/app-sdk.md) 會針對第 1 方和第 3 方版本的 SDK，使用 [Azure Active Directory 驗證程式庫](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) (ADAL) \(部分機器翻譯\) 中一些先進的新式驗證功能。 因此，[Microsoft 驗證程式庫](https://docs.microsoft.com/azure/active-directory/develop/reference-v2-libraries) \(部分機器翻譯\) (MSAL) 並不適用於我們許多的核心案例，例如向 Intune 應用程式防護服務進行驗證，以及條件式啟動。 有鑑於來自 Microsoft 身分識別小組的整體指示是要將所有 Microsoft Office 應用程式切換至 MSAL，[Intune App SDK](../developer/app-sdk.md) 未來一定會需要支援它，但目前尚未有確切計畫。

## <a name="end-user-requirements-to-use-app-protection-policies"></a>使用應用程式防護原則的終端使用者需求

下列清單提供在 Intune 受控應用程式上使用應用程式防護原則的終端使用者需求：

- 終端使用者必須擁有 Azure Active Directory (AAD) 帳戶。 請參閱[新增使用者並提供管理權限給 Intune](../fundamentals/users-add.md)，以了解如何在 Azure Active Directory 中建立 Intune 使用者。

- 終端使用者必須擁有指派給其 Azure Active Directory 帳戶的 Microsoft Intune 授權。 請參閱[管理 Intune 授權](../fundamentals/licenses-assign.md)，以了解如何將 Intune 授權指派給終端使用者。

- 終端使用者必須隸屬於由應用程式保護原則設為目標的安全性群組。 相同的應用程式保護原則必須將已使用的特定應用程式設為目標。 應用程式保護原則可在 [Azure 入口網站](https://portal.azure.com)中的 Intune 主控台中建立與部署。 安全群組目前可在 [Microsoft 365 糸統管理中心](https://admin.microsoft.com)內建立。

- 終端使用者必須使用其 AAD 帳戶來登入應用程式。

## <a name="app-protection-policies-for-microsoft-office-apps"></a>Microsoft Office 應用程式的應用程式防護原則

使用應用程式防護原則搭配 Microsoft Office 應用程式時，需要注意幾個額外的需求。

### <a name="outlook-mobile-app"></a>Outlook 行動應用程式
使用 [Outlook 行動應用程式](https://products.office.com/outlook)的其他需求包括下列各項：

- 終端使用者必須在其裝置上安裝 Outlook 行動裝置應用程式。
- 終端使用者必須具有連結到其 Azure Active Directory 帳戶的 [Office 365 Exchange Online](https://products.office.com/exchange/exchange-online) 信箱和授權。

  >[!NOTE]
  > Outlook 行動應用程式目前僅針對 Microsoft Exchange Online 和[具有混合式新式驗證的 Exchange Server](https://technet.microsoft.com/library/mt846639(v=exchg.160).aspx) 支援「Intune 應用程式防護」，而不支援「Office 365 專用」中的 Exchange。

### <a name="word-excel-and-powerpoint"></a>Word、Excel 和 PowerPoint
使用 [Word、Excel 與 PowerPoint](https://products.office.com/business/office) 應用程式的其他需求包括下列各項：

- 終端使用者必須擁有連結到其 Azure Active Directory 帳戶的 [Office 365 商務版或企業版](https://products.office.com/business/compare-more-office-365-for-business-plans)授權。 訂用帳戶必須包括行動裝置版 Office 應用程式，而且可以包括[商務用 OneDrive](https://onedrive.live.com/about/business/) 的雲端儲存體帳戶。 Office 365 授權可在 [Microsoft 365 系統管理中心](https://admin.microsoft.com)內根據這些[指示](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)指派。

- 使用者必須有受控的位置，此位置是使用 [儲存組織資料複本] 應用程式保護原則設定下的細微另存新檔功能所設定。 例如，若受控位置是 OneDrive，則 [OneDrive](https://onedrive.live.com/about/) 應用程式應該在終端使用者的 Word、Excel 或 PowerPoint 應用程式中設定。

- 若受控位置是 OneDrive，則應用程式必須是部署到終端使用者之應用程式保護原則的目標。

  >[!NOTE]
  > Office 行動裝置應用程式目前僅支援 SharePoint Online，不支援 SharePoint 內部部署。

### <a name="managed-location-needed-for-office"></a>Office 所需的受控位置
Office 所需的受控位置 (例如 OneDrive)。 Intune 會將應用程式中的所有資料標示為「公司」或「個人」。 當資料來自公司地點時，會將資料視為「公司」資料。 針對 Office 應用程式，Intune 會將下列位置視為公司地點：電子郵件 (Exchange) 或雲端儲存體 (包含商務用 OneDrive 帳戶的 OneDrive 應用程式)。

### <a name="skype-for-business"></a>商務用 Skype
使用商務用 Skype 還有其他需求。 請參閱[商務用 Skype](https://products.office.com/skype-for-business/it-pros) 授權需求。 如需商務用 Skype (SfB) 的混合式和內部部署設定，請分別參閱 [Hybrid Modern Auth for SfB and Exchange goes GA](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Hybrid-Modern-Auth-for-SfB-and-Exchange-goes-GA/ba-p/134756) (正式推出適用於 SfB 和 Exchange 的混合式新式驗證) 和 [Modern Auth for SfB OnPrem with AAD](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Modern-Auth-for-SfB-OnPrem-with-AAD/ba-p/180910) (使用 AAD 啟用適用於 SfB 內部部署的新式驗證)。

## <a name="app-protection-global-policy"></a>應用程式保護的全域原則

如果 OneDrive 系統管理員瀏覽至 **admin.office.com** 並選取 [裝置]  存取，他們可以設定 OneDrive 和 SharePoint 用戶端應用程式的 [行動應用程式管理]  控制項。 

這些設定會開放給 OneDrive 管理主控台使用，可設定稱為**全域**原則的特殊 Intune 應用程式保護原則。 此全域原則適用於租用戶中的所有使用者，且無法控制原則目標。 

一旦啟用，適用於 iOS 和 Android 的 OneDrive 和 SharePoint 應用程式預設會以選取的設定進行保護。 IT 專業人員可以在 Intune 主控台中編輯此原則，以新增更多目標應用程式，並修改任何原則設定。 

根據預設，每個租用戶只能有一個**全域**原則。 不過，您可以使用 [Intune 圖形 API](../developer/intune-graph-apis.md) 來建立每個租用戶的額外全域原則，但不建議這樣做。 因為針對這類原則的實作進行疑難排解會變得很複雜，所以不建議建立額外的全域原則。

雖然**全域**原則會套用到租用戶中的所有使用者，但任何標準的 Intune 應用程式保護原則都會覆寫這些設定。

## <a name="app-protection-features"></a>應用程式保護功能

### <a name="multi-identity"></a>多重身分識別

多重身分識別支援可讓應用程式支援多個對象。 這些對象同時是「公司」使用者和「個人」使用者。 公司和學校帳戶是由「公司」對象使用，而個人帳戶則會針對消費者對象使用 (例如 Microsoft Office 使用者)。 支援多重身分識別的應用程式可公開發行，其中應用程式防護原則只適用於在公司和學校 (「公司」) 內容中使用應用程式的情況。 多重身分識別支援使用 [Intune App SDK](../developer/app-sdk.md) 僅將應用程式防護原則套用至已登入應用程式之公司或學校帳戶的功能。 如果個人帳戶已登入應用程式，就不會更動資料。

舉一個個人內容的範例，想像有一個使用者在 Word 中開始一個新文件，這會被系統視為「個人」內容，因此不會套用 Intune 應用程式防護原則。 當該使用者把文件儲存到「公司」OneDrive 帳戶上時，系統便會把該文件視為「公司」內容，並套用 Intune 應用程式防護原則。

舉一個工作或「公司」內容的範例，想像有一個使用其公司帳戶來啟動 OneDrive 應用程式的使用者。 在工作環境中，他們無法將檔案移至個人儲存位置。 之後，當使用者以個人帳戶使用 OneDrive 時，他們可以從個人 OneDrive 複製並移動資料，而沒有任何限制。

Outlook 具有「個人」和「公司」電子郵件的合併電子郵件檢視。 在此情況下，Outlook 應用程式會在啟動時提示您提供 Intune PIN。

如需 Intune 中多重身分識別的詳細資訊，請參閱 [MAM 和多重身分識別](apps-supported-intune-apps.md)。

### <a name="intune-app-pin"></a>Intune 應用程式 PIN

個人識別碼 (PIN) 是一組密碼，用來驗證在應用程式中存取組織資料的是正確的使用者。

**PIN 提示**<br>
Intune 會在使用者要存取「公司」資料時，提示使用者提供應用程式 PIN。 在多重身分識別應用程式 (例如 Word、Excel 或 PowerPoint) 中，系統會在使用者嘗試開啟「公司」文件或檔案時提示他們提供 PIN。 在單一身分識別應用程式 (例如使用 [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) 管理的企業營運應用程式) 中，系統會在啟動時提示提供 PIN，因為 [Intune App SDK](../developer/app-sdk.md) 知道使用者在該應用程式中的體驗一律會是「公司」。

**PIN 提示，或公司認證提示，頻率**<br>
IT 系統管理員可以在 Intune 管理主控台中定義 Intune 應用程式防護原則設定 [重新檢查存取需求前的剩餘時間 (分鐘)]  。 這項設定會指定多久之後要在裝置上檢查存取要求，並再次顯示應用程式 PIN 畫面或公司認證提示。 不過，還有下列關於 PIN 的重要詳細資料會影響使用者收到通知的頻率：

- **PIN會在相同發行者的應用程式間共用，以改進可用性：**<br> 在 iOS 上，應用程式個人識別碼會在**相同應用程式發行者**的所有應用程式之間共用。 例如，所有 Microsoft 應用程式會共用相同的 PIN。 在 Android，一組應用程式 PIN 會在所有應用程式間共用。
- **裝置重新開機後的 [重新檢查存取需求前的剩餘時間 (分鐘)]  行為：**<br> 計時器會追蹤閒置的分鐘數，可判斷何時顯示下一個 Intune 應用程式 PIN 或公司認證提示。 在 iOS 上，計時器不會受到裝置重新啟動的影響。 因此，裝置重新啟動不會影響使用者在使用 Intune PIN (或公司認證) 原則的 iOS 應用程式中閒置的分鐘數。 在 Android 上，計時器會在裝置重新開機時重設。 因此，使用 Intune PIN (或公司認證) 原則的 Android 應用程式可能會提示輸入應用程式 PIN 或公司認證提示，而不論**裝置重新開機之後**的「重新檢查存取需求前等候時間 (分鐘)」設定值。  
- **與 PIN 相關的計時器過時性質：**<br> 在輸入 PIN 以存取應用程式 (應用程式 A) 之後，應用程式會離開裝置的前景 (主要輸入焦點)，而該組 PIN 的計時器會重設。 由於計時器已經重設，共用這組 PIN 的任何應用程式 (應用程式 B) 都不會提示使用者輸入 PIN。 提示會在再次達到「重新檢查存取需求前等候時間 (分鐘)」值時再度顯示。

若為 iOS 裝置，即使在不同發行者的應用程式之間共用 PIN，當非主要輸入焦點之應用程式的 「重新檢查存取需求前等候時間 (分鐘)」  值再次達到時，就會再度顯示提示。 例如，使用者有發行者 _X_ 的應用程式 _A_ 和發行者 _Y_ 的應用程式 _B_，而且這兩個應用程式共用相同的 PIN。 使用者將焦點放在應用程式 _A_ (前景)，並將應用程式 _B_ 最小化。 達到 「重新檢查存取需求前等候時間 (分鐘)」  值，而且使用者切換至應用程式 _B_ 之後，則需要 PIN。

  >[!NOTE]
  > 為了提高驗證使用者存取需求的頻率 (亦即 PIN 提示)，尤其是經常使用的應用程式，建議您降低「重新檢查存取需求前等候時間 (分鐘)」設定的值。

**適用於 Outlook 和 OneDrive 的內建應用程式 PIN**<br>
Intune PIN 會根據以閒置為基礎的計時器 ( [重新檢查存取需求前的剩餘時間 (分鐘)]  的值) 運作。 因此，Intune PIN 提示會與 Outlook 和 OneDrive 的內建應用程式 PIN 提示分開顯示，後者預設通常與應用程式啟動相關。 如果使用者同時收到兩個 PIN 提示，預期的行為應該是優先使用 Intune PIN。

**Intune PIN 安全性**<br>
PIN 是用來允許僅有正確的使用者可以存取應用程式中的組織資料。 因此，終端使用者必須使用他們的公司或學校帳戶登入，之後才能設定或重設其 Intune 應用程式 PIN。 這個驗證是由 Azure Active Directory 透過安全性權杖交換來處理，且未向 [Intune App SDK](../developer/app-sdk.md) 公開。 從安全性角度來看，保護工作或學校資料的最佳方式是將資料加密。 加密與應用程式 PIN 無關，而是其本身的應用程式保護原則。

**Intune PIN - 防範暴力密碼破解攻擊**<br>
做為應用程式 PIN 原則的一部份，IT 系統管理員可以設定在鎖定應用程式之前，使用者可以嘗試驗證其 PIN 的次數上限。 當嘗試次數達到上限之後，[Intune App SDK](../developer/app-sdk.md) 可以抹除應用程式中的「公司」資料。
  
**在同一個發行者的應用程式上設定 PIN 兩次？**<br>
MAM (在 iOS 上) 目前允許應用程式層級 PIN 包含英數字元與特殊字元 (稱為「密碼」)，這需要應用程式 (亦即 WXP、Outlook、Managed Browser、Yammer) 參與以整合[適用於 iOS 的 Intune APP SDK](../developer/app-sdk-ios.md)。 如果沒有，密碼設定將不會正確地針對目標應用程式強制執行。 這是在「適用於 iOS 7.1.12 版的 Intune SDK」中推出的功能 。

為了支援此功能，並確保對其他版本「適用於 iOS 的 Intune SDK」的回溯相容性，7.1.12 及更新版本中的所有 PIN (不論數字或密碼)，都與先前 SDK 版本中的數字 PIN 分開處理。 因此，如果裝置上有來自同一個發行者的多個應用程式，且其使用的「適用於 iOS 的 Intune SDK」有 7.1.12 之前和 7.1.12 之後的版本，則這些應用程式必須設定兩次 PIN。 這兩個 PIN (針對每個應用程式) 沒有任何關係 (亦即，它們必須遵守套用至應用程式的應用程式保護原則)。 確切地說，只有  當應用程式 A 和 B 套用相同的原則 (相對於 PIN) 時，使用者才需要設定相同的 PIN 兩次。 

針對啟用了「Intune 行動裝置應用程式管理」的 iOS 應用程式，這是應用程式上的 PIN 特有的行為。 一段時間之後，隨著應用程式採用較新版的「適用於 iOS 的 Intune SDK」，需要針對同一個發行者的應用程式設定 PIN 兩次的問題就會減少。 如需範例，請查看下面的注意事項。

  >[!NOTE]
  > 例如，若應用程式 A 是使用 7.1.12 前的版本建置，而相同發行者的應用程式 B 是使用 7.1.12 或之後的版本建置，當 A 和 B 安裝在同一部 iOS 裝置上時，終端使用者將需要針對兩者分別設定 PIN。
  > 如果 SDK 版本是 7.1.9 的應用程式 C 安裝在該裝置上，則它會和應用程式 A 共用相同的 PIN。使用 7.1.14 建置的應用程式 D 將與應用程式 B 共用相同的 PIN。  
  > 如果只有應用程式 A 和 C 安裝在同一部裝置上，則只需要設定一個 PIN。 只有應用程式 B 和 D 安裝在同一部裝置上的情況也是如此。

### <a name="app-data-encryption"></a>應用程式資料加密
IT 系統管理員可以部署要求將應用程式資料加密的應用程式保護原則。 做為原則的一部分，IT 系統管理員也可以指定將內容加密的時機。

**Intune 資料加密的處理方式**<br> 如需加密應用程式保護原則設定的詳細資訊，請參閱 [Android 應用程式保護原則設定](app-protection-policy-settings-android.md)和 [iOS 應用程式保護原則設定](app-protection-policy-settings-ios.md)。

**已加密的資料**<br>
僅有標示為「公司」的資料會根據 IT 系統管理員的應用程式保護原則加密。 當資料來自公司地點時，會將資料視為「公司」資料。 針對 Office 應用程式，Intune 會將下列內容視為商務位置：

- 電子郵件 (Exchange) 
- 雲端儲存體 (使用商務用 OneDrive 帳戶的 OneDrive 應用程式)

針對由 [Intune App Wrapping Tool](../developer/apps-prepare-mobile-application-management.md) 管理的企業營運應用程式，所有的應用程式資料都將視為「公司」資料。

**從遠端抹除資料**<br>
Intune 可以用三種不同的方式抹除應用程式資料： 
- 完整裝置抹除
- 適用於 MDM 的選擇性抹除 
- MDM 選擇性抹除

如需 MDM 遠端抹除的詳細資訊，請參閱[使用抹除或淘汰來移除裝置](../remote-actions/devices-wipe.md)。 如需使用 MAM 選擇性抹除的詳細資訊，請參閱[淘汰動作](../remote-actions/devices-wipe.md#retire)和[如何只抹除應用程式中的公司資料](apps-selective-wipe.md)。

[抹除](../remote-actions/devices-wipe.md)會移除**裝置**的所有使用者資料和設定，方法是將裝置還原為其原廠預設設定。 並從 Intune 移除裝置。

  >[!NOTE]
  > 抹除只能在已向 Intune 行動裝置管理 (MDM) 註冊的裝置上執行。

**適用於 MDM 的選擇性抹除**<br>
請參閱[移除裝置 - 淘汰](../remote-actions/devices-wipe.md#retire)，以閱讀移除公司資料的相關資訊。

**適用於 MAM 的選擇性抹除**<br>
MAM 選擇性抹除僅會從應用程式移除公司應用程式資料。 該要求是使用 Intune Azure 入口網站來起始的。 若要了解如何起始抹除要求，請參閱[如何只抹除應用程式中的公司資料](apps-selective-wipe.md)。

如果使用者在起始選擇性抹除時正在使用應用程式，[Intune App SDK](../developer/app-sdk.md) 每隔 30 分鐘就會檢查來自 Intune MAM 服務的選擇性抹除要求。 它也會在使用者首次啟動應用程式並以其工作或學校帳戶登入時檢查選擇性抹除。

**當內部部署 (on-prem) 服務無法搭配受 Intune 保護的應用程式運作時**<br>
Intune 應用程式防護會取決於使用者的身分識別，以在應用程式與 [Intune App SDK](../developer/app-sdk.md) 之間保持一致。 保證一致的唯一方式是透過新式驗證。 有些案例中，應用程式可搭配內部部署組態運作，但是不保證一定運作。

**從受控應用程式開啟網頁連結的安全方式**<br>
IT 系統管理員可以針對 [Intune Managed Browser 應用程式](app-configuration-managed-browser.md)部署與設定應用程式保護原則，這是由 Microsoft Intune 開發的網頁瀏覽器，可輕鬆地利用 Intune 加以管理。 針對 Intune 受控應用程式，IT 系統管理員可以要求其中的所有網頁連結都必須使用 Managed Browser 應用程式來開啟。

## <a name="examples-of-app-protection-policies"></a>應用程式防護原則的範例

若要深入了解應用程式防護原則範例，並查看每個應用程式防護原則設定的詳細資訊，請參閱 [Android 應用程式防護原則設定](app-protection-policy-settings-android.md)與 [iOS 應用程式防護原則設定](app-protection-policy-settings-ios.md)。

## <a name="app-protection-experience-for-ios-devices"></a>iOS 裝置的應用程式防護體驗

### <a name="device-fingerprint-or-face-ids"></a>裝置指紋或 Face ID 
Intune 應用程式防護原則可控制應用程式只存取 Intune 授權使用者。 控制應用程式存取的其中一種方式，就是在支援裝置上要求 Apple 的 Touch ID 或 Face ID。 如果裝置的生物特徵辨識資料庫有任何變更，Intune 會在下次達到非使用狀態逾時值時，提示使用者輸入 PIN。 對生物特徵辨識資料所做的變更包括新增或移除指紋或臉部。 如果 Intune 使用者未設定 PIN，則會引導他們設定一個 Intune PIN。
 
此程序的用意是為了持續確保應用程式內組織資料的安全，並在應用程式層級受到保護。 此功能僅適用於 iOS，並需要整合 Intune APP SDK for iOS 9.0.1 版或更新版本的應用程式參與。 您必須整合此 SDK，才能針對目標應用程式強制執行該行為。 這項整合會輪流發生並取決於特定的應用程式小組。 參與的一些應用程式包括 WXP、Outlook、Managed Browser 和 Yammer。
  
### <a name="ios-share-extension"></a>iOS 共用延伸模組
您可以使用 iOS 共用延伸模組在非受控應用程式中開啟公司或學校資料，即使在資料傳輸原則已設定為 [僅限受控應用程式]  或 [沒有應用程式]  的情況下也可以。 Intune 應用程式保護原則必須管理裝置才能控制 iOS 共用延伸模組。 因此，Intune _**會先加密「公司」資料，才會在應用程式之外共用**_ 。 您可以嘗試在受控應用程式外開啟「公司」檔案來驗證此加密行為。 檔案應已加密且無法在受管理的應用程式之外開啟。

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>相同應用程式和使用者集合的多個 Intune 應用程式防護存取設定
Intune 應用程式防護存取原則，在使用者嘗試從其公司帳戶存取目標應用程式時，會以特定順序套用在終端使用者裝置上。 一般情況下，其順序會是抹除、封鎖及可關閉的警告。 例如，如果適用於特定的使用者/應用程式，警告使用者更新其 iOS 版本的最低 iOS 作業系統設定，將在封鎖使用者使其無法存取的最低 iOS 作業系統設定之後套用。 因此，當情況是 IT 系統管理員將最低 iOS 作業系統設定為 11.0.0.0，最低 iOS 作業系統 (僅警告) 設定為 11.1.0.0 時，如果嘗試存取應用程式的裝置使用 iOS 10，則因為導致封鎖存取的最低 iOS 作業系統版本設定限制更多，而使得終端使用者將會被封鎖。

處理不同類型的設定時，Intune 應用程式 SDK 版本需求會優先，然後是應用程式版本需求，再然後是 iOS 作業系統版本需求。 接著會以相同順序檢查所有類型之設定的任何警告。 我們建議您只針對必要的封鎖情況，在 Intune 產品小組的指導下，設定 Intune App SDK 版本需求。

## <a name="app-protection-experience-for-android-devices"></a>Android 裝置的應用程式防護體驗

### <a name="company-portal-app-and-intune-app-protection"></a>公司入口網站應用程式和 Intune 應用程式防護
大部分的應用程式保護功能是內建在公司入口網站應用程式中。 雖然公司入口網站應用程式一律為必要，但也不需要註冊裝置。 針對沒有註冊的行動應用程式管理 (MAM-WE)，終端使用者只需要在裝置上安裝公司入口網站應用程式即可。

### <a name="multiple-intune-app-protection-access-settings-for-same-set-of-apps-and-users"></a>相同應用程式和使用者集合的多個 Intune 應用程式防護存取設定
Intune 應用程式防護存取原則，在使用者嘗試從其公司帳戶存取目標應用程式時，會以特定順序套用在終端使用者裝置上。 一般情況下，封鎖會優先，然後是可以關閉的警告。 例如，如果適用於特定的使用者/應用程式，警告使用者進行修補程式升級的最低 Android 修補程式版本設定，將在封鎖使用者使其無法存取的最低 Android 修補程式版本設定之後套用。 因此，當情況是 IT 系統管理員將最低 Android 修補程式版本設定為 2018-03-01，最低 Android 修補程式版本 (僅警告) 設定為 2018-02-01 時，如果嘗試存取應用程式的裝置使用修補程式版本 2018-01-01，則因為導致封鎖存取的最低 Android 修補程式版本設定限制更多，而使得終端使用者將會被封鎖。 

處理不同類型的設定時，應用程式版本需求會優先，然後是 Android 作業系統版本需求和 Android 修補程式版本需求。 接著會以相同順序檢查所有類型之設定的任何警告。

### <a name="intune-app-protection-policies-and-googles-safetynet-attestation-for-android-devices"></a>適用於 Android 裝置的 Intune 應用程式防護原則和 Google SafetyNet 證明 
Intune 應用程式防護原則提供一個功能，可讓系統管理員要求終端使用者裝置通過 Google 適用於 Android 裝置的 SafetyNet 證明。 新 Google Play 服務判斷將會依照 Intune 服務所決定的間隔報告給 IT 系統管理員。 進行服務呼叫的頻率已由於負載而節流處理，因此這個值會在內部維護，且無法設定。 任何 IT 系統管理員針對 Google SafetyNet 證明設定所設定的動作，將會根據條件式啟動上次回報給 Intune 服務的結果來執行。 如果沒有任何資料，將會根據沒有其他的條件式啟動檢查失敗來允許存取，而 Google Play 服務用來判斷證明結果的「往返」動作將在後端開始，並在裝置未通過時以非同步方式提示使用者。 如果有過時的資料，將會根據上次回報的結果封鎖或允許存取，同樣地，Google Play 服務用來判斷證明結果的「往返」動作將會開始，並在裝置未通過時以非同步方式提示使用者。

### <a name="intune-app-protection-policies-and-googles-verify-apps-api-for-android-devices"></a>適用於 Android 裝置的 Intune 應用程式防護原則和 Google Verify Apps API
Intune 應用程式防護原則提供一個功能，可讓系統管理員要求終端使用者裝置透過 Google 適用於 Android 裝置的 Verify Apps API 來傳送訊號。 有關如何執行這項操作的指示會因裝置而稍有差異。 一般步驟是前往 Google Play 商店，然後按一下 [我的應用程式與遊戲]  ，再按一下上次應用程式掃描結果，其會將您引導至「Play 安全防護」功能表。 確定 [掃描裝置中的安全性威脅]  的切換開關已切換為開啟。

### <a name="googles-safetynet-attestation-api"></a>Google 的 SafetyNet Attestation API 
Intune 會利用 Google Play Protect SafetyNet API，在我們現有 Root 破解偵測檢查中新增對已取消註冊裝置的檢查。 如果不想在 Root 破解的裝置上執行其應用程式，Google 已開發和維護這個 API 集合供 Android 應用程式採用。 例如，Android Pay 應用程式已採用此集合。 雖然 Google 不會公開共用所發生 Root 破解偵測檢查的全部內容，但我們預期這些 API 會偵測到其裝置遭到 Root 破解的使用者。 接著可防止這些使用者存取，或從其啟用原則的應用程式抹除其公司帳戶。 [檢查基本完整性]  會告訴您有關裝置的一般完整性。 Root 破解的裝置、模擬器、虛擬裝置，以及具有竄改跡象的裝置都無法通過基本完整性檢查。 [檢查基本完整性與經過認證的裝置]  會告訴您有關裝置與 Google 服務的相容性。 只有經過 Google 認證且未修改的裝置可以通過這項檢查。 下列裝置將無法通過：

- 無法通過基本完整性的裝置
- 開機載入器已解除鎖定的裝置
- 具有自訂系統映像/ROM 的裝置
- 製造商未為其申請或通過 Google 認證的裝置
- 直接從 Android Open Source Program 來源檔案建置系統映像的裝置
- 具有搶鮮版 (Beta)/開發人員預覽系統映像的裝置

如需技術詳細資料，請參閱 [Google 有關 SafetyNet 證明的文件](https://developer.android.com/training/safetynet/attestation)。

### <a name="safetynet-device-attestation-setting-and-the-jailbrokenrooted-devices-setting"></a>[SafetyNet 裝置證明] 設定和 [已進行越獄或 Root 的裝置] 設定
「Google Play 安全防護」的 SafetyNet API 檢查，需要終端使用者至少在判斷證明結果之「往返」動作執行的時間範圍內已連線。 如果終端使用者已離線，IT 系統管理員還是能夠預期從 [已進行越獄或 Root 的裝置]  設定強制執行的結果。 話雖如此，如果終端使用者離線太久，[離線寬限期]  值就會起作用，一旦達到該計時器值，對公司或學校資料的存取便會被封鎖，直到可以存取網路為止。 開啟這兩個設定可允許採用分層方式來保持終端使用者裝置的良好狀況，這在終端使用者存取行動裝置上的公司或學校資料時非常重要。

### <a name="google-play-protect-apis-and-google-play-services"></a>Google Play Protect API 與 Google Play Services
利用 Google Play Protect API 的應用程式保護原則設定需要 Google Play Services 才能正常運作。 [SafetyNet 裝置證明]  和 [對應用程式進行威脅掃描]  設定，都需要 Google 決定的 Google Play Services 版本才能正確運作。 由於這些都是屬於安全性領域的設定，如果終端使用者是這些設定的目標，但不符合適當的 Google Play Services 版本或無法存取 Google Play 服務，則會封鎖這些使用者。

## <a name="next-steps"></a>後續步驟

[如何使用 Microsoft Intune 建立及部署應用程式保護原則](app-protection-policies.md)

## <a name="see-also"></a>請參閱
協力廠商應用程式 (例如 Salesforce 行動應用程式) 可以特定方式與 Intune 搭配使用來保護公司資料。 若要深入了解 Salesforce 應用程式與 Intune 搭配使用的特定方式 (包括 MDM 應用程式組態設定)，請參閱 [Salesforce 應用程式和 Microsoft Intune](https://gallery.technet.microsoft.com/Salesforce-App-and-Intune-c47d44ee/file/188000/1/Salesforce%20App%20and%20Intune%20for%20external.pdf) \(英文\)。
