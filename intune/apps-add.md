---
title: "如何將應用程式新增至 Microsoft Intune"
titlesuffix: Azure portal
description: "這些程序可協助您將應用程式加入 Intune，讓您可以指派給使用者與裝置。 \""
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 01/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a1ded457-0ecf-4f9c-a2d2-857d57f8d30a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f84adced59d2057cd4d18f05ff6953293f7c44cc
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-add-an-app-to-microsoft-intune"></a>如何將應用程式新增至 Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

您必須先將應用程式新增至 Intune，才可以指派、監視、設定或保護它們。 Intune 支援各種不同的應用程式類型。 每種應用程式類型的可用選項都不相同。

Intune 可讓您新增及指派下列應用程式類型：
| 應用程式類型                                  | 安裝                                                                  | Updates                       |
|------------------------------------------ |----------------------------------------------------------------------------   |---------------------------    |
| 網站上的應用程式                           | Intune 會在裝置主畫面上建立 Web 應用程式捷徑          | 應用程式會自動更新     |
| 內部撰寫的應用程式 (企業營運)  | Intune 將應用程式安裝在裝置上 (您提供安裝檔案)    | 您必須更新應用程式       |
| 市集的應用程式                       | Intune 將應用程式安裝在裝置上                                       | 應用程式會自動更新     |


除了 Web 應用程式，Intune 也為市集應用程式和 LOB 應用程式支援下列特定平台：
- 市集應用程式
    - Android 市集應用程式
    - iOS 市集應用程式
    - Windows Phone 8.1 市集應用程式
    - Windows 市集應用程式
    - Android for Work 應用程式
    - 適用於 Windows 的 Office 365 應用程式
    - 適用於 macOS 的 Office 365 應用程式
- 建置應用程式 - 企業營運 (LOB)
    - Android 企業營運 (LOB) 應用程式
    - iOS 企業營運 (LOB) 應用程式
    - Windows Phone 企業營運 (LOB) 應用程式 (.xap 檔案)
    - Windows 企業營運 (LOB) 應用程式 (僅限 .msi 檔案)

>[!TIP]
> 企業營運 (LOB) 應用程式是您從應用程式安裝檔案新增的應用程式。 例如，若要安裝 iOS LOB 應用程式，您要從 [新增應用程式] 刀鋒視窗選擇 [企業營運應用程式] 作為**應用程式類型**來新增應用程式。 然後，選取應用程式套件檔案 (副檔名為 .ipa)。 這些類型的應用程式通常都是內部撰寫的。

## <a name="assess-application-requirements"></a>評估應用程式需求 
身為 IT 管理員，您不僅必須判斷您的群組必須使用哪些應用程式，還必須為每個群組和子群組判斷所需要的功能。 您必須為每個應用程式決定需要的平台、需要應用程式的使用者群組、這些群組要套用的設定原則，以及要套用的保護原則。  

此外，您還必須決定重心要放在行動裝置管理 (MDM) 還是只放在行動應用程式管理 (MAM)。 使用 Intune 管理裝置 (行動裝置管理) 很有用，當：
- 使用者需要 WiFi 或 VPN 公司連線設定檔才能具有生產力。
- 使用者需要將一組應用程式推送到他們的裝置。
- 您的組織需要遵守呼叫特定行動裝置管理 (MDM) 控制項的法規或其他原則，例如安全性或加密。

使用 Intune 管理應用程式 (行動應用程式管理) 但不管理裝置很有用，當：
- 您想要讓使用者使用他們自己的裝置 (BYOD)。
- 您想要提供單次快顯視窗，讓使用者知道 MAM 保護已就位，而不是一直發送裝置層級的通知。
- 您想要遵守對個人裝置較少管理功能的原則。 例如，您想要針對應用程式管理公司資料，而不是管理整部裝置的公司資料。

如需詳細資訊，請[比較 MDM 和 MAM](byod-technology-decisions.md)。

