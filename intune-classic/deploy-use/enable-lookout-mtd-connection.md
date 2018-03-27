---
title: 在 Intune 中啟用 Lookout MTP
description: 在 Intune 管理主控台中啟用 Lookout 行動裝置威脅保護。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2f835fd0-4e62-42f3-b7ca-ce8b7ddd40e4
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 99c9952b8df3e9b4b1992cbc45366a5ceed458aa
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="enable-lookout-mtd-connection-in-the-intune-classic-portal"></a>在 Intune 傳統入口網站中啟用 Lookout MTD 連線

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要在 Intune 中啟用 Lookout Mobile Threat Defense (MTD) 連線，您應該已在 Lookout 主控台中設定 Intune 連接器。  如果您尚未這麼做，則應該[設定您的 Lookout Mobile Threat Defense 訂閱](setup-your-lookout-mtd-subscription.md)。

若要在 Intune 中啟用 Lookout MTP 連線，請在 [Microsoft Intune 系統管理員主控台](https://manage.microsoft.com)的 [系統管理] 頁面上，選擇 [協力廠商服務整合]。 選擇 [Lookout 狀態] 並使用切換按鈕啟用 [與 MTP 同步處理]。

![醒目提示啟用切換按鈕之 Lookout 同步處理頁面的螢幕擷取畫面](../media/mtp/lookout-intune-synchronization.png)

>[!IMPORTANT]
> 您**必須**先設定 Lookout for Work 應用程式，再建立合規性政策規則及設定條件式存取。 這樣做可確保應用程式已準備好供使用者進行安裝，安裝後，使用者才能存取電子郵件或其他公司資源。

如此即完成 Intune 系統管理員主控台中的 Lookout 與 Intune 整合設定。  實作此解決方案的接下來幾個步驟，涉及部署 [Lookout for Work 應用程式](/intune-classic/deploy-use/device-threat-protection-policy)原則。


## <a name="next-steps"></a>接下來的步驟
[設定 Lookout 工作應用程式](/intune-classic/deploy-use/device-threat-protection-apps)
