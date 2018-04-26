---
title: 使用 Microsoft Intune 重設裝置密碼 - Azure | Micrososft Docs
description: 使用您以 Intune 管理或監視之裝置上的移除密碼動作，移除或重設密碼。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 905c51dcbc5b7731be207c25ffd368b339dbec57
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>在 Intune 中重設或移除裝置密碼

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

若要建立新的裝置密碼，請使用 [移除密碼] 動作。

## <a name="supported-platforms"></a>支援的平台

- 以工作設定檔、7.0 版及更新版本註冊的 Android 裝置
- 版本為 6.0 或更舊版本的 Android 裝置
- iOS 
     
## <a name="unsupported-platforms"></a>不支援的平台

- 以工作設定檔、6.0 版及更舊版本註冊的 Android 裝置
- 版本為 7.0 或更新版本的 Android 裝置
- macOS
- Windows

## <a name="reset-a-passcode"></a>重設密碼

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]，然後選取 [所有裝置]。
4. 從您管理的裝置清單中選取裝置，再選擇 [...More] (...其他)。 然後選擇 [Remove passcode] (移除密碼) 裝置遠端動作。

## <a name="resetting-android-for-work-passcodes"></a>重設 Android for Work 密碼

支援的 Android for Work 裝置會收到新的裝置解除鎖定密碼，或使用者的受控設定檔查問。 針對具有工作設定檔的 Android 7.0 或更新版本裝置，使用者會在完成註冊後立即收到啟用其重設密碼權杖的通知。 如果工作設定檔密碼為必要且已設定，就會顯示通知。 輸入其密碼之後，就會關閉通知。

## <a name="resetting-ios-passcodes"></a>重設 iOS 密碼

密碼會從 iOS 裝置中移除。 如果已設定密碼合規性原則，則裝置會提示使用者在 [設定] 中設定新密碼。 

## <a name="next-steps"></a>接下來的步驟

若要查看您剛採取的動作狀態，請在 [裝置] 中選擇 [裝置動作]。
