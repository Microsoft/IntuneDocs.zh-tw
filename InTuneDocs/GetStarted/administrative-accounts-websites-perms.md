---
title: "系統管理帳戶、網站和權限 | Microsoft Intune"
description: "系統管理帳戶權限網站"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: db3075e7-38fd-4dfe-b266-26aed10ac8ea
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0d422b421c3716ad576c4fc565b181dec28c947e
ms.openlocfilehash: 69b19cec363c769209dab02a941f286057e9dc3e


---

# Microsoft Intune 中的系統管理帳戶、網站和權限

設定 Microsoft Intune 之前，請檢閱本主題及[啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)中列示的其他需求。

若要管理 Intune，您將使用︰
- 兩種類型的系統管理員帳戶
- 具有其他權限的使用者帳戶
- 兩個 Web 架構系統管理主控台/入口網站，授與系統管理員存取權，以存取他們應該管理的項目。

下列各節將說明這些帳戶和入口網站。

## 系統管理員帳戶和具有特殊權限的使用者帳戶

以下是您會在 Intune 中使用的帳戶及權限。

### 租用戶系統管理員
|權限層級|詳細資訊|
|--------------------------|-------------------------|
|租用戶系統管理員會被指派一個系統管理員角色，此角色定義該使用者的系統管理範圍以及他們可以管理的工作。<br /><br />系統管理員角色在不同的 Microsoft 雲端服務之間是共通的，不過某些服務可能不支援部分角色。<br /><br /> Microsoft Intune 使用下列角色：<br /><br />- 全域管理員<br />- 計費管理員<br />- 密碼管理員<br />- 服務支援系統管理員<br />- 使用者管理管理員|依預設，您用來建立 Microsoft Intune 訂閱的帳戶是具有全域管理員角色的租用戶系統管理員。<br /></br>  身為租用戶系統管理員，您可以使用 [!INCLUDE[wit_icp_1](../includes/wit_icp_1_md.md)] 來管理 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的訂閱，以及從 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)] 指派租用戶系統管理員。<br /><br />使用具有全域管理員角色的租用戶系統管理員可以存取 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)]來指派第一個服務系統管理員。 基於最佳作法，請勿使用租用戶系統管理員來進行日常管理工作。 租用戶系統管理員不需要 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的授權即可存取 [!INCLUDE[wit_icp_2](../includes/wit_icp_2_md.md)]。<br /><br />租用戶系統管理員是 Microsoft 雲端服務之間的共通概念。 當您訂閱 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 時，您的服務就是 Microsoft Azure AD 的租用戶。 請參閱[什麼是 Azure AD 目錄？](http://technet.microsoft.com/library/jj573650.aspx)的 Azure AD 租用戶一節。|


### 服務系統管理員
|權限層級|詳細資訊|
|--------------------------|-------------------------|
|服務系統管理員會獲指派下列其中一種權限：<br /><br />**完整存取權**：授與 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 所有區域的存取權，而無任何限制。 這也可新增及管理其他服務系統管理員。<br /><br />**唯讀存取權**：授與 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 所有區域的讀取權限。 唯讀服務系統管理員無法修改資料，但可以執行報表。<br /><br />**服務台人員 - 群組節點**：授與權限，讓服務管理員只執行一組通常會與服務台人員案例相關聯的工作。 如需此權限集合的資訊，請參閱[根據系統管理員角色自訂 Intune 主控台檢視](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)。|根據預設，[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 不會指派服務系統管理員。 反之，您必須使用具有全域管理員角色的租用戶系統管理員來指派訂閱的第一個服務系統管理員。 </br></br> 身為服務系統管理員，您可以使用 [!INCLUDE[wit_adminconsole](../includes/wit_adminconsole_md.md)] 來管理 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 日常工作。<br /><br />您可以從管理主控台中指派服務系統管理員。 服務系統管理員需要 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的授權，才能存取管理主控台。|



### 裝置註冊管理員
|權限層級|詳細資訊|
|--------------------------|-------------------------|
|裝置註冊管理員是標準使用者帳戶，具有可註冊五個以上裝置的其他權限。|每位 [!INCLUDE[wit_firstref](../includes/wit_firstref_md.md)] 使用者預設最多可以註冊五個裝置。 不過，您可以將裝置註冊管理員權限提供給使用者帳戶，然後使用該帳戶來註冊大型公司所擁有裝置的群組。 如果會暫時性地將裝置指派給使用者，或可能以不需要使用者與裝置關聯的資訊站模式提供服務，則這非常實用。|


## Intune 系統管理網站
 不同的系統管理工作需要您使用下列一個系統管理網站，您可以使用[支援的網頁瀏覽器](supported-web-browsers.md)來存取該網站。

- [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)
- [Microsoft Intune 系統管理員主控台](https://admin.manage.microsoft.com/)

### [Office 365 入口網站](http://go.microsoft.com/fwlink/p/?LinkId=698854)

**身為租用戶系統管理員，使用此入口網站可管理訂閱**，包括下列工作 (若系統管理員角色允許)：

- 管理訂閱的使用者帳戶，以及設定從內部部署 Active Directory 進行目錄同步處理。
- 管理稱為安全性群組的使用者群組。
- 將使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的授權指派給使用者。
- 設定用於訂閱的網域名稱。 網域名稱定義使用者用來登入的帳戶。
- 管理訂閱的計費和購買詳細資料，包括您擁有的授權數目，或是您可以使用的雲端存放裝置空間容量。
- 尋找連結來檢視 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 服務的健全狀況。
- 身為租用戶系統管理員，您可以登入 Office 365 帳戶入口網站來管理訂閱，即使您的帳戶沒有獲指派使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的授權。
- 任何擁有 Intune 授權但不是系統管理員的使用者，都可以使用此入口網站來重設其帳戶密碼並編輯其設定檔。
- 若要存取 Office 365 入口網站，您帳戶的登入狀態必須為 [已允許]。 此狀態與獲得訂閱的授權有所區別。 根據預設，所有使用者帳戶的狀態均為 [已允許]。


### [Microsoft Intune 系統管理員主控台](https://admin.manage.microsoft.com/)

**身為服務系統管理員，使用此入口網站可管理日常作業**，包括：

- 設定電腦和行動裝置的原則。
- 上傳和部署軟體，例如軟體更新和應用程式。
- 管理電腦上的 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] Endpoint Protection。
- 檢視裝置狀態和執行報表。
- 登入此入口網站。 您必須具有服務系統管理員權限，或必須是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。


唯有具有服務系統管理員權限的使用者，或是具有全域系統管理員角色的租用戶系統管理員，才能登入此入口網站。 若要存取管理主控台，您的帳戶必須擁有使用 [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] 的授權，且登入狀態必須為 [已允許]。

深入了解[新增您訂閱的使用者](start-with-a-paid-subscription-to-microsoft-intune-step-3.md)及[指派您訂閱的授權](start-with-a-paid-subscription-to-microsoft-intune-step-4.md)。

 ### 請參閱
 [啟動 Microsoft Intune 前的須知事項](what-to-know-before-you-start-microsoft-intune.md)



<!--HONumber=Oct16_HO4-->


