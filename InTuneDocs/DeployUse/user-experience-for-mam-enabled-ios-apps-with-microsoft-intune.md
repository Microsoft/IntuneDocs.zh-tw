---
title: "使用 MAM 原則的 iOS 應用程式 | Microsoft Intune"
description: "本主題描述當您的 iOS 應用程式由行動應用程式管理原則管理時會發生的情況。"
keywords: 
author: karthikaraman
ms.author: karaman
manager: angrobe
ms.date: 10/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 389daf0ed39fa2cd4b2e5d6e52cbd6809a568c9e
ms.openlocfilehash: 3f9d9c7cafcdac0db21e5ba35f713fe630c65b99


---

# 當 iOS 應用程式由 MAM 原則管理時會發生的情況
 本主題描述使用 MAM 原則之應用程式的使用者經驗。 只有在工作內容中使用應用程式時，才會套用行動應用程式管理 (MAM) 原則，例如，使用工作帳戶來存取應用程式，或存取公司 OneDrive 辦公室地點中所儲存的檔案。
##  存取應用程式

如果裝置**未註冊於 Intune 中**，會要求使用者在第一次使用應用程式時重新啟動應用程式。  必須重新啟動，才能將 MAM 原則套用到應用程式。 下列螢幕擷取畫面使用 Skype 應用程式來說明這點︰


![顯示 PIN 提示之 iOS 裝置的螢幕擷取畫面](../media/appmanagement/iOS_AppPINPrompt.png)

針對**在 Intune 中註冊以進行管理**的裝置，使用者會看到現在已管理其應用程式的訊息：

![顯示公司訊息所管理並具有 PIN 提示之 iOS 裝置的螢幕擷取畫面](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  使用多重身分識別支援的應用程式

使用應用程式時，只會將 MAM 原則套用到工作內容，因此，根據內容 (工作或個人)，您可能會看到不同的應用程式行為。  

針對支援多身分識別的應用程式，只有在使用者於工作內容中使用應用程式時，Intune 才會套用 MAM 原則。  例如，使用者會在存取工作資料時取得 PIN 提示。  針對 **Outlook 應用程式**，系統會提示使用者在啟動應用程式時輸入 PIN。 針對 **OneDrive 應用程式**，這發生在使用者輸入工作帳戶時。  針對 Microsoft **Word**、**PowerPoint* 和 **Excel**，這發生於使用者存取公司商務用 OneDrive 位置中所儲存的文件時。
##  管理裝置上的使用者帳戶

Intune 僅支援將 MAM 原則部署到每個裝置的一個使用者帳戶。

* 根據您所使用的應用程式，可能或不會封鎖裝置上的第二位使用者。 不過，在所有情況下，只有取得 MAM 原則的第一個使用者會受原則影響。
  * **Microsoft Word**、**Excel** 和 **PowerPoint** 不會封鎖第二個使用者帳戶，但第二個使用者帳戶不會受 MAM 原則影響。  

  * 若為 **OneDrive 和 Outlook 應用程式**，您只能使用一個工作帳戶。  在這些應用程式中新增多個工作帳戶會遭到封鎖。  不過，您可以在裝置上移除使用者並新增不同的使用者。

* 如果裝置在 MAM 原則部署之前結束多個使用者帳戶，則 MAM 原則部署到的第一個帳戶會受 Intune MAM 原則影響。


閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在每個公司有一個工作帳戶，且兩者都使用 Intune 來部署 MAM 原則。 **X 公司**在 **Y 公司****之前**部署 MAM 原則。**X 公司**相關聯的帳戶將得到 MAM 原則，Y 公司的相關聯帳戶則否。如果您希望 Y 公司相關聯的使用者帳戶受 MAM 原則管理，您必須移除與 X 公司相關聯的使用者帳戶。
### 新增第二個帳戶

如果您使用 iOS 裝置，則嘗試在同一部裝置上新增第二個工作帳戶時，會看到封鎖訊息。  將會顯示帳戶，而且您可以選擇想要移除的帳戶。

![包含封鎖訊息和 [是] 與 [否] 選項之對話方塊的螢幕擷取畫面](../media/AppManagement/iOS_SwitchUser.PNG)
## 後續步驟
[當 Android 應用程式由 MAM 原則管理時會發生的情況](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### 請參閱
[使用 Microsoft Intune 建立及部署行動應用程式管理原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO3-->


