---
title: 如何將 macOS 企業營運應用程式新增至 Microsoft Intune
titleSuffix: ''
description: 深入了解如何將 macOS 企業營運 (LOB) 應用程式新增至 Microsoft Intune。
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
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7aa6af751e5ab3e1e3cdff6b1d2e3d6693f65df
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755165"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>如何將 macOS 企業營運 (LOB) 應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

使用本文中的資訊，協助您將 macOS 企業營運應用程式新增至 Microsoft Intune。 您必須下載外部工具來預先處理 *.pkg* 檔案，然後才能將企業營運應用程式上傳到 Microsoft Intune。 必須在 macOS 裝置上對您的 *.pkg* 檔案進行預先處理。

> [!NOTE]
> 從 macOS Catalina 10.15 版本開始，在將應用程式新增至 Intune 之前，請先檢查以確定 macOS LOB 應用程式已驗證。 如果 LOB 應用程式的開發人員未驗證其應用程式，則這些應用程式即無法在使用者的 macOS 裝置上執行。 如需如何檢查應用程式是否已驗證的詳細資訊，請瀏覽 [Notarize your macOS apps to prepare for macOS Catalina](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Notarizing-your-macOS-apps-to-prepare-for-macOS/ba-p/808579) (驗證 macOS 應用程式以為 macOS Catalina 作準備)。

> [!NOTE]
> 雖然 macOS 裝置的使用者可以移除部分內建的 macOS 應用程式 (如股票和地圖)，但您無法使用 Intune 來重新部署這些應用程式。 如果使用者刪除這些應用程式，他們必須移至應用程式市集，並手動重新進行安裝。

## <a name="before-your-start"></a>開始之前

您必須下載外部工具，將已下載的工具標記為可執行檔，然後使用該工具來預先處理 *.pkg* 檔案，然後才能將企業營運檔案上傳到 Microsoft Intune。 必須在 macOS 裝置上對您的 *.pkg* 檔案進行預先處理。 使用 [Mac 版 Intune App Wrapping Tool]，讓 Mac 應用程式能受 Microsoft Intune 管理。

> [!IMPORTANT]
> *.pkg* 檔案必須使用「開發人員識別碼安裝程式」憑證簽署，此憑證是從 Apple Developer 帳戶取得。 只能使用 *.pkg* 檔案將 macOS LOB 應用程式上傳到 Microsoft Intune。 不支援轉換其他格式，例如將 *.dmg* 轉換為 *.pkg*。
>

1. 下載 [Mac 版 Intune App Wrapping Tool](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac) \(英文\)。

    > [!NOTE]
    > [Mac 版 Intune App Wrapping Tool]  必須 macOS 機器上執行。 

2. 將已下載的工具標記為可執行檔：
   - 啟動終端機應用程式。
   - 將目錄變更為 `IntuneAppUtil` 的所在位置。
   - 執行下列命令來使該工具成為可執行檔：<br> 
       `chmod +x IntuneAppUtil`

3. 使用[Mac 版 Intune App Wrapping Tool]  中的 `IntuneAppUtil` 命令，將 *.intunemac* 檔案包裝成 *.pkg* LOB 應用程式檔案。<br>

    用於 macOS 版 Microsoft Intune App Wrapping Tool 的範例命令：
    > [!IMPORTANT]
    > 在執行 `IntuneAppUtil` 命令之前，請確定引數 `<source_file>` 不包含空格。

    - `IntuneAppUtil -h`<br>
    此命令會顯示工具的使用方式資訊。
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    此命令會將 *.pkg* LOB 應用程式檔案包裝成 *.intunemac* 檔案。
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    此命令會擷取在所建立 *.intunemac* 檔案偵測到的參數和版本。

## <a name="select-the-app-type"></a>選取應用程式類型

