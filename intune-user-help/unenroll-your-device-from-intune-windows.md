---
title: 從 Intune 移除 Windows 裝置 | Microsoft Docs
description: 描述如何從 Intune 移除 Windows 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 89a69f7d5cda31658cc9faf068a2a37698fdd93c
ms.sourcegitcommit: 4c06fa8e9932575e546ef2e880d96e96a0618673
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="remove-your-windows-device-from-intune"></a>從 Intune 移除 Windows 裝置

如果您的裝置已向 Intune 註冊，但您已不想再使用 Windows 裝置來存取工作或學校電子郵件、應用程式或其他資源，就必須將該裝置自管理中移除。 從 Intune 移除您的裝置之後，您將不再能夠存取這些資源。 如需有關將裝置自管理中移除時所發生情況的詳細資訊，請參閱[如果將裝置從 Intune 取消註冊，會發生什麼情況？](what-happens-if-you-unenroll-your-device-from-intune-windows.md)。

## <a name="remove-your-windows-10-device"></a>移除 Windows 10 裝置

1.  如需取得 App 清單，請點選 [公司入口網站]  App。

2.  使用工作或學校認證登入。

3.  在 [我的裝置] 中，選取要取消註冊的裝置。

4.  點選 [移除] &gt; [移除]。

## <a name="remove-your-windows-81-computer"></a>移除 Windows 8.1 電腦

1.  移至 [電腦設定] &gt; [網路] &gt; [工作場所]。

2.  選取 [工作場所聯結] 下的 [離開]。

3.  選取 **「Turn on device management」** \(開啟裝置管理) 下的 **[關閉]**。

4.  在開啟的快顯視窗上，選取 [關閉]。

## <a name="remove-your-windows-phone-81-mobile-device"></a>移除 Windows Phone 8.1 行動裝置

1.  移至 [設定] &gt; [工作場所]。

2.  點選您要取消註冊的工作場所帳戶。

3.  點選畫面底部的 [刪除]。

4.  在 [刪除帳戶] 對話方塊上，點選 [刪除]。

## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>在移除公司入口網站之後移除您的個人資訊

公司入口網站會將兩種資料儲存在您的 Windows 裝置上：

-   **診斷記錄**：解除安裝公司入口網站應用程式時，會自動清除 Microsoft 所收集的標準應用程式活動資料，例如應用程式已開啟多久或是否當機。
-   **應用程式快取**：儲存應用程式運作所需的特定支援檔案，例如圖示和設定。

以下是一些您必須執行才能完全刪除此資訊的步驟。

### <a name="uninstall-the-company-portal"></a>將公司入口網站解除安裝  

[將公司入口網站應用程式解除安裝](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs)會將儲存在您裝置上的一些應用程式資料移除。  

### <a name="reset-the-company-portal"></a>重設公司入口網站

您可以透過在 [設定] 中重設公司入口網站應用程式，來重設此入口網站的其餘應用程式資料。 請開啟 [設定] > [應用程式與功能] > [公司入口網站] > [進階選項] > [重設]。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
