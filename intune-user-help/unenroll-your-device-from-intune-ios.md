---
title: 從 Intune 移除 iOS 裝置 | Microsoft Docs
description: 描述如何從 Intune 移除 iOS 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28914db1-3e62-45f5-9632-b0d2a808a44d
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2eb47240516737f03c10d1280887fea275c5ed99
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883949"
---
# <a name="remove-your-ios-device-from-intune"></a>從 Intune 移除 iOS 裝置

當您從 Intune 移除 iOS 裝置時，該裝置將無法再存取公司資源，並且將不再受 Intune 管理。


## <a name="removing-the-device-from-my-devices"></a>從我的裝置移除裝置

若要從 Intune 移除您的裝置，請使用下列步驟或觀看這部影片：


1. 在公司入口網站應用程式中，點選 [裝置]  ， 然後選取您要取消註冊的裝置。 如果您只有一部裝置，當您點選 [裝置]  時，會直接移至裝置詳細資料畫面。

2. 點選 [重新命名]  旁邊的省略符號按鈕 > [移除裝置]   > [移除]  。  

    |![公司入口網站應用程式 [裝置] 畫面的螢幕擷取畫面，當中顯示使用者按一下 [移除] 後的選項。 顯示 [移除裝置] 按鈕、[重設成出廠預設值] 按鈕，以及 [取消] 按鈕。](/intune-user-help/media/cp_ios_unenroll_after_1804_001.png)|

    |![公司入口網站應用程式 [裝置] 畫面的螢幕擷取畫面，當中顯示使用者按一下 [移除裝置] 按鈕後的選項。 顯示以紅色醒目提示的 [移除] 按鈕，以及以藍色醒目提示的 [進一步了解] 按鈕和 [取消] 按鈕。](/intune-user-help/media/cp_ios_unenroll_after_1804_002.png)|


    當您從 Intune 取消註冊裝置時，會發生下列情況：

    - 您的裝置將不再顯示於公司入口網站中。

    - 您無法再從公司入口網站安裝應用程式。

    - 您在新增裝置時變更的任何裝置設定 (例如停用相機或需要特定密碼長度) 都將失效。

    - 您可能無法再存取裝置上的某些公司資源，例如檔案共用或內部網站。

    - 您無法再使用裝置上的公司應用程式和公司資料。

    - 您可能無法再使用 Wi-Fi 或虛擬私人網路 (VPN) 連線到公司網路。

    - 移除裝置中的公司電子郵件設定檔。

    - 只有公司入口網站應用程式或網站上不會再顯示為電子郵件設定的裝置。

    - 已將應用程式解除安裝。 將會移除公司應用程式資料。

## <a name="removing-data-collected-by-the-company-portal-app"></a>移除公司入口網站應用程式所收集的資料

公司入口網站會在您裝置上的三個位置儲存本機資料。

- **資訊記錄**：當您從公司入口網站移除裝置時，會自動清除 Microsoft 所收集的標準應用程式活動資料，例如應用程式已開啟多久或是否當機。

- **Apple 分析**：Apple 所收集的標準應用程式當機活動資料。 只有將裝置重設回出廠設定，才能移除此資訊。 這會清除您裝置上的所有個人資訊。 若要這樣做，請開啟 [設定]   > [一般]   > [重設]   > [清除所有內容及設定]  。

- **金鑰鏈結**：裝置會將密碼及其他用來登入的資訊儲存在金鑰鏈結中。 Microsoft 應用程式會在您裝置上 Microsoft 所開發的任何應用程式 (包括 Microsoft Outlook 和 Microsoft Authenticator) 之間共用您的登入資訊。 與 Apple 分析一樣，只有將裝置重設回出廠設定，才能移除此資訊。 這會清除您裝置上的所有個人資訊。 若要這樣做，請開啟 [設定]   > [一般]   > [重設]   > [清除所有內容及設定]  。


是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
