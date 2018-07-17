---
title: Microsoft Intune 的常見使用方式
description: 了解大約有六個 Microsoft Intune 可協助您管理的常見工作。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/30/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 9e2ad930a9ff9a12e649c6ff46f0a9f6fcacca16
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38225284"
---
# <a name="common-ways-to-use-microsoft-intune"></a>Microsoft Intune 的常見使用方式

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

深入實作工作時，契合貴公司的企業行動力專案關係人與業務目標很重要。  不論您是企業行動力新手，還是從另一個產品移轉而來，這一點都很重要。  

對於企業行動力的需求一直在大幅進化，Microsoft 用來解決這些需求的方法有時與市場上的其他解決方案不同。 契合業務目標的最佳方式是以您想要為員工、協力廠商和 IT 部門塑造的環境，表達您的目標。  

以下簡介六個依賴 Intune 的常見案例，以及如何規劃及部署每個案例的詳細資訊連結。

>[!NOTE]
>您是否想要了解 Microsoft IT 如何使用 Intune，讓 Microsoft 在其行動裝置上存取公司資源，同時保護公司資料？ [閱讀此技術性案例研究](https://www.microsoft.com/itshowcase/Article/Content/588)，詳細查看 Microsoft IT 如何使用 Intune 與其他服務來管理身分識別、裝置、應用程式和資料。  

>[!IMPORTANT]
>我們想要確保行動裝置對於最近在 iOS 裝置上的 "Trident" 惡意程式碼攻擊，處於最新狀態。 因此我們發佈了一篇部落格文章，稱為 [Ensuring mobile devices are up to date using Microsoft Intune](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) (使用 Microsoft Intune 確定行動裝置為最新狀態)。 它提供 Intune 可協助保持您的裝置安全且最新的不同方式的相關資訊。

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>保護內部部署電子郵件和資料，以透過行動裝置安全存取
大部分企業行動力策略計劃一開始都是讓員工，在連接網際網路的行動裝置上安全地存取電子郵件。 許多組織仍然有內部部署資料和應用程式伺服器，例如裝載在其公司網路上的 Microsoft Exchange。


Intune 和 Microsoft Enterprise Mobility + Security (EMS) 提供唯一的 Exchange Server 整合[條件式存取解決方案](conditional-access.md) ([傳統入口網站](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune))，確保在裝置向 Intune 註冊前，沒有任何行動應用程式可以存取電子郵件。 您不必在公司網路邊緣部署另一部閘道電腦，就能完全做到。

Intune 支援也能存取需要安全存取內部部署資料的行動應用程式，像是商務營運應用程式伺服器。 這通常會使用 [Intune 管理的憑證](certificates-configure.md) ([傳統入口網站](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)) 來完成，適用於在周邊網路結合標準 VPN 閘道或 Proxy 的存取控制，例如 Microsoft Azure Active Directory 應用程式 Proxy。 

在這些情況下，存取公司資料的唯一方法就是註冊裝置進行管理。 註冊裝置之後，管理系統會先確保它們符合您的原則，然後才能存取公司資料。 此外，Intune 的 [App Wrapping Tool 與 App SDK](apps-prepare-mobile-application-management.md) 可協助包含企業營運應用程式中的存取資料，讓它無法將公司資料傳遞至取用者應用程式或服務。

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>保護 Office 365 電子郵件和資料，以透過行動裝置安全存取
您可以更容易，您的使用者也以更順暢地在 Office 365 中保護公司資料 (電子郵件、文件、立即訊息、連絡人)。


Intune 與 Enterprise Mobility Suite + Security 解決方案特別加入了條件式存取功能，確保只有符合您公司之相容性需求 (已執行[多重要素驗證](/intune-classic/deploy-use/multi-factor-authentication-azure-active-directory)、已在 Intune 註冊，並使用受管理的 App、受支援的 OS 版本、裝置 PIN 碼、低使用者風險設定檔等等) 的使用者、應用程式或裝置，才能存取 Office 365 資料。


各自應用程式市集裡的 Office 行動應用程式已經準備好開始使用資料內含項目原則，您可以透過 Intune 進行設定。 這可讓您避免與應用程式 (例如原生電子郵件應用程式) 及不受 IT 管理的儲存位置 (例如 Dropbox) 共用資料。 這項功能內建於 Office 365 和 EMS。 您不需要部署額外的基礎結構即可取得此值。

常見的 Office 365 部署作法是要求註冊裝置加以管理，但前題是它們需要使用公司應用程式、憑證、Wi-Fi 或 VPN 設定以完整設定，這是公司擁有的裝置常見情況。  


不過，如果使用者只需要存取公司電子郵件與文件 (通常是個人擁有的裝置情況)，則可要求使用者使用您已套用[應用程式保護原則](app-protection-policies.md) ([傳統入口網站](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune)) 的 Office 行動應用程式，並完全略過註冊裝置。  



無論如何，將由已定義的原則保護 Office 365 資料。

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>將攜帶您自己的裝置計劃提供給所有員工
攜帶您自己的裝置 (BYOD) 會繼續在組織間受歡迎，為員工減少硬體支出或提高行動產能選擇。 目前幾乎每個人都有手機，因此為什麼不在口袋內再放一支？ 主要的挑戰一直都是說服員工註冊其個人裝置加以管理，因為它們害怕 IT 部門會看到並使用他們的裝置做其他事。  

當裝置註冊不可行時，Intune 提供一個 BYOD 替代方法來簡單[管理包含公司資料的應用程式](app-protection-policies.md) ([傳統入口網站](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune))。 Intune 可保護公司資料，即使有問題的應用程式存取公司和個人資料也可以，此情況適用於 Office 行動應用程式。  

身為系統管理員，您可以要求使用者從 Office 行動應用程式存取 Office 365，並使用保護資料的原則來設定應用程式 (例如將它加密、使用 PIN 來保護它等等)。 這些應用程式保護原則會防止因未受管理的應用程式和儲存位置而遺失資料 - 應用程式內部或外部。 例如，這些原則會防止使用者將公司電子郵件設定檔的文字複製到取用者的電子郵件設定檔，即使兩個設定檔都是在 Outlook Mobile 中設定也是如此。 可針對您的 BYOD 使用者需要的其他服務及應用程式部署類似設定。

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>向您的員工發放屬於公司的電話
現今有許多員工用行動裝置工作，這讓行動裝置生產力成為競爭力的要件。 這些員工隨時隨地都需要順暢地存取所有公司應用程式和資料。 您需要確保公司資料安全且具有低管理成本。  

Intune 提供了[大量佈建和管理解決方案](device-enrollment.md) ([傳統入口網站](/intune-classic/deploy-use/manage-corporate-owned-devices))，可以與目前市場上的主要企業裝置管理平台整合，包括 Apple 裝置註冊計劃和 Samsung Knox 行動安全性平台。 使用 Intune 集中撰寫裝置設定，有助於高度自動化佈建某些公司裝置。  

試想一下︰將未拆封的 iPhone 手機交給員工。 員工開啟手機電源，然後瀏覽他們必須自行驗證之帶有公司品牌的安裝流程。 已順利使用[安全性原則](device-profiles.md) ([傳統入口網站](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)) 設定 iPhone。

接著，員工啟動 Intune 公司入口網站應用程式以存取提供給他們的選擇性公司應用程式。

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>將使用受限的共用平板電腦發放給您的員工
有越來越多員工使用行動技術。 例如，共用的平板電腦現在經常由零售商店員工使用。  不論是用來處理銷售或立即檢查庫存，平板電腦皆有助於大幅提升與客戶的互動。

在此情況下，簡單的使用者體驗很重要。 基於這個理由，通常會將有限用途模式下的平板電腦散發給員工，例如，單一特定業務應用程式是員工可進行互動的唯一工具。 Intune 可讓您大量佈建、保護和集中管理這些共用的 [iOS 與 Android](device-profiles.md) ([傳統入口網站](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)) 裝置，而這些裝置可設定為在此有限用途模式下執行。

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>讓您的員工從未受管理的公用 kiosk 中安全存取 Office 365
有時候您的員工需要使用您無法管理的裝置、應用程式或瀏覽器，例如商展和旅館的公用電腦。

您應該允許員工從中存取公司電子郵件？ 您可以利用 Intune 與 Microsoft Enterprise Mobility + Security，藉由[限制您組織所管理之裝置的電子郵件存取權](conditional-access.md) ([傳統入口網站](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune))，告訴大家「不行」。 這可確保經過嚴格驗證的員工不會不小心將公司資料放在不受信任的電腦上。
