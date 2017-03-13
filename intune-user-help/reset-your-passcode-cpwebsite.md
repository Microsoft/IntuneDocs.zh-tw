---
title: "如何從公司入口網站重設密碼 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: 
ms.reviewer: mamoriss
ms.suite: ems
ms.custom: intune-enduser
translationtype: Human Translation
ms.sourcegitcommit: f293901d3865f0b10ed876e83b151cf59a046cba
ms.openlocfilehash: 68725bb63ae2750e89a03c16027f8b4fd9111255
ms.lasthandoff: 02/24/2017


---

# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>如何從公司入口網站重設裝置密碼

如果您在 Intune 中註冊的裝置遺失裝置 PIN 或密碼，您可以使用[公司入口網站](http://portal.manage.microsoft.com)重設密碼。 您可以使用公司入口網站來管理已在 Intune 註冊的電腦和裝置，而且就像使用公司入口網站應用程式一樣，可讓您執行大部分同樣的工作。

> [!NOTE]
> 您在公司入口網站上可能不會看到 [重設密碼] 按鈕。 如果沒看到此按鈕，您需要透過公司入口網站連絡 IT 管理員以尋求支援。

若要重設密碼：

1.    在[公司入口網站](http://portal.manage.microsoft.com)上，點選 [功能表] 按鈕![功能表按鈕的小圖像，以平行方式堆疊的三個水平橫條](/Intune/whats-new/media/CP_hamburger_menu.png)，然後選取 [我的裝置]。

2. 在 [我的裝置] 頁面上，選取您想要重設密碼的裝置名稱。

  ![[我的裝置] 頁面的螢幕擷取畫面，在橫幅提示上方有一些無法辨識的裝置，橫幅提示要註冊未列出的裝置，或找出無法辨識的裝置。](./media/macOS_enroll_002_tap_here_banner.png)

3.    裝置會在快顯視窗中開啟。 選取 [重設密碼] 按鈕。

    ![公司入口網站上所選裝置的所有選項，包括重新命名、移除、重設裝置、重設密碼，以及遠端鎖定。 ](./media/iwp-screen-with-all-options.png)

4.  會出現橫幅，要求您確認您想要重設密碼，而且完成之後您的裝置會將您登出。 然後您必須等候 5 分鐘，才能再次登入。

  ![重設密碼橫幅，與重設裝置密碼和使用者將如何登出的警告。 使用者輸入的按鈕為 [登出] 和 [取消]。](./media/iwp-reset-passcode-popup.png)

4.  選取 [登出]，您會收到最後一個訊息，告訴您密碼從裝置移除的相關資訊。 如果您的裝置不在手邊，請勿移除密碼，因為任何能夠實際存取裝置的人都將能夠存取其上的大部分個人或公司資訊。

  ![第二個重設密碼橫幅，與重設裝置密碼和將會如何從裝置移除密碼的警告。 它也會建議如何前往裝置設定來設定新的密碼。](./media/iwp-reset-passcode-2nd-popup.png)


由於不同的裝置有不同類型的密碼，您可以在下表中找出重設密碼對您的特定裝置可能會有什麼影響。 

    |裝置類型|重設時會發生什麼事|
    |------------|-----------|
    |Android|移除現有的密碼並使用字母和數字建立暫時密碼|
    |iOS|移除現有的密碼，但不建立暫時密碼。 如果您使用 Touch ID 指紋掃描器來開啟裝置或進行購物，您需要再設定一次。|
    |Windows 10 Mobile|移除現有的密碼，並使用字母和數字建立暫時密碼。 如果您使用 Windows Hello 臉部辨識登入，其仍受支援。|
    |Windows Phone 8.1|移除現有的密碼，並使用數字建立暫時密碼。|

    5.  解除鎖定裝置並設定新密碼，或移至裝置的 [設定] 變更暫時密碼。

    若要查看密碼重設成功的確認通知，請按一下公司入口網站右上方的的通知旗標。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。

