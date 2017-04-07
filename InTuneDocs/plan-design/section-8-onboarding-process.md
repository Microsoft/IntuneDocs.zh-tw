---
title: "Intune 上架程序 | Microsoft Docs"
description: "本文可協助您在環境中上架 Intune 僅限雲端解決方案時，處理需要考量的所有詳細資訊。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: fa33bd3833f7f7198eed3f4f486c27bae3ba47d7
ms.openlocfilehash: 87832ec7f295c08678052d19164af9a8db051f9f
ms.lasthandoff: 12/30/2016


---

# <a name="intune-implementation"></a>Intune 實作

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

在上架階段中，您要將 Intune 實作到生產環境。 實作程序包含安裝及設定 Intune 與外部相依性 (如有必要)，根據本指南前幾節已檢閱的[使用案例的需求](section-3-determine-use-case-requirements.md)。

下一節提供包括需求和高階工作的 Intune 實作程序概觀。

>[!TIP]
> 如需 Intune 實作程序的詳細資訊，請參閱[其他資源](additional-resources.md)。

## <a name="intune-requirements"></a>Intune 需求

下面提供主要的 Intune 獨立需求︰

-   EMS/Intune 訂閱

-   Office 365 訂閱 (適用於 Office 應用程式和 MAM 原則管理的應用程式)

-   Apple APN 憑證 (啟用 iOS 裝置平台管理)

-   Azure AD Connect (適用於目錄同步作業)

-   Intune On-Premises Connector for Exchange (適用於 CA for Exchange 內部部署，如有需要)

-   Intune 憑證連接器 (適用於 SCEP 憑證部署，如有需要)

