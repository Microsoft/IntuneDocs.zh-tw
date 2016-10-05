---
title: "部署 Lookout for Work 應用程式 | Microsoft Intune"
description: "設定及部署適用於 Android 的 Lookout for Work 應用程式。"
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c4d05b9ba7249e4068d21480b1c9db342277757e
ms.openlocfilehash: 687a102ccb34cb7acfaab1e8a1d4b67cb54b9e92


---

# 設定及部署 Lookout for Work 應用程式
本文說明如何為已註冊且執行 Android 4.1 或更新版本的裝置，設定和部署 Lookout for Work 應用程式。

* **步驟 1：**在 [Microsoft Intune 系統管理員主控台](https://manage.microsoft.com)中，移至 [應用程式]，然後選擇 [新增應用程式]。   
* **步驟 2**︰在發行者的 [軟體安裝程式] 頁面上，選擇 [外部連結]，然後指定下列 URL：https://play.google.com/store/apps/details?id=com.lookout.enterprise
>[!NOTE]
>請勿按下要求 Managed Browser 的方塊。

* **步驟 3**︰在 [軟體描述] 頁面上，填入下列資訊：
  * **發行者**︰Lookout 行動安全性
  * **名稱**︰Lookout for Work
  * **描述**︰Lookout 提供最佳行動裝置威脅保護，以確保您的裝置安全無虞。 在裝置上安裝 Lookout 應用程式時，該應用程式可保護您的裝置免受威脅，並於發現任何威脅時，通知您及公司的系統管理員。
  * **類別**：電腦管理
* **步驟 4**︰成功完成時，您會看到 [上傳資料至 Microsoft Intune 已順利完成] 的訊息。

當您按一下 Intune 主控台上的 [應用程式] 時，即可在清單中看到 Lookout for Work 應用程式。![在清單中顯示 Lookout for Work 應用程式之 Intune 管理主控台 [應用程式] 頁面的螢幕擷取畫面](../media/mtp/lookout-app-listed-intune-console.png)

**若要將應用程式部署給使用者**，請選取以上畫面中所示的 Lookout for Work 應用程式，然後選取 [管理部署]。

您必須選取已在 Lookout MTP 主控台中新增至 [Enrollment Management] (註冊管理) 選項的相同使用者。  如需將使用者群組新增至 Lookout MTP 的資訊，請參閱[設定訂用帳戶使用 Lookout MTP](set-up-your-subscription-with-lookout-mtp#configure-your-subscription-with-lookout-mtp) 一節中的步驟 3。
>[!IMPORTANT]
> Intune 應用程式部署精靈無法察覺 Azure AD 使用者群組，而會改用 Intune 使用者群組，因此您必須依據 Lookout MTP 主控台中已註冊的 Azure AD 使用者群組，來建立一個 Intune 使用者群組 (如[本主題](plan-your-user-and-device-groups.md)中所述)。

選擇 [必要安裝] 選項，要求必須在使用者裝置上安裝 Lookout 應用程式。


針對部署選取 [必要安裝] 選項時，Intune 會將 Lookout for Work 應用程式發送至裝置。   

當使用者在裝置上開啟 Lookout for Work 時，系統會提示他們啟動應用程式，並選擇 [使用 Azure Active Directory 登入] 選項。 您可以在下列主題中，找到使用者流程的詳細逐步解說：

* [系統提示在您的 Android 裝置上安裝 Lookout for Work](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [您必須解決 Lookout for Work 在 Android 裝置上找到的威脅](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## 後續步驟
* [啟用相容性原則中的裝置威脅保護規則](enable-device-threat-protection-rule-in-compliance-policy.md)



<!--HONumber=Sep16_HO3-->


