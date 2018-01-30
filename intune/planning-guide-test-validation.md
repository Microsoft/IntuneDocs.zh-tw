---
title: "Intune 測試與驗證"
description: "以下是當您在環境中測試和驗證 Intune 僅限雲端解決方案時必須考慮的詳細資料。"
keywords: 
author: arob98
ms.author: angrobe
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.openlocfilehash: 8521ae12062ad73dfddb0f03aeac8c07ce65de58
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="intune-testing-and-validation"></a>Intune 測試與驗證

在實作階段期間和之後，都需要執行測試階段。 您需要測試帳戶、群組和裝置，以測試先前所識別的所有必要 IT (管理員) 和使用者 (使用案例) 案例。

建議您在測試階段納入 IT 支援和技術服務人員，以便建立支援文件，讓 IT 支援和技術服務人員熟悉支援產品。 如果元件或案例無法根據使用案例運作，請務必記錄必要的變更，並包含進行變更的原因。

## <a name="before-you-begin"></a>開始之前

建議您記錄下列各項：

-   **測試準則：**找出測量的測試基準。

-   **設計元件：**至少必須存在於一項測試準則中。

如果設計元件不存在於至少符合需求或案例的一項測試準則中，請考慮設計元件是否為必要。 此外，請確定擁有下列項目︰

-   **帳戶：**有 EMS 和 Office 365 授權可測試所有使用案例的測試帳戶。

-   **裝置：**可以抹除或重設為原廠預設值的測試裝置。

-   **整合元件：**如有需要，應該安裝並設定所有的整合元件 (憑證連接器、適用於託管 Exchange 的 Intune 服務至服務連接器以及 Intune 內部部署 Exchange 連接器)。

您可能需要設計變更，以備處理無法預見的問題。 此外，所有的設計變更都應該詳細記錄每項變更的原因。 下例示範可能的變更︰

<blockquote>您知道自己不符合網路裝置註冊服務 (NDES) 的需求，也了解可以使用根 CA 設定 VPN 和 Wi-Fi 設定檔，在不實作 NDES 的情況下滿足相同的需求。</blockquote>

在測試和驗證過程中，您可能會遇到需要技術指導或特定疑難排解的困難或問題。 建議您透過 Microsoft 支援管道尋求協助。

-   [如何取得 Microsoft Intune 的管理支援](get-support.md)

-   [Microsoft Intune 的連絡電話協助支援](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>功能驗證測試

功能驗證包含測試每個元件和設定，以判斷是否正確運作。 下表有驗證測試範例。

![第 9 節表 1](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>使用案例驗證測試

執行使用案例驗證測試，以確認案例都完整且運作正常。 使用案例有兩種類型：IT 管理員和使用者。

### <a name="it-admin"></a>IT 管理員

執行 IT 管理員驗證測試，以驗證對裝置或使用者功能執行的管理動作正確無誤。 下例是 IT 管理員的端對端驗證案例。

![第 9 節表 2](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>使用者

執行使用者驗證測試，以確認所有使用者通訊中的使用者體驗都能如預期正確呈現。 請務必確認使用者體驗正確無誤。 如果無法確認，它可能會導致採用率較低以及較大量的技術服務人員呼叫。

![第 9 節表 3](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>接下來的步驟

現在您已測試並驗證您的 Intune 功能和使用案例，因此可以[推出 Intune 產品](planning-guide-rollout-plan.md)。

如需更多規劃範本和資訊，請參閱[其他資源](planning-guide-resources.md)。