1. 登入 [Microsoft 端點管理員系統管理中心](https://go.microsoft.com/fwlink/?linkid=2109431)。
2. 選取 [應用程式]   > [所有應用程式]   > [新增]  。
3. 在 [選取應用程式類型]  窗格中，在 [其他]  應用程式類型底下，選取 [企業營運應用程式]  。
4. 按一下 [選取]  。 [新增應用程式]  步驟隨即顯示。

## <a name="step-1---app-information"></a>步驟 1 - 應用程式資訊

### <a name="select-the-app-package-file"></a>選取應用程式套件檔案

1. 在 [新增應用程式]  窗格中，按一下 [選取應用程式套件檔案]  。 
2. 在 [應用程式套件檔案]  窗格中，選取 [瀏覽] 按鈕。 然後，選取副檔名為 *.intunemac* 的 macOS 安裝檔案。
   將會顯示應用程式詳細資料。
3. 當您完成時，請選取 [應用程式套件檔案]  窗格上的 [確定]  以新增應用程式。

### <a name="set-app-information"></a>設定應用程式資訊

1. 在 [應用程式資訊]  頁面中，新增應用程式的詳細資料。 窗格中某些值會隨著所選的應用程式自動填入。
    - **名稱**：輸入在公司入口網站中顯示的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，只有一個應用程式會出現在公司入口網站中。
    - **描述**：輸入應用程式的描述。 此描述會出現在公司入口網站上。
    - **發行者**：輸入應用程式發行者的名稱。
    - **最基本的作業系統**：從清單中，選擇能夠安裝應用程式的最基本作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別**：選取一或多個內建的應用程式類別，或選取您建立的類別。 類別可以讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式**：當使用者瀏覽應用程式時，在公司入口網站的主頁面上，以突顯的方式顯示應用程式。
    - **資訊 URL**：(選用) 輸入包含此應用程式相關資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **隱私權 URL**：(選擇性) 輸入包含這個應用程式之隱私權資訊的網站 URL。 此 URL 會出現在公司入口網站上。
    - **開發人員**：(選擇性) 輸入應用程式開發人員的姓名。
    - **擁有者**：(選擇性) 輸入此應用程式之擁有者的名稱。 **人力資源部門**就是一個例子。
    - **附註**：輸入要與此應用程式建立關聯的任何附註。
    - **標誌**：上傳與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
2. 按一下 [下一步]  以顯示 [範圍標籤]  頁面。

## <a name="step-2---select-scope-tags-optional"></a>步驟 2 - 選取範圍標籤 (選擇性)
您可以使用範圍標籤來決定可在 Intune 中看見用戶端應用程式資訊的人員。 如需範圍標籤的完整詳細資料，請參閱[針對分散式 IT 使用角色型存取控制和範圍標籤](../fundamentals/scope-tags.md)。

1. 按一下 [選取範圍標籤]  以選擇性地為應用程式新增範圍標籤。 
2. 按一下 [下一步]  以顯示 [指派]  頁面。

## <a name="step-3---assignments"></a>步驟 3 - 指派

1. 為應用程式選取 [必要]  、[適用於已註冊的裝置]  ，或 [解除安裝]  群組指派。 如需詳細資訊，請參閱[新增群組來組織使用者和裝置](~/fundamentals/groups-add.md)與[使用 Microsoft Intune 將應用程式指派給群組](apps-deploy.md)。
2. 按一下 [下一步]  以顯示 [檢閱 + 建立]  頁面。 

## <a name="step-4---review--create"></a>步驟 4 - 檢閱 + 建立

1. 檢閱您針對應用程式所輸入的值與設定。
2. 當您完成時，請按一下 [建立]  以將應用程式新增到 Intune。

    企業營運應用程式的 [概觀]  刀鋒視窗隨即顯示。

您建立的應用程式會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

> [!NOTE]
> 如果 *.pkg* 檔案包含多個應用程式或應用程式安裝程式，則 Microsoft Intune 只會在裝置上偵測到所有安裝的應用程式時，報告已成功安裝該*應用程式*。

## <a name="update-a-line-of-business-app"></a>更新企業營運應用程式

[!INCLUDE [shared-proc-lob-updateapp](../includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> 為了讓 Intune 服務能成功部署新的 *.pkg* 至裝置，您必須遞增 *.pkg* 套件內 *packageinfo*檔案中的套件 `version` 和 `CFBundleVersion` 字串。

## <a name="next-steps"></a>後續步驟

- 您已建立的應用程式會顯示在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

- 深入了解您可用來監視應用程式屬性和指派的方式。 如需詳細資訊，請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

- 深入了解您應用程式在 Intune 中的內容。 如需詳細資訊，請參閱[裝置和應用程式生命週期的概觀](../fundamentals/device-lifecycle.md)。
