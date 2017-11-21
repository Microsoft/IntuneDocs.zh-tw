---
title: "使用 Intune 重設及移除裝置密碼"
titlesuffix: Azure portal
description: "了解如何在使用 Intune 管理的裝置上重設及移除密碼。"
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 11/06/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: dfa94d11f978bbe4d23b6672423c849e1f061986
ms.sourcegitcommit: 474a24ba67f6bf4f00268bf9e4eba52331a6b82d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="reset-and-remove-the-passcode-on-intune-managed-devices"></a>在 Intune 管理的裝置上重設及移除密碼


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

本文會交換使用「移除」和「重設」二詞。

[移除密碼] 動作會為裝置產生新的密碼，新密碼會顯示在 [<裝置名稱> 概觀] 刀鋒視窗上。

## <a name="supported-platforms"></a>支援的平台

- Windows - 不支援
- Windows Phone - 支援 Windows Phone 8.1 至未加入 Azure AD 的 Windows 10 Creators Update、Windows 10 Creators Update 和更新版本
- iOS - 支援
- macOS - 不支援
- Android - 支援 Android 7 之前的 Android 版本。 不支援 Android for Work。

## <a name="how-to-reset-a-passcode"></a>如何重設密碼

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。
4. 在 [裝置和群組] 刀鋒視窗中選擇 [所有裝置]。
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [移除密碼] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。
