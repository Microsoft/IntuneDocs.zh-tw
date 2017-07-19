---
title: "服務台疑難排解入口網站"
titleSuffix: Intune on Azure
description: "服務台人員使用疑難排解入口網站來解決使用者的技術問題"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 7a61c3703cd1016ef63c8baa371c3a21dca127fc
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2017
---
# <a name="help-users-with-the-troubleshooting-portal-in-microsoft-intune"></a>使用 Microsoft Intune 中的疑難排解入口網站協助使用者

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

針對入口網站進行疑難排解可讓服務台操作員和 Intune 系統管理員檢視使用者資訊，以修正使用者協助要求。 將服務台操作員納入其人員的組織可以將**服務台操作員**指派給一群使用者，這些使用者即可使用 [疑難排解] 刀鋒視窗來協助使用者。

例如，當使用者向支援人員諮詢 Intune 的技術問題時，服務台操作員會輸入使用者的名稱。 Intune 會顯示可協助解決許多第 1 層問題的相關資訊，例如使用者狀態、應用程式安裝失敗或合規性問題。 解決的問題可能包含：
- 裝置沒有回應
-   裝置無法取得 VPN 或 Wi-Fi 設定
-   應用程式安裝失敗


## <a name="add-help-desk-operators"></a>新增服務台操作員
Intune 系統管理員可以使用兩種方式，將服務台操作員權限指派給使用者：
- 指派內建的**服務台操作員**角色
- 建立並指派自訂角色

## <a name="assign-help-desk-operator-role"></a>指派服務台操作員角色
身為 Intune 管理員，您可以將服務台操作員角色指派給使用者群組。 該群組的成員可以使用管理入口網站。 每個服務台操作員都必須要有 Intune 授權來存取 Intune 入口網站。 了解如何[指派 Intune 授權](licenses-assign.md)。

1. 以 Intune 系統管理員身分，登入 Intune 入口網站，然後選取 [Intune 角色]。
2. 在 [Intune 角色] 工作負載上，選取 [服務台操作員]  >  [指派]，然後選取 [指派]。
  ![顯示反白顯示的 Intune 角色，以及包含服務台操作員 (已反白顯示 [指派] 且 [指派] 周圍出現紅框) 之內建角色清單的 Intune 入口網站螢幕擷取畫面](./media/help-desk-user-assign.png)
3. 輸入 [指派名稱] (必要)、[指派描述] (選擇性)，然後指派 [成員 (群組)] 和 [範圍 (群組)]。
4. 「服務台操作員」角色的成員現在即可使用疑難排解入口網站。

如需 Intune 角色的詳細資訊，請參閱 [Intune 角色 (RBAC)](role-based-access-control.md)。

## <a name="create-a-custom-role-for-troubleshooting"></a>建立自訂角色進行疑難排解
身為 Intune 管理員，您可以建立自訂角色，讓使用者以符合您組織需要的權限使用疑難排解入口網站。 如需 Intune 角色的詳細資訊，請參閱 [Intune 角色 (RBAC)](role-based-access-control.md)。

![顯示反白顯示的 Intune 角色，以及包含服務台操作員之內建角色清單的 Intune 入口網站螢幕擷取畫面](./media/help-desk-user-add.png)

若要使用 Intune 主控台來檢視服務台，自訂服務台角色應該具有下列權限：
- MobileApps：讀取
- ManagedApps：讀取
- ManagedDevices：讀取
- Organization：讀取

## <a name="access-the-troubleshooting-portal"></a>存取疑難排解入口網站

服務台人員和 Intune 系統管理員有兩種方式可以存取疑難排解入口網站：
- 在網頁瀏覽器中開啟 [http://aka.ms/intunetroubleshooting](http://aka.ms/intunetroubleshooting)。
- 在 Intune 入口網站中，移至 [說明及支援]  >  [疑難排解]。

![Intune 疑難排解工作負載 (包含 [選取使用者] 連結) 的螢幕擷取畫面](media/help-desk-user.png)

## <a name="use-the-troubleshooting-portal"></a>使用疑難排解入口網站

在疑難排解入口網站中，您可以選擇 [選取使用者] 來檢視使用者的資訊。 使用者資訊可協助您了解使用者與其裝置的目前狀態。 疑難排解入口網站會顯示下列疑難排解詳細資料︰
- **租用戶狀態**
- **使用者狀態**
- **裝置**及裝置動作
- **群組成員資格**
- **應用程式保護狀態**
