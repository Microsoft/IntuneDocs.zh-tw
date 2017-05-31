---
title: "使用應用程式保護原則的 iOS 應用程式 | Microsoft Docs"
description: "本主題說明當 iOS 應用程式交由應用程式保護原則管理時的行為。"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 92a91fab353c78c751ae5eb25c9853df5cbcfe53
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017


---

# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>當 iOS 應用程式交由應用程式保護原則管理時的行為

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

 針對已套用應用程式保護原則的應用程式，本主題說明使用者的使用體驗。 只有在工作環境中使用應用程式時，才會套用應用程式保護原則；例如，當使用者使用工作帳戶來存取應用程式的情況，或是存取公司商務用 OneDrive 地點中所儲存檔案的情況。

##  <a name="access-apps"></a>存取應用程式

如果裝置**未註冊於 Intune 中**，會要求使用者在第一次使用應用程式時重新啟動應用程式。 必須先重新啟動，才會將應用程式保護原則套用到應用程式。 

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

針對**在 Intune 中註冊以進行管理**的裝置，使用者會看到其應用程式現在已受管理的訊息。

##  <a name="use-apps-with-multi-identity-support"></a>使用具有多重身分識別支援的應用程式

當應用程式保護原則只有在工作環境中使用應用程式時才會套用，支援多重身分識別的應用程式讓您能夠使用不同的帳戶 (工作和個人) 來存取相同的應用程式。  

例如，使用者會在存取工作資料時看到 PIN 提示。 針對 **Outlook 應用程式**，使用者在啟動應用程式時，系統會提示使用者輸入 PIN。 針對 **OneDrive 應用程式**，使用者輸入工作帳戶時，系統會提示使用者輸入 PIN。  針對 Microsoft **Word**、**PowerPoint** 和 **Excel**，當使用者存取公司商務用 OneDrive 位置中所儲存的文件時，系統會提示使用者輸入 PIN。

- 深入了解支援 Intune 的 [MAM 和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

應用程式保護原則只適用於工作環境。 因此，應用程式可能因工作環境或個人環境而有不同的行為。

##  <a name="manage-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

Intune 僅支援將應用程式保護原則部署到每個裝置的一個使用者帳戶。

* 根據您所使用的應用程式，可能會封鎖裝置上的第二個使用者。 在所有情況下，只有套用應用程式保護原則的第一位使用者會受原則影響。
  * **Microsoft Word**、**Excel** 及 **PowerPoint** 不會封鎖第二個使用者帳戶，但第二個使用者帳戶不會受應用程式保護原則影響。  

  * 若為 **OneDrive** 和 **Outlook 應用程式**，您只能使用一個工作帳戶。 您無法針對這些應用程式新增多個工作帳戶。 不過，您可以在裝置上移除使用者並新增不同的使用者。

* 若裝置在應用程式保護原則部署之前已有多個使用者帳戶，則應用程式保護原則所部署的第一個帳戶將由 Intune 應用程式保護原則管理。


閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。**X 公司**關聯的帳戶將得到應用程式保護原則，Y 公司關聯的帳戶則否。如果您希望 Y 公司關聯的使用者帳戶受應用程式保護原則管理，您必須移除與 X 公司關聯的使用者帳戶。

### <a name="add-a-second-account"></a>新增第二個帳戶

如果您使用 iOS 裝置，則嘗試在該裝置上新增第二個工作帳戶時，會看到封鎖訊息。 將會顯示帳戶，接著您可以選擇想要移除的帳戶。

## <a name="next-steps"></a>後續步驟
[當 Android 應用程式交由應用程式保護原則管理時的行為](user-experience-for-mam-enabled-android-apps-with-microsoft-intune.md)
### <a name="see-also"></a>請參閱
[使用 Microsoft Intune 建立及部署行動應用程式管理原則](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)

