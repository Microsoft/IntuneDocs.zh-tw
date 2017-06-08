---
title: "在 Intune 註冊 macOS 裝置 | Microsoft Docs"
description: "描述在 Intune 註冊 macOS 裝置的方式"
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
searchScope:
- User help
ROBOTS: 
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 16f7f06d02a56b4887c0d29ffcaed111185652a9
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017


---

# <a name="enroll-your-macos-device-in-intune"></a>在 Intune 註冊 macOS 裝置

取得組織應用程式、資料及資源的存取權，讓您能夠執行您的工作。 如果您使用 macOS 裝置來工作，這表示要安裝__管理設定檔__。 這只是由 IT 系統管理員所設定的檔案，可在您的 Mac 上載入設定和存取資訊。 想要深入了解嗎？ 請參閱[當您安裝公司入口網站應用程式並在 Intune 註冊您的裝置時，會發生什麼情況](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)

  > [!NOTE]
  > 如果您真的想要嘗試註冊 iOS 裝置 (例如 iPhone 或 iPad)，請[試著改用下列指示](enroll-your-device-in-intune-ios.md)。

1. 在您的 __Dock__ 上，尋找 __Safari__ 並開啟新視窗，然後開啟[公司入口網站](http://portal.manage.microsoft.com)。
2. 使用您的工作或學校帳戶登入公司入口網站。

  [!INCLUDE[wit_nextref](includes/end-user-password-guidance.md)]

3. 當您登入時，您會看到任何可用的 [首頁]、[應用程式] 和 [類別] 索引標籤。 此頁面會顯示可供您安裝的任何應用程式。 如果您尚未註冊任何裝置，您會看到通知，指出**我們無法顯示任何應用程式。** 您可以選取 [我的裝置] 繼續。

 ![Web 入口網站登陸頁面的螢幕擷取畫面，顯示尚無任何應用程式可以安裝，並且在下方有 [我的裝置] 按鈕。](./media/macOS_enroll_001_landing_page.png)

4. 在 [我的裝置] 頁面上，您將看到一份已註冊的裝置清單或是只看到橫幅。 這取決於您是否已註冊裝置、macOS 或其他。 若要註冊未列出的裝置，請選取橫幅：__如果已列出您的裝置，請點選這裡來識別它。您也可以點選這裡來註冊未列出的裝置__。

  ![[我的裝置] 頁面的螢幕擷取畫面，在橫幅提示上方有一些無法辨識的裝置，橫幅提示要註冊未列出的裝置，或找出無法辨識的裝置。](./media/macOS_enroll_002_tap_here_banner.png)

5. 隨即會顯示一個快顯視窗，簡短說明為什麼您即將__識別或註冊此裝置__。 檢閱此資訊，然後按一下 [註冊] 繼續進行。

 ![識別或註冊此裝置 macOS](./media/macOS_enroll_003_IDenroll_popup.png)

6. 隨即會顯示第二個快顯視窗，簡短說明當您__註冊此裝置__時，會發生什麼情況。 檢閱此資訊，然後按一下 [安裝] 繼續進行。

 ![註冊此裝置 macOS](./media/macOS_enroll_004_enroll_popup.png)

  > [!NOTE]
  > Intune 需要存取您的電腦，藉此確定您的裝置具備足夠的安全性可存取您組織的資源。 請參閱[當您在 Intune 註冊您的裝置時，會發生什麼情況](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios.md)。

7. 隨即會開啟 [系統喜好設定]，並詢問您是否想要__安裝「管理設定檔」？__ 按一下 [安裝] 繼續進行，或按一下 [顯示設定檔] 以取得更多詳細資料。

 ![安裝管理設定檔](./media/macOS_enroll_005_sysprefs_mgmt_profile.png)

8. 隨即會顯示 macOS 快顯視窗。 提供電腦的__使用者名稱__和__密碼__，然後按一下 [確定]，藉以確認您想要進行變更。 這會將管理設定檔安裝到您的 Mac 上。

 ![macOS 設定檔安裝快顯視窗](./media/macOS_enroll_006_sysprefs_admin_login.png)

9. 您可能會看到一些來自您 Mac 的其他訊息，其中包括更多關於此設定檔的詳細資料，或者您是否確定要__安裝__。 在這些過程中按一下 [繼續] 和 [安裝] 繼續進行。 一旦安裝完成後，您將能夠在 [裝置設定檔] 清單中檢視剛安裝的 [管理設定檔]。

 ![已安裝 macOS 設定檔](./media/macOS_enroll_007_sysprefs_installed_profile.png)

是否仍需要協助？ 請洽詢您的 IT 系統管理員。 您可以在[公司入口網站](http://portal.manage.microsoft.com)中找到他們的連絡資訊。

