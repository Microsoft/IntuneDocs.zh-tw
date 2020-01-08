---
title: 適用於延伸模組的應用程式保護原則
titleSuffix: Microsoft Intune
description: 此主題描述延伸模組的應用程式保護原則 (APP)。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: demerson
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ff4fcd7d1b2115c4fbe0bc00759ef3d60482904
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75692109"
---
# <a name="protecting-application-extensions"></a>保護應用程式延伸模組

此文章描述 Microsoft Intune 中應用程式保護原則的延伸模組。

## <a name="add-ins-for-outlook-app"></a>Outlook 應用程式增益集

Outlook 增益集可讓您將熱門應用程式與電子郵件用戶端整合。 Web、Windows、Mac，以及 Android 和 iOS 版的 Outlook，皆提供 Outlook 增益集。 Intune APP SDK 與 Intune 應用程式保護原則不包含管理 Outlook 增益集的支援，但還有其他方法可以限制其使用。 因為增益集透過 Microsoft Exchange 進行管理，所以除非使用者的 Exchange 對使用者關閉了增益集，否則，使用者將可在 Outlook 與未受管理的增益集應用程式之間，共用資料與郵件。

若想要讓使用者無法存取及安裝 Outlook 增益集 (如此會影響所有 Outlook 用戶端)，請務必在 Exchange 系統管理中心對角色進行下列變更︰

- 為避免使用者安裝 Office 市集增益集，請移除使用者的「我的市集」角色。
- 為避免使用者側載增益集，請移除使用者的「我的自訂應用程式」角色。
- 為避免使用者安裝所有增益集，請移除使用者的「我的自訂應用程式」與「我的市集」角色。

這些指示適用於 Office 365、Exchange 2016、Exchange 2013 (跨 Web、Windows、Mac 與行動裝置上的 Outlook)。

- 深入了解[適用於 Outlook 的增益集](https://technet.microsoft.com/library/jj943753(v=exchg.150).aspx)。
- 深入了解 [How to specify the administrators and users who can install and manage add-ins for Outlook app](https://technet.microsoft.com/library/jj943754(v=exchg.150).aspx) (如何指定可安裝及管理 Outlook 應用程式增益集的系統管理員與使用者)。

## <a name="linkedin-account-connections-for-microsoft-apps"></a>Microsoft 應用程式的 LinkedIn 帳戶連線

LinkedIn 帳戶連線讓使用者在某些 Microsoft 應用程式內看到公用 LinkedIn 設定檔資訊。 根據預設，您的使用者可以選擇連線 LinkedIn 和 Microsoft 工作或學校帳戶，來查看額外的 LinkedIn 設定檔資訊。 

> [!NOTE]
> LinkedIn 整合目前無法用於美國政府客戶，以及 裝載於澳洲、加拿大、中國、法國、德國、印度、韓國、英國、日本和南非的組織的 Exchange Online 信箱。

Intune SDK 和 Intune 應用程式防護原則不包含管理 LinkedIn 帳戶連線的支援，但還有其他方法可以管理這些連線。 您可以停用整個組織的 LinkedIn 帳戶連線，或是您可以針對組織中的選取使用者群組啟用 LinkedIn 帳戶連線。 這些設定會影響跨所有平台 (Web、行動裝置和桌面) 上的 Office 365 應用程式之間的 LinkedIn 連線。 您可以：

- 在 Azure 入口網站為租用戶啟用或停用 LinkedIn 帳戶連線。 
- 使用群組原則為組織的 Office 2016 應用程式啟用或停用 LinkedIn 帳戶連線。

如果已為租用戶啟用 LinkedIn 整合，則當您組織中的使用者連線 LinkedIn 和 Microsoft 工作或學校帳戶時，他們有兩個選項： 

- 他們可以提供在這兩個帳戶之間共用資料的權限。 這表示他們會提供權限讓 LinkedIn 帳戶與 Microsoft 工作或學校帳戶共用資料，以及讓 Microsoft 工作或學校帳戶與其 LinkedIn 帳戶共用資料。 與 LinkedIn 共用的資料會離開連線服務。 
- 他們提供只能從 LinkedIn 帳戶將資料與 Microsoft 工作及學校帳戶共用的權限

如果使用者同意在帳戶之間共用資料，如同 Office 增益集一樣，LinkedIn 整合會使用現有的 Microsoft Graph API。 LinkedIn 整合只會使用可供 Office 增益集使用的 API 子集，並支援各種排除項目。


|Microsoft Graph 權限  |說明  |
|---------|---------|
|[人員](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#people-permissions)的讀取權限     |可讓應用程式讀取與登入使用者相關的人員評分清單。 清單可以包括本機連絡人、來自社交網路或貴組織目錄的連絡人，以及最近連絡過 (例如電子郵件與 Skype) 的人員。         |
|[行事曆](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#calendars-permissions)的讀取權限     |允許應用程式讀取使用者行事曆中的事件。 包含登入使用者行事曆中的會議、其時間、位置及出席者。         |
|[使用者設定檔](https://developer.microsoft.com/graph/docs/concepts/permissions_reference#user-permissions)的讀取權限     |允許使用者登入應用程式，以及允許應用程式讀取登入之使用者的設定檔。 它也允許應用程式讀取登入之使用者的基本公司資訊。         |
|訂閱     |未提供此範圍且尚未使用。 它包含使用者組織提供給 Microsoft 應用程式和服務 (例如 Office 365) 的訂閱。         |
|深入資訊     |未提供此範圍且尚未使用。 它包含根據 Microsoft 服務的使用，與登入的使用者帳戶建立關聯的興趣。         |

### <a name="learn-more"></a>深入了解

- 深入了解 [LinkedIn information and features in your Microsoft apps](https://go.microsoft.com/fwlink/?linkid=850740) (Microsoft 應用程式中的 LinkedIn 資訊與功能)。
- 在 [Office 365 藍圖頁面](https://products.office.com/en-US/business/office-365-roadmap?filters=%26freeformsearch=linkedin#abc)上深入了解 LinkedIn 帳戶連線版本。 
- 深入了解 [Microsoft 應用程式和服務的 LinkedIn 帳戶連線](https://docs.microsoft.com/azure/active-directory/linkedin-integration)。
- 如需在使用者的 LinkedIn 與 Microsoft 工作或學校帳戶之間共用之資料的詳細資訊，請參閱 [LinkedIn in Microsoft applications at your work or school](https://www.linkedin.com/help/linkedin/answer/84077) (工作或學校之 Microsoft 應用程式中的 LinkedIn)。

