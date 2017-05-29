---
title: "Intune 基本設定 | Microsoft Docs"
description: "本文旨在提供設定 Microsoft Intune 的必要步驟。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: fc5e14656b4f6dd883881a8dcb33df1dce6b29d7
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="phase-1-basic-setup"></a>階段 1：基本設定

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

完成環境評估之後，即可開始設定 Intune。

## <a name="external-dependencies-for-an-intune-deployment"></a>Intune 部署的外部相依性

### <a name="identity"></a>權杖服務 (STS)

Intune 需要 Azure Active Directory (AAD) 作為身分識別和使用者分組提供者。

-   深入了解[設計考量概觀](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)。

-   深入了解[判斷目錄同步處理需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)。

-   深入了解[判斷混合式身分識別解決方案的多重要素驗證需求](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements)。

-   深入了解 [Plan your user and device groups](/intune-classic/deploy-use/plan-your-user-and-device-groups) (規劃您的使用者和裝置群組)。

-   了解[在 Microsoft Intune 中使用群組管理使用者和裝置](/intune-classic/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune)。

如果貴組織已使用 Office 365，Intune 使用相同的 Azure Active Directory 環境極為重要。

### <a name="pki-optional"></a>PKI (選用)

如果您打算在 Intune 針對 VPN、Wi-Fi 或電子郵件設定檔使用憑證式驗證，您必須確定您有支援的 [PKI 基礎結構](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles)，隨時可建立及部署憑證設定檔。

以下是在 Intune 中設定憑證的詳細資訊。

-   [設定 SCEP 的憑證基礎結構](/intune-classic/deploy-use/configure-certificate-infrastructure-for-scep)。

-   [設定 PFX 憑證基礎結構](/intune-classic/deploy-use/configure-certificate-infrastructure-for-pfx)。

-   [設定 Intune 憑證設定檔](/intune-classic/deploy-use/configure-intune-certificate-profiles)。

-   [使用 Microsoft Intune 存取公司資源](/intune-classic/deploy-use/enable-access-to-company-resources-with-microsoft-intune)。

## <a name="task-list-for-an-intune-setup"></a>Intune 設定的工作清單

### <a name="task-1-intune-subscription"></a>工作 1：Intune 訂閱

移轉至 Intune 之前，您必須先訂閱 Intune。

-   您可以瀏覽[此頁面](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)，其中包含下列作業的指示︰

    -   建立連結至新的 AAD 租用戶的全新 Intune 訂閱。

    -   登入現有的 AAD 租用戶以連結 Intune 訂閱。

### <a name="task-2-assign-intune-user-licenses"></a>工作 2：指派 Intune 使用者授權

-   了解[如何指派 Intune 使用者授權](/intune-classic/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)。

-   如果您已建立新的 Azure Active Directory 租用戶，請學習[如何從內部部署的 Active Directory (AD) 建立新的使用者或同步處理使用者](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。

### <a name="task-3-set-your-mdm-authority-to-intune"></a>工作 3：將 MDM 授權單位設定為 Intune

您可以透過 Azure 入口網站或 Configuration Manager 最新分支主控台來管理 Intune。 除非您需要整合 Intune 與 Configuration Manager 最新分支部署，否則，建議您從 [Azure 入口網站](https://portal.azure.com)管理 Intune。

將 MDM 授權單位設定為 **Intune** 以啟用 Intune Azure 入口網站。 使用其他 MDM 授權單位可讓 Intune 將 MDM 管理移交至其他 Microsoft 管理主控台。 這種情況並不常見。

> [!IMPORTANT]
> 如果您是第一次將行動裝置管理移交至 Intune，應該將 MDM 授權單位設定為 Intune。

-   了解[如何設定行動裝置管理授權單位](/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority)。

## <a name="next-step"></a>後續步驟

[階段 1：設定裝置與應用程式管理原則](/intune-classic/plan-design/migration-phase1-configure-device-and-app-management-policies)

