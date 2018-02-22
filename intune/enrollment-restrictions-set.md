---
title: "在 Intune 中設定註冊限制"
titlesuffix: Azure portal
description: "在 Intune 中限制不同平台的註冊以及設定裝置註冊限制。 \""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/30/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fab385762efa3ab095553fe21fb045f4f11ff197
ms.sourcegitcommit: 93622d740cbd12043eedc25a9699cc4256e23e7e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="set-enrollment-restrictions"></a>設定註冊限制

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

身為 Intune 系統管理員，您可以建立和管理註冊限制，定義可以註冊使用 Intune 管理的裝置數目和類型。 您可以建立多項限制，並將它們套用至不同的使用者群組。 您可以設定不同限制的[優先順序](#change-enrollment-restriction-priority)。

>[!NOTE]
>註冊限制不是安全性功能。 遭盜用的裝置可以冒用身分。 這些限制是非惡意使用者的最佳屏障。

>[!NOTE]
>正陸續針對所有 Intune 客戶推出以下所述的群組指派註冊限制和優先權功能。 全部推出後，您可能無法存取群組，也沒有優先權功能。

您可以建立的特定註冊限制包括：

- 已註冊裝置的數目上限
- 可以註冊的裝置平台：
  - Android
  - Android for Work
  - iOS
  - macOS
  - Windows
- iOS、Android、Android for Work 和 Windows 的平台作業系統版本 (只會使用 Windows 10 版本，如果允許 Windows 8.1 此項請留白)
  - 最低版本
  - 最高版本
- 限制個人擁有的裝置 (僅限 iOS、Android、Android for Work、macOS)

## <a name="default-restrictions"></a>預設限制

裝置類型和裝置限制註冊限制都會自動提供預設限制。 您可以變更預設選項。 預設限制適用於所有使用者和無使用者註冊。 您可以使用較高的優先順序建立新的限制，覆寫這些預設值。

## <a name="create-a-restriction"></a>建立限制

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]，搜尋 [Intune]，然後選擇 [Intune]。
3. 選擇 [裝置註冊] > [註冊限制]。
4. 選擇 [建立限制]。
5. 提供限制的名稱和描述。
6. 選擇 [限制類型]，然後按一下 [建立]。
7. 如需限定裝置限制，請按一下 [裝置限制] 設定使用者能夠註冊的裝置數上限。
8. 如需裝置類型限制，請按一下 [平台] 和 [平台設定] 允許或封鎖各種平台和版本。
9. 按一下 [指派] > + [選取群組]。
10. 在 [選取群組] 下，選取一或多個群組，然後按一下 [選取]。 限制只適用於指派限制的群組。 如果限制不指派給至少一個群組，就不會產生任何效果。
11. 按一下 **[儲存]**。
12. 新建立的限制優先順序剛好在預設值前。 您可以[變更優先順序](#change-enrollment-restriction-priority)。

## <a name="set-device-type-restrictions"></a>設定裝置類型限制

您可以遵循下列步驟變更裝置類型限制的設定：

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]，搜尋 [Intune]，然後選擇 [Intune]。
3. 選擇 [裝置註冊] > [註冊限制]。
4. 在 [裝置類型限制] 下選擇您想要設定的限制。
5. 在限制名稱下 (預設限制為 [所有使用者])，選取 [平台]。 為每個列出的平台選擇 [允許] 或 [封鎖]。
6. 按一下 **[儲存]**。
7. 在限制名稱下 (預設限制為 [所有使用者])，選取 [平台設定] 並選取所列平台的 [版本] 最小值及最大值。 支援的版本包括：
  - Android 和 Android for Work 支援 major.minor.rev.build。
  - iOS 支援 major.minor.rev。
  - Windows 支援 major.minor.rev.build，僅限 Windows 10。
  作業系統版本不適用於以裝置註冊計劃、Apple School Manager 或 Apple Configurator 應用程式註冊的 Apple 裝置。
8. 指定要 [允許] 還是 [封鎖] 每個平台列出的**個人所有**裝置。

    ![顯示設定 [個人所擁有] 設定之預設裝置平台設定的裝置限制工作區螢幕擷取畫面。](media/device-restrictions-platform-configurations.png)
9. 按一下 **[儲存]**。

>[!NOTE]
>- 如果您從註冊封鎖個人擁有的 Android 裝置，則個人擁有的 Android for Work 裝置仍可以註冊。
>- 根據預設，Android for Work 裝置設定會與您的 Android 裝置設定相同。 不過，變更 Android for Work 設定後，就不再是那麼回事了。
>- 如果您封鎖個人的 Android for Work 註冊，只有公司的 Android 裝置可以註冊為 Android for Work。

## <a name="set-device-limit-restrictions"></a>設定裝置限制

您可以遵循下列步驟變更裝置限制的設定：

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]，搜尋 [Intune]，然後選擇 [Intune]。
3. 選擇 [裝置註冊] > [註冊限制]。
4. 在 [裝置限制] 下選擇您想要設定的限制。
5. 選擇 [裝置限制]，然後在下拉式清單中，選取使用者可以註冊的裝置數目上限。
    ![有裝置數量限制之 [device limit restrictions] (裝置數量限制) 刀鋒視窗的螢幕擷取畫面。](./media/device-restrictions-limit.png)
6. 按一下 **[儲存]**。

您的使用者會看到通知，告訴他們何時符合其已註冊裝置的限制。 例如，在 iOS 上，它看起來會像這樣：

![iOS 裝置限制通知的螢幕擷取畫面](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>變更註冊限制優先順序

當使用者屬於多個指派限制的群組時，會使用優先順序。 使用者只受制於所屬群組被指派的最高優先順序限制。 例如，Joe 屬於指派了優先順序 5 限制的群組 A 與指派了優先順序 2 限制的群組 B。 Joe 只受制於優先順序 2 限制。

當您建立一項限制時，它會新增至清單，剛好高預設值一階。

裝置註刪包括裝置類型和裝置限制的預設限制。 除非為更高的優先順序限制所覆寫，否則這兩項限制適用於所有使用者。

您可以變更任何非預設限制的優先順序。

**變更限制優先順序**

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]，搜尋 [Intune]，然後選擇 [Intune]。
3. 選擇 [裝置註冊] > [註冊限制]。
4. 將滑鼠停留在優先順序清單的限制上。
5. 使用三個垂直點，將優先順序拖曳到所要的清單位置。
