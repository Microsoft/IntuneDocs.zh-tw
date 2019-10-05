---
title: 針對 Microsoft Intune 中的軟體更新進行疑難排解 - Azure | Microsoft Docs
description: 解決 Microsoft Intune 的軟體更新問題。
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3deb023a7e3683658139c2319945c7c3aaeb8ee
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2019
ms.locfileid: "71735606"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Microsoft Intune 的軟體更新疑難排解

協助解決 Microsoft Intune 中的軟體更新問題。 若要查看錯誤碼和說明的清單，請前往 [Microsoft Intune 中的軟體更新代理程式錯誤碼](../protect/software-update-agent-error-codes.md)。

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>含有許多已取代更新的 Windows 7 裝置停止向 Intune 回報

Microsoft Intune 用戶端可能會遇到一或多個下列徵兆：

- 裝置突然停止向 Intune 回報。  
- 裝置經歷了高 CPU 使用率。
- 透過 Intune 安裝應用程式時，它們的安裝速度緩慢。
- Microsoft Intune Center 顯示下列錯誤：`An error occurred while updating your computer. Error found: Code 0x800705b4`。
- [Intune 管理主控台] > [群組] > [所有裝置] > [狀態] 顯示：`One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

如果已取代的更新 (這類更新已由其他更新所取代) 並未長時間遭到拒絕，可能就會發生此問題。 在某些處理序 (例如安裝應用程式) 期間，Windows 會循序檢查所有已取代的更新，以便正確對應更新及其後續更新。 如果已取代的更新清單變得太大，則此檢查工作可能因為處理負載和所需的時間而導致高 CPU 使用率。 由於有大量可供 Windows 7 使用的已取代更新，因此，這個問題主要會對 Windows 7 用戶端產生影響。 較新版的作業系統可能沒有這麼多可用的已取代更新，而且可能不容易受到這個問題所影響。

**解決方法**

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 選取 [軟體更新]  。
3. 拒絕所有可能套用至 Windows 7 或受影響用戶端上所安裝之應用程式 (例如 Microsoft Office) 的已取代更新。
4. 重新啟動受影響的用戶端。

如果您執行 Windows 7，請確定已安裝下列更新︰[3050265 適用於 Windows 7 的 Windows Update 用戶端：2015 年 6 月](https://support.microsoft.com/kb/3050265) \(機器翻譯\)。

## <a name="next-steps"></a>後續步驟

取得[來自 Microsoft 的支援說明](get-support.md)或使用[社群論壇](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)。