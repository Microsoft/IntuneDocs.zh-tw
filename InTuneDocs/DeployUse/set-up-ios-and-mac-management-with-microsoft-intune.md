---
# required metadata

title: 使用 Microsoft Intune 設定 iOS 和 Mac 管理 | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 設定 iOS 和 Mac 裝置管理
Microsoft Intune 可讓您為 iOS 和 Mac OS X 裝置註冊啟用 BYOD (「攜帶您自己的裝置」)，使 iPhone、iPad 和 Mac 使用者能夠存取公司電子郵件和應用程式。 註冊之後，使用者可以安裝 Intune 公司入口網站應用程式，並使用 Intune 管理主控台，透過原則將他們的裝置設為目標。

管理 iOS 裝置必須能夠與 Intune 通訊，您才能使用 Intune 管理裝置。 Apple 要求匯入 Apple 推播通知服務 (APNs) 憑證，以便與 Intune 建立信任關係。

1.  **設定 Intune**<br>
    如果尚未這麼做，請將[行動裝置管理授權單位](get-ready-to-enroll-devices-in-microsoft-intune.md#set-mobile-device-management-authority)設定為 Microsoft Intune 並設定 MDM，為行動裝置管理做好準備。

2.  **取得憑證簽署要求**<br>
    以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS 和 Mac OS X] &gt; [上傳 APNs 憑證]，然後按一下 [下載 APNs 憑證要求]。 在本機儲存憑證簽署要求 (.csr) 檔案。 .csr 檔案用來向 Apple Push Certificates Portal 要求信任關係憑證。

    ![上傳 APNs 憑證對話方塊](../media/Intune-iOS-enrollment-with-apns.png)

3.  **取得 Apple Push Notification service 憑證**<br>
    前往 [Apple Push Certificates 入口網站](http://go.microsoft.com/fwlink/?LinkId=269844) ，然後使用您公司的 Apple ID 登入，以使用 .csr 檔案建立 APNs 憑證。 在 Apple Push Certificate 入口網站上按一下 [上傳] 之後，您會收到一個無法用於 APNs 的 .json 檔案。 完成下載，回到 Apple Push Certificate 入口網站的 [協力廠商伺服器的憑證]，按一下 [下載]

    下載 APNs (.pem) 憑證，並將該檔案儲存在本機。 未來必須使用這個 Apple 識別碼來更新 APNs 憑證。

4.  **將 APNs 憑證新增至 Intune**<br>
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS 和 Mac OS X] &gt; [上傳 APNs 憑證]，按一下 [上傳 APNs 憑證]. [瀏覽] 找出憑證 (.pem) 檔案，按一下 [開啟]，然後輸入您的 [Apple ID]。 使用 APNs 憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。 告訴使用者如何使用公司入口網站存取公司資源

5.  **您的使用者必須知道如何註冊其裝置，以及開始管理之後會發生的情況。**<br>
    要告訴使用者之關於使用 Microsoft Intune 的事項 [如果您的公司或組織為使用者購買 iOS 裝置，這些裝置也可以註冊為[公司擁有的 iOS 裝置](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)以納入管理](what-to-tell-your-end-users-about-using-microsoft-intune.md)

另請參閱

### 準備在 Microsoft Intune 中註冊裝置
[Get ready to enroll devices in Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->


