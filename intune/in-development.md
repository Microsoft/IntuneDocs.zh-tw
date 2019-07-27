---
title: 開發中 - Microsoft Intune
titleSuffix: ''
description: 正在開發的 Microsoft Intune 功能
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9b02deb529bd6a9bca882fecb3d55d9db513191
ms.sourcegitcommit: 614c4c36cfe544569db998e17e29feeaefbb7a2e
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68427180"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>Microsoft Intune 正在開發的項目 - 2019 年 7 月

為了協助您整備及規劃，此頁面會列出正在開發，但尚未發行的 Intune UI 更新及功能。 此外：

- 若我們預期您將需要在變更前先行採取動作，我們會發佈輔助性的 Office 訊息中心貼文。
- 當功能在生產環境中啟動時，無論是作為預覽功能還是正式推出，功能描述都會從此頁面移除，並移到 [[新增功能]](whats-new.md) 頁面。
- 此頁面和 [[新增功能]](whats-new.md) 頁面會定期更新。 請回來查看其他更新。
- 請參閱 [M365 藍圖](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)以取得策略性的交付時間表。

> [!Note]
> 這些項目會反映 Microsoft 目前針對未來版本中 Intune 功能的預期。 日期和個別的功能可能會產生變更。 並非所有正在開發的項目在此頁面上都具有功能描述。

**RSS 摘要**：將下列 URL 複製並貼上至您的摘要讀取器中，以在本頁更新時收到通知：`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>應用程式管理

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>設定組織帳戶的代理程式更新內容 <!-- 2576686 -->
Android 和 iOS 裝置上的 Intune 應用程式保護原則 (應用程式) 可讓您控制組織帳戶的代理程式更新內容。 這項功能將需要應用程式的支援, 而且可能無法供所有啟用應用程式的應用程式使用。 如需 APP 的詳細資訊，請參閱[什麼是應用程式防護原則？](app-protection-policy.md)

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>報告 Android 工作設定檔的可用 Google Play 應用程式 <!-- 3041956  -->
針對安裝在 Android 工作設定檔裝置上的可用應用程式，您可以檢視應用程式安裝狀態，以及受控 Google Play 應用程式的安裝版本。 如需詳細資訊，請參閱[如何監視應用程式保護原則](app-protection-policies-monitor.md)、[使用 Intune 管理 Android 工作設定檔裝置](android-enterprise-overview.md)及[受控的 Google Play 應用程式類型](apps-add-android-for-work.md#managed-google-play-app-type)。

<!-- ***********************************************-->
## <a name="device-configuration"></a>裝置設定

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>支援 iOS 版的 IKEv2 VPN 設定檔 <!-- 1943438 -->
您可以使用 IKEv2 通訊協定建立 iOS 原生 VPN 用戶端的 VPN 設定檔。 IKEv2 是 [裝置設定]   > [設定檔]   > [建立設定檔]   > [iOS]  (平台) > [VPN]  (設定檔類型) > [設定]  中的新連線類型。

這些 VPN 設定檔會設定原生的 VPN 用戶端。 因此，不會有 VPN 用戶端應用程式安裝或推送到受控裝置。 這項功能需要向 Intune 註冊裝置 (MDM 註冊)。

若要查看您目前可以設定的 VPN 設定，請前往[在 Microsoft Intune 中的 iOS 裝置上設定 VPN 設定](vpn-settings-ios.md)。

適用於：iOS


<!-- ***********************************************-->
## <a name="device-management"></a>裝置管理

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>將自動裝置清除時間限制設定為30天 <!--4231059  -->
在最後一次登入之後, 您將能夠將自動裝置清除時間限制設定為30天 (而不是目前的限制為90天)。 若要這麼做, 請移至**Intune**  > **裝置** > **設定** > **裝置清除規則**。

<!-- ***********************************************-->
## <a name="security"></a>安全性

### <a name="import-and-export-security-baselines------3408610------------"></a>匯入和匯出安全性基準    <!--3408610          -->  
我們新增了匯出和匯入安全性基準的功能, 讓您可以進行自訂, 並在 Intune 環境之間共用。


<!-- ***********************************************-->
## <a name="notices"></a>通知

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>請參閱
如需近期發展的詳細資料，請參閱 [Microsoft Intune 的新功能](whats-new.md)。


