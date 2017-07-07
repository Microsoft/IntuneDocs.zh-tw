---
title: "Intune 裝置註冊的多重要素驗證"
description: "如何在 Azure AD 中針對裝置註冊要求多重要素驗證。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angerobe
ms.date: 02/17/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 47abdabd-dcd6-48d8-aade-3f3eefb92ee1
ROBOTS: 
ms.custom: intune-classic
ms.openlocfilehash: 805ca79932788786636d365109e06aee836d8a0e
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="multi-factor-authentication-for-intune-device-enrollments"></a>Intune 裝置的註冊的多重要素驗證 | Microsoft Docs

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune 針對裝置註冊整合 Azure AD 多重要素驗證 (MFA) 來協助您保護公司資源的安全。

MFA 的運作方式是要求使用下列任兩個或更多個驗證方法： 

- 您知道的某種資訊 (通常是密碼或 PIN)。
- 您擁有的某種東西 (不容易複製的信任裝置，例如手機)。
- 您的某種身分表徵 (生物識別技術)。

iOS、Android、Windows 8.1 或更新版本，或 Windows Phone 8.1 或更新的裝置支援 MFA。

> [!NOTE]
> 在較舊版本的 Configuration Manager (1610 之前的版本)，您仍然會在 Configuration Manager 系統管理主控台中看到 MFA 設定。 請勿嘗試在 Configuration Manager 系統管理主控台中設定 MFA，因為它將會無法運作。 請依照本主題中所述方式設定 MFA。

### <a name="configure-intune-to-require-multi-factor-authentication-at-device-enrollment"></a>設定 Intune 以在裝置註冊時要求多重要素驗證
若要在註冊裝置時要求 MFA，請遵循下列步驟︰

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
