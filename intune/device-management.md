---
title: "使用 Intune 管理裝置"
titleSuffix: Intune on Azure
description: "了解如何使用 Intune 查看您管理的裝置，以及對這些裝置執行各種動作。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 07/05/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 8f066e62e323fffb7c6954d83b2b55ee63f4be46
ms.sourcegitcommit: fd5b7aa26446d2fa92c21638cb29371e43fe169f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2017
---
# <a name="what-is-microsoft-intune-device-management"></a>什麼是 Microsoft Intune 裝置管理？


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

**裝置**工作負載可讓您深入了解您所管理的裝置，並讓您從遠端對這些裝置執行工作。 若要存取工作負載︰

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗中，選擇 [裝置]。

現在，您可以執行下列動作：

- [檢視裝置清查](device-inventory.md)
- 執行遠端裝置動作：
    - [移除公司資料](device-company-data-remove.md) 
    - [重設為原廠設定](device-factory-reset.md)
    - [遠端鎖定](device-remote-lock.md)
    - [重設密碼](device-passcode-reset.md)
    - [略過啟用鎖定](device-activation-lock-bypass.md)
    - [全新開始](device-fresh-start.md)
    - [遺失模式](device-lost-mode.md)
    - [尋找裝置](device-locate.md)
    - [重新啟動](device-restart.md)
    - [重設 Windows 10 的 PIN 碼](device-windows-pin-reset.md)
    - [Android 裝置的遠端控制](device-profile-android-teamviewer.md)


## <a name="support-for-each-device-action"></a>支援每個裝置的動作

請使用下表了解每個動作支援的裝置平台。

|||||||
|-|-|-|-|-|-|
|裝置動作|訊息|Windows Phone|iOS|macOS|Android|
|**移除公司資料**|是|是|是|是|是|
|**重設為原廠設定**|Windows 8.1 和更新版本 (非 EAS 管理裝置)|是|是|否|不支援 Android for Work|
|**刪除**|是|是|是|是|是|
|**遠端鎖定**|否|Windows Phone 8.1 和更新版本|是|否|是|
|**重設密碼**|否|Windows Phone 8.1 至未聯結 Azure AD 的 Windows 10 Creators Update、Windows 10 Creators Update 及更新版本 - 全部|是|否|不支援 Android 7 以前的 Android for Work|
|**新密碼** (適用於 Windows 10 裝置)|否|Windows 10 Creators Update 和更新版本 (已聯結 Azure AD)|否|否|不支援 Android for Work|
|**略過啟用鎖定**|否|否|僅限公司擁有的裝置|否|否|
|**遺失模式**|否|否|受監督且為公司擁有的 iOS 9.3 和更新版本|否|否|
|**尋找裝置**|否|否|受監督且為公司擁有的 iOS 9.3 和更新版本遺失模式|否|否|
|**登出目前的使用者**|否|否|iOS 9.3 和更新版本 (僅限共用的 iPad 裝置)|否|否|
|**重新啟動**|Windows 8.1 及更新版本|Windows Phone 8.1 和更新版本|否|否|否|
|**全新開始**|Windows 10 Creators Update 和更新版本|否|否|否|否|
|**新的遠端協助工作階段**|否|否|否|否|是|
|**移除使用者**|否|否|iOS 9.3 和更新版本 (僅限共用的 iPad 裝置)|否|否|

## <a name="next-steps"></a>後續步驟

- 選擇 [裝置動作] 查看您管理的裝置上所執行動作的狀態。 
![監視裝置動作](./media/monitor-device-actions.png)