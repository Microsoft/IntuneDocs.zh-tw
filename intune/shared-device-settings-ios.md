---
title: "適用於 iOS 的 Intune 共用裝置組態設定"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰了解您可以用來在 iOS 裝置鎖定畫面上顯示資訊的 Intune 設定。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/12/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f122e4ee-90e7-4b42-b801-8c1c7c0a5bf7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 6a2aba8b2f062a3e06d517a572992b84fd977514
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>在 iOS 裝置鎖定畫面上顯示訊息的共用裝置組態設定

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

共用裝置組態設定可讓您指定登入視窗與鎖定畫面上所顯示的選擇性文字 (例如，「若遺失，請送回」訊息和「資產標籤資訊」)。 

>[!IMPORTANT]
> 執行 iOS 9.3 和更新版本的受監督裝置支援這項功能。

1. 在 [裝置功能] 刀鋒視窗上，選擇 [共用裝置設定 (僅限受監督)]。
2. 在 [共用裝置設定 (僅限受監督)] 刀鋒視窗上，設定下列各項：
    - **資產標籤資訊**：輸入裝置資產標籤的相關資訊。 例如：「由 Contoso 公司所擁有」。您輸入的資訊將會套用至您指派此設定檔的所有裝置上。
    - **鎖定畫面註腳**：輸入裝置遺失或遭竊時，可能有助於取回裝置的備註。 例如：「如果拾獲，請撥打 (號碼)」。
3. 完成之後，選擇 [確定] 直到您返回 [建立設定檔] 刀鋒視窗，然後選擇 [建立]。 

