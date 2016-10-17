---
title: "使用裝置威脅保護限制存取 | Microsoft Intune"
description: "根據裝置、網路和應用程式風險，限制對公司資源的存取。"
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 92422c2937c608d1aa6c9d11517fa08e4a8c7798
ms.openlocfilehash: a3c7e7cfef6223103fe0588f900f164635b042aa


---

# 根據裝置、網路和應用程式風險，限制對公司資源的存取
您可以根據與 Microsoft Intune 整合的裝置威脅保護解決方案 Lookout 所進行的風險評估，來控制從行動裝置對公司資源的存取。 此風險的評估依據是 Lookout 服務從裝置收集到有關作業系統 (OS) 漏洞、已安裝的惡意應用程式和惡意網路設定檔的遙測資料。 根據透過 Intune 相容性原則啟用的 Lookout 風險評估，您可以在 Intune 中設定條件式存取原則，並允許或封鎖因這些裝置上偵測到的威脅而判斷為不相容的裝置。  目前支援執行 **4.1 和更新版本**的 **Android** 裝置及執行 **iOS 8 和更新版本**的裝置。 這些裝置必須註冊於 Microsoft Intune。  如需 Lookout 所支援平台和語言的相關資訊，請參閱本[文章](https://personal.support.lookout.com/hc/en-us/articles/114094140253)。
## 這會解決哪個問題？
公司和組織必須保護機密資料免於遭受新興威脅 (包括實體、應用程式型和網路型威脅) 及 OS 漏洞的攻擊。

在過去，公司和組織向來會主動保護電腦免於遭受惡意攻擊。 但行動裝置是經常未受保護的新興領域。 雖然行動平台內建有使用應用程式隔離和經審核之消費者 App Store 等技術的 OS 保護，但這些平台持續容易受到複雜的攻擊。 隨著員工愈來愈頻繁地使用行動裝置來執行工作，而且需要存取可能機密且重要的資訊，這些裝置必須受到保護，以防範各種複雜的攻擊。

Intune 可讓您根據 Lookout 等裝置威脅保護解決方案所提供的風險評估，來控制對公司資源和資料的存取。

## Intune 和 Lookout 裝置威脅保護如何協助保護公司資源？
在行動裝置上執行的 Lookout 行動裝置應用程式 (Lookout for Work) 可擷取檔案系統、網路堆疊、裝置和應用程式遙測 (如果可用)，並將其傳送至 Lookout 裝置威脅保護雲端服務，以計算行動裝置威脅的彙總裝置風險。 您也可以在 Lookout 主控台中變更威脅的風險等級分類，以符合您的需求。  

Intune 中的相容性原則現在包含新的 Lookout 行動裝置威脅保護規則，該規則是以 Lookout 裝置威脅風險評估為依據。 啟用此規則時，Microsoft Intune 會接著評估裝置是否符合您啟用的原則。

如果裝置經判斷與相容性原則不相容，則可以使用條件式存取原則封鎖對 Exchange Online 和 SharePoint Online 等資源的存取。 當存取遭到封鎖時，會提供使用者逐步解說，以協助解決問題並取得公司資源的存取權。 此逐步解說是透過 Lookout for Work 應用程式來啟動。

## 範例案例
以下是一些常見的案例：
### 根據惡意應用程式的威脅來控制存取權：
在裝置上偵測到惡意應用程式時 (例如惡意程式碼)，您可以封鎖這類裝置執行下列動作：
* 在解決威脅之前連線到公司電子郵件。
* 使用工作用 OneDrive 應用程式來同步處理公司檔案。
* 存取攸關業務的應用程式。

**偵測到惡意應用程式時封鎖存取︰**
![圖中顯示條件式存取原則在裝置因含有惡意應用程式而判斷為不相容時封鎖存取](../media/mtp/malicious-apps-blocked.png)

**補救威脅之後，裝置已解除封鎖，並且能夠存取公司資源：**

![圖中顯示條件式存取原則在補救後判斷裝置為相容時授與存取權](../media/mtp/malicious-apps-unblocked.png)
### 根據網路威脅來控制存取權：
偵測到攔截式攻擊等網路威脅，並根據裝置風險限制對 WiFi 網路的存取。

**已封鎖透過 WiFi 的網路存取︰**
![圖中顯示條件式存取根據網路威脅封鎖 WiFi 存取](../media/mtp/network-wifi-blocked.png)

**補救後授與存取權：**

![圖中顯示條件式存取在補救威脅之後允許存取](../media/mtp/network-wifi-unblocked.png)
### 根據網路威脅來控制 SharePoint Online 的存取權：

偵測到攔截式攻擊等網路威脅，並根據裝置風險防止同步處理公司檔案。

**根據裝置上偵測到的網路威脅封鎖對 SharePoint Online 的存取：**

![圖中顯示條件式存取根據威脅偵測封鎖對 SharePoint Online 的裝置存取](../media/mtp/network-spo-blocked.png)


**補救後授與存取權：**

![圖中顯示條件式存取在補救網路威脅之後允許存取](../media/mtp/network-spo-unblocked.png)

## 後續步驟
以下是為了實作此解決方案所必須執行的主要步驟：
1.  [設定訂用帳戶使用 Lookout 行動裝置威脅保護](set-up-your-subscription-with-lookout-mtp.md)
2.  [在 Intune 中啟用 Lookout MTP 連線](enable-lookout-mtp-connection-in-intune.md)
3.  [設定及部署 Lookout for Work 應用程式](configure-and-deploy-lookout-for-work-apps.md)
4.  [設定相容性原則](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Lookout 整合疑難排解](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Oct16_HO2-->


