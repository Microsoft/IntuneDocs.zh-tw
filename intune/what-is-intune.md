---
title: "Azure 入口網站中的 Intune 簡介"
titlesuffix: 
description: "在 Azure 入口網站中，現在已可使用 Microsoft Intune。 在 Azure 入口網站中取得 Intune 的基本概念。"
keywords: 
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/28/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.suite: ems
ms.custom: 
ms.openlocfilehash: c9c8485a3ab68be745c8903659df0fd35af2a644
ms.sourcegitcommit: aafed032492c1b5861d7097a335f9bbb29ce3221
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2018
---
# <a name="introduction-to-microsoft-intune-in-the-azure-portal"></a>Azure 入口網站之 Microsoft Intune 的簡介


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Microsoft Intune 現在就如同其他 Azure 服務，已可在 Azure 入口網站中使用。 選取 Azure 入口網站內的 [Intune]，您就能管理組織的行動裝置、電腦及應用程式。

>[!NOTE] 
> 如果您使用過舊版的 Microsoft Intune，以下資訊會對您有幫助：
    * [我的功能在 Azure 的什麼位置？](ui-changes.md)此參考會向您顯示因為移至 Azure 而變更的特定工作流程與 UI。
    * [Azure 入口網站中的 Intune 傳統群組](groups-get-started.md)說明移至 Azure Active Directory 安全性群組對群組管理的含意。

Azure 入口網站中的 Microsoft Intune 體驗重點包括：

- 所有 Enterprise Mobility + Security (EMS) (EMS) 元件全部整合在同一主控台內
- 主控台採用符合網路標準的 HTML
- Microsoft Graph API 可用於自動化許多動作
- Azure Active Directory (AD) 群組可為所有 Azure 應用程式提供相容性
- 支援時下絕大多數的現代化網頁瀏覽器

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

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure 入口網站中的 Microsoft Intune

您可以在 [Azure 入口網站](https://portal.azure.com)中找到 Microsoft Intune 服務。 Azure 中有多項服務，而其中幾項您可能不會定期使用。 如需自訂入口網站體驗的快速指南，請參閱[開始在 Azure 入口網站中使用 Intune](get-started-azure.md)。

## <a name="the-microsoft-intune-documentation"></a>Microsoft Intune 文件

本主題及整份 Microsoft Intune 文件集均持續更新。 您對於這項服務如有任何建議，可在主題評論中留下您的意見反應。 我們十分希望您提供您的寶貴意見。

文件反映了 Microsoft Intune 在 Azure 入口網站中的版面配置 (如下所示)，因此較容易找到您需要的資訊。

![Azure 入口網站的工作負載](./media/azure-portal-workloads.png)

### <a name="documentation-guide"></a>文件指南

使用下表快速尋找並了解 Microsoft Intune 的主要領域。

| 區段                                                      | 說明                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [簡介和入門](introduction-intune.md)       | 了解 Intune 的基本概念，包括：<br /> - 常用解決方案<br /> - Microsoft Intune 運作方式<br /> - Intune 中的裝置管理<br /> - Intune 中的應用程式管理<br /> - 已註冊及未註冊裝置的 Enterprise Mobility Management (EMM)                                                         |
| [規劃和設計](planning-guide.md)                         | 協助您成功規劃及設計 Microsoft Intune 環境的指南。                                                                                                                                                                                                             |
| [裝置註冊](device-enrollment.md)                    | 了解 Microsoft Intune 如何協助您透過向 Intune 服務註冊員工裝置來加以管理。 有數種方法可以註冊員工裝置。                                                                                                         |
| [裝置合規性](device-compliance.md)                    | Intune 裝置合規性政策會定義規則與設定，裝置必須遵循才能讓 Microsoft Intune 將其視為符合規範。 例如，要求裝置存取的密碼、為裝置加密及要求最低 OS 版本都是合規性的例子。 |
| [裝置設定](device-profiles.md)                   | 建立裝置設定檔，在您使用 Microsoft Intune 管理的所有裝置上進行包含功能在內的設定。 例如，您可以設定通知、資料共用、電子郵件支援、wi-fi 連線、憑證及端點保護等功能。              |
| [裝置](device-management.md)                              | 確保您管理的裝置只為終端使用者提供他們進行工具所需要的資源，同時保護公司資料遠離風險。 透過檢閱員工裝置清查及執行遠端裝置動作來管理裝置。                                                      |
| [行動裝置應用程式](app-management.md)                             | 了解如何新增、部署、監視、設定及保護應用程式。                                                                                                                                                                                                                             |
| [條件式存取](conditional-access.md)                  | 定義以裝置為基礎及以應用程式為基礎的條件，以限制公司資料的存取。                                                                                                                                                                                                            |
| [使用者](users-add.md)                                        | 了解如何新增您管理的裝置及應用程式使用者。                                                                                                                                                                                                                                           |
| [群組](groups-get-started.md)                              | 了解如何使用 Intune 建立及管理群組。 使用群組就能快速指派裝置及應用程式設定與保護原則。                                                                                                                                             |
| [Intune 角色](role-based-access-control.md)                 | 了解如何控制可以執行各種 Intune 動作的使用者，以及這些動作的應用方式。 您可以利用涵蓋一些常見 Intune 案例的內建角色，或建立自己的角色。                                                                                 |
| [軟體更新](windows-update-for-business-configure.md) | 了解如何為 Windows 10 裝置設定軟體更新。                                                                                                                                                                                                                                  |

## <a name="whats-new"></a>新功能

若要了解 Microsoft Intune 的最新功能，請參閱[新增功能](whats-new.md)。
