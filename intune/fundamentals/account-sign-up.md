---
title: 註冊或登入 Microsoft Intune
description: 如何註冊 Microsoft Intune 訂用帳戶，或如何登入以開始使用訂用帳戶。
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f3ce07a-b718-42a9-bace-f99a8b8abd94
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78d38b72c9853a9eadaf71fcdff7567fc66d35ca
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414660"
---
# <a name="sign-up-or-sign-in-to-microsoft-intune"></a>註冊或登入 Microsoft Intune

本主題會告訴系統管理員如何註冊 Intune 帳戶。

註冊 Intune 之前，請先判斷您是否已有 Microsoft Online Services 帳戶、Enterprise 合約或等同的大量授權合約。 Microsoft 大量授權合約或 Office 365 等其他 Microsoft 雲端服務訂閱，通常包括工作或學校帳戶。

如果您已經有工作或學校帳戶，請**登入**該帳戶，並將 Intune 新增您的訂閱。 否則，您可以**註冊**新帳戶供您的組織使用 Intune。

>[!WARNING]
>註冊新帳戶後，無法合併現有的工作或學校帳戶。

## <a name="how-to-sign-up-for-intune"></a>如何註冊 Intune

1. 請瀏覽 [Intune 註冊](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)頁面。

   ![Microsoft Intune 試用帳戶註冊網頁的螢幕擷取畫面](./media/account-sign-up/account-sign-up-site.png)

2. 在 [註冊] 頁面上，登入或註冊以管理 Intune 的新訂閱。

## <a name="post-sign-up-considerations"></a>註冊後的考量

註冊新的訂閱後，在您於註冊過程中提供的電子郵件位址上，您會收到包含帳戶資訊的電子郵件訊息。 本電子郵件可確認您的訂閱是使用中的狀態。

完成註冊程序後，會將您導向 Microsoft 365 系統管理中心，讓您新增使用者並指派授權給他們。 如果您只有使用預設 onmicrosoft.com 網域名稱的雲端式帳戶，則您現在可以繼續新增使用者並指派授權。 不過，如果您計劃使用組織的[自訂網域名稱](custom-domain-name-configure.md)，或想要從內部部署 Active Directory [同步處理使用者帳戶資訊](users-add.md#sync-active-directory-and-add-users-to-intune)，則可關閉該瀏覽器視窗。

## <a name="sign-in-to-microsoft-intune"></a>登入 Microsoft Intune

一旦註冊 Intune 之後，您就可以使用任何具有[支援瀏覽器](supported-devices-browsers.md#intune-supported-web-browsers)的裝置登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 來管理服務。

根據預設，您的帳戶在 Azure AD 中必須具備下列其中一個權限：

- 全域管理員
- Intune 服務管理員 (也稱為 Intune 管理員)

若要授與存取權以管理具有其他權限之使用者的服務，則請參閱[依角色區分的存取控制](role-based-access-control.md)

### <a name="intune-admin-portal-url"></a>Intune 管理入口網站 URL

Microsoft 365 系統管理中心： https://devicemanagement.microsoft.com

Intune Azure 入口網站： https://portal.azure.com/#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade

Intune 教育版： https://intuneeducation.portal.azure.com

Intune 傳統入口網站： https://manage.microsoft.com Intune 傳統入口網站僅用於管理已向 Intune 電腦軟體用戶端註冊的裝置

### <a name="urls-for-intune-services-provided-by-office-365"></a>Office 365 所提供的 Intune 服務 URL

Microsoft 365 商務版： https://portal.microsoft.com/adminportal

Office 365 行動裝置管理： https://portal.office.com/adminportal/home#/MifoDevices

## <a name="see-also"></a>請參閱

[您無法登入 Office 365、Azure 或 Intune](https://support.microsoft.com/help/2412085) \(英文\)
