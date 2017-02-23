---
title: "Azure 入口網站的 Intune 簡介 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解 Azure 入口網站之 Intune 預覽版的基本概念，以及這項服務如何協助您管理裝置。"
keywords: 
author: robstackmsft
ms.author: robstack
nmanager: angrobe
ms.date: 01/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 4a085264-232a-4af0-97f1-747496c44517
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1024d2a33d843c628ffbb68f7b01a5d511191e7e
ms.openlocfilehash: f7f6dd79531d8d69eda3ed80bbb1cddf2692ab81


---


# <a name="introduction-to-microsoft-intune-in-the-azure-portal-preview"></a>Azure 入口網站之 Microsoft Intune 預覽版的簡介


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Microsoft Intune 即將移轉到 Azure 入口網站，這意味著您所使用的工作流程及功能將會有所改變。
新的入口網站可讓您預覽 Azure 入口網站中的新功能及更新功能，您可在此管理您組織的行動裝置、電腦及應用程式。
所有 Intune 功能最終都會移至 Azure，但您目前仍可在 Azure 入口網站中執行某些 Intune 工作。 這些新功能目前仍為預覽階段，所以仍有一些功能尚未在入口網站提供。 如需詳細資料，請檢閱[預覽版的新功能](#what's-new-in-the-preview)一節。

> [!IMPORTANT]
> **還沒1看到新的入口網站嗎？**<br>
> 我們已經開始為一些預選的租用戶導入預覽版。 現有的租用戶自 2017 初開始，將陸續移轉到新的服務平台上。 在移轉您的租用戶之前，您會在 Office 訊息中心收到相關通知。 如果您有任何關於租用戶移轉時間表的問題，請連絡我們的移轉團隊：[intunegrps@microsoft.com](mailto:intunegrps@microsoft.com)。


您可以在此文件庫中找到新的產品文件，而這份在文件在預覽期間仍會持續更新。 您對於這項服務如有任何建議，可在主題評論中留下您的意見反應。 我們十分希望您提供您的寶貴意見。

<!--- You can view the new Intune technical preview console in Azure at [portal.azure.com]. --->

以下是新版服務的一些重點摘要︰

- 所有 Enterprise Mobility + Security (EMS) (EMS) 元件全部整合在同一主控台內
- 主控台採用符合網路標準的 HTML
- Microsoft Graph API 可用於自動化許多動作
- Azure AD 群組可為所有 Azure 應用程式提供相容性
- 支援時下絕大多數的現代化網頁瀏覽器

如需傳統 Intune 主控台中的文件，請參閱 [Intune 文件庫](https://docs.microsoft.com/en-us/intune/)。

## <a name="before-you-start"></a>開始之前

若要使用 Azure 入口網站的 Intune ，必須具備 Intune 系統管理員與租用戶帳戶。 您可以前往[這裡](https://portal.office.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)註冊帳戶。

## <a name="supported-web-browsers-for-the-azure-portal"></a>Azure 入口網站支援的網頁瀏覽器

Azure 入口網站可以在時下絕大多數的電腦、 Mac 與平板電腦上執行 。 不支援行動電話。
目前支援的瀏覽器包括：

- Microsoft Edge (最新版本)
- Microsoft Internet Explorer 11
- Safari (最新版本，僅限 Mac)
- Chrome (最新版本)
- Firefox (最新版本)

如需支援的瀏覽器最新資訊，請參閱[這裡](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)。

## <a name="whats-in-this-library"></a>本文件庫內容

為方便您尋找所需的資訊，此文件採用 Intune 入口網站的配置。

![Azure 入口網站的工作負載](./media/azure-portal-workloads.png)

<!--- ### Plan and design
Information to help you plan and design your Intune environment.
[Read more](/intune-azure/plan-and-design/get-started) --->
### <a name="enroll-devices"></a>註冊裝置
如何將您的裝置交付 Intune 管理。
[閱讀更多](/intune-azure/enroll-devices/what-is)
### <a name="devices--groups"></a>裝置和群組
透過清查與報表了解您所管理的的裝置。
[閱讀更多](/intune-azure/manage-devices/what-is)
### <a name="manage-users"></a>管理使用者
了解您所管理的裝置使用者。
[閱讀更多](/intune-azure/manage-users/what-is)
### <a name="manage-apps"></a>管理應用程式
包含有關如何發行、管理、設定及保護應用程式的資訊。
[閱讀更多](/intune-azure/manage-apps/what-is-app-management)
### <a name="configure-devices"></a>設定裝置
包含您可用於在您管理的裝置上配置設定及功能之各種設定檔的資訊。
[閱讀更多](/intune-azure/configure-devices/what-are-device-profiles)
### <a name="set-device-compliance"></a>設定裝置相容性
定義裝置的合規性層級，然後據此回報不合規範的裝置[閱讀更多](/intune-azure/set-device-compliance/what-is-device-compliance)
### <a name="conditional-access"></a>條件式存取
依據您指定的條件，限制對 Exchange 服務的存取。
[閱讀更多](/intune-azure/conditional-access/what-is-conditional-access)
### <a name="access-control"></a>存取控制
控制可以執行各種 Intune 動作的使用者，以及這些動作的適用對象。 您可以利用涵蓋一些常見 Intune 案例的內建角色，或建立自己的角色。
[閱讀更多](/intune-azure/access-control/role-based-access-control)


## <a name="whats-new"></a>新功能

[了解預覽版的新功能](/intune-azure/introduction/whats-new)。


<!--HONumber=Feb17_HO1-->


