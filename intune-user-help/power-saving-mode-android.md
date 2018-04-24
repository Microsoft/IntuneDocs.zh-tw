---
title: 電源最佳化阻止電子郵件存取 | Microsoft Docs
description: 了解如何關閉 Android 的電源最佳化，以確保取得電子郵件。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 663da92e11befeae1f65467e887870a52640cbeb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Android 開啟電池最佳化時，Outlook 不會同步處理受管理的電子郵件。

> [!IMPORTANT]
> 此問題記錄在此，是因為我們收到的客戶相關報告數量一直不斷增加。 如果在您採取下列步驟之後仍然遇到這個問題，請連絡[公司支援人員](https://portal.manage.microsoft.com#HelpDeskDialog)取得額外協助。

在 Intune 中註冊裝置，可讓您存取公司資源。 電子郵件是最常存取的資源之一。 當電池最佳化開啟時，已知在 Android 裝置上透過 Outlook 存取電子郵件會發生問題。 電池最佳化可能會自動開啟，嘗試協助裝置保持電池的續航力。 電池最佳化因為會嘗試停止自動下載電子郵件，所以能在這方面提供一些協助。

Microsoft Intune 小組正積極處理有關此問題的解決方案。 確定電池電量保持在 30% 以上，是防止裝置進入低電量模式的一種方法。 為在進入低電量模式時不發生此問題，您必須從應用程式清單中移除公司入口網站和 Outlook，讓它們不受電池最佳化和省電設定的影響。

許多 Android 裝置有很多製造商。 我們無法一一記錄每部裝置所需採取的確切步驟。 您可能只需要在系統設定中執行此動作，或也需要在某些製造商特定設定中動作。 我們提供了一些常見範例，示範如何解決 Android 裝置此一問題。

## <a name="unmodified-android-devices"></a>未修改的 Android 裝置

許多製造商會在他們的 Android 裝置中新增修改。 如此會變更您與裝置互動的某些方式，例如佈景主題和通知。 Google 通常不會在他們的電話上進行這類修改。 例如，在使用 Android 7.0 或更高版本的 Google Pixel 裝置上，您要依照下列步驟從電池最佳化中移除這些應用程式：

1. 開啟 [設定] 。
2. 點選 [電池] > [更多] > [Battery optimization] (電池最佳化)。
3. 點選向下箭號，再點選 [Not optimized] (未最佳化)。
4. 選取公司入口網站和 Outlook 應用程式，然後關閉電池最佳化。

## <a name="samsung-devices"></a>Samsung 裝置

至於其他類型的 Android 裝置，例如使用 Android 7.0 或更新版本的 Samsung 裝置，您可能必須遵循不同的步驟從電池最佳化中移除 Outlook 和公司入口網站應用程式。

1. 開啟 [設定] 。
2. 點選 [功能表 (…)]  > [特殊存取] > [Optimize battery usage] (最佳化電池使用方式)。
3. 從下拉式清單選取 [所有應用程式]。
4. **關閉**公司入口網站和 Outlook 應用程式旁邊的切換按鈕，以關閉電池最佳化。

此外，如果您使用的是具有較低 Android 版本的 Samsung 裝置，您可能需要遵循下列步驟從省電模式中移除這些應用程式。

1. 開啟 [設定] 。
2. 點選 [Device maintenance] (裝置維護) > [電池] > [Unmonitored apps] (未受監視的應用程式)。
3. 點選 [新增應用程式]。
4. 選取公司入口網站和 Outlook 應用程式，然後點選 [完成]。

## <a name="oneplus-devices"></a>OnePlus 裝置

另一個找到這些設定的不同方式範例，是搜尋系統設定。 例如，在使用 Android 7.1.1 的 OnePlus 3 裝置中，您要按照下列步驟進行： 

1. 開啟 [系統設定]。 
2. 點選 [搜尋] 按鈕。 這看起來像螢幕右上方的放大鏡。 
3. 在搜尋中鍵入**電池最佳化**，然後在出現的 [設定] 畫面中選取 [Battery optimization] (電池最佳化) 選項。 
4. 點選 [電池] > [Battery optimization] \(電池最佳化)。
5. 選取公司入口網站和 Outlook 應用程式，然後點選 [Don't optimize] (不要最佳化)。 點選 [完成]。

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

是否仍需要協助？ 請連絡您公司的支援人員。 如需其連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
