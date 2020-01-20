---
title: Microsoft Intune 基本設定
description: 本文提供設定 Microsoft Intune 的必要步驟。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 60cfa440-0723-4ea0-bacf-3c5d26f9a1d3
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c705e8863ef4e01906a773d528f9ae2f40461c71
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885846"
---
# <a name="basic-setup"></a>基本設定

評估環境之後，即可開始設定 Microsoft Intune。

## <a name="external-dependencies-for-an-intune-deployment"></a>Intune 部署的外部相依性

### <a name="identity"></a>身分識別

Intune 需要 Azure Active Directory (AAD) 作為身分識別和使用者分組提供者。 深入了解：

- [身分識別需求](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview)

- [目錄同步作業需求](https://docs.microsoft.com/azure/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements)

- [Multi-Factor Authentication (MFA)](https://docs.microsoft.com/azure/active-directory/authentication/concept-mfa-howitworks)

- [規劃您的使用者和裝置群組](users-add.md)

- [如何建立使用者和裝置群組](groups-get-started.md)

如果貴組織已使用 Office 365，Intune 必須使用相同的 Azure Active Directory 環境。

### <a name="pki-optional"></a>PKI (選用)

如果您打算在 Intune 針對 VPN、Wi-Fi 或電子郵件設定檔使用憑證式驗證，您必須確定您有支援的 [PKI 基礎結構](../protect/certificates-configure.md)，隨時可建立及部署憑證設定檔。 深入了解如何在 Intune 中設定憑證：

- [如何設定 SCEP 的憑證基礎結構](/intune/certificates-scep-configure)

- [設定 PFX 憑證基礎結構](/intune/certficates-pfx-configure)。


## <a name="task-list-for-an-intune-setup"></a>Intune 設定的工作清單

### <a name="task-1-intune-subscription"></a>工作 1：Intune 訂閱

移轉至 Intune 之前，您必須先訂閱 Intune。

- 您可以瀏覽[此頁面](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0)，其中包含下列作業的指示︰

  - 建立連結至新的 AAD 租用戶的全新 Intune 訂閱。

  - 登入現有的 AAD 租用戶以連結 Intune 訂閱。

### <a name="task-2-assign-intune-user-licenses"></a>工作 2：指派 Intune 使用者授權

- 了解[如何指派 Intune 使用者授權](licenses-assign.md)。

- 如果您已建立新的 Azure Active Directory 租用戶，請學習[如何從內部部署的 Active Directory (AD) 建立新的使用者或同步處理使用者](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)。

### <a name="task-3-set-your-mdm-authority-to-intune"></a>工作 3：將 MDM 授權單位設定為 Intune

我們建議您使用 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)來管理 Intune。

將 MDM 授權單位設定為 [Intune]  。 使用其他 MDM 授權單位可讓 Intune 將 MDM 管理移交至其他 Microsoft 管理主控台。 這種情況並不常見。

> [!IMPORTANT]
> 如果您是第一次將行動裝置管理移交至 Intune，應該將 MDM 授權單位設定為 Intune。

了解[如何設定行動裝置管理授權單位](mdm-authority-set.md)。

## <a name="next-step"></a>後續步驟

設定[裝置與應用程式管理原則](../migration-guide-configure-policies.md)。
