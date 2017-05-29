---
title: "設定行動裝置管理授權單位"
titleSuffix: Intune Azure preview
description: "Intune Azure Preview︰了解如何在 Intune 中設定行動裝置管理授權單位。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 04/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: c36ddef7e53d6f4f15c82c97dc6d18863e6859f1
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---

# <a name="set-the-mobile-device-management-authority"></a>設定行動裝置管理授權單位

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

行動裝置管理 (MDM) 授權單位設定會決定您管理裝置的方式。 身為 IT 系統管理員，您必須在使用者可以註冊裝置以進行管理之前，設定 MDM 授權單位。

可能的設定如下︰

- **Intune 獨立版** - 雲端版管理解決方案，可透過 Azure 入口網站設定。 包含 Intune 提供的完整功能集。 [在 Intune 主控台中設定 MDM 授權單位](#mdm-authority-set-to-intune)。

- **Intune 混合版** - Intune 雲端解決方案與 System Center Configuration Manager 的整合版。 您可以使用 Configuration Manager 主控台設定 Intune。 [在 Configuration Manager 中設定 MDM 授權單位](https://docs.microsoft.com/sccm/mdm/deploy-use/configure-intune-subscription)。

- **Office 365 的行動裝置管理** - Office 365 與 Intune 雲端解決方案的整合版。 您可以從 Office 365 系統管理中心設定 Intune。 包含 Intune 獨立版提供的功能子集。 在 Office 365 系統管理中心中設定 MDM 授權單位。

>[!IMPORTANT]
>當您設定行動裝置管理授權單位之後，必須連絡 [Microsoft 支援服務](https://docs.microsoft.com/intune-classic/troubleshoot/get-support)加以變更，因此請務必慎選。

## <a name="set-mdm-authority-to-intune"></a>將 MDM 授權單位設為 Intune

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。
  ![Intune 疑難排解工作負載 (包含選取使用者連結) 的螢幕擷取畫面](media/set-mdm-auth.png)
2. 在 [Intune] 刀鋒視窗上，選擇 [裝置註冊]，然後選擇 [概觀]。

3. 在 [開始管理裝置] 刀鋒視窗上，選擇 [將 MDM 授權單位設為 Intune]。 接著會顯示一則訊息指出您已成功將 Intune 設定為 MDM 授權單位。

