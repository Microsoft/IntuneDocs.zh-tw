---
title: "啟用相容性原則中的裝置保護規則 | Microsoft Intune"
description: "啟用裝置相容性原則中的行動裝置威脅保護規則。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: c951692d-6538-46c0-a9f0-d607ded189ae
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: fa05027e1785bb27a607aa9e31b685107a84f63f
ms.openlocfilehash: 3de68238515a2584b6f1a5785e13688097468415


---

# 啟用相容性原則中的裝置威脅保護規則
具有 Lookout 行動裝置威脅保護的 Intune 可讓您偵測行動裝置威脅，並在裝置上進行風險評估。 您可以建立相容性原則的規則以納入此風險評估，並判斷裝置是否符合您的原則。 接著，您即可使用條件式存取原則，根據裝置相容性來允許或封鎖 Exchange、SharePoint 和其他服務的存取。

若要讓 Lookout MTP 威脅偵測影響裝置的相容性原則：

* 必須啟用相容性原則中的 [裝置威脅保護] 規則。

* **Intune 管理主控台**中的 [Lookout 狀態] 頁面必須顯示為 [作用中]。 如需如何啟用 Lookout 整合的詳細資訊和指示，請參閱[在 Intune 中啟用 Lookout MTP 連線](enable-lookout-mtp-connection-in-intune.md)主題。


在相容性原則中建立裝置威脅保護規則之前，建議您先[設定訂用帳戶使用 Lookout MTP](set-up-your-subscription-with-lookout-mtp.md)、[在 Intune 中啟用 Lookout 連線](enable-lookout-mtp-connection-in-intune.md)並[設定 Lookout for Work 應用程式](configure-and-deploy-lookout-for-work-apps.md)。 唯有完成設定之後，才會強制執行相容性規則。

若要啟用裝置威脅保護規則，您可以使用現有的相容性原則或建立新的相容性原則。

在 Lookout MTP 的設定過程中，您已在 [Lookout MTP 主控台](https://aad.lookout.com)中建立一項原則，將各種威脅分類為高、中與低等級。 在 Intune 相容性原則中，您將使用威脅等級來設定允許的最高威脅等級。

在 **Intune 系統管理員主控台**的 [相容性原則] 頁面中，移至 [裝置健全狀況]，並使用切換選項啟用 [裝置威脅保護] 規則。 然後選取允許的最高威脅等級，這會是下列其中一項：
* **無 (受保護)**︰這是最安全的選項。  這表示裝置不能受到任何威脅。  一旦發現任何等級的威脅，即會將裝置評估為不相容。  
* **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
* **中**︰如果發現裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果偵測到高等級的威脅，則會將裝置判斷為不相容。
* **高**：這是最不安全的選項。 基本上，這幾乎等於允許所有威脅等級；可能只有當您僅將此解決方案用於報告用途時，才適合使用這個選項。

![顯示裝置威脅保護規則設定的螢幕擷取畫面 ](../media/mtp/mtp-compliance-policy-rule.png)

![顯示裝置威脅保護規則設定之威脅等級選項的螢幕擷取畫面](../media/mtp/mtp-compliance-policy-setting.png)

如果您建立 Office 365 和其他服務的條件式存取原則，系統會將上述相容性評估納入考量，並封鎖不相容裝置，使其無法存取公司資源，直到威脅獲得解決為止。

您可以在 **Intune 系統管理員主控台**的 [所有裝置] 頁面上，查看裝置的相容性狀態。

![Intune 管理主控台中顯示裝置相容性狀態之 [裝置] 頁面的螢幕擷取畫面](../media/mtp/mtp-device-status-intune-console.png)

## 後續步驟
* 建立條件式存取原則
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange 內部部署](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [商務用 Skype Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [動態 CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO3-->


