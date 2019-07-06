---
title: 手動同步您的 Windows 裝置 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
searchScope:
- User help
ROBOTS: ''
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 328ec3111aae5f8363f2743d423a56eafc47d765
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67546259"
---
# <a name="sync-your-windows-device-manually"></a>手動同步處理您的 Windows 裝置

當應用程式安裝的速度小於理想速度時，您可以起始手動裝置同步處理。手動同步處理會強制您的裝置與 Intune 連線，以獲得最新的更新和通訊。 裝置同步處理完成之後，安裝速度可能會提升。

Intune 支援從公司入口網站應用程式、桌面工作列或 [開始] 功能表以及從裝置的 [設定] 應用程式手動同步處理。 執行 Creators Update (1703) 或更新版本的 Windows 10 裝置支援公司入口網站應用程式功能。 

所有 Windows 裝置都可從裝置的「設定」應用程式進行同步處理，包括：

* [Windows 10 Desktop](#windows-10-desktop)  
* [Microsoft HoloLens](#microsoft-hololens)   
* [Windows 10 Mobile](#windows-10-mobile)  
* [Windows Phone 8.1](#windows-phone-81)    

## <a name="sync-directly-from-company-portal-app-for-windows"></a>直接從 Windows 版公司入口網站應用程式進行同步
完成這些步驟以手動同步處理執行 Creators Update (1703 版) 或更新版本的任何 Windows 10 裝置。

1. 在您的裝置上開啟「公司入口網站」應用程式。

2. 選取 [設定]   > [同步處理]  。

    ![公司入口網站應用程式的首頁螢幕擷取畫面，已反白顯示 [設定]](./media/RS1_homePage_settings_04.png)  
    
    ![公司入口網站應用程式的設定頁面螢幕擷取畫面，已反白顯示 [同步處理] 按鈕](./media/RS1_settingspage_sync05.png)  

## <a name="sync-from-device-taskbar-or-start-menu"></a>從裝置工作列或 [開始] 功能表同步   

您也可以從您裝置的桌面存取應用程式外部的同步控制項。 如果您直接將應用程式釘選到工作列或 [開始] 功能表，而且想要快速同步，則這種方式十分有用。  

1. 在工作列或 [開始] 功能表中找到公司入口網站應用程式圖示。  
2. 以滑鼠右鍵按一下應用程式的圖示，以顯示其功能表 (也稱為捷徑清單)。  

    ![裝置桌面上之 Windows 工作列的螢幕擷取畫面。 已按一下公司入口網站應用程式圖示，以顯示含有 [釘選到工作列]、[關閉視窗] 和 [同步此裝置] 動作選項的功能表。](./media/sync-device-from-start-menu-1807.png)  

3. 選取 [同步此裝置]  。 公司入口網站應用程式會開啟至 [設定]  頁面並起始您的同步。  

## <a name="sync-from-settings-app"></a>從「設定」應用程式進行同步處理 
完成這些步驟以手動從「設定」應用程式同步處理 Microsoft HoloLens、Windows 10 Desktop、Windows 10 行動裝置版或 Windows Phone 8.1 裝置。  

### <a name="windows-10-desktop"></a>Windows 10 Desktop
1. 在您的裝置上選取 [開始]   > [設定]  。

2. 選取 [帳戶]  。

    ![選擇 [設定] 頁面上的帳戶](./media/win10pc-sync-2-settings-accounts.png)  

3. 適用於桌上型電腦的 Windows 10 有多個版本。 請比較您的畫面與下列螢幕擷取畫面，以判斷要遵循哪一組步驟。 

    * 如果您的畫面顯示 [存取公司或學校資源]  ，請跳至 [[存取公司或學校資源]](#access-work-or-school-steps) 中的步驟。

    ![設定應用程式中的 [存取公司或學校資源] 選項](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

    * 如果您的畫面顯示 [公司存取]  ，請跳至 [[公司存取]](#work-access-steps) 底下的步驟。  

    ![選擇 [公司存取] 作為帳戶類型](./media/win10pc-sync-3-work-access.png)

#### <a name="access-work-or-school-steps"></a>存取公司或學校資源

1. 按一下 [存取公司或學校資源]  。

    ![顯示 [存取公司或學校資源] 選項的螢幕擷取畫面](./media/w10-enroll-rs1-connect-to-work-or-school.png)  

2. 選取旁邊有公事包圖示的帳戶。 如果您完全沒有看到此類帳戶，您的公司可能是以其他方式設定您的設定。 請改為按一下旁邊有 Microsoft 標誌的帳戶。

     ![選擇公事包或 Microsoft 標誌旁邊的帳戶名稱](./media/win10pc-rs1-sync-info-button.png)

3. 按一下 [資訊]  。 

4. 按一下 [同步處理]  。 

#### <a name="work-access-steps"></a>公司存取步驟

1. 按一下 [公司存取]  。

    ![選擇 [公司存取] 作為帳戶類型](./media/win10pc-sync-3-work-access.png)

2. 在 [註冊裝置管理]  下方，選取您的公司名稱。

    ![選擇用於裝置管理的公司名稱](./media/win10pc-sync-4-tap-com-name.png)

3. 按一下 [同步處理]  。按鈕會保持停用狀態，直到同步處理完成為止。

    ![選擇 [同步] 按鈕](./media/win10pc-sync-5-tap-sync.png)  


### <a name="windows-10-mobile"></a>Windows 10 Mobile

   1. 在您的裝置上，移至 [所有應用程式]   > [設定]   > [帳戶]  。

       ![選擇 [設定] 畫面上的帳戶](./media/win10m-sync-1-settings-accounts.png)

   2. 選取 [公司存取]  。

       ![選擇 [公司存取] 作為帳戶類型](./media/win10m-sync-2-work-access.png)

   3. 在 [註冊裝置管理]  下方，選取您的公司名稱。

       ![選擇用於裝置管理的公司名稱](./media/win10m-sync-3-tap-comp-name.png)

   4. 選取**同步處理**圖示。 按鈕會保持停用狀態，直到同步處理完成為止。

       ![選擇同步圖示](./media/win10m-sync-4-tap-sync.png)  
### <a name="microsoft-hololens"></a>Microsoft HoloLens  
這些指示適用於執行 Windows 10 年度更新版 (也稱為 RS1) 的 HoloLens 裝置。 
1. 在您的裝置上開啟 [設定] 應用程式。  

2. 選取 [帳戶]   > [公司存取]  。  
    ![HoloLens 設定應用程式的螢幕擷取畫面，已反白顯示帳戶連結](./media/RS1_holoLens_SettingsRS1_Accounts_06.png)  

3. 選取您的已連線帳戶 > [同步處理]  。![HoloLens 設定應用程式的螢幕擷取畫面，已反白顯示同步處理按鈕](./media/RS1_holoLens_SyncRS1_Sync_08.png)  

### <a name="windows-phone-81"></a>Windows Phone 8.1

1. 移至 [所有應用程式]   > [設定]   > [工作場所]  。

    ![設定清單](./media/wp81-1-sync-settings-workplace.png)

2. 選取您的公司名稱。

    ![選擇工作場所帳戶的公司名稱](./media/wp81-2-sync-tap-compname.png)

3. 選取**同步處理**圖示。

    ![選擇同步圖示](./media/wp81-3-sync-tap-sync-button.png)

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。