### <a name="determine-who-will-use-the-app"></a>決定誰會使用應用程式
一旦將應用程式新增至 Intune 之後，您就要指派可以使用應用程式的使用者群組。 首先，您必須根據應用程式包含的資料敏感度，決定應該存取應用程式的適當群組。 您可能要包含或排除組織內特定的角色類型。 例如，銷售群組可能只需要特定的 LOB 應用程式，而關注工程、財務、人力資源或法律的使用者可能不需要使用 LOB 應用程式。 此外，您的銷售群組可能需要額外的資料保護，以及從行動裝置存取內部的公司服務。 您必須決定這個群組如何使用應用程式連線到資源。 應用程式存取的資料是存在雲端中或內部部署？ 以及，使用者如何使用應用程式連線到資源。 Intune 支援也能存取需要安全存取內部部署資料的行動應用程式，像是商務營運應用程式伺服器。 這種存取通常是使用 [Intune 受控憑證](certificates-configure.md)完成，適用於在周邊網路結合標準 VPN 閘道或 Proxy 的存取控制，例如 Microsoft Azure Active Directory 應用程式 Proxy。 Intune 的 [App Wrapping Tool 與 App SDK](apps-prepare-mobile-application-management.md) 可協助包含企業營運應用程式中的存取資料，讓它無法將公司資料傳遞至取用者應用程式或服務。

使用 [Intune 部署規劃、設計和實作指南](planning-guide.md)來協助判斷如何識別與每個使用案例和子使用案例應用程式狀況建立關聯的組織群組。 如需指派群組應用程式的詳細資料，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。 

### <a name="determine-the-type-of-app-for-your-solution"></a>決定解決方案的應用程式類型
您可以選擇下列應用程式類型：
- **網站上的應用程式** - Web 應用程式是用戶端伺服器應用程式。 伺服器提供 Web 應用程式，包括 UI、內容和功能。 此外，現代的 Web 裝載平台通常會提供安全性、負載平衡和其他優勢。 這種類型的應用程式在網站上會分開維護。 您使用 Intune 指向此應用程式類型。 您也可以指派哪些使用者群組可以存取這個應用程式。 請注意，Android 不支援 Web 應用程式。
- **內部撰寫的應用程式 (企業營運)** - 內部建立的應用程式是企業營運 (LOB) 應用程式。 已為其中一個 Intune 支援的平台，例如 Windows、iOS 或 Android 建立此類型應用程式的功能。 您的組織會建立更新，並以個別檔案提供給您。 您使用 Intune 新增及部署更新，向使用者提供應用程式更新。 
- **市集的應用程式** - 市集應用程式是已上傳至 Microsoft Store、iOS Store 或 Android Store 的應用程式。 市集應用程式的提供者會維護應用程式並提供更新。 您從市集清單中選取應用程式，使用 Intune 將它新增為使用者可用的應用程式。

在決定您的組織需要的應用程式時，請考慮這些應用程式如何與雲端服務整合、應用程式存取哪些資料、BYOD 使用者是否能夠使用這些應用程式，以及應用程式是否需要存取網際網路。

