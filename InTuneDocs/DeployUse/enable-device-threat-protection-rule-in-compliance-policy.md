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
ms.sourcegitcommit: 9c2ffb5fe497d56d8250fe3dec7db606c2067a1c
ms.openlocfilehash: 761372b2c8b81699bc2584ab1ef8d0f9d523abe9


---

# 啟用相容性原則中的裝置威脅保護規則
具有 Lookout 行動裝置威脅保護的 Intune 可讓您偵測行動裝置威脅，並在裝置上進行風險評估。  
相容性原則規則可讓您使用此風險評估，來判斷裝置是否符合您的原則。 您接著可以使用條件式存取原則，根據裝置相容性來允許或封鎖 Exchange、SharePoint 和其他服務的存取。

若要讓 Lookout MTP 威脅偵測影響裝置的相容性原則：

1.  必須啟用相容性原則中的 [裝置威脅保護] 規則。

2.  Intune 管理主控台中的 [Lookout 狀態] 頁面必須顯示 [作用中]。 如需如何啟用 Lookout 整合的詳細資訊和指示，請參閱[在 Intune 中啟用 Lookout MTP 連線](enable-lookout-mtp-connection-in-intune.md)主題。


## 設定裝置威脅保護規則

在相容性原則中建立裝置威脅保護規則之前，建議您[設定訂用帳戶使用 Lookout MTP](set-up-your-subscription-with-lookout-mtp.md)、[在 Intune 中啟用 Lookout 連線](enable-lookout-mtp-connection-in-intune.md)和[設定 Lookout for Work 應用程式](configure-and-deploy-lookout-for-work-apps.md)。 設定完成之後，只會強制執行相容性規則一次。

若要啟用裝置威脅保護規則，您可以使用現有的相容性原則或建立新的相容性原則。

在 Lookout MTP 的設定過程中，您已在 [Lookout MTP 主控台](https://aad.lookout.com)中建立一項原則，將各種威脅分類為高、中與低等級。 在 Intune 相容性原則中，您將使用威脅等級來設定允許的最高威脅等級。

在 Intune 系統管理員主控台的 [相容性原則] 頁面中，移至 [裝置健全狀況]，並使用切換選項啟用 [裝置威脅保護] 規則。 然後選取允許的最高威脅等級，這會是下列其中一項：
* **無 (受保護)**︰這是最安全的選項。  這表示裝置不能有任何威脅。  如果在裝置上偵測到任何威脅等級，則會評估為不相容。  
* **低**︰如果只有低等級的威脅，則會將裝置評估為相容。 任何更高等級的威脅都會使裝置處於不相容狀態。
* **中**︰如果裝置有低等級或中等級的威脅，則會將裝置評估為相容。 如果在裝置上偵測到高等級的威脅，則會判斷為不相容。
* **高**：這是最不安全的選項。 基本上，這會允許所有威脅等級，或許僅在此解決方案的用途只有報告時才適用。

![顯示裝置威脅保護規則設定的螢幕擷取畫面 ](../media/mtp/mtp-compliance-policy-rule.png)

![顯示裝置威脅保護規則設定之威脅等級選項的螢幕擷取畫面](../media/mtp/mtp-compliance-policy-setting.png)

如果您建立 O365 和其他服務的條件式存取原則，則會將上述相容性評估納入考量，並封鎖不相容裝置的存取，直到威脅獲得解決為止。

您可以在 Intune 系統管理員主控台的 [裝置] 頁面上，查看裝置的相容性狀態。

![Intune 管理主控台中顯示裝置相容性狀態之 [裝置] 頁面的螢幕擷取畫面](../media/mtp/mtp-device-status-intune-console.png)

## 後續步驟
* 建立條件式存取原則
  * [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md)
  * [Exchange 內部部署](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
  * [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md)
  * [商務用 Skype Online](restrict-access-to-skype-for-business-online-with-microsoft-intune,md)
  * [動態 CRM](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


