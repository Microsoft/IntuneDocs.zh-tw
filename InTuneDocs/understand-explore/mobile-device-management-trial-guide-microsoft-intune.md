---
title: "評估 Microsoft Intune 中的行動裝置管理功能 | Microsoft Docs"
description: "評估 Intune 免費試用版中的 MDM。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 47806f69-303d-41d9-9b0e-9b9445ea24ac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 4133c64d283682f0be37cd6ac69164ef872a5026


---

# <a name="evaluate-mobile-device-management-in-microsoft-intune"></a>評估 Microsoft Intune 中的行動裝置管理功能
本評估指南將示範 Intune 中行動裝置管理的運作方式。 您將會：
- 註冊要由 Intune 管理的裝置。
- 建立群組來組織使用者和裝置。
- 建立一些裝置管理原則並部署到您的群組。
- 發佈應用程式讓持有已註冊裝置的使用者可在其裝置上安裝應用程式。
<!--- - Monitor the device? View a report of compliant devices?--->
<!--- - Remove the device from management--->

## <a name="assumptions"></a>假設
本指南假設您僅針對評估用途使用試用版，且您訂閱時想要以全新的環境開始。

為使您可以輕鬆地開始使用試用版，我們設定了一個非常簡單的環境，其中僅使用 Intune，並假設它將會是您的行動裝置管理授權單位。 不過，如果您想要進一步探索，在整個指南中我們將指引您進入更深入的技術內容。

您可以在試用版中執行訂閱版的所有動作；唯一的差別是試用版中限制 100 個使用者帳戶。

