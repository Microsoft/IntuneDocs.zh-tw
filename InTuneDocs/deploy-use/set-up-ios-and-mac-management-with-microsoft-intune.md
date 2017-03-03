---
title: "設定 iOS 和 Mac 管理 | Microsoft Docs"
description: "使用 Microsoft Intune 來支援 iOS 裝置 (包括 iPad、iPhone 及 Mac OS X 裝置) 的行動裝置管理 (MDM)。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 11/17/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: afca2af0b07b939adc66c8804f04a1125e12001b
ms.openlocfilehash: 9c71a83f9514187753360fa9c2085584d1b76711


---

# <a name="set-up-ios-and-mac-device-management"></a>設定 iOS 和 Mac 裝置管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 可啟用 iPad、iPhone 和 macOS 裝置的行動裝置管理 (MDM)，且可提供使用者對公司電子郵件和應用程式的存取。 Intune 需要 Apple Push Notification Service (APNs) 憑證，才能管理 iOS 和 Mac 裝置。 將憑證新增到 Intune 之後，使用者就可以安裝公司入口網站應用程式來註冊其裝置，或者系統管理員可以設定[公司擁有的 iOS 裝置管理](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)。

1.  **設定 Intune**<br>
    如果尚未這麼做，請將[行動裝置管理授權單位](prerequisites-for-enrollment.md#step-2-set-mdm-authority)設定為 **Microsoft Intune** 並設定 MDM，為行動裝置管理做好準備。

2.  **取得憑證簽署要求**<br>
    以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，並移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS 和 Mac OS X] &gt; [上傳 APNs 憑證]，然後選擇 [下載 APNs 憑證要求]。 在本機儲存憑證簽署要求 (.csr) 檔案。 .csr 檔案用來向 Apple Push Certificates Portal 要求信任關係憑證。

    ![上傳 APNs 憑證對話方塊](../media/Intune-iOS-enrollment-with-apns.png)

3.  **取得 Apple 推送通知服務憑證**<br>
    前往 [Apple Push Certificates 入口網站](http://go.microsoft.com/fwlink/?LinkId=269844)，然後使用您公司的 Apple ID 登入，以使用 .csr 檔案建立 APNs 憑證。 在 Apple Push Certificates 入口網站上選擇 [上傳] 之後，您會收到一個無法用於 APNs 的 .json 檔案。 完成下載，並回到 Apple Push Certificates 入口網站的 「Certificates for Third-Party Servers」 (協力廠商伺服器的憑證)，然後選擇 [下載]。

    下載 APNs (.pem) 憑證，並將該檔案儲存在本機。

    > [!NOTE]
    > 每年您都需要更新 (不是取代) 此 APNs 憑證。 使用相同的這個 Apple 識別碼登入 Apple Push Certificate 入口網站來更新憑證，然後使用本主題中的相同指示下載憑證，再將它上傳至 Intune。

4.  **將 APNs 憑證新增至 Intune**<br>
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS 和 Mac OS X] &gt; [上傳 APNs 憑證]，然後選擇 [上傳 APNs 憑證]。 移至憑證 (.pem) 檔案，並選擇 [開啟]，然後輸入您的 [Apple ID]。 使用 APNs 憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。

5.  **告訴使用者如何註冊其裝置來存取公司資源。**

    如需終端使用者註冊指示，請參閱[在 Intune 註冊 iOS 裝置](../enduser/enroll-your-device-in-intune-ios.md)和[在 Intune 註冊 macOS 裝置](../enduser/enroll-your-device-in-intune-macos.md)。 註冊程序會告知使用者，他們能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

    如需其他使用者工作的資訊，請參閱下列文章：
    - [使用 Microsoft Intune 之使用者體驗的相關資源](how-to-educate-your-end-users-about-microsoft-intune.md)
    - [iOS 與 Mac 裝置的使用者指南](../enduser/using-your-ios-or-macOS-device-with-intune.md)

如果您的公司或組織為使用者購買 iOS 裝置，這些裝置也可以註冊為[公司擁有的 iOS 裝置](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)以納入管理。

### <a name="see-also"></a>另請參閱
[使用 Microsoft Intune 的註冊必要條件](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO3-->


