---
title: "設定 iOS 和 Mac 管理 | Microsoft Intune"
description: "使用 Microsoft Intune 來支援 iOS 裝置 (包括 iPad、iPhone 及 Mac OS X 裝置) 的行動裝置管理 (MDM)。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 07/20/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc451224-1372-4b84-b641-cfa67cb3849b
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b3f6323912707d56d23380217a07e6474593d83f
ms.openlocfilehash: f93f7bfe99e878691dccd24c124a781c8607e7c6


---

# 設定 iOS 和 Mac 裝置管理
如需設定 iOS 或 Mac 裝置的說明，請參閱[透過 Intune 使用 iOS 或 Mac OS X 裝置](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)。

Intune 可啟用 iPad、iPhone 和 Mac OS X 裝置的行動裝置管理 (MDM)，且可提供使用者對公司電子郵件和應用程式的存取。 Intune 需要 Apple Push Notification Service (APNs) 憑證，才能管理 iOS 和 Mac 裝置。 將憑證新增到 Intune 之後，使用者就可以安裝公司入口網站應用程式來註冊其裝置，或者系統管理員可以設定[公司擁有的 iOS 裝置管理](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)。

1.  **設定 Intune**<br>
    如果尚未這麼做，請將[行動裝置管理授權單位](prerequisites-for-enrollment.md#set-mobile-device-management-authority)設定為 **Microsoft Intune** 並設定 MDM，為行動裝置管理做好準備。

2.  **取得憑證簽署要求**<br>
    以系統管理使用者身分開啟 [Microsoft Intune 管理主控台](http://manage.microsoft.com)，並移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS 和 Mac OS X] &gt; [上傳 APNs 憑證]，然後選擇 [下載 APNs 憑證要求]。 在本機儲存憑證簽署要求 (.csr) 檔案。 .csr 檔案用來向 Apple Push Certificates Portal 要求信任關係憑證。

    ![上傳 APNs 憑證對話方塊](../media/Intune-iOS-enrollment-with-apns.png)

3.  **取得 Apple Push Notification service 憑證**<br>
    前往 [Apple Push Certificates 入口網站](http://go.microsoft.com/fwlink/?LinkId=269844)，然後使用您公司的 Apple ID 登入，以使用 .csr 檔案建立 APNs 憑證。 在 Apple Push Certificates 入口網站上選擇 [上傳] 之後，您會收到一個無法用於 APNs 的 .json 檔案。 完成下載，並回到 Apple Push Certificates 入口網站的 [Certificates for Third-Party Servers] (協力廠商伺服器的憑證)，然後選擇 [下載]。

    下載 APNs (.pem) 憑證，並將該檔案儲存在本機。 稍後必須使用這個 Apple ID 來更新 APNs 憑證。

4.  **將 APNs 憑證新增至 Intune**<br>
    在 [Microsoft Intune 管理主控台](http://manage.microsoft.com)中，移至 [系統管理] &gt; [行動裝置管理] &gt; [iOS 和 Mac OS X] &gt; [上傳 APNs 憑證]，然後選擇 [上傳 APNs 憑證]。 移至憑證 (.pem) 檔案，並選擇 [開啟]，然後輸入您的 [Apple ID]。 使用 APNs 憑證，透過將原則推送到已註冊的行動裝置，Intune 即可註冊和管理 iOS 裝置。

5.  **告訴使用者如何使用公司入口網站存取公司資源**<br>
    您的使用者必須知道如何註冊其裝置，以及開始管理之後會發生的情況。
    - [要告訴使用者之關於使用 Microsoft Intune 的事項](what-to-tell-your-end-users-about-using-microsoft-intune.md)
    - [iOS 與 Mac 裝置的終端使用者指南](../enduser/using-your-ios-or-mac-os-x-device-with-intune.md)

如果您的公司或組織為使用者購買 iOS 裝置，這些裝置也可以註冊為[公司擁有的 iOS 裝置](enroll-corporate-owned-ios-devices-in-microsoft-intune.md)以納入管理。

### 另請參閱
[使用 Microsoft Intune 的註冊必要條件](prerequisites-for-enrollment.md)



<!--HONumber=Oct16_HO3-->


