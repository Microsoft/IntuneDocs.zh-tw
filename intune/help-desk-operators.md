---
title: "服務台疑難排解入口網站"
titlesuffix: Azure portal
description: "服務台人員使用疑難排解入口網站來解決使用者的技術問題"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 14b47727428fcd6a16f9960e21f70ee64c7757d1
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2017
---
# <a name="use-the-troubleshooting-portal-to-help-users"></a>使用疑難排解入口網站協助使用者

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

疑難排解入口網站可協助技術服務人員和 Intune 系統管理員檢視使用者資訊，以解決使用者協助要求。 將服務台操作員納入其人員的組織可以將**服務台操作員**指派給一群使用者，這些使用者即可使用 [疑難排解] 刀鋒視窗來協助使用者。

例如，當使用者向支援人員諮詢 Intune 的技術問題時，服務台操作員會輸入使用者的名稱。 Intune 會顯示可協助解決許多第 1 層問題的實用資料，包括：
- 使用者狀態
- 作業
- 相容性問題
- 裝置沒有回應
-   裝置無法取得 VPN 或 Wi-Fi 設定
-   應用程式安裝失敗

## <a name="add-help-desk-operators"></a>新增服務台操作員
身為 Intune 管理員，您可以將服務台操作員角色指派給使用者群組。 該群組的成員可以使用 Azure 入口網站來為使用者的問題進行疑難排解。 每個服務台操作員都必須要有 Intune 授權來存取 Azure 入口網站。 了解如何[指派 Intune 授權](licenses-assign.md)。

若要新增支援人員使用者：
1. 視需要[將使用者新增至 Intune](users-add.md)。
2. [建立支援人員群組](groups-add.md)，並將使用者新增至該群組。
3. [指派 RBAC 技術服務人員角色](role-based-access-control.md#built-in-roles).

  ![顯示反白顯示的 Intune 角色，以及包含技術服務人員之內建角色清單的 Azure 入口網站螢幕擷取畫面](./media/help-desk-user-add.png)您也可以[建立自訂角色](role-based-access-control.md#custom-roles)，以進一步修改並授與技術服務人員存取權。  技術服務人員需要下列權限，以協助為使用者問題進行疑難排解：
    - MobileApps：讀取
    - ManagedApps：讀取
    - ManagedDevices：讀取
    - Organization：讀取
    - DeviceCompliancePolices：讀取
    - DeviceConfigurations：讀取

4. 若要將檢視服務健全狀況和開啟 Intune 支援票證的權限授與技術服務人員，請以**服務管理員**身分[將系統管理員權限授與使用者](https://docs.microsoft.com/azure/active-directory/active-directory-users-assign-role-azure-portal)。 請勿授與 **Intune 服務管理員**權限，因為此目錄角色具有比技術服務人員所需更多的權限。

## <a name="access-the-troubleshooting-portal"></a>存取疑難排解入口網站

服務台人員和 Intune 系統管理員有兩種方式可以存取疑難排解入口網站：
- 在網頁瀏覽器中開啟 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)，僅檢視疑難排解入口網站。
  ![疑難排解主控台的螢幕擷取畫面](./media/help-desk-console.png)
- 登入 Azure 入口網站，選擇 [More Services] (更多服務) > [監視 + 管理] > [Intune]，然後移至 [說明及支援] > [疑難排解]。

按一下 [選取使用者] 以檢視使用者及其詳細資料。

## <a name="use-the-troubleshooting-portal"></a>使用疑難排解入口網站

在疑難排解入口網站中，您可以選擇 [選取使用者] 來檢視使用者的資訊。 使用者資訊可協助您了解使用者與其裝置的目前狀態。 疑難排解入口網站會顯示下列疑難排解詳細資料︰
- **帳戶狀態**
- **使用者狀態**
- **裝置**及裝置動作
- **群組成員資格**
- **應用程式保護狀態**
