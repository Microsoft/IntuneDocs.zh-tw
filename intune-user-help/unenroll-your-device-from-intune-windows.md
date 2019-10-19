---
title: 從 Intune 管理移除您的 Windows 裝置
description: 描述如何從 Intune 管理移除 Windows 裝置
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/03/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 018bda65-7238-41f5-b92a-e5f67b7fe085
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: e64911ea9b1b1d3c619a82eac9dc78e4e78a53e9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508137"
---
# <a name="remove-your-windows-device-from-management"></a>從管理移除您的 Windows 裝置

當您不再想要或不需要進行下列動作時，請從管理移除註冊的 Windows 裝置：  
* 使用您的公司或學校裝置。 
* 存取公司或學校電子郵件、應用程式或其他資源。

取消註冊裝置之後，您將會遺失學校或公司資源的裝置存取權。 您可以從管理移除下列 Windows 裝置。  
* Windows 10 裝置 
* Windows 8.1 電腦
* Windows 8.1 手機
 
如需將裝置從管理移除時所發生情況的詳細資訊，請參閱[如果將裝置從 Intune 移除，會發生什麼情況](what-happens-if-you-unenroll-your-device-from-intune-windows.md)。  

## <a name="remove-your-windows-10-device"></a>移除 Windows 10 裝置
完成下列步驟，以從管理移除 Windows 10 裝置。

### <a name="remove-in-company-portal-app-home-page"></a>在公司入口網站應用程式中的 [首頁]  頁面移除  

1. 開啟公司入口網站應用程式。
2. 在 [首頁]  上，移至 [我的裝置]  區段。
3. 選取您要移除的裝置。
3. 在應用程式的右上角，選取 [查看更多]  圖示。
4. 選取 [移除]  。 
5. 若要確認裝置移除，請選取 [移除]  。  

### <a name="remove-in-company-portal-app-device-context-menu"></a>在公司入口網站應用程式中的裝置操作功能表移除  

1. 開啟公司入口網站應用程式，並移至 [我的裝置]  。

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，其中醒目提示 [首頁] 頁面的 [我的裝置] 區段。](./media/1809_CheckAccess_Context_Select_Device.png)

2. 按一下滑鼠右鍵，或按住裝置，開啟其[操作功能表](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)。  

3. 選取 [移除]  。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，首頁。 裝置操作功能表會顯示頁面的 [我的裝置]**** 區段，並顯示 [重新命名]、[移除] 和 [檢查存取權] 等動作。](./media/1809_DeviceContextMenu_Windows_CP.png)  

5. 在確認中，按一下 [深入了解]  閱讀您的公司和學校資源存取權可能會有什麼變更。 若要確認裝置移除，請選取 [移除]  。   

     ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，首頁。 [重新命名] 欄位會出現在裝置上，使用者可以在其中輸入新名稱，然後按一下 [重新命名] 或 [取消]。](./media/1808_RemoveDevice_Popup.png)  


### <a name="remove-in-device-settings-app"></a>在裝置 [設定] 應用程式中移除
1. 開啟 [設定] 應用程式。 
2. 移至 [帳戶]   > [存取公司或學校資源]  。
3. 選取您想要移除的連接的帳戶 > [中斷連線]  。
4. 若要確認裝置移除，請選取 [是]  。

## <a name="remove-your-windows-81-computer"></a>移除 Windows 8.1 電腦
完成下列步驟，以從 Intune 中移除 Windows 8.1 的電腦。

1. 移至 [電腦設定]   > [網路]   > [工作場所]  。
2. 選取 [工作場所聯結]  下的 [離開]  。
3. 選取 **「Turn on device management」** \(開啟裝置管理) 下的 **[關閉]** 。
4. 在開啟的快顯視窗上，選取 [關閉]  。

## <a name="remove-your-windows-81-phone"></a>移除 Windows 8.1 手機
完成下列步驟，以從 Intune 移除 Windows 8.1 手機。

1. 移至 [設定]   > [工作區]  。
2. 點選您要取消註冊的工作場所帳戶。
3. 點選畫面底部的 [刪除]  。
4. 在 [刪除帳戶]  對話方塊上，點選 [刪除]  。  
## <a name="removing-your-personal-information-after-removing-the-company-portal"></a>在移除公司入口網站之後移除您的個人資訊  

公司入口網站會將兩種資料儲存在您的 Windows 裝置上：

- **診斷記錄檔**：Microsoft 收集的標準應用程式活動資料。 這會在您解除安裝公司入口網站應用程式時自動清除。 例如，應用程式活動資料是關於應用程式開啟或應用程式當機時間長度的資料。
- **應用程式快取**：應用程式運作所需的特定支援檔案，例如圖示和設定。

若要刪除已儲存的記錄檔和快取，請完成下列其中一個步驟：

* [解除安裝公司入口網站應用程式](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* 重設公司入口網站應用程式。 開啟 [設定]  應用程式，然後選取 > [應用程式]   > [公司入口網站]   > [進階選項]   > [重設]  。 

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
