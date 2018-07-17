---
title: 使用公司入口網站在 Intune 註冊 macOS 裝置 | Microsoft Docs
description: 描述如何使用公司入口網站應用程式在 Intune 中註冊 macOS 裝置
keywords: Mac OS X, macOS, OS X
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3bb659cc-9b57-4d19-8631-2c26749fa71c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: elocholi
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 3dac9446d7a1097f5be4d0851cd78e8cbb86cc4e
ms.sourcegitcommit: 2198a39ae48beca5fc74316976bc3fc9db363659
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38224751"
---
# <a name="enroll-your-macos-device-in-intune-with-the-company-portal-app"></a>使用公司入口網站應用程式在 Intune 中註冊 macOS 裝置

取得組織應用程式、資料及資源的存取權，讓您更輕鬆地執行工作。 您的組織使用 Intune [管理這些資源的存取權](what-happens-if-you-install-the-Company-Portal-app-and-enroll-your-device-in-intune-macos.md)，而這需要您下載 macOS 的公司入口網站應用程式。 這些指示適用於 OS X El Capitan 10.11+ 上的 macOS 裝置。


1. 在您的 __Dock__ 上，尋找 __Safari__ 並開啟新視窗，然後開啟[公司入口網站](https://portal.manage.microsoft.com)。

2. 使用您的工作或學校帳戶登入公司入口網站。

   [!INCLUDE [wit_nextref](includes/end-user-password-guidance.md)]


3. 登入之後，按一下頁面左上角的 [功能表]，然後選取 [我的裝置]。

   ![Web 入口網站登陸頁面的螢幕擷取畫面，顯示尚無任何應用程式可以安裝，並且在下方有 [我的裝置] 按鈕。](./media/macOS_enroll_001_landing_page.png)

4. 在 [我的裝置] 頁面上，您將看到一份已註冊的裝置清單或是只看到橫幅。 這取決於您是否已註冊裝置、macOS 或其他。 若要註冊未列出的裝置，請選取橫幅：__如果已列出您的裝置，請點選這裡來識別它。您也可以點選這裡來註冊未列出的裝置__。 如果您沒有任何已註冊的裝置，橫幅會顯示**您沒有任何已註冊的裝置。請點選這裡註冊這部裝置。**

    ![[我的裝置] 頁面的螢幕擷取畫面，在橫幅提示上方有一些無法辨識的裝置，橫幅提示要註冊未列出的裝置，或找出無法辨識的裝置。](./media/macOS_enroll_002_tap_here_banner.png)

5. 將公司入口網站應用程式下載到您的 macOS 裝置以繼續註冊。

    ![提示使用者下載 macOS 公司入口網站應用程式的通知。 此通知會在右下角顯示 [下載] 的按鈕上方顯示步驟所述的文字。](./media/macOS_enroll_IWP_CP_app_notice.png)

6. Mac 將確認可安全地開啟 **CompanyPortal.pkg** 的下載。 開啟安裝程式並完成安裝程序。

7. 安裝程式完成後，開啟 [應用程式] 資料夾或 [啟動控制板]，然後開啟 [公司入口網站]。

8. Mac 將顯示一則訊息，指出：**"CompanyPortal" 是從網際網路下載的應用程式。您確定要繼續嗎？ 按一下 [開啟]。

   > [!NOTE]
   > Intune 需要存取您的電腦，藉此確定您的裝置具備足夠的安全性可存取您組織的資源。 如果您的電腦拒絕開啟公司入口網站應用程式，請嘗試[關閉閘道管理員](https://support.apple.com/HT202491)，然後開啟應用程式。

9. 您在公司入口網站應用程式中看到的第一個畫面，會提示您使用用來登入公司入口網站的相同公司或學校帳戶進行 [登入]。

10. 公司入口網站會確認您的帳戶資訊，然後向您顯示您的 [裝置註冊] 和 [裝置合規性] 狀態。 將會有黃色三角形，讓您知道您擁有需要採取的動作，確定可在工作時安全使用 Mac。 按一下 [開始] 開始[註冊裝置進行管理](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md)。

11. Mac 將會開始註冊以進行管理。 在此期間，系統可能會提示您提供您電腦的登入資訊。 這可能需要幾分鐘的時間註冊。 在此期間，您可以在電腦上執行其他事項。 完成公司存取設定之後會顯示一則訊息，讓您知道已完成。

是否仍需要協助？ 請向公司支援人員確認。 您可以在[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)中找到他們的連絡資訊。
