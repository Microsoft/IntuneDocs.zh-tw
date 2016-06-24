---
# required metadata

title: 註冊評估行動裝置 | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 註冊評估行動裝置並安裝應用程式
若要透過 Intune 設定行動裝置管理，您首先必須設定行動裝置管理授權單位、啟用裝置平台的管理，然後向公司入口網站應用程式註冊您的裝置。 接著便可部署您發行的 Microsoft Skype 應用程式。

## 準備服務進行裝置管理

1.  **讓 Intune 成為您的行動裝置管理授權單位**

    在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [管理] &gt; [行動裝置管理]。 選擇 [工作] > [設定 MDM 授權單位]，然後選擇 [MDM 授權單位] 對話方塊中的 [是]。

2.  **針對您的裝置平台啟用 MDM**

    針對您想要管理的裝置平台啟用行動裝置管理。 依您的平台而異，需要使用不同的需求：

    -   iOS 和 Mac OS X：請參閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/Intune/Deploy-Use/set-up-ios-and-mac-management-with-microsoft-intune)

    -   Android：Android 行動裝置可讓使用者使用 Google Play 提供的公司入口網站 App 來註冊。 在 Intune 中無需進行其他設定。

    -   Windows Phone：請參閱[使用 Microsoft Intune 設定 Windows Phone 管理](/Intune/Deploy-Use/set-up-windows-phone-management-with-microsoft-intune)

## 註冊測試裝置

### iOS 和 Mac OS X
安裝 App Store 上 Microsoft Corporation 所提供的 Microsoft Intune 公司入口網站應用程式，然後使用上述新增的 Intune 使用者認證登入。 檢視 [註冊的裝置]  以新增您的裝置。

### Android
安裝 [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) 上 Microsoft Corporation 所提供的 Intune 公司入口網站應用程式，然後使用上述新增的 Intune 使用者認證登入。

### Windows Phone 8.1
使用者會安裝 Windows Phone 市集上 Microsoft Corporation 所提供的公司入口網站應用程式，然後使用上述新增的 Intune 使用者認證登入。  檢視 [註冊的裝置]  以新增您的裝置。

 ### Windows Phone 8。0
 使用者可以按一下 [系統設定] &gt; [公司應用程式]，然後使用上述新增的 Intune 使用者認證登入。 公司入口網站應用程式會部署到您的手機上。

如果系統提示您提供 伺服器位址，請輸入 "manage.microsoft.com"。


## 安裝先前部署的應用程式
在行動裝置上開啟 [公司入口網站]，並選擇 [應用程式]，然後安裝 Microsoft Skype

若要深入了解如何使用 Intune 管理行動裝置，請參閱[準備在 Microsoft Intune 中註冊裝置](/Intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune)

### 後續步驟
恭喜！ 您剛剛已完成 Microsoft Intune 評估逐步解說的步驟 5。

>[!div class="step-by-step"]

>[&larr; 建立原則](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-4.md)     [選項和額外項目 &rarr;](.\get-started-with-a-30-day-trial-of-microsoft-intune-step-6.md)  


<!--HONumber=May16_HO2-->


