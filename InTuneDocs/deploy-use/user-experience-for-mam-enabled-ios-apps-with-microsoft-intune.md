---
title: "使用 MAM 原則的 iOS 應用程式 | Microsoft Intune"
description: "本主題描述當您的 iOS 應用程式由行動應用程式管理原則管理時會發生的情況。"
keywords: 
author: NathBarn
ms.author: nathbarn
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
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 3aa6728036ff66ea489176063af2d136bef4c7cc


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-mam-policies"></a>當 iOS 應用程式由 MAM 原則管理時會發生的情況
 本主題描述使用行動存取管理 (MAM) 原則之應用程式的使用者體驗。 只有在工作內容中使用應用程式時，才會套用 MAM 原則：例如，當使用者使用工作帳戶來存取應用程式，或存取公司商務用 OneDrive 地點中所儲存的檔案。

##  <a name="access-apps"></a>存取應用程式

如果裝置**未註冊於 Intune 中**，會要求使用者在第一次使用應用程式時重新啟動應用程式。  必須重新啟動，才能將 MAM 原則套用到應用程式。 下列 Skype 應用程式的螢幕擷取畫面說明這個重新啟動要求：


![顯示 PIN 提示的 iOS 裝置螢幕擷取畫面](../media/appmanagement/iOS_AppPINPrompt.png)

針對**在 Intune 中註冊以進行管理**的裝置，使用者會看到其應用程式現在已受管理的訊息：

![顯示應用程式現在已受您的公司管理並附有 PIN 提示之訊息的 iOS 裝置螢幕擷取畫面](../media/appmanagement/ios-managed-devices-pin-prompt.png)

##  <a name="use-apps-with-multi-identity-support"></a>使用具有多重身分識別支援的應用程式

MAM 原則只會套用至工作環境。 因此，應用程式可能因工作環境或個人環境而有不同的行為。

 例如，使用者會在存取工作資料時看到 PIN 提示。 針對 **Outlook 應用程式**，使用者在啟動應用程式時，系統會提示使用者輸入 PIN。 針對 **OneDrive 應用程式**，使用者輸入工作帳戶時，系統會提示使用者輸入 PIN。  針對 Microsoft **Word**、**PowerPoint** 和 **Excel**，當使用者存取公司商務用 OneDrive 位置中所儲存的文件時，系統會提示使用者輸入 PIN。

##  <a name="manage-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

Intune 僅支援將 MAM 原則部署到每個裝置的一個使用者帳戶。

* 根據您所使用的應用程式，可能會封鎖裝置上的第二個使用者。 不過，在所有情況下，只有取得 MAM 原則的第一個使用者會受原則影響。
  * **Microsoft Word**、**Excel** 和 **PowerPoint** 不會封鎖第二個使用者帳戶，但第二個使用者帳戶不會受 MAM 原則影響。  

  * 若為 **OneDrive** 和 **Outlook 應用程式**，您只能使用一個工作帳戶。 您無法針對這些應用程式新增多個工作帳戶。 不過，您可以在裝置上移除使用者並新增不同的使用者。

* 如果裝置在 MAM 原則部署之前存在多個使用者帳戶，則 MAM 原則部署到的第一個帳戶會受 Intune MAM 原則管理。


閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在每個公司有一個工作帳戶，且兩者都使用 Intune 來部署 MAM 原則。 **X 公司**在 **Y 公司****之前**部署 MAM 原則。**X 公司**相關聯的帳戶將得到 MAM 原則，Y 公司的相關聯帳戶則否。如果您希望 Y 公司相關聯的使用者帳戶受 MAM 原則管理，您必須移除與 X 公司相關聯的使用者帳戶。

### <a name="add-a-second-account"></a>新增第二個帳戶

如果您使用 iOS 裝置，則嘗試在該裝置上新增第二個工作帳戶時，會看到封鎖訊息。 將會顯示帳戶，接著您可以選擇想要移除的帳戶。

![包含封鎖訊息和 [是] 與 [否] 選項之對話方塊的螢幕擷取畫面](../media/AppManagement/iOS_SwitchUser.PNG)
## <a name="next-steps"></a>後續步驟
[當 Android 應用程式由 MAM 原則管理時會發生的情況](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 建立及部署行動應用程式管理原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


