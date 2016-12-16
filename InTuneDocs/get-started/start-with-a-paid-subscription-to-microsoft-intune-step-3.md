---
title: "新增使用者並授與權限 | Microsoft Intune"
description: "同步處理內部部署使用者和 Azure AD 以及將您 Intune 訂閱的權限授與系統管理員"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 18d31a306549bae6dd44ab78d1dd08649ee71158


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>新增使用者並授與 Intune 系統管理權限

身為系統管理員，您可以直接新增使用者，或同步內部部署 Active Directory 中的使用者。 新增之後，使用者便可以註冊裝置，並存取公司資源。 您也可以授與使用者其他權限，包括「租用戶系統管理員」、「服務管理員」，以及「裝置註冊管理員」權限。

本主題可協助您︰

- [將使用者新增至 Intune](#add-users-to-intune)
- [授與其他 Intune 權限](#grant-intune-permissions)，包括︰
  - [租用戶系統管理員](#tenant-administrator)
  - [服務管理員](#service-administrator)
  - [裝置註冊管理員](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>將使用者新增至 Intune
您可以透過 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)，手動將使用者加入 Intune 訂閱，他們不會自動被指派 Intune 授權。 而是在稍後，Intune 租用戶系統管理員必須編輯使用者帳戶，以從 Office 365 入口網站將授權指派給使用者。 如需指引，請參閱[單獨或大量新增使用者到 Office 365 入口網站](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec)。

### <a name="sync-active-directory-and-add-users-to-intune"></a>同步處理 Active Directory 並將使用者新增至 Intune
您可以設定目錄同步處理，將使用者帳戶從內部部署 Active Directory 匯入到其中包括 Intune 使用者的 Microsoft Azure Active Directory (Azure AD)。 讓內部部署的 Active Directory 與所有 Azure Active Directory 服務連線，可更易於管理使用者身分識別。 您也可以設定單一登入功能，讓使用者的驗證體驗親切又簡單。 透過連結同一個 [Azure AD 租用戶](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)與多個服務，您之前已經同步的使用者帳戶就可用於所有雲端服務。

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>如何將內部部署使用者與 Azure AD 同步
同步處理使用者帳戶與 Azure AD 唯一需要的工具是 [Azure AD Connect 精靈](https://www.microsoft.com/download/details.aspx?id=47594)。 Azure AD Connect 精靈提供簡單和引導式的體驗，將內部部署身分識別基礎結構連線至雲端。  請選擇您的拓撲和需求 (單一或多個目錄、密碼同步或同盟)，精靈就會部署並設定讓連線運作所需的一切元件。 包括︰同步處理服務、Active Directory 同盟服務 (AD FS)，以及 Azure AD PowerShell 模組。

> [!TIP]
> Azure AD Connect 包含先前發行為 Dirsync 和 Azure AD Sync 的功能。 深入了解[目錄整合](http://technet.microsoft.com/library/jj573653.aspx)。 若要了解將使用者帳戶從本機目錄同步至 Azure AD 的優點，請參閱 [Active Directory 與 Azure AD 的相似性](http://technet.microsoft.com/library/dn518177.aspx)。

## <a name="grant-intune-permissions"></a>授與 Intune 權限

將使用者新增到 Intune 訂閱之後，我們建議您將系統管理權限授與幾個使用者帳戶。 若要管理 Intune，您可以授與使用者三種 Intune 權限
-   **租用戶系統管理員**：使用 Office 365 入口網站指派此類型系統管理員來管理您的訂用帳戶，包括計費、雲端存放裝置及管理可使用 Intune 的使用者。
-   **服務管理員**：使用 Microsoft Intune 系統管理員主控台指派此類型系統管理員來執行日常工作，包括管理裝置和電腦、部署原則和應用程式，以及執行報表。
-   **裝置註冊管理員**：使用 Microsoft Intune 系統管理員主控台指派此類型系統管理員來執行日常工作，包括管理裝置和電腦、部署原則和應用程式，以及執行報表。


### <a name="tenant-administrator"></a>租用戶系統管理員


租用戶系統管理員會被指派一個系統管理員角色，此角色定義該使用者的系統管理範圍以及他們可以管理的工作。 系統管理員角色在不同的 Microsoft 雲端服務之間是共通的，不過某些服務可能不支援部分角色。 Intune 使用下列角色：
- **全域管理員** - 存取 Intune 中的所有系統管理功能。 註冊 Intune 的人員將成為全域管理員。 全域管理員是唯一可以指派其他管理員角色的管理員。 在組織中可以有一個以上的全域管理員。 我們建議的最佳作法是只讓公司內幾位人員擁有此角色，以降低企業風險。
- **計費管理員** - 進行採購、管理訂閱、管理支援票證以及監控服務健康狀況。
- **密碼管理員** - 重設密碼、管理服務要求以及監控服務健康狀況。 密碼管理員限於重設使用者的密碼。
- **服務支援管理員** - 開啟 Microsoft 的支援要求，以及檢視服務儀表板和訊息中心。 除了開啟及讀取支援票證之外，他們擁有「僅檢視」權限。
- **使用者管理管理員** - 重設密碼、監控服務健康狀況、新增和刪除使用者帳戶和管理服務要求。 使用者管理管理員無法刪除全域管理員、建立其他管理員角色，或重設計費、全域和服務管理員的密碼。

依預設，您用來建立 Microsoft Intune 訂閱的帳戶是具有全域管理員角色的租用戶系統管理員。 身為租用戶系統管理員，您可以使用 Intune 系統管理員主控台來管理 Intune 的訂閱，以及從 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)指派租用戶系統管理員。 使用具有全域管理員角色的租用戶系統管理員可以存取入口網站並指派第一個服務管理員。 基於最佳作法，請勿使用租用戶系統管理員來進行日常管理工作。 租用戶系統管理員不需要 Intune 的授權即可存取 Intune 系統管理員主控台。 租用戶系統管理員是 Microsoft 雲端服務之間的共通概念。 當您訂閱 Intune 時，您的服務就是 Azure AD 的租用戶。 如需詳細資訊，請參閱[什麼是 Azure AD 目錄？](http://technet.microsoft.com/library/jj573650.aspx)的 Azure AD 租用戶一節。

身為租用戶系統管理員，使用 [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)可管理訂閱，包括下列工作 (若系統管理員角色允許)：

- 管理使用者帳戶，以及設定從內部部署 Active Directory 進行目錄同步處理
- 管理稱為安全性群組的使用者群組
- 指派使用者 Intune 授權
- 設定使用者登入您的訂用帳戶時所使用的網域名稱 (如 contoso.com)
- 管理計費和購物，包括授權和雲端儲存空間
- 尋找連結來檢視 Intune 服務的健全狀況

若要存取 Office 365 入口網站，您帳戶的登入狀態必須為 [已允許]。 此狀態與獲得訂閱的授權有所區別。 根據預設，所有使用者帳戶的狀態均為 [已允許]。 沒有系統管理員權限的使用者可以使用 Office 365 入口網站來重設 Intune 密碼。

### <a name="service-administrator"></a>服務系統管理員

根據預設，Intune 不會指派服務管理員。 反之，您必須使用具有全域管理員角色的租用戶系統管理員來指派訂閱的第一個服務系統管理員。 身為服務管理員，您可以使用 [Intune 系統管理員主控台](https://manage.microsoft.com/)來管理 Intune 的日常工作。 您可以從管理主控台中指派服務系統管理員。 服務管理員需要 Intune 的授權，以取系統管理主控台。

服務管理員會獲指派下列其中一種權限：
- **完整存取**：不受限制地存取 Intune 系統管理員主控台的所有區域、新增及管理其他服務管理員
- **唯讀存取**：Intune 系統管理員主控台所有區域的讀取權限，不能修改資料，但可以執行報表
- **服務台人員 - 群組節點**：讓服務系統管理員僅執行與服務台案例相關的工作，請參閱[根據系統管理員角色自訂 Intune 主控台檢視](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)

身為服務管理員，使用此入口網站可管理日常作業，包括：

- 建立及管理電腦和行動裝置的原則
- 上傳及部署軟體更新與應用程式
- 管理電腦上的 Endpoint Protection
- 檢視裝置狀態和執行報表

### <a name="device-enrollment-managers"></a>裝置註冊管理員

裝置註冊管理員是標準使用者帳戶，具有可註冊更多無使用者裝置的其他權限。 每位 Intune 使用者預設最多可以註冊五個裝置。 身為系統管理員，您可以將裝置註冊管理員權限授與使用者帳戶。 該帳戶可以註冊大量由公司所擁有的裝置。 如果會暫時性地將裝置指派給使用者，或可能以不需要使用者與裝置關聯的資訊站模式提供服務，則這非常實用。 如需詳細資訊，請參閱[裝置註冊管理員](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune)。

>[!div class="step-by-step"]

>[&larr; **網域設定**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**管理 Intune 授權** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Dec16_HO2-->


