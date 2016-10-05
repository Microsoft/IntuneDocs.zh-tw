---
title: "應用程式部署問題疑難排解 | Microsoft Intune"
description: "本主題會協助您解決 Microsoft Intune 的相關應用程式部署問題"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 30d42bc4ee38a45895320eebd665fe8f5a0cb4ee
ms.openlocfilehash: 0db3e6a39bd0d30231c339cb4501ce25059e4657


---

# Microsoft Intune 的應用程式部署問題疑難排解
如果您有使用 Intune 部署和管理應用程式的問題，請從這裡開始。 本主題包含一些您在使用解決方案上可能會遇到的常見問題。

## 常見應用程式部署錯誤碼

|錯誤碼|可能的問題|建議的解決方式|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (用戶端錯誤)|若要安裝此應用程式，您必須具有已啟用側載功能的系統。|確定應用程式套件已經由信任的簽章簽署，而且已經安裝在已加入網域並啟用 AllowAllTrustedApps 原則的電腦上，或已經安裝在具有已啟用 AllowAllTrustedApps 原則 (在註冊 Windows RT 裝置時套用) 之 Windows 側載授權的電腦上。|
|0x80073CF0|無法開啟套件。|可能的原因：<br /><br />-   套件未經簽署。<br />-   發行者名稱與簽署憑證主體不符。<br /><br />查看 AppxPackagingOM 事件記錄檔以取得詳細資訊。|
|0x80073CF3|套件更新失敗、具相依項目或發生驗證衝突|可能的原因：<br /><br />-   傳入的套件與安裝的套件衝突。<br />-   找不到指定的套件相依項目。<br />-   套件不支援正確的處理器架構。<br /><br />查看 AppXDeployment-Server 事件記錄檔以取得詳細資訊。|
|0x80073CFB|提供的套件已經安裝，不允許重新安裝套件|如果您要安裝的套件與已經安裝的套件不同，可能就會收到這項錯誤。 請確認數位簽章也包含在套件中。 重建或重新簽署套件後，該套件之位元就不再與先前安裝的套件相同。 此錯誤有下列兩種可能的修正選項：<br /><br />-   遞增應用程式的版本號碼，然後再重建及重新簽署應用程式。<br />-   在安裝新套件之前，針對系統上的每個使用者移除舊套件。|
|0x87D1041C|應用程式安裝成功，但未偵測到應用程式。|- Intune 已成功部署應用程式，接著便解除安裝 (可能為終端使用者所執行)。 指示使用者從公司入口網站重新安裝應用程式。 需要的應用程式會在裝置下次簽入時自動重新安裝。|

## 針對來自 Windows 市集的應用程式進行疑難排解

[Troubleshooting packaging, deployment, and query of Windows Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) (針對封裝、部署及查詢 Windows 市集應用程式進行疑難排解) 主題中的資訊可協助您使用 Intune 或任何其他方法疑難排解從 Windows 市集安裝應用程式時可能發生的常見問題。

## 針對將應用程式部署至受 Intune 軟體用戶端管理的電腦進行疑難排解
為了協助您針對將應用程式部署至受 Intune 軟體用戶端管理之電腦的問題進行疑難排解，您可以查看下列兩個記錄檔︰
- %ProgramFiles%\Microsoft\OnlineManagement\Logs 資料夾
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

此外，如果您需要開啟 Intune 的支援案例，則這也適用於將這些記錄檔傳送給 Microsoft。


### 後續步驟
如果這項疑難排解資訊對您沒有幫助，請連絡 Microsoft 支援服務 (如[如何取得 Microsoft Intune 支援](how-to-get-support-for-microsoft-intune.md)中所述)。



<!--HONumber=Sep16_HO4-->


