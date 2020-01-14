---
title: 使用應用程式保護原則的 iOS 應用程式
description: 本主題說明當 iOS 應用程式交由應用程式保護原則管理時的行為。
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606616"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>當 iOS 應用程式交由應用程式保護原則管理時的行為

Intune 應用程式保護原則適用於公司或學校所使用的應用程式。 這表示當您的員工和學生在個人內容中使用他們的應用程式時，他們的體驗可能不會有任何差異。 不過，在公司或學校內容中，他們可能會收到提示以做出帳戶決策、更新其設定，或與您聯繫以尋求幫助。 使用此文章來了解使用者在嘗試存取和使用受 Intune 保護的應用程式時的體驗。  

## <a name="access-apps"></a>存取應用程式

如果裝置**未註冊於 Intune 中**，會要求使用者在第一次使用應用程式時重新啟動應用程式。 必須先重新啟動，才會將應用程式保護原則套用到應用程式。

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

針對**在 Intune 中註冊以進行管理**的裝置，使用者會看到其應用程式現在已受管理的訊息。

## <a name="use-apps-with-multi-identity-support"></a>使用具有多重身分識別支援的應用程式

支援多重身分識別的應用程式可讓您使用不同的公司和個人帳戶來存取相同的應用程式。 當使用者在公司或學校內容中存取這些應用程式時，就會啟用應用程式保護原則，例如輸入裝置 PIN。   

視您設定原則的方式而定，使用者在其所有應用程式中體驗到的 PIN 提示可能會有所不同。  例如，您可以設定原則，以便：       
* 使用者在啟動應用程式時，Microsoft Outlook 會提示使用者輸入 PIN。 
* OneDrive 會在使用者登入其公司帳戶時提示他們輸入 PIN。  
* 當使用者存取公司商務用 OneDrive 位置中所儲存的文件時，Microsoft Word、PowerPoint 和 Excel 會提示使用者輸入 PIN。  

- 深入了解支援 Intune 的[應用程式保護和多重身分識別](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)的應用程式。  

## <a name="manage-user-accounts-on-the-device"></a>管理裝置上的使用者帳戶  

Intune 應用程式保護原則會將使用者限制為每個應用程式一個受控的公司或學校帳戶。 應用程式保護原則不會限制使用者可以新增的非受控帳戶數目。   

- 若使用者嘗試新增第二個受控帳戶，系統會要求使用者選取要使用哪個受控帳戶。 如果使用者新增第二個帳戶，則會移除第一個帳戶。
- 如果您將保護原則新增至您的另一個使用者帳戶，系統會要求使用者選取要使用哪個受控帳戶。 另一個帳戶會移除。 

有些使用者無法選擇在受控帳戶之間切換或選取。 下列裝置無法使用此選項：
* 由 Intune 管理  
* 由協力廠商企業行動管理解決方案管理，並使用 IntuneMAMUPN 設定進行設定 

下列案例範例說明如何處理多個使用者帳戶：  

使用者 A 為兩家公司服務 - **X 公司**和 **Y 公司**。使用者 A 在這兩家公司各有一個工作帳戶，且兩者全都使用 Intune 部署應用程式保護原則。 **X 公司**部署**先於** **Y 公司**部署應用程式保護原則。與 **X 公司**建立關聯的帳戶會先得到應用程式保護原則。 如果您希望與 Y 公司建立關聯的使用者帳戶受控於應用程式保護原則，您必須移除與 X 公司建立關聯的使用者帳戶，然後新增與 Y 公司建立關聯的使用者帳戶。  

## <a name="next-steps"></a>後續步驟

[當 Android 應用程式交由應用程式防護原則管理時的行為](end-user-mam-apps-android.md)
