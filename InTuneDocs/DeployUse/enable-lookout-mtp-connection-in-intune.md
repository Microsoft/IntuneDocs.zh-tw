---
title: "在 Intune 中啟用 Lookout MTP | Microsoft Intune"
description: "在 Intune 管理主控台中啟用 Lookout 行動裝置威脅保護。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ceaeba74f8671caf4125252fce02fd06752c3fe8
ms.openlocfilehash: 2052aca24baa752bc4fad3bd7a75f8efa109e9e9


---

# 在 Intune 管理主控台中啟用 Lookout MTP 連線
本主題說明如何在 Intune 中啟用 Lookout MTP 連線。 執行此步驟之前，您應該已在 Lookout 主控台中設定 Intune 連接器。  如果您尚未這麼做，請執行[設定訂用帳戶使用 Lookout 行動裝置威脅保護](set-up-your-subscription-with-lookout-mtp.md)中所述的步驟。

若要在 Intune 中啟用 Lookout MTP 連線，請在 [Microsoft Intune 系統管理員主控台](https://manage.microsoft.com)的 [系統管理] 頁面上，選擇 [協力廠商服務整合]。 選擇 [Lookout 狀態] 並使用切換按鈕啟用 [與 MTP 同步處理]。

![醒目提示啟用切換按鈕之 Lookout 同步處理頁面的螢幕擷取畫面](../media/mtp/lookout-intune-synchronization.png)

如此即完成 Intune 系統管理員主控台中的 Lookout 與 Intune 整合設定。  實作此解決方案的接下來幾個步驟，涉及部署 [Lookout for Work 應用程式](configure-and-deploy-lookout-for-work-apps.md)，以及設定[相容性](enable-device-threat-protection-rule-in-compliance-policy.md)原則。

>[!IMPORTANT]
> 您**必須**先設定 Lookout for Work 應用程式，再建立相容性原則規則及設定條件式存取。 這樣做可確保應用程式已準備好供使用者進行安裝，安裝後，使用者才能存取電子郵件或其他公司資源。
## 後續步驟
[設定 Lookout for Work 應用程式 ](configure-and-deploy-lookout-for-work-apps.md)



<!--HONumber=Sep16_HO4-->


