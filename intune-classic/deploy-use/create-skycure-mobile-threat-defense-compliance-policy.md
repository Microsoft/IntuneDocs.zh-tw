---
title: "建立 Skycure Mobile Threat Defense 合規性原則"
description: "在 Intune 傳統入口網站中，建立 Skycure Mobile Threat Defense 合規性原則。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 56ff1728-1119-4e8a-aae6-ed5c7fafa052
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8f7b6c5c1e8497ca698b83215525ba9b4056f59
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="create-skycure-mobile-threat-defense-compliance-policy"></a>建立 Skycure Mobile Threat Defense 合規性原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

具有 Skycure Mobile Threat Defense 的 Intune 可讓您偵測行動裝置上的威脅，以及評估那些裝置上的風險。 您可以建立評估風險的合規性原則規則，來判斷裝置是否符合規範。 接著，您即可使用條件式存取原則，根據裝置相容性來封鎖對服務的存取。

## <a name="before-you-begin"></a>開始之前

具有 Skycure 裝置威脅防護之合規性原則的必要條件：

-   [設定 Skycure 與 Intune 整合](/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)

-   [在 Intune 中啟用 Skycure 連線](/intune-classic/deploy-use/enable-skycure-mobile-threat-defense-in-intune)

在 Skycure Mobile Threat Defense 的設定過程中，您已在 Skycure 主控台中建立一項原則來將各種威脅分類為高、中和低。 您現在需要在 Intune 合規性原則中設定允許的最高威脅層級。

## <a name="to-create-skycure-compliance-policy"></a>建立 Skycure 合規性原則

1.  移至 [Intune 傳統入口網站](https://manage.microsoft.com/)，然後輸入您的認證。

2.  選擇 [原則] &gt; [合規性原則]。 您可以使用現有的相容性原則，也可以建立新的相容性原則。

3.  選擇 [新增] &gt; [裝置健全狀況]，然後啟用 [裝置威脅防護]。

4.  選取 [允許的最高威脅層級]：

    a.  **無 (受保護)**：這是最安全的選項。 裝置不能在具有任何威脅的同時還能存取公司資源。 發現任何威脅時，即會將裝置評估為不相容。

    b。  **低**︰如果只有低層級的威脅，則裝置相容。 任何更高等級的威脅都會使裝置處於不相容狀態。

    c.  **中**︰如果發現裝置有低層級或中層級的威脅，則裝置相容。 如果偵測到高等級的威脅，則會將裝置判斷為不相容。

    d.  **高**：這是最不安全的選項。 這可允許所有威脅層級，並僅針對報告用途使用 Skycure Mobile Threat Defense。

> [!IMPORTANT]
> 如果您建立 Office 365 或其他服務的條件式存取原則，則會評估這個相容性評估，並封鎖不相容裝置，使其無法存取這些服務，直到威脅獲得解決為止。

## <a name="span-idmonitor-device-threats-classanchorspan-idnext-steps-classanchorspan-idtoc477360344-classanchorspanspanspannext-steps"></a><span id="monitor-device-threats" class="anchor"><span id="next-steps" class="anchor"><span id="_Toc477360344" class="anchor"></span></span></span>後續步驟

-   建立條件式存取原則：

    -   [Exchange Online](/intune-classic/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
    -   [Exchange 內部部署](/intune-classic/deploy-use/restrict-access-to-exchange-onpremises-with-microsoft-intune)
    -   [SharePoint Online](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)
    -   [商務用 Skype Online](/intune-classic/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)
    -   [Dynamics CRM](/intune-classic/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)
