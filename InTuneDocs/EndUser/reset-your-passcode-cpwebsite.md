---
title: "從公司入口網站重設裝置密碼 | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
ms.author: stabar
manager: angrobe
ms.date: 09/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2aea845bc00c153f070e04abb67582a5d5a726ca
ms.openlocfilehash: 47b36616f7a8ee23d4d47b41a1db2c41c185c6f5


---


# 從公司入口網站重設裝置密碼

如果您在 Intune 中註冊的裝置遺失裝置 PIN 或密碼，您可以使用[公司入口網站](http://portal.manage.microsoft.com)重設密碼。 您可以使用公司入口網站來管理已在 Intune 註冊的電腦和裝置，而且就像使用公司入口網站應用程式一樣，可讓您執行大部分同樣的工作。

> [!NOTE]
> 公司入口網站上可能不會顯示 [重設密碼] 按鈕，這是由 IT 系統管理員設定 Intune 的方式決定。 Windows 8.1 裝置不支援密碼重設。

若要重設密碼：

1.  開啟 [公司入口網站](http://portal.manage.microsoft.com)，然後選擇您想要重設密碼的裝置。

2.  選擇 [重設密碼]。

    ![裝置詳細資料與 [重設密碼] 按鈕](./media/iwp-screen-with-all-options.png)

3.  選擇 [登出]，然後以工作或學校認證登入。 您必須在五分鐘內登入。

    ![重設訊息與 [登出] 按鈕](./media/iwp-2-sign-out.png)

4.  選擇 [重設密碼]。

    ![說明當您重設密碼時所發生情況的訊息](./media/iwp-3-tap-reset-passcode-after-signin.png)

    檢查資料表查看 [重設密碼] 在您裝置上的運作方式。

    |平台|支援|
    |------------|-----------|
    |Android|建立暫時英數字元密碼。|
    |iOS|從裝置移除密碼，但不建立暫時密碼。 如果使用 Touch ID，裝置上就必須再設定一次，因為當您重設密碼時就會移除它。|
    |Windows 10 (僅限行動裝置)|建立暫時英數字元密碼。 支援 Windows Hello。|
    |Windows Phone 8.1|建立暫時數值密碼。|
    解除鎖定裝置後，您可以移至裝置的 [設定] 設定新密碼。

5.  解除鎖定裝置，然後移至裝置的 **[設定]** 設定新密碼或變更暫時密碼。

    若要查看密碼重設成功的確認通知，請按一下公司入口網站右上方的的通知旗標。

是否仍需要協助？ 請連絡 IT 系統管理員。 如需其連絡資訊，請查看[公司入口網站](http://portal.manage.microsoft.com)。



<!--HONumber=Oct16_HO3-->


