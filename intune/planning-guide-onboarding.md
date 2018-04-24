---
title: Intune 上架流程
titlesuffix: Microsoft Intune
description: 本文可協助您在讓 Microsoft Intune 僅限雲端解決方案於環境中上線時，處理需要考量的所有細節。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac7bd764-5365-4920-8fd0-ea57d5ebe039
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 871e091af1f2046206dbc94fdc7d199435645190
ms.sourcegitcommit: e04e1652e121b4b9dbed05d0bbaa569e6d5d09bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="implement-your-microsoft-intune-plan"></a>實作 Microsoft Intune 計劃

在上架階段中，您要將 Intune 部署到生產環境。 實作程序包含根據[使用案例需求](planning-guide-requirements.md)安裝及設定 Intune 與外部相依性 (如有必要)。

下一節提供包括需求和高階工作的 Intune 實作程序概觀。

## <a name="intune-requirements"></a>Intune 需求

主要的 Intune 獨立需求如下︰

-   Enterprise Mobility + Security (EMS)/Intune 訂閱

-   Office 365 訂閱 (適用於 Office 應用程式和應用程式保護原則管理的應用程式)

-   Apple APN 憑證 (啟用 iOS 裝置平台管理)

-   Azure AD Connect (適用於目錄同步作業)

-   Intune On-Premises Connector for Exchange (適用於 Exchange 內部部署的條件式存取，如有需要)

-   Intune 憑證連接器 (適用於 SCEP 憑證部署，如有需要)

>[!TIP]
> 如需可以使用 Intune 管理的完整裝置清單，請查看[支援的裝置](supported-devices-browsers.md)清單。

## <a name="intune-implementation-process"></a>Intune 實作程序

我們已找出實作 Intune 部署的 13 項分開的工作。 根據業務需求、現有的基礎結構和裝置管理策略，其中部分工作可能已經完成。 其他可能不適合您的計劃。

### <a name="task-1-get-an-intune-subscription"></a>工作 1：取得 Intune 訂閱

如前面的＜Intune 需求＞一節所述，您需要 EMS 或 Intune 訂閱。 如果貴組織沒有訂閱，請連絡 Microsoft 或 Microsoft 帳戶小組洽詢 Enterprise Mobility + Security (EMS) 或 Intune 購買事宜。

-   深入了解[如何購買 Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune-pricing)。

### <a name="task-2-add-office-365-subscription"></a>工作 2︰新增 Office 365 訂閱

這個參數是選擇性的。 如果您打算使用 Exchange Online，以及使用應用程式保護原則管理 Office 行動應用程式，您需要訂閱 Office 365。 貴組織若未訂閱 Office 365，請連絡 Microsoft 或 Microsoft 帳戶小組洽詢 Office 365 購買事宜。

