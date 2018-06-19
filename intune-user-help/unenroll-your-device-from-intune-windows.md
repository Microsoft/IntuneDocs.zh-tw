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
ms.openlocfilehash: a3cad6a73b3455790441c594933d599b2c6e89f9
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224427"
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

-   **診斷記錄檔**：Microsoft 收集的標準應用程式活動資料。 這會在您解除安裝公司入口網站應用程式時自動清除。 例如，應用程式活動資料是關於應用程式開啟或應用程式當機時間長度的資料。
-   **應用程式快取**：應用程式運作所需的特定支援檔案，例如圖示和設定。

若要刪除已儲存的記錄檔和快取，請完成下列其中一個步驟：

* [解除安裝公司入口網站應用程式](https://support.microsoft.com/help/4028003/windows-10-uninstall-apps-and-programs) 

* 重設公司入口網站應用程式。 開啟 [設定] 應用程式，然後選取 > [應用程式] > [公司入口網站] > [進階選項] > [重設]。 

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
