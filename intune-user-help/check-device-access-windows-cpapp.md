---
title: 檢查裝置存取 | Microsoft Docs
description: 檢查裝置存取，以了解您的裝置是否符合需求，且能夠存取公司或學校資源。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/05/2018
ms.topic: article
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 49075fd750ade6aaa412d551f4177822b52ce7f2
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490096"
---
# <a name="check-access-from-company-portal-app-for-windows"></a>從 Windows 公司入口網站應用程式來檢查存取

確認您的裝置能存取公司或學校資源。 

組織會強制執行需求&ndash;例如加密和密碼限制&ndash;以確定只有受信任的安全裝置能存取其資料。 受控裝置必須符合並維護這些需求，才能存取組織的資源。

[檢查存取]  動作會評估您的裝置設定和其存取狀態。 [裝置詳細資料]  頁面會列出您需要調整以重獲存取權的設定。 

請完成本文中的步驟，以從 Windows 版公司入口網站應用程式檢查存取權。  

## <a name="check-access-from-device-details-page"></a>從 [裝置詳細資料] 頁面檢查存取權  
1. 開啟 Windows 版公司入口網站應用程式，並移至 [我的裝置]  。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，其中醒目提示 [首頁] 頁面的 [我的裝置] 區段。](./media/1809_CheckAccess_Context_Select_Device.png)  
2. 選取一個裝置。  
3. 在 [裝置詳細資料]  頁面上，選取 [檢查存取權]  。 應用程式會同步處理您的裝置與組織目前需求，並檢查以確定您的裝置符合需求。 這可能需要幾分鐘的時間。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示 [檢查存取權] 按鈕。](./media/1809_CheckAccess_Checking_Status.png) 

4. 查看狀態更新。 它會顯示您的裝置**可以存取您組織的資源**或是**無法存取您的組織資源**。  

   ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示 [狀態] 區段。](./media/1809_CheckAccess_Device_details_status1.png)  
   
5. 如果您的裝置無法存取資源，請移至頁面頂端的警示。 按一下 [更多]  展開其詳細資料。 按一下 [較少]  摺疊它們。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示頁面頂端的警示。](./media/1809_CheckAccess_Device_details_alert1.png)  

6. 適用時，訊息會顯示其他說明連結和修復動作。 選取這些選項的一或多個，立即開始進行疑難排解。 解決、同步和連絡動作&ndash;如下所述&ndash;只有在受影響的裝置上使用公司入口網站時才會顯示。  

     * **如何解決此問題**會開啟相關的說明文章，如果有的話。  
     * **解決**會將您重新導向至裝置上的設定。  
     * **同步處理**會評估您的裝置，確定它符合您組織的需求。  
     * **連絡 IT** 會將您重新導向至您 IT 小組的連絡資訊。   
 
6. 更新設定之後，請按一下 [檢查存取權]  ，確認您的裝置狀態。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示 [狀態] 區段。](./media/1809_CheckAccess_Device_details_status1.png)  

## <a name="check-access-from-device-context-menu"></a>從裝置操作功能表檢查存取權  
1. 開啟 Windows 版公司入口網站應用程式，並移至 [我的裝置]  。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，其中醒目提示 [首頁] 頁面的 [我的裝置] 區段。](./media/1809_CheckAccess_Context_Select_Device.png)  

2. 按一下滑鼠右鍵，或按住裝置，開啟其[操作功能表](https://docs.microsoft.com//windows/uwp/design/controls-and-patterns/menus)。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，首頁。 裝置操作功能表會顯示頁面的 [我的裝置]**** 區段，並顯示 [重新命名]、[移除] 和 [檢查存取權] 等動作。](./media/1809_DeviceContextMenu_Windows_CP.png)  
3. 選取 [檢查存取權]  。 應用程式會同步處理您的裝置與組織目前的需求，並檢查以確定您的裝置符合。 這可能需要幾分鐘的時間。  
 
4. 在裝置下會出現一則訊息，讓您知道裝置**可以存取公司資源**或是**無法存取公司資源**。 

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示 [狀態] 區段。](./media/1809_CheckAccess_Context_Menu_Alert2.png) 

5. 如果您的裝置無法存取資源，請選取裝置。  
6. 在 [裝置詳細資料]  頁面上，前往頁面頂端的警示。 按一下 [更多]  展開其詳細資料。 按一下 [較少]  摺疊它們。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示頁面頂端的警示。](./media/1809_CheckAccess_Device_details_alert1.png)  

6. 適用時，訊息會顯示其他說明連結和修復動作。 選取這些選項的一或多個，立即開始進行疑難排解。 解決、同步和連絡動作&ndash;如下所述&ndash;只有在受影響的裝置上使用公司入口網站時才會顯示。  

     * **如何解決此問題**會開啟相關的說明文章，如果有的話。  
     * **解決**會將您重新導向至裝置上的設定。  
     * **同步處理**會評估您的裝置，確定它符合您組織的需求。  
     * **連絡 IT** 會將您重新導向至您 IT 小組的連絡資訊。    

7. 更新設定之後，請按一下頁面底部的 [檢查存取權]  。  

    ![Windows 版公司入口網站應用程式的範例螢幕擷取畫面，[裝置詳細資料] 頁面，醒目提示 [檢查存取權] 動作。](./media/1809_CheckAccess_Device_details_button.png) 


需要其他協助？ 如需公司支援人員的連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
