---
title: 什麼是 Microsoft Intune
description: 了解 Microsoft Intune 作為 Enterprise Mobility + Secutiry 解決方案的行動裝置管理 (MDM) 和行動裝置應用程式管理 (MAM) 元件如何運作，以及它如何協助您保護公司資料。
keywords: 什麼是 Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/20/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0ba46314a7c44e8db89d11a2866c86375a4cdfd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726176"
---
# <a name="what-is-microsoft-intune"></a>什麼是 Microsoft Intune？

Microsoft Intune 是企業行動力管理 (EMM) 空間中的雲端式服務，可協助讓您的工作人員提高生產力，同時保護公司資料。 Microsoft Intune 現在就如同其他 Azure 服務，已可在 Azure 入口網站中使用。 使用 Intune，您可以︰

- 管理您的工作人員用來存取公司資料的行動裝置。
- 管理您的工作人員使用的行動應用程式。
- 藉由協助控制您的工作人員存取並共用公司資訊的方式，保護您的公司資訊。
- 確保裝置和應用程式都符合公司安全性需求。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune 協助解決的常見商務問題

- [保護內部部署電子郵件和資料，以透過行動裝置存取](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
- [保護 Office 365 電子郵件和資料，以透過行動裝置安全存取](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
- [向工作人員核發公司擁有的電話](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
- [將「攜帶您自己的裝置」(BYOD) 或個人裝置計劃提供給所有員工](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
- [讓您的員工從未受管理的公用 kiosk 中安全存取 Office 365](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
- [將有使用限制的共用平板電腦核發給工作人員](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="how-does-intune-work"></a>Intune 如何運作？

Intune 是 Microsoft Enterprise Mobility + Security (EMS) 套件中的元件，可管理行動裝置和應用程式。 它會與 Azure Active Directory (Azure AD) 這類其他 EMS 元件緊密整合以進行身分識別和存取控制，以及與 Azure 資訊保護緊密整合以進行資料保護。 將它與 Office 365 搭配使用時，您可以讓您的工作人員在所有裝置上都具有生產力，同時持續保護您的組織資訊。

![Intune 架構的影像](./media/what-is-intune/intunearch_sm.png)

檢視[較大版本](./media/intunearchitecture.svg)的 Intune 架構圖。

您使用 Intune 的裝置和應用程式管理功能以及 EMS 資料保護的方式，取決於[您試圖解決的商務問題](#common-business-problems-that-intune-helps-solve)。 例如：
* 如果您要建立一次性裝置的集區，讓零售商店中的輪班工作者共用，則您會大量使用裝置管理。
* 如果您允許工作人員使用其個人裝置存取公司資料 (BYOD)，則會借助應用程式管理和資料保護。  
* 如果您要發出公司電話給資訊工作者，則將依賴所有技術。

## <a name="intune-device-management-explained"></a>說明的 Intune 裝置管理
Intune 裝置管理的運作方式是使用行動作業系統中可用的通訊協定或 API。 它包含這類的工作︰
* 註冊裝置管理，以便 IT 部門擁有存取公司服務的裝置清查
* 設定裝置，以確保它們符合公司安全性和健全狀況標準
* 提供憑證和 Wi-Fi/VPN 設定檔，以存取公司的服務
* 報告和測量裝置對於公司標準的合規性
* 從受管理的裝置移除公司資料  

有時候，人們認為**公司資料的存取控制**是一項裝置管理功能。 我們不這麼認為，因為它不是行動作業系統提供的項目。 而是由身分識別提供者所提供。 在本例中，身分識別提供者是 Azure Active Directory (Azure AD)，也就是 Microsoft 的身分識別與存取管理系統。  

Intune 整合了 Azure AD，以啟用一組廣泛的存取控制案例。 例如，您可以先要求行動裝置符合 Intune 中所定義公司標準的規範，裝置才能存取公司服務，例如 Exchange。 同樣地，您可以將公司服務鎖定在一組特定的行動應用程式。 例如，您可以將 Exchange Online 鎖定成只供 Outlook 或 Outlook Mobile 存取。

## <a name="intune-app-management-explained"></a>說明的 Intune 應用程式管理
當我們談到應用程式管理時，指的是：
* 將行動應用程式指派給員工
* 使用應用程式執行時所使用的標準設定來設定應用程式
* 控制公司資料在行動應用程式中的使用與共用
* 從行動應用程式移除公司資料   
* 更新應用程式
* 報告行動應用程式清查
* 追蹤行動應用程式使用方式

我們看到行動應用程式管理 (MAM) 一詞用來意指那些事的其中一者，或是意指特定的組合。 尤其是，人們很常將應用程式設定的概念與在行動裝置應用程式內保護公司資料的概念結合在一起。 這是因為某些行動應用程式公開了允許設定其資料安全性功能的設定。

當我們談到應用程式設定和 Intune 時，具體指的是 [iOS 上的 Managed 應用程式設定](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)這類技術。

當您使用 Intune 與 EMS 中的其他服務時，可以提供給組織的行動應用程式安全性，會比行動作業系統和行動應用程式本身透過應用程式設定所提供的安全性更高。 使用 EMS 管理的應用程式可以存取更廣泛的行動裝置應用程式和資料保護功能，包括：

* [單一登入](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
* [多重要素驗證](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [應用程式條件式存取 - 如果行動應用程式包含公司資料，便允許存取](../protect/app-based-conditional-access-intune.md)
* [隔離公司資料與相同應用程式內的個人資料](../apps/app-protection-policy.md)
* [應用程式保護原則 (PIN、加密、另存新檔、剪貼簿等)](../apps/app-protection-policies.md)
* [從行動應用程式抹除公司資料](../apps/apps-selective-wipe.md)
* [權限管理支援](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![顯示應用程式管理資料安全性層級的影像](./media/what-is-intune/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Intune 應用程式安全性
提供應用程式安全性是應用程式管理的一部分，而且在 Intune 中，當我們談到行動應用程式安全性，我們是指︰
* 保持個人資訊隔離不被公司 IT 所知
* 限制使用者可用公司資訊採取的動作，例如複製、剪下/貼上、儲存和檢視
* 從行動應用程式移除公司資料，也稱為「選擇性抹除」或「公司抹除」

Intune 提供行動裝置應用程式安全性的一種方式，是透過其**應用程式保護原則**功能。 應用程式保護原則會使用 Azure AD 身分識別，來隔離公司資料與個人資料。 使用公司認證存取的資料將會得到額外的公司防護措施。

例如，當使用者以公司認證登入裝置時，使用者的公司身分識別可讓其存取拒絕其個人身分識別存取的資料。 使用該公司資料時，應用程式保護原則會控制其儲存和共用方式。 當使用者以個人身分識別登入裝置時，相同的保護不會套用到存取的資料。 如此一來，IT 能夠控制公司資料，而終端使用者則維護了對個人資料的控制權和隱私權。

## <a name="emm-with-and-without-device-enrollment"></a>需註冊裝置的 EMM 與不需註冊裝置的 EMM
大部分的企業行動管理解決方案可支援基本的行動裝置和行動應用程式技術。 這些通常會繫結至您組織的行動裝置管理 (MDM) 解決方案中註冊的裝置。 Intune 支援這些案例，而且還支援許多「不需註冊」的案例。  

組織會隨著它們採用「不需註冊」案例的程度而不同。 有些組織會以它為標準。 有些允許伴隨裝置，例如個人平板電腦。 其他的組織則完全不支援。 即使在最後這個情況下，亦即組織要求所有員工裝置都在 MDM 註冊，他們通常會為承包商、廠商以及其他有特定豁免的裝置支援「不需註冊」的案例。

您甚至可以在已註冊的裝置上使用 Intune 的「不需註冊」技術。 例如，在 MDM 中註冊的裝置可能會有行動作業系統所提供的 "open-in" 保護。 "Open-in" 保護是 Apple iOS 的功能，會限制您不能在某個應用程式 (例如 Word) 中開啟另一個應用程式 (例如 Outlook) 的文件，除非兩個應用程式均受同一個 MDM 提供者管理。 此外，IT 可能會對 EMS 管理行動裝置應用程式套用應用程式保護原則，來控制另存新檔或提供多重要素驗證。

無論貴組織在註冊和未註冊的行動裝置和應用程式上的定位如何，Intune 作為 EMS 的一部分，都有工具可以協助提升工作人員產能，同時保護公司資料。

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure 入口網站中的 Microsoft Intune

您可以在 [Azure 入口網站](https://portal.azure.com)中找到 Microsoft Intune 服務。

Azure 入口網站中的 Microsoft Intune 體驗重點包括：

- 所有 Enterprise Mobility + Security (EMS) (EMS) 元件全部整合在同一主控台內
- 主控台採用符合網路標準的 HTML
- Microsoft Graph API 可用於自動化許多動作
- Azure Active Directory (AD) 群組可為所有 Azure 應用程式提供相容性
- 支援時下絕大多數的現代化網頁瀏覽器

如需自訂入口網站體驗的快速指南，請參閱[開始在 Azure 入口網站中使用 Intune](tutorial-walkthrough-intune-portal.md)。

> [!NOTE]
> 如果您使用過舊版的 Microsoft Intune，以下資訊會對您有幫助：
> * [我的功能在 Azure 的什麼位置？](../ui-changes.md)此參考會向您顯示因為移至 Azure 而變更的特定工作流程與 UI。
> * [Azure 入口網站中的 Intune 傳統群組](groups-get-started.md)說明移至 Azure Active Directory 安全性群組對群組管理的含意。

### <a name="before-you-start"></a>開始之前

若要使用 Azure 入口網站的 Intune ，必須具備 Intune 系統管理員與租用戶帳戶。 如果您還沒有帳戶，請[註冊帳戶](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)。

### <a name="supported-web-browsers-for-the-azure-portal"></a>Azure 入口網站支援的網頁瀏覽器

Azure 入口網站可以在時下絕大多數的電腦、 Mac 與平板電腦上執行 。 不支援行動電話。
目前支援的瀏覽器包括：

- Microsoft Edge (最新版本)
- Microsoft Internet Explorer 11
- Safari (最新版本，僅限 Mac)
- Chrome (最新版本)
- Firefox (最新版本)

如需所支援瀏覽器的最新資訊，請參閱 [Azure 入口網站](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)。

## <a name="next-steps"></a>後續步驟
* 請閱讀一些[常見的 Intune 使用方式](common-scenarios.md)。
* [使用 Intune 的 30 天試用](free-trial-sign-up.md)來熟悉產品。
* 深入了解 Intune 的[技術需求和功能](supported-devices-browsers.md)。
