---
title: 如何將 macOS 企業營運應用程式新增至 Microsoft Intune
titlesuffix: ''
description: 了解如何將 macOS 企業營運 (LOB) 應用程式新增至 Microsoft Intune。
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ef8008ac-8b85-4bfc-86ac-1f9fcbd3db76
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0304d90384bb2f6a5a78dd14bcf289fc8eb03bd1
ms.sourcegitcommit: 34e96e57af6b861ecdfea085acf3c44cff1f3d43
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
ms.locfileid: "34224359"
---
# <a name="how-to-add-macos-line-of-business-lob-apps-to-microsoft-intune"></a>如何將 macOS 企業營運 (LOB) 應用程式新增至 Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

使用本文中的資訊，協助您將 macOS 企業營運應用程式新增至 Microsoft Intune。 您必須下載外部工具來預先處理 *.pkg* 檔案，然後才能將企業營運應用程式上傳到 Microsoft Intune。 必須在 macOS 裝置上對您的 *.pkg* 檔案進行預先處理。

>[!NOTE]
>雖然 macOS 裝置的使用者可以移除部分內建的 macOS 應用程式 (如股票和地圖)，但您無法使用 Intune 來重新部署這些應用程式。 如果使用者刪除這些應用程式，他們必須移至應用程式市集，並手動重新進行安裝。
>
>只能使用 *.pkg* 檔案將 macOS LOB 應用程式上傳到 Microsoft Intune。 

## <a name="step-1---pre-process-your-software-setup-file"></a>步驟 1 - 預先處理您的軟體安裝檔

使用 [Mac 版 Intune App Wrapping Tool]，讓 Mac 應用程式能受 Microsoft Intune 管理。

1. 下載並執行 [Mac 版 Intune App Wrapping Tool](https://github.com/msintuneappsdk/intune-app-wrapping-tool-mac) \(英文\)。

    > [!NOTE]
    > [Mac 版 Intune App Wrapping Tool] 必須 macOS 機器上執行。

2. 使用[Mac 版 Intune App Wrapping Tool] 中的 `IntuneAppUtil` 命令，將 *.intunemac* 檔案包裝成 *.pkg* LOB 應用程式檔案。<br>

    用於 macOS 版 Microsoft Intune App Wrapping Tool 的範例命令：
    
    - `IntuneAppUtil -h`<br>
    此命令會顯示工具的使用方式資訊。
    
    - `IntuneAppUtil -c <source_file> -o <output_file> [-v]`<br>
    此命令會將 *.pkg* LOB 應用程式檔案包裝成 *.intunemac* 檔案。
    
    - `IntuneAppUtil -r <filename.intunemac> [-v]`<br>
    此命令會擷取在所建立 *.intunemac* 檔案偵測到的參數和版本。

## <a name="step-2---specify-the-software-setup-file"></a>步驟 2 - 指定軟體安裝檔

1. 登入 [Azure 入口網站](https://portal.azure.com)。
2. 選擇 [All services] (所有服務) > [Intune]。 Intune 位於 [Monitoring + Management] (監視 + 管理) 區段。
3. 在 [Intune] 窗格中，選擇 [行動應用程式]。
4. 在**行動應用程式**工作負載中選擇 [管理]  >  [應用程式]。
5. 從應用程式清單上方選擇 [新增]。
6. 在 [新增應用程式] 窗格中，選擇 [企業營運應用程式]。

## <a name="step-3---configure-the-app-package-file"></a>步驟 3 - 設定應用程式套件檔案

1. 在 [新增應用程式] 窗格中，選擇 [應用程式套件檔案]。
2. 在 [應用程式套件檔案] 窗格中，選擇瀏覽按鈕，然後選取副檔名為 *.intunemac* 的 macOS 安裝檔。
3. 完成之後，請選擇 [確定]。


## <a name="step-4---configure-app-information"></a>步驟 4 - 設定應用程式資訊

1. 在 [新增應用程式] 窗格中選擇 [應用程式資訊]。
2. 在 [應用程式資訊] 窗格中，新增您應用程式的詳細資料。 窗格中某些值會隨所選的應用程式自動填入︰
    - **名稱** - 輸入要顯示在公司入口網站中的應用程式名稱。 確定您使用的所有應用程式名稱都是唯一的。 如果有重複的應用程式名稱，使用者只會在公司入口網站中看到其中一個應用程式。
    - **描述** - 輸入公司入口網站中要向使用者顯示的應用程式描述。
    - **發行者** - 輸入應用程式的發行者名稱。
    - **最小作業系統** - 從清單中選擇應用程式所能安裝的最小作業系統版本。 若將應用程式指派給安裝舊版作業系統的裝置，就不會進行安裝。
    - **類別**：選取一或多個內建應用程式類別，或選取您建立的類別。 這可讓使用者在瀏覽公司入口網站時，更輕鬆地找到應用程式。
    - **將此顯示為公司入口網站中的精選應用程式** - 當使用者瀏覽應用程式時，以醒目方式在公司入口網站的主頁面上顯示此應用程式。
    - **資訊 URL** - 選擇是否要輸入包含此應用程式相關資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **隱私權 URL** - 選擇是否要輸入包含此應用程式之隱私權資訊的網站 URL。 使用者會在公司入口網站中看到這個 URL。
    - **開發人員** - 選擇是否要輸入應用程式開發人員的姓名。
    - **擁有者** - 選擇是否要輸入此應用程式的擁有者名稱，例如**人力資源部門**。
    - **注意** - 輸入要與此應用程式相關聯的附註。
    - **標誌** - 上傳將與應用程式相關聯的圖示。 這是使用者瀏覽公司入口網站時，會隨應用程式一起顯示的圖示。
3. 完成之後，請選擇 [確定]。

## <a name="step-5---finish-up"></a>步驟 5 - 完成

1. 在 [新增應用程式] 窗格中，驗證您應用程式的詳細資料正確。
2. 選擇 [新增]，將應用程式上傳至 Intune。

您建立的應用程式會顯示在應用程式清單中，而您可從中將應用程式指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

> [!NOTE]
> 如果 *.pkg* 檔案包含多個應用程式或應用程式安裝程式，則 Microsoft Intune 只會在裝置上偵測到所有安裝的應用程式時，報告已成功安裝該*應用程式*。

## <a name="step-6---update-a-line-of-business-app"></a>步驟 6 - 更新企業營運應用程式

[!INCLUDE [shared-proc-lob-updateapp](./includes/shared-proc-lob-updateapp.md)]

> [!NOTE]
> 為了讓 Intune 服務能成功部署新的 *.pkg* 至裝置，您必須遞增 *.pkg* 套件內 *packageinfo*檔案中的套件 `version` 和 `CFBundleVersion` 字串。

## <a name="next-steps"></a>接下來的步驟

- 您已建立的應用程式會顯示在應用程式清單中。 您現在可以將它指派給您選擇的群組。 如需協助，請參閱[如何將應用程式指派給群組](apps-deploy.md)。

- 深入了解您可用來監視應用程式屬性和指派的方式。 如需詳細資訊，請參閱[如何監視應用程式資訊和指派](apps-monitor.md)。

- 深入了解您應用程式在 Intune 中的內容。 如需詳細資訊，請參閱[裝置和應用程式生命週期的概觀](introduction-device-app-lifecycles.md)。
