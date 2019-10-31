---
title: 將適用於 Windows 10 的 Microsoft Edge 新增至 Microsoft Intune
titleSuffix: ''
description: 了解如何將適用於 Windows 的 Microsoft Edge 新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: kellieei
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 492feb3f2ef5f5bbbc1537d4c60ac12d5fd6bdcd
ms.sourcegitcommit: 0be25b59c8e386f972a855712fc6ec3deccede86
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72585601"
---
# <a name="add-microsoft-edge-for-windows-10-to-microsoft-intune"></a>將適用於 Windows 10 的 Microsoft Edge 新增至 Microsoft Intune

您必須先將應用程式新增至 Intune，才可以部署、設定、監視或保護它們。 其中一個可用的[應用程式類型](~/apps/apps-add.md#app-types-in-microsoft-intune)是 Microsoft Edge 77 版和更新版本  。 藉由在 Intune 中選取此應用程式類型，您可以指派 Microsoft Edge *77 版和更新版本*，並將其安裝到您所管理且執行 Windows 10 的裝置。

> [!IMPORTANT]
> 此應用程式類型處於**公開預覽**，並提供 Windows 10 的開發人員和搶鮮版 (Beta) 通道。 部署僅限英文 (EN)，不過，終端使用者可以在瀏覽器中的 [設定]   > [語言]  下變更顯示語言。 Microsoft Edge 是一個 Win32 應用程式，安裝在系統內容和類似的架構 (x86 OS 上的 x86 應用程式，以及 x64 OS 上的 x64 應用程式) 上。 此外，Edge 的自動更新預設會 [開啟]  ，而且無法解除安裝 Edge。

> [!NOTE]
> Microsoft Edge *77 版和更新版本*也適用於 macOS。
> 
> 您不能將 Microsoft Edge 的內建應用程式部署用於加入工作場所網路的電腦。 內建應用程式部署需要 Intune 管理延伸模組，這僅適用於已加入 AAD 的裝置。 您仍然可以使用上傳至**用戶端應用程式**的 *.msi* 來部署 Microsoft Edge *77 版和更新版本*，請參閱[將 Windows 企業營運應用程式新增至 Microsoft Intune](~/apps/lob-apps-windows.md)。

## <a name="prerequisites"></a>必要條件
- 需要 Windows 10 RS2 和更新版本。
- 在使用者內容中為**開發人員**和**搶鮮版 (Beta)** 通道提供的 Microsoft Edge *77 版和更新版本*的任何預先安裝版本，將被在系統內容中安裝的 Edge 覆寫。

## <a name="configure-the-app-in-intune"></a>在 Intune 中設定應用程式
您可以使用下列步驟，將 Microsoft Edge 77 版和更新版本新增至 Intune：

1. 登入 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)。
2. 在 [Intune]  窗格中，選取 [用戶端應用程式]   > [應用程式]   > [新增]  。
3. 在 [應用程式類型]  清單中的 [Microsoft Edge 77 版和更新版本]  底下，選取 [Windows 10]  。

## <a name="configure-app-information"></a>設定應用程式資訊
在此步驟中，您要提供應用程式部署的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式，並幫助使用者在公司入口網站中尋找應用程式。

1. 按一下 [應用程式資訊]  以顯示 [應用程式資訊]  刀鋒視窗。
2. 在 [應用程式資訊]  刀鋒視窗中，您會提供此應用程式部署的相關資訊。 這項資訊可協助您在 Intune 中識別應用程式，並幫助使用者在公司入口網站中尋找應用程式。
    - **名稱**：輸入要顯示在公司入口網站中的應用程式名稱。 請確定所有名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述**：輸入應用程式的描述。 例如，您可以在 [描述] 中列出目標使用者。
    - **發行者**：Microsoft 會顯示為發行者。
    - **類別**：(選擇性) 選取一或多個內建的應用程式類別，或選取您建立的類別。 此設定可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：若要在使用者瀏覽應用程式時，於公司入口網站的主頁面上以醒目方式顯示應用程式，請選取此選項。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員**：Microsoft 會顯示為開發人員。
    - **擁有者**：Microsoft 會顯示為擁有者。
    - **附註**：(選擇性) 輸入要與此應用程式建立關聯的任何附註。
3. 選取 [確定]  。

## <a name="configure-app-settings"></a>設定應用程式設定
在此步驟中，設定應用程式的安裝選項。

1. 接著，從 [新增應用程式]  刀鋒視窗選取 [應用程式設定]  。
2. 在 [應用程式設定]  刀鋒視窗中，從 [通道]  清單中選取 [Beta]  或 [Dev]  ，以確定將從哪個 Edge 通道部署應用程式。
    - **搶鮮版 (Beta)** 頻道是最穩定的 Microsoft Edge 預覽體驗，也是在您組織內進行完整試驗的最佳選擇。 每隔六週進行重大更新，每個版本都會納入 Dev 通道的學習和改良功能。
    - **Dev** 通道已準備好取得 Windows、Windows Server 和 macOS 的企業意見反應。 它會每週更新，並包含最新的改良功能和修正程式。

    > [!NOTE]
    > Microsoft Edge 瀏覽器標誌是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的標誌。

3.  選取 [確定]  。

## <a name="select-scope-tags-optional"></a>選取範圍標籤 (選擇性)
您可以使用範圍標籤來決定可在 Intune 中看見用戶端應用程式資訊的人員。 如需範圍標籤的完整詳細資料，請參閱針對分散式 IT 使用角色型存取控制和範圍標籤。
1.  選取 [範圍 (標籤)]   > [新增]  。
2.  使用 [選取]  方塊來搜尋範圍標籤。
3.  選取您想要指派至此應用程式之範圍標籤旁邊的核取方塊。
4.  按一下 [選取]   > [確定]  。

## <a name="add-the-app"></a>新增應用程式
當您完成設定應用程式時，請從 [應用程式]  刀鋒視窗中選取 [新增]  。 

您建立的應用程式即會顯示在應用程式清單中，而您可從中將該應用程式指派給所選的群組。 

> [!NOTE]
> 目前，如果您取消指派 Microsoft Edge 的部署，它會保留在裝置上。

## <a name="troubleshooting"></a>疑難排解
**適用於 Windows 10 的 Microsoft Edge 77 版和更新版本：**<br>
Intune 會使用 Intune 管理延伸模組來下載 Microsoft Edge 安裝程式，並將其部署至指派的 Windows 10 裝置，然後將部署設定傳達給 Microsoft Edge 安裝程式，以直接從 CDN 下載並安裝 Microsoft Edge 瀏覽器。 參考 [Intune 管理延伸模組的必要條件](~/apps/intune-management-extension.md#prerequisites)，以及存取 Azure 更新服務和 CDN 中所述的最佳做法，以確保您的網路設定允許 Windows 10 裝置存取這些位置。

## <a name="next-steps"></a>後續步驟
- [將應用程式指派給群組](~/apps/apps-deploy.md)
