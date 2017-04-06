---
title: "準備 Intune 以用於行動裝置管理 | Microsoft Docs"
description: "本文旨在協助讀者於移轉到 Intune 前評估其業務和技術需求。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58591442-6606-4f39-a06b-f17a1f25af25
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 8da2695c4c6dc8b45559323b83a4bb77167303b7
ms.openlocfilehash: 2e7bcedebdf777db64a9ec90aa758822634ed435
ms.lasthandoff: 03/28/2017


---

# <a name="phase-1-prepare-intune-for-mobile-device-management-mdm"></a>階段 1：準備 Intune 以用於行動裝置管理 (MDM)

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

在探究設定 Intune 的詳細資訊之前，讓我們先檢閱您組織的行動裝置管理需求。 這可能有助於在您目前的 MDM 提供者中執行作用中使用者的報告以識別重要的使用者群組，接著您就可以開始處理[評估 MDM 需求](https://docs.microsoft.com/intune/plan-design/migration-phase1-prepare-intune-for-mobile-device-management#assess-mdm-requirements)一節中的問題。

## <a name="assess-mdm-requirements"></a>評估 MDM 需求

### <a name="what-kinds-of-devices-do-you-need-to-manage"></a>您需要管理的裝置種類？

-   需要支援的[平台](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers)？

-   您需要支援的是公司或 BYOD 裝置？

-   使用何種連線？ Wi-Fi、行動電話、VPN？

### <a name="what-do-your-users-need-to-do-on-managed-devices"></a>使用者在受管理的裝置上需執行什麼工作？

-   您需要佈建使用者的應用程式嗎？

-   您使用自訂的企業營運應用程式嗎？ 或是您只需要公用儲存區應用程式？

-   您需要佈建電子郵件帳戶嗎？

### <a name="what-kinds-of-users"></a>使用者的種類？

-   多少個使用者會使用單一裝置？

-   您需要的使用規定？

    -   請務必提前和您的法務部門對此協商。

    -   需要的當地語系化？

-   使用者是否熟悉一般技術和 IT？

### <a name="what-is-your-device-security-policy"></a>您的行動裝置安全性原則是什麼？ 

-   您需要裝置層級加密嗎？

-   裝置密碼/PIN 碼長度？

-   您需要停用裝置功能，或限制特定裝置行為嗎？

    -   您可以使用裝置組態設定檔控制各種平台特定的設定，例如︰停用數位相機、鎖定在單一應用程式模式。
<br></br>
-   您必須支援何種驗證？

    -   如果您需要憑證式驗證，必須佈建何種憑證？

        -   Intune 可使用資源存取設定檔為已註冊的裝置佈建憑證。
<br></br>
    -   您需要支援何種公開金鑰基礎結構 (PKI)？
<br></br>
-   您需要在裝置或應用程式層級支援虛擬私人網路 (VPN) 嗎？

    -   Intune 可以佈建協力廠商 VPN 提供者的 VPN 設定。
<br></br>
-   可容許因應特定需求的暫時性例外狀況，以避免停機時間嗎？ 或是具有存取權的裝置永遠必須符合所有安全性需求？

## <a name="additional-information"></a>其他資訊

-   如需詳細範例，請檢閱這些來自不同產業面的[個案研究 (英文)](https://customers.microsoft.com/en-US/story/mwh-global-now-part-of-stantec-secures-mobile-devices-with-intune)，觀察組織如何評估其行動裝置管理的需求。

## <a name="next-steps"></a>後續步驟

[階段 1：基本設定](https://docs.microsoft.com/intune/plan-design/migration-phase1-basic-setup)

