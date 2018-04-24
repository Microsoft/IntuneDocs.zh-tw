---
title: 如何登入公司入口網站應用程式 | Microsoft 文件
description: 了解如何在多種平台上登入「公司入口網站」應用程式。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 84f8e70d8321ca27d689d13472b69007a1d6c186
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>如何登入公司入口網站應用程式？ <!--User Story 1132123-->

您可以使用公司入口網站應用程式來存取公司資源，如電子郵件和商務應用程式。 登入公司入口網站有兩種主要方式：

* 使用您的工作電子郵件地址和密碼
* 從另一部裝置登入

即使下圖適用於 iOS，但 Android 和 Windows 裝置的程序幾乎都相同。

## <a name="signing-in-with-your-email-address-and-password"></a>使用您的電子郵件地址和密碼登入

1. 在您的裝置上開啟公司入口網站應用程式，然後點選 [登入]。

   ![公司入口網站登入頁面，具有一個人員位於代表網站的圖形前方的圖示。 下面是「取得公司資源的存取權，並維護其安全」文字及 [登入] 按鈕。 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   沒有公司入口網站應用程式？ 了解如何針對 [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) 或 [Android](install-the-company-portal-app-android.md) 進行安裝和下載。

2. 輸入您的 [工作或學校帳戶]，然後點選 [下一步]。

   ![系統會在畫面上單獨提示使用者輸入電子郵件地址，而不是同時提示輸入電子郵件與密碼。](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. 輸入您的密碼，然後點選 [登入]。

   ![接受使用者的電子郵件地址後，系統會提示使用者輸入密碼。](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. 在公司入口網站接受您的登入之後，就會將您登入，而您便可以開始存取公司資源。   

   ![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出進度。](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>以憑證式驗證登入

1.  在您的裝置上開啟「公司入口網站」應用程式。

2.  輸入 [工作或學校帳戶]。

3.  點選 [以憑證登入] 連結。

4.  點選 [繼續] 以使用憑證。

## <a name="signing-in-from-another-device"></a>從另一部裝置登入

如果您不使用密碼來登入公司資源，則可以使用加一部裝置的方式來確認您是具有適當存取層級的適當人員。 如果貴公司使用智慧卡來存取您的電腦，您可能需要使用另一部裝置來登入。

1. 請選取電子郵件文字方塊下方的 [從另一部裝置登入] 連結，而不是輸入電子郵件地址。

   ![公司入口網站登入頁面會提示使用者輸入電子郵件地址。  下面是 [下一步] 按鈕和 [從另一部裝置登入] 連結。 此外，也包含 [無法存取您的帳戶?] 連結 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. 您會收到用來登入公司入口網站的唯一一次性驗證碼。

   ![系統會提供指示和一個唯一密碼，說明應從工作電腦移至 https://microsoft.com/devicelogin 頁面，然後使用該驗證碼來進行登入。](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. 在其他裝置上，開啟瀏覽器並移至 [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin) 來輸入該驗證碼。

   ![使用者工作電腦上的瀏覽器 (而非公司入口網站應用程式) 的影像。 顯示的 [裝置登入] 頁面提示使用者輸入在公司入口網站應用程式中收到的驗證碼。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. 在 [裝置登入] 頁面驗證該驗證碼後，選取 [繼續] 以允許在其他裝置上登入公司入口網站。

   ![使用者已將唯一驗證碼輸入至欄位，且 [裝置登入] 網站已要求確認 Intune 公司入口網站是接收驗證以登入的正確應用程式。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. 驗證碼一旦驗證後，您便可以關閉此視窗。

   ![確認頁面指出使用者現已在其裝置上登入公司入口網站應用程式，並且可以關閉此頁面。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. 在原始裝置上，公司入口網站應用程式會開始登入。

   ![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出其進度。](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://portal.manage.microsoft.com#HelpDeskDialog)。
