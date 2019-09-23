---
title: 如何從公司入口網站重設密碼 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 690fb81350c0c264677c6c75b8942e9cdcd4e8f0
ms.sourcegitcommit: c19584b36448bbd4c8638d7cab552fe9b3eb3408
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2019
ms.locfileid: "71163368"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>如何從公司入口網站重設裝置密碼

如果您遺失裝置 PIN 或密碼，您可以使用[公司入口網站](https://portal.manage.microsoft.com)重設。 

公司註冊的裝置可能不會顯示 [重設密碼] 選項。 在此情況下，請洽詢您公司的支援人員，讓它為您重設。  

執行 Android 7.0 和更新版本的裝置無法使用密碼重設。 如果您忘記其中一個裝置上的密碼，您必須將它重設為原廠設定。  

## <a name="reset-your-passcode"></a>重設密碼

1. 開啟[公司入口網站](https://portal.manage.microsoft.com)，然後選取 [功能表]  按鈕 > [裝置]  。  

2. 選取需要重設密碼的裝置。  

    ![[裝置] 頁面的螢幕擷取畫面，含有兩個磚顯示無法辨識且以常用名稱命名的裝置。 灰色的橫幅位於裝置正下方，並提示使用者識別他們正在使用裝置，或是新增一部新的裝置。](./media/rename-reset-device-step2-1808.png) 

3. 選取 [重設密碼]  。 如果頁面頂端未顯示密碼選項，請選取 [其他 (...)]   > [重設密碼]  。   

   ![公司入口網站上所選裝置的裝置詳細資料頁面，頂端含有連結清單，顯示 [重新命名]、[移除]、[重設裝置]、[重設密碼] 及 [遠端鎖定]。 ](./media/rename-reset-device-1808.png)   

    ![[其他] 圖示的螢幕擷取畫面，該圖示以紅色箭頭醒目提示。](./media/rename-reset-device-step3-more-1808.png)  

4. 出現提示時，按一下 [登出]  。於再次出現提示時，重新登入。 您必須在五分鐘內重新登入公司入口網站，否則公司入口網站將不會重設裝置密碼。  

   > [!NOTE]
   > 您必須重新登入來確認身分識別。 這可防止惡意嘗試重設您的裝置密碼。

   ![顯示登出公司入口網站提示的範例螢幕擷取畫面。 使用者輸入的按鈕為 [登出] 和 [取消]。](./media/iwp-reset-passcode-popup-1808.png)

5. 訊息將隨後出現，警告您即將移除現有的裝置密碼。 按一下 [重設密碼]  確認。  
    > [!WARNING]
    > 重設密碼之後，任何能夠實際存取裝置的人員將能存取其上的多數個人和公司資訊。 如果您目前沒有裝置，請不要重設密碼。  

   ![顯示第二則重設密碼訊息的範例螢幕擷取畫面。 包含連結以在文件中深入了解有關設定新密碼的資訊，以及用來重設密碼和取消的個別按鈕。](./media/iwp-reset-passcode-popup2-1808.png) 

6. 如果您重設 iOS 裝置的密碼，將會移除其現有的密碼。 針對 Windows 或 Android 裝置，您會收到暫時密碼來解除鎖定裝置並設定新密碼。 

   > [!NOTE]
   > 您可以在公司入口網站的裝置詳細資料頁面下，找到 Windows 和 Android 裝置的暫時密碼。 如需更多特定 OS 密碼說明，請參閱[設定新密碼](reset-your-passcode-cpwebsite.md#set-up-a-new-passcode)一節。  
   
7. 在您的裝置上，移至 [設定]  並變更暫時密碼。 

8. 公司入口網站右上方會出現一個旗標。 按一下以閱讀通知並確認已成功重設密碼。  

## <a name="set-up-a-new-passcode"></a>設定新密碼  

本節說明每個裝置平台的重設密碼及暫時密碼行為。  

**Android**：移除現有的密碼，並建立由字母和數字組成的暫時密碼。

**iOS**：移除現有的密碼，但不建立暫時密碼。 如果您使用 Touch ID 來開啟您的裝置或進行購買，您必須再次設定。  

**Windows 10 行動裝置版**：移除現有的密碼，並建立由字母和數字組成的暫時密碼。 如果已設定 Windows Hello 臉部辨識，此功能仍可於裝置使用。

**Windows Phone 8.1**：移除現有的密碼，並建立由數字組成的暫時密碼。  

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
