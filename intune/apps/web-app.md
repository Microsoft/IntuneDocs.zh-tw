---
title: 將 Web 應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 深入了解將 Web 應用程式 (主從式應用程式) 新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5f08752f-0e87-4ad9-a34c-4991b3150775
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 90cdff66d32ac5edb3b1867a545f2c9627ccfe39
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754774"
---
# <a name="add-web-apps-to-microsoft-intune"></a>將 Web 應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 支援各種不同的應用程式類型，包括 Web 應用程式。 Web 應用程式是主從式應用程式。 伺服器提供了 Web 應用程式，其中包括 UI、內容和功能。 此外，現代的 Web 裝載平台通常具有安全性、負載平衡以及其他優勢。 Web 應用程式會在網路上進行個別維護。 您可以使用 Microsoft Intune 指向此應用程式類型。 您也可以指派哪些使用者群組可以存取這個應用程式。 

在您可以管理並指派應用程式給使用者之前，請將該應用程式新增至 Intune。 

Intune 會在使用者的裝置上建立 Web 應用程式捷徑。 針對 iOS 裝置，會在主畫面新增 Web 應用程式的捷徑。 針對 Android 裝置管理員裝置，會新增 Web 應用程式的捷徑到 Intune 公司入口網站應用程式小工具，而且使用者必須手動釘選該小工具。 針對 Windows 裝置，Web 應用程式的捷徑會放在 [開始] 功能表。

> [!Note]
> 使用者的裝置上必須安裝瀏覽器，以啟動網頁。 

> [!Note]
> 針對 Android Enterprise 裝置，請參閱[受控 Google Play Web 連結](apps-add-android-for-work.md#managed-google-play-web-links)

## <a name="add-a-web-app-to-intune"></a>將 Web 應用程式新增至 Intune
您可以執行下列動作，將應用程式新增至 Intune 以作為該應用程式的網路捷徑：

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在可用的 [其他]  類型下，選取 [網頁連結]  。
4. 按一下 [選取]  。 [新增應用程式]  步驟隨即顯示。
5. 在 [應用程式資訊]  頁面上，新增下列資訊：
    - **名稱**：輸入要顯示在公司入口網站中的應用程式名稱。 

        > [!NOTE]
        > 若您在部署並安裝應用程式之後透過 Intune Azure 入口網站變更應用程式名稱，將無法再使用命令定位應用程式。

    - **描述**：輸入應用程式的描述。 使用者會在公司入口網站上看到這項描述。
    - **發行者**：輸入此應用程式發行者的名稱。
    - **應用程式 URL**：輸入裝載您要指派之應用程式的網站 URL。
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 這麼做的話，當使用者在瀏覽公司入口網站時，可以更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式套件，請選取此選項。
    - **需要受管理瀏覽器以開啟此連結**：選取此選項時，可將網站或 Web 應用程式的連結指派給使用者，以讓他們在 Intune Managed Browser 中開啟連結。 他們的裝置上必須安裝此瀏覽器。
    - **標誌**：上傳要與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
6. 按一下 [下一步]  以顯示 [範圍標籤]  頁面。
7. 按一下 [選取範圍標籤]  來選擇性地為應用程式新增範圍標籤。 如需詳細資訊，請參閱[針對分散式 IT 使用角色型存取控制 (RBAC) 和範圍標籤](~/fundamentals/scope-tags.md)。
8. 按一下 [下一步]  以顯示 [指派]  頁面。
9. 為應用程式選取群組指派。 如需詳細資訊，請參閱[新增群組來組織使用者與裝置](~/fundamentals/groups-add.md)。 
10. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。 檢閱您針對應用程式所輸入的值和設定。
11. 當您完成時，請按一下 [建立]  以將應用程式新增到 Intune。

    您所建立之應用程式的 [概觀]  刀鋒視窗隨即顯示。

> [!Note]
> 目前，將 Intune Web 應用程式部署到 iOS 裝置會與管理設定檔相關聯，因而無法手動移除。 您可以在 Intune 入口網站中將部署類型變更為 [解除安裝]  ，此時系統便可以自動移除 Web 應用程式。 不過，如果在將應用程式指派意圖變更為 [解除安裝]  之前移除部署，Web 應用程式將會永久保留在裝置上，直到從 Intune 取消註冊該裝置為止。

終端使用者可以選取 Web 應用程式，然後選擇 [以瀏覽器開啟]  選項，直接從 Windows 公司入口網站應用程式啟動 Web 應用程式。 已發佈的 Web URL 會直接在網頁瀏覽器中開啟。 

## <a name="next-steps"></a>後續步驟

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 如需相關說明，請參閱[將應用程式指派給群組](apps-deploy.md)。 