-   深入了解[如何購買 Office 365](https://products.office.com/business/compare-office-365-for-business-plans)。

### <a name="task-3-add-users-groups-in-azure-ad"></a>工作 3︰在 Azure AD 中新增使用者群組

您可能需要根據 Intune 部署使用案例和需求，在 Active Directory 或 Azure Active Directory 中新增使用者或安全性群組。 請檢閱 Active Directory 或 Azure Active Directory 目前的使用者和安全性群組，並判斷其是否完全符合您的需求。 在新增新的使用者和安全性群組時，建議您將它們新增至 Active Directory，使用 Azure AD Connect 與 Azure Active Directory 同步處理。


-   深入了解[新增使用者並授與 Intune 系統管理權限](users-permissions-add.md)。
<!---why not send them to the AAD connect topic? Question out to Andre: https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect--->



### <a name="task-4-assign-intune-and-office-365-user-licenses"></a>工作 4︰指派 Intune 和 Office 365 的使用者授權

EMS/Intune 和 Office 365 新產品的所有目標使用者，都需要獲指派授權。 您可在 Office 365 系統管理中心入口網站中指派 EMS/Intune 和 Office 365 授權。

-   深入了解[管理 Intune 授權](licenses-assign.md)。

### <a name="task-5-set-mobile-device-management-authority-to-intune"></a>工作 5：將行動裝置管理授權單位設定為 Intune

您必須先將裝置管理授權單位設定為 Intune，才能使用 Intune 開始安裝、設定、管理與和註冊裝置。

-   深入了解[如何設定裝置管理授權單位](mdm-authority-set.md)。

### <a name="task-6-enable-device-platforms"></a>工作 6︰啟用裝置平台

依預設，除了 Apple 裝置 (iOS 和 Mac) 之外，大部分的裝置平台都會啟用。 您必須先啟用裝置平台，才可以在 Intune 中註冊及管理 iOS 裝置。 若要這樣做，您需要建立 MDM Push Certificate，並將其新增至 Intune。

-   深入了解[如何啟用 Apple 裝置註冊](apple-mdm-push-certificate-get.md)。

### <a name="task-7-add-and-deploy-terms-and-conditions-policies"></a>工作 7︰新增及部署條款及條件原則

Intune 支援條款和條件原則。 適當新增條款及條件原則，根據您的 Intune 部署使用案例和需求將它們部署至目標群組。

-   深入了解 [Microsoft Intune 的條款和條件原則設定](terms-and-conditions-create.md)。

### <a name="task-8-add-and-deploy-configuration-policies"></a>工作 8︰新增及部署設定原則

Intune 支援兩種類型的設定原則：一般和自訂。 適當新增設定原則，根據您的 Intune 部署使用案例和需求將其部署至目標群組。

-   深入了解[透過 Microsoft Intune 原則管理裝置上的設定和功能](device-profiles.md)。

### <a name="task-9-add-and-deploy-resource-profiles"></a>工作 9︰新增及部署資源設定檔

Intune 支援電子郵件、Wi-Fi 和 VPN 設定檔。 適當新增這些設定檔，根據您的 Intune 部署使用案例和需求將它們部署至目標群組。

-   深入了解[如何使用 Intune 存取公司資源](device-profiles.md)。

### <a name="task-10-add-and-deploy-apps"></a>工作 10：新增及部署應用程式

Intune 支援部署 Web、企業營運和公用市集應用程式。 您也可以建立應用程式與應用程式保護原則的關聯性，來管理已與 Intune SDK 整合的應用程式。 適當新增應用程式，根據您的 Intune 部署使用案例和需求將它們部署至目標群組。

-   深入了解[新增與部署應用程式](app-management.md)。

### <a name="task-11-add-and-deploy-compliance-policies"></a>工作 11：新增及部署相容性原則

Intune 支援合規性原則。 適當新增合規性原則，根據您的 Intune 部署使用案例和需求將它們部署至目標群組。

-   深入了解 [Microsoft Intune 的裝置相容性原則](device-compliance.md)。

### <a name="task-12-enable-conditional-access-policies"></a>工作 12：啟用條件式存取原則

Intune 支援 Exchange Online、Exchange 內部部署、SharePoint Online、商務用 Skype Online 及 Dynamics CRM Online 的條件式存取。 根據您的 Intune 部署使用案例和需求適當啟用及設定條件式存取。

-   深入了解[使用 Microsoft Intune 限制電子郵件、Office 365 和其他服務的存取](conditional-access.md)。

### <a name="task-13-enroll-devices"></a>工作 13：註冊裝置

Intune 支援 iOS、Mac 作業系統、Android、Windows Desktop 和 Windows 行動裝置平台。 根據您的 Intune 部署使用案例和需求，適當啟用行動裝置平台。

-   深入了解[註冊裝置以在 Intune 中管理](device-enrollment.md)。


## <a name="next-steps"></a>接下來的步驟

如需 Intune 實作程序的詳細資訊，請參閱 [Microsoft Virtual Academy Intune 工作階段模組](https://mva.microsoft.com/en-US/training-courses/deploying-microsoft-enterprise-mobility-suite-16408)。


請參閱[測試與驗證 Intune 部署](planning-guide-test-validation.md)的指引。
