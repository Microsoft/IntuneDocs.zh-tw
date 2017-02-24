---
title: "設定行動裝置管理授權單位 | Intune Azure Preview | Microsoft Docs"
description: "Intune Azure Preview︰了解如何在 Intune 中設定行動裝置管理授權單位。 "
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8deff871-5dff-4767-9484-647428998d82
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 08dad848a48adad7d9c6f0b5b3286f6550a266bd
ms.openlocfilehash: 72a162175e278faa236add5698d65233fa851c7b

---

# <a name="set-the-mobile-device-management-authority"></a>設定行動裝置管理授權單位 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

行動裝置管理授權單位設定決定您如何管理裝置。 可能的設定如下︰

- **Intune 獨立版** - 雲端版管理解決方案，可透過 Azure 入口網站設定。 包含 Intune 提供的完整功能集。

- **Intune 混合版** - Intune 雲端解決方案與 System Center Configuration Manager 的整合版。 您可以使用 Configuration Manager 主控台設定 Intune。

- **Office 365 的行動裝置管理** - Office 365 與 Intune 雲端解決方案的整合版。 您可以從 Office 365 系統管理中心設定 Intune。 包含 Intune 獨立版提供的功能子集。

>[!IMPORTANT]
>當您設定行動裝置管理授權單位之後，必須連絡 [Microsoft 支援服務](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune)加以變更，因此請務必慎選。

**設定行動裝置管理授權單位：**

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 [Intune] 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [概觀]。

3. 在 [開始管理裝置] 刀鋒視窗上，選擇 [將 MDM 授權單位設為 Intune]。 接著會顯示一則訊息指出您已成功將 Intune 設定為 MDM 授權單位。



<!--HONumber=Feb17_HO3-->


