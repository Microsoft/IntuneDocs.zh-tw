---
title: "適用於 Windows 的 Multi-Factor Authentication | Microsoft Intune"
description: "Intune 整合 Multi-Factor Authentication (MFA) 來協助您保護公司資源。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 9b4f197d-bc10-4bee-91c9-19bcc8287d36
ms.reviewer: vinaybha
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ab9ad1fb42176f2fc2babaa6fa3c91cea40b4ca5
ms.openlocfilehash: 1bfd17f9fcc73049254bc77351eae48da874fb4c


---

# <a name="protect-windows-devices-with-multifactor-authentication"></a>Protect Windows devices with multi-factor authentication
Microsoft Intune 整合 Multi-Factor Authentication (MFA) 來協助您保護公司資源。 除了使用者名稱和密碼，MFA 還需要其他驗證因素，如文字驗證。 在註冊 Windows 8.1 或更新版本、Windows Phone 8.1 或 Windows 10 桌面版和行動裝置版的裝置期間，Intune 支援使用 MFA。

## <a name="onpremises-infrastructure-requirements-for-adfs-mfa"></a>適用於 ADFS MFA 的內部部署基礎結構需求
若要設定 Multi-factor Authentication，需要下列項目：

-   自動註冊，如[設定 Windows 裝置管理](set-up-windows-device-management-with-microsoft-intune.md)中所述。
-   **已加入 ADFS 伺服器的 Active Directory 網域。**

-   **為 MFA 設定的 Active Directory 同盟服務 (ADFS) 伺服器。** 執行 Windows Server 2012 R2 且設定為 ADFS 伺服器的伺服器。 如需詳細資訊，請參閱[搭配 Windows Server 2012 R2 AD FS 使用 Azure Multi-Factor Authentication Server 保護雲端和內部部署資源](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-adfs-w2k12/)

這些伺服器必須符合 [Windows Server 2012 R2 的系統需求和安裝資訊](http://technet.microsoft.com/library/dn303418.aspx)中的系統需求。

 


#### <a name="mfa-with-intune"></a>MFA 搭配 Intune
如果您的組織有內部部署 IT 基礎結構 (含有 Active Directory 網域和 Active Directory Federation Services (ADFS))，您可以在同盟伺服器上設定 MFA，然後針對 Intune 註冊啟用 MFA。 藉由在 Intune 上設定 MFA，使用者在註冊期間驗證一次，之後就能使用公司資源，而不需要每次重複 MFA 程序。

>[!NOTE]
>ADFS 伺服器上可針對每個使用者或每個群組來要求 MFA。  

#### <a name="mfa-without-intune"></a>MFA 未搭配 Intune
如果您在同盟伺服器上設定 MFA，但未針對在 Intune 中註冊而啟用 MFA，則使用者每次存取公司資源時 (不只是註冊裝置) 都需要使用 MFA。

您也可以使用 Azure Active Directory (Azure AD) MFA 要求每個使用者在每次存取公司資源時都需要 MFA。 Azure AD MFA 是一項不需要任何內部部署 IT 基礎結構的雲端服務。 若要了解如何設定 Azure AD MFA，請參閱[開始在雲端中使用 Azure Multi-Factor Authentication](https://azure.microsoft.com/en-us/documentation/articles/multi-factor-authentication-get-started-cloud/)。

## <a name="requiring-adfs-mfa-during-enrollment-of-windows-devices"></a>在 Windows 裝置註冊期間要求 ADFS MFA
如需如何在 ADFS 中啟用 MFA 的相關資訊，請參閱 [透過其他多因素驗證管理機密應用程式的風險](http://technet.microsoft.com/library/dn280949.aspx)。

## <a name="set-up-device-enrollment-mfa-in-intune"></a>在 Intune 中設定裝置註冊 MFA
>[!Important]  
>您必須先啟用 Azure AD 租用戶或內部部署環境中的 MFA，才能要求使用 MFA 進行 Windows 裝置的 Intune 註冊。 如果不這麼做，當使用者嘗試註冊他們的 Windows 裝置時，或當他們嘗試將裝置加入 Azure AD 時，使用者會收到錯誤訊息 (當設定在加入 Azure AD 期間自動註冊時)。

1.  在 Intune 管理主控台中，選擇 [系統管理] &gt;[行動裝置管理] &gt;[Multi-factor authentication (多重要素驗證 )]。

2.  選擇 [設定 Multi-Factor Authentication]，然後選擇 [啟用 Multi-Factor Authentication]。



<!--HONumber=Nov16_HO1-->


