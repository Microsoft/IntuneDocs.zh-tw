---
title: "在 Intune 中啟用 Skycure Mobile Threat Defense"
description: "在 Intune 傳統入口網站中啟用 Skycure Mobile Threat Defense。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0cc4e59d-819a-47a2-a26f-4f8d0f8df7bf
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ce0e61a27f44f0c6cb00d79442d346db679a55ea
ms.sourcegitcommit: 1a54bdf22786aea1cf1b497d54024470e1024aeb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/10/2017
---
# <a name="enable-skycure-mobile-threat-defense-in-intune"></a>在 Intune 中啟用 Skycure Mobile Threat Defense

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

若要啟用 Skycure Mobile Threat Defense，您應該已設定 [Skycure 主控台中的 Intune 連接器] (/intune-classic/deploy-use/setup-the-skycure-integration-with-Intune)。

## <a name="to-enable-the-skycure-mtd-connection-in-intune"></a>在 Intune 中啟用 Skycure MTD 連線

1.  移至 [Intune 傳統入口網站](https://manage.microsoft.com/)，然後輸入您的認證。

2.  選擇 [管理] &gt; [協力廠商服務整合]，然後選擇 [Skycure 狀態]，接著使用切換按鈕來啟用 [以 MTD 進行同步處理]。

    ![在 Intune 傳統入口網站中啟用 Skycure 切換](../media/mtp/enable-skycure-1.png)

> [!IMPORTANT] 
> 您必須先設定 Skycure 應用程式，然後建立合規性原則規則及設定條件式存取。 這樣做可確保應用程式已準備好供使用者進行安裝，安裝後，使用者才能存取電子郵件或其他公司資源。

如此即會完成 Intune 管理員主控台中的 Skycure 與 Intune 整合設定。 實作此解決方案的後續幾個步驟，涉及部署 Skycure for Work 應用程式，以及設定合規性原則。

## <a name="next-steps"></a>後續步驟

[建立 Skycure Mobile Threat Defense 合規性原則](/intune-classic/deploy-use/create-skycure-mobile-threat-defense-compliance-policy)
