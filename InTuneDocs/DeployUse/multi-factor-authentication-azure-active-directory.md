---
title: "使用 Azure AD 進行多重要素驗證| Microsoft Intune"
description: "如何在 Azure AD 中針對裝置註冊要求多重要素驗證。"
keywords: 
author: nbigman
ms.author: nbigman
manager: angerobe
ms.date: 09/22/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: NOINDEX,NOFOLLOW
translationtype: Human Translation
ms.sourcegitcommit: a7cced90c482498b5f5af424165f8dcf77b79b75
ms.openlocfilehash: ccd55cc8637ebccfdbddd05c4f6b182c7923a2ab


---

# Microsoft Intune 的多重要素驗證

Intune 針對裝置註冊整合 Azure AD 多重要素驗證 (MFA) 來協助您保護公司資源的安全。 除了使用者名稱和密碼，MFA 還需要其他驗證因素，如文字驗證。 iOS、Android、Windows 8.1 或更新版本，或 Windows Phone 8.1 或更新的裝置支援此功能。

> [!NOTE]
>
> 在較舊版本的 Configuration Manager (1610 之前的版本)，您仍然會在 Configuration Manager 系統管理主控台中看到 MFA 設定。 請勿嘗試在 Configuration Manager 系統管理主控台中設定 MFA，因為它將會無法運作。 請依照本主題中所述方式設定 MFA。

### 設定 Intune 以在裝置註冊時要求多重要素驗證
若要在裝置註冊時要求 MFA，請遵循下列步驟：

1. 使用您的系統管理員認證登入您的 [Microsoft Azure 入口網站](https://manage.windowsazure.com)。
2. 選擇您的租用戶。
2. 選擇 [應用程式] 索引標籤。 您將會看到一份服務清單，您可以在其中設定 Azure AD 安全性功能。
3. 選擇 [Microsoft Intune 註冊]。
4. 選擇 **[設定]**。 
5. 在 [多重要素驗證與以位置為準的存取規則] 底下，您可以：
    -  啟用存取規則
    -  選擇是否要將規則套用到所有的使用者，或是套用到特定的 Azure AD 安全性群組。
    -  針對所有裝置的註冊要求多重要素驗證。
    -  當裝置為非工作中時，針對註冊要求多重要素驗證。
    -  選擇 [封鎖存取公司資源] 以防止裝置在未連接到公司網路時註冊。 
4. 您也可以按一下 [定義/編輯您的工作網路位置] 連結，來設定裝置註冊的網路連線需求。

> [!IMPORTANT]
> 
> 請勿針對 Microsoft Intune 註冊設定 [以裝置為準的存取規則]。



<!--HONumber=Sep16_HO4-->


