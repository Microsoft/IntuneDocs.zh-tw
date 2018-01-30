---
title: "如何從公司入口網站重設密碼 | Microsoft Docs"
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 111cbc1aa2dd9c537a7f5581d0dd6f2e75d8c7f3
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>如何從公司入口網站重設裝置密碼

如果您在 Intune 中註冊的裝置遺失裝置 PIN 或密碼，您可以使用[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)重設密碼。 您可以使用公司入口網站來管理已在 Intune 註冊的電腦和裝置，而且就像使用公司入口網站應用程式一樣，可讓您執行大部分同樣的工作。

> [!NOTE]
> 如果使用公司註冊的裝置，您在公司入口網站上可能不會看到 [重設密碼] 按鈕。 如果沒有看到該按鈕，您必須連絡公司支援人員為您重設密碼。

若要重設密碼：

1.  在[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)上，點選 [功能表] 按鈕![功能表按鈕的小圖像，以平行方式堆疊的三個水平橫條](/intune/media/CP_hamburger_menu.png)，然後選取 [我的裝置]。

2. 在 [我的裝置] 頁面上，選取您想要重設密碼的裝置名稱。

  ![[我的裝置] 頁面的螢幕擷取畫面，在橫幅提示上方有一些無法辨識的裝置，橫幅提示要註冊未列出的裝置，或找出無法辨識的裝置。](./media/macOS_enroll_002_tap_here_banner.png)

3.  裝置會在快顯視窗中開啟。 選取 [重設密碼] 按鈕。

    ![公司入口網站上所選裝置的所有選項，包括重新命名、移除、重設裝置、重設密碼，以及遠端鎖定。 ](./media/iwp-screen-with-all-options.png)

4.  會出現橫幅，要求您確認您想要重設密碼，而且完成之後您的裝置會將您登出。 然後您必須等候 5 分鐘，才能再次登入。

  ![重設密碼橫幅，與重設裝置密碼和使用者將如何登出的警告。使用者輸入的按鈕為 [登出] 和 [取消]。](./media/iwp-reset-passcode-popup.png)

5.  選取 [登出]，就會收到最後一個訊息，告訴您密碼從裝置移除的相關資訊。 如果您的裝置不在手邊，請勿移除密碼，因為任何能夠實際存取裝置的人都將能夠存取其上的大部分個人或公司資訊。 

  ![第二個重設密碼橫幅，與重設裝置密碼和將會如何從裝置移除密碼的警告。 它也會建議如何前往裝置設定來設定新的密碼。](./media/iwp-reset-passcode-2nd-popup.png)

  不同的裝置具有不同類型的密碼。

  **Android**：移除現有的密碼，並建立包含字母和數字的暫時密碼 
  
  > [!NOTE]
  > 您無法重設 Android 7.0 和更新版本裝置的密碼。 如果您忘記密碼，則必須將這些裝置重設為原廠設定。

  **iOS**：移除現有的密碼，但不建立暫時密碼。 如果您使用 Touch ID 指紋掃描器來開啟裝置或進行購買，您必須再次設定指紋。

  **Windows 10 行動裝置版**：移除現有的密碼，並建立包含字母和數字的暫時密碼。 如果您使用 Windows Hello 臉部辨識登入，系統將繼續支援它。
    
  **Windows Phone 8.1**：移除現有的密碼，並建立包含數字的暫時密碼

  針對 Android 和 Windows 裝置，暫時密碼會顯示在 [裝置詳細資料] 中。 

6.  解除鎖定裝置並設定新密碼，或移至裝置的 [設定] 變更暫時密碼。

若要查看密碼重設成功的確認通知，請按一下公司入口網站右上方的的通知旗標。

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
