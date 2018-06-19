---
title: 如何從 Intune 移除 Android 裝置 | Microsoft Docs
description: 描述從 Intune 取消註冊 Android 裝置的方式
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018357"
---
# <a name="how-to-remove-your-android-device-from-intune"></a>如何從 Intune 移除 Android 裝置

當您從 Intune 移除 Android 裝置時，該裝置即無法再存取公司資源。  如需有關將裝置自管理中移除時所發生情況的詳細資訊，請參閱[如果將裝置從 Intune 取消註冊，會發生什麼情況？](what-happens-if-you-unenroll-your-device-from-intune-android.md)

## <a name="removing-the-device-from-the-company-portal-app"></a>從公司入口網站應用程式移除裝置

若要從 Intune 和公司入口網站應用程式移除裝置，請依照下列步驟：

1. 點選公司入口網站應用程式右上角的三個垂直點，開啟 [動作功能表]。

   ![Android 公司入口網站應用程式的影像，右上角是開啟的動作功能表。 新的 [移除公司入口網站] 選項是第三個選項，位於 [我的設定檔] 和 [設定] 底下，在 [條款及條件]、[說明與意見反應] 和 [關於] 之上。](./media/android_remove_cp_menu_action_after_1705.png)

2. 點選 [移除公司入口網站]。

3. 確認將會出現，詢問您是否確定要移除公司入口網站。 它會提供有關當您取消註冊裝置時，會發生什麼情況的一些資訊。 閱讀此訊息後，點選 [確定] 來移除應用程式。

   ![確認對話方塊的影像，從動作功能表選取新的 [移除公司入口網站] 選項後就會顯示。 此對話方塊會告知使用者「若移除公司入口網站，您的裝置將不再受公司支援人員，並可能移除對公司資料、公司應用程式及公司電子郵件的存取權。」 然後，它會要求使用者選取 [是] 以確認要移除公司入口網站應用程式。](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>移除公司入口網站應用程式所收集的資料

移除 Android 版公司入口網站應用程式在您裝置上安裝的所有資料：

-   清除應用程式資料，方法是在 [應用程式] 中 -> 按一下應用程式 -> 按一下 [清除資料] 按鈕
-   刪除 '\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal' 資料夾

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
