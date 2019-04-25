---
title: 使用 EMS 的 BYOD 技術決策
description: 使用 Microsoft Enterprise Mobility + Security 啟用 BYOD 和保護公司資料的主要技術決策。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b42360cd3e7be3e4662d8cef1868643475a1304
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61508403"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>使用 Microsoft Enterprise Mobility + Security (EMS) 啟用 BYOD 的技術決策

當您開發策略，讓員工在自己的裝置 (BYOD) 上從遠端工作時，您需要在這些狀況中進行重大決定，啟用 BYOD 以及如何保護公司資料。 幸運的是，EMS 以完整解決方案集提供您需要的所有功能。  

在本主題中，我們會檢查啟用 BYOD 存取公司電子郵件的簡單使用案例。 我們會將焦點放在您需要管理整部裝置或只管理應用程式，兩者都是完全有效的選項。

## <a name="assumptions"></a>假設
* 您有 Azure Active Directory 和 Microsoft Intune 的基本知識
* 電子郵件帳戶裝載在 Exchange Online 中

## <a name="common-reasons-to-manage-the-device-mdm"></a>管理裝置的常見原因 (MDM)
您可以在 Exchange Online 上部署[條件式存取](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)原則，輕鬆地讓使用者向裝置管理註冊其裝置。 以下是您想要管理個人裝置的可能原因：

**WiFi/VPN** – 如果您的使用者需要公司連線設定檔才能發揮生產力，這可以順暢地設定。

**應用程式** – 如果您的使用者需要一組推送至其裝置的應用程式，這些可以順暢地傳遞。 這包括因安全性目的可能需要的應用程式，例如 Mobile Threat Defense 應用程式。

**合規性** – 某些組織必須遵守法規或其他原則，以呼叫特定的 MDM 控制項。 例如，您需要 MDM 加密整部裝置，或產生裝置上所有應用程式的報表。

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>只管理應用程式的常見原因 (MAM)
沒有 MDM 的 MAM 在支援 BYOD 的組織中很普遍。 您可以在 Exchange Online 上部署條件式存取原則，讓使用者從 Outlook Mobile (它支援 MAM 保護) 存取電子郵件。 以下是您只想管理個人裝置之應用程式的可能原因：

**使用者體驗** – MDM 註冊包含許多警告提示 (由平台強制執行)，通常會造成使用者決定完全不在個人裝置上存取電子郵件。 MAM 對使用者的警告力度較弱，因為它們只會快顯一次，讓使用者知道 MAM 保護已就位。

**合規性** – 某些組織需要遵守對個人裝置較少管理功能的原則。 例如，MAM 只能夠從應用程式移除公司資料，而 MDM 卻能從裝置移除所有資料。

![比較行動裝置的裝置和應用程式管理映像](./media/byod-app-device-mgmt.png)

深入了解[裝置管理和應用程式管理生命週期](introduction-device-app-lifecycles.md)。

## <a name="mdm-vs-mam-capability-comparison"></a>MDM 與 MAM 的功能比較
如前所述，條件存取可以讓使用者註冊其裝置，或使用受控應用程式，例如 Outlook Mobile。 任一情況皆可套用許多其他條件，包括：

* 哪位使用者正在嘗試存取
* 位置受信任或不受信任
*   登入風險等級
* 裝置平台

但許多組織通常仍有在意的特定風險。  下表列出常見考量，以及 MDM 與 MAM 對該考量的回應。

| 考量   |   MDM  |   MAM  |
|------------|--------|--------|
|未經授權的資料存取 | 需要群組成員資格 | 需要群組成員資格 |
|未經授權的資料存取 | 需要裝置註冊 | 需要受保護的應用程式 |
|未經授權的資料存取 | 需要特定的位置 | 需要特定的位置 |
| | | |
|遭盜用的使用者帳戶| 需要 MFA | 需要 MFA|
|遭盜用的使用者帳戶 | 封鎖高風險使用者 | 封鎖高風險使用者 |
|遭盜用的使用者帳戶 | 裝置 PIN | 應用程式 PIN |
| | | |
| 遭盜用的裝置或應用程式 | 需要相容的裝置 | 應用程式啟動破解檢查 |
| 遭盜用的裝置或應用程式 | 加密裝置資料 | 加密應用程式資料 |
| | | |
|遺失或遭竊的裝置 | 移除所有的裝置資料 | 移除所有的應用程式資料|
| | | |
| 意外的資料共用或儲存至不安全的位置 | 限制裝置資料備份 | 限制剪下/複製/貼上|
| 意外的資料共用或儲存至不安全的位置 | 限制另存為 | 限制另存為 |
|意外的資料共用或儲存至不安全的位置 | 停用列印 | n/a|

## <a name="next-steps"></a>後續步驟
現在要將焦點放在裝置管理、應用程式管理或兩者的組合，決定您組織中是否啟用 BYOD。 實作選擇的決定權在您，以確保無論如何都能使用 Azure AD 提供的身分識別和安全性功能。  

使用 Intune [規劃指南](planning-guide.md)規劃下一個層級。
