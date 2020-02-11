---
title: 將 Android Enterprise 系統應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何將 Enterprise 系統應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755250"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>將 Android Enterprise 系統應用程式新增至 Microsoft Intune

在您將應用程式指派給一部裝置或一群使用者之前，必須先將該應用程式新增到 Microsoft Intune。 Android Enterprise 裝置上支援系統應用程式。 您可以針對 [Android Enterprise 專用裝置](../enrollment/android-kiosk-enroll.md)或[完全受控裝置](../enrollment/android-fully-managed-enroll.md)啟用系統應用程式。

## <a name="add-the-app"></a>新增應用程式

您可以採取下列步驟，從 Azure 入口網站將 Android Enterprise 系統應用程式新增至 Intune：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在可用的 [其他]  類型下，選取 [Android Enterprise 系統應用程式]  。
4. 按一下 [選取]  。 [新增應用程式]  步驟隨即顯示。
在 [應用程式資訊]  頁面中，新增應用程式詳細資料：
    - **應用程式名稱**：輸入應用程式的名稱。
    - **發行者**：輸入應用程式發行者的名稱。  
    - **套件名稱**：輸入套件名稱。 Intune 將會驗證套件名稱是否有效。
5. 按一下 [下一步]  以顯示 [範圍標籤]  頁面。
8. 按一下 [選取範圍標籤]  來選擇性地為應用程式新增範圍標籤。 如需詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](~/fundamentals/scope-tags.md)。
9. 按一下 [下一步]  以顯示 [指派]  頁面。
10. 為應用程式選取群組指派。 如需詳細資訊，請參閱[新增群組來組織使用者與裝置](~/fundamentals/groups-add.md)。 
11. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。 檢閱您針對應用程式所輸入的值和設定。
12. 當您完成時，請按一下 [建立]  以將應用程式新增到 Intune。

您所建立之應用程式的 [概觀]  刀鋒視窗隨即顯示。

> [!NOTE]
> 您必須使用裝置的 OEM 來尋找您想要啟用/停用之應用程式的套件名稱。

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 

Android Enterprise 系統應用程式將啟用或停用已屬於平台一部分的應用程式。 若要啟用應用程式，將系統應用程式指派為 [必要]  。 若要停用應用程式，將系統應用程式指派為 [解除安裝]  。 無法將系統應用程式指派為可供使用者使用。


## <a name="next-steps"></a>後續步驟

- [將應用程式指派給群組](apps-deploy.md)
