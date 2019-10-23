---
title: 什麼是 Microsoft Intune - Azure | Microsoft Docs
description: 了解 Microsoft Intune 作為 Enterprise Mobility + Secutiry 解決方案的行動裝置管理 (MDM) 和行動裝置應用程式管理 (MAM) 元件如何運作，以及它如何協助您保護公司資料。
keywords: 什麼是 Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3c03c67a99b78804c999250f8d1148a4b3d1d97
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504759"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune 是適用於您裝置的 MDM 和 MAM 提供者

Microsoft Intune 是以雲端為基礎的服務，著重於行動裝置管理 (MDM) 和行動應用程式管理 (MAM)。 Intune 包含在 Microsoft 的 [Enterprise Mobility + Security (EMS) 套件](https://www.microsoft.com/microsoft-365/enterprise-mobility-security)中，可讓使用者提高生產力，同時保護您的組織資料。 它會與其他服務整合，包括 Microsoft 365 和 Azure Active Directory (Azure AD) 以控制具有存取權的人員以及他們有權存取的內容，還有用於資料保護的 Azure 資訊保護。 將它與 Microsoft 365 搭配使用時，您可以讓您的工作人員在所有裝置上都具有生產力，同時持續保護您的組織資訊。

![Intune 架構的影像](./media/what-is-intune/intunearch_sm.png)

檢視[較大版本](./media/what-is-intune/intunearchitecture.svg)的 Intune 架構圖。

使用 Intune，您可以︰

- 選擇使用 Intune 實現 100% 雲端，或者使用 Configuration Manager 和 Intune [共同管理](https://docs.microsoft.com/sccm/comanage/overview)。
- 在個人和組織擁有的裝置上設定規則和組態設定，以存取資料和網路。
- 部署及驗證裝置上的應用程式 -- 內部部署和行動裝置。
- 藉由控制使用者存取和共用資訊的方式來保護您的公司資訊。
- 請確定裝置和應用程式都符合您的安全性需求。

## <a name="manage-devices"></a>管理裝置

在 Intune 中，您可以使用最適合您的方法來管理裝置。 針對組織擁有的裝置，您可能會想要完全控制裝置，包括設定、功能和安全性。 在此方法中，這些裝置的裝置和使用者會在 Intune 中「註冊」。 註冊完成後，他們會透過 Intune 中設定的原則來接收您的規則和設定。 例如，您可以設定密碼和 PIN 需求、建立 VPN 連線、設定威脅防護等。

對於個人裝置或攜帶您自己的裝置 (BYOD)，使用者可能不想讓組織系統管理員擁有完全控制權。 在這種方法中，請提供使用者選項。 例如，如果使用者想要完整存取您的組織資源，請[註冊](../enrollment/device-enrollment.md)其裝置。 或者，如果這些使用者只想要存取電子郵件或 Microsoft Teams，則請使用需要多重要素驗證 (MFA) 的應用程式保護原則來使用這些應用程式。

當裝置在 Intune 中註冊和管理時，系統管理員可以：

- 查看已註冊的裝置，並取得存取組織資源之裝置的詳細目錄。
- 設定裝置，使其符合您的安全性和健康情況標準。 例如，您可能會想要封鎖已越獄的裝置。
- 將憑證推送至裝置，讓使用者可以輕鬆地存取您的 Wi-Fi 網路，或使用 VPN 來連線到您的網路。
- 查看符合規範以及不符合規範的使用者和裝置報告。
- 如果裝置遺失、遭竊或不再使用，請移除組織資料。

**線上資源** ：

- [什麼是裝置註冊？](../enrollment/device-enrollment.md)

- [使用裝置設定檔將功能和設定套用至您的裝置](../configuration/device-profiles.md)

- [使用 Microsoft Intune 保護裝置](../protect/device-protect.md)

## <a name="manage-apps"></a>管理應用程式

Intune 中的行動應用程式管理 (MAM) 是設計來保護應用程式等級的組織資料，包括自訂應用程式和市集應用程式。 應用程式管理可以在組織擁有的裝置和個人裝置上使用。

當應用程式在 Intune 中受控時，系統管理員可以：

- 新增行動應用程式並將其指派給使用者群組和裝置，包括特定群組中的使用者、特定群組中的裝置等等。
- 將應用程式設定為在啟用特定設定的情況下啟動或執行，並更新裝置上已有的現有應用程式。
- 查看已使用的應用程式相關報告，並追蹤其使用方式。
- 透過僅移除應用程式中的組織資料，進行選擇性抹除。

Intune 提供行動應用程式安全性的一種方式，是透過 **[應用程式保護原則](../apps/app-protection-policy.md)** 。 應用程式保護原則：

- 使用 Azure AD 身分識別，將組織資料與個人資料隔離。 因此，個人資訊會被隔離不被組織 IT 所知。 使用組織認證存取的資料會獲得額外的安全性保護。
- 限制使用者可採取的動作 (例如複製並貼上、儲存和檢視)，協助保護個人裝置上的存取。
- 可以在已於 Intune 中註冊的裝置上、在另一個 MDM 服務中註冊的裝置上、或未在任何 MDM 服務中註冊的裝置上建立及部署。 在已註冊的裝置上，應用程式保護原則可以新增額外的保護層。

例如，使用者以其組織認證登入裝置。 其組織身分識別允許存取其個人身分識別所拒絕的資料。 使用該組織資料時，應用程式保護原則會控制資料的儲存和共用方式。 當使用者使用其個人身分識別登入時，不會套用相同的保護。 如此一來，IT 能夠控制組織資料，而終端使用者則維持對個人資料的控制權和隱私權。

而且，您可以將 Intune 與 EMS 中的其他服務搭配使用。 這項功能為您的組織所提供的行動應用程式安全性，超出了作業系統和任何應用程式所包含的範圍。 使用 EMS 管理的應用程式可以存取更廣泛的行動應用程式和資料保護功能。

![顯示應用程式管理資料安全性層級的影像](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>合規性與條件式存取

Intune 整合了 Azure AD，以啟用一組廣泛的存取控制案例。 例如，要求行動裝置必須符合 Intune 中定義的組織標準，才能存取網路資源 (例如電子郵件或 SharePoint)。 同樣地，您可以鎖定服務，使其僅適用於一組特定的行動應用程式。 例如，您可以鎖定 Exchange Online，使其僅供 Outlook 或 Outlook Mobile 存取。

**線上資源** ：

- [設定裝置上的規則以允許存取組織資源](../protect/device-compliance-get-started.md)

- [搭配 Intune 使用條件式存取的常見方式](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>如何取得 Intune

Intune 可以下列方式提供使用：

- 作為獨立的 [Azure 服務](https://go.microsoft.com/fwlink/?linkid=2090973)
- 隨附於 [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) 和 [Microsoft 365 政府版](https://www.microsoft.com/microsoft-365/government)
- 作為 [Office 365 中的行動裝置管理](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22)，其中包含一些有限的 Intune 功能

Intune 用於許多領域，包括[政府機關](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description)、[教育](https://www.microsoft.com/en-us/education/intune)、用於製造和零售業的[資訊站或專用裝置](../configuration/kiosk-settings.md)等等。

## <a name="next-steps"></a>後續步驟

- 閱讀ㄧ些 [Intune 協助解決的常見商務問題](https://docs.microsoft.com/intune/common-scenarios)。
- 開始使用 [Intune 30 天試用版](free-trial-sign-up.md)。
- 規劃您的 [Intune 移轉](migration-guide.md)。
- 使用免費試用版或訂用帳戶，逐步執行 [Quickstart:Create an email device profile for iOS](../configuration/quickstart-email-profile.md) (快速入門：建立 iOS 的電子郵件裝置設定檔)
