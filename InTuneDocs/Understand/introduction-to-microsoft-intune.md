---
title: "什麼是 Microsoft Intune？ | Microsoft Docs"
description: "了解 Intune 為何是 Enterprise Mobility + Security 解決方案的行動裝置管理元件，以及它如何協助您保護公司資料。"
keywords: "什麼是 Intune"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6932a0d81654edc4c2e3108ca11df892e9ec5bf4
ms.openlocfilehash: 50a9b89140a0fff9994b267f10fa7912af89f116


---

# <a name="what-is-intune"></a>什麼是 Intune？
Intune 是以雲端為基礎的企業行動管理 (EMM) 服務，可協助讓您的工作人員提高生產力，同時保護公司資料。 使用 Intune，您可以︰
* 管理您的工作人員用來存取公司資料的行動裝置。
* 管理您的工作人員使用的行動應用程式。
* 藉由協助控制您的工作人員存取並共用公司資訊的方式，保護您的公司資訊。
* 確保裝置和應用程式都符合公司安全性需求。

Intune 和 Azure Active Directory (Azure AD) 緊密整合以進行身分識別和存取控制，並和 Azure Rights Management (Azure RMS) 緊密整合以進行資料保護。 它是 Microsoft Enterprise Mobility + Security (EMS) 的「管理手臂」，而 Office 365 則是 Microsoft 行動解決方案的「生產手臂」。  

Office 365 和 EMS 結合，能讓您的工作人員在所有裝置上都具有生產力，同時持續保護您的組織資訊。 Office 365 和 EMS 是企業行動 (包括生產力、身分識別、存取控制、管理和資料保護) 的完整整合式套件。 它可提供您在組織中部署和操作行動解決方案的有效方式。

## <a name="how-does-intune-work"></a>Intune 如何運作？
Intune 提供行動裝置管理 (MDM) 與行動應用程式管理 (MAM)。 Intune 的 MDM 和 MAM 功能參與了資料保護與法規遵循案例的 EMS 套件。  

