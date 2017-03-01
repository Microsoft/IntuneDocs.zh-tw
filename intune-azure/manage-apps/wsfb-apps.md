---
title: "管理商務用 Windows 市集的應用程式 | Intune Azure 預覽版 | Microsoft Docs"
description: "Intune Azure 預覽版︰了解如何將應用程式從商務用 Windows 市集同步到 Intune，然後加以指派及追蹤。"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b4d095506215b775d56d172e9aabae1737757310
ms.openlocfilehash: b213fcaae8f17af412687d01df6ea27b39b3edb9
ms.lasthandoff: 02/16/2017

---

# <a name="how-to-manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune"></a>如何使用 Microsoft Intune 管理購自商務用 Windows 市集的應用程式

[!INCLUDE[azure_preview](../includes/azure_preview.md)]


[商務用 Windows 市集](https://www.microsoft.com/business-store)可讓您為組織個別或大量尋找和購買應用程式。 連接市集與 Microsoft Intune 可讓您從 Intune 入口網站管理大量採購的應用程式。 例如：
* 您可以同步處理您使用 Intune 從市集購買的應用程式的清單。
* 經過同步的應用程式會出現在 Intune 系統管理主控台。一如其他應用程式，您也可以指派這些應用程式。
* 您可以追蹤有多少可用的授權，以及 Intune 管理主控台中正使用多少授權。
* 如果可用授權數目不足，Intune 會禁止部署及安裝應用程式。

## <a name="before-you-start"></a>開始之前
從商務用 Windows 市集開始同步處理及部署應用程式之前，請檢閱下列資訊︰
* 您必須將 Intune 設定為組織的行動裝置管理授權單位。
* 您必須已在商務用 Windows 市集註冊帳戶。
* 一旦您將 Intune 與企業用 Windows 市集帳戶建立關聯，未來將無法變更為不同帳戶。
* 從市集購買的應用程式無法手動加入 Intune 中，或從中刪除。 它們只能與商務用 Windows 市集同步。
* Intune 只會同步處理您透過商務用 Windows 市集購買的線上授權應用程式。
* 裝置必須加入 Active Directory Domain Services 或工作場所，才能使用此功能。
* 註冊的裝置必須使用 Windows 10 的 1511 版或更新版本。

## <a name="associate-your-windows-store-for-business-account-with-intune"></a>將您的商務用 Windows 市集帳戶與 Intune 相關聯
在 Intune 主控台中啟用同步處理之前，您必須將您的市集帳戶設定為使用 Intune 做為管理工具︰
1. 請確定使用您用來登入 Intune 的相同租用戶帳戶來登入商務用市集。
2. 在商務用市集中，選擇 **[設定]** > **[管理工具]**。
3. 在 [管理工具] 頁面上，選擇 **[Add a management tool (新增管理工具)]**，然後選擇 **[Microsoft Intune]**。

> [!NOTE]
> 如果您使用多種管理工具來部署商務用 Windows 市集應用程式，以前只能建立其中一種與商務用 Windows 市集的關聯性。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。

您現在可以繼續進行，並在 Intune 主控台中設定同步處理。

## <a name="configure-synchronization"></a>設定同步處理

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [其他]  >  [Intune]。
3. 在 **Intune** 刀鋒視窗上選擇 [管理應用程式]。
1. 在 [行動應用程式] 刀鋒視窗中選擇 [安裝]  >  [商務用 Windows 市集]。
2. 按一下 [啟用]。
3. 若還未執行此動作，請依照前文所述按一下連結註冊商務用 Windows 市集及關聯您的帳戶。
5. 從 [語言] 下拉式清單中，選擇商務用 Windows 市集應用程式在 Intune 主控台中的顯示語言。 無論顯示的語言為何，可用時將以使用者的語言安裝。
6. 按一下 [同步]，以取得您從 Windows 市集購買的應用程式，將其同步到 Intune。

## <a name="synchronize-apps"></a>同步處理應用程式

1. 在**管理應用程式**工作負載中，選擇 [安裝]  >  [商務用 Windows 市集]。
2. 按一下 [同步]，以取得您從 Windows 市集購買的應用程式，將其同步到 Intune。

## <a name="assign-apps"></a>指派應用程式

您可以使用部署任何其他 Intune 應用程式的方式來部署市集應用程式。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](deploy-apps.md)。 但您也可以不從 [所有應用程式] 頁面而改從 [授權的應用程式] 頁面指派應用程式。

當您部署商務用 Windows 市集應用程式時，安裝該應用程式的每位使用者都會佔用一個授權。 如果您對某個已部署的應用程式使用所有可用的授權，將無法再部署任何複本。 您必須採取下列其中一個動作：
* 從某些裝置解除安裝應用程式。
* 將目前部署的範圍減少，僅以您擁有足夠授權的使用者為目標。
* 從商務用 Windows 市集購買更多份應用程式。

> [!Important]
> 只有原先註冊裝置的使用者可使用已部署的應用程式。 其他使用者都不能存取應用程式。