>[!TIP]
> 您可在[這裡](https://docs.microsoft.com/intune/get-started/what-to-know-before-you-start-microsoft-intune)找到 Intune 獨立需求的詳細資訊。

## <a name="intune-implementation-process"></a>Intune 實作程序

### <a name="overview-of-implementation-tasks"></a>實作工作概觀

以下是實作 Intune 時，每項工作的概觀。

#### <a name="task-1-add-intune-subscription"></a>工作 1：新增 Intune 訂閱

如前一節＜需求＞所指出，需要訂閱 EMS 或 Intune。 貴組織若未訂閱 EMS 或 Intune，請連絡 Microsoft 或 Microsoft 帳戶小組洽詢 Enterprise Mobility + Security (EMS) 或 Intune 購買事宜。

-   深入了解[如何購買 Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-pricing)。

#### <a name="task-2-add-office-365-subscription"></a>工作 2︰新增 Office 365 訂閱

這個參數是選擇性的。 如前一節＜需求＞中所指出，如果您打算使用 MAM 原則來使用 Exchange Online 及管理 Office 行動裝置應用程式，您需要 Office 365 訂閱。 貴組織若未訂閱 Office 365，請連絡 Microsoft 或 Microsoft 帳戶小組洽詢 Office 365 購買事宜。

-   深入了解[如何購買 Office 365](https://products.office.com/business/compare-office-365-for-business-plans)。

#### <a name="task-3-add-users-groups-in-azure-ad"></a>工作 3︰在 Azure AD 中新增使用者群組

您可能需要根據 Intune 部署使用案例和需求，在 AD 或 AAD 中新增使用者或安全性群組。 您應該檢閱 Active Directory 或 Azure Active Directory 目前的使用者和安全性群組，並判斷其是否完全符合您的需求。 新的使用者和安全性群組最常在 Active Directory 中新增，透過 Azure AD Directory Connect 同步處理至 Azure Active Directory。

-   深入了解[新增使用者並授與 Intune 系統管理權限](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-3)。

#### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>工作 4︰指派 Intune 和 Office 365 的使用者授權

EMS/Intune 和 Office 365 新產品的所有目標使用者，都要獲指派授權。 您可在 Office 365 系統管理中心入口網站中完成 EMS/Intune 和 Office 365 的授權指派。

-   深入了解[管理 Intune 授權](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)。

#### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>工作 5：將行動裝置管理授權單位設定為 Intune

您必須先將裝置管理授權單位設定為 Intune，才能使用 Intune 開始安裝、設定、管理與和註冊裝置。 您會在 Intune 管理員入口網站的 [管理] 工作區中完成設定裝置管理授權單位工作。

-   深入了解[設定 MDM 授權單位](https://docs.microsoft.com/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority)。

#### <a name="task-6-enable-device-platforms"></a>工作 6︰啟用裝置平台

依預設，在 Intune 管理主控台中，除了 Apple 裝置 (iOS 和 Mac) 之外，大部分的裝置平台都會啟用。 您必須先啟用裝置平台，才可以在 Intune 中註冊及管理 iOS 裝置。 啟用 iOS 裝置平台有三個步驟︰建立及下載的APN 憑證，並將 APN 憑證上傳至 Intune。

-   深入了解[設定 iOS 和 Mac 裝置管理](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。

#### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>工作 7︰新增及部署條款及條件原則

Microsoft Intune 支援新增及部署條款及條件原則。 您可在 Intune 管理入口網站的 [原則] 工作區中完成新增與部署條款及條件原則。 適當新增條款及條件原則，根據您的 Intune 部署使用案例和需求部署至目標群組。

-   深入了解 [Microsoft Intune 的條款和條件原則設定](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune)。

#### <a name="task-8-add-and-deploy-configuration-policies"></a>工作 8︰新增及部署設定原則

Microsoft Intune 支援新增與部署兩種類型的設定原則：一般和自訂。 您可在 Intune 管理入口網站的 [原則] 工作區中完成新增與部署設定原則。 適當新增設定原則，根據您的 Intune 部署使用案例和需求部署至目標群組。

-   深入了解[透過 Microsoft Intune 原則管理裝置上的設定和功能](https://docs.microsoft.com/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)。

#### <a name="task-9-add-and-deploy-resource-profiles"></a>工作 9︰新增及部署資源設定檔

Microsoft Intune 支援電子郵件、Wi-Fi 和 VPN 設定檔。 您可在 Intune 管理入口網站的 [原則] 工作區中完成新增與部署設定檔。 適當新增電子郵件/Wi-Fi/VPN 設定檔，根據您的 Intune 部署使用案例和需求部署至目標群組。

-   深入了解[使用 Microsoft Intune 存取公司資源](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune)。

#### <a name="task-10-add-and-deploy-apps"></a>工作 10：新增及部署應用程式

Microsoft Intune 支援部署 Web、LOB 和公用市集應用程式。 此外，支援透過建立已整合 Intune SDK 的應用程式與 MAM 原則的關聯性，來管理它們。 您可在 Intune 管理入口網站的 [應用程式] 工作區中完成新增與部署應用程式。 您可在 Intune 管理入口網站的 [原則] 工作區中完成新增 MAM 原則。 適當新增應用程式，根據您的 Intune 部署使用案例和需求部署至目標群組。

-   深入了解 [Deploy apps with Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/deploy-apps) (使用 Microsoft Intune 部署應用程式)。

#### <a name="task-11-add-and-deploy-compliance-policies"></a>工作 11：新增及部署相容性原則

Microsoft Intune 支援相容性原則。 您可在 Intune 管理入口網站的 [原則] 工作區中完成新增與部署相容性原則。 適當新增相容性原則，根據您的 Intune 部署使用案例和需求部署至目標群組。

-   深入了解 [Microsoft Intune 的裝置相容性原則](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)。

#### <a name="task-12-enable-conditional-access-policies"></a>工作 12：啟用條件式存取原則

Microsoft Intune 支援 Exchange Online 和內部部署、SharePoint Online、商務用 Skype Online 及 Dynamics CRM Online 的條件式存取。 您可在 Intune 系統管理入口網站的 [原則] 工作區中啟用條件式存取原則。 根據您的 [Intune 部署使用案例和需求](section-3-determine-use-case-requirements.md)適當啟用及設定條件式存取。

-   深入了解[使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)。

#### <a name="task-13-enroll-devices"></a>工作 13：註冊裝置

Intune 支援 iOS、Mac OS、Android、Windows 桌面及 Windows 行動裝置平台。 根據您的 Intune 部署使用案例和需求，適當啟用行動裝置平台。

-   深入了解[註冊裝置以在 Intune 中管理](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)。

>[!TIP]
> 如需 Intune 實作程序的詳細資訊，請參閱 [Microsoft Virtual Academy Intune 工作階段模組](https://mva.microsoft.com/training-courses/deploying-microsoft-enterprise-mobility-suite-16408?l=PPWNoZxvD_1404778676)。

## <a name="next-section"></a>下一節

下一節提供有關[測試與驗證 Intune 部署](section-9-test-and-validation.md)的指引。

