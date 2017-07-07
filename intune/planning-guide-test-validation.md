---
title: "Intune 測試與驗證"
description: "本文可協助您在測試及驗證您環境中 Intune 僅限雲端解決方案時，處理需要考量的所有詳細資訊。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4ea2974c4724564cd8f9972fdb238b06d1b100e6
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="intune-testing-and-validation"></a>Intune 測試與驗證

[!INCLUDE[note for both-portals](./includes/note-for-both-portals.md)]

實作階段期間與之後應該進行測試階段，您需要有測試帳戶、群組和裝置對所有前面找出的必要 IT (管理) 和終端使用者案例 (使用案例) 進行測試。

建議您在測試階段納入 IT 支援/技術服務人員，以便建立支援文件，讓 IT 支援/技術服務人員熟悉支援產品。 如果元件或案例無法根據使用案例運作，請務必記錄必要的變更，並包含變更的原因。

## <a name="before-you-begin"></a>開始之前

建議您記錄以下項目︰

-   **測試條件︰**找出測量的測試基準。

-   **設計元件︰**至少必須存在於 1 項測試條件中。

如果設計元件不存在於至少符合需求或案例的 1 項測試條件中，請考慮設計元件是否為必要。 此外，請確定擁有下列項目︰

-   **帳戶︰**測試中使用的帳戶應為有 EMS 和 Office 365 授權可測試所有使用案例的測試帳戶。

-   **裝置︰**此時使用的裝置應該是可能會被抹除或重設為原廠預設值的測試裝置。

-   **整合元件︰**如有需要，應該安裝並設定所有的整合元件 (憑證連接器、針對託管 Exchange 的服務連接器 Intune 服務以及 Intune 內部部署 Exchange 連接器)。

有可能需要設計變更，以備處理無法預見的問題。 此外，所有的設計變更都應該詳細記錄每項變更的原因。 下例示範可能的變更︰

-   您可能知道自己不符合網路裝置註冊服務 (NDES) 的需求，也了解可以使用根 CA 設定 VPN 和 Wi-Fi 設定檔，在不實作 NDES 的情況下滿足相同的需求。

在測試和驗證過程中，您可能會遇到需要技術指導或特定疑難排解的困難或問題。 建議您透過 Microsoft 支援管道尋求協助。

-   [如何取得 Microsoft Intune 的管理支援](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Microsoft Intune 的一般疑難排解提示](/intune-classic/troubleshoot/general-troubleshooting-tips-for-microsoft-intune)。

-   [如何取得 Microsoft Intune 的管理支援](/intune-classic/troubleshoot/how-to-get-support-for-microsoft-intune)

-   [Microsoft Intune 的連絡電話協助支援](/intune-classic/troubleshoot/contact-assisted-phone-support-for-microsoft-intune)

## <a name="functional-validation-testing"></a>功能驗證測試

功能驗證包含測試每個元件和設定，以判斷是否正確運作。 下表有驗證測試範例。

![第 9 節表 1](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>使用案例驗證測試

應該執行使用案例驗證測試，以確認案例都完整且運作正常。 使用案例有兩種類型，IT 管理員和終端使用者。

### <a name="it-admin"></a>IT 管理員

應該執行 IT 管理員驗證測試，驗證對裝置或使用者功能執行的管理動作是否正常運作。 下例是 IT 管理員的端對端驗證案例。

![第 9 節表 2](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>使用者

應該執行終端使用者驗證測試，確認所有使用者通訊中的終端使用者體驗都能如預期正確呈現。 驗證終端使用者體驗是否正確非常重要，因為未驗證可能會導致較低的採用率和大量的技術支援電話。

![第 9 節表 3](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>後續步驟

現在您已測試並驗證您的 Intune 功能和使用者使用案例，因此已可推出 Intune 產品。 如需詳細資訊，請參閱[其他資源](planning-guide-resources.md)。
