---
title: "管理來自商務用 Microsoft 網上商店的應用程式"
titlesuffix: Azure portal
description: "了解如何將應用程式從商務用 Microsoft 網上商店同步到 Intune，然後加以指派及追蹤。"
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4460924b3e53a9540ff21aa009a0c028de92f26f
ms.sourcegitcommit: 1978a30ab1af0f43aa5f447690d0bbcdcb9b563b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/24/2018
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>以 Microsoft Intune 管理購自商務用 Microsoft 網上商店的應用程式

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


[商務用 Microsoft 網上商店](https://www.microsoft.com/business-store)可讓您為組織個別或大量尋找及購買應用程式。 將市集連接到 Microsoft Intune，就可以從 Azure 入口網站管理大量採購的應用程式。 例如：
* 您可以同步處理您使用 Intune 從市集購買的應用程式的清單。
* 經過同步的應用程式會出現在 Intune 系統管理主控台；一如其他應用程式，您也可以指派這些應用程式。
* 您可以追蹤有多少可用的授權，以及 Intune 管理主控台中正使用多少授權。
* 如果可用授權數目不足，Intune 會禁止指派及安裝應用程式。
* 當使用者離開企業，或系統管理員移除使用者及使用者裝置時，受商務用 Microsoft Store 管理的應用程式就會自動撤銷授權。

## <a name="before-you-start"></a>開始之前

從商務用 Microsoft 網上商店開始同步及指派應用程式之前，請檢閱下列資訊：

- 將 Intune 設定為組織的行動裝置管理授權單位。
- 您必須已在商務用 Microsoft 網上商店註冊帳戶。
- 一旦您將 Intune 與商務用 Microsoft Store 帳戶建立關聯，未來將無法變更為不同帳戶。
- 從市集購買的應用程式無法手動加入 Intune 中，或從中刪除。 它們只能與商務用 Microsoft 網上商店同步處理。
- 您透過商務用 Microsoft Store 購買的線上和離線授權應用程式都會同步處理到 Intune 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 
- 線上應用程式安裝由市集來管理。
- 免費的離線應用程式也可以同步處理至 Intune。 這些應用程式會透過 Intune 安裝，而不透過市集。
- 裝置必須加入 Active Directory Domain Services 或工作場所，才能使用此功能。
- 註冊的裝置必須使用 Windows 10 的 1511 版或更新版本。

此外，從商務用 Microsoft 市集同步處理的相關集合和離線授權應用程式，現在將合併成 UI 中的單一應用程式項目。 來自個別套件的任何部署詳細資料都會移轉到單一項目。 若要在 Azure 入口網站中檢視相關的集合，請選取 [Mobile Apps] 刀鋒視窗中的 [應用程式授權]。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>建立您的商務用 Microsoft 網上商店帳戶與 Intune 的關聯
在 Intune 主控台中啟用同步處理之前，您必須將您的市集帳戶設定為使用 Intune 做為管理工具︰
1. 請確定使用您用來登入 Intune 的相同租用戶帳戶來登入商務用市集。
2. 在商務用市集中，選擇 **[設定]** > **[管理工具]**。
3. 在 [管理工具] 頁面上，選擇 **[Add a management tool (新增管理工具)]**，然後選擇 **[Microsoft Intune]**。

> [!NOTE]
> 您先前可能只建立了某個用來指派應用程式的管理工具與商務用 Microsoft 網上商店的關聯。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。

您現在可以繼續進行，並在 Intune 主控台中設定同步處理。

## <a name="configure-synchronization"></a>設定同步處理

1. 登入 Azure 入口網站。
2. 選擇 [更多服務]  >  [監視 + 管理]  >  [Intune]。
3. 在 [Intune] 刀鋒視窗上，選擇 [行動應用程式]。
4. 在 [Mobile Apps] 刀鋒視窗中選擇 [安裝] > [商務用 Microsoft 網上商店]。
5. 按一下 [啟用]。
6. 若還未執行此動作，請遵循前文所述按一下連結來註冊商務用 Microsoft 網上商店並關聯您的帳戶。
7. 從 [語言] 下拉式清單中，選擇來自商務用 Microsoft 網上商店應用程式在 Azure 入口網站中顯示的語言。 無論顯示的語言為何，可用時將以使用者的語言安裝。
8. 按一下 [同步]，以取得您從 Microsoft 網上商店購買的應用程式，將其同步到 Intune。
9. 按一下 **[儲存]**。

## <a name="synchronize-apps"></a>同步處理應用程式

1. 在 [Mobile Apps] 工作負載中，選擇 [安裝] > [商務用 Microsoft 網上商店]。
2. 按一下 [同步]，以取得您從 Microsoft 網上商店購買的應用程式，將其同步到 Intune。

## <a name="assign-apps"></a>指派應用程式

您可以使用指派任何其他 Intune 應用程式的方式來指派市集應用程式。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。 但您也可以不從 [所有應用程式] 頁面而改從 [授權的應用程式] 頁面指派應用程式。

離線應用程式可以將目標設為使用者群組、 裝置群組或包含使用者和裝置的群組。
離線應用程式可以針對裝置上的特定使用者或裝置上的所有使用者進行安裝。 


當您指派商務用 Microsoft 網上商店應用程式時，安裝應用程式的每個使用者會使用一個授權。 如果您對某個已指派的應用程式使用了所有可用的授權，則無法再指派任何複本。 請採取下列其中一個動作：
* 從某些裝置解除安裝應用程式。
* 將目前指派的範圍減少，僅以您擁有足夠授權的使用者為目標。
* 從商務用 Microsoft 網上商店購買更多份應用程式。


