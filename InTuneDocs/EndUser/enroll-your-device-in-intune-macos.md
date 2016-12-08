---
title: "在 Intune 註冊 macOS 裝置 | Microsoft Intune"
description: "描述在 Intune 註冊 macOS 裝置的方式"
keywords: Mac OS X, macOS, OS X
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 11/21/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 58eb0e7a-1321-4c66-a281-88fb01e72c1c
ROBOTS: 
ms.reviewer: esmich
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 162d176c5f272f5f19ba18cdd07fe815ac1bcce7
ms.openlocfilehash: fc0efceb8a0c3e1323f7d94625bc5f618d35bfd6


---

# <a name="enroll-your-macos-device-in-intune"></a>在 Intune 註冊 macOS 裝置

取得組織應用程式、資料及資源的存取權，讓您能夠執行您的工作。 如果您使用 macOS 裝置來工作，這表示要安裝__管理設定檔__。 這只是由 IT 系統管理員所設定的檔案，可在您的 Mac 上載入設定和存取資訊。 想要深入了解嗎？ 請參閱[當您安裝公司入口網站應用程式並在 Intune 註冊您的裝置時，會發生什麼情況](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios.md)。

  > [!NOTE]
  > 如果您真的想要嘗試註冊 iOS 裝置 (例如 iPhone 或 iPad)，請[試著改用下列指示](enroll-your-device-in-intune-ios.md)。

1. 在您的 __Dock__ 上，尋找 __Safari__ 並開啟新視窗，然後開啟[公司入口網站](http://portal.manage.microsoft.com)。
2. 使用您的工作或學校帳戶登入公司入口網站。

  [!INCLUDE[wit_nextref](../includes/end-user-password-guidance.md)]

3. 當您登入時，將看到適用於您 IT人員的所有可用__應用程式__、__我的裝置__，以及任何可用的__連絡資訊__。 您將會在頁面頂端看到一個通知，指出**此裝置尚未註冊，或公司入口網站無法辨識其身分。若要選取其他裝置，請<u>點選這裡</u>。** 按一下 [點選這裡]。

 ![公司入口網站 macOS 登陸頁面](./media/macOS_enroll_001_landing_page.png)

4. 隨即會顯示一個快顯視窗，簡短說明為什麼您即將__識別或註冊此裝置__。 檢閱此資訊，然後按一下 [註冊] 繼續進行。

 ![識別或註冊此裝置 macOS](./media/macOS_enroll_002_IDenroll_popup.png)

5. 隨即會顯示第二個快顯視窗，簡短說明當您__註冊此裝置__時，會發生什麼情況。 檢閱此資訊，然後按一下 [安裝] 繼續進行。

 ![註冊此裝置 macOS](./media/macOS_enroll_003_enroll_popup.png)

  > [!NOTE]
  > Intune 需要存取您的電腦，藉此確定您的裝置具備足夠的安全性可存取您組織的資源。 請參閱[當您在 Intune 註冊您的裝置時，會發生什麼情況](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-ios)。

6. 隨即會開啟 [系統喜好設定]，並詢問您是否想要__安裝「管理設定檔」？__ 按一下 [安裝] 繼續進行，或按一下 [顯示設定檔] 以取得更多詳細資料。

 ![安裝管理設定檔](./media/macOS_enroll_004_sysprefs_mgmt_profile.png)

7. 隨即會顯示 macOS 快顯視窗。 提供電腦的__使用者名稱__和__密碼__，然後按一下 [確定]，藉以確認您想要進行變更。 這會將管理設定檔安裝到您的 Mac 上。

 ![macOS 設定檔安裝快顯視窗](./media/macOS_enroll_005_sysprefs_admin_login.png)

8. 您可能會看到一些來自您 Mac 的其他訊息，其中包括更多關於此設定檔的詳細資料，或者您是否確定要__安裝__。 在這些過程中按一下 [繼續] 和 [安裝] 繼續進行。 一旦安裝完成後，您將能夠在 [裝置設定檔] 清單中檢視剛安裝的 [管理設定檔]。

 ![已安裝 macOS 設定檔](./media/macOS_enroll_006_sysprefs_installed_profile.png)

是否仍需要協助？ 請洽詢您的 IT 系統管理員。 您可以在[公司入口網站](http://portal.manage.microsoft.com)中找到他們的連絡資訊。



<!--HONumber=Nov16_HO4-->


