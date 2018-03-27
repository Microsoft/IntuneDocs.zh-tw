---
title: 對 O365 以應用程式為基礎的條件式存取
description: 了解 MAM CA 如何協助控制哪些應用程式可存取 O365 服務的概念。
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/05/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: b0b0fbfce086729551b211dd4bc4b83348aa4787
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="allow-only-mobile-apps-that-support-intune-app-protection-policies-to-access-office-365-services"></a>只允許支援 Intune 應用程式保護原則的行動裝置應用程式存取 Office 365 服務

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

[Intune 應用程式保護原則](protect-apps-and-data-with-microsoft-intune.md)可協助您在向 Intune 註冊管理的裝置上保護公司資料。 您也可以在**未向 Intune 註冊管理之屬員工擁有的裝置**上，使用應用程式保護原則。  在此情況下，即使未管理裝置，仍然需要確定公司資料和資源受到保護。 透過應用程式型條件式存取與 MAM，您可以建立原則，只允許支援 Intune 應用程式保護原則的行動裝置應用程式存取 Exchange Online 等 O365 服務。

例如，您可以藉由只允許 **Microsoft Outlook 應用程式**存取 Exchange Online，來**封鎖 iOS 和 Android 上的內建郵件應用程式**，這些應用程式從**Exchange Online** 取得電子郵件時，不會受到 Intune MAM 原則所提供的資料保護。 或者您可以禁止不具有 Intune MAM 支援的行動裝置存取 **SharePoint Online**。

下列圖表描述應用程式型條件式存取原則在決定允許或封鎖存取時所使用的流程：![此圖表顯示所含用以決定要允許或封鎖存取的各種準則](../media/mam-ca-decision-flow_simple.png)。

圖表中使用的縮寫描述：
* **CP**：公司入口網站應用程式
* **AA**：Azure Authenticator 應用程式
* **AAD**：Azure Active Directory
* **EAS**：Exchange Active Sync

## <a name="prerequisites"></a>必要條件
建立應用程式型條件式存取原則**之前**，您必須擁有 **Enterprise Mobility + Security 或 Azure Active Directory Premium 訂用帳戶**，且使用者必須獲 EMS 或 Azure AD 授權。 如需詳細資訊，請參閱 [Enterprise Mobility 定價頁面](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)或 [Azure Active Directory 定價頁面](https://azure.microsoft.com/pricing/details/active-directory/)。


## <a name="supported-apps"></a>支援的應用程式
**Exchange Online**：
* 適用於 Android 和 iOS 的 **Microsoft Outlook**。

**SharePoint Online**
* 適用於 iOS 和 Android 的 Microsoft Word
* 適用於 iOS 和 Android 的 Microsoft Excel
* 適用於 iOS 和 Android 的 Microsoft PowerPoint
* 適用於 iOS 和 Android 的商務用 Microsoft OneDrive
* 適用於 iOS 的 Microsoft OneNote

>[!IMPORTANT]
>針對 Android 裝置，初始裝置註冊必須透過登入至 OneDrive 應用程式或 Outlook 應用程式來完成。 適用於 Android 的 OneNote 應用程式尚未支援不需要註冊的 MAM。

若要了解具有應用程式型條件式存取原則之應用程式的使用者體驗，請參閱[搭配 MAM CA 使用應用程式時的預期狀況](use-apps-with-mam-ca.md)。


## <a name="next-steps"></a>接下來的步驟
[建立 MAM 應用程式的 Exchange Online 原則](mam-ca-for-exchange-online.md)

[建立 MAM 應用程式的 SharePoint Online 原則](mam-ca-for-sharepoint-online.md)

[封鎖沒有新式驗證的應用程式](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>另請參閱

[使用應用程式保護原則保護應用程式資料](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
