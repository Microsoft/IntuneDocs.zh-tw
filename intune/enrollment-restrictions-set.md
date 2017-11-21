---
title: "在 Intune 中設定註冊限制"
titlesuffix: Azure portal
description: "在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。 \""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.date: 11/6/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 463278e4dc9ad677f654754d4710b110b376cc2d
ms.sourcegitcommit: 5279a0bb8c5aef79aa57aa247ad95888ffe5a12b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/08/2017
---
# <a name="set-enrollment-restrictions"></a>設定註冊限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 Intune 管理員，您可以決定哪些裝置可以註冊使用 Intune 管理。 使用 Azure 入口網站設定下列裝置註冊限制：

- 已註冊裝置的數目上限
- 可以註冊的裝置平台：
  - Android
  - iOS
  - macOS
  - 訊息
- iOS、Android 和 Windows 的平台作業系統版本 (只會使用 Windows 10 版本，如果允許 Windows 8.1 此項請留白)
  - 最低版本
  - 最高版本
- 限制個人擁有的裝置 (僅限 iOS、Android、macOS)

>[!NOTE]
>註冊限制不是安全性功能。 遭盜用的裝置可以冒用身分。 這些限制是非惡意使用者的最佳屏障。

## <a name="set-device-type-restrictions"></a>設定裝置類型限制
預設註冊限制適用於所有使用者和無使用者註冊。
1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 選擇 [裝置註冊] > [註冊限制]。
4. 選取 [註冊限制]  >  [裝置類型限制] 下的 [預設]。
5. 選取 [所有使用者] 下的 [平台]。 為每個平台選擇 [允許] 或 [封鎖]：
  - **Android**
  - **iOS**
  - **macOS**
  - **Windows**

  按一下 **[儲存]**。
6. 選取 [所有使用者] 下的 [平台設定]，然後選取下列設定。 每個允許的平台都可以設定下列選項：
  - **版本** - 指定 Android、iOS 或 Windows 裝置平台作業系統版本的 [最小值] 和 [最大值]。 Android 支援 major.minor.rev.build。 iOS 支援 major.minor.rev。Windows 支援 major.minor.rev.build，僅限 Windows 10。 作業系統版本不適用於以裝置註冊計劃、Apple School Manager 或 Apple Configurator 應用程式註冊的 Apple 裝置。 
  - **個人所擁有** - 指定要 [允許] 或 [封鎖] Android、iOS 和 macOS 裝置。
  ![顯示設定 [個人所擁有] 設定之預設裝置平台設定的裝置限制工作區螢幕擷取畫面。](media/device-restrictions-platform-configurations.png)
  按一下 **[儲存]**。

>[!NOTE]
>如果您從註冊封鎖個人擁有的 Android 裝置，則個人擁有的 Android for Work 裝置仍可以註冊。

## <a name="set-device-limit-restrictions"></a>設定裝置限制
預設註冊限制適用於所有使用者。
1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 選擇 [裝置註冊] > [註冊限制]。
4. 在 Azure 入口網站中，依序選擇 [裝置註冊] 和 [註冊限制]。
5. 選擇 [註冊限制] > [Device Limit Restrictions] (裝置數量限制)。
6. 選取 [所有使用者] 下的 [裝置限制]。 指定每位使用者已註冊裝置的數目上限。  
![有裝置數量限制之 [device limit restrictions] (裝置數量限制) 刀鋒視窗的螢幕擷取畫面。](./media/device-restrictions-limit.png)

  按一下 [儲存]。
