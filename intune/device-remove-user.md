---
title: "使用 Intune 從 iOS 裝置移除使用者"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 從共用的 iOS 裝置中移除使用者。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 00f5898d0f2cc167a66026dd108d6bbd54c39cec
ms.sourcegitcommit: ee7f69efe9f32a1d6bdeb1fab73d03dbfe1ae58c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2017
---
# <a name="remove-a-user-from-a-shared-ios-device-with-intune"></a>使用 Intune 從共用的 iOS 裝置中移除使用者


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[移除使用者] 動作會在已使用 [iOS 教育設定檔](education-settings-configure-ios.md)進行設定，以管理 iOS Classroom 應用程式的共用 iPad 裝置上，將您選擇的使用者從本機快取中刪除。 

## <a name="supported-platforms"></a>支援的平台

- Windows - 不支援
- Windows Phone - 不支援
- iOS - 支援 iOS 9.3 和更新版本 (僅限共用的 iPad 裝置)
- macOS - 不支援
- Android - 不支援

## <a name="how-to-remove-a-user"></a>如何移除使用者

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置] 刀鋒視窗中，選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇 iOS 裝置。
6. 在該裝置的刀鋒視窗中，選擇 [使用者]。
7. 從清單中，以滑鼠右鍵按一下您想要移除的使用者，然後選擇 [移除使用者]。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。
