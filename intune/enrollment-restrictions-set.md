---
title: "在 Intune 中設定註冊限制"
titleSuffix: Intune on Azure
description: "在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。 \""
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2dfcba8c788f262ce816dcd23dc2921fd57f331b
ms.sourcegitcommit: d1ad84edf4f03cb4c11fe55131556b43fc3a4500
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2017
---
# <a name="set-enrollment-restrictions"></a>設定註冊限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 Intune 管理員，您可以決定哪些裝置可以註冊使用 Intune 管理。 使用 Intune 入口網站設定下列裝置註冊限制：

- 已註冊裝置的數目上限
- 可以註冊的裝置平台：
  - Android
  - iOS
  - macOS
  - 訊息
- 限制個人擁有的裝置 (僅限 iOS 與 Android)

>[!NOTE]
>註冊限制不是安全性功能。 遭盜用的裝置可以冒用身分。 這些限制是非惡意使用者的最佳屏障。

## <a name="set-device-type-restrictions"></a>設定裝置類型限制
預設註冊限制適用於所有未獲指派較高優先順序註冊限制的使用者。  
1. 在 Intune 入口網站中，依序選擇 [裝置註冊] 和 [註冊限制]。
![有預設裝置類型限制和裝置數量限制的 [裝置限制] 工作區螢幕擷取畫面。](media/device-restrictions-set-default.png)
2. 選取 [註冊限制]  >  [裝置類型限制] 下的 [預設]。
3. 選取 [所有使用者] 下的 [平台]。 為每個平台選擇 [允許] 或 [封鎖]：
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  按一下 [儲存]。
4. 選取 [所有使用者] 下的 [平台設定]，然後選取下列設定：
  - **個人所擁有** - 指定要 [允許] 或 [封鎖] Android 和 iOS 裝置。
  ![顯示設定 [個人所擁有] 設定之預設裝置平台設定的裝置限制工作區螢幕擷取畫面。](media/device-restrictions-platform-configurations.png)
  按一下 [儲存]。

>[!NOTE]
>如果您從註冊封鎖個人擁有的 Android 裝置，Android for Work 裝置仍可以註冊。

## <a name="set-device-limit-restrictions"></a>設定裝置限制
預設註冊限制適用於所有未獲指派較高優先順序註冊限制的使用者。  
1. 在 Intune 入口網站中，依序選擇 [裝置註冊] 和 [註冊限制]。
2. 選擇 [註冊限制] > [Device Limit Restrictions] (裝置數量限制)。
3. 選取 [所有使用者] 下的 [裝置限制]。 指定每位使用者已註冊裝置的數目上限。  
![有裝置數量限制之 [device limit restrictions] (裝置數量限制) 刀鋒視窗的螢幕擷取畫面。](./media/device-restrictions-limit.png)

  按一下 [儲存]。
