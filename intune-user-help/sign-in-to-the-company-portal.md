---
title: 如何登入公司入口網站應用程式 | Microsoft 文件
description: 了解如何在多種平台上登入「公司入口網站」應用程式。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 68a44027c14e0a52d72fc032a6ab42413fa8df96
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508296"
---
# <a name="sign-in-to-company-portal"></a>登入以公司入口網站  

有三種方式可登入公司入口網站應用程式：

* 使用您的工作電子郵件地址與密碼登入。  
* 使用憑證式驗證登入。  
* 從另一部裝置登入。    


## <a name="sign-in-with-your-email-address-and-password"></a>使用您的電子郵件地址與密碼登入
下列步驟顯示適用于 iOS 的公司入口網站螢幕擷取畫面。  

1. 在您的裝置上開啟應用程式，然後按 [登**入**]。  

   [![Example 公司入口網站登入頁面的螢幕擷取畫面。](/intune-user-help/media/intune-ios-cp-signin-1908.png)](/intune-user-help/media/intune-ios-cp-signin-lightbox-1908.png#lightbox)  


2. 輸入您的 [工作或學校帳戶]  ，然後點選 [下一步]  。

   ![系統會在畫面上單獨提示使用者輸入電子郵件地址，而不是同時提示輸入電子郵件與密碼。](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. 輸入您的密碼，然後點選 [登入]  。

   ![接受使用者的電子郵件地址後，系統會提示使用者輸入密碼。](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. 應用程式將會驗證您的認證。 完成時，您可以存取您組織的資源，並安裝可用的應用程式。  

   ![執行驗證程序之後，公司入口網站應用程式會登入，並顯示載入列。](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="sign-in-with-certificate-based-authentication"></a>使用憑證式驗證登入

1. 在您的裝置上開啟「公司入口網站」應用程式。  

2. 輸入 [工作或學校帳戶]  。  

3. 點選 [以憑證登入]  連結。  

4. 點選 [繼續]  以使用憑證。  

## <a name="sign-in-from-another-device"></a>從另一部裝置登入

如果您的公司使用智慧卡來存取您的電腦，您可能必須從另一部裝置登入來進行驗證。  

1. 在您的裝置上開啟「公司入口網站」應用程式。 請確定這是您將用來存取工作資源的裝置。       

1. 選取 [從另一部裝置登入]  。  

   ![公司入口網站登入頁面會提示使用者輸入電子郵件地址。  顯示 [下一步] 按鈕與 [從另一部裝置登入] 連結。 此外，也包含 [無法存取您的帳戶?] 連結 底部的連結會指向 Microsoft 隱私權與 Cookie 資訊。](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. 您會收到用來登入公司入口網站的唯一一次性驗證碼。 複製程式碼。

   ![系統會提供指示和一個唯一密碼，說明應從工作電腦移至 https://microsoft.com/devicelogin 頁面，然後使用該驗證碼來進行登入。](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. 在您的其他裝置（您用來驗證的裝置）上，開啟瀏覽器並移至[https://microsoft.com/devicelogin](https://microsoft.com/devicelogin)。 輸入或貼上程式碼。  

   ![使用者工作電腦上的瀏覽器 (而非公司入口網站應用程式) 的影像。 顯示的 [裝置登入] 頁面提示使用者輸入在公司入口網站應用程式中收到的驗證碼。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. 選取 [__繼續__] 以允許公司入口網站登入您的工作裝置。   

   ![使用者已將唯一驗證碼輸入至欄位，且 [裝置登入] 網站已要求確認 Intune 公司入口網站是接收驗證以登入的正確應用程式。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. 驗證碼一旦驗證後，您便可以關閉此視窗。  

   ![確認頁面指出使用者現已在其裝置上登入公司入口網站應用程式，並且可以關閉此頁面。](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. 公司入口網站應用程式會在您的工作裝置上登入。  

   ![經過驗證程序之後，公司入口網站應用程式會登入，並以載入列指出其進度。](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

是否仍需要協助？ 請連絡您公司的支援人員。 如需連絡資訊，請查看[公司入口網站](https://go.microsoft.com/fwlink/?linkid=2010980)。  