## <a name="whats-not-covered"></a>未涵蓋的項目
|如果您有興趣 |閱讀這個 |
|------------------------|----------|
|非測試環境中的 MDM | [快速入門](https://docs.microsoft.com/en-us/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune) |
|MDM 搭配 Intune 和 System Center Configuration Manager | [混合式行動裝置管理](https://docs.microsoft.com/en-us/sccm/mdm/understand/hybrid-mobile-device-management) |

因為上述指南會協助您在生產環境中設定 Intune，它們的設定程序較長，且設定時需要您做決定的決策點也比評估指南多。

若要讓自己快速地熟悉 Intune，建議您從評估指南開始，然後再移至其他指南。

## <a name="prerequisites-for-this-evaluation"></a>這個評估的先決條件
- Internet Explorer 10 或更新版本
- 您將用來測試 Intune 使用者如何使用公司入口網站來註冊及管理其裝置的裝置。 我們在此指南中使用 iPad 和 Android 手機。
- 若要管理 iPad 或其他 iOS 裝置，您將需要 [Apple Push Notification Service 憑證](https://docs.microsoft.com/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)。
- [Intune 試用版訂閱](sign-up-for-30-day-trial-microsoft-intune.md)

## <a name="set-your-mdm-authority"></a>設定您的 MDM 授權單位
您要使用 Intune 管理行動裝置時，需採取的第一個步驟是設定**行動裝置管理 (MDM) 授權單位**。

如果您單獨使用 Intune (如此試用版所假設)，或如果您在 Enterprise Mobility + Security (EMS) 訂閱中使用 Intune，您需要將 Intune 設定為您的行動裝置管理授權單位。 也就是說，您將 Intune 指定為要在組織中用來管理行動裝置的服務。

想要使用 Intune 搭配 System Center Configuration Manager 來管理行動裝置的客戶，必須決定要使用 Intune 或 Configuration Manager 做為他們的行動裝置管理授權單位。 在生產環境中這是很重要的決策，因為一旦決定後就非常難以變更這個設定，但這已經超出本評估指南的範圍。 若要深入了解將 Intune 或 Configuration Manager 設定為您 MDM 授權單位的影響，請參閱[在獨立 Intune 和混合式行動裝置管理之間做選擇](https://docs.microsoft.com/en-us/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)。

針對試用版，我們會將 Intune 設為 MDM 授權單位；這不會影響您的生產環境，除非您決定要將試用版用於實際執行環境。

1. 在 [Intune 管理主控台](https://manage.microsoft.com/)中，選擇 [管理] &gt; [行動裝置管理]。
2. 在 [工作] 清單中，選擇 [設定 MDM 授權單位]。 [設定 MDM 授權單位]  對話方塊隨即開啟。 <!---screen shot--->
3. Intune 要求您確認是否要以 Intune 做為 MDM 授權單位。 選取核取方塊，然後選擇 [是] 以使用 Intune 來管理行動裝置。

## <a name="enroll-your-test-devices-into-intune"></a>將您的測試裝置註冊到 Intune

在本指南中，我們將會註冊 Android 手機和 Apple iPad，但會在本節結尾處提供[深入了解 Intune 的裝置註冊](#Learn-more-about-device-enrollment)的連結。
### <a name="android"></a>Android
安裝 Microsoft Corporation 在 [Google Play](http://go.microsoft.com/fwlink/p/?LinkId=386612) 上提供的「Intune 公司入口網站」App，然後使用您註冊免費試用版時建立的 Intune [使用者認證](sign-up-for-30-day-trial-microsoft-intune.md#add-users)登入。

### <a name="ios"></a>iOS
在使用者註冊他們的 iOS 裝置之前，您必須設定 Intune 以管理這些裝置。

1. **取得憑證簽署要求**<br/>
使用您的系統管理員帳戶登入，然後移至 [系統管理] > [行動裝置管理] > [iOS 與 Mac OS X] > [上傳 APNs 憑證]，然後選擇 [下載 APNs 憑證要求]。 在本機儲存憑證簽署要求 (.csr) 檔案。 .csr 檔案用來向 Apple Push Certificates Portal 要求信任關係憑證。 <!--- screen shot--->
2.  **取得 Apple 推送通知服務憑證**<BR/>
前往 [Apple Push Certificates 入口網站](https://idmsa.apple.com/IDMSWebAuth/login?appIdKey=3fbfc9ad8dfedeb78be1d37f6458e72adc3160d1ad5b323a9e5c5eb2f8e7e3e2&rv=2)，然後使用您公司的 Apple ID 登入，以使用 .csr 檔案建立 APNs 憑證。 選擇 [在 Apple Push Certificates 入口網站上上傳] 之後，您會收到一個無法用於 APNs 的 .json 檔案。 完成下載，並回到 Apple Push Certificates 入口網站的 [Certificates for Third-Party Servers] (協力廠商伺服器的憑證)，然後選擇 [下載]。

 下載 APNs (.pem) 憑證，並將該檔案儲存在本機。 稍後必須使用這個 Apple ID 來更新 APNs 憑證。
3.  **將 APNs 憑證新增至 Intune**<BR/>
在 Microsoft Intune 管理主控台中，移至 [系統管理] > [行動裝置管理] >  [iOS 與 Mac OS X] > [上傳 APNs 憑證]，然後選擇 [上傳 APNs 憑證]。 移至憑證 (.pem) 檔案，並選擇 [開啟]，然後輸入您的 Apple ID。 使用 APNs 憑證。 透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。
4.  **告訴使用者如何註冊其裝置來存取公司資源。**<br/>
如需使用者註冊指示，請參閱[在 Intune 中註冊您的 iOS 裝置](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-ios)和[在 Intune 中註冊您的 Mac OS X 裝置](https://docs.microsoft.com/en-us/Intune/enduser/enroll-your-device-in-intune-mac-os-x)。 註冊程序會告知使用者，他們能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。


### <a name="learn-more-about-device-enrollment"></a>深入了解裝置註冊

Intune 支援下列裝置平台：

[!INCLUDE[mdm-supported-devices](../includes/mdm-supported-devices.md)]

啟用裝置管理的需求取決於您想要管理的平台。
- **Android** 行動裝置可讓使用者使用從 Google Play 取得的[公司入口網站應用程式來註冊](/intune/deploy-use/set-up-android-management-with-microsoft-intune)。 在 Intune 中無需進行其他設定。
- [**iOS 與 Mac OS X** 的設定需求](/intune/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune)
- [**Windows Phone** 的設定需求](/intune/deploy-use/set-up-windows-phone-management-with-microsoft-intune)。

<!--- ## Verify enrollment--->
<!--- START HERE

### iOS and Mac OS X
Install the **Microsoft Intune Company Portal** app from Microsoft Corporation available in the App Store and sign in with Intune user credentials added above. View **Enrolled devices** to add your device.



### Windows Phone 8.1
Users install the **Company Portal** app from Microsoft Corporation, available in the Windows Phone store, and sign in with the Intune user credentials added above.  View **Enrolled devices** to add your device.

## Install the previously deployed app
Open the Company Portal on the mobile device, choose **Apps**, and then install **Microsoft Skype**.--->



## <a name="next-steps"></a>後續步驟
[建立群組來組織使用者和裝置](get-started-with-a-30-day-trial-of-microsoft-intune-step-3.md)



<!--HONumber=Nov16_HO5-->


