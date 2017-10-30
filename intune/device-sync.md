---
title: "使用 Intune 同步裝置"
titlesuffix: Azure portal
description: "了解如何使用 Intune 同步處理裝置以取得最新的原則和動作。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dadcd33f39827365fc3f22c46d4332f3ea3cbf09
ms.sourcegitcommit: a1c751959c9b3d5678bd9d67007e762df30eab59
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2017
---
# <a name="sync-devices-with-intune-to-get-the-latest-policies-and-actions"></a>使用 Intune 同步裝置以取得最新的原則和動作


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[同步] 裝置動作會強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。  這個動作可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。

## <a name="supported-platforms"></a>支援的平台

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="how-to-sync-a-device"></a>如何同步裝置

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [同步] 遠端動作。
7. 選擇 [是] 確認該動作。


## <a name="retriable-error-codes"></a>可重試的錯誤碼

當系統管理員執行 [同步] 裝置動作時，失敗但引發可重試錯誤碼的 iOS 和 Androids 應用程式將提供給裝置使用。 不過，引發不可重試錯誤碼的應用程式必須等候七天，才能提供給裝置使用。


| 錯誤碼  | 建議的描述                                                                                                                  | 可重試 |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------|-----------|
| 2016330898 | 發生未知的錯誤。                                                                                                             | 否        |
| 2016330897 | Intune 的連接逾時。請重設您的連線                                                                             | 是       |
| 2016330896 | 失去網際網路連線。 請重設您的連線。                                                                            | 是       |
| 2016330895 | 失去網際網路連線。 請重設您的連線。                                                                            | 是       |
| 2016330894 | 失去網際網路連線。 請重設您的連線。                                                                            | 是       |
| 2016330893 | 失去網際網路連線。 請重設您的連線。                                                                            | 是       |
| 2016330892 | 已停用國際漫遊。                                                                                                     | 否        |
| 2016330891 | 通話進行時，無法存取此裝置的行動電話通訊資料連線。 請等候通話完成。 | 是       |
| 2016330890 | 此裝置的行動電話通訊網路。 此時無法使用這些裝置。                                                   | 否        |
| 2016330889 | 安全連線失敗。 請重設您的連線。                                                                                   | 是       |
| 2016330888 | 伺服器信任評估失敗。                                                                                                | 否        |

## <a name="next-steps"></a>後續步驟

選擇 [裝置動作] 以查看同步動作的狀態。 
