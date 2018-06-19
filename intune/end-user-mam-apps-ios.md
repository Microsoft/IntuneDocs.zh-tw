---
title: 使用應用程式保護原則的 iOS 應用程式
description: 本主題說明當 iOS 應用程式交由應用程式保護原則管理時的行為。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 955120228289da3bac7cf013955effeee0cd7579
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023422"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>當 iOS 應用程式交由應用程式保護原則管理時的行為

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

 針對已套用應用程式保護原則的應用程式，本主題說明使用者的使用體驗。 只有在工作環境中使用應用程式時，才會套用應用程式保護原則；例如，當使用者使用工作帳戶來存取應用程式的情況，或是存取公司商務用 OneDrive 地點中所儲存檔案的情況。

##  <a name="access-apps"></a>存取應用程式

如果裝置**未註冊於 Intune 中**，會要求使用者在第一次使用應用程式時重新啟動應用程式。 必須先重新啟動，才會將應用程式保護原則套用到應用程式。

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

針對**在 Intune 中註冊以進行管理**的裝置，使用者會看到其應用程式現在已受管理的訊息。

##  <a name="use-apps-with-multi-identity-support"></a>使用具有多重身分識別支援的應用程式

當應用程式保護原則只有在工作環境中使用應用程式時才會套用，支援多重身分識別的應用程式讓您能夠使用不同的帳戶 (工作和個人) 來存取相同的應用程式。  

例如，使用者會在存取工作資料時看到 PIN 提示。 針對 **Outlook 應用程式**，使用者在啟動應用程式時，系統會提示使用者輸入 PIN。 針對 **OneDrive 應用程式**，使用者輸入工作帳戶時，系統會提示使用者輸入 PIN。  針對 Microsoft **Word**、**PowerPoint** 和 **Excel**，當使用者存取公司商務用 OneDrive 位置中所儲存的文件時，系統會提示使用者輸入 PIN。

- 深入了解支援 Intune 的[應用程式保護和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。

應用程式保護原則只適用於工作環境。 因此，應用程式可能因工作環境或個人環境而有不同的行為。

##  <a name="manage-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶

多重身分識別應用程式可讓使用者新增多個帳戶。  Intune 應用程式僅支援一個受控帳戶。  Intune 應用程式不會限制非受控帳戶的數目。

當應用程式中有受控帳戶時：
*   若使用者嘗試新增第二個受控帳戶，系統會要求使用者選取要使用哪個受控帳戶。  另一個帳戶會移除。
*   若 IT 系統管理員對第二個現有帳戶新增原則，系統會要求使用者選取要使用哪個受控帳戶。  另一個帳戶會移除。

閱讀下列案例範例以深入了解如何處理多個使用者帳戶。

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。與 **X 公司**建立關聯的帳戶會先得到應用程式保護原則。 如果您希望與 Y 公司建立關聯的使用者帳戶受控於應用程式保護原則，您必須移除與 X 公司建立關聯的使用者帳戶，然後新增與 Y 公司建立關聯的使用者帳戶。

### <a name="add-a-second-account"></a>新增第二個帳戶

如果您使用 iOS 裝置，則嘗試在該裝置上新增第二個工作帳戶時，會看到封鎖訊息。 帳戶隨即顯示，接著您可以選擇想要移除的帳戶。

## <a name="next-steps"></a>接下來的步驟
[當 Android 應用程式交由應用程式防護原則管理時的行為](end-user-mam-apps-android.md)
