---
title: "使用 Intune 重設裝置密碼"
titlesuffix: Azure portal
description: "了解如何在使用 Intune 管理的裝置上重設密碼。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7a292342000a4f60455aa44202a1bf0493ae66f0
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="reset-the-passcode-on-intune-managed-devices"></a>在 Intune 管理的裝置上重設密碼


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

[重設密碼] 動作會為裝置產生新的密碼，新密碼會顯示在 [<裝置名稱> 概觀] 刀鋒視窗上。

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
5. 從您管理的裝置清單中，選擇裝置，然後選擇 [重設密碼] 裝置遠端動作。

## <a name="next-steps"></a>後續步驟

若要查看您剛採取的動作狀態，請在 [裝置和群組] 刀鋒視窗中，選擇 [裝置動作]。
