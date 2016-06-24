---
# required metadata

title: 註冊行動裝置並安裝 App | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5d3215e7-0a5c-44bd-afb0-aeafce98c43f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 註冊行動裝置並安裝 App
若要透過 Intune 設定行動裝置管理，您首先必須設定行動裝置管理授權單位、啟用裝置平台的管理，然後向公司入口網站應用程式註冊您的裝置。 接著便可部署您在步驟 6 發行的 Microsoft Skype 應用程式。

## 啟用裝置管理並註冊裝置

1.  讓 Intune 成為您的行動裝置管理授權單位  在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [系統管理]  >  [行動裝置管理]，然後選擇 [工作] 下的 [設定 MDM 授權單位]。
    ![在 [MDM 授權單位] 對話方塊中，選擇 [是]。 管理主控台。](./media/mdmAuthority.png)

2.  將 mdm 設為 Intune 針對您的裝置平台啟用 MDM

    -   針對您想要管理的裝置平台啟用行動裝置管理。

    -   依您的平台而異，需要使用不同的需求：

    -   iOS 和 Mac OS X：請參閱[使用 Microsoft Intune 設定 iOS 和 Mac 管理](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune) Windows Phone：請參閱[使用 Microsoft Intune 設定 Windows Phone 管理](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)

3.  Android：Android 行動裝置可讓使用者使用 [Google Play](https://play.google.com/store/apps/details?id=com.skype.raider) 提供的公司入口網站 App 來註冊。

    -   在 Intune 中無需進行其他設定。

    -   註冊裝置： Android - 安裝 [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) 上 Microsoft Corporation 所提供的 Intune 公司入口網站 App，然後使用上述新增的 Intune 使用者認證登入。

    -   iOS 和 Mac OS X - 安裝 App Store 上 Microsoft Corporation 所提供的 Microsoft Intune 公司入口網站應用程式，然後使用上述新增的 Intune 使用者認證登入。  檢視 [註冊的裝置]  以新增您的裝置。

    -   Windows Phone 8.1 - 使用者會安裝 Windows Phone 市集上 Microsoft Corporation 所提供的公司入口網站 App，然後使用上述新增的 Intune 使用者認證登入。 檢視 [註冊的裝置]  以新增您的裝置。

    Windows Phone 8.0  - 使用者可以選擇 [系統設定]  &gt;  [公司應用程式]，然後使用上述新增的 Intune 使用者認證登入。

## 公司入口網站應用程式會部署到您的手機上。
如果系統提示您提供 伺服器位址，請輸入 "manage.microsoft.com"。 在已註冊的裝置上安裝應用程式

在本快速入門指南的[步驟 6](start-with-a-paid-subscription-to-microsoft-intune-step-6.md) 中，您已發佈 Skype 應用程式到您的自訂 Intune 使用者群組。

您現在將在新註冊的裝置上安裝該應用程式。


### 在已註冊的行動裝置上開啟 [公司入口網站]，選擇 [應用程式] ，然後安裝 Microsoft Skype
若要深入了解如何使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 管理行動裝置，請參閱[準備在 Microsoft Intune 中註冊裝置](/intune/deploy-use/get-ready-to-enroll-devices-in-microsoft-intune) 後續步驟 恭喜！

>您剛完成 Intune 快速入門指南的最後一個步驟。

>在您完成初始設定之後，您可以考慮啟用其他 MDM 功能。  


<!--HONumber=May16_HO2-->


