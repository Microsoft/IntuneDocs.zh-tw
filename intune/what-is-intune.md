---
title: "Azure 入口網站中的 Intune 簡介"
titlesuffix: Azure portal
description: "了解 Azure 入口網站中 Intune 的基本概念，以及這些概念如何協助您管理裝置。"
keywords: 
author: arob98
ms.author: angrobe
nmanager: angrobe
ms.date: 07/17/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: e3002d08506b68069d617c413a9c3801cf4326f8
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2017
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure 入口網站之 Microsoft Intune 的簡介


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 現已在 Azure 入口網站上提供，這意味著您慣用的工作流程及功能現在會有所改變。
新的入口網站在 Azure 入口網站中提供新功能及更新功能，您可在其中管理您組織的行動裝置、電腦及應用程式。

* [我的功能在 Azure 的什麼位置？](ui-changes.md)此參考會向您顯示因為移至 Azure 而變更的特定工作流程與 UI。
* [Azure 入口網站中的 Intune 傳統群組](groups-get-started.md)說明移至 Azure Active Directory 安全性群組對群組管理的含意。




您可以在此文件庫中找到新入口網站的相關資訊，這項資訊會不斷更新。 您對於這項服務如有任何建議，可在主題評論中留下您的意見反應。 我們十分希望您提供您的寶貴意見。

以下是新版服務的一些重點摘要︰

- 所有 Enterprise Mobility + Security (EMS) (EMS) 元件全部整合在同一主控台內
- 主控台採用符合網路標準的 HTML
- Microsoft Graph API 可用於自動化許多動作
- Azure Active Directory (AD) 群組可為所有 Azure 應用程式提供相容性
- 支援時下絕大多數的現代化網頁瀏覽器

> [!IMPORTANT]
> **還沒看到新的入口網站嗎？**<br>
> 現有的租用戶將移轉至新的體驗。 在您的租用戶移轉之前，通知會顯示在 Office 訊息中心。
>
> 在 2017 年 1 月之前建立的 Intune 帳戶，將需要進行一次性移轉，才能在 Azure 中使用 Apple 註冊工作流程。 移轉的排程尚未公告。 如果您現有的帳戶無法存取 Azure 入口網站，建議您建立試用帳戶。
>
> 請檢閱潛在封鎖程式的清單 https://blogs.technet.microsoft.com/intunesupport/2017/05/17/intune-migration-blockers-for-grouping-targeting/


## <a name="before-you-start"></a>開始之前

若要使用 Azure 入口網站的 Intune ，必須具備 Intune 系統管理員與租用戶帳戶。 如果您還沒有帳戶，請[註冊帳戶](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)。

## <a name="supported-web-browsers-for-the-azure-portal"></a>Azure 入口網站支援的網頁瀏覽器

Azure 入口網站可以在時下絕大多數的電腦、 Mac 與平板電腦上執行 。 不支援行動電話。
目前支援的瀏覽器包括：

- Microsoft Edge (最新版本)
- Microsoft Internet Explorer 11
- Safari (最新版本，僅限 Mac)
- Chrome (最新版本)
- Firefox (最新版本)

如需所支援瀏覽器的最新資訊，請參閱 [Azure 入口網站](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)。

## <a name="whats-in-this-library"></a>本文件庫內容

為方便您尋找所需的資訊，此文件採用 Azure 入口網站的配置。

![Azure 入口網站的工作負載](./media/azure-portal-workloads.png)

### <a name="introduction-and-get-started"></a>簡介和開始使用
此小節包含[簡介資訊](introduction-intune.md)，可以協助您開始使用 Intune。
### <a name="plan-and-design"></a>規劃和設計
可協助您[計劃和設計](/intune-classic/plan-design/introduction) Intune 環境的資訊。
### <a name="device-enrollment"></a>裝置註冊
[如何將您的裝置交付 Intune 管理](device-enrollment.md)。
### <a name="device-compliance"></a>裝置合規性
[定義裝置的合規性層級，並回報所有不符合規範的裝置](device-compliance.md)。
### <a name="device-configuration"></a>裝置設定
[了解您可用於在您管理之裝置上進行設定及功能的各種設定檔](device-profiles.md)。
### <a name="devices"></a>裝置
[透過清查與報表了解您所管理的裝置](device-management.md)。
### <a name="mobile-apps"></a>行動裝置應用程式
[如何發行、管理、設定和保護應用程式](app-management.md)。
### <a name="conditional-access"></a>條件式存取
[依據您指定的條件，限制對 Exchange 服務的存取](conditional-access.md)。
### <a name="on-premises-access"></a>內部部署存取
[設定 Exchange ActiveSync 和 Exchange 內部部署的存取](/intune-classic/deploy-use/mobile-device-management-with-exchange-activesync-and-microsoft-intune)
### <a name="users"></a>Users
[了解您管理之裝置的使用者，並將資源整理歸入群組](users-add.md)。
### <a name="groups"></a>中
[了解如何搭配 Intune 使用 Azure Active Directory 群組](groups-get-started.md)
### <a name="intune-roles"></a>Intune 角色
[控制可以執行各種 Intune 動作的使用者，以及這些動作的適用對象](role-based-access-control.md)。 您可以利用涵蓋一些常見 Intune 案例的內建角色，或建立自己的角色。
### <a name="software-updates"></a>軟體更新
[了解如何為 Windows 10 裝置設定軟體更新](windows-update-for-business-configure.md)。



## <a name="whats-new"></a>新功能

[Intune 的新功能](whats-new.md)。
