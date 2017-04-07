---
title: "服務描述 | Microsoft Docs"
description: "Intune 是雲端式服務，可協助您管理 Windows、iOS、Mac OS X、Android 及 Windows Mobile 裝置。"
keywords: 
author: lindavr
ms.author: lindavr
manager: angrobe
ms.date: 09/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f268cf29461447306d0f5c3ca06d541d9a03a49d
ms.openlocfilehash: 8e8257a426bd6b9a99e21e928b08c84f162d5da3
ms.lasthandoff: 12/16/2016


---

# <a name="microsoft-intune-service-description"></a>Microsoft Intune 服務描述

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Microsoft Intune 是雲端式服務，可協助您管理執行 Windows、Mac OS X、iOS、Android 或 Windows Mobile 的裝置。 Intune 也可協助保護公司應用程式和資料。 您可以單獨使用 Intune，或與 System Center Configuration Manager 整合以擴充管理功能。

Microsoft 提供 Intune 登入權益，適用於合格方案中的合格服務。 登入權益讓您能夠從遠端與 Microsoft 專家合作，來準備您的 Intune 環境以供使用。 如需登入權益的詳細資訊，請參閱 [Microsoft Intune 登入權益說明](http://go.microsoft.com/fwlink/?LinkId=619281)。

您可以從包含 100 個使用者授權的 30 天免費試用版開始使用 Intune。 若要使用免費的試用版，[請前往 Intune 註冊頁面](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)。 如果您的組織有 Enterprise 合約或對等的大量授權合約，請連絡您的 Microsoft 代表來設定您的免費試用版。

> [!NOTE]
> 您的組織若已有 Microsoft Online Services 的工作或學校帳戶，而您在試用期結束後仍要繼續在生產環境中使用此 Intune 訂用帳戶，請在該頁面選擇 [登入] 選項，然後再以您組織的全域管理員帳戶進行驗證。 這個動作可確保您的 Intune 試用版連結至您現有的工作或學校帳戶。

如需可在行動裝置上指定之設定值的清單，請參閱：

-   [Microsoft Intune 的已註冊裝置管理功能](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [搭配 System Center Configuration Manager 和 Microsoft Intune 的混合式行動裝置管理 (MDM)](https://technet.microsoft.com/library/mt627883.aspx)

如需 System Center Configuration Manager 的詳細資訊，請參閱 [System Center Configuration Manager 文件](https://technet.microsoft.com/library/mt346023.aspx)。

## <a name="learn-how-intune-service-updates-affect-you"></a>了解 Intune 服務更新對您的影響
由於 Intune 是線上服務，因此 Microsoft 會定期更新。

使用本文章中的資訊，可協助您深入了解這些服務更新的頻率，以及我們在更新可能影響您使用服務時提供給您的進階通知。

若要了解 Intune 服務的變更，請參閱 [Microsoft Intune 的新功能](/intune/deploy-use/whats-new-in-microsoft-intune)。 [Microsoft Intune 部落格](http://blogs.technet.com/b/microsoftintune/)也會討論服務的變更，並提供實用秘訣，協助您充分利用 Intune。

我們也將會透過 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx)訊息中心，通知您重要的服務更新。 如果您安裝隨附的 [Office 365 管理行動應用程式](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)，即可在行動裝置上接收通知。

> [!NOTE]
> 您可以在 [Office 365 管理入口網站](https://portal.office.com/Admin/Default.aspx)中監視 Intune 服務健全狀況。 選擇左窗格中的 **[服務健全狀況]**。  

以下是 Microsoft 提供與 Intune 服務有關的通知類型︰
-   為了協助您規劃服務變更，我們會在服務升級前至少 30-90 天通知您，視變更的影響而定。 使用類似佈告欄警示的產品內通訊通道時，就會發生這項變更。 這些變更可能包括︰
    * 可能會影響相容性或法規的更新
    * 使用者體驗、使用者介面和工作流程的變更
    * 全新或已變更的 API - 通知您必須進行測試以確保自訂應用程式的回溯相容性
    * 系統需求變更，例如必要的最低瀏覽器版本
    * 需要您採取動作來啟用功能或避免功能服務中斷的任何更新。
-   Microsoft 在我們每月的服務更新中提供新特性、新功能，以及現有功能之增強功能的相關資訊。 Microsoft 一般會在每月的月中推出服務更新。 [Microsoft Intune 的新功能](/intune/deploy-use/whats-new-in-microsoft-intune)中會描述更新。
    -   萬一 Intune 服務停用，將提前在 12 個月之前通知您。

## <a name="choose-the-management-solution-thats-right-for-you"></a>選擇適合您的管理方案
您可以透過幾種方式設定 Intune 來管理和協助保護公司的行動裝置和電腦 (在本文章中稱之為**裝置**)。

-**Intune 獨立設定。** 使用 Intune 中的 Web 式管理主控台來管理您組織中的裝置。 Intune 可以用於不含任何內部部署 IT 基礎結構的情況。 如果您使用 Intune 搭配 Active Directory 網域服務，就可以將透過網域服務來管理的網域使用者帳戶與 Intune 搭配使用。

-**Intune 搭配 System Center Configuration Manager。** 使用 Configuration Manager 管理主控台來管理您企業中的電腦和行動裝置。 此設定可協助您透過單一主控台 (Configuration Manager 管理主控台) 來管理貴組織的所有裝置。 Configuration Manager 可支援非常大量的行動裝置、伺服器及電腦。 如需 Configuration Manager 的詳細資訊，請參閱[搭配 System Center Configuration Manager 和 Microsoft Intune 的混合式行動裝置管理 (MDM)](https://technet.microsoft.com/library/mt627883.aspx)。 若要更多協助以決定哪種方法最適合您，請參閱 [選擇 Microsoft Intune 獨立和混合式行動裝置管理與 Configuration Manager](https://technet.microsoft.com/en-us/library/mt706478.aspx)。


## <a name="learn-more-about-intune"></a>深入了解 Intune
您可以使用這些資源來深入了解 Intune：

- [Microsoft Intune 信任中心](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/)提供 Intune 的安全性、隱私權和合規性作法的相關資訊，並說明其中一些 Intune 憑證。

- [Microsoft Intune 的已註冊裝置管理功能](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

### <a name="see-also"></a>請參閱
[Microsoft Intune](https://docs.microsoft.com/intune/)
[System Center 2012 Configuration Manager 文件庫](https://technet.microsoft.com/library/gg682041.aspx)

[Microsoft Intune 的新功能](/intune/deploy-use/whats-new-in-microsoft-intune)

