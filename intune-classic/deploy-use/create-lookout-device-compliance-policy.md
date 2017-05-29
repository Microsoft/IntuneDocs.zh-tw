---
title: "啟用裝置保護規則 | Microsoft Docs"
description: "啟用裝置相容性原則中的行動裝置威脅保護規則。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 67913bfcbca3cef52e309ad86bfe722db6e16895
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="create-lookout-device-compliance-policy-in-intune"></a>在 Intune 中建立 Lookout 裝置合規性原則

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

具有 Lookout Mobile Threat Defense 的 Intune 可讓您偵測行動裝置上的威脅，以及評估那些裝置上的風險。 您可以建立評估風險的相容性原則規則，來判斷裝置是否相容。 接著，您即可使用條件式存取原則，根據裝置相容性來封鎖對服務的存取。

具有 Lookout Mobile Threat Defense 之合規性原則的必要條件：

- [設定 Lookout Mobile Threat Defense 訂閱](setup-your-lookout-mtd-subscription.md)
- [在 Intune 中啟用 Lookout 連線](enable-lookout-mtd-connection.md)
- [設定及部署 Lookout for Work 應用程式](configure-deploy-lookout-for-work-app.md)

在 Lookout Mobile Threat Defense 的設定過程中，您已在 [Lookout 主控台](https://aad.lookout.com)中建立一項原則來將各種威脅分類為高、中和低。 在 Intune 相容性原則中，您設定允許的最高威脅層級。

1. 在 [Intune 系統管理員主控台](https://manage.microsoft.com)中，移至 [相容性原則] 頁面。 您可以使用現有的相容性原則，也可以建立新的相容性原則。 移至 [裝置健全狀況]，並啟用 [裝置威脅防護]。
  ![顯示裝置威脅防護規則設定的螢幕擷取畫面 ](../media/mtp/mtp-compliance-policy-rule.png)

2. 選取 [允許的最高威脅層級]：
  * **無 (受保護)**：這是最安全的選項。  裝置不能在具有任何威脅的同時還能存取公司資源。  發現任何威脅時，即會將裝置評估為不相容。  
  * **低**︰如果只有低層級的威脅，則裝置相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
  * **中**︰如果發現裝置有低層級或中層級的威脅，則裝置相容。 如果偵測到高等級的威脅，則會將裝置判斷為不相容。
  * **高**：這是最不安全的選項。 這可允許所有威脅層級，並僅針對報告用途使用 Lookout 行動裝置威脅防護。

![顯示裝置威脅保護規則設定之威脅等級選項的螢幕擷取畫面](../media/mtp/mtp-compliance-policy-setting.png)

如果您建立 Office 365 或其他服務的條件式存取原則，則會評估這個相容性評估，並封鎖不相容裝置，使其無法存取這些服務，直到威脅獲得解決為止。

## <a name="monitor-device-threats"></a>監視裝置威脅
若要查看裝置的相容性狀態，請移至 [Intune 系統管理員主控台](https://manage.microsoft.com)，並檢視 [所有裝置]。

![Intune 管理主控台中顯示裝置相容性狀態之 [裝置] 頁面的螢幕擷取畫面](../media/mtp/mtp-device-status-intune-console.png)

## <a name="next-steps"></a>後續步驟
* 建立條件式存取原則
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange 內部部署](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [商務用 Skype Online](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
  * [Dynamics CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)

