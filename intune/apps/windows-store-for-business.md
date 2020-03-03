---
title: 管理來自商務用 Microsoft Store 的 VPP 應用程式
titleSuffix: Microsoft Intune
description: 了解如何將應用程式從商務用 Microsoft Store 同步到 Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6faaa800d8dedc53ab20f1dae2c3049132642b7d
ms.sourcegitcommit: 29f3ba071c9348686d3ad6f3b8864d8557e05b97
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2020
ms.locfileid: "77609153"
---
# <a name="how-to-manage-volume-purchased-apps-from-the-microsoft-store-for-business-with-microsoft-intune"></a>如何使用 Microsoft Intune 從商務用 Microsoft Store 管理大量購買的應用程式

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[商務用 Microsoft 網上商店](https://www.microsoft.com/business-store)可讓您為組織個別或大量尋找及購買應用程式。 將市集連接到 Microsoft Intune，就可以從 Azure 入口網站管理大量採購的應用程式。 例如：
* 您可以使用 Intune，同步處理您已經從商店購買 (或免費) 的應用程式的清單。
* 經過同步的應用程式會出現在 Intune 系統管理主控台；一如其他應用程式，您也可以指派這些應用程式。
* 線上與離線授權的應用程式版本都會同步到 Intune。 在入口網站中，應用程式名稱將會附加「線上」或「離線」。
* 您可以追蹤有多少可用的授權，以及 Intune 管理主控台中正使用多少授權。
* 如果可用授權數目不足，Intune 會禁止指派及安裝應用程式。
* 當使用者離開企業，或系統管理員移除使用者及使用者裝置時，受商務用 Microsoft Store 管理的應用程式就會自動撤銷授權。

## <a name="before-you-start"></a>在您開始使用 Intune 之前

從商務用 Microsoft 網上商店開始同步及指派應用程式之前，請檢閱下列資訊：

- 將 Intune 設定為組織的行動裝置管理授權單位。
- 您必須已在商務用 Microsoft 網上商店註冊帳戶。
- 一旦您將 Intune 與商務用 Microsoft Store 帳戶建立關聯，未來將無法變更為不同帳戶。
- 從市集購買的應用程式無法手動加入 Intune 中，或從中刪除。 它們只能與商務用 Microsoft 網上商店同步處理。
- 您透過商務用 Microsoft Store 購買的線上和離線授權應用程式都會同步處理到 Intune 入口網站。 您接著可將這些應用程式部署至裝置群組或使用者群組。 
- 線上應用程式安裝由市集來管理。
- 免費的離線應用程式也可以同步處理至 Intune。 這些應用程式會透過 Intune 安裝，而不透過市集。
- 裝置必須加入 Active Directory Domain Services、Azure AD 或工作場所才能使用此功能。
- 註冊的裝置必須使用 Windows 10 的 1511 版或更新版本。

此外，從商務用 Microsoft 市集同步處理的相關集合和離線授權應用程式，現在將合併成 UI 中的單一應用程式項目。 來自個別套件的任何部署詳細資料都會移轉到單一項目。 若要在 Azure 入口網站中檢視相關的集合，請選取 [應用程式]  窗格中的 [應用程式授權]  。

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>建立您的商務用 Microsoft 網上商店帳戶與 Intune 的關聯
在 Intune 主控台中啟用同步處理之前，您必須將您的市集帳戶設定為使用 Intune 做為管理工具︰
1. 確定您登入[商務用 Microsoft Store](https://www.microsoft.com/business-store) 的租用戶帳戶，與您用來登入 Intune 的帳戶相同。
2. 在商務用市集中，選擇 [管理]  索引標籤，選取 [設定]  ，然後選擇 [散發]  索引標籤。
3. 如果您未特別將 **Microsoft Intune** 設定為行動裝置管理工具，請選擇 [新增管理工具]  以新增 **Microsoft Intune**。 如果您未啟用 **Microsoft Intune** 作為行動裝置管理工具，請按一下 [Microsoft Intune]  旁邊的 [啟用]  。 請注意，您應該啟用 [Microsoft Intune]  ，而不是 [Microsoft Intune 註冊]  。

> [!NOTE]
> 您先前可能只建立了某個用來指派應用程式的管理工具與商務用 Microsoft 網上商店的關聯。 現在可以建立多種管理工具與市集的關聯性，例如，Intune 和 Configuration Manager。 

您現在可以繼續進行，並在 Intune 主控台中設定同步處理。

## <a name="configure-synchronization"></a>設定同步處理

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [租用戶系統管理]   > [連接器與權杖]   > [商務用 Microsoft Store]  。
3. 按一下 [啟用]  。
4. 若還未執行此動作，請遵循前文所述按一下連結來註冊商務用 Microsoft 網上商店並關聯您的帳戶。
5. 從 [語言]  下拉式清單中，選擇來自商務用 Microsoft 網上商店應用程式在 Azure 入口網站中顯示的語言。 無論顯示的語言為何，可用時將以使用者的語言安裝。
6. 按一下 [同步]  ，以取得您從 Microsoft 網上商店購買的應用程式，將其同步到 Intune。

## <a name="synchronize-apps"></a>同步處理應用程式

1. 選取 [租用戶系統管理]   > [連接器與權杖]   > [商務用 Microsoft Store]  。
2. 按一下 [同步]  ，以取得您從 Microsoft 網上商店購買的應用程式，將其同步到 Intune。

> [!NOTE]
> 目前不支援具有已加密應用程式套件的應用程式，且不會同步到 Intune。

## <a name="assign-apps"></a>指派應用程式

您可以使用指派任何其他 Intune 應用程式的方式來指派市集應用程式。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。 

離線應用程式可以將目標設為使用者群組、 裝置群組或包含使用者和裝置的群組。
離線應用程式可以針對裝置上的特定使用者或裝置上的所有使用者進行安裝。 


當您指派商務用 Microsoft 網上商店應用程式時，安裝應用程式的每個使用者會使用一個授權。 如果您對某個已指派的應用程式使用了所有可用的授權，則無法再指派任何複本。 請採取下列其中一個動作：
* 從某些裝置解除安裝應用程式。
* 將目前指派的範圍減少，僅以您擁有足夠授權的使用者為目標。
* 從商務用 Microsoft 網上商店購買更多份應用程式。

## <a name="remove-apps"></a>移除應用程式

若要移除從商務用 Microsoft Store 同步的應用程式，您需要登入商務用 Microsoft Store 並退還應用程式。 不論應用程式是否免費，程序都相同。 針對免費應用程式，市集會退款 $0 美元。 以下範例顯示免費應用程式的退款。 

![移除應用程式詳細資料的螢幕擷取畫面](./media/windows-store-for-business/microsoft-store-for-business-01.png)

> [!NOTE]
> 移除應用程式在私人市集中的可見性，並不會防止 Intune 對該應用程式進行同步。 您必須對應用程式進行退款，才能將其完全移除。

## <a name="next-steps"></a>後續步驟

- [使用 Microsoft Intune 管理大量採購的應用程式與書籍](../vpp-apps.md)
