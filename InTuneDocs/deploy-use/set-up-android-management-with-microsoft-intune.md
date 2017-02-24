---
title: "設定 Android 管理 | Microsoft Docs"
description: "使用 Microsoft Intune 來支援 Android 和 KNOX Standard 裝置的行動裝置管理 (MDM)。"
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dbe5cad1-3e0d-41a9-966b-738156089700
ms.reviewer: lacranda
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6b99854e17e00a0dd0f91fa82fd1b79d1dfe5663
ms.openlocfilehash: 8e2588e2bb0537877f0164bc996fa973f25ea4dd


---

# <a name="set-up-android-device-management"></a>設定 Android 裝置管理

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

身為 Intune 系統管理員，您可以從公司入口網站啟用 Android 裝置的管理，包括 Samsung Knox Standard 裝置。 使用者接著可以使用 Google Play 提供的公司入口網站應用程式來註冊其裝置。

Android 裝置預設可以在 Intune 中註冊。 若要阻擋註冊 Android 裝置，請以系統管理員認證登入 [Microsoft Intune 管理員入口網站](http://manage.microsoft.com)。 選擇 [管理員] > [行動裝置管理] > [註冊規則]，然後清除 [允許 Android 裝置] 核取方塊。

1.  **設定 Intune**<br>
    如果尚未這麼做，請將[行動裝置管理授權單位](prerequisites-for-enrollment.md#step-2-set-mdm-authority)設定為 **Microsoft Intune** 並設定 MDM，為行動裝置管理做好準備。

2.  **啟用 Android 註冊**<br>
    啟用 Android 行動裝置註冊並不需要在 Intune 主控台中進行任何其他設定。

3.  **告訴使用者如何註冊其裝置來存取公司資源。**

    如需使用者註冊指示，請參閱[在 Intune 註冊 Android 裝置](../enduser/enroll-your-device-in-intune-android.md)。 註冊程序會告知使用者，他們能獲得什麼，以及 IT 系統管理員可以和無法在其裝置上看到什麼。

    如需其他使用者工作的資訊，請參閱下列文章：
  - [使用 Microsoft Intune 之使用者體驗的相關資源](how-to-educate-your-end-users-about-microsoft-intune.md)
  - [適用於 Android 裝置的使用者指南](../enduser/using-your-android-device-with-intune.md)

由於中國沒有 Google Play 商店，因此 Android 裝置必須從中文應用程式市集取得公司入口網站。 適用於 Android 的公司入口網站應用程式可在下列市集下載：
* [百度](https://go.microsoft.com/fwlink/?linkid=836946)
* [華為](https://go.microsoft.com/fwlink/?linkid=836948)
* [騰訊](https://go.microsoft.com/fwlink/?linkid=836949)
* [豌豆莢](https://go.microsoft.com/fwlink/?linkid=836950)
* [小米應用商店](https://go.microsoft.com/fwlink/?linkid=836947)

適用於 Android 的公司入口網站應用程式會使用 Google Play 服務來與 Microsoft Intune 服務通訊。 由於中國尚無法使用 Google Play 服務，因此執行下列任何工作可能需要多達 8 小時才能完成。 

|Intune 管理主控台| 適用於 Android 的 Intune 公司入口網站應用程式 |Intune 公司入口網站|   
|---|---|---|
|完整抹除| 移除遠端裝置| 移除裝置 (本機和遠端)|
|選擇性抹除| 重設裝置| 重設裝置|
|新的或更新的應用程式部署| 安裝可用的企業營運應用程式| 裝置密碼重設|
|遠端鎖定|||
|密碼重設|||

### <a name="see-also"></a>請參閱
[Microsoft Intune 中註冊裝置的必要條件](prerequisites-for-enrollment.md)



<!--HONumber=Feb17_HO3-->