您使用 Intune MDM/MAM 功能以及 EMS 資料保護的方式，取決於[您試圖解決的商務問題](#common-business-problems-that-intune-helps-solve)。 例如：
* 如果您要建立一次性裝置的集區，讓零售商店中的輪班工作者共用，則您會大量使用 MDM。
* 如果您允許工作人員使用其個人裝置存取公司資料 (BYOD)，則會借助 MAM 和資料保護。  
* 如果您要發出公司電話給資訊工作者，您將大量依賴所有技術。

## <a name="intune-mobile-device-management-mdm-explained"></a>Intune 行動裝置管理 (MDM) 的解釋
MDM 的運作方式是使用行動作業系統中可用的通訊協定或 API。 它包含這類的工作︰
* 註冊裝置管理，以便 IT 擁有存取公司服務的裝置清查
* 設定裝置，以確保它們符合公司安全性和健全狀況標準
* 提供憑證和 Wi-Fi/VPN 設定檔，以存取公司的服務
* 報告和測量裝置對於公司標準的合規性
* 從受管理的裝置移除公司資料  

有時候，人們認為**公司資料的存取控制**是一項 MDM 功能。 我們不這麼認為，因為它不是行動作業系統提供的項目。 而是由身分識別提供者所提供。 在本例中，身分識別提供者是 Azure Active Directory (Azure AD)，也就是 Microsoft 的身分識別與存取管理系統。  

Intune 整合了 Azure AD，以啟用一組廣泛的存取控制案例。 例如，您可以要求行動裝置必須符合公司標準的規範，如 Intune 中所定義，然後裝置才能存取公司服務，例如 Exchange。 同樣地，您可以將公司服務鎖定在一組特定的行動應用程式。 例如，您可以將 Exchange Online 鎖定成只供 Outlook 或 Outlook Mobile 存取。

## <a name="intune-mobile-app-management-mam-explained"></a>Intune 行動應用程式管理 (MAM) 的解釋
當我們談論 MAM 時，我們是在討論我們的解決方案能讓 IT 專業人員以行動應用程式達到的事，例如︰
* 發佈行動應用程式給員工
* 設定應用程式
* 控制公司資料在行動應用程式中的使用與共用
* 從行動應用程式移除公司資料   
* 更新行動應用程式
* 報告行動應用程式清查
* 追蹤行動應用程式使用方式

我們看到 MAM 一詞用來意指那些事的其中一者，或是意指特定的組合。 尤其是，人們很常將應用程式設定的概念 (亦即，使用像是[在 iOS 上的受管理應用程式設定](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)的技術) 與在行動應用程式內保護公司資料的概念混淆。 這是因為某些行動應用程式公開了允許設定其資料安全性功能的設定。

再結合保護資料的作業系統功能 (例如 MDM 功能，像是 Windows 10 上的 Windows 資訊保護)，這可為行動裝置上的資料帶來許多保護。

當您使用 Intune 與 EMS 中的其他服務時，可以提供給組織的行動應用程式安全性，會比行動作業系統和行動應用程式本身透過應用程式設定所提供的安全性更高。 使用 EMS 管理的應用程式可以存取更廣泛的行動應用程式和資料保護，包括︰

* [單一登入](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [多重要素驗證](https://docs.microsoft.com/en-us/multi-factor-authentication/multi-factor-authentication)
* [應用程式條件式存取 (如果行動應用程式包含公司資料，便允許存取)](https://docs.microsoft.com/en-us/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [隔離公司資料與相同應用程式內的個人資料](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [應用程式保護原則 (PIN、加密、另存新檔、剪貼簿等)](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [從行動應用程式抹除公司資料](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [權限管理支援](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-azure-rms)

![顯示應用程式管理資料安全性層級的影像](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Intune 行動應用程式安全性
提供應用程式安全性是 MAM 的一部分，而且在 Intune 中，當我們談到行動應用程式安全性，我們是指︰
* 保持個人資訊隔離不被公司 IT 所知
* 限制使用者可用公司資訊採取的動作，例如複製、剪下/貼上、儲存和檢視
* 從行動應用程式移除公司資料，也稱為「選擇性抹除」或「公司抹除」

Intune 提供行動應用程式安全性的一種方式，是透過其**應用程式保護原則**功能。 應用程式保護原則會使用 Azure AD 身分識別，來隔離公司資料與個人資料。 使用公司認證存取的資料將會得到額外的公司防護措施。

當使用者以公司認證登入裝置時，她的公司身分識別可讓她存取個人身分識別遭拒的資料。 使用該公司資料時，Intune 以及其他 EMS 技術，會控制如何儲存和共用它。 當使用者以個人身分識別登入裝置時，相同的保護不會套用到存取的資料。 如此一來，IT 能夠控制公司資料，而使用者則維護了對個人資料的控制權和隱私權。

## <a name="emm-with-and-without-device-enrollment"></a>需註冊裝置的 EMM 與不需註冊裝置的 EMM
大部分的企業行動管理解決方案可支援基本的行動裝置和行動應用程式技術。 這些通常會繫結至您組織的 MDM 解決方案中註冊的裝置。 Intune 支援這些案例，而且還支援許多「不需註冊」的案例。  

組織會隨著它們採用「不需註冊」案例的程度而不同。 有些組織會以它為標準。 有些允許伴隨裝置，例如個人平板電腦。 其他的組織則完全不支援。 即使在最後這個情況下，亦即組織要求所有員工裝置都在 MDM 註冊，這些組織通常會為承包商、廠商以及其他有特定豁免的裝置支援「不需註冊」的案例。

您甚至可以在已註冊的裝置上使用 Intune 的「不需註冊」技術。 例如，在 MDM 中註冊的裝置可能會有行動作業系統所提供的已開啟保護。 此外，IT 可能會對 EMS 管理行動應用程式，套用應用程式保護原則來控制另存新檔，或是提供多因素驗證。

無論貴組織在註冊和未註冊的行動裝置和應用程式上的定位如何，Intune 作為 EMS 的一部分，都有工具可以協助提升工作人員產能，同時保護公司資料。

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune 協助解決的常見商務問題
下列商務問題清單連結到關於我們所能提供之解決方案的更詳細資訊。 只有最後一個項目需要在解決方案中進行 MDM 註冊︰

* [保護內部部署電子郵件和資料，以透過行動裝置存取](common-ways-to-use-intune.md#Protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [保護 Office 365 電子郵件和資料，以透過行動裝置安全存取](common-ways-to-use-intune.md#Protecting-your-Office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [向工作人員核發公司擁有的電話](common-ways-to-use-intune.md#Issue-corporate-owned-phones-to-your-information-workers)
* [將「攜帶您自己的裝置」(BYOD) 或個人裝置計劃提供給所有員工](common-ways-to-use-intune.md#Offer-a-bring-your-own-device-program-to-all-employees)
* [讓您的員工從未受管理的公用 kiosk 中安全存取 Office 365](common-ways-to-use-intune.md#Enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [將限制使用的共用平板電腦發給您的工作人員](common-ways-to-use-intune.md#Issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>後續步驟
* 請閱讀一些[常見的 Intune 使用方式](common-ways-to-use-intune.md)。
* [使用 Intune 的 30 天試用](get-started-with-a-30-day-trial-of-microsoft-intune.md)來熟悉產品。
* 深入了解 Intune 的[技術需求和功能](/intune/get-started/what-to-know-before-you-start-microsoft-intune)。



<!--HONumber=Nov16_HO3-->


