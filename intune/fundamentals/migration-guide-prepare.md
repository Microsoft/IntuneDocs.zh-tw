---
title: 準備 Intune 以用於行動裝置管理
titleSuffix: Microsoft Intune
description: 請先評估您的商務和技術需求，再移轉至 Microsoft Intune。
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29ae889e99a843a8569782bad2b1303c7bb4304c
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727476"
---
# <a name="phase-1-prepare-microsoft-intune-for-mobile-device-management-mdm"></a>階段 1：準備 Microsoft Intune 以用於行動裝置管理 (MDM)

在探究設定 Intune 的詳細資訊之前，讓我們先檢閱您組織的行動裝置管理需求。 它可能有助於在目前的 MDM 提供者中執行作用中使用者的報告，以識別重要的使用者群組。 然後，您就可以開始處理[評估 MDM 需求](migration-guide-prepare.md#assess-mdm-requirements)一節中的問題。

## <a name="assess-mdm-requirements"></a>評估 MDM 需求

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>您需要管理的裝置種類？

- 需要支援的[平台](supported-devices-browsers.md)？

- 您需要支援的裝置是屬公司擁有的裝置或個人裝置？

- 使用何種連線？ Wi-Fi、行動電話、VPN？

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>使用者在受管理的裝置上需執行什麼工作？

- 您需要佈建使用者的應用程式嗎？

- 您使用自訂的企業營運應用程式嗎？ 或是您只需要公用儲存區應用程式？

- 您需要佈建電子郵件帳戶嗎？

### <a name="what-kinds-of-users"></a>使用者的種類？

- 多少個使用者會使用單一裝置？

- 您需要的使用條款？

  - 請務必提前和您的法務部門對此協商。
  - 需要的當地語系化？

- 使用者是否熟悉一般技術和 IT？

### <a name="what-is-your-device-security-policy"></a>您的行動裝置安全性原則是什麼？

- 您需要裝置層級加密嗎？

- 您目前的裝置密碼/PIN 碼長度是多少？

- 您需要停用裝置功能，或限制特定裝置行為嗎？ 您可以使用裝置組態設定檔控制各種平台特定的設定，例如：
  - 停用數位相機
  - 鎖定在單一應用程式模式<br/>

- 您必須支援何種驗證？ 如果您需要憑證式驗證，必須佈建何種憑證？
  - Intune 可使用資源存取設定檔為已註冊的裝置佈建憑證。
  - 您需要支援何種公開金鑰基礎結構 (PKI)？
  <br></br>
- 您需要在裝置或應用程式層級支援虛擬私人網路 (VPN) 嗎？

  - Intune 可以佈建協力廠商 VPN 提供者的 VPN 設定。
  <br/><br/>
- 可容許因應特定需求的暫時性例外狀況，以避免停機時間嗎？ 或是具有存取權的裝置永遠必須符合所有安全性需求？

## <a name="next-steps"></a>後續步驟
閱讀這些來自不同產業面的[個案研究 (英文)](https://customers.microsoft.com/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune)，觀察組織如何評估其行動裝置管理的需求。

檢閱[基本 Intune 設定](migration-guide-setup.md)。
