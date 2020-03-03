---
title: 為 Autopilot 佈建裝置新增並指派 Windows 10 公司入口網站應用程式
titleSuffix: Microsoft Intune
description: 為 Autopilot 佈建裝置新增並指派 Windows 10 公司入口網站應用程式至 Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/21/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c13d8d774037f0d2db5832af7f39c864330fef30
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/25/2020
ms.locfileid: "77577281"
---
# <a name="add-and-assign-the-windows-10-company-portal-app-for-autopilot-provisioned-devices"></a>為 Autopilot 佈建裝置新增並指派 Windows 10 公司入口網站應用程式

若要管理裝置及安裝應用程式，您的使用者可以使用公司入口網站應用程式。 您可以直接從 Intune 指派 Windows 10 公司入口網站應用程式。 

## <a name="prerequisites"></a>先決條件

針對 Windows 10 Autopilot 佈建裝置，建議您將商務用 Microsoft Store 帳戶與 Intune 建立關聯。 如需詳細資訊，請參閱[如何使用 Microsoft Intune 從商務用 Microsoft Store 管理大量購買的應用程式](~/apps/windows-store-for-business.md)。

您可以透過下列步驟選擇公司入口網站 (離線) 並安裝。 當指派給 Autopilot 群組時，公司入口網站應用程式便會安裝在裝置內容中，並在使用者登入之前安裝於裝置上。 

## <a name="configure-settings-to-show-offline-apps"></a>組態設定以顯示離線應用程式
1. 使用您的系統管理員帳戶，登入[商務用 Microsoft Store](https://www.microsoft.com/business-store)。
2. 選取靠近視窗頂端的 [管理]  索引標籤。
3. 在左窗格中，選取 [設定]  。
4. 在 [購物體驗]  下方，將 [顯示離線應用程式]  設定為 [開啟]  。  
    隨即顯示離線授權應用程式。

## <a name="get-the-offline-company-portal-app"></a>取得離線公司入口網站應用程式
1. 搜尋「公司入口網站」  應用程式，然後加以選取。
2. 將 [授權類型]  設定為 [離線]  。
3. 選取 [取得應用程式]  ，以取得離線公司入口網站應用程式，並將其新增至您的清查。

## <a name="assign-the-company-portal-app"></a>指派公司入口網站應用程式
1. 使用您的系統管理員帳戶登入  [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431) 。 
2. 在右側窗格中，選取 [應用程式] ****   索引標籤。 
3. 在 [依平台] **** 底下，選取 [Windows]  。 
4. 選取 [公司入口網站 (離線)] **** 。   
5. 您必須等候同步排程完成，或從 Microsoft 端點管理員系統管理中心進行手動同步。
6. 針對您所選的 Autopilot 裝置群組，將公司入口網站應用程式指派為必要的應用程式。

## <a name="next-steps"></a>後續步驟

- 若要深入了解如何指派應用程式，請參閱[將應用程式指派給群組](apps-deploy.md)。

