---
title: 使用 Microsoft Intune 重設裝置密碼 - Azure | Micrososft Docs
description: 使用您以 Intune 管理或監視之裝置上的移除密碼動作，移除或重設密碼。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4cca5922f036711093469e71489e267af53f05a9
ms.sourcegitcommit: e6319ff186d969da34bd19c9730ba003d6cce353
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2018
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>在 Intune 中重設或移除裝置密碼

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

若要建立新的裝置密碼，請使用 [移除密碼] 動作。

## <a name="supported-platforms"></a>支援的平台

- Windows Phone 8.1 (未加入 Azure Active Directory)，包括最新的 Windows 10 Creators Update
- Windows 10 Creators Update 和更新版本
- iOS
- Android 7 之前的 Android 版本

下列系統不支援這項功能：

- Windows
- macOS
- Android for Work

## <a name="reset-a-passcode"></a>重設密碼

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選取 [所有服務]，篩選 [Intune]，然後選取 [Microsoft Intune]。
3. 選取 [裝置]，然後選取 [所有裝置]。
4. 從您管理的裝置清單中選取裝置，再選擇 [...More] (...其他)。 然後選擇 [Remove passcode] (移除密碼) 裝置遠端動作。

## <a name="next-steps"></a>接下來的步驟

若要查看您剛採取的動作狀態，請在 [裝置] 中選擇 [裝置動作]。
