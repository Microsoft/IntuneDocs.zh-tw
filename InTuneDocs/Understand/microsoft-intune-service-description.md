---
title: "服務描述 | Microsoft Intune"
description: "Intune 是雲端式服務，可協助您管理 Windows 電腦及 iOS、Mac OS X、Android 及 Windows 行動裝置。"
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c1e215320168c659d5f838355f6350111d6979b0
ms.openlocfilehash: 98a5013ef42732e6a1a541e128986bedbb004611


---

# Microsoft Intune 服務描述

Microsoft Intune 是雲端式服務，可協助您管理 Windows 電腦以及 iOS、Mac OS X、Android 和 Windows 行動裝置。 Intune 也可協助保護公司應用程式和資料。 您可以單獨使用 Intune，或與 System Center 2012 R2 Configuration Manager 整合以擴充管理功能。

Microsoft 提供 Intune 登入權益，適用於合格方案中的合格服務。 登入權益讓您能夠從遠端與 Microsoft 專家合作，來準備您的 Intune 環境以供使用。 如需詳細資訊，請參閱 [Microsoft Intune 登入權益說明](http://go.microsoft.com/fwlink/?LinkId=619281)。

您可以從包含 100 個使用者授權的 30 天免費試用版開始使用 Intune。 若要使用免費的試用版，請[按一下這裡前往 Intune 的註冊頁面](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)。 如果您的組織有 Enterprise 合約或對等的大量授權合約，請連絡您的 Microsoft 代表來設定您的免費試用版。

> [!NOTE]
> 您的組織若已有 Microsoft Online Services 的工作或學校帳戶，而您在試用期結束後仍要繼續在生產環境中使用此 Intune 訂用帳戶，請在該頁面按一下 [登入] 選項，然後再以您組織的全域管理員帳戶進行驗證。 這個動作可確保您的 Intune 試用版連結至您現有的工作或學校帳戶。

如需可在行動裝置上指定之設定值的清單，請參閱：

-   [Microsoft Intune 的行動裝置管理功能](/intune/get-started/mobile-device-management-capabilities-in-microsoft-intune)

-   [Configuration Manager 中行動裝置的一般設定](https://technet.microsoft.com/library/dn376523.aspx)

如需 System Center 2012 R2 Configuration Manager 的資訊，請參閱 [System Center 2012 Configuration Manager 文件庫](https://technet.microsoft.com/library/gg682041.aspx)。

## 了解 Intune 服務更新對您的影響
由於 Intune 是線上服務，因此 Microsoft 會定期更新。

使用本主題中的資訊，可協助您了解這些服務更新的頻率，以及我們在更新可能影響您使用服務時提供給您的進階通知。

若要了解 Intune 服務變更，請參閱 [Microsoft Intune 的新功能](/intune/deploy-use/Whats-new-in-microsoft-intune.md)。 [Microsoft Intune 部落格](http://blogs.technet.com/b/microsoftintune/)也會討論服務的變更，並提供實用秘訣，讓您充分利用 Intune。

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

## 選擇適合您的管理方案
您可以透過幾種方式設定 Intune 來管理和協助保護公司的行動裝置和電腦 (在本文件中稱之為**裝置**)。

-   **Intune 獨立設定。** 使用 Intune 中的 Web 式管理主控台來管理您組織中的裝置。 您可以在不含任何內部部署 IT 基礎結構的情況下使用 Intune，但是如果您使用 Intune 搭配 Active Directory 網域服務，就可以將透過網域服務來管理的網域使用者帳戶與 Intune 搭配使用。

-   **Intune 搭配 System Center Configuration Manager。** 使用 Configuration Manager 管理主控台來管理您企業中的電腦和行動裝置。 此設定可協助您透過單一主控台 (Configuration Manager 管理主控台) 來管理貴組織的所有裝置。 Configuration Manager 可支援非常大量的行動裝置、伺服器及電腦。 如需詳細資訊，請參閱 [System Center 2012 Configuration Manager 文件庫](https://technet.microsoft.com/library/gg682041.aspx)中的[如何使用 Configuration Manager 和 Microsoft Intune 管理行動裝置](http://go.microsoft.com/fwlink/?LinkID=271118)。  若要更多協助以決定哪種方法最適合您，請參閱 [選擇 Microsoft Intune 獨立和混合式行動裝置管理與 Configuration Manager](https://technet.microsoft.com/en-us/library/mt706478.aspx)。


## 深入了解 Intune
您可以使用這些資源來深入了解 Intune：

-   [Microsoft Intune 信任中心](http://www.microsoft.com/en-us/server-cloud/products/intune-trust-center/)提供 Intune 的安全性、隱私權和相容性做法的相關資訊，並說明其中一些 Intune 憑證。

-   [Microsoft Intune 的行動裝置管理功能](/intune/understand-explore/mobile-device-management-capabilities-in-microsoft-intune)

### 請參閱
[Microsoft Intune](https://docs.microsoft.com/intune/)
[System Center 2012 Configuration Manager 文件庫](https://technet.microsoft.com/library/gg682041.aspx)

[Microsoft Intune 的新功能](/intune/deploy-use/whats-new-in-microsoft-intune)



<!--HONumber=Jul16_HO3-->


