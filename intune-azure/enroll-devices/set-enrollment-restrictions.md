---
title: "在 Intune 中設定註冊限制"
titleSuffix: Intune Azure preview
description: "Intune Azure Preview：在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。 "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 56996592febf0be5ab74b158a70404728fe17a4d
ms.lasthandoff: 02/18/2017

---

# <a name="set-enrollment-restrictions"></a>設定註冊限制 

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

您也可以設定您將允許註冊的裝置類型和數目上限。 在 [註冊限制] 刀鋒視窗上，您可以設定︰

- 允許註冊的平台，以及是否封鎖註冊適用於 Android 和 iOS 的個人擁有裝置。

- 使用者能夠註冊的裝置數上限。

## <a name="set-device-type-restrictions"></a>設定裝置類型限制

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 [Intune] 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [註冊限制]。

3. 從 [裝置類型限制] 下選取 [預設]。

4. 在 [所有使用者] 刀鋒視窗上，選取 [平台]。

5. 對於可以在 Intune 中註冊的平台，請選取 [允許]。 對於您要禁止註冊的平台，請選取 [封鎖]。 平台預設會設定為 [允許]。 

    >[!NOTE]
    >這些設定不適用於或封鎖使用 Intune 軟體用戶端的 Windows 註冊。 這些設定只會影響使用行動裝置管理的註冊。 

6. 選取 [儲存]。

7. 選取 [平台設定]。

8. 選擇要 [允許] 或 [封鎖] 註冊個人擁有的 iOS 和 Android 裝置。

9. 選取 [儲存]。

## <a name="set-device-limit-restrictions"></a>設定裝置限制

1. 在 Azure 入口網站中，選擇 [更多服務] > [監視 + 管理] > [Intune]。

2. 在 [Intune] 刀鋒視窗上，選擇 [註冊裝置]，然後選擇 [註冊限制]。

3. 在 [裝置限制] 下選取 [預設]。

4. 在 [所有使用者] 刀鋒視窗上，選取 [裝置限制]。

5. 選取使用者能夠註冊的裝置數上限，然後選取 [儲存]。

