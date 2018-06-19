---
title: 使用 Microsoft Intune 同步處理裝置 - Azure | Micrososft Docs
description: 同步處理使用 Microsoft Intune 註冊或管理的裝置，以取得最新的原則和動作。 使用 Azure 入口網站包含要同步處理的步驟，並列出可重試的錯誤碼。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 02ad249e-f098-421f-861f-6b2ff733ac7c
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fb609f0d99378e2e30b3c3a4f769781448aea1b5
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31833360"
---
# <a name="sync-devices-to-get-the-latest-policies-and-actions-with-intune"></a>使用 Intune 同步裝置以取得最新的原則和動作


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[同步] 裝置動作會強制所選裝置立即使用 Intune 簽入。 當裝置簽入時，會立即收到所有擱置動作或已指派給它的原則。 這項功能可協助您立即驗證和針對您已指派的原則進行疑難排解，不用等到下次排程的簽入。

## <a name="supported-platforms"></a>支援的平台

- Windows
- Windows Phone
- iOS
- macOS
- Android

## <a name="sync-a-device"></a>同步處理裝置

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。 
3. 在 [Intune] 中選取 [裝置] > [所有裝置]。
4. 在您管理的裝置清單中，依序選取裝置、[其他]，然後選取 [同步處理]。
5. 選取 [是] 確認。


## <a name="retryable-error-codes"></a>可重試的錯誤碼

當系統管理員執行 [同步處理] 裝置動作時，失敗但引發可重試錯誤碼的 iOS 和 Androids 應用程式將提供給裝置使用。 不過，引發不可重試錯誤碼的應用程式必須等候七天，才能提供給裝置使用。


| 錯誤碼  | 建議的描述 | 可重試 |
|---|---|---|
| 2016330898 | 發生未知的錯誤。 | 否 |
| 2016330897 | Intune 的連接逾時。請重設您的連線。 | 是 |
| 2016330896 | 失去網際網路連線。 請重設您的連線。 | 是 |
| 2016330895 | 失去網際網路連線。 請重設您的連線。 | 是 |
| 2016330894 | 失去網際網路連線。 請重設您的連線。 | 是 |
| 2016330893 | 失去網際網路連線。 請重設您的連線。 | 是|
| 2016330892 | 已停用國際漫遊。 | 否|
| 2016330891 | 通話進行時，無法存取此裝置的行動電話通訊資料連線。 請等候通話完成。 | 是|
| 2016330890 | 此裝置的行動電話通訊網路。 此時無法使用這些裝置。 | 否|
| 2016330889 | 安全連線失敗。 請重設您的連線。 | 是|
| 2016330888 | 伺服器信任評估失敗。 | 否|

## <a name="next-steps"></a>接下來的步驟

- 選取 [裝置動作] 以查看同步處理動作的狀態。 