如需判斷貴組織所需應用程式類型的詳細資訊，請參閱[建立設計](planning-guide-design.md#feature-requirements)**功能需求**一節的**應用程式**。

### <a name="understanding-app-management-and-protection-policies"></a>了解應用程式管理和保護原則
Intune 讓您修改部署的應用程式功能，幫助這些應用程式符合公司的規範及安全性原則。 這項控制能讓您決定保護公司資料的方式。 Intune 受控應用程式使用一組豐富的行動應用程式保護原則，例如：

- 限制複製和貼上及另存新檔功能
- 設定在 Intune Managed Browser 應用程式內開啟網頁連結
- 啟用使用多重身分識別和應用程式層級的條件式存取

Intune 受控應用程式也可以不需要註冊就啟用應用程式保護，讓您選擇套用資料外洩防護原則，但不用管理使用者的裝置。 此外，您可以使用 Intune 應用程式軟體開發套件和應用程式包裝工具，將行動裝置應用程式管理併入您的行動裝置和企業營運應用程式。 如需這些工具的詳細資訊，請參閱 [Intune App SDK 概觀](app-sdk.md)。

### <a name="understanding-licensed-apps"></a>了解授權應用程式
除了 Web 應用程式、市集應用程式和 LOB 應用程式，您應該也要知道大量採購方案應用程式和授權應用程式的目的地，例如：     
- **Apple 商務大量採購方案 (iOS 和 MacOS)** - iOS App Store 可讓您購買多個想要在公司中執行的應用程式授權。 購買多個複本有助於您在公司中有效率地管理應用程式。 如需詳細資訊，請參閱[管理 iOS 大量採購的應用程式](vpp-apps-ios.md)。
- **Android for Work (Android)** - 將應用程式指派至 Android for Work 裝置的方式，與您將應用程式指派至標準 Android 裝置的方式不同。 您針對 Android for Work 安裝的所有應用程式都是來自 Google Play for Work 商店。 您可以登入商店、瀏覽所需的應用程式並核准這些應用程式。 應用程式接著會出現在 Azure 入口網站的 [授權的應用程式] 節點中。 您可以在這裡管理應用程式的指派，方式與指派任何其他應用程式相同。
- **商務用 Microsoft Store (Windows 10)** - 商務用 Microsoft Store 可讓您為組織個別或大量尋找及購買應用程式。 將市集連接到 Microsoft Intune，就可以從 Azure 入口網站管理大量採購的應用程式。 如需詳細資訊，請參閱[從商務用 Microsoft Store 管理應用程式](windows-store-for-business.md)。 

## <a name="before-you-start"></a>開始之前
在您開始新增和指派應用程式之前，請考慮下列事項。

- 當您新增及指派來自市集的應用程式時，使用者必須擁有該市集的帳戶，才能安裝應用程式。
- 您指派的某些應用程式或項目可能相依於內建的 iOS 應用程式。 例如，如果您指派來自 iOS Store 的書籍，則裝置上必須有 iBooks 應用程式。 如果您已經移除了 iBooks 內建應用程式，您將無法使用 Intune 來恢復該應用程式。

## <a name="cloud-storage-space"></a>雲端儲存空間
使用軟體安裝程式安裝類型所建立的所有應用程式 (例如企業營運應用程式)，都必須封裝並上傳至 Intune 雲端儲存空間。 Intune 的試用版訂閱內容包含 2 GB 的雲端式儲存空間，可用來儲存受管理的應用程式和更新。 完整訂閱將包含 20 GB 的儲存空間。

您可以使用原始購買方法來購買 Intune 的額外儲存空間。  如果您是用發票或信用卡支付，請前往[訂用帳戶管理入口網站](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions)。  否則，請連絡合作夥伴或銷售人員。

雲端儲存空間需求如下：

-   所有應用程式安裝檔案必須位於相同的資料夾。
-   您上傳的任何檔案其檔案大小上限都是 2 GB。

## <a name="how-to-create-and-edit-categories-for-apps"></a>如何建立及編輯應用程式的類別

應用程式類別可協助您排序應用程式，以利使用者在公司入口網站中執行搜尋。 您可以指派一或多個類別給應用程式，例如**開發人員應用程式**或**通訊應用程式**。
當您將應用程式新增到 Intune 時，可以自由選取所需的類別。 使用平台相關的主題來新增應用程式及指派類別。 若要建立及編輯您自己的類別，請使用下列程序︰

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在**行動應用程式**工作負載中，選擇 [安裝] >  [應用程式類別]。
5. 在 [應用程式類別] 刀鋒視窗中會列出目前的類別。 請選擇下列其中一個動作：
    - **建立類別**︰選取 [新增] 顯示 [建立類別] 刀鋒視窗，然後新增新類別的名稱。 名稱只能以一種語言輸入，而且 Intune 不會翻譯它。 完成時按一下 [建立]。
    - **編輯類別** - 為清單中的類別選擇 [...]。 此選項會顯示快顯功能表，讓您 [釘選至儀表板] 或 [刪除] 類別。

## <a name="apps-added-automatically-by-intune"></a>Intune 自動新增的應用程式

原本，Intune 包含許多您可以快速指派的內建應用程式。 本清單已應客戶意見反應移除，您不會再看到內建應用程式。
不過，您已指派的任何內建應用程式仍會顯示在應用程式清單中。 若有需要，您可以繼續指派這些應用程式。
在之後的版本中，我們計劃新增一個方法，讓從 Azure 入口網站選取及指派內建應用程式的流程變得更輕鬆。

## <a name="next-steps"></a>接下來的步驟

選擇下列其中一個主題，以了解如何針對各平台將應用程式新增到 Intune：

- [Android 市集應用程式](store-apps-android.md)
- [Android LOB 應用程式](lob-apps-android.md)
- [iOS 市集應用程式](store-apps-ios.md)
- [iOS LOB 應用程式](lob-apps-ios.md)
- [Web 應用程式 (適用於所有平台)](web-app.md)
- [Windows Phone 8.1 市集應用程式](store-apps-windows-phone-8-1.md)
- [Windows Phone LOB 應用程式](lob-apps-windows-phone.md)
- [Windows 市集應用程式](store-apps-windows.md)
- [Windows LOB 應用程式](lob-apps-windows.md)
- [適用於 Windows 10 的 Office 365 應用程式](apps-add-office365.md)

