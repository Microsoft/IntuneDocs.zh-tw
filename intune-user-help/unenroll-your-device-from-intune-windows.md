---
title: 從 Intune 移除 Windows 裝置
description: 描述如何從 Intune 移除 Windows 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 05/08/2018
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
ms.openlocfilehash: 1dd64250c1996c6b13c62f80572282d639112ba6
ms.sourcegitcommit: 8ee543c864097dc195b6f440471dca713fc21ed2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2018
---
# <a name="remove-your-windows-device-from-intune-management"></a>從 Intune 管理移除您的 Windows 裝置

當您不再想要或不需要進行下列動作時，請從 Intune 移除註冊的 Windows 裝置：  
* 使用您的公司或學校裝置。 
* 存取公司或學校電子郵件、應用程式或其他資源。

移除之後，您將無法從該裝置存取學校或公司資源。 可以從 Intune 移除的 Windows 裝置包括：  
* Windows 10 裝置 
* Windows 8.1 電腦
* Windows 8.1 行動裝置
 
如需有關將裝置自 Intune 管理中移除時所發生情況的詳細資訊，請參閱[如果將裝置從 Intune 移除，會發生什麼情況](what-happens-if-you-unenroll-your-device-from-intune-windows.md)。

## <a name="remove-your-windows-10-device"></a>移除 Windows 10 裝置
完成下列步驟，以從 Intune 移除 Windows 10 裝置。

### <a name="via-the-company-portal-app"></a>透過公司入口網站應用程式

1. 開啟公司入口網站應用程式。
2. 使用工作或學校認證登入。
3. 在 [我的裝置] 中，選取要移除的裝置。
4. 在應用程式的右上角，選取 [查看更多] 圖示。
5. 選取 [移除]。 
6. 若要確認裝置移除，請選取 [移除裝置]。

### <a name="via-device-settings-app"></a>透過裝置設定應用程式
1. 開啟 [設定] 應用程式。 
2. 移至 [帳戶] > [存取公司或學校資源]。
3. 選取您想要移除的連接的帳戶 > [中斷連線]。
4. 若要確認裝置移除，請選取 [是]。

## <a name="remove-your-windows-81-computer"></a>移除 Windows 8.1 電腦
完成下列步驟，以從 Intune 中移除 Windows 8.1 的電腦。

1.  移至 [電腦設定] > [網路] > [工作場所]。
2.  選取 [工作場所聯結] 下的 [離開]。
3.  選取 **「Turn on device management」** \(開啟裝置管理) 下的 **[關閉]**。
4.  在開啟的快顯視窗上，選取 [關閉]。

## <a name="remove-your-windows-81-mobile-device"></a>移除 Windows 8.1 行動裝置
完成下列步驟，以從 Intune 中移除 Windows 8.1 行動裝置。

1.  移至 [設定] > [工作區]。
2.  點選您要取消註冊的工作場所帳戶。
3.  點選畫面底部的 [刪除]。
4.  在 [刪除帳戶] 對話方塊上，點選 [刪除]。  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>在移除公司入口網站之後移除您的個人資訊
公司入口網站會將兩種資料儲存在您的 Windows 裝置上：

-   **診斷記錄**：當您從公司入口網站移除裝置時，會自動清除 Microsoft 所收集的標準應用程式活動資料。 例如，應用程式活動資料是關於應用程式開啟或應用程式當機時間長度的資料。
-   **應用程式快取**：應用程式運作所需的特定支援檔案，例如圖示和設定。

以下是一些您必須執行才能完全刪除此資訊的步驟。

1. 將公司入口網站解除安裝。 [將公司入口網站應用程式解除安裝](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs)會將儲存在您裝置上的一些應用程式資料移除。  

2. 重設公司入口網站以重設預存的應用程式資料。 開啟 [設定] 應用程式，然後選取 > [應用程式] > [公司入口網站] > [進階選項] > [重設]。 

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。