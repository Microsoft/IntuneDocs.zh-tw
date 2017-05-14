---
title: "使用應用程式保護原則的 iOS 應用程式 | Intune Azure Preview"
titleSuffix: Intune Azure preview
description: "Intune Azure 預覽版︰本主題說明當 iOS 應用程式交由應用程式保護原則管理時的行為。"
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 5a4ce6d6248378ba48cddeaefb941c139dd990f6
ms.contentlocale: zh-tw
ms.lasthandoff: 02/18/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>當 iOS 應用程式交由應用程式保護原則管理時的行為
[!INCLUDE[azure_preview](../includes/azure_preview.md)]本主題說明使用者在使用應用程式保護原則所管理之應用程式時的體驗。 僅當應用程式在工作內容中使用時 (例如使用工作帳戶存取應用程式，或存取公司 OneDrive 上公司位置內儲存的檔案)，才會套應用程式保護原則。
##  <a name="accessing-apps"></a>存取應用程式

如果裝置**未註冊於 Intune 中**，會要求使用者在第一次使用應用程式時重新啟動應用程式。  必須先重新啟動，才會將應用程式保護原則套用到應用程式。 下列螢幕擷取畫面使用 Skype 應用程式來說明這點︰


![顯示 PIN 提示之 iOS 裝置的螢幕擷取畫面](../media/ios-pin-prompt.png)

針對**在 Intune 中註冊以進行管理**的裝置，使用者會看到現在已管理其應用程式的訊息：

![顯示公司訊息所管理並具有 PIN 提示之 iOS 裝置的螢幕擷取畫面](../media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>使用多重身分識別支援的應用程式

使用應用程式時，因為只會對工作內容套用應用程式保護原則，所以原則的行為會隨內容 (工作或個人) 而不同。  

對於支援多種身分識別的應用程式，Intune 只會在使用者於工作內容中使用應用程式時，才套用應用程式保護原則。  例如，使用者會在存取工作資料時取得 PIN 提示。  針對 **Outlook 應用程式**，系統會提示使用者在啟動應用程式時輸入 PIN。 針對 **OneDrive 應用程式**，這發生在使用者輸入工作帳戶時。  針對 Microsoft **Word**、**PowerPoint* 和* *Excel**，這發生於使用者存取公司商務用 OneDrive 位置中所儲存的文件時。
##  <a name="managing-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

Intune 只允許將應用程式保護原則部署到每部裝置上的一個使用者帳戶。

* 根據您所使用的應用程式，可能或不會封鎖裝置上的第二位使用者。 在所有情況下，只有套用應用程式保護原則的第一位使用者會受原則影響。
  * **Microsoft Word**、**Excel** 及 **PowerPoint** 不會封鎖第二個使用者帳戶，但第二個使用者帳戶不會受應用程式保護原則影響。  

  * 若為 **OneDrive 和 Outlook 應用程式**，您只能使用一個工作帳戶。  在這些應用程式中新增多個工作帳戶會遭到封鎖。  不過，您可以在裝置上移除使用者並新增不同的使用者。

* 若裝置在應用程式保護原則部署之前已有多個使用者帳戶，則應用程式保護原則所部署的第一個帳戶將由 Intune 應用程式保護原則管理。


閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。因此將會對 **X 公司**所關聯的帳戶套用應用程式保護原則，而不會對 Y 公司所關聯的帳戶套用。若希望 Y 公司所關聯的使用者帳戶也能交由應用程式保護原則管理，必須移除 X 公司所關聯的使用者帳戶。
### <a name="adding-a-second-account"></a>新增第二個帳戶

如果您使用 iOS 裝置，則嘗試在同一部裝置上新增第二個工作帳戶時，會看到封鎖訊息。  將會顯示帳戶，而且您可以選擇想要移除的帳戶。

![包含封鎖訊息和 [是] 與 [否] 選項之對話方塊的螢幕擷取畫面](../media/ios-switch-user.PNG)

## <a name="next-steps"></a>後續步驟
[當 Android 應用程式交由應用程式保護原則管理時的行為](app-protection-enabled-android-apps.md)
### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 建立及部署應用程式保護原則](app-protection-policies.md)

