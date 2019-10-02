---
title: 使用 Microsoft Intune 從 iOS 裝置移除使用者
titleSuffix: ''
description: 了解如何使用 Intune 從共用的 iOS 裝置中移除使用者。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f418149d8640f7fd663f0bbf4b3151ffb428a75e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728477"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>從共用的 iOS 裝置中移除使用者


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[移除使用者]  動作會刪除您從共用 iPad 裝置本機快取中選取的使用者。 iPad 裝置必須使用 [iOS 教育設定檔](../fundamentals/education-settings-configure-ios.md)設定，來管理 iOS Classroom 應用程式。 

## <a name="supported-platforms"></a>支援的平台

- Windows - 不支援
- Windows Phone - 不支援
- iOS - 支援 iOS 9.3 和更新版本 (僅限共用的 iPad 裝置)
- macOS - 不支援
- Android - 不支援

## <a name="remove-a-user"></a>移除使用者

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
3. 在 [Intune]  窗格中，選取 [裝置]  。
4. 在 [裝置]  窗格中，選取 [所有裝置]  。
5. 在您管理的裝置清單中選取 iOS 裝置。
6. 在裝置的窗格中選取 [使用者]  。
7. 在清單中，以滑鼠右鍵按一下您想要移除的使用者，然後選取 [移除使用者]  。

## <a name="next-steps"></a>後續步驟

- 若要查看 [移除使用者]  動作的狀態，請選取 [裝置]   > [裝置動作]  。
